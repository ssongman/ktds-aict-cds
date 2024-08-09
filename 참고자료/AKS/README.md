## AKS

- Network 및 Infra 관련 고가용성을 위한 AZ 구성과, 노드 그룹 분배 및 설계 전략 관련
- backup 전략
- Pod Auto scaling
- Cluster Auto scaling

### 기본 아키텍처

1. Node Group 설계
   - 멀티-AZ 배포: 노드 풀을 여러 가용성 영역에 배포하여 고가용성을 보장
   - 다양한 노드 유형 사용: 워크로드에 맞춘 노드 유형과 크기를 사용하여 성능을 최적화
   - Cluster 기본 arch.: <https://learn.microsoft.com/ko-kr/azure/architecture/reference-architectures/containers/aks/baseline-aks>
   - AKS MSA 기본 arch.: <https://learn.microsoft.com/ko-kr/azure/architecture/reference-architectures/containers/aks-microservices/aks-microservices>

2. Backup 방안
   - ETCD, Persistent Volume, 애플리케이션 데이터의 정기적인 백업을 설정하여 데이터 손실에 대비
   - Velero 와 통합하여 backup 활용도 증대시킴
   - AKS Backup 기본: <https://learn.microsoft.com/ko-kr/azure/backup/azure-kubernetes-service-backup-overview>
   - AKS Velero 통합: <https://learn.microsoft.com/ko-kr/azure/aks/hybrid/backup-workload-cluster>

3. Pod Auto Scaling
   - HPA와 VPA를 설정하여 Pod 수와 리소스를 자동으로 조절
   - 사용자 정의 메트릭을 기반으로 하는 오토스케일링을 설정
   - K8s HPA 기본: <https://kubernetes.io/ko/docs/tasks/run-application/horizontal-pod-autoscale/>
   - AKS HPA 기본: <https://learn.microsoft.com/ko-kr/azure/aks/concepts-scale>
   - AKS VPA 기본: <https://learn.microsoft.com/ko-kr/azure/aks/use-vertical-pod-autoscaler>
   - AKS Custom Metric Autoscaling (Application Gateway metrics 기반): <https://learn.microsoft.com/en-us/azure/application-gateway/ingress-controller-autoscale-pods>

4. Cluster Autoscaler
   - 클러스터의 리소스 사용량을 기반으로 노드를 자동으로 추가하거나 제거하여 비용 효율성과 성능을 최적화
   - Cluster Autoscaler official: <https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler>
   - AKS Autoscaler official: <https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/cloudprovider/azure/README.md>
   - AKS Autoscaler 예제: <https://learn.microsoft.com/ko-kr/azure/aks/cluster-autoscaler?tabs=azure-cli>


## Chat GPT 정리 내역

,,,

---

### 1. **고가용성을 위한 Node Group 설계 방안**

#### 1.1. **멀티-AZ 배포**
- **노드 풀 분산**: AKS 클러스터를 여러 가용성 영역(Availability Zones)에서 배포합니다. 이를 통해 가용성 영역 장애 시에도 클러스터의 가용성을 유지할 수 있습니다.
- **노드 풀 예시**: 각 가용성 영역에 대해 별도의 노드 풀을 구성하여 노드가 각 영역에 분산되도록 합니다.
  - **예시**: 
    - Node Pool 1: AZ1 (Standard_D4_v5)
    - Node Pool 2: AZ2 (Standard_D4_v5)
    - Node Pool 3: AZ3 (Standard_D4_v5)

#### 1.2. **다양한 노드 크기**
- **다양한 노드 유형**: 다양한 노드 크기와 유형을 사용하여 워크로드의 CPU와 메모리 요구 사항에 맞춰 리소스를 최적화합니다.
  - **예시**: 기본 노드 풀은 `Standard_D4_v5`를 사용하고, 메모리 집약적인 작업에는 `Standard_E4_v5`를 추가로 구성합니다.

#### 1.3. **수명 주기 관리**
- **정기적인 노드 교체**: 노드 수명 주기와 업그레이드를 관리하여 노드의 오래된 하드웨어 문제를 방지합니다.
  - **예시**: `node pool` 업그레이드를 자동화하여 새로운 노드에 배포한 후 구형 노드를 교체합니다.

### 2. **Backup 방안**

#### 2.1. **ETCD 백업**
- **정기적 ETCD 백업**: Kubernetes 클러스터의 상태를 저장하는 ETCD의 정기적인 백업을 설정합니다.
  - **Azure Backup**: Azure Backup을 사용하여 ETCD 스냅샷을 주기적으로 백업합니다.
  - **Backup 빈도**: 매일 또는 매주 백업을 설정하여 클러스터 상태를 정기적으로 저장합니다.

#### 2.2. **Persistent Volume 백업**
- **Azure Disk Backup**: Azure Disk을 사용하는 Persistent Volume의 백업을 수행합니다.
  - **Snapshot**: Azure Managed Disk의 스냅샷 기능을 사용하여 데이터를 주기적으로 백업합니다.
  - **Azure Backup**: Azure Backup을 사용하여 파일과 디렉토리 수준의 복원점을 생성합니다.

#### 2.3. **애플리케이션 데이터 백업**
- **애플리케이션 데이터 백업**: 애플리케이션의 데이터베이스와 파일 시스템을 주기적으로 백업합니다.
  - **예시**: SQL Database와 Redis의 백업을 자동화하여 데이터 손실에 대비합니다.

