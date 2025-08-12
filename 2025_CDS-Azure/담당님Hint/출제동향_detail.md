

# 1. 프롬프트



## 프롬프트1

```

회사에서 Azure 관련으로 역량 시험이 있어.

대략적인 시험범위가 나와 있어서

준비를 해야 해.






```







# 2. 시험범위



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







## 변환 샘플



* **Azure Resource RBAC Policy: 관리그룹 및 구도에 계층형 구조에 따른 사용자권한 제어**

  * 링크 : (https://learn.microsoft.com/ko-kr/azure/role-based-access-control/scope-overview)

  - Key : 관리그룹→구독→RG→리소스 스코프 구분





## 변환 완료