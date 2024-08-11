다음은 Azure 클라우드 기반으로 MSA(Microservices Architecture) 아키텍처를 구축하기 위한 설계 방안에 대한 테스트 문제입니다. 이 테스트는 요구사항 정의, 시스템 용량 산정, 컨테이너 상세 설계 역량을 검증하며, 시스템 구축 및 운영 비용 절감을 위한 아키텍처 개선 요건을 포함하고 있습니다.

### 문제 설명

당신은 A회사에서 Azure 클라우드를 기반으로 MSA 아키텍처를 설계하고 구축해야 합니다. 이 프로젝트의 목표는 회사의 기존 모놀리식(단일체) 애플리케이션을 MSA로 전환하여 서비스의 유연성을 높이고, 확장성을 강화하며, 운영 비용을 최적화하는 것입니다.

#### **요구사항**
1. **비즈니스 요구사항**
   - 특정 서비스는 24/7 무중단 운영이 필요합니다.
   - 사용자 트래픽이 급증할 수 있는 특정 시간대(예: 월요일 오전 9시~12시)에 자동으로 확장 가능한 아키텍처가 필요합니다.
   - 새로운 기능은 독립적으로 배포 가능해야 하며, 롤백이 쉽게 이루어질 수 있어야 합니다.
   - 서비스 간 통신은 최소한의 레이턴시로 이루어져야 하며, 각 서비스의 독립성을 보장해야 합니다.

2. **기술 요구사항**
   - 각 서비스는 컨테이너로 패키징되어 Azure Kubernetes Service(AKS) 위에서 동작해야 합니다.
   - 서비스 간 통신은 Azure Service Bus 또는 Azure API Management를 통해 이루어져야 합니다.
   - Azure Monitor와 Azure Application Insights를 통해 서비스의 상태를 모니터링하고, 문제 발생 시 즉시 알림을 받을 수 있어야 합니다.
   - 서비스의 배포는 CI/CD 파이프라인(Azure DevOps 또는 GitHub Actions)을 통해 자동화되어야 합니다.

3. **비용 최적화 요구사항**
   - 시스템 구축 및 운영 비용 절감을 위해 서버리스 서비스(예: Azure Functions)와 비용 절감형 저장소(예: Azure Blob Storage, Azure SQL Serverless) 사용을 고려해야 합니다.
   - 피크 시간대를 제외하고는 최소한의 리소스만 사용하도록 설정해야 합니다.
   - 불필요한 데이터 전송 비용을 줄이기 위해 서비스의 데이터와 로직을 최대한 지역적으로 배치해야 합니다.

#### **시스템 용량 산정**
1. 예상되는 최대 동시 접속자는 10,000명이며, 평균 응답 시간은 200ms 이내여야 합니다.
2. 각 서비스는 평균적으로 2,000 TPS(Transactions Per Second)를 처리할 수 있어야 합니다.
3. 특정 서비스는 파일 업로드 기능을 제공하며, 하루에 10GB 이상의 파일이 업로드될 것으로 예상됩니다.

### 과제

1. **요구사항 정의 및 시스템 용량 산정**
   - 위에서 제공된 비즈니스 및 기술 요구사항을 바탕으로 시스템 용량을 산정하고, 각 서비스의 필요한 자원을 정의하세요.
   - 각 서비스별로 필요한 컨테이너 수, CPU 및 메모리 자원을 산정하고, 예상되는 비용을 계산하세요.
  
2. **컨테이너 상세 설계**
   - Azure Kubernetes Service(AKS)를 기반으로 각 서비스가 어떻게 배포될지 상세 설계를 작성하세요.
   - 각 서비스의 컨테이너 이미지를 빌드하고 배포하기 위한 CI/CD 파이프라인을 설계하세요.
   - 서비스 간 통신, 데이터 저장 및 읽기/쓰기를 위한 설계 방안을 제시하세요.

3. **비용 절감을 위한 아키텍처 개선 제안**
   - 비용 절감을 위해 어떤 Azure 서비스 및 기능을 활용할 수 있을지 제안하세요.
   - 피크 시간대를 고려한 자동 확장 및 축소 계획을 작성하세요.
   - 서버리스 아키텍처를 도입할 수 있는 부분을 식별하고, 이를 어떻게 구현할지 설명하세요.

### 평가 기준
- 요구사항 정의 및 시스템 용량 산정의 정확성
- 컨테이너 및 CI/CD 설계의 적합성
- 비용 절감을 위한 아키텍처 개선 방안의 현실성 및 효과성
- 설계의 유연성과 확장 가능성

이 문제는 설계 역량뿐만 아니라 Azure 클라우드 서비스의 이해도, 비용 최적화 전략, 그리고 실제 운영 환경에서의 문제 해결 능력을 평가하기 위해 고안되었습니다.