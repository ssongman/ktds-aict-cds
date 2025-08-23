## 000 Sample Answer

- 고객 상황 분석

Z사는 NFT(Non-fungible-token) 기반의 마켓 플랫폼을 구축하려고 하며, 모든 시스템을 Public Cloud에 구축하고자 한다. 주요 요구사항은 비용 효율성, 글로벌 서비스 제공, MSA(마이크로서비스 아키텍처) 기반 시스템 구축, 높은 트래픽 대응 능력, 그리고 보안 인증(ISMS) 등이 있다.

- 아키텍처 설계 개요

이번 문제에서는 단일 리전으로 글로벌 서비스를 제공하기 위해 필요한 아키텍처를 설계하는 데 중점을 둡니다. 글로벌 사용자를 대상으로 하며, 서비스의 가용성과 확장성을 유지하기 위해 클라우드 네이티브 기술을 사용해야 한다. 

## 제안 아키텍처

### 1. 리전 및 네트워크 구성

#### 1.1. 가용 영역(AZ) 구성

Multi-AZ 아키텍처:
- 목표: 데이터 센터 장애 발생 시에도 서비스가 계속 운영되도록 보장.
- 설계:
  - 리전 내 가용 영역 배포: AKS 클러스터, 데이터베이스, 캐시 서버 등을 최소 2개 이상의 가용 영역에 분산 배치.
  - 예시:
    - Node Pool 1: 가용성 영역 1 (AZ1) – `Standard_D4_v5`
    - Node Pool 2: 가용성 영역 2 (AZ2) – `Standard_D4_v5`
    - Node Pool 3: 가용성 영역 3 (AZ3) – `Standard_D4_v5`

#### 1.2. 네트워크 구성

Virtual Network (VNet):
- 목표: 보안 및 통신 분리를 통해 서비스 간의 통신을 효율적으로 관리.
- 설계:
  - VNet: 모든 리소스를 연결하는 단일 VNet 구성, 필요 시 다른 VNet과 연결 가능.

서브넷 구성:
1. 퍼블릭 서브넷:
   - 목표: 외부 트래픽과 연결이 필요한 프론트엔드 및 API Gateway 배포.
   - 리소스 배포:
     - 프론트엔드 애플리케이션: SPA 또는 웹 서버
     - API Gateway: 외부 API 요청 처리
     - 로드 밸런서: 외부와의 연결을 관리하고 트래픽 분산
   - 보안: 퍼블릭 서브넷의 리소스는 인터넷에서 접근 가능, NSGs를 사용하여 트래픽 제어.

2. 프라이빗 서브넷:
   - 목표: 외부와 직접 연결되지 않아야 하는 백엔드 서비스, 데이터베이스, 캐시 서버 배포.
   - 리소스 배포:
     - 백엔드 서비스: 애플리케이션 서버, 마이크로서비스
     - 데이터베이스: Azure SQL Database, Cosmos DB
     - 캐시 서버: Azure Cache for Redis
   - 보안: 프라이빗 서브넷의 리소스는 인터넷과 직접 연결되지 않으며, NSGs를 설정하여 접근 제어.

3. 관리 서브넷:
   - 목표: 클러스터 및 애플리케이션 상태 모니터링, 로그 수집 및 관리 도구 배포.
   - 리소스 배포:
     - 로그 수집: Azure Monitor, Log Analytics
     - 모니터링 도구: Grafana, Prometheus
     - 백업 및 복구: Azure Backup
   - 보안: 관리 서브넷은 외부 접근 필요 없으며, 관리 도구만 접근 가능하도록 NSGs 설정.

네트워크 보안:
- Network Security Groups (NSGs):
  - 퍼블릭 서브넷에 대한 NSG 설정으로 허용된 IP 및 포트만 접근 가능.
  - 프라이빗 서브넷에 대한 NSG 설정으로 외부 접근 차단, 내부 트래픽만 허용.
- Azure Firewall:
  - VNet의 트래픽 필터링 및 보안 강화.