#### 2.4 **Velero 활용**
Velero는 Kubernetes 클러스터의 백업 및 복구를 관리하는 강력한 도구입니다. Velero를 사용하면 클러스터와 관련된 리소스, 볼륨 데이터, 그리고 애플리케이션 상태를 백업하고 복구할 수 있습니다. Azure Kubernetes Service (AKS)와 함께 사용할 때 Velero의 활용도를 다음과 같이 설명할 수 있습니다:

##### 1. **ETCD 백업**

Velero는 기본적으로 ETCD 백업을 지원하지 않습니다. ETCD 백업을 관리하려면 Azure Backup 또는 Azure의 ETCD 스냅샷 도구를 사용하는 것이 좋습니다. Velero는 Kubernetes 리소스의 상태와 관련된 메타데이터를 백업합니다.

- **Velero의 역할**: Kubernetes 리소스와 구성(예: ConfigMap, Secret, Deployment 등)의 백업 및 복구를 지원합니다. ETCD와 같은 클러스터의 상태 정보를 직접 백업할 수는 없습니다.

##### 2. **Persistent Volume 백업**

Velero는 Persistent Volume (PV) 데이터를 백업하고 복구할 수 있는 기능을 제공합니다. Azure Disk을 사용하는 Persistent Volume의 백업을 Velero와 통합하여 처리할 수 있습니다.

- **Velero의 VolumeSnapshot 지원**: Velero는 Kubernetes VolumeSnapshot을 사용하여 Persistent Volume의 스냅샷을 생성하고, 이를 백업합니다.
  - **VolumeSnapshot**: Velero는 Kubernetes VolumeSnapshot API를 사용하여 스냅샷을 관리합니다.
  - **백업 및 복구**: Velero를 사용하여 볼륨 데이터의 백업과 복구를 자동화할 수 있습니다.

##### 3. **애플리케이션 데이터 백업**

Velero는 애플리케이션 데이터와 관련된 백업을 지원하지만, 데이터베이스나 애플리케이션의 상태를 백업하는 데는 특정한 설정이 필요합니다.

- **애플리케이션 리소스 백업**: Velero는 Kubernetes의 모든 리소스(예: Deployment, Service, ConfigMap 등)를 백업할 수 있으며, 이와 관련된 애플리케이션의 상태를 보존합니다.
- **정기적인 데이터 백업**: 데이터베이스와 같은 애플리케이션 데이터를 백업하려면 Velero 외에 데이터베이스 자체의 백업 솔루션(예: SQL Database의 자동 백업)을 사용하는 것이 좋습니다.

### 3. **Pod Auto Scaling 정책**

#### 3.1. **Horizontal Pod Autoscaler (HPA)**
- **HPA 설정**: CPU 사용량, 메모리 사용량, 또는 사용자 정의 메트릭에 기반하여 Pod 수를 자동으로 조절합니다.
  - **예시**: 
    - `kubectl autoscale deployment backend --cpu-percent=50 --min=10 --max=50`
    - **기준**: 평균 CPU 사용량이 50%를 초과하면 Pod 수를 자동으로 늘립니다.

#### 3.2. **Vertical Pod Autoscaler (VPA)**
- **VPA 설정**: Pod의 리소스 요청과 제한을 동적으로 조정하여 워크로드의 CPU와 메모리 요구를 충족합니다.
  - **예시**: 
    - **VPA 설정**: `VerticalPodAutoscaler` 리소스를 정의하여 Pod의 CPU와 메모리 리소스를 조정합니다.

#### 3.3. **Custom Metrics Autoscaler**
- **사용자 정의 메트릭**: CPU와 메모리 외에 애플리케이션별 사용자 정의 메트릭을 사용하여 Auto Scaling을 설정합니다.
  - **예시**: `Prometheus`와 `KEDA`를 사용하여 사용자 정의 메트릭에 기반한 오토스케일링을 구현합니다.

### 4. **Cluster Autoscaler 설정**

#### 4.1. **Cluster Autoscaler 설치**
- **Cluster Autoscaler**: 클러스터의 리소스 사용량을 모니터링하고, 필요에 따라 노드를 자동으로 추가하거나 제거합니다.
  - **설정**:
    - **Azure CLI**: `az aks update --resource-group <rg> --name <aks-cluster> --enable-cluster-autoscaler --min-count <min> --max-count <max> --nodepool-name <nodepool-name>`

#### 4.2. **자동 스케일링 정책**
- **노드 풀 관리**: 각 노드 풀의 최소 및 최대 노드 수를 설정하여 클러스터의 확장성을 조절합니다.
  - **예시**:
    - **노드 풀 1**: 최소 2, 최대 10 노드
    - **노드 풀 2**: 최소 2, 최대 5 노드

#### 4.3. **리소스 요청 및 제한**
- **Pod 리소스 요청**: 각 Pod의 리소스 요청과 제한을 설정하여 노드 리소스의 효율적인 사용을 보장합니다.
  - **예시**:
    - **Pod 리소스 요청**: `cpu: 500m`, `memory: 1Gi`
    - **Pod 리소스 제한**: `cpu: 1000m`, `memory: 2Gi`
