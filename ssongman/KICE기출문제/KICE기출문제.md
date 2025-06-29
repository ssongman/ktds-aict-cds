





# CDS-Azure

[KICE 2025년 Pilot]

---

## 문항 1

A사는 Azure에 시스템을 구성하여 사용 중이다. 카카오사태로 인하여 DR시스템을 구축할 것을 권고 받아 DR을 구성하려고 한다. 현재 Korea Central Region을 사용 중에 있으며 DR의 경우 Korea South Region에 구성하려고 한다. 보기 중 적절하지 않은 것을 고르시오. [4점]

1. Korea South Region에 VNET를 생성한다.
2. Korea South Region에 현 Korea Central에 사용중인 모든 VM SKU가 DR에 사용가능한지 확인한다.
3. Korea South Region에 구성된 Azure DNS Private Resolver에 장애 상황을 대비하여 Korea Central Region에서 사용하는 도메인 정보를 추가한다.
4. Korea South Region에 On-Premise 데이터센터와 ExpressRoute를 구성한다.
5. Korea South Region에 사용하는 outbound용 public IP를 한정하기 위하여 Hub VNET에 NAT Gateway를 구성한다.

**(정답)** 3

**(해설)** Azure DNS Private Resolver는 Korea Central Region에서 제공하는 서비스로 Region 장애를 대비하여 Korea South Region에는 VM 기반의 DNS를 구성해야 한다.

---

## 문항 2

A사는 Azure로 인프라를 마이그레이션하려고 하며 그 중 Database는 대부분 MSSQL을 사용 중에 있다. Database 마이그레이션 관련되어 아래 고객의 요구사항이 있어 부합되는 Azure의 Database 서비스 및 기능을 선정하려고 한다. 보기의 내용 중 적절한 것을 선택하여 보기 번호를 답안에 작성하시오. [4점]

### [요구사항]

- Region은 Korea Central을 사용해야 한다.
- 주 Region인 Korea Central과 Pair Region인 Korea South에 Read Replica가 필요하다.
- DR 상황 시 Application들의 Endpoint 변경이 없는 단일 Endpoint가 가능해야 한다.
- Timezone 설정을 할 수 있어야 한다.
- DBLink를 사용할 수 있어야 한다.

### [보기]
| SQL서버 종류 및 Tier                             | 고가용성 옵션              |
| ------------------------------------------------ | -------------------------- |
| 가. Azure SQL DataBase General Purpose           | 가. Active Geo-Replication |
| 나. Azure SQL Database Business Critical         | 나. Auto Failover Group    |
| Et. Azure SQL Managed Instance General Purpose   |                            |
| 라. Azure SQL Managed Instance Business Critical |                            |

**[답안]**

(1) SQL서버 종류 및 Tier 보기 선택:  
(2) 고가용성 옵션 보기 선택:  

**(정답)** 라, 나  

**(해설)** Azure SQL Managed Instance는 Active Geo-Replication 기능이 없음. Primary Region에 Read Replica는 기본 제공 HA를 구성하여 사용하고, Pair Region인 Korea South에 Read Replica가 필요하므로 Auto Failover Group으로 구성함.

---

## 문항 3

김선임은 C고객사의 시스템을 운영 중 Private 네트워크에서만 접근해야 하는 중요 파일 저장용 Storage Account에 퍼블릭 접근 권한을 실수로 부여하였다. 일주일 후 해당 조치가 문제가 있다는 것을 확인하여 퍼블릭 접근 권한을 회수 조치하였다. 추후 동일 이슈가 발생하지 않도록 변경사항에 대해 사전에 자동으로 모니터링될 수 있도록 방안을 수립하기로 하였다. 다음 중 적절하지 못한 것을 고르시오. [4점]

1. Azure Policy를 적용하여 퍼블릭 접근이 허용된 Storage Account에 대해 Audit Log를 남기고 알람을 발생시키도록 한다.
2. Azure Automation을 활용하여 주기적으로 퍼블릭 접근이 허용된 Storage Account을 확인하고 조치할 수 있도록 한다.
3. Azure CLI를 활용하여 Resource Graph에 질의하여 private endpoint가 구성되지 않은 Storage Account을 확인하고 수정할 수 있도록 한다.
4. Azure 활동 로그 이벤트를 수신할 수 있는 Event Grid와 Logic Apps를 활용하여 퍼블릭 접근 권한이 부여되는 Storage Account을 확인하고 수정할 수 있도록 한다.
5. Storage Account에 진단 설정을 활성화하여 익명 요청이 성공한 Storage Account을 확인하고 수정할 수 있도록 한다.