- Azure Bastion:
  - 관리 서브넷의 VM에 안전하게 접근, 퍼블릭 IP 사용하지 않고 RDP/SSH 접근.

서비스 간 통신:
- Service Endpoints: Azure Storage, SQL Database 등의 서비스에 대한 서비스 엔드포인트 설정.
- Private Link: 인터넷을 통해 노출되지 않고 VNet 내에서 직접 Azure 서비스에 접근.


### 2. 컴퓨팅 및 스토리지 구성

#### 2.1. 컴퓨팅 리소스

Kubernetes 클러스터:
- Node Group:
  - 서비스별 NodeGroup: 각 서비스(Market, Notification, Event, Metaverse, Admin)에 대해 별도의 NodeGroup을 설정하여 트래픽과 리소스 요구 사항을 분리합니다.
    - 예시:
      - Node Pool 1: Market 서비스용 – `Standard_D4_v5`
      - Node Pool 2: Notification 서비스용 – `Standard_D4_v5`
      - Node Pool 3: Event 서비스용 – `Standard_D4_v5`
      - Node Pool 4: Metaverse 서비스용 – `Standard_D4_v5`
      - Node Pool 5: Admin 서비스용 – `Standard_D4_v5`
  - 자동 확장(Auto-scaling):
    - VM Scale Sets (VMSS): NodePool의 자동 확장을 위해 VMSS를 사용하여 노드 수를 자동으로 조정합니다.
    - Cluster Autoscaler: 클러스터의 총 리소스를 자동으로 조절하여 높은 트래픽 상황에 맞게 노드를 추가하거나 제거합니다.

Namespace:
- 목표: 각 시스템의 리소스 및 네트워크 정책을 분리하여 관리합니다.
- 구성:
  - Namespace 1: Market
  - Namespace 2: Notification
  - Namespace 3: Event
  - Namespace 4: Metaverse
  - Namespace 5: Admin
- 정책: 네트워크 정책과 리소스 쿼터를 통해 각 네임스페이스 간의 자원 사용을 제한하고 보안을 강화합니다.

Pod:
- 설계: Stateless 애플리케이션으로 구성하여 장애 발생 시 빠르게 재시작 가능하도록 설정합니다.
  - 기능:
    - 자동 복구: Pod가 실패하면 Kubernetes가 자동으로 재시작합니다.
    - 재배포: 새로운 버전으로의 배포 시, 기존 Pod를 점진적으로 교체하여 무중단 서비스를 유지합니다.

#### 2.2. 스토리지 리소스

Blob Storage:
- 목표: 사용자 데이터(이미지, 동영상 등)와 NFT 관련 데이터를 안전하게 저장합니다.
- 설계:
  - Blob Storage 계정: Azure Blob Storage를 사용하여 대용량 비정형 데이터 저장.
  - 데이터 관리: 데이터를 지역적으로 분산하여 고가용성을 보장하고, 백업 및 복원 전략을 설정합니다.

Managed Database:
- 목표: 고가용성과 데이터 일관성을 보장합니다.
- 구성:
  - Azure SQL Database: 자동화된 백업, 고가용성, 성능 최적화 기능을 제공하는 관리형 관계형 데이터베이스.
  - Cosmos DB: 전 세계적으로 분산된 데이터베이스로 높은 성능과 낮은 지연 시간을 제공하며, 글로벌 애플리케이션에 적합합니다.
- 설계:
  - 백업 및 복구: 정기적인 자동 백업을 설정하고, 필요 시 데이터를 복구할 수 있는 복원 지점을 생성합니다.
  - 성능 모니터링: Azure Monitor와 같은 도구를 사용하여 데이터베이스 성능을 모니터링하고 조정합니다.


### 3. API 및 백엔드 구성

#### 3.1. API Gateway

