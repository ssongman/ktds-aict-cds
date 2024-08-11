# ISMS 인증 주요 결함항목

Public Cloud 기반, ISMS 인증 대응.  
Cloud architecture 설계 관점에서 고려해야 할 항목은, **네트워크 / 시스템 / 데이터 보안** 등이 주요 고려 항목으로 보이며, **컴플라이언스** 영역은 간단한 언급이 필요할 것으로 보임.  
**물리 보안**의 경우, 기본 제공이므로 특별한 언급은 필요 없음.

- Azure 인증 관련 참고 문서: <https://www.skshieldus.com/download/files/download.do?o_fname=2023%20%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C%20%EB%B3%B4%EC%95%88%20%EA%B0%80%EC%9D%B4%EB%93%9C_%20Azure.pdf&r_fname=20221220170359688.pdf>

## Azure

| 범주             | 서비스/기능                                          | 설명                                                        |
|------------------|------------------------------------------------------|-------------------------------------------------------------|
| **네트워크 보안** | Virtual Network (VNet)                              | 네트워크 영역을 분리하고 사설 IP를 할당합니다.                 |
|                  | Azure Firewall                                      | VNet의 트래픽 필터링 및 보안을 강화합니다.                   |
|                  | Network Security Groups (NSGs)                      | VNet의 서브넷 및 리소스에 대한 네트워크 접근 제어를 제공합니다. |
|                  | Azure Bastion                                       | 퍼블릭 IP 없이 안전하게 VM에 RDP/SSH 접근을 제공합니다.        |
|                  | Application Gateway (WAF)                           | 웹 애플리케이션 방화벽을 통해 보안을 강화합니다.              |
|                  | Private Link                                        | 인터넷을 통해 노출되지 않고 VNet 내에서 Azure 서비스에 접근합니다. |
| **시스템 보안**   | Azure Active Directory (AAD)                        | 계정 접근 제어 및 다중 인증을 지원합니다.                    |
|                  | Azure Monitor                                       | 로그 수집, 애플리케이션 성능 모니터링 및 경고를 설정합니다.    |
|                  | Azure Security Center                               | 보안 상태 모니터링, 보안 정책 적용 및 위협 탐지를 제공합니다.  |
|                  | Azure Policy                                        | 리소스 구성 정책을 정의하고 준수를 모니터링합니다.             |
| **데이터 보안**   | Azure Key Vault                                     | 암호화 키 및 비밀을 안전하게 저장하고 관리합니다.             |
|                  | Azure Confidential Computing                         | 데이터 처리 시 보안성을 강화하여 비밀 유지를 지원합니다.       |
| **컴플라이언스**   | Azure Compliance Manager                             | ISO27001, PCI DSS, FISMA, FedRAMP 등 다양한 보안 표준을 지원합니다. |
|                  | Azure Policy                                        | 규정 준수 및 보안 정책을 관리합니다.                         |
| **물리 보안**     | Azure Data Center Security                           | 화재 감지 및 진압, 전원 이중화, 항온항습, 보안 가드, 물리적 출입 통제 등의 보안을 제공합니다. |

## AWS

| 범주             | 서비스/기능                                          | 설명                                                        |
|------------------|------------------------------------------------------|-------------------------------------------------------------|
| **네트워크 보안** | VPC (Virtual Private Cloud)                         | 네트워크 영역을 분리하고 사설 IP를 할당합니다.                 |
|                  | AWS WAF                                              | AWS 기반 웹 방화벽을 제공하여 웹 애플리케이션 방어합니다.      |
|                  | 보안 그룹                                           | VPC 인스턴스의 인바운드 및 아웃바운드 트래픽을 제어합니다.      |
|                  | VPC NACL (Network ACL)                              | VPC의 서브넷 간 트래픽을 제어하는 네트워크 ACL입니다.           |
|                  | VPC Flow Logs                                       | VPC 내의 모든 트래픽을 분석하여 가시성을 제공합니다.          |
|                  | Bastion Hosts/NAT                                    | Private Network에 접속하기 위한 Proxy 서버 및 NAT Gateway 제공 |
|                  | HTTPS/SSL/TLS                                       | 전송 구간 암호화 및 IPSEC VPN을 통한 터널링을 제공합니다.     |
| **시스템 보안**   | IAM (Identity and Access Management)                | AWS 계정에 대한 접근 제어 및 권한 관리를 제공하며 MFA를 지원합니다. |
|                  | CloudWatch Logs                                     | AWS 리소스 및 애플리케이션 모니터링 및 임계치 설정을 지원합니다. |
|                  | Trusted Advisor                                     | 비용, 가용성, 성능, 보안 측면의 감사 및 개선 사항을 안내합니다. |
|                  | Config/Config Rule                                  | AWS 리소스 구성 변경 내역 기록 및 변경 내역 검증, 대시보드 제공. |
| **데이터 보안**   | KMS (Key Management Service)                         | 암호키 생성, 제어, 사용을 용이하게 해주는 서비스입니다.       |
|                  | CloudHSM                                            | 위·변조 감시 가능한 암호키 저장 어플라이언스입니다.             |
| **컴플라이언스**   | CloudTrail                                          | 모든 API 요청들에 대한 신뢰성 있는 로그 기록을 제공합니다.     |
|                  | 컴플라이언스 프로그램                               | ISO27001, PCI DSS, FISMA, FedRAMP 등 다양한 보안 표준을 지원합니다. |
| **물리 보안**     | 보호설비                                            | 화재 감지 및 진압, 전원 이중화, 항온항습, 설비 관리, 매체 파기 등을 제공합니다. |
|                  | 물리적 출입 통제                                    | 영상 감시, 침입 탐지, 보안 가드, 2중 인증, 인솔자 통제, 권한 관리 등을 포함합니다. |