**(정답)** 3

**(해설)** Storage Account에서 private endpoint와 퍼블릭 접근 차단 설정은 별개의 설정이며, 각각 독립적으로 설정할 수 있으므로, private endpoint 구성 여부로 퍼블릭 접근 가능 여부를 판별할 수 없다.

---

## 문항 4

A사는 차세대 프로젝트를 위해 Azure Public Cloud를 선정하였으며 금융권 Cloud 보안 요건 중 데이터센터 가용성 항목에 대응하기 위해서 Azure의 Availability Zone 기능 검토를 확인 중에 있다. 다음 내용 중 올바른 것을 고르시오. [4점]

1. VM의 경우 Availability Zone 내 Availability Set을 함께 구성하여 VM 가용성을 극대화할 수 있다.
2. Standard Load Balancer는 Frontend-ip를 Availability Zone 분산, Availability Zone 지정을 할 수 있으며 Zone 지정을 할 경우 Back-End VM들의 Zone과 동일하지 않아도 LB를 통한 통신을 할 수 있다.
3. Multi Subscription을 사용할 경우 각 Subscription의 Availability Zone Number는 동일한 데이터센터를 의미한다.
4. Azure Virtual Network은 Availability Zone을 사용하기 위하여 Zone별로 Subnet을 생성해야만 한다.
5. Azure VPN Gateway는 Availability Zone 분산(Zone Redundant)을 제공하지 않으므로 2개의 Zone을 사용하도록 각각의 VPN Gateway를 구성한다.

**(정답)** 2 

**(해설)** 1) VM의 경우 AZ을 지정하면 AS을 사용자가 지정할 수 없다. 

---

## 문항 5

B사는 VM 기반 WEB / WAS 서버를 이중화 구성하였고, 대용량 파일(동영상 파일 또는 데이터 분석을 위한 로우 파일)의 저장을 위해 Azure Files를 공유 볼륨으로 구성하여 VM에 Mount하였다. 처리하는 파일 개수가 증가함에 따라 응답시간에 대한 지연이 발생하였고, 원인 분석 결과는 많은 대용량 파일의 업로드 / 다운로드로 인한 WAS 서버의 리소스 사용량이 증가였다. Azure Files의 성능 지표에서는 요청에 대한 응답 병목은 발생하지 않았다. WAS 서버의 리소스 사용량 감소를 위한 방안으로 보안을 최대한 준수하면서도 비용 효율적인 방법을 고르시오. [4점]

1. WAS에 클라이언트 인증 서비스를 구성하여 인증된 클라이언트에게 Azure Files의 Access Key를 제공하여 직접 접근하여 사용하도록 한다.
2. WAS에 클라이언트 인증 서비스를 구성하여 인증된 클라이언트에게 Azure Files의 SAS (Shared access signature)를 제공하여 클라이언트에서 직접 접근하여 사용하도록 한다.
3. Azure Shared Disk를 생성하여 VM에 할당하여 사용한다.
4. WAS에 클라이언트 인증 서비스를 구성하여 인증된 클라이언트에게 Azure Blob Storage의 SAS (Shared access signature)를 제공하여 클라이언트에서 직접 접근하여 사용하도록 한다.
5. 대용량 파일 업로드/다운로드용 Azure Function을 추가로 생성하여 사용한다.

**(정답)** 4

**(해설)** 한번만 기록하고 시퀀스 액세스로 파일을 사용하는 워크로드의 경우 Azure Files보다 Azure Blob Storage가 더 최적화되어 있다. 또한, 인증된 클라이언트에 SAS를 제공하여 필요한 최소한의 권한 및 유효 기간 부여가 가능하다.

---

## 문항 6

VM 기반으로 구축된 웹 서비스를 운영하고 있다. 해당 서비스는 Azure Load Balancer로 이중화 구성이 되어 있다. 서비스에 장애가 발생하여 VM 서버 확인 결과 모든 서버에서 서비스 Port를 정상적으로 Listen 하고 있었다. 하지만 한 대의 서버에서 WAS가 Hang이 걸려 요청을 처리하지 못하는 상태임에도 불구하고 Azure Load Balancer는 요청을 장애가 발생한 서버로 전달하고 있다. 다음 제시된 보기 중 장애가 발생한 VM으로 트래픽 전달을 방지하기 위한 Azure Load Balancer 설정 중 변경해야 하는 항목과 내용이 올바른 것을 고르시오. [4점]