Azure API Management:
- 목표: 글로벌 사용자에게 빠르고 안정적인 API 서비스를 제공하기 위해 Azure API Management를 사용합니다.
- 설계:
  - 엣지 노드: 전 세계 여러 지역에 위치한 엣지 노드를 통해 API 요청을 라우팅하여 사용자와의 연결 속도를 최적화합니다.
  - 트래픽 관리: API 호출의 부하 분산, 요청 및 응답 모니터링, SLA 관리 등을 지원합니다.
  - 보안: API 요청에 대한 인증 및 권한 부여를 설정하여 외부 공격으로부터 보호합니다.

CORS 설정:
- 목표: 프론트엔드와 백엔드 간의 안전한 통신을 보장합니다.
- 설계:
  - CORS 정책: Azure API Management에서 CORS 정책을 설정하여 특정 도메인만 API에 접근할 수 있도록 허용합니다.
  - 설정 예시:
    - 허용된 출처: `https://frontend.example.com`
    - 허용된 메서드: `GET`, `POST`, `PUT`, `DELETE`
    - 허용된 헤더: `Content-Type`, `Authorization`

#### 3.2. 백엔드 서비스

Spring Boot 기반 마이크로서비스:
- 목표: 각 기능을 독립적인 마이크로서비스로 모듈화하여 유연성과 확장성을 보장합니다.
- 설계:
  - 서비스 구성: 각 마이크로서비스는 Spring Boot를 사용하여 개발하며, RESTful API를 통해 상호작용합니다.
  - 독립 배포: 각 서비스는 독립적으로 배포 가능하며, 서비스 간 의존성을 최소화합니다.
  - Docker 이미지: 각 Spring Boot 애플리케이션을 Docker 이미지로 패키징하여 일관된 환경에서 실행합니다.

Azure Container Registry (ACR):
- 목표: Docker 이미지를 안전하게 저장하고 관리합니다.
- 설계:
  - 이미지 저장: ACR을 사용하여 Docker 이미지를 중앙에서 관리하고, Kubernetes 클러스터에서 이를 Pull하여 사용합니다.
  - 액세스 관리: ACR에 대한 액세스를 제어하고, 필요한 권한을 가진 사용자 및 서비스만 이미지에 접근할 수 있도록 설정합니다.

API별 캐시 적용:
- 목표: 자주 요청되는 데이터를 캐시하여 API 응답 속도를 향상시키고 서버 부하를 줄입니다.
- 설계:
  - Redis 캐시: Azure Cache for Redis를 사용하여 API 응답을 캐시합니다.
  - 캐시 정책:
    - TTL 설정: 자주 변경되지 않는 데이터의 경우 긴 TTL(Time-To-Live)을 설정하여 캐시의 유효성을 유지합니다.
    - 캐시 무효화: 데이터가 변경될 때 캐시를 무효화하여 최신 데이터를 보장합니다.
  - 구성:
    - 캐시 키: API 요청의 특정 파라미터를 사용하여 캐시 키를 생성합니다.
    - 캐시 저장소: Redis의 인메모리 저장소를 활용하여 빠른 데이터 접근을 제공합니다.

이와 같은 API 및 백엔드 구성은 글로벌 사용자에게 신속한 API 응답을 제공하고, 마이크로서비스 기반으로 유연한 개발 및 배포를 지원하며, 캐시를 활용하여 성능을 최적화합니다.

### 4. 트래픽 및 이벤트 관리

트래픽이 많은 이벤트 시나리오에 대응:
- 목표: 이벤트 처리 시스템을 통해 높은 트래픽을 효율적으로 분산시키고, 지연을 최소화하여 시스템의 성능과 안정성을 보장합니다.

#### 4.1. Kubernetes 기반 Kafka

설계:
- 목표: Kubernetes 클러스터 내에서 Kafka를 실행하여 컨테이너화된 환경에서도 데이터 스트리밍 및 처리 기능을 지원합니다.
- 구성:
  - Kafka StatefulSet: Kafka 브로커를 StatefulSet으로 배포하여 안정적인 상태 관리를 지원합니다.
  - Headless Service: Kafka의 파티션과 브로커 간의 통신을 위한 Headless Service를 설정하여 DNS 기반의 클러스터링을 지원합니다.
  - Persistent Volumes (PV): Kafka 데이터의 지속성을 보장하기 위해 Azure Managed Disks를 사용하여 PV를 설정합니다.
  - Zookeeper StatefulSet: Kafka 클러스터의 메타데이터를 관리하기 위한 Zookeeper를 StatefulSet으로 배포합니다.

