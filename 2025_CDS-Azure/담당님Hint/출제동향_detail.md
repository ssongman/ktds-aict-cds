



# 1. 시험범위



## Raw



**Azure Resource RBAC Policy: 관리그룹 및 구도에 계층형 구조에 따른 사용자권한 제어**
(https://learn.microsoft.com/ko-kr/azure/role-based-access-control/scope-overview)

- ●관리그룹→구독→RG→리소스 스코프 구분



**Azure Storage Account(Object Storage) Tier 별 특성**
(https://learn.microsoft.com/ko-kr/azure/storage/blobs/access-tiers-overview)

- ●접근 패턴 기준 Hot/Cool/Archive 티어링, 라이프사이클 정책으로 자동 전환

**Azure Storage Account Life Cycle Event 활용법: Event 처리를 위한 구성방법, 데이터 유지관리 등 자동화 기능에 대한 이해**
(https://learn.microsoft.com/ko-kr/azure/storage/blobs/lifecycle-management-overview)
(https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-event-overview)

- ●Lifecycle 정책+Event Grid로 업로드/삭제 후처리·보존 자동화 파이프라인 구성

**VNet 구성시 Inbound(LB), Outbound(NAT)구성방법과 기술구조/네트웍 흐름 이해**
(https://learn.microsoft.com/en-us/azure/nat-gateway/nat-gateway-design)

- ●Inbound는 Standard LB/AGW, Outbound는 NAT Gateway

**Saving Plan, Reserved Instance을 활용한 비용절감 방안 이해**
(https://learn.microsoft.com/ko-kr/azure/cost-management-billing/savings-plan/savings-plan-compute-overview)

**Azure Storage Account 특징과 차이**
(https://learn.microsoft.com/ko-kr/azure/storage/common/storage-introduction?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json)
(https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-feature-support-in-storage-accounts)

- ●GPv2 기본, 복제(ZRS/GRS)·성능(Premium/Standard)

**VMSS 특성에 대한 이해**
(https://learn.microsoft.com/ko-kr/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-orchestration-modes)

- ●Uniform=표준화, Flexible=유연성/이종; 업그레이드·헬스 정책

**DNS Resolver 구성법: AWS/Azure/Onpremise DNS동기화를 위한 구성과 필요한 Network 구성**
(https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-overview)
(https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-get-started-portal)

- ●Private Resolver In/Out 엔드포인트로 온프렘↔클라우드 포워딩 경로 표준화

**AKS Monitoring를 활용한 자원/Workload 모니터링 이해**
(https://learn.microsoft.com/ko-kr/azure/azure-monitor/autoscale/autoscale-overview)
(https://learn.microsoft.com/ko-kr/azure/azure-monitor/platform/monitor-azure-resource)

- ●Azure Monitor 기반 메트릭/오토스케일 연계, 수집 범위·보존기간으로 비용 제어

**Azure 기반 Messaging 구성법 및 필요로 하는 Azure 서비스**
(https://learn.microsoft.com/ko-kr/azure/messaging-services/)

- ●Event Grid(이벤트), Event Hubs(스트림), Service Bus(큐/명령)로 역할 분리

**AKS Autoscale 이해: POD, Node(Node Group)**
(https://learn.microsoft.com/ko-kr/azure/aks/cluster-autoscaler?tabs=azure-cli)
(https://kubernetes.io/ko/docs/tasks/run-application/horizontal-pod-autoscale/)

- ●HPA는 파드, CA는 노드

**AKS 설치 구성에 대한 이해: Ingress Controller, CNI, CSI (최근 업데이트 된 내용 확인 필요)**
(https://learn.microsoft.com/ko-kr/azure/aks/learn/quick-kubernetes-deploy-terraform?pivots=development-environment-azure-cli)
(https://learn.microsoft.com/ko-kr/azure/aks/concepts-network-cni-overview)
(https://learn.microsoft.com/ko-kr/azure/aks/concepts-network-ingress)
(https://learn.microsoft.com/ko-kr/azure/aks/concepts-storage)

- ●AGIC vs NGINX, Azure CNI/Overlay, CSI(Disk/Files)

**AKS PV/PVC 사용법 및 CSI구성에 따른 Azure Files 특성 이해**

- ●Stateful은 Disk, 공유는 Files; SC·접근경로·성능 특성 사전 숙지

**AKS Overlaynetwork 구성에 대한 이해: POD IP 할당과 특징**

- ●Overlay로 Pod CIDR 분리·서브넷 고갈 방지

**Github Action의 의 기술구조 이해(Trigger Event 등)**
(https://docs.github.com/ko/actions/reference/workflow-syntax-for-github-actions)

- ●트리거/잡/컨텍스트 이해, 재사용 워크플로로 표준화

**CICD 기본 개념**
(https://docs.github.com/ko/actions/how-tos/security-for-github-actions/security-guides/using-secrets-in-github-actions)

- ●시크릿은 OIDC/키없는 접근, 환경 승인·보호 브랜치로 변경 통제

**Azure RBAC 이해: Built in Role/Role Group 활용법**

- ●그룹 단위 할당

**Azure Loadbalancer 이해: 가용성, 분산처리 특징과 Coverage**
(https://learn.microsoft.com/ko-kr/azure/load-balancer/skus)

**AKS권한 관리 방식: K8S의 IAM처리 방식의 이해 Entra ID, Service Account 등 이해와 차이점**
(https://learn.microsoft.com/ko-kr/azure/aks/enable-authentication-microsoft-entra-id)

- ●Entra ID 연동

**Container 기본 개념 및 Dockerfile 이해**

- ●이미지 슬림화

**Support VM OS SKU 및 Migration 방법(제약사항)**
(https://learn.microsoft.com/en-us/azure/migrate/server-migrate-overview?view=migrate-classic)

**AKS 장애 대응:Node Not Ready,POD Pending 등 이슈 원인 파악 및 대응방법 이해**

**Azure Network의 암호화 방식 단답식**

**AKS의 이슈상황 원인과 대응방안 역량: POD Faile, FackOff, POD Schedule Design, Nodegroup scale in 시 고래해야할 POD Life Cycle 설정**

**용도에 따른 Azure Storage Account 선택**

- ●액세스 패턴·복제·성능·보안 요구 사항 확인하여 유형 설정

**RAG를 위한 저장소/DBMS Azure 서비스 선택**

- ●원천은 Blob/ADLS, 검색은 AI Search/pgvector/Cosmos 등 벡터 지원으로 매핑

**Azure Function Tier 특징이해와 선택(대용량 Batch를 위한 Function Tier)**
(https://learn.microsoft.com/ko-kr/azure/azure-functions/durable/)

- ●Durable/Consumption/Premium 특성 비교

**Azure Disk 관리 운영 상의 특징: 크기 조절방법 및 제약 사항, OS Reboot 필요 등**

- ●파일시스템 조건·재부팅 필요 여부 사전 확인

**Terraform 내용 이해**

**비용 최적화 방안: Saving Plan, RI, Size 조절, VM Schedule 방안에 대한 이해와 적용법**

**PV, PVC 운영상의 특징(Azure File)**

**Express Route 개념 및 SKU Tier 특징 이해**

**DNS Resolver 방법 및 개념**

**Istio Service Mesh 개념과 각 자원/서비스 용어와 이해**

- ●트래픽 정책

**AKS 성능 개선에 대한 이해**

- ●노드풀 분리

**Node Pool 개념 이해와 운영 방안 특징**

**CICD Pipeline 구성시 Credential관리 주의 사항에 대한 이해와 방법**

**Github Action의 기본구성 이해와 기본 Task명에 대한 이해**

**Storage의 암호화 방식에 대한 이해**

- ●Key vault 사용

**Azure Native 보안 서비스 이해**

- ●보안 서비스

**Azure Monitoring 서비스 활용시 비용적인 측면의 Log Data 관리 방법에 대한 이해**

- ●스토리지 보관 방안

**Migration From VMWare VM: 제약조건, 구성법 등**

**PV/PVC with Azure File 구성시 필요한 Network 설정**

**Data Platform 구축시 요구사항정의와 그에 따른 Cloud특징**

- ●서비스 아키텍처 정의

**구독 할당 및 관리에 대한 이해**

**Vnet Flow log 서비스 종류와 특징 이행**

**AKS with GPU 구성시, 자원을 효율적으로 사용하기 위한 방안**

- ●노드풀 분리







# 2. 변환 샘플



* **Azure Resource RBAC Policy: 관리그룹 및 구도에 계층형 구조에 따른 사용자권한 제어**

  * 링크 : (https://learn.microsoft.com/ko-kr/azure/role-based-access-control/scope-overview)

  - Key : 관리그룹→구독→RG→리소스 스코프 구분



# 3. 1차 변환





## 1) **Azure Resource RBAC Policy**
- **내용:** 관리그룹 및 구도에 계층형 구조에 따른 사용자권한 제어
- **링크:** https://learn.microsoft.com/ko-kr/azure/role-based-access-control/scope-overview
- **Key:** 관리그룹 → 구독 → RG → 리소스 스코프 구분  



## 2) **Azure Storage Account(Object Storage) Tier 별 특성**
- **내용:** 접근 패턴 기준 Hot / Cool / Archive 티어링, 라이프사이클 정책으로 자동 전환
- **링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/access-tiers-overview
- **Key:** 티어별 접근 패턴 최적화 및 자동 전환  



## 3) **Azure Storage Account Life Cycle Event 활용법**
- **내용:** Event 처리를 위한 구성방법, 데이터 유지관리 등 자동화 기능 이해
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/storage/blobs/lifecycle-management-overview
  - https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-event-overview
- **Key:** Lifecycle 정책 + Event Grid로 업로드/삭제 후처리 및 보존 자동화  



## 4) **VNet 구성시 Inbound(LB), Outbound(NAT) 구성방법과 흐름 이해**
- **내용:** Inbound/LB, Outbound/NAT 구성과 네트워크 흐름 설계
- **링크:** https://learn.microsoft.com/en-us/azure/nat-gateway/nat-gateway-design
- **Key:** Inbound=Standard LB/AGW, Outbound=NAT Gateway  



## 5) **Saving Plan, Reserved Instance을 활용한 비용절감 방안**
- **내용:** 장기 사용 계획 기반의 비용 절감 전략 이해
- **링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/savings-plan/savings-plan-compute-overview
- **Key:** Saving Plan / RI를 통한 할인, 유연한 자원 변경  





## 6) **Azure Storage Account 특징과 차이**
- **내용:** GPv2 기본, 복제(ZRS/GRS)·성능(Premium/Standard) 차이 이해
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/storage/common/storage-introduction?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&bc=%2Fazure%2Fstorage%2Fblobs%2Fbreadcrumb%2Ftoc.json
  - https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-feature-support-in-storage-accounts
- **Key:** 계정 유형, 복제 옵션, 성능 계층 특성 이해  



## 7) **VMSS 특성에 대한 이해**
- **내용:** Uniform=표준화, Flexible=유연성/이종 노드 구성 차이와 정책 이해
- **링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-orchestration-modes
- **Key:** 업그레이드·헬스 정책 및 구성 모드 차이  



## 8) **DNS Resolver 구성법**
- **내용:** AWS/Azure/Onpremise DNS 동기화를 위한 구성 및 네트워크 설계
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-overview
  - https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-get-started-portal
- **Key:** Private Resolver In/Out 엔드포인트로 온프렘↔클라우드 포워딩 경로 표준화  



## 9) **AKS Monitoring를 활용한 자원/Workload 모니터링 이해**
- **내용:** Azure Monitor 기반 자원/워크로드 메트릭 수집과 비용 제어
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/azure-monitor/autoscale/autoscale-overview
  - https://learn.microsoft.com/ko-kr/azure/azure-monitor/platform/monitor-azure-resource
- **Key:** 오토스케일 연계, 수집 범위·보존기간 설계  



## 10) **Azure 기반 Messaging 구성법**
- **내용:** 이벤트, 스트림, 큐/명령 기반 메시징 서비스 구성
- **링크:** https://learn.microsoft.com/ko-kr/azure/messaging-services/
- **Key:** Event Grid(이벤트), Event Hubs(스트림), Service Bus(큐/명령) 역할 분리  



## 11) **AKS Autoscale 이해**
- **내용:** POD 단위(HPA)와 Node 단위(CA) 오토스케일 동작 방식
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/aks/cluster-autoscaler?tabs=azure-cli
  - https://kubernetes.io/ko/docs/tasks/run-application/horizontal-pod-autoscale/
- **Key:** HPA=파드, CA=노드  



## 12) **AKS 설치 구성**
- **내용:** Ingress Controller, CNI, CSI 개념과 구성
- **링크:**
  - https://learn.microsoft.com/ko-kr/azure/aks/learn/quick-kubernetes-deploy-terraform?pivots=development-environment-azure-cli
  - https://learn.microsoft.com/ko-kr/azure/aks/concepts-network-cni-overview
  - https://learn.microsoft.com/ko-kr/azure/aks/concepts-network-ingress
  - https://learn.microsoft.com/ko-kr/azure/aks/concepts-storage
- **Key:** AGIC vs NGINX, Azure CNI/Overlay, CSI(Disk/Files)  



## 13) **AKS PV/PVC 사용법 및 Azure Files 특성**
- **내용:** Stateful=Disk, 공유=Files; SC·접근경로·성능 특성 사전 숙지
- **링크:** (없음)
- **Key:** 스토리지 클래스 및 접근 모드 선택  



## 14) **AKS Overlaynetwork 구성**
- **내용:** Pod CIDR 분리 및 서브넷 고갈 방지 설계
- **링크:** (없음)
- **Key:** Overlay 네트워크로 IP 관리 최적화  



## 15) **Github Action 기술구조 이해**
- **내용:** Trigger Event, Job, Context, 재사용 워크플로 구성 이해
- **링크:** https://docs.github.com/ko/actions/reference/workflow-syntax-for-github-actions
- **Key:** 표준화된 워크플로 구성 가능  



## 16) **CICD 기본 개념**
- **내용:** GitHub Actions 시크릿 관리, OIDC, 승인·보호 브랜치
- **링크:** https://docs.github.com/ko/actions/how-tos/security-for-github-actions/security-guides/using-secrets-in-github-actions
- **Key:** 안전한 시크릿 관리와 변경 통제  



## 17) **Azure RBAC 이해**
- **내용:** Built-in Role, Role Group 활용
- **링크:** (없음)
- **Key:** 그룹 단위 권한 할당  



## 18) **Azure Loadbalancer 이해**
- **내용:** 가용성, 분산처리 특징과 Coverage
- **링크:** https://learn.microsoft.com/ko-kr/azure/load-balancer/skus
- **Key:** SKU별 특성과 범위  



## 19) **AKS 권한 관리 방식**
- **내용:** K8S IAM 처리 방식과 Entra ID, Service Account 차이
- **링크:** https://learn.microsoft.com/ko-kr/azure/aks/enable-authentication-microsoft-entra-id
- **Key:** Entra ID 연동  



## 20) **Container 기본 개념 및 Dockerfile 이해**
- **내용:** 이미지 슬림화 및 빌드 최적화
- **링크:** (없음)
- **Key:** 효율적 컨테이너 이미지 작성  



## 21) **Support VM OS SKU 및 Migration 방법**
- **내용:** 지원되는 VM OS SKU와 마이그레이션 제약사항 이해
- **링크:** https://learn.microsoft.com/en-us/azure/migrate/server-migrate-overview?view=migrate-classic
- **Key:** OS 호환성 및 마이그레이션 절차 숙지  



## 22) **AKS 장애 대응**
- **내용:** Node Not Ready, Pod Pending 등 이슈 원인 파악 및 대응 방법
- **링크:** (없음)
- **Key:** 장애 유형별 진단 및 조치 방법  



## 23) **Azure Network의 암호화 방식**
- **내용:** 네트워크 암호화 방식 단답식 이해
- **링크:** (없음)
- **Key:** 암호화 기술 종류 및 적용 범위  



## 24) **AKS 이슈 상황 원인과 대응 방안**
- **내용:** Pod Fail, BackOff, Pod Scheduling 문제, Nodegroup Scale-in 시 Pod Life Cycle 고려사항
- **링크:** (없음)
- **Key:** 이슈 유형별 원인 분석과 해결 절차  



## 25) **용도에 따른 Azure Storage Account 선택**
- **내용:** 액세스 패턴, 복제, 성능, 보안 요구사항에 따른 스토리지 유형 결정
- **링크:** (없음)
- **Key:** 워크로드 특성 기반 스토리지 선택  



## 26) **RAG를 위한 저장소/DBMS Azure 서비스 선택**
- **내용:** 원천 데이터 저장, 검색 및 벡터 DB 매핑
- **링크:** (없음)
- **Key:** Blob/ADLS, AI Search, pgvector, Cosmos DB 활용  



## 27) **Azure Function Tier 특징 이해와 선택**
- **내용:** 대용량 Batch 작업을 위한 Function Tier 비교
- **링크:** https://learn.microsoft.com/ko-kr/azure/azure-functions/durable/
- **Key:** Durable / Consumption / Premium 특성 차이  



## 28) **Azure Disk 관리 운영 특징**
- **내용:** 크기 조절 방법 및 제약 사항, OS Reboot 필요 여부
- **링크:** (없음)
- **Key:** 파일시스템 조건과 재부팅 여부 사전 확인  



## 29) **Terraform 내용 이해**
- **내용:** Terraform 구성 및 IaC 개념 이해
- **링크:** (없음)
- **Key:** 선언형 인프라 관리  



## 30) **비용 최적화 방안**
- **내용:** Saving Plan, RI, VM Size 조절, VM Schedule 활용
- **링크:** (없음)
- **Key:** 비용 절감 전략 적용 방법  



## 31) **PV, PVC 운영 특징(Azure File)**
- **내용:** Azure File 기반 PV/PVC 동작 특성
- **링크:** (없음)
- **Key:** 공유 스토리지 특성 및 네트워크 요구사항  



## 32) **Express Route 개념 및 SKU Tier 특징**
- **내용:** 전용망 서비스와 SKU별 특성 이해
- **링크:** (없음)
- **Key:** 전용 회선 및 대역폭 옵션  



## 33) **DNS Resolver 방법 및 개념**
- **내용:** DNS 질의 처리 및 포워딩 구성 방법
- **링크:** (없음)
- **Key:** Private Resolver 활용  



## 34) **Istio Service Mesh 개념**
- **내용:** 각 자원/서비스 용어와 트래픽 정책 이해
- **링크:** (없음)
- **Key:** 서비스 간 통신 정책  



## 35) **AKS 성능 개선 이해**
- **내용:** 노드풀 분리와 자원 최적화
- **링크:** (없음)
- **Key:** 워크로드 분리 운영  



## 36) **Node Pool 개념 이해와 운영 방안**
- **내용:** Node Pool 구성 및 운영 전략
- **링크:** (없음)
- **Key:** 워크로드별 Pool 구성  



## 37) **CICD Pipeline 구성 시 Credential 관리 주의 사항**
- **내용:** 보안 강화를 위한 Credential 관리 방법
- **링크:** (없음)
- **Key:** 시크릿 저장소, 최소 권한 원칙 적용  



## 38) **Github Action 기본 구성 이해**
- **내용:** 기본 Task와 Workflow 구조 이해
- **링크:** (없음)
- **Key:** 이벤트 기반 자동화 구성  



## 39) **Storage의 암호화 방식 이해**
- **내용:** Key Vault를 활용한 스토리지 암호화
- **링크:** (없음)
- **Key:** 서버측 암호화, 고객관리 키  



## 40) **Azure Native 보안 서비스 이해**
- **내용:** Azure 내장 보안 서비스 개념 이해
- **링크:** (없음)
- **Key:** 위협 탐지, 방어 기능  



## 41) **Azure Monitoring 서비스 활용 시 비용 관리**
- **내용:** 로그 데이터 보관 및 비용 절감 방안
- **링크:** (없음)
- **Key:** 보존 기간, 스토리지 정책  



## 42) **Migration From VMWare VM**
- **내용:** 마이그레이션 제약조건과 구성 방법
- **링크:** (없음)
- **Key:** 네트워크·스토리지 호환성 검토  



## 43) **PV/PVC with Azure File 네트워크 설정**
- **내용:** Azure File 기반 PV/PVC 사용 시 필요한 네트워크 구성
- **링크:** (없음)
- **Key:** SMB 포트, 프라이빗 엔드포인트 설정  



## 44) **Data Platform 구축 시 요구사항 정의**
- **내용:** 서비스 아키텍처 및 클라우드 특성 정의
- **링크:** (없음)
- **Key:** 데이터 수집·저장·처리 설계  



## 45) **구독 할당 및 관리 이해**
- **내용:** 구독별 리소스 할당과 관리 체계 이해
- **링크:** (없음)
- **Key:** 거버넌스 구조 설계  



## 46) **VNet Flow log 서비스 종류와 특징**
- **내용:** Flow log 유형과 분석 방법
- **링크:** (없음)
- **Key:** NSG Flow Log, Traffic Analytics  



## 47) **AKS with GPU 구성**
- **내용:** GPU 노드풀 구성 및 자원 효율화 방안
- **링크:** (없음)
- **Key:** 전용 노드풀 운영  