1. Health probe 설정에서 프로토콜 항목이 TCP인 경우 HTTP나 HTTPS로 변경 후 웹 서비스의 동작 확인 가능한 경로를 추가로 설정한다.
2. Load balancing rule 설정에서 Session persistence 설정이 되어 있는 경우 None으로 변경한다.
3. Health probe 설정에서 서비스의 비정상적인 상태를 빠르게 인지하기 위하여 확인 주기를 최소 주기로 설정한다.
4. Health probe 설정에서 프로토콜 항목이 HTTP나 HTTPS인 경우 정상 응답 HTTP 상태 코드 범위를 변경한다.
5. Load balancing rule 설정에서 Idle timeout 값을 10 이하로 변경한다.

**(정답)** 1

**(해설)** TCP로 상태를 모니터링하는 경우 웹 서비스의 비정상적인 동작 감지가 되지 않는다. TCP의 경우 단순 TCP 핸드셰이크 여부만을 체크한다.

---

## 문항 7

K 책임은 G 고객사의 클라우드 MSP를 수행하는 담당자이다. 디스크 변경 작업을 검토한 내용 중 잘못 설명된 보기를 고르시오. [3점]

1. VM에 데이터 디스크를 추가로 attach하기 위해서는 VM을 중지시키지 않고 구성이 가능하기 때문에 별도의 서비스 중단 시간을 고려하지 않고 작업을 진행할 수 있다.
2. 데이터 디스크를 동일한 유형의 더 큰 사이즈로 resize 하는 경우 VM을 중지시키지 않고 작업이 가능하여 별도의 서비스 중단 시간을 고려하지 않고 작업을 진행할 수 있다.
3. 데이터 디스크가 공유 디스크로 다수의 VM에 할당된 경우 사이즈 조정을 위해서는 모든 VM에서 detach 이후 진행을 해야 하기 때문에 서비스 중단 시간을 확보한 이후 작업을 진행할 수 있다.
4. VM에 attach되었지만 볼륨을 구성하지 않았던 데이터 디스크에 대한 삭제 요청 시에는 VM을 중지시키지 않고 detach가 가능하기 때문에 별도의 서비스 중단 시간을 고려하지 않고 작업을 진행할 수 있다.
5. 할당된 데이터 디스크의 사이즈의 축소를 요청하는 경우 용량 문제가 없다면 해당 데이터 디스크에서 직접 용량을 줄일 수 있으므로 서비스 중단 시간을 고려하지 않고 작업을 진행할 수 있다.

**(정답)** 5

**(해설)** 데이터 디스크의 사이즈를 직접 줄일 수 없다. 데이터 디스크의 사이즈를 축소하고자 하는 경우 신규 디스크를 추가한 후 기존 데이터를 신규 디스크에 복제 후 기존 데이터 디스크를 삭제하는 방식(마이그레이션)을 통해 진행해야 한다.

---

## 문항 8

Azure Public 클라우드와 On-premise간 전용선 연결 구성을 하려고 한다. 보기의 전용선 구축 전 고려해야 할 내용중 적절하지 않은 것을 고르시오. [4점]

1. Korea Central Region의 Azure ExpressRoute Circuit(Premium SKU)을 Japan EAST Region에 있는 구축된 Express Route Gateway와 연결 후 On-Premise와 Japan EAST Region의 VNET 간의 통신이 가능하다.
2. Korea Central Region의 Azure ExpressRoute Circuit(Standard SKU)을 Korea South Region에 있는 Express Route Gateway와 연결 후 On-Premise와 South Region의 VNET 간의 통신이 가능하다.
3. Korea Central Region의 Azure ExpressRoute Circuit과 연결된 On-Premise와 Korea South Region의 Azure ExpressRoute Circuit과 연결된 On-Premise는 서로 통신이 가능하므로 On-Premise 간 통신을 위해 별도의 전용회선 연결이 불필요하다.
4. Azure Express Route Circuit Private Peering과 Express Route Gateway 간에는 QoS 설정 기능이 없기 때문에 ExpressRoute Gateway에 여러 개의 VNET이 Peering되어 연결된 경우 하나의 VNET에서 전용선 대역폭을 모두 사용하여 다른 VNET에 영향을 끼치지 않도록 설계 시 고려가 필요하다.
5. Azure Express Route Circuit과 Azure Express Route Gateway를 통해 두 개의 VNET이 연결되어 있는 경우 Express Route Circuit 자체의 라우팅 기능을 통해 VNET 간 직접 통신이 가능하다.