고려 사항:
- 볼륨: Kafka의 로그와 데이터를 저장하기 위한 볼륨을 구성합니다. 높은 IOPS와 스루풋을 지원하는 Azure Managed Disk를 사용하는 것이 좋습니다.
- 파티셔닝: Kafka 토픽의 파티션 수를 적절히 설정하여 데이터 처리 성능을 최적화합니다. 파티션 수는 데이터의 트래픽 양과 처리량 요구에 따라 조절합니다.
- 리플리케이션: 데이터의 내결함성을 보장하기 위해 파티션의 리플리케이션을 설정합니다. 일반적으로 리플리케이션 팩터를 3으로 설정하여 데이터 손실을 방지합니다.

#### 4.2. Azure Managed Kafka (Azure Event Hubs for Kafka)

설계:
- 목표: Azure에서 관리되는 Kafka 호환 서비스인 Azure Event Hubs for Kafka를 활용하여 Kafka와 호환되는 이벤트 스트리밍 솔루션을 제공합니다.
- 구성:
  - Event Hubs Namespace: 이벤트 허브 네임스페이스를 생성하여 Kafka 클라이언트와 통신합니다.
  - Kafka Endpoint: Event Hubs에 Kafka 프로토콜을 사용하여 연결할 수 있는 Kafka 엔드포인트를 제공합니다.
  - 자동 스케일링: Event Hubs는 트래픽에 따라 자동으로 스케일링하여 높은 트래픽을 처리할 수 있습니다.
  - 데이터 보존: 데이터 보존 기간을 설정하여 이벤트 데이터를 장기적으로 저장할 수 있습니다.

고려 사항:
- 볼륨: Event Hubs는 자동으로 스케일링되며, 별도의 디스크 관리는 필요 없습니다.
- 파티셔닝: Event Hubs의 파티션 수를 설정하여 데이터 분산 및 처리 성능을 조절합니다.
- 모니터링 및 관리: Azure Monitor를 사용하여 Event Hubs의 성능 및 트래픽을 모니터링합니다.

이와 같은 트래픽 및 이벤트 관리 설계는 시스템의 확장성과 안정성을 보장하며, 고속 데이터 스트리밍과 대규모 이벤트 처리를 지원합니다.

### 5. 보안 및 인증

- IAM & RBAC: Azure의 IAM 기능을 활용하여 각 역할에 맞는 접근 권한을 정의하고, 관리자 시스템(Admin)은 특정 IP 대역에서만 접근 가능하도록 NSG(Network Security Group)를 설정
- 보안 인증: ISMS 인증을 위한 로깅, 접근 제어, 데이터 암호화 등을 구현
- SSL/TLS: 모든 통신에서 SSL/TLS 암호화를 적용하여 데이터의 기밀성을 보장

### 6. 비용 효율화 방안

- Auto-scaling: Kubernetes의 Auto-scaling을 활용하여 트래픽에 따라 리소스를 동적으로 조정
- 단기/장기 스토리지: Application 로그와 데이터를 단기 보관과 장기 보관으로 나누어 저장하며, 비용 최적화를 위해 고성능 스토리지는 단기 보관에, 저렴한 스토리지는 장기 보관에 활용

### 7. 운영 및 모니터링

- Logging: Azure Monitor와 Log Analytics를 통해 애플리케이션 및 인프라 로그를 실시간으로 수집하고 분석
- Alerting: 로그 분석을 통해 이상이 감지되면, SMS, 이메일, Slack 등을 통해 담당자에게 알림을 전송
- Azure Service Bus 통합

### 8. 아키텍처 구조도

,,,