**(정답)** 3

**(해설)** Circuit 만으로는 불가능하며 Global Reach를 추가 구성하여 사용해야 가능하다.

---

## 문항 9

B 사의 김선임은 Kubernetes 기반으로 구축된 홈쇼핑 서비스를 운영하고 있다. 조회용 API 서비스 로그를 확인해보니 간헐적으로 에러가 발생하였으며 원인을 추적한 결과 서비스의 기능 개선 및 오류 수정을 위한 배포 시 POD 시작/종료 시점에 에러가 발생하고 있었다. 조치사항으로 잘못된 것을 고르시오. [4점]

1. POD 종료 시 에러는 PreStop Hook를 설정하여 Graceful ShutDown을 통해 해결한다.
2. ReadinessProbe의 설정을 조정하여 서비스가 정상 기동 후에 K8S Service에 등록되도록 한다.
3. StartUpProbe를 활용하여 LivenessProbe와 ReadinessProbe가 서비스가 정상 기동 후에 동작하도록 한다.
4. Ingress 컨트롤러에서 Internal Error(500) 오류 발생 시 Retry를 적용하여 End-User 에러 발생 빈도를 현저히 감소시킬 수 있다.
5. Service Mesh를 사용하고 에러가 발생하는 서버에서 다른 Micro Service Pod의 조회 API를 호출하는 경우 Circuit Breaker의 Retry 설정을 확인하여 다른 Micro Service 배포 시 발생할 수 있는 에러를 줄일 수 있다.

**(정답)** 4

**(해설)** (4) Internal Error의 경우 Application 자체에 문제가 있는 경우이며, Retry로 해결되지 않는다. Bad Gateway의 경우에는 Retry로 개선이 가능할 수 있다.

---

## 문항 10

다음 제시된 보기 중 Azure Cache for Redis를 활용하는 예시로 잘못 설명된 보기를 고르시오. [3점]

1. DB에서 데이터를 빈번하게 조회하는 경우 DB에 부하를 주어 성능이 저하될 수 있으므로 해당 서비스를 데이터 캐시로 사용하여 애플리케이션 응답성을 높일 수 있다.
2. 해당 서비스를 세션 저장소로 사용하여 WAS 간 세션 클러스터링을 구성할 수 있다.
3. 애플리케이션이 비동기 처리를 해야 하나 별도의 Queue가 존재하지 않는 경우 해당 서비스를 활용하여 Queue 서비스를 대체할 수 있다.
4. 해당 서비스는 데이터를 메모리에만 저장하며, Ehcache와 같은 로컬 Cache보다 속도가 빠르므로 어플리케이션에서 데이터 캐시 사용 필요 시 성능 측면에서 해당 서비스를 우선적으로 사용해야 한다.
5. 해당 서비스는 Premium Tier 사용 시 Scale Up/Down뿐 아니라 Scale In/Out도 적용할 수 있어 부하 증가에 따라 유연하게 대응할 수 있다.

**(정답)** 4

**(해설)** (4) 로컬 Cache는 네트워크 구간을 거치지 않으므로 일반적으로 더 성능이 우수하다. 

---

## 문항 11

A 선임은 Kubernetes 환경의 SpringBoot 2.7.18 (JDK 8u441)로 구성된 Pod에 장애가 자주 발생하는 것을 조치하기 위해 투입되었다. Deployment.yaml 파일에서 수정되어야 할 부분을 찾아 Line Number를 작성하시오. [4점]

### [추가 확인 사안 및 제한]

장애가 발생 중인 Pod의 SpringBoot가 사용하는 Max Heap Memory size는 1GB 이다. 원인 파악 진행 중 POD 장애 시 Out Of Memory 관련 로그를 확인하였다. configmap과 service.yaml을 수정하지 않는 선에서 조치를 수행해야 한다.
| [Pod Describe]           | Line | [deployment.yaml]       |
| ------------------------ | ---- | ----------------------- |
| State: Waiting           | 1    | apiVersion: apps/v1     |
| Reason: CrashLoopBackOff | 2    | kind: Deployment        |
| Last State: Terminated   | 3    | metadata:               |
| Reason: OOMKilled        | 4    | name: backend           |
| Exit Code: 137           | 5    | spec:                   |
|                          | 6    | replicas: 2             |
|                          | 6    | selector:               |
| apiVersion: v1           | 8    | matchLabels: backend    |
| data:                    | 9    | template:               |
| JAVA_OPTIONS: -Xmx1g     | 10   | metadata:               |
| metadata:                | 11   | labels:                 |
| name: cm-backend         | 12   | app: backend            |
| namespace: default       | 13   | spec:                   |
|                          | 14   | containers:             |
| # service.yaml           | 15   | - name: backend         |
| apiVersion: v1           | 16   | image: backend:1.14.2   |
| metadata:                | 17   | imagePullPolicy: Always |
| name: svc-backend        | 18   | envFrom:                |
| namespace: default       | 19   | - configMapRef:         |
|                          | 20   | name: cm-backend        |
| ports:                   | 21   | resources:              |
| - name: http             | 22   | requests:               |
| port: 80                 | 23   | cpu: 500m               |
| protocol: TCP            | 24   | memory: 500Mi           |
| targetPort: 80           | 25   | limits:                 |
| selector:                | 26   | cpu: 500m               |
| app: backend             | 27   | memory: 500Mi           |

**[답안]**
---
**정답** 27
**(해설)** Limits.memory 사양을 지정한 힙사이즈보다 크게 설정해야 한다.

---

## 문항 12

아래 제시된 AzureRM Resource Provider를 사용하여 구성한 AKS Terraform 코드에 대해서 설명한 내용 중 잘못 설명한 것을 고르시오. [4 점]

### [Terraform tfvars 파일]

```hcl
AKSCluster = {
중략
...
default_node_pool = {
name = "np-default"
vm_size = "Standard_D2_v2"
zones = [1]
enable_auto_scaling = true
max_count = 5
min_count = 2
node_count = 2
kubelet_disk_type = "OS"
orchestrator_version = "1.31.7"
os_sku = "Ubuntu"
node_subnet_name = "sbn-aks"
type = "VirtualMachineScaleSets"
}
...
중략
}
```

1. default_node_pool은 추가적인 Pod Scheduling 요청이 발생하더라도, 최대 5개의 Node까지만 Scale-out이 가능하다.
2. 해당 AKS Cluster의 kubernetes version은 이미 수명 종료가 되어 상위 버전으로 업데이트가 필요하다.
3. 해당 default_node_pool은 단일 Zone으로 구성되어 있어 해당 Zone 장애 발생 시 해당 Cluster 상에서 구동되는 Application은 서비스 불가 상태에 빠질 수 있다.
4. 해당 AKS Cluster에는 OS가 Ubuntu인 Container 이미지만 배포가 가능하다.
5. AKS Cluster는 Pod 간 네트워크 통신을 제어할 수 있는 Network Policy로 calico를 사용한다.

**(정답)** 4

**(해설)** (4) os_sku에 설정될 수 있는 값은 AzureLinux, Ubuntu, Windows2019와 Windows2022이며, 해당 설정은 Node Pool에 공급되는 VM의 기본 OS에 관련된 것이며, 컨테이너의 OS와는 관계가 없다.

---

## 문항 13

아래와 같이 한 개의 Node Pool로 구성된 AKS 클러스터를 업그레이드하려고 한다. 업그레이드를 위해 제시된 작업 목록을 확인하여 작업해야 하는 순서를 답안에 맞게 순서대로 기재하시오. [4점]

| Node pool | Provisioning state O | Power state | O Node count | Mode   | Kubernetes version | Node size        |
| --------- | -------------------- | ----------- | ------------ | ------ | ------------------ | ---------------- |
| agentpool | Succeeded            | Running     | ☒ 3/3 ready  | System | 1.25.5             | Standard_D2as_v4 |

### [제약 조건]
- Node Pool 업그레이드시 서비스 영향도는 최소화되어야 한다. 무중단 또는 중단시간이 0에 가까워야 한다.
- 해당 클러스터는 Public이 아닌 Private 환경으로 구성되어 있다.
- 포탈에 접속하는 단말과 AKS를 제어하는 단말은 망분리에 따라 분리되어 있다.
- 개발, 사용자 테스팅, 통합 테스트, 운영 환경으로 각각 동일한 사이즈로 분리되어 구성되어 있다.
- 반복하는 작업을 위해서 매뉴얼 작업이