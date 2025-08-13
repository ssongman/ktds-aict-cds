# KICE CDS-Azure 예상문제 200문항



## 1. Azure 기본 서비스 & 거버넌스 (40문항)

### 문항 1
김선임은 A사의 Azure 환경에서 개발팀 구성원들에게 리소스 접근 권한을 부여하려고 한다. 개발자들은 VM을 시작/중지하고 로그를 확인할 수 있어야 하지만, VM 삭제나 네트워크 설정 변경은 불가능해야 한다. 다음 중 RBAC 최소 권한 원칙에 가장 적합한 방법은 무엇인가?

A. 개발팀 구성원들에게 구독 수준에서 Owner 역할을 부여한다.
B. 개발팀 구성원들에게 리소스 그룹 수준에서 Virtual Machine Contributor 역할을 부여한다.
C. 개발팀 구성원들에게 리소스 그룹 수준에서 Reader 역할과 VM 수준에서 Virtual Machine Operator 커스텀 역할을 부여한다.
D. 개발팀 구성원들에게 관리 그룹 수준에서 Contributor 역할을 부여한다.

**정답:** C
**해설:** A (틀림): Owner 역할은 모든 권한을 포함하므로 최소 권한 원칙에 위배됩니다. B (틀림): Virtual Machine Contributor는 VM 생성, 삭제, 수정이 모두 가능하므로 요구사항보다 과도한 권한입니다. C (정답): Reader 역할로 로그 확인이 가능하고, Virtual Machine Operator 커스텀 역할로 VM 시작/중지만 허용할 수 있어 최소 권한 원칙에 부합합니다. D (틀림): 관리 그룹 수준의 Contributor는 더 넓은 범위에 영향을 미치며, VM 삭제 권한도 포함됩니다.
**문제주제:** Azure RBAC 최소 권한 원칙 적용
**관련링크:** https://learn.microsoft.com/ko-kr/azure/role-based-access-control/overview
**난이도:** 중
**Top50:** O

### 문항 2
이책임은 B사의 Azure Policy를 구성하여 리소스 명명 규칙을 강제하려고 한다. 모든 Storage Account는 'st'로 시작하고 환경 코드(dev/prd)를 포함해야 한다. 다음 중 이 요구사항을 구현하는데 적절하지 않은 것은?

A. Policy Definition에서 "effect": "deny" 조건과 함께 "field": "name"에 대한 패턴 매칭을 사용한다.
B. Policy Assignment 시 Management Group 수준에 적용하여 모든 하위 구독에 상속되도록 한다.
C. Policy에서 "like" 연산자를 사용하여 "st*dev*" 또는 "st*prd*" 패턴을 검증한다.
D. 이미 생성된 Storage Account는 Policy 적용 후 자동으로 이름이 변경된다.

**정답:** D
**해설:** Azure Policy는 새로 생성되는 리소스에만 적용되며, 기존 리소스의 이름을 자동으로 변경하지 않습니다. 기존 리소스는 규정 미준수로 표시될 뿐입니다.
**문제주제:** Azure Policy 명명 규칙 강제
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/policy/concepts/definition-structure
**난이도:** 중
**Top50:** X

### 문항 3
송팀장은 C사의 Azure 구독 관리 체계를 설계하고 있다. 다음 중 Azure 구독과 관리 그룹에 대한 설명으로 맞는 것은?

A. 하나의 Azure 구독은 여러 개의 Azure AD 테넌트에 동시에 속할 수 있다.
B. 관리 그룹은 최대 6개 수준의 계층 구조를 가질 수 있으며, 루트 관리 그룹은 제외된다.
C. 구독 간 리소스 이동 시 대상 구독의 할당량이 초과되면 자동으로 할당량이 증가한다.
D. 관리 그룹에 적용된 RBAC 권한은 하위 구독에 자동으로 상속된다.

**정답:** D
**해설:** 관리 그룹의 RBAC 설정은 모든 하위 관리 그룹, 구독, 리소스 그룹, 리소스에 상속됩니다.
**문제주제:** Azure 구독 및 관리 그룹 계층 구조
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/management-groups/overview
**난이도:** 중
**Top50:** X

### 문항 4
장전임은 D사의 Azure 환경에서 리소스 태그 전략을 수립하고 있다. 다음 중 Azure 태그에 대한 설명으로 틀린 것은?

A. 태그는 최대 50개의 이름-값 쌍을 리소스에 적용할 수 있다.
B. 태그는 리소스 그룹에서 리소스로 자동 상속되지 않는다.
C. Azure Policy를 사용하여 특정 태그를 필수로 강제할 수 있다.
D. 태그 이름은 대소문자를 구분하며, 태그 값은 구분하지 않는다.

**정답:** D
**해설:** 태그 이름은 대소문자를 구분하지 않지만, 태그 값은 대소문자를 구분합니다.
**문제주제:** Azure 리소스 태그 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/tag-resources
**난이도:** 하
**Top50:** X

### 문항 5
김선임은 E사의 MSP 운영 중 고객의 VM이 예기치 않게 중지되는 문제를 조사하고 있다. 다음 중 VM 중지 원인을 파악하는데 가장 효과적인 방법은?

A. VM의 Performance Metrics를 확인한다.
B. Azure Activity Log에서 VM 관련 작업을 조회한다.
C. Network Watcher의 Connection Monitor를 확인한다.
D. Azure Advisor의 권장 사항을 검토한다.

**정답:** B
**해설:** Azure Activity Log는 누가, 언제, 어떤 작업을 수행했는지 기록하므로 VM 중지 원인 파악에 가장 효과적입니다.
**문제주제:** MSP 운영 중 문제 추적
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/essentials/activity-log
**난이도:** 중
**Top50:** O

### 문항 6
이책임은 F사의 Azure Blueprint를 구성하여 표준화된 환경을 배포하려고 한다. 다음 중 Blueprint에 포함할 수 없는 것은?

A. ARM 템플릿으로 정의된 리소스
B. Azure Policy 할당
C. RBAC 역할 할당
D. Azure DevOps 파이프라인 정의

**정답:** D
**해설:** Azure DevOps 파이프라인은 Blueprint와 별개의 서비스이며, Blueprint에 포함될 수 없습니다.
**문제주제:** Azure Blueprint 구성 요소
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/blueprints/overview
**난이도:** 중
**Top50:** X

### 문항 7
송팀장은 G사의 MSP 서비스를 제공하면서 여러 고객의 Azure 환경을 관리해야 한다. 다음 중 Azure Lighthouse를 사용하는 이점으로 적절하지 않은 것은?

A. 고객 테넌트에 로그인하지 않고 리소스를 관리할 수 있다.
B. 여러 고객의 리소스를 단일 포털 뷰에서 관리할 수 있다.
C. 고객의 모든 구독에 자동으로 전체 액세스 권한을 얻는다.
D. 위임된 권한에 대한 감사 로그를 제공한다.

**정답:** C
**해설:** Azure Lighthouse는 고객이 명시적으로 위임한 구독과 리소스에만 액세스 가능하며, 자동으로 전체 권한을 부여하지 않습니다.
**문제주제:** Azure Lighthouse MSP 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/lighthouse/overview
**난이도:** 상
**Top50:** O

### 문항 8
장전임은 H사의 Azure Cost Management를 통해 비용을 최적화하려고 한다. 개발 환경 VM들이 주말에도 실행되고 있어 불필요한 비용이 발생하고 있다. 다음 중 가장 효과적인 해결 방법은?

A. VM을 B-series(버스터블) 인스턴스로 변경한다.
B. Azure Automation을 사용하여 스케줄 기반 자동 시작/중지를 구성한다.
C. VM에 대해 3년 Reserved Instance를 구매한다.
D. VM 크기를 한 단계 낮춘다.

**정답:** B
**해설:** Azure Automation의 Start/Stop 솔루션으로 업무 시간 외 VM을 자동 중지하면 최대 75% 비용 절감이 가능합니다.
**문제주제:** Azure VM 비용 최적화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/automation/automation-solution-vm-management
**난이도:** 중
**Top50:** O

### 문항 9
김선임은 I사의 Azure Policy Initiative를 구성하고 있다. 다음 중 Policy Initiative(정책 집합)에 대한 설명으로 틀린 것은?

A. 여러 개의 Policy Definition을 그룹화하여 관리할 수 있다.
B. Initiative 내의 개별 정책을 선택적으로 활성화/비활성화할 수 있다.
C. 하나의 Initiative를 여러 범위에 할당할 수 있다.
D. Initiative에 매개변수를 정의하여 재사용성을 높일 수 있다.

**정답:** B
**해설:** Initiative 할당 시 포함된 모든 정책이 적용되며, 개별 정책을 선택적으로 비활성화할 수 없습니다.
**문제주제:** Azure Policy Initiative 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/policy/concepts/initiative-definition-structure
**난이도:** 중
**Top50:** X

### 문항 10
이책임은 J사의 Azure Managed Identity를 구성하고 있다. 다음 중 System-assigned Managed Identity에 대한 설명으로 맞는 것은?

A. 여러 리소스에서 동일한 Identity를 공유할 수 있다.
B. 리소스가 삭제되면 Identity도 자동으로 삭제된다.
C. 사용자가 직접 Service Principal을 생성해야 한다.
D. Identity 생성 후 다른 리소스로 이동할 수 있다.

**정답:** B
**해설:** System-assigned Identity는 리소스 수명 주기와 연결되어 리소스 삭제 시 자동 삭제됩니다.
**문제주제:** Managed Identity 유형별 특징
**관련링크:** https://learn.microsoft.com/ko-kr/azure/active-directory/managed-identities-azure-resources/overview
**난이도:** 중
**Top50:** O

### 문항 11
송팀장은 K사의 Azure 환경에서 Privileged Identity Management(PIM)를 구성하고 있다. 다음 중 PIM의 기능이 아닌 것은?

A. Just-in-Time 액세스 권한 부여
B. 권한 승격 시 승인 워크플로우
C. 자동으로 만료되는 시간 제한 할당
D. 리소스 수준 방화벽 규칙 관리

**정답:** D
**해설:** PIM은 ID 및 액세스 관리 도구이며, 네트워크 방화벽 규칙과는 무관합니다.
**문제주제:** Azure PIM 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/active-directory/privileged-identity-management/pim-configure
**난이도:** 중
**Top50:** X

### 문항 12
장전임은 L사의 MSP 운영 중 고객의 리소스가 예상치 못하게 삭제되는 문제를 방지하려고 한다. 다음 중 가장 효과적인 방법은?

A. 모든 사용자의 권한을 Reader로 제한한다.
B. 중요 리소스에 Delete Lock을 적용한다.
C. Azure Policy로 리소스 삭제를 차단한다.
D. Activity Log 알림만 설정한다.

**정답:** B
**해설:** Delete Lock은 권한이 있는 사용자도 실수로 리소스를 삭제하는 것을 방지하는 가장 효과적인 방법입니다.
**문제주제:** Azure 리소스 보호
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/lock-resources
**난이도:** 중
**Top50:** O

### 문항 13
김선임은 M사의 Azure Arc를 구성하여 하이브리드 환경을 관리하려고 한다. 다음 중 Azure Arc로 관리할 수 없는 것은?

A. 온프레미스 Windows Server
B. AWS EC2 Linux 인스턴스  
C. 온프레미스 Kubernetes 클러스터
D. Azure 네이티브 가상 머신

**정답:** D
**해설:** Azure 네이티브 VM은 이미 Azure에서 직접 관리되므로 Arc가 필요하지 않습니다.
**문제주제:** Azure Arc 적용 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-arc/overview
**난이도:** 중
**Top50:** X

### 문항 14
이책임은 N사의 Resource Graph를 사용하여 리소스를 쿼리하려고 한다. 다음 중 Resource Graph의 특징으로 틀린 것은?

A. KQL(Kusto Query Language)을 사용하여 쿼리를 작성한다.
B. 실시간으로 모든 리소스 변경 사항을 반영한다.
C. 여러 구독에 걸친 리소스를 한 번에 쿼리할 수 있다.
D. 쿼리 결과를 CSV나 JSON 형식으로 내보낼 수 있다.

**정답:** B
**해설:** Resource Graph는 준실시간으로 업데이트되며, 일반적으로 몇 분의 지연이 있습니다.
**문제주제:** Azure Resource Graph 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/resource-graph/overview
**난이도:** 중
**Top50:** X

### 문항 15
송팀장은 O사의 Azure Advisor 권장 사항을 검토하고 있다. 다음 중 Azure Advisor가 제공하지 않는 권장 사항 범주는?

A. 비용 최적화
B. 보안 강화
C. 성능 개선
D. 라이선스 컴플라이언스

**정답:** D
**해설:** Azure Advisor는 신뢰성, 보안, 성능, 비용, 운영 우수성 5개 범주만 제공하며, 라이선스 컴플라이언스는 별도 도구가 필요합니다.
**문제주제:** Azure Advisor 권장 사항 범주
**관련링크:** https://learn.microsoft.com/ko-kr/azure/advisor/advisor-overview
**난이도:** 하
**Top50:** X

### 문항 16
장전임은 P사의 MSP 운영 중 여러 고객의 Update Management를 중앙에서 관리하려고 한다. 다음 중 Update Management의 기능으로 적절한 것은?

A. Windows와 Linux VM의 OS 업데이트만 관리한다.
B. 온프레미스 서버의 업데이트도 관리할 수 있다.
C. 애플리케이션 업데이트를 자동으로 수행한다.
D. VM 재부팅 없이 모든 업데이트를 적용한다.

**정답:** B
**해설:** Azure Arc를 통해 온프레미스 서버의 업데이트 관리가 가능합니다.
**문제주제:** Azure Update Management 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/automation/update-management/overview
**난이도:** 중
**Top50:** X

### 문항 17
김선임은 Q사의 Azure Monitor를 구성하여 리소스 모니터링을 수행하려고 한다. 다음 중 Azure Monitor 메트릭에 대한 설명으로 틀린 것은?

A. 메트릭 데이터는 93일간 보관된다.
B. 1분 단위의 세분화된 데이터를 제공한다.
C. 실시간 스트리밍이 가능하다.
D. 모든 메트릭은 추가 비용 없이 수집된다.

**정답:** D
**해설:** 플랫폼 메트릭은 무료이지만, 사용자 지정 메트릭과 게스트 OS 메트릭은 추가 비용이 발생합니다.
**문제주제:** Azure Monitor 메트릭 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/essentials/data-platform-metrics
**난이도:** 중
**Top50:** X

### 문항 18
이책임은 R사의 Application Insights를 구성하고 있다. 다음 중 Application Insights가 자동으로 수집하지 않는 데이터는?

A. HTTP 요청 및 응답 시간
B. 예외 및 스택 추적
C. 데이터베이스 쿼리 성능
D. 사용자의 개인 식별 정보

**정답:** D
**해설:** GDPR 준수를 위해 PII(개인 식별 정보)는 기본적으로 수집하지 않으며, 명시적 구성이 필요합니다.
**문제주제:** Application Insights 데이터 수집
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/app/app-insights-overview
**난이도:** 중
**Top50:** X

### 문항 19
송팀장은 S사의 Azure Automation을 사용하여 작업을 자동화하려고 한다. 다음 중 Azure Automation Runbook 유형이 아닌 것은?

A. PowerShell
B. Python
C. JavaScript
D. Graphical PowerShell

**정답:** C
**해설:** JavaScript는 지원되지 않습니다. Azure Functions를 사용해야 합니다.
**문제주제:** Azure Automation Runbook 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/automation/automation-runbook-types
**난이도:** 하
**Top50:** X

### 문항 20
장전임은 T사의 Azure Sentinel(Microsoft Sentinel)을 구성하고 있다. 다음 중 Sentinel의 주요 기능이 아닌 것은?

A. 보안 정보 및 이벤트 관리(SIEM)
B. 보안 오케스트레이션 자동 응답(SOAR)
C. 위협 인텔리전스 통합
D. 네트워크 대역폭 최적화

**정답:** D
**해설:** Sentinel은 보안 솔루션이며, 네트워크 대역폭 최적화는 Azure Front Door나 CDN의 영역입니다.
**문제주제:** Microsoft Sentinel 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/sentinel/overview
**난이도:** 중
**Top50:** X

### 문항 21
김선임은 U사의 MSP 운영 중 고객 환경의 Service Health 이벤트를 모니터링하고 있다. 다음 중 Service Health에서 제공하지 않는 알림 유형은?

A. 계획된 유지 관리
B. 서비스 문제
C. 리소스 할당량 초과
D. 보안 권고

**정답:** C
**해설:** 할당량 초과는 Azure Monitor 메트릭 알림으로 처리되며, Service Health 범위가 아닙니다.
**문제주제:** Azure Service Health 알림 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/service-health/overview
**난이도:** 하
**Top50:** X

### 문항 22
이책임은 V사의 Azure 환경에서 Custom Role을 생성하려고 한다. 다음 중 Custom Role 정의에 포함되지 않는 요소는?

A. Actions - 허용할 작업 목록
B. NotActions - 제외할 작업 목록
C. Priority - 역할 우선순위
D. AssignableScopes - 할당 가능한 범위

**정답:** C
**해설:** Priority는 Custom Role 정의에 없는 속성입니다. Azure RBAC는 우선순위가 아닌 권한 누적 방식으로 작동합니다.
**문제주제:** Azure Custom Role 구성 요소
**관련링크:** https://learn.microsoft.com/ko-kr/azure/role-based-access-control/custom-roles
**난이도:** 중
**Top50:** X

### 문항 23
송팀장은 W사의 Azure 환경에서 비용 예산 알림을 설정하고 있다. 다음 중 Azure Budget에 대한 설명으로 맞는 것은?

A. 예산 초과 시 리소스가 자동으로 중지된다.
B. 예산 설정 시 크레딧은 자동으로 제외되어 계산된다.
C. 실시간으로 비용이 업데이트되어 즉시 알림이 발송된다.
D. 리소스 그룹 수준에서만 예산을 설정할 수 있다.

**정답:** B
**해설:** 예산 계산 시 Azure 크레딧은 자동으로 제외되어 실제 청구 금액 기준으로 계산됩니다.
**문제주제:** Azure Budget 설정
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/tutorial-acm-create-budgets
**난이도:** 중
**Top50:** O

### 문항 24
장전임은 X사의 MSP 서비스 운영 중 여러 고객의 규정 준수 상태를 관리해야 한다. 다음 중 Azure Policy의 Compliance 상태가 아닌 것은?

A. Compliant
B. Non-compliant
C. Conflicted
D. Exempt

**정답:** D
**해설:** Azure Policy의 규정 준수 상태는 Compliant, Non-compliant, Conflicted만 있으며, Exempt는 존재하지 않습니다.
**문제주제:** Azure Policy Compliance 상태
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/policy/how-to/get-compliance-data
**난이도:** 중
**Top50:** X

### 문항 25
김선임은 Y사의 Azure 환경에서 Management Group 구조를 설계하고 있다. 다음 중 Management Group에 대한 설명으로 맞는 것은?

A. 하나의 구독은 여러 Management Group에 동시에 속할 수 있다.
B. Root Management Group은 삭제하거나 이름을 변경할 수 있다.
C. Management Group 간 이동 시 하위 리소스의 권한이 자동으로 재설정된다.
D. 각 Azure AD 테넌트는 Root Management Group이라는 단일 최상위 관리 그룹을 가진다.

**정답:** D
**해설:** 모든 Azure AD 테넌트는 자동으로 생성되는 단일 Root Management Group을 가집니다.
**문제주제:** Azure Management Group 계층 구조
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/management-groups/overview
**난이도:** 중
**Top50:** X

### 문항 26
이책임은 Z사의 Azure 환경에서 리소스 잠금을 구성하려고 한다. 다음 중 ReadOnly 잠금이 적용된 리소스에서 가능한 작업은?

A. VM 재시작
B. Storage Account Access Key 재생성
C. 리소스 태그 추가
D. 리소스 속성 조회

**정답:** D
**해설:** 읽기 작업인 속성 조회는 ReadOnly 잠금에서도 허용됩니다.
**문제주제:** Azure 리소스 잠금 동작
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/lock-resources
**난이도:** 중
**Top50:** X

### 문항 27
송팀장은 AA사의 MSP 운영 중 고객의 VM 성능 문제를 조사하고 있다. 다음 중 VM 성능 분석에 가장 효과적인 도구는?

A. Azure Service Health
B. Azure Monitor VM Insights
C. Azure Advisor
D. Azure Cost Management

**정답:** B
**해설:** VM Insights는 VM의 성능, 종속성, 프로세스 등을 상세히 분석할 수 있는 전문 도구입니다.
**문제주제:** VM 성능 모니터링
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/vm/vminsights-overview
**난이도:** 중
**Top50:** O

### 문항 28
장전임은 AB사의 Azure 환경에서 Activity Log를 장기 보관하려고 한다. 다음 중 Activity Log 보관에 대한 설명으로 맞는 것은?

A. Activity Log는 기본적으로 90일간 보관된다.
B. Storage Account로 아카이브 시 무제한 보관이 가능하다.
C. Log Analytics로 전송 시 최대 30일만 보관된다.
D. Activity Log는 삭제할 수 없으며 영구 보관된다.

**정답:** B
**해설:** Activity Log를 Storage Account로 아카이브하면 보존 기간을 사용자가 정의할 수 있으며 무제한 보관이 가능합니다.
**문제주제:** Activity Log 보관 정책
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/essentials/activity-log
**난이도:** 중
**Top50:** X

### 문항 29
김선임은 AC사의 Azure 환경에서 비용 분석을 수행하고 있다. 다음 중 Azure Cost Analysis에서 사용할 수 없는 기능은?

A. 리소스별 비용 그룹화
B. 태그별 비용 필터링
C. 미래 비용 예측
D. 실시간 비용 알림

**정답:** D
**해설:** 비용 데이터는 8-24시간 지연되므로 실시간 알림은 불가능합니다.
**문제주제:** Azure Cost Analysis 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/quick-acm-cost-analysis
**난이도:** 중
**Top50:** X

### 문항 30
이책임은 AD사의 MSP 운영 중 고객의 구독 간 리소스 이동을 계획하고 있다. 다음 중 구독 간 이동이 불가능한 리소스는?

A. Virtual Machine
B. Storage Account
C. Azure Backup Recovery Services Vault (백업 데이터 포함)
D. Virtual Network

**정답:** C
**해설:** Recovery Services Vault는 백업 데이터가 있는 경우 구독 간 이동이 불가능합니다.
**문제주제:** Azure 리소스 이동 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/move-support-resources
**난이도:** 상
**Top50:** O

### 문항 31
송팀장은 AE사의 Azure 환경에서 Compliance Manager를 사용하여 규정 준수를 관리하려고 한다. 다음 중 Compliance Manager의 기능이 아닌 것은?

A. 규정 준수 점수 제공
B. 개선 작업 권장 사항 제시
C. 자동으로 비준수 리소스 수정
D. 규정 준수 보고서 생성

**정답:** C
**해설:** Compliance Manager는 권장 사항만 제공하며, 자동으로 리소스를 수정하지 않습니다.
**문제주제:** Azure Compliance Manager 기능
**관련링크:** https://learn.microsoft.com/ko-kr/microsoft-365/compliance/compliance-manager
**난이도:** 중
**Top50:** X

### 문항 32
장전임은 AF사의 Azure 환경에서 Defender for Cloud를 구성하고 있다. 다음 중 Defender for Cloud가 보호하지 않는 것은?

A. Azure VM
B. On-premises 서버
C. AWS EC2 인스턴스
D. 사용자 개인 디바이스

**정답:** D
**해설:** Defender for Cloud는 클라우드 워크로드 보호 플랫폼으로, 개인 디바이스는 보호 범위가 아닙니다.
**문제주제:** Defender for Cloud 보호 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/defender-for-cloud/defender-for-cloud-introduction
**난이도:** 중
**Top50:** X

### 문항 33
김선임은 AG사의 MSP 운영 중 여러 고객의 보안 점수를 개선하려고 한다. 다음 중 Azure Secure Score 개선에 도움이 되지 않는 것은?

A. MFA 활성화
B. Just-In-Time VM 액세스 구성
C. VM 크기 증가
D. Network Security Group 규칙 강화

**정답:** C
**해설:** VM 크기는 성능과 관련된 것으로 보안 점수와 무관합니다.
**문제주제:** Azure Secure Score 개선
**관련링크:** https://learn.microsoft.com/ko-kr/azure/defender-for-cloud/secure-score-security-controls
**난이도:** 중
**Top50:** X

### 문항 34
이책임은 AH사의 Azure 환경에서 Log Analytics Workspace를 구성하고 있다. 다음 중 Log Analytics의 특징으로 틀린 것은?

A. KQL을 사용하여 로그를 쿼리한다.
B. 여러 구독의 로그를 단일 Workspace에 수집할 수 있다.
C. 데이터는 기본적으로 무제한 보관된다.
D. 사용자 정의 로그 수집이 가능하다.

**정답:** C
**해설:** Log Analytics는 기본 30일 보관이며, 최대 730일까지 설정 가능합니다. 무제한은 아닙니다.
**문제주제:** Log Analytics Workspace 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/logs/log-analytics-workspace-overview
**난이도:** 중
**Top50:** X

### 문항 35
송팀장은 AI사의 Azure 환경에서 Azure Policy 예외 처리를 구성하려고 한다. 다음 중 Policy 예외 처리 방법으로 적절하지 않은 것은?

A. Policy Exemption 생성
B. Policy 효과를 Disabled로 설정
C. 특정 리소스를 Policy 범위에서 제외
D. Policy Definition 자체를 삭제

**정답:** D
**해설:** Policy Definition 삭제는 예외 처리가 아니라 정책 자체를 제거하는 것으로 부적절합니다.
**문제주제:** Azure Policy 예외 처리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/governance/policy/concepts/exemption-structure
**난이도:** 중
**Top50:** X

### 문항 36
장전임은 AJ사의 MSP 운영 중 고객의 Reserved Instance 구매를 검토하고 있다. 다음 중 Reserved Instance에 대한 설명으로 틀린 것은?

A. 1년 또는 3년 약정이 가능하다.
B. 선불 결제 시 추가 할인을 받을 수 있다.
C. 구매 후 크기 변경이 불가능하다.
D. 사용하지 않은 예약은 Exchange가 가능하다.

**정답:** C
**해설:** Reserved Instance는 Instance Size Flexibility 기능으로 동일 VM 시리즈 내에서 크기 변경이 가능합니다.
**문제주제:** Azure Reserved Instance 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/reservations/reserved-vm-instance-flexibility
**난이도:** 중
**Top50:** O

### 문항 37
김선임은 AK사의 Azure 환경에서 Azure Monitor Alert를 구성하고 있다. 다음 중 Alert Rule 구성 요소가 아닌 것은?

A. Target Resource
B. Signal
C. Criteria
D. Subscription ID

**정답:** D
**해설:** Alert Rule은 Target Resource, Signal, Criteria, Action Group으로 구성되며, Subscription ID는 구성 요소가 아닙니다.
**문제주제:** Azure Monitor Alert 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/alerts/alerts-overview
**난이도:** 중
**Top50:** X

### 문항 38
이책임은 AL사의 Azure 환경에서 Resource Health를 확인하고 있다. 다음 중 Resource Health 상태가 아닌 것은?

A. Available
B. Degraded
C. Unavailable
D. Deleted

**정답:** D
**해설:** Resource Health는 Available, Degraded, Unavailable, Unknown 상태만 표시하며, Deleted는 상태가 아닙니다.
**문제주제:** Azure Resource Health 상태
**관련링크:** https://learn.microsoft.com/ko-kr/azure/service-health/resource-health-overview
**난이도:** 하
**Top50:** X

### 문항 39
송팀장은 AM사의 MSP 운영 중 고객의 Azure 환경에 대한 Well-Architected Review를 수행하고 있다. 다음 중 Azure Well-Architected Framework의 기둥이 아닌 것은?

A. 비용 최적화
B. 운영 우수성
C. 성능 효율성
D. 데이터 거버넌스

**정답:** D
**해설:** Azure Well-Architected Framework는 비용 최적화, 운영 우수성, 성능 효율성, 신뢰성, 보안 5개 기둥으로 구성됩니다.
**문제주제:** Azure Well-Architected Framework
**관련링크:** https://learn.microsoft.com/ko-kr/azure/well-architected/
**난이도:** 중
**Top50:** X

### 문항 40
장전임은 AN사의 Azure 환경에서 Azure Migrate를 사용하여 온프레미스 서버를 평가하고 있다. 다음 중 Azure Migrate가 평가하지 않는 것은?

A. VM 적합성
B. 예상 비용
C. 종속성 매핑
D. 라이선스 유효성

**정답:** D
**해설:** Azure Migrate는 기술적 평가를 수행하며, 라이선스 유효성 검증은 범위가 아닙니다.
**문제주제:** Azure Migrate 평가 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/migrate/migrate-services-overview
**난이도:** 중
**Top50:** X

## 2. 스토리지 & 데이터 관리 (40문항)

### 문항 41
김선임은 A사의 Blob Storage에 7년간 보관해야 하는 감사 로그를 저장하려고 한다. 로그는 업로드 후 수정이나 삭제가 불가능해야 한다. 다음 중 가장 적절한 구성은?

A. Blob을 Hot 계층에 저장하고 Storage Account 방화벽으로 접근을 제한한다.
B. Blob을 Archive 계층에 저장하고 Time-based retention policy와 Legal hold를 설정한다.
C. Blob을 Cool 계층에 저장하고 Immutable blob storage의 Time-based retention을 7년으로 설정한다.
D. Blob을 Archive 계층에 저장하고 RBAC로 삭제 권한을 제거한다.

**정답:** C
**해설:** Cool 계층은 장기 보관과 간헐적 접근에 적합하며, Immutable storage의 Time-based retention으로 7년간 WORM(Write Once Read Many) 보장이 가능합니다.
**문제주제:** Blob Storage 불변성 정책 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/immutable-storage-overview
**난이도:** 중
**Top50:** O

### 문항 42
이책임은 B사의 Storage Account 비용 최적화를 담당하고 있다. 현재 Hot 계층에 저장된 데이터 중 30일 이상 접근하지 않은 파일을 Cool로, 180일 이상은 Archive로 자동 이동시키려 한다. 다음 중 틀린 설명은?

A. Lifecycle Management Policy를 구성하여 자동 계층 전환이 가능하다.
B. Archive 계층으로 이동된 데이터는 rehydration 없이 즉시 읽기가 가능하다.
C. 계층 전환 시 트랜잭션 비용이 발생하며, 조기 삭제 시 패널티가 있을 수 있다.
D. Policy는 Blob 유형, Prefix, Index 태그 등으로 필터링이 가능하다.

**정답:** B
**해설:** Archive 계층의 데이터는 오프라인 상태로, 읽기 전에 반드시 rehydration(Hot 또는 Cool로 복원) 과정이 필요합니다. 이 과정은 표준 우선순위로 최대 15시간이 소요됩니다.
**문제주제:** Storage Account Lifecycle Management
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/lifecycle-management-overview
**난이도:** 중
**Top50:** O

### 문항 43
송팀장은 C사의 MSP 운영 중 고객의 Storage Account가 실수로 삭제되는 것을 방지하려고 한다. 다음 중 가장 효과적인 방법은?

A. Storage Account에 Delete Lock 적용
B. Soft Delete 활성화
C. RBAC로 삭제 권한 제거
D. Private Endpoint만 사용

**정답:** A
**해설:** Delete Lock은 관리자 실수로 인한 Storage Account 삭제를 방지하는 가장 확실한 방법입니다. Soft Delete는 데이터 복구용입니다.
**문제주제:** Storage Account 보호
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/lock-account-resource
**난이도:** 중
**Top50:** O

### 문항 44
장전임은 D사의 Storage Account에서 대용량 파일 업로드 성능을 개선하려고 한다. 다음 중 가장 효과적인 방법은?

A. Storage Account를 Premium 성능 계층으로 업그레이드
B. AzCopy의 병렬 업로드 기능 사용
C. Storage Account 지역 변경
D. 방화벽 규칙 제거

**정답:** B
**해설:** AzCopy는 자동으로 병렬 업로드를 수행하며, 대용량 파일 전송에 최적화되어 있습니다. --parallel-level 매개변수로 동시 작업 수를 조정할 수 있습니다.
**문제주제:** Storage 업로드 성능 최적화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-use-azcopy-v10
**난이도:** 중
**Top50:** X

### 문항 45
김선임은 E사의 Azure Files를 구성하여 온프레미스와 파일을 동기화하려고 한다. 다음 중 Azure File Sync의 특징으로 틀린 것은?

A. 클라우드 계층화로 자주 사용하지 않는 파일을 클라우드에만 보관할 수 있다.
B. 여러 온프레미스 서버를 하나의 Azure File Share와 동기화할 수 있다.
C. Linux 서버에서도 File Sync Agent를 설치할 수 있다.
D. 오프라인 데이터 전송을 위해 Azure Data Box를 사용할 수 있다.

**정답:** C
**해설:** Azure File Sync Agent는 Windows Server에서만 지원되며, Linux는 지원하지 않습니다.
**문제주제:** Azure File Sync 제약사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/file-sync/file-sync-introduction
**난이도:** 중
**Top50:** X

### 문항 46
이책임은 F사의 Storage Account에 Private Endpoint를 구성하고 있다. 다음 중 Private Endpoint 구성 후에도 필요한 설정은?

A. Public network access를 완전히 비활성화
B. DNS 설정을 통한 이름 확인 구성
C. Storage Account 방화벽에서 모든 네트워크 차단
D. NSG에서 모든 아웃바운드 규칙 제거

**정답:** B
**해설:** Private Endpoint 사용 시 privatelink 도메인으로 DNS 확인이 필요하며, Private DNS Zone 또는 사용자 지정 DNS 설정이 필요합니다.
**문제주제:** Private Endpoint DNS 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-private-endpoints
**난이도:** 상
**Top50:** O

### 문항 47
송팀장은 G사의 MSP 운영 중 Storage Account의 비정상적인 액세스 패턴을 감지하려고 한다. 다음 중 가장 적절한 방법은?

A. Storage Analytics Logging 활성화
B. Microsoft Defender for Storage 활성화
C. Azure Monitor 메트릭만 확인
D. Activity Log만 모니터링

**정답:** B
**해설:** Microsoft Defender for Storage는 AI 기반으로 비정상적인 액세스 패턴과 잠재적 위협을 자동으로 감지합니다.
**문제주제:** Storage 보안 모니터링
**관련링크:** https://learn.microsoft.com/ko-kr/azure/defender-for-cloud/defender-for-storage-introduction
**난이도:** 중
**Top50:** X

### 문항 48
장전임은 H사의 Storage Account에서 실수로 삭제된 Blob을 복구하려고 한다. 다음 중 Soft Delete에 대한 설명으로 틀린 것은?

A. Container와 Blob 모두에 대해 Soft Delete를 설정할 수 있다.
B. 보존 기간은 1일에서 365일까지 설정 가능하다.
C. Soft Delete가 활성화되면 이전에 삭제된 데이터도 복구할 수 있다.
D. 삭제된 데이터도 보존 기간 동안 스토리지 비용이 발생한다.

**정답:** C
**해설:** Soft Delete는 활성화 이후에 삭제된 데이터만 보호하며, 이전에 삭제된 데이터는 복구할 수 없습니다.
**문제주제:** Blob Soft Delete 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/soft-delete-blob-overview
**난이도:** 중
**Top50:** X

### 문항 49
김선임은 I사의 Storage Account 간 데이터를 복사하려고 한다. 다음 중 Storage Account 간 복사에 사용할 수 없는 방법은?

A. AzCopy
B. Azure Data Factory
C. Storage Explorer
D. Azure File Sync

**정답:** D
**해설:** Azure File Sync는 온프레미스 Windows Server와 Azure Files 간 동기화용이며, Storage Account 간 복사에는 사용할 수 없습니다.
**문제주제:** Storage 데이터 복사 방법
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-choose-data-transfer-solution
**난이도:** 중
**Top50:** X

### 문항 50
이책임은 J사의 Storage Account에서 네트워크 제한을 구성하고 있다. 다음 중 Storage Account 방화벽 예외로 추가할 수 없는 것은?

A. 특정 Azure 서비스
B. 특정 가상 네트워크
C. 특정 공용 IP 주소 범위
D. 특정 사용자 계정

**정답:** D
**해설:** Storage Account 방화벽은 네트워크 수준 제어이며, 사용자 계정별 제한은 RBAC로 처리해야 합니다.
**문제주제:** Storage Account 네트워크 보안
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-network-security
**난이도:** 중
**Top50:** X

### 문항 51
송팀장은 K사의 MSP 운영 중 고객의 Storage Account 복제 전략을 검토하고 있다. 다음 중 지역 간 복제를 제공하지 않는 옵션은?

A. GRS (Geo-Redundant Storage)
B. RA-GRS (Read-Access Geo-Redundant Storage)
C. ZRS (Zone-Redundant Storage)
D. GZRS (Geo-Zone-Redundant Storage)

**정답:** C
**해설:** ZRS는 단일 지역 내 3개 가용성 영역에만 복제하며, 지역 간 복제는 제공하지 않습니다.
**문제주제:** Storage Account 복제 옵션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-redundancy
**난이도:** 중
**Top50:** O

### 문항 52
장전임은 L사의 Azure Managed Disk 성능을 최적화하려고 한다. 다음 중 Managed Disk 성능에 영향을 주지 않는 요소는?

A. Disk 크기
B. Disk 유형 (Premium SSD, Standard SSD, HDD)
C. VM 크기
D. Resource Group 이름

**정답:** D
**해설:** Resource Group 이름은 논리적 그룹핑일 뿐 성능에 영향을 주지 않습니다.
**문제주제:** Managed Disk 성능 요소
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/disks-types
**난이도:** 하
**Top50:** X

### 문항 53
김선임은 M사의 VM에 추가 데이터 디스크를 연결하려고 한다. 다음 중 데이터 디스크 연결에 대한 설명으로 틀린 것은?

A. VM이 실행 중인 상태에서도 데이터 디스크를 추가할 수 있다.
B. 하나의 데이터 디스크를 여러 VM에 동시에 연결할 수 있다.
C. VM 크기에 따라 연결 가능한 데이터 디스크 수가 제한된다.
D. 데이터 디스크를 제거해도 디스크 자체는 삭제되지 않는다.

**정답:** B
**해설:** 일반 Managed Disk는 한 번에 하나의 VM에만 연결 가능합니다. Shared Disk 기능을 활성화한 경우에만 여러 VM에 연결 가능합니다.
**문제주제:** VM 데이터 디스크 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/managed-disks-overview
**난이도:** 중
**Top50:** O

### 문항 54
이책임은 N사의 MSP 운영 중 고객의 디스크 암호화를 구성하고 있다. 다음 중 Azure Disk Encryption에 대한 설명으로 맞는 것은?

A. OS 디스크만 암호화 가능하다.
B. 암호화 후에는 VM 크기를 변경할 수 없다.
C. Key Vault와 VM이 같은 지역에 있어야 한다.
D. 암호화를 해제하면 데이터가 손실된다.

**정답:** C
**해설:** Azure Disk Encryption을 사용하려면 Key Vault와 VM이 동일한 Azure 지역 및 구독에 있어야 합니다.
**문제주제:** Azure Disk Encryption 요구사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/disk-encryption-overview
**난이도:** 중
**Top50:** X

### 문항 55
송팀장은 O사의 Storage Account에서 Anonymous 액세스를 허용해야 하는 컨테이너를 구성하고 있다. 다음 중 Public Access Level로 설정할 수 없는 것은?

A. Private (no anonymous access)
B. Blob (anonymous read access for blobs only)
C. Container (anonymous read access for containers and blobs)
D. Write (anonymous write access for blobs)

**정답:** D
**해설:** Anonymous 액세스는 읽기 전용이며, 쓰기 권한은 부여할 수 없습니다. 쓰기는 SAS 토큰이나 인증이 필요합니다.
**문제주제:** Blob Container 공용 액세스 수준
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/anonymous-read-access-configure
**난이도:** 중
**Top50:** X

### 문항 56
장전임은 P사의 Azure Files 성능을 개선하려고 한다. 다음 중 Azure Files 성능 향상에 도움이 되지 않는 것은?

A. Premium 파일 공유 사용
B. SMB Multichannel 활성화
C. 파일 공유 크기 증가
D. 파일 압축 활성화

**정답:** D
**해설:** Azure Files는 자체 압축 기능을 제공하지 않으며, 클라이언트 측 압축은 오히려 CPU 오버헤드로 성능을 저하시킬 수 있습니다.
**문제주제:** Azure Files 성능 최적화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/files/storage-files-scale-targets
**난이도:** 중
**Top50:** X

### 문항 57
김선임은 Q사의 MSP 운영 중 Storage Account의 액세스 키를 정기적으로 회전시키려고 한다. 다음 중 키 회전 시 고려사항으로 틀린 것은?

A. 두 개의 키를 번갈아 사용하여 무중단 회전이 가능하다.
B. Key Vault에 키를 저장하면 자동 회전을 구성할 수 있다.
C. 키 재생성 시 기존 SAS 토큰은 즉시 무효화된다.
D. Activity Log에서 키 재생성 작업을 추적할 수 있다.

**정답:** C
**해설:** Account SAS는 키 재생성 시 무효화되지만, Service SAS와 User Delegation SAS는 영향받지 않습니다.
**문제주제:** Storage Account 키 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-account-keys-manage
**난이도:** 상
**Top50:** X

### 문항 58
이책임은 R사의 Storage Account에서 Static Website 호스팅을 구성하려고 한다. 다음 중 Static Website 호스팅의 제약사항은?

A. HTTPS만 지원한다.
B. 사용자 정의 도메인을 사용할 수 없다.
C. 서버 측 스크립트를 실행할 수 없다.
D. 100MB 이상의 파일을 호스팅할 수 없다.

**정답:** C
**해설:** Static Website는 정적 콘텐츠만 제공하며, PHP, ASP.NET 등 서버 측 스크립트는 실행할 수 없습니다.
**문제주제:** Static Website 호스팅 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-static-website
**난이도:** 중
**Top50:** X

### 문항 59
송팀장은 S사의 대용량 데이터를 Azure로 마이그레이션하려고 한다. 100TB 데이터 전송에 가장 적합한 방법은?

A. AzCopy를 통한 인터넷 전송
B. Azure Data Box 사용
C. Storage Explorer를 통한 업로드
D. Azure Portal을 통한 업로드

**정답:** B
**해설:** 100TB 규모의 대용량 데이터는 Azure Data Box를 사용하여 오프라인으로 전송하는 것이 가장 효율적입니다.
**문제주제:** 대용량 데이터 마이그레이션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/databox/data-box-overview
**난이도:** 중
**Top50:** O

### 문항 60
장전임은 T사의 MSP 운영 중 Storage Account의 Event Grid 통합을 구성하고 있다. 다음 중 Storage Event Grid가 지원하지 않는 이벤트는?

A. Blob Created
B. Blob Deleted
C. Blob Accessed
D. Blob Renamed

**정답:** C
**해설:** Blob Accessed는 Event Grid 이벤트가 아닙니다. 액세스 로깅은 Storage Analytics나 진단 설정을 사용해야 합니다.
**문제주제:** Storage Event Grid 이벤트 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-event-overview
**난이도:** 중
**Top50:** X

### 문항 61
김선임은 U사의 Azure Table Storage를 Cosmos DB Table API로 마이그레이션하려고 한다. 다음 중 마이그레이션의 이점이 아닌 것은?

A. 전역 분산 지원
B. 자동 인덱싱
C. 더 낮은 비용
D. SLA 99.99% 보장

**정답:** C
**해설:** Cosmos DB는 더 많은 기능을 제공하지만 일반적으로 Table Storage보다 비용이 높습니다.
**문제주제:** Table Storage vs Cosmos DB
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cosmos-db/table/introduction
**난이도:** 중
**Top50:** X

### 문항 62
이책임은 V사의 Storage Account에서 Change Feed를 활성화하려고 한다. 다음 중 Change Feed에 대한 설명으로 틀린 것은?

A. Blob의 생성, 수정, 삭제 이벤트를 기록한다.
B. 실시간 스트리밍을 제공한다.
C. 장기간 보관이 가능하다.
D. 추가 비용이 발생한다.

**정답:** B
**해설:** Change Feed는 실시간이 아닌 정렬된 로그 기록을 제공합니다. 실시간 이벤트는 Event Grid를 사용해야 합니다.
**문제주제:** Blob Change Feed 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-change-feed
**난이도:** 상
**Top50:** X

### 문항 63
송팀장은 W사의 MSP 운영 중 고객의 Storage Account 성능 문제를 조사하고 있다. 다음 중 Storage Analytics Metrics에서 확인할 수 없는 것은?

A. 트랜잭션 수
B. 평균 지연 시간
C. 개별 파일 액세스 로그
D. 가용성 백분율

**정답:** C
**해설:** Storage Analytics Metrics는 집계된 메트릭만 제공하며, 개별 파일 액세스 로그는 Storage Analytics Logging을 활성화해야 합니다.
**문제주제:** Storage Analytics Metrics 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-analytics-metrics
**난이도:** 중
**Top50:** X

### 문항 64
장전임은 X사의 Azure NetApp Files를 구성하고 있다. 다음 중 Azure NetApp Files의 특징으로 틀린 것은?

A. NFS와 SMB 프로토콜을 모두 지원한다.
B. 온프레미스 NetApp과 데이터 복제가 가능하다.
C. 모든 VM 크기에서 사용 가능하다.
D. 서비스 수준을 온라인으로 변경할 수 있다.

**정답:** C
**해설:** Azure NetApp Files는 고성능이 필요한 워크로드용으로, 특정 VM 크기와 지역에서만 사용 가능합니다.
**문제주제:** Azure NetApp Files 제약사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-netapp-files/azure-netapp-files-introduction
**난이도:** 상
**Top50:** X

### 문항 65
김선임은 Y사의 Storage Account에서 Object Replication을 구성하려고 한다. 다음 중 Object Replication의 요구사항이 아닌 것은?

A. 원본과 대상 Storage Account에 Blob versioning이 활성화되어야 한다.
B. 원본과 대상 Storage Account가 같은 지역에 있어야 한다.
C. Change Feed가 원본 Storage Account에 활성화되어야 한다.
D. 원본과 대상이 Standard 또는 Premium 계정이어야 한다.

**정답:** B
**해설:** Object Replication은 지역 간 복제를 지원하며, 같은 지역에 있을 필요는 없습니다.
**문제주제:** Object Replication 요구사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/object-replication-overview
**난이도:** 상
**Top50:** X

### 문항 66
이책임은 Z사의 MSP 운영 중 고객의 Ultra Disk를 구성하고 있다. 다음 중 Ultra Disk의 특징으로 맞는 것은?

A. 모든 VM 시리즈에서 사용 가능하다.
B. IOPS와 처리량을 독립적으로 조정할 수 있다.
C. 가용성 집합과 함께 사용할 수 있다.
D. 무료 평가판으로 제공된다.

**정답:** B
**해설:** Ultra Disk는 IOPS와 처리량을 VM 재시작 없이 독립적으로 조정할 수 있는 유일한 디스크 유형입니다.
**문제주제:** Ultra Disk 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/disks-types#ultra-disks
**난이도:** 상
**Top50:** X

### 문항 67
송팀장은 AA사의 Storage Account에서 Hierarchical Namespace를 활성화하려고 한다. 다음 중 이 기능의 용도는?

A. Blob 계층화 자동화
B. Data Lake Storage Gen2 활성화
C. 네트워크 격리 구성
D. 암호화 강화

**정답:** B
**해설:** Hierarchical Namespace는 Azure Data Lake Storage Gen2를 활성화하여 빅데이터 분석 워크로드에 최적화된 파일 시스템을 제공합니다.
**문제주제:** Data Lake Storage Gen2
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/data-lake-storage-introduction
**난이도:** 중
**Top50:** X

### 문항 68
장전임은 AB사의 Premium Block Blob Storage를 구성하고 있다. 다음 중 Premium Block Blob의 제약사항은?

A. 지역 간 복제를 지원하지 않는다.
B. 100GB 이상의 파일을 저장할 수 없다.
C. Private Endpoint를 사용할 수 없다.
D. Change Feed를 활성화할 수 없다.

**정답:** A
**해설:** Premium Block Blob Storage는 LRS와 ZRS만 지원하며, GRS 같은 지역 간 복제는 지원하지 않습니다.
**문제주제:** Premium Block Blob 제약사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-performance-tiers
**난이도:** 중
**Top50:** X

### 문항 69
김선임은 AC사의 MSP 운영 중 고객의 Storage Account 보안을 강화하려고 한다. 다음 중 Storage Account 보안 Best Practice가 아닌 것은?

A. 공용 Blob 액세스 비활성화
B. HTTPS 전용 전송 강제
C. 모든 사용자에게 Storage Account Key 공유
D. Azure AD 인증 사용

**정답:** C
**해설:** Storage Account Key는 root 권한과 같으므로 최소한의 인원만 알아야 하며, 가능하면 Azure AD 인증을 사용해야 합니다.
**문제주제:** Storage Account 보안 Best Practice
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/security-recommendations
**난이도:** 하
**Top50:** O

### 문항 70
이책임은 AD사의 Azure Backup을 사용하여 Blob 백업을 구성하려고 한다. 다음 중 Azure Backup for Blobs의 특징으로 맞는 것은?

A. 다른 지역으로 백업 데이터를 복제한다.
B. 운영 백업으로 원본 Storage Account에 저장된다.
C. 백업 데이터는 별도 요금이 발생하지 않는다.
D. 최대 7일까지만 복원 가능하다.

**정답:** B
**해설:** Blob의 운영 백업은 원본 Storage Account에 저장되며, Point-in-time 복원을 제공합니다.
**문제주제:** Azure Backup for Blobs
**관련링크:** https://learn.microsoft.com/ko-kr/azure/backup/blob-backup-overview
**난이도:** 중
**Top50:** X

### 문항 71
송팀장은 AE사의 Storage Account에서 Encryption Scope를 구성하려고 한다. 다음 중 Encryption Scope의 용도는?

A. 네트워크 수준 암호화 강화
B. 컨테이너나 Blob별로 다른 암호화 키 사용
C. 암호화 알고리즘 변경
D. 암호화 비활성화

**정답:** B
**해설:** Encryption Scope를 사용하면 동일 Storage Account 내에서 컨테이너나 Blob별로 다른 암호화 키를 사용할 수 있습니다.
**문제주제:** Storage Encryption Scope
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-service-encryption
**난이도:** 상
**Top50:** X

### 문항 72
장전임은 AF사의 MSP 운영 중 고객의 File Share 스냅샷을 관리하고 있다. 다음 중 Azure Files 스냅샷에 대한 설명으로 틀린 것은?

A. 최대 200개의 스냅샷을 생성할 수 있다.
B. 스냅샷은 증분 방식으로 저장된다.
C. 스냅샷에서 개별 파일을 복원할 수 있다.
D. 스냅샷은 다른 Storage Account로 이동할 수 있다.

**정답:** D
**해설:** Azure Files 스냅샷은 해당 File Share에 종속되며, 다른 Storage Account로 직접 이동할 수 없습니다.
**문제주제:** Azure Files 스냅샷
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/files/storage-snapshots-files
**난이도:** 중
**Top50:** X

### 문항 73
김선임은 AG사의 Storage Account에서 WORM(Write Once Read Many) 정책을 구성하려고 한다. 다음 중 Immutable Storage 정책 유형이 아닌 것은?

A. Time-based retention policy
B. Legal hold
C. Encryption policy
D. Locked time-based retention policy

**정답:** C
**해설:** Immutable Storage는 Time-based retention과 Legal hold 두 가지 정책만 제공하며, Encryption은 별개의 기능입니다.
**문제주제:** Immutable Storage 정책 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/immutable-storage-overview
**난이도:** 중
**Top50:** X

### 문항 74
이책임은 AH사의 Storage Account 모니터링을 구성하고 있다. 다음 중 Storage Account 진단 설정으로 수집할 수 없는 데이터는?

A. 메트릭
B. 리소스 로그
C. 활동 로그
D. 게스트 OS 로그

**정답:** D
**해설:** 게스트 OS 로그는 VM 관련 로그이며, Storage Account와는 무관합니다.
**문제주제:** Storage Account 진단 설정
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/storage-monitor-storage-account
**난이도:** 중
**Top50:** X

### 문항 75
송팀장은 AI사의 MSP 운영 중 고객의 Storage Account 비용을 분석하고 있다. 다음 중 Storage 비용 구성 요소가 아닌 것은?

A. 저장된 데이터 용량
B. 트랜잭션 수
C. 데이터 전송(Egress)
D. CPU 사용량

**정답:** D
**해설:** Storage Account는 서버리스 서비스로 CPU 사용량은 비용 요소가 아닙니다.
**문제주제:** Storage Account 비용 구성
**관련링크:** https://azure.microsoft.com/ko-kr/pricing/details/storage/
**난이도:** 하
**Top50:** X

### 문항 76
장전임은 AJ사의 Azure Files에서 AD 인증을 구성하려고 한다. 다음 중 요구사항이 아닌 것은?

A. Storage Account가 AD 도메인에 조인되어야 한다.
B. 클라이언트가 AD 도메인에 조인되어야 한다.
C. Storage Account Key를 모든 사용자에게 배포해야 한다.
D. SMB 3.0 이상을 지원해야 한다.

**정답:** C
**해설:** AD 인증을 사용하면 Storage Account Key 없이 AD 자격 증명으로 접근하므로 키 배포가 불필요합니다.
**문제주제:** Azure Files AD 인증
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/files/storage-files-identity-auth-active-directory-enable
**난이도:** 상
**Top50:** X

### 문항 77
김선임은 AK사의 Storage Account에서 Lifecycle Management를 구성하고 있다. 다음 중 Lifecycle 규칙 조건으로 사용할 수 없는 것은?

A. Blob 생성 후 경과 일수
B. Blob 크기
C. Blob 유형
D. Blob 접두사

**정답:** B
**해설:** Lifecycle Management는 시간 기반 조건만 지원하며, 파일 크기 기반 규칙은 설정할 수 없습니다.
**문제주제:** Lifecycle Management 조건
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/lifecycle-management-overview
**난이도:** 중
**Top50:** X

### 문항 78
이책임은 AL사의 MSP 운영 중 고객의 Page Blob 사용 사례를 검토하고 있다. 다음 중 Page Blob의 일반적인 용도는?

A. 비디오 스트리밍
B. VM의 OS 및 데이터 디스크
C. 로그 파일 저장
D. 정적 웹사이트 호스팅

**정답:** B
**해설:** Page Blob은 512바이트 페이지의 랜덤 읽기/쓰기에 최적화되어 있어 VM 디스크로 사용됩니다.
**문제주제:** Page Blob 용도
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blobs-introduction
**난이도:** 중
**Top50:** X

### 문항 79
송팀장은 AM사의 Storage Account에서 Customer-managed Key를 구성하려고 한다. 다음 중 요구사항이 아닌 것은?

A. Key Vault가 같은 테넌트에 있어야 한다.
B. Key Vault와 Storage Account가 같은 지역에 있어야 한다.
C. Storage Account가 Premium 성능 계층이어야 한다.
D. Storage Account에 Identity가 할당되어야 한다.

**정답:** C
**해설:** Customer-managed Key는 Standard와 Premium 모든 성능 계층에서 사용 가능합니다.
**문제주제:** Customer-managed Key 요구사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/common/customer-managed-keys-overview
**난이도:** 중
**Top50:** X

### 문항 80
장전임은 AN사의 Azure Storage에서 SAS(Shared Access Signature)를 생성하려고 한다. 다음 중 User Delegation SAS의 장점이 아닌 것은?

A. Azure AD 자격 증명으로 서명된다.
B. Storage Account Key가 노출되지 않는다.
C. 최대 7일간 유효하다.
D. 무제한 유효 기간을 설정할 수 있다.

**정답:** D
**해설:** User Delegation SAS는 보안상 최대 7일의 유효 기간 제한이 있습니다.
**문제주제:** User Delegation SAS 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-user-delegation-sas-create-cli
**난이도:** 상
**Top50:** O

## 3. 네트워크 & 보안 (40문항)

### 문항 81
송팀장은 A사의 온프레미스 데이터센터와 Azure Korea Central Region을 ExpressRoute로 연결하려고 한다. 다음 중 ExpressRoute 구성에 대한 설명으로 맞는 것은?

A. ExpressRoute Standard SKU로 Korea Central과 Japan East Region의 VNET을 연결할 수 있다.
B. ExpressRoute Circuit만으로 서로 다른 온프레미스 위치 간 통신이 자동으로 가능하다.
C. ExpressRoute Premium SKU와 Global Reach를 사용하면 서로 다른 지역의 ExpressRoute 회선 간 통신이 가능하다.
D. ExpressRoute Gateway는 VNET 간 직접 라우팅을 제공한다.

**정답:** C
**해설:** Premium SKU는 글로벌 연결을 지원하며, Global Reach를 활성화하면 서로 다른 ExpressRoute 회선에 연결된 온프레미스 네트워크 간 통신이 가능합니다.
**문제주제:** ExpressRoute 연결 구성 및 제약사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/expressroute/expressroute-introduction
**난이도:** 상
**Top50:** O

### 문항 82
이책임은 B사의 Storage Account를 Private Endpoint로 보호하면서도 특정 파트너사 IP에서는 접근을 허용해야 한다. 다음 중 적절하지 않은 구성은?

A. Storage Account 방화벽에 파트너사 공인 IP 주소를 예외로 추가한다.
B. Private Endpoint 구성 후 "Allow trusted Microsoft services" 옵션을 활성화한다.
C. NSG를 Private Endpoint 서브넷에 적용하여 파트너사 IP만 허용한다.
D. Storage Account의 공용 네트워크 액세스를 "선택한 네트워크에서 사용"으로 설정한다.

**정답:** C
**해설:** Private Endpoint는 기본적으로 NSG 규칙을 우회합니다. NSG를 적용하려면 Private Endpoint Network Policy를 먼저 활성화해야 하며, 이 경우에도 외부 공인 IP 제어는 불가능합니다.
**문제주제:** Private Endpoint와 네트워크 보안 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/private-link/private-endpoint-overview
**난이도:** 상
**Top50:** X

### 문항 83
김선임은 C사의 MSP 운영 중 고객의 Azure Firewall을 구성하고 있다. 다음 중 Azure Firewall Premium SKU에서만 제공되는 기능은?

A. 네트워크 규칙
B. TLS 검사
C. NAT 규칙
D. 애플리케이션 규칙

**정답:** B
**해설:** TLS 검사는 Premium SKU에서만 제공되며, HTTPS 트래픽의 심층 패킷 검사를 가능하게 합니다.
**문제주제:** Azure Firewall SKU 기능 차이
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall/premium-features
**난이도:** 중
**Top50:** O

### 문항 84
장전임은 D사의 Azure Virtual Network에서 서브넷을 설계하고 있다. 다음 중 서브넷 설계 시 고려사항으로 틀린 것은?

A. Azure는 각 서브넷에서 처음 4개와 마지막 1개 IP를 예약한다.
B. GatewaySubnet은 최소 /29 크기가 필요하다.
C. 서브넷 간 트래픽은 기본적으로 차단된다.
D. AzureFirewallSubnet은 최소 /26 크기가 필요하다.

**정답:** C
**해설:** 동일 VNET 내 서브넷 간 트래픽은 기본적으로 허용되며, NSG로 제어해야 합니다.
**문제주제:** Azure 서브넷 설계 원칙
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/virtual-networks-faq
**난이도:** 중
**Top50:** O

### 문항 85
송팀장은 E사의 Application Gateway를 구성하고 있다. 다음 중 Application Gateway가 제공하지 않는 기능은?

A. SSL/TLS 종료
B. URL 경로 기반 라우팅
C. TCP 부하 분산
D. Web Application Firewall

**정답:** C
**해설:** Application Gateway는 Layer 7(HTTP/HTTPS) 부하 분산 장치로, TCP(Layer 4) 부하 분산은 Azure Load Balancer가 제공합니다.
**문제주제:** Application Gateway vs Load Balancer
**관련링크:** https://learn.microsoft.com/ko-kr/azure/application-gateway/overview
**난이도:** 중
**Top50:** O

### 문항 86
이책임은 F사의 MSP 운영 중 고객의 NSG(Network Security Group) 규칙을 최적화하고 있다. 다음 중 NSG 규칙 처리 순서에 대한 설명으로 맞는 것은?

A. 우선순위 번호가 높을수록 먼저 처리된다.
B. 우선순위 번호가 낮을수록 먼저 처리된다.
C. 인바운드 규칙이 아웃바운드 규칙보다 먼저 처리된다.
D. 허용 규칙이 거부 규칙보다 먼저 처리된다.

**정답:** B
**해설:** NSG 규칙은 우선순위 번호가 낮은 것부터 처리되며, 100-4096 범위를 사용합니다.
**문제주제:** NSG 규칙 처리 순서
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/network-security-groups-overview
**난이도:** 중
**Top50:** O

### 문항 87
김선임은 G사의 VPN Gateway를 구성하고 있다. 다음 중 VPN Gateway SKU 선택 시 고려사항으로 틀린 것은?

A. Basic SKU는 Point-to-Site를 지원하지 않는다.
B. VpnGw1-5는 Generation1과 Generation2가 있다.
C. SKU 변경 시 Gateway 재생성이 필요하다.
D. 모든 SKU가 Zone-redundant 배포를 지원한다.

**정답:** D
**해설:** Zone-redundant 배포는 AZ 접미사가 붙은 특정 SKU(VpnGw1AZ 등)에서만 지원됩니다.
**문제주제:** VPN Gateway SKU 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings
**난이도:** 중
**Top50:** X

### 문항 88
장전임은 H사의 Azure Bastion을 구성하려고 한다. 다음 중 Azure Bastion Basic SKU의 제약사항은?

A. RDP/SSH 연결 지원
B. 파일 전송 미지원
C. Azure Portal을 통한 접속
D. VM에 공용 IP 불필요

**정답:** B
**해설:** 파일 전송 기능은 Standard SKU부터 지원되며, Basic SKU는 연결만 가능합니다.
**문제주제:** Azure Bastion SKU 차이
**관련링크:** https://learn.microsoft.com/ko-kr/azure/bastion/bastion-overview
**난이도:** 중
**Top50:** X

### 문항 89
송팀장은 I사의 MSP 운영 중 고객의 Azure Front Door를 구성하고 있다. 다음 중 Front Door의 주요 기능이 아닌 것은?

A. 글로벌 HTTP 부하 분산
B. SSL 오프로드
C. VM 백업 관리
D. URL 재작성

**정답:** C
**해설:** Front Door는 글로벌 웹 애플리케이션 가속 및 부하 분산 서비스로, VM 백업과는 무관합니다.
**문제주제:** Azure Front Door 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/frontdoor/front-door-overview
**난이도:** 중
**Top50:** X

### 문항 90
이책임은 J사의 Azure DNS를 구성하고 있다. 다음 중 Azure DNS가 지원하지 않는 것은?

A. 도메인 이름 등록
B. DNS 호스팅
C. Private DNS Zone
D. Alias 레코드

**정답:** A
**해설:** Azure DNS는 DNS 호스팅 서비스로, 도메인 등록은 외부 등록업체를 통해야 합니다.
**문제주제:** Azure DNS 기능 및 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/dns/dns-overview
**난이도:** 중
**Top50:** X

### 문항 91
김선임은 K사의 Traffic Manager를 구성하여 글로벌 트래픽을 분산하려고 한다. 다음 중 Traffic Manager 라우팅 방법이 아닌 것은?

A. Priority
B. Weighted
C. Performance
D. Session Affinity

**정답:** D
**해설:** Traffic Manager는 DNS 기반 라우팅으로 Session Affinity를 제공하지 않습니다. Priority, Weighted, Performance, Geographic, MultiValue, Subnet이 지원됩니다.
**문제주제:** Traffic Manager 라우팅 방법
**관련링크:** https://learn.microsoft.com/ko-kr/azure/traffic-manager/traffic-manager-routing-methods
**난이도:** 중
**Top50:** O

### 문항 92
장전임은 L사의 MSP 운영 중 고객의 VNET Peering을 구성하고 있다. 다음 중 VNET Peering에 대한 설명으로 틀린 것은?

A. 다른 지역 간 VNET도 Peering 가능하다.
B. Peering된 VNET 간 전이적 라우팅이 자동으로 설정된다.
C. 다른 구독의 VNET과도 Peering 가능하다.
D. Peering 연결은 양방향으로 설정해야 한다.

**정답:** B
**해설:** VNET Peering은 전이적 라우팅을 자동으로 제공하지 않습니다. Hub-Spoke 토폴로지에서는 추가 라우팅 구성이 필요합니다.
**문제주제:** VNET Peering 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/virtual-network-peering-overview
**난이도:** 중
**Top50:** O

### 문항 93
송팀장은 M사의 Azure Key Vault를 구성하고 있다. 다음 중 Key Vault에서 관리할 수 없는 것은?

A. TLS/SSL 인증서
B. Storage Account 액세스 키
C. VM 로컬 관리자 암호
D. 데이터베이스 연결 문자열

**정답:** C
**해설:** VM 로컬 관리자 암호는 Key Vault가 아닌 VM 설정이나 Azure AD에서 관리됩니다.
**문제주제:** Azure Key Vault 관리 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/key-vault/general/overview
**난이도:** 중
**Top50:** O

### 문항 94
이책임은 N사의 Azure DDoS Protection을 구성하려고 한다. 다음 중 DDoS Protection Standard의 특징으로 틀린 것은?

A. 적응형 튜닝을 통한 자동 임계값 설정
B. 공격 중 실시간 완화
C. 모든 Azure 서비스 자동 보호
D. DDoS 공격 비용 보호

**정답:** C
**해설:** DDoS Protection Standard는 VNET에 연결된 리소스만 보호하며, 모든 Azure 서비스를 자동으로 보호하지는 않습니다.
**문제주제:** DDoS Protection Standard 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/ddos-protection/ddos-protection-overview
**난이도:** 중
**Top50:** X

### 문항 95
김선임은 O사의 MSP 운영 중 고객의 Network Watcher를 구성하고 있다. 다음 중 Network Watcher가 제공하지 않는 기능은?

A. 패킷 캡처
B. 연결 문제 해결
C. NSG 흐름 로그
D. 자동 네트워크 구성

**정답:** D
**해설:** Network Watcher는 모니터링 및 진단 도구로, 자동 네트워크 구성 기능은 제공하지 않습니다.
**문제주제:** Network Watcher 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/network-watcher/network-watcher-monitoring-overview
**난이도:** 중
**Top50:** X

### 문항 96
장전임은 P사의 Azure Virtual WAN을 구성하려고 한다. 다음 중 Virtual WAN의 이점이 아닌 것은?

A. 여러 VPN 연결 집계
B. ExpressRoute 연결 통합
C. 자동 허브 간 연결
D. 무료 데이터 전송

**정답:** D
**해설:** Virtual WAN도 일반적인 Azure 네트워크 요금이 적용되며, 무료 데이터 전송은 제공되지 않습니다.
**문제주제:** Azure Virtual WAN 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-wan/virtual-wan-about
**난이도:** 중
**Top50:** X

### 문항 97
송팀장은 Q사의 Azure Firewall Policy를 구성하고 있다. 다음 중 Firewall Policy의 장점이 아닌 것은?

A. 여러 Firewall 인스턴스에 적용 가능
B. 계층적 정책 구조 지원
C. 자동 위협 인텔리전스 업데이트
D. 무제한 규칙 생성

**정답:** D
**해설:** Firewall Policy도 규칙 수에 제한이 있으며, SKU에 따라 다릅니다.
**문제주제:** Azure Firewall Policy 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall/firewall-policy-overview
**난이도:** 중
**Top50:** X

### 문항 98
이책임은 R사의 MSP 운영 중 고객의 Service Endpoint를 구성하고 있다. 다음 중 Service Endpoint와 Private Endpoint의 차이점으로 맞는 것은?

A. Service Endpoint는 Private IP를 할당한다.
B. Private Endpoint는 인터넷 경로를 사용한다.
C. Service Endpoint는 Microsoft 백본 네트워크를 사용한다.
D. 두 기능은 동일하다.

**정답:** C
**해설:** Service Endpoint는 Microsoft 백본 네트워크를 통해 최적화된 경로를 제공하지만, Private IP는 할당하지 않습니다.
**문제주제:** Service Endpoint vs Private Endpoint
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/virtual-network-service-endpoints-overview
**난이도:** 상
**Top50:** O

### 문항 99
김선임은 S사의 Azure Load Balancer를 구성하고 있다. 다음 중 Standard Load Balancer에서만 지원되는 기능은?

A. 부하 분산 규칙
B. 가용성 영역
C. 상태 프로브
D. NAT 규칙

**정답:** B
**해설:** 가용성 영역 지원은 Standard SKU에서만 가능하며, Basic SKU는 지원하지 않습니다.
**문제주제:** Load Balancer SKU 차이
**관련링크:** https://learn.microsoft.com/ko-kr/azure/load-balancer/skus
**난이도:** 중
**Top50:** O

### 문항 100
장전임은 T사의 Azure NAT Gateway를 구성하려고 한다. 다음 중 NAT Gateway의 용도로 적절한 것은?

A. 인바운드 연결 부하 분산
B. 아웃바운드 연결 SNAT
C. VPN 연결 제공
D. DNS 확인

**정답:** B
**해설:** NAT Gateway는 아웃바운드 인터넷 연결을 위한 SNAT(Source Network Address Translation)를 제공합니다.
**문제주제:** Azure NAT Gateway 용도
**관련링크:** https://learn.microsoft.com/ko-kr/azure/nat-gateway/nat-overview
**난이도:** 중
**Top50:** X

### 문항 101
송팀장은 U사의 MSP 운영 중 고객의 Azure Private DNS Zone을 구성하고 있다. 다음 중 Private DNS Zone에 대한 설명으로 틀린 것은?

A. VNET 내에서만 이름 확인이 가능하다.
B. 자동 VM 호스트 이름 등록을 지원한다.
C. 인터넷에서 쿼리할 수 있다.
D. 여러 VNET에 연결할 수 있다.

**정답:** C
**해설:** Private DNS Zone은 VNET 내부에서만 확인 가능하며, 인터넷에서는 쿼리할 수 없습니다.
**문제주제:** Azure Private DNS Zone 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/dns/private-dns-overview
**난이도:** 중
**Top50:** X

### 문항 102
이책임은 V사의 Azure Route Table을 구성하고 있다. 다음 중 사용자 정의 경로(UDR)의 Next Hop 유형이 아닌 것은?

A. Virtual Network Gateway
B. Virtual Appliance
C. Internet
D. Storage Account

**정답:** D
**해설:** Storage Account는 Next Hop 유형이 아닙니다. 유효한 유형은 VirtualNetworkGateway, VnetLocal, Internet, VirtualAppliance, None입니다.
**문제주제:** User Defined Route Next Hop 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/virtual-networks-udr-overview
**난이도:** 중
**Top50:** X

### 문항 103
김선임은 W사의 Azure Firewall에서 DNAT 규칙을 구성하려고 한다. 다음 중 DNAT 규칙 구성 시 필요하지 않은 것은?

A. 대상 공용 IP
B. 변환된 주소
C. 변환된 포트
D. 원본 국가/지역

**정답:** D
**해설:** DNAT 규칙은 대상 주소/포트 변환을 위한 것으로, 원본 국가/지역은 필수 요소가 아닙니다.
**문제주제:** Azure Firewall DNAT 규칙
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall/tutorial-firewall-dnat
**난이도:** 중
**Top50:** X

### 문항 104
장전임은 X사의 MSP 운영 중 고객의 Azure WAF(Web Application Firewall)를 구성하고 있다. 다음 중 WAF가 방어할 수 없는 공격은?

A. SQL Injection
B. Cross-site Scripting
C. DDoS 볼륨 공격
D. Protocol Violations

**정답:** C
**해설:** WAF는 애플리케이션 계층(Layer 7) 공격을 방어하며, 대용량 DDoS 공격은 DDoS Protection이 필요합니다.
**문제주제:** Azure WAF 보호 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/web-application-firewall/overview
**난이도:** 중
**Top50:** X

### 문항 105
송팀장은 Y사의 Azure Virtual Network에서 IPv6를 구성하려고 한다. 다음 중 Azure IPv6 지원에 대한 설명으로 틀린 것은?

A. IPv4와 IPv6 듀얼 스택을 지원한다.
B. 모든 Azure 서비스가 IPv6를 지원한다.
C. IPv6 전용 VNET은 생성할 수 없다.
D. Standard Load Balancer는 IPv6를 지원한다.

**정답:** B
**해설:** 모든 Azure 서비스가 IPv6를 지원하는 것은 아니며, 지원 여부는 서비스별로 확인이 필요합니다.
**문제주제:** Azure IPv6 지원 현황
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/ip-services/ipv6-overview
**난이도:** 상
**Top50:** X

### 문항 106
이책임은 Z사의 Azure Firewall Manager를 구성하고 있다. 다음 중 Firewall Manager로 중앙 관리할 수 없는 것은?

A. Azure Firewall 정책
B. 타사 SECaaS 파트너 통합
C. Virtual WAN 보안 허브
D. 온프레미스 하드웨어 방화벽

**정답:** D
**해설:** 온프레미스 하드웨어 방화벽은 Azure Firewall Manager 범위 밖입니다.
**문제주제:** Azure Firewall Manager 관리 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall-manager/overview
**난이도:** 상
**Top50:** X

### 문항 107
김선임은 AA사의 MSP 운영 중 고객의 ExpressRoute Direct를 구성하려고 한다. 다음 중 ExpressRoute Direct의 특징으로 틀린 것은?

A. 100Gbps 연결을 지원한다.
B. 물리적 포트 쌍에 직접 연결한다.
C. 모든 ExpressRoute 위치에서 사용 가능하다.
D. MACsec 암호화를 지원한다.

**정답:** C
**해설:** ExpressRoute Direct는 선택된 피어링 위치에서만 사용 가능하며, 모든 위치에서 제공되지는 않습니다.
**문제주제:** ExpressRoute Direct 가용성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/expressroute/expressroute-erdirect-about
**난이도:** 상
**Top50:** X

### 문항 108
장전임은 AB사의 Azure Private Link Service를 구성하려고 한다. 다음 중 Private Link Service 구성 요구사항이 아닌 것은?

A. Standard Load Balancer
B. Backend Pool의 VM
C. Public IP 주소
D. NAT IP 구성

**정답:** C
**해설:** Private Link Service는 Private 연결을 위한 것으로 Public IP가 필수가 아닙니다.
**문제주제:** Private Link Service 요구사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/private-link/private-link-service-overview
**난이도:** 상
**Top50:** X

### 문항 109
송팀장은 AC사의 Azure Network Security Group에서 Application Security Group을 사용하려고 한다. 다음 중 ASG의 이점이 아닌 것은?

A. IP 주소 대신 논리적 그룹으로 규칙 정의
B. 규칙 관리 간소화
C. 다른 지역의 VM도 그룹화 가능
D. 동적 멤버십 관리

**정답:** C
**해설:** ASG는 같은 지역 내의 VM만 그룹화할 수 있습니다.
**문제주제:** Application Security Group 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/application-security-groups
**난이도:** 중
**Top50:** X

### 문항 110
이책임은 AD사의 MSP 운영 중 고객의 Azure Firewall에서 위협 인텔리전스를 구성하고 있다. 다음 중 위협 인텔리전스 모드가 아닌 것은?

A. Off
B. Alert only
C. Alert and deny
D. Deny only

**정답:** D
**해설:** 위협 인텔리전스는 Off, Alert only, Alert and deny 세 가지 모드만 제공합니다.
**문제주제:** Azure Firewall 위협 인텔리전스
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall/threat-intel
**난이도:** 중
**Top50:** X

### 문항 111
김선임은 AE사의 Azure CDN을 구성하려고 한다. 다음 중 Azure CDN이 제공하지 않는 기능은?

A. 정적 콘텐츠 캐싱
B. 동적 사이트 가속
C. 비디오 스트리밍 최적화
D. 데이터베이스 복제

**정답:** D
**해설:** CDN은 콘텐츠 전송 최적화 서비스로, 데이터베이스 복제는 제공하지 않습니다.
**문제주제:** Azure CDN 기능 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cdn/cdn-overview
**난이도:** 중
**Top50:** X

### 문항 112
장전임은 AF사의 Azure API Management를 구성하고 있다. 다음 중 API Management 계층 중 VNET 통합을 지원하지 않는 것은?

A. Developer
B. Basic
C. Standard
D. Premium

**정답:** B
**해설:** Basic 계층은 VNET 통합을 지원하지 않으며, Developer, Standard, Premium 계층에서만 가능합니다.
**문제주제:** API Management VNET 통합
**관련링크:** https://learn.microsoft.com/ko-kr/azure/api-management/api-management-features
**난이도:** 중
**Top50:** X

### 문항 113
송팀장은 AG사의 MSP 운영 중 고객의 Azure Bastion 네이티브 클라이언트를 구성하려고 한다. 다음 중 요구사항이 아닌 것은?

A. Standard SKU 이상
B. Azure CLI 또는 Azure PowerShell
C. VM에 공용 IP 할당
D. Azure AD 인증

**정답:** C
**해설:** Bastion의 핵심 이점은 VM에 공용 IP가 필요 없다는 것입니다.
**문제주제:** Azure Bastion 네이티브 클라이언트
**관련링크:** https://learn.microsoft.com/ko-kr/azure/bastion/native-client
**난이도:** 중
**Top50:** X

### 문항 114
이책임은 AH사의 Azure Route Server를 구성하려고 한다. 다음 중 Route Server의 용도로 적절한 것은?

A. 정적 라우팅 구성
B. NVA와 VNET 간 동적 라우팅
C. 인터넷 라우팅 최적화
D. DNS 라우팅

**정답:** B
**해설:** Route Server는 NVA(Network Virtual Appliance)와 Azure VNET 간 BGP를 사용한 동적 라우팅을 활성화합니다.
**문제주제:** Azure Route Server 용도
**관련링크:** https://learn.microsoft.com/ko-kr/azure/route-server/overview
**난이도:** 상
**Top50:** X

### 문항 115
김선임은 AI사의 Azure Firewall에서 Just-In-Time 액세스를 구성하려고 한다. 다음 중 JIT 액세스 구성 위치로 올바른 것은?

A. Azure Firewall
B. Microsoft Defender for Cloud
C. Network Security Group
D. Application Gateway

**정답:** B
**해설:** JIT VM 액세스는 Microsoft Defender for Cloud에서 구성하며, NSG 규칙을 자동으로 관리합니다.
**문제주제:** Just-In-Time VM 액세스
**관련링크:** https://learn.microsoft.com/ko-kr/azure/defender-for-cloud/just-in-time-access-usage
**난이도:** 중
**Top50:** X

### 문항 116
장전임은 AJ사의 MSP 운영 중 고객의 Azure Virtual Network TAP을 구성하려고 한다. 다음 중 Virtual Network TAP의 용도는?

A. 네트워크 트래픽 미러링
B. 네트워크 대역폭 증가
C. 네트워크 암호화
D. 네트워크 압축

**정답:** A
**해설:** Virtual Network TAP(Terminal Access Point)는 네트워크 트래픽을 모니터링 도구로 미러링하는 기능입니다.
**문제주제:** Virtual Network TAP 용도
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-network/virtual-network-tap-overview
**난이도:** 상
**Top50:** X

### 문항 117
송팀장은 AK사의 Azure에서 Hub-Spoke 네트워크 토폴로지를 설계하고 있다. 다음 중 Spoke VNET 간 통신을 위한 방법으로 적절하지 않은 것은?

A. Hub VNET에 NVA 배치
B. Hub VNET에 Azure Firewall 배치
C. Spoke 간 직접 Peering
D. Spoke 간 자동 전이 라우팅

**정답:** D
**해설:** VNET Peering은 전이 라우팅을 자동으로 제공하지 않으므로, Hub를 통한 라우팅 구성이 필요합니다.
**문제주제:** Hub-Spoke 네트워크 설계
**관련링크:** https://learn.microsoft.com/ko-kr/azure/architecture/reference-architectures/hybrid-networking/hub-spoke
**난이도:** 상
**Top50:** O

### 문항 118
이책임은 AL사의 Azure에서 강제 터널링을 구성하려고 한다. 다음 중 강제 터널링의 용도로 적절한 것은?

A. 모든 인터넷 트래픽을 온프레미스로 라우팅
B. VNET 간 트래픽 암호화
C. 트래픽 부하 분산
D. 대역폭 제한

**정답:** A
**해설:** 강제 터널링은 인터넷 바운드 트래픽을 검사나 감사를 위해 온프레미스로 강제 라우팅하는 기능입니다.
**문제주제:** Azure 강제 터널링
**관련링크:** https://learn.microsoft.com/ko-kr/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm
**난이도:** 상
**Top50:** X

### 문항 119
김선임은 AM사의 MSP 운영 중 고객의 Azure Firewall에서 SQL FQDN 필터링을 구성하려고 한다. 다음 중 요구사항은?

A. Basic SKU
B. Standard SKU
C. Premium SKU
D. 모든 SKU에서 가능

**정답:** C
**해설:** SQL FQDN 필터링은 Premium SKU에서만 지원되는 고급 기능입니다.
**문제주제:** Azure Firewall SQL FQDN 필터링
**관련링크:** https://learn.microsoft.com/ko-kr/azure/firewall/sql-fqdn-filtering
**난이도:** 상
**Top50:** X

### 문항 120
장전임은 AN사의 Azure에서 Private DNS Resolver를 구성하려고 한다. 다음 중 Private DNS Resolver의 구성 요소가 아닌 것은?

A. Inbound Endpoint
B. Outbound Endpoint
C. Forwarding Ruleset
D. Public Endpoint

**정답:** D
**해설:** Private DNS Resolver는 Inbound/Outbound Endpoint와 Forwarding Ruleset으로 구성되며, Public Endpoint는 없습니다.
**문제주제:** Azure Private DNS Resolver 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-overview
**난이도:** 상
**Top50:** O

## 4. AKS / Kubernetes (40문항)

### 문항 121
김선임은 A사의 AKS 클러스터에서 Pod 배포 중 간헐적으로 503 에러가 발생하는 것을 확인했다. 신규 Pod가 아직 준비되지 않았는데 트래픽을 받는 것이 원인이었다. 다음 중 가장 적절한 해결 방법은?

A. Pod의 resources.limits.memory를 증가시킨다.
B. Deployment의 ReadinessProbe를 구성하여 애플리케이션 준비 상태를 확인한다.
C. HPA(Horizontal Pod Autoscaler)의 임계값을 낮춘다.
D. Service의 sessionAffinity를 ClientIP로 설정한다.

**정답:** B
**해설:** ReadinessProbe는 Pod가 트래픽을 받을 준비가 되었는지 확인하며, 준비되지 않은 Pod는 Service Endpoint에서 제외됩니다.
**문제주제:** Kubernetes Pod 상태 프로브 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/developer-best-practices-pod-security
**난이도:** 중
**Top50:** O

### 문항 122
장전임은 B사의 AKS 클러스터 업그레이드를 계획하고 있다. 현재 1.28 버전을 1.30으로 업그레이드하려 한다. 다음 중 무중단 업그레이드를 위한 방법으로 틀린 것은?

A. Control Plane을 먼저 업그레이드한 후 Node Pool을 업그레이드한다.
B. PodDisruptionBudget을 설정하여 최소 가용 Pod 수를 보장한다.
C. 모든 Node Pool을 동시에 업그레이드하여 작업 시간을 단축한다.
D. Blue-Green 방식으로 새 Node Pool을 추가한 후 기존 Pool을 제거한다.

**정답:** C
**해설:** 모든 Node Pool 동시 업그레이드는 전체 워크로드가 동시에 재시작되어 서비스 중단을 유발합니다. 순차적 또는 Blue-Green 방식이 필요합니다.
**문제주제:** AKS 무중단 업그레이드 전략
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/upgrade-cluster
**난이도:** 상
**Top50:** O

### 문항 123
송팀장은 C사의 MSP 운영 중 고객의 AKS에서 Pod가 OOMKilled 상태가 되는 문제를 해결하려고 한다. 다음 중 가장 적절한 해결 방법은?

A. Node의 메모리를 증가시킨다.
B. Pod의 resources.limits.memory를 증가시킨다.
C. HPA의 targetMemoryUtilizationPercentage를 낮춘다.
D. Cluster Autoscaler를 활성화한다.

**정답:** B
**해설:** OOMKilled는 Pod가 메모리 제한을 초과했을 때 발생하므로, Pod의 메모리 제한을 증가시켜야 합니다.
**문제주제:** Kubernetes OOM 문제 해결
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/developer-best-practices-resource-management
**난이도:** 중
**Top50:** O

### 문항 124
이책임은 D사의 AKS에서 Ingress Controller를 구성하고 있다. 다음 중 NGINX Ingress Controller와 Application Gateway Ingress Controller(AGIC)의 차이점으로 틀린 것은?

A. AGIC는 Azure Application Gateway를 사용한다.
B. NGINX는 Pod로 실행된다.
C. AGIC는 WAF 기능을 제공할 수 있다.
D. NGINX는 SSL 종료를 지원하지 않는다.

**정답:** D
**해설:** NGINX Ingress Controller도 SSL/TLS 종료를 완벽하게 지원합니다.
**문제주제:** AKS Ingress Controller 비교
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/ingress-basic
**난이도:** 중
**Top50:** X

### 문항 125
김선임은 E사의 AKS에서 Pod Security Policy를 대체할 방법을 찾고 있다. 다음 중 권장되는 대안은?

A. Network Policy
B. Pod Security Standards with Azure Policy
C. RBAC만 사용
D. Service Mesh

**정답:** B
**해설:** Kubernetes 1.25부터 PSP가 제거되었으며, Pod Security Standards를 Azure Policy와 함께 사용하는 것이 권장됩니다.
**문제주제:** Pod Security 정책 마이그레이션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/use-pod-security-policies
**난이도:** 상
**Top50:** X

### 문항 126
장전임은 F사의 MSP 운영 중 고객의 AKS Node Pool을 구성하고 있다. 다음 중 System Node Pool의 특징으로 틀린 것은?

A. 최소 1개의 Node가 필요하다.
B. CoreDNS와 같은 시스템 Pod가 실행된다.
C. Windows Node를 사용할 수 있다.
D. Critical Add-on Pod가 우선 스케줄링된다.

**정답:** C
**해설:** System Node Pool은 Linux만 지원하며, Windows는 User Node Pool에서만 사용 가능합니다.
**문제주제:** AKS System Node Pool 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/use-system-pools
**난이도:** 중
**Top50:** X

### 문항 127
송팀장은 G사의 AKS에서 Cluster Autoscaler를 구성하려고 한다. 다음 중 Cluster Autoscaler의 동작 조건이 아닌 것은?

A. Pending 상태의 Pod가 있을 때 Scale Out
B. Node 사용률이 낮을 때 Scale In
C. HPA와 함께 사용 가능
D. Pod의 CPU 사용률이 높을 때 Node 추가

**정답:** D
**해설:** Cluster Autoscaler는 Pod 스케줄링 기반으로 동작하며, Pod의 CPU 사용률은 HPA의 트리거입니다.
**문제주제:** Cluster Autoscaler vs HPA
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/cluster-autoscaler
**난이도:** 중
**Top50:** O

### 문항 128
이책임은 H사의 AKS에서 Azure CNI를 구성하고 있다. 다음 중 Azure CNI와 Kubenet의 차이점으로 맞는 것은?

A. Kubenet은 Pod에 VNET IP를 직접 할당한다.
B. Azure CNI는 네트워크 성능이 더 좋다.
C. Kubenet은 Network Policy를 지원하지 않는다.
D. Azure CNI는 IP 주소를 절약할 수 있다.

**정답:** B
**해설:** Azure CNI는 Pod에 VNET IP를 직접 할당하여 네트워크 성능이 더 좋지만, IP 주소를 더 많이 사용합니다.
**문제주제:** Azure CNI vs Kubenet
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/configure-azure-cni
**난이도:** 중
**Top50:** O

### 문항 129
김선임은 I사의 MSP 운영 중 고객의 AKS에서 Persistent Volume을 구성하고 있다. 다음 중 Azure Disk와 Azure Files의 차이점으로 틀린 것은?

A. Azure Disk는 단일 Pod에만 마운트 가능하다.
B. Azure Files는 여러 Pod에서 동시 읽기/쓰기가 가능하다.
C. Azure Disk가 일반적으로 성능이 더 좋다.
D. Azure Files는 Premium 성능을 지원하지 않는다.

**정답:** D
**해설:** Azure Files도 Premium 성능 계층을 지원하며, NFS와 SMB 프로토콜 모두 사용 가능합니다.
**문제주제:** AKS Persistent Storage 옵션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/concepts-storage
**난이도:** 중
**Top50:** X

### 문항 130
장전임은 J사의 AKS에서 Pod Identity를 구성하려고 한다. 다음 중 권장되는 방법은?

A. Service Principal을 Secret에 저장
B. Managed Identity 사용
C. Storage Account Key 하드코딩
D. 개발자 개인 계정 사용

**정답:** B
**해설:** Workload Identity(Managed Identity)를 사용하면 자격 증명 관리 없이 안전하게 Azure 리소스에 액세스할 수 있습니다.
**문제주제:** AKS Pod Identity Best Practice
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/workload-identity-overview
**난이도:** 중
**Top50:** O

### 문항 131
송팀장은 K사의 AKS에서 Container Insights를 구성하고 있다. 다음 중 Container Insights가 수집하지 않는 데이터는?

A. Container 로그
B. 성능 메트릭
C. Kubernetes 이벤트
D. 애플리케이션 소스 코드

**정답:** D
**해설:** Container Insights는 모니터링 도구로, 소스 코드는 수집하지 않습니다.
**문제주제:** Container Insights 수집 데이터
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/containers/container-insights-overview
**난이도:** 하
**Top50:** X

### 문항 132
이책임은 L사의 MSP 운영 중 고객의 AKS에서 GitOps를 구현하려고 한다. 다음 중 Azure에서 권장하는 GitOps 도구는?

A. Jenkins
B. Flux
C. TeamCity
D. Bamboo

**정답:** B
**해설:** Azure는 Flux 기반의 GitOps를 공식 지원하며, AKS에 쉽게 통합할 수 있습니다.
**문제주제:** AKS GitOps 구현
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-arc/kubernetes/conceptual-gitops-flux2
**난이도:** 중
**Top50:** X

### 문항 133
김선임은 M사의 AKS에서 네트워크 정책을 구성하려고 한다. 다음 중 Azure Network Policy와 Calico의 차이점으로 맞는 것은?

A. Azure Network Policy는 Windows Node를 지원한다.
B. Calico는 더 많은 정책 기능을 제공한다.
C. Azure Network Policy는 설치가 필요하다.
D. Calico는 Azure CNI에서만 작동한다.

**정답:** B
**해설:** Calico는 더 풍부한 네트워크 정책 기능을 제공하지만, 추가 관리 오버헤드가 있습니다.
**문제주제:** AKS Network Policy 옵션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/use-network-policies
**난이도:** 상
**Top50:** X

### 문항 134
장전임은 N사의 AKS에서 Spot Node Pool을 구성하려고 한다. 다음 중 Spot Node Pool의 특징으로 틀린 것은?

A. 비용을 크게 절감할 수 있다.
B. 언제든지 축출될 수 있다.
C. System Node Pool로 사용 가능하다.
D. 최대 가격을 설정할 수 있다.

**정답:** C
**해설:** Spot Node Pool은 언제든 축출될 수 있으므로 System Node Pool로 사용할 수 없습니다.
**문제주제:** AKS Spot Node Pool 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/spot-node-pool
**난이도:** 중
**Top50:** X

### 문항 135
송팀장은 O사의 MSP 운영 중 고객의 AKS에서 Azure Key Vault와 통합을 구성하고 있다. 다음 중 권장되는 방법은?

A. Secret을 환경 변수로 하드코딩
B. Secrets Store CSI Driver 사용
C. ConfigMap에 저장
D. 이미지에 포함

**정답:** B
**해설:** Secrets Store CSI Driver를 사용하면 Key Vault의 비밀을 Pod에 안전하게 마운트할 수 있습니다.
**문제주제:** AKS Key Vault 통합
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/csi-secrets-store-driver
**난이도:** 중
**Top50:** O

### 문항 136
이책임은 P사의 AKS에서 KEDA(Kubernetes Event-driven Autoscaling)를 구성하려고 한다. 다음 중 KEDA의 특징으로 틀린 것은?

A. 0에서 n으로 스케일링 가능하다.
B. HPA를 대체한다.
C. 다양한 이벤트 소스를 지원한다.
D. Node 수를 조정한다.

**정답:** D
**해설:** KEDA는 Pod 수를 조정하는 것이며, Node 수 조정은 Cluster Autoscaler의 역할입니다.
**문제주제:** KEDA 기능 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/keda-about
**난이도:** 상
**Top50:** X

### 문항 137
김선임은 Q사의 AKS에서 Azure Policy를 사용하여 Pod 보안을 강화하려고 한다. 다음 중 Azure Policy로 제어할 수 없는 것은?

A. 특권 컨테이너 차단
B. 특정 레지스트리만 허용
C. Pod의 CPU 사용량 제한
D. Root 파일 시스템 읽기 전용 강제

**정답:** C
**해설:** CPU 사용량 제한은 resources.limits로 설정하며, Azure Policy는 구성 준수를 확인하지만 런타임 사용량은 제어하지 않습니다.
**문제주제:** Azure Policy for AKS 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/policy-reference
**난이도:** 중
**Top50:** X

### 문항 138
장전임은 R사의 MSP 운영 중 고객의 AKS에서 Azure Monitor를 통한 비용 분석을 수행하고 있다. 다음 중 AKS 비용 구성 요소가 아닌 것은?

A. Node VM 비용
B. 관리 플레인 비용
C. 디스크 및 IP 비용
D. Pod 수에 따른 비용

**정답:** D
**해설:** AKS는 Pod 수가 아닌 Node(VM) 기준으로 비용이 청구됩니다. Control Plane은 무료입니다.
**문제주제:** AKS 비용 구조
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/cost-management-best-practices
**난이도:** 중
**Top50:** O

### 문항 139
송팀장은 S사의 AKS에서 Windows 컨테이너를 실행하려고 한다. 다음 중 Windows Node Pool의 제약사항으로 틀린 것은?

A. System Node Pool로 사용할 수 없다.
B. DaemonSet을 실행할 수 없다.
C. Azure CNI만 지원한다.
D. Linux 컨테이너와 동일 Node에서 실행 가능하다.

**정답:** D
**해설:** Windows와 Linux 컨테이너는 서로 다른 Node Pool에서 실행되어야 하며, 동일 Node에서 실행할 수 없습니다.
**문제주제:** Windows Node Pool 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/windows-container-cli
**난이도:** 중
**Top50:** X

### 문항 140
이책임은 T사의 AKS에서 Availability Zone을 구성하려고 한다. 다음 중 AZ 구성 시 고려사항으로 틀린 것은?

A. Node Pool 생성 시에만 AZ를 지정할 수 있다.
B. Standard Load Balancer가 필요하다.
C. 기존 클러스터에 AZ를 추가할 수 있다.
D. Cross-AZ 트래픽 비용이 발생할 수 있다.

**정답:** C
**해설:** AZ는 클러스터나 Node Pool 생성 시에만 구성 가능하며, 기존 클러스터에는 추가할 수 없습니다.
**문제주제:** AKS Availability Zone 구성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/availability-zones
**난이도:** 중
**Top50:** X

### 문항 141
김선임은 U사의 MSP 운영 중 고객의 AKS에서 컨테이너 이미지 취약점을 스캔하려고 한다. 다음 중 권장되는 방법은?

A. 수동으로 이미지 검사
B. Microsoft Defender for Containers 사용
C. 오픈소스 도구만 사용
D. 스캔 없이 배포

**정답:** B
**해설:** Microsoft Defender for Containers는 이미지 스캔, 런타임 보호, 환경 강화를 제공합니다.
**문제주제:** AKS 컨테이너 보안
**관련링크:** https://learn.microsoft.com/ko-kr/azure/defender-for-cloud/defender-for-containers-introduction
**난이도:** 중
**Top50:** X

### 문항 142
장전임은 V사의 AKS에서 Service Mesh를 구현하려고 한다. 다음 중 Azure가 지원하는 Service Mesh가 아닌 것은?

A. Istio
B. Linkerd
C. Open Service Mesh (OSM)
D. AppMesh

**정답:** D
**해설:** AppMesh는 AWS의 Service Mesh이며, Azure는 Istio, Linkerd, OSM을 지원합니다.
**문제주제:** AKS Service Mesh 옵션
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/servicemesh-about
**난이도:** 중
**Top50:** X

### 문항 143
송팀장은 W사의 AKS에서 Blue-Green 배포를 구현하려고 한다. 다음 중 가장 적절한 방법은?

A. Rolling Update만 사용
B. 두 개의 Deployment와 Service Selector 전환
C. Pod 직접 교체
D. 클러스터 재생성

**정답:** B
**해설:** Blue-Green 배포는 두 개의 Deployment를 유지하고 Service의 Selector를 전환하여 트래픽을 즉시 전환합니다.
**문제주제:** AKS 배포 전략
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/deployment-strategies
**난이도:** 중
**Top50:** X

### 문항 144
이책임은 X사의 MSP 운영 중 고객의 AKS에서 Prometheus를 구성하려고 한다. 다음 중 Azure Monitor와 Prometheus 통합의 이점이 아닌 것은?

A. 관리형 Prometheus 제공
B. Grafana 통합
C. 장기 메트릭 보관
D. 자동 애플리케이션 코드 수정

**정답:** D
**해설:** Prometheus는 메트릭 수집 도구이며, 애플리케이션 코드를 자동으로 수정하지 않습니다.
**문제주제:** Azure Monitor for Prometheus
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-monitor/essentials/prometheus-metrics-overview
**난이도:** 중
**Top50:** X

### 문항 145
김선임은 Y사의 AKS에서 GPU Node Pool을 구성하려고 한다. 다음 중 GPU Node Pool의 용도로 적절하지 않은 것은?

A. 기계 학습 워크로드
B. 비디오 렌더링
C. 일반 웹 애플리케이션
D. AI 추론

**정답:** C
**해설:** GPU는 비용이 높으므로 일반 웹 애플리케이션에는 적합하지 않으며, AI/ML 워크로드에 사용해야 합니다.
**문제주제:** GPU Node Pool 사용 사례
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/gpu-cluster
**난이도:** 중
**Top50:** X

### 문항 146
장전임은 Z사의 AKS에서 Helm을 사용하여 애플리케이션을 배포하려고 한다. 다음 중 Helm의 구성 요소가 아닌 것은?

A. Chart
B. Values
C. Release
D. Operator

**정답:** D
**해설:** Operator는 Kubernetes의 확장 패턴이며, Helm의 구성 요소가 아닙니다. Helm은 Chart, Values, Release로 구성됩니다.
**문제주제:** Helm 구성 요소
**관련링크:** https://helm.sh/docs/topics/architecture/
**난이도:** 중
**Top50:** X

### 문항 147
송팀장은 AA사의 MSP 운영 중 고객의 AKS에서 Confidential Computing을 구성하려고 한다. 다음 중 요구사항이 아닌 것은?

A. DCsv2/DCsv3 시리즈 VM
B. 특별한 SDK 사용
C. Standard Node Pool
D. Intel SGX 지원

**정답:** C
**해설:** Confidential Computing은 특수한 하드웨어(DCsv2/DCsv3)가 필요하며, Standard Node Pool로는 불가능합니다.
**문제주제:** AKS Confidential Computing
**관련링크:** https://learn.microsoft.com/ko-kr/azure/confidential-computing/confidential-nodes-aks-overview
**난이도:** 상
**Top50:** X

### 문항 148
이책임은 AB사의 AKS에서 Start/Stop 기능을 구성하려고 한다. 다음 중 AKS Start/Stop의 특징으로 틀린 것은?

A. 비용 절감을 위해 사용한다.
B. 클러스터 상태가 보존된다.
C. System Node Pool만 중지된다.
D. PV 데이터가 유지된다.

**정답:** C
**해설:** AKS Start/Stop은 전체 클러스터(모든 Node Pool)를 중지하며, System Node Pool만 선택적으로 중지할 수 없습니다.
**문제주제:** AKS Start/Stop 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/start-stop-cluster
**난이도:** 중
**Top50:** X

### 문항 149
김선임은 AC사의 AKS에서 Pod Disruption Budget을 구성하고 있다. 다음 중 PDB 설정 방법이 아닌 것은?

A. minAvailable
B. maxUnavailable
C. targetAvailable
D. selector

**정답:** C
**해설:** PDB는 minAvailable과 maxUnavailable만 지원하며, targetAvailable은 존재하지 않는 설정입니다.
**문제주제:** Pod Disruption Budget 구성
**관련링크:** https://kubernetes.io/docs/concepts/workloads/pods/disruptions/
**난이도:** 중
**Top50:** O

### 문항 150
장전임은 AD사의 MSP 운영 중 고객의 AKS에서 Azure Arc 통합을 구성하고 있다. 다음 중 Arc-enabled Kubernetes의 기능이 아닌 것은?

A. GitOps 배포
B. Azure Policy 적용
C. Azure Monitor 통합
D. 자동 클러스터 생성

**정답:** D
**해설:** Arc-enabled Kubernetes는 기존 클러스터를 Azure에 연결하는 것이며, 클러스터를 생성하지는 않습니다.
**문제주제:** Arc-enabled Kubernetes 기능
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-arc/kubernetes/overview
**난이도:** 중
**Top50:** X

### 문항 151
송팀장은 AE사의 AKS에서 Container Registry 통합을 구성하고 있다. 다음 중 ACR 통합 방법으로 권장되지 않는 것은?

A. Managed Identity 사용
B. Service Principal 사용
C. Admin 계정 사용
D. RBAC 역할 할당

**정답:** C
**해설:** Admin 계정은 보안상 권장되지 않으며, Managed Identity나 Service Principal을 사용해야 합니다.
**문제주제:** AKS-ACR 통합 보안
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/cluster-container-registry-integration
**난이도:** 중
**Top50:** O

### 문항 152
이책임은 AF사의 AKS에서 Ephemeral OS Disk를 구성하려고 한다. 다음 중 Ephemeral Disk의 이점이 아닌 것은?

A. 더 낮은 읽기/쓰기 지연 시간
B. 더 빠른 Node 재이미징
C. 데이터 영구 보존
D. 비용 절감

**정답:** C
**해설:** Ephemeral Disk는 임시 디스크로 Node가 재시작되면 데이터가 손실됩니다.
**문제주제:** Ephemeral OS Disk 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/ephemeral-os
**난이도:** 중
**Top50:** X

### 문항 153
김선임은 AG사의 MSP 운영 중 고객의 AKS에서 Virtual Node를 구성하려고 한다. 다음 중 Virtual Node의 제약사항은?

A. Azure Container Instances 기반
B. 빠른 스케일링 가능
C. DaemonSet 지원
D. 서버리스 컴퓨팅

**정답:** C
**해설:** Virtual Node는 ACI 기반으로 DaemonSet, Privileged Containers 등 일부 Kubernetes 기능을 지원하지 않습니다.
**문제주제:** AKS Virtual Node 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/virtual-nodes
**난이도:** 상
**Top50:** X

### 문항 154
장전임은 AH사의 AKS에서 Cluster Extension을 관리하고 있다. 다음 중 AKS Extension이 아닌 것은?

A. Azure Machine Learning
B. Azure App Service
C. Dapr
D. Azure Functions

**정답:** D
**해설:** Azure Functions는 별도 서비스이며, AKS Extension으로 제공되지 않습니다.
**문제주제:** AKS Cluster Extensions
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/cluster-extensions
**난이도:** 중
**Top50:** X

### 문항 155
송팀장은 AI사의 AKS에서 Private Cluster를 구성하려고 한다. 다음 중 Private Cluster의 특징으로 틀린 것은?

A. API Server가 Private IP만 가진다.
B. Node와 API Server 간 통신이 Private Network로 이루어진다.
C. Public IP를 통한 kubectl 접근이 가능하다.
D. Private DNS Zone이 필요하다.

**정답:** C
**해설:** Private Cluster는 API Server에 Public IP가 없으므로 Private Network나 VPN/ExpressRoute를 통해서만 접근 가능합니다.
**문제주제:** AKS Private Cluster 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/private-clusters
**난이도:** 중
**Top50:** O

### 문항 156
이책임은 AJ사의 MSP 운영 중 고객의 AKS에서 AAD Pod Identity를 Workload Identity로 마이그레이션하려고 한다. 다음 중 Workload Identity의 이점이 아닌 것은?

A. 더 나은 보안
B. Kubernetes 네이티브
C. 더 간단한 구성
D. Windows Node 지원

**정답:** D
**해설:** Workload Identity는 현재 Linux Node만 지원하며, Windows Node 지원은 제한적입니다.
**문제주제:** Workload Identity 제약
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/workload-identity-migrate-from-pod-identity
**난이도:** 상
**Top50:** X

### 문항 157
김선임은 AK사의 AKS에서 Backup을 구성하려고 한다. 다음 중 Azure Backup for AKS가 백업하지 않는 것은?

A. Persistent Volumes
B. Cluster 구성
C. Secrets
D. Node OS 설정

**정답:** D
**해설:** Azure Backup for AKS는 Kubernetes 리소스와 PV를 백업하지만, Node OS 수준 설정은 백업하지 않습니다.
**문제주제:** AKS Backup 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/backup/azure-kubernetes-service-backup-overview
**난이도:** 중
**Top50:** X

### 문항 158
장전임은 AL사의 AKS에서 Resource Quota를 설정하려고 한다. 다음 중 Resource Quota로 제한할 수 없는 것은?

A. Namespace별 Pod 수
B. Namespace별 CPU/Memory
C. Namespace별 PVC 수
D. Cluster 전체 Node 수

**정답:** D
**해설:** Resource Quota는 Namespace 수준 리소스 제한이며, Cluster 전체 Node 수는 다른 방법으로 관리됩니다.
**문제주제:** Kubernetes Resource Quota 범위
**관련링크:** https://kubernetes.io/docs/concepts/policy/resource-quotas/
**난이도:** 중
**Top50:** X

### 문항 159
송팀장은 AM사의 MSP 운영 중 고객의 AKS 네트워크 성능을 최적화하려고 한다. 다음 중 권장사항이 아닌 것은?

A. Azure CNI 사용
B. Accelerated Networking 활성화
C. Proximity Placement Group 사용
D. 모든 트래픽을 인터넷 경유

**정답:** D
**해설:** 인터넷 경유는 지연시간과 비용을 증가시키므로, Private Network를 사용해야 합니다.
**문제주제:** AKS 네트워크 성능 최적화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/operator-best-practices-network
**난이도:** 중
**Top50:** X

### 문항 160
이책임은 AN사의 AKS에서 Maintenance Window를 구성하려고 한다. 다음 중 Maintenance Window 설정이 적용되지 않는 것은?

A. Node OS 업데이트
B. Kubernetes 버전 업그레이드
C. Node 이미지 업그레이드
D. 애플리케이션 배포

**정답:** D
**해설:** Maintenance Window는 AKS 인프라 유지보수용이며, 애플리케이션 배포는 사용자가 제어합니다.
**문제주제:** AKS Maintenance Window 범위
**관련링크:** https://learn.microsoft.com/ko-kr/azure/aks/planned-maintenance
**난이도:** 중
**Top50:** X

## 5. CI/CD & 비용 최적화 (40문항)

### 문항 161
이책임은 A사의 Azure 비용 최적화를 담당하고 있다. 개발 환경 VM들이 업무 시간 외에도 계속 실행되어 불필요한 비용이 발생하고 있다. 다음 중 비용 절감 방안으로 가장 효과적인 것은?

A. 모든 개발 VM을 Spot Instance로 전환한다.
B. Azure Automation과 태그를 활용하여 업무 시간 외 자동 시작/중지를 구성한다.
C. 개발 VM의 크기를 한 단계 낮춘다.
D. 개발 VM에 대해 3년 Reserved Instance를 구매한다.

**정답:** B
**해설:** Azure Automation의 Start/Stop 솔루션과 환경 태그(dev/test/prod)를 활용하면 스케줄에 따라 자동으로 VM을 관리할 수 있습니다. 업무 시간 외 중지로 최대 75% 비용 절감이 가능합니다.
**문제주제:** Azure VM 비용 최적화 자동화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/automation/automation-solution-vm-management
**난이도:** 중
**Top50:** O

### 문항 162
송팀장은 B사의 GitHub Actions를 사용한 AKS 배포 파이프라인을 구성 중이다. 빌드한 컨테이너 이미지를 ACR에 푸시하고 AKS에 배포해야 한다. 다음 중 보안 측면에서 가장 적절한 인증 방법은?

A. ACR Access Key를 GitHub Secrets에 저장하여 사용한다.
B. Service Principal의 Client Secret을 소스 코드에 하드코딩한다.
C. Workload Identity Federation을 구성하여 비밀 정보 없이 인증한다.
D. 개발자 개인 계정의 Azure CLI 토큰을 사용한다.

**정답:** C
**해설:** Workload Identity Federation(OIDC)은 GitHub Actions와 Azure 간 신뢰 관계를 설정하여 비밀 정보 없이 안전한 인증이 가능합니다. 이는 현재 권장되는 Best Practice입니다.
**문제주제:** GitHub Actions Azure 인증 보안
**관련링크:** https://learn.microsoft.com/ko-kr/azure/developer/github/connect-from-azure
**난이도:** 상
**Top50:** O

### 문항 163
김선임은 C사의 MSP 운영 중 고객의 Azure DevOps Pipeline에서 빌드 실패 문제를 해결하려고 한다. 다음 중 디버깅 방법으로 적절하지 않은 것은?

A. System.Debug 변수를 true로 설정
B. Pipeline 로그 확인
C. 로컬 환경에서 동일한 명령 실행
D. 프로덕션 환경에서 직접 테스트

**정답:** D
**해설:** 프로덕션 환경에서 직접 테스트는 위험하며, 별도의 테스트 환경이나 로컬에서 문제를 재현해야 합니다.
**문제주제:** Azure DevOps Pipeline 디버깅
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/troubleshooting/debug-deployment-issues
**난이도:** 중
**Top50:** X

### 문항 164
장전임은 D사의 Terraform을 사용하여 Azure 인프라를 관리하고 있다. 다음 중 Terraform State 파일 관리 Best Practice가 아닌 것은?

A. Remote Backend 사용
B. State 파일을 Git에 커밋
C. State Lock 활성화
D. State 파일 암호화

**정답:** B
**해설:** State 파일은 민감한 정보를 포함하므로 절대 Git에 커밋하면 안 되며, Remote Backend에 안전하게 저장해야 합니다.
**문제주제:** Terraform State 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/developer/terraform/store-state-in-azure-storage
**난이도:** 중
**Top50:** O

### 문항 165
송팀장은 E사의 Azure Bicep을 사용하여 IaC를 구현하려고 한다. 다음 중 Bicep의 장점이 아닌 것은?

A. ARM 템플릿보다 간결한 구문
B. 타입 안정성과 IntelliSense 지원
C. 다른 클라우드 공급자 지원
D. 모듈화 및 재사용성

**정답:** C
**해설:** Bicep은 Azure 전용 IaC 도구이며, 다른 클라우드는 지원하지 않습니다. 멀티클라우드는 Terraform을 사용해야 합니다.
**문제주제:** Azure Bicep vs Terraform
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/bicep/overview
**난이도:** 중
**Top50:** X

### 문항 166
이책임은 F사의 MSP 운영 중 고객의 CI/CD 파이프라인에서 보안 스캔을 통합하려고 한다. 다음 중 DevSecOps 구현 순서로 적절한 것은?

A. 개발 → 빌드 → 보안 스캔 → 배포
B. 개발 → 보안 스캔 → 빌드 → 배포
C. 보안 스캔 → 개발 → 빌드 → 배포
D. 개발 → 빌드 → 배포 → 보안 스캔

**정답:** A
**해설:** 보안 스캔은 빌드 후, 배포 전에 수행하여 취약점이 있는 코드가 프로덕션에 배포되는 것을 방지해야 합니다.
**문제주제:** DevSecOps 파이프라인 설계
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/devops-at-microsoft/security-in-devops
**난이도:** 중
**Top50:** X

### 문항 167
김선임은 G사의 Azure 환경에서 Savings Plan을 구매하려고 한다. 다음 중 Savings Plan에 대한 설명으로 틀린 것은?

A. 1년 또는 3년 약정이 가능하다.
B. Reserved Instance보다 유연성이 높다.
C. 컴퓨트 비용만 절감 가능하다.
D. 사용량 초과분은 종량제 요금이 적용된다.

**정답:** C
**해설:** Azure Savings Plan은 컴퓨트뿐만 아니라 특정 서비스에도 적용 가능하며, 더 넓은 범위의 비용 절감이 가능합니다.
**문제주제:** Azure Savings Plan 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/savings-plan/savings-plan-compute-overview
**난이도:** 중
**Top50:** O

### 문항 168
장전임은 H사의 Azure DevOps에서 Artifact Feed를 구성하고 있다. 다음 중 Artifact Feed가 지원하지 않는 패키지 유형은?

A. NuGet
B. npm
C. Maven
D. Docker Images

**정답:** D
**해설:** Docker Images는 Azure Container Registry를 사용해야 하며, Artifact Feed는 NuGet, npm, Maven, Python, Universal Packages를 지원합니다.
**문제주제:** Azure Artifacts 지원 패키지
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/artifacts/start-using-azure-artifacts
**난이도:** 중
**Top50:** X

### 문항 169
송팀장은 I사의 MSP 운영 중 고객의 Azure Cost Allocation을 구성하고 있다. 다음 중 비용 할당 방법으로 적절하지 않은 것은?

A. 태그 기반 비용 할당
B. 리소스 그룹별 비용 분석
C. 구독별 비용 분리
D. 사용자 IP별 비용 계산

**정답:** D
**해설:** Azure는 사용자 IP별 비용 추적을 제공하지 않으며, 태그, 리소스 그룹, 구독 단위로 비용을 관리합니다.
**문제주제:** Azure 비용 할당 방법
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/allocate-costs
**난이도:** 중
**Top50:** X

### 문항 170
이책임은 J사의 GitHub Actions에서 Matrix Build를 구성하려고 한다. 다음 중 Matrix Build의 용도로 적절한 것은?

A. 순차적 빌드 실행
B. 여러 환경에서 병렬 테스트
C. 빌드 실패 시 자동 복구
D. 빌드 아티팩트 암호화

**정답:** B
**해설:** Matrix Build는 여러 OS, 언어 버전, 환경에서 동시에 빌드/테스트를 실행하여 호환성을 확인하는 기능입니다.
**문제주제:** GitHub Actions Matrix Build
**관련링크:** https://docs.github.com/en/actions/using-jobs/using-a-matrix-for-your-jobs
**난이도:** 중
**Top50:** X

### 문항 171
김선임은 K사의 Azure 환경에서 Spot VM을 사용하여 비용을 절감하려고 한다. 다음 중 Spot VM 사용에 적합하지 않은 워크로드는?

A. 배치 처리 작업
B. 개발/테스트 환경
C. 프로덕션 데이터베이스
D. CI/CD 빌드 에이전트

**정답:** C
**해설:** Spot VM은 언제든 축출될 수 있으므로, 중단되면 안 되는 프로덕션 데이터베이스에는 부적합합니다.
**문제주제:** Spot VM 사용 사례
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/spot-vms
**난이도:** 중
**Top50:** O

### 문항 172
장전임은 L사의 MSP 운영 중 고객의 Azure DevOps에서 Release Pipeline을 구성하고 있다. 다음 중 Approval Gate 설정 위치로 적절한 것은?

A. 빌드 파이프라인 시작 전
B. 각 스테이지 전/후
C. 아티팩트 생성 중
D. 소스 코드 커밋 시

**정답:** B
**해설:** Approval Gate는 각 배포 스테이지 전후에 설정하여 수동 승인을 통한 배포 제어가 가능합니다.
**문제주제:** Azure DevOps Release 승인
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/release/approvals/approvals
**난이도:** 중
**Top50:** X

### 문항 173
송팀장은 M사의 Infrastructure as Code에서 환경별 구성을 관리하려고 한다. 다음 중 권장되는 방법은?

A. 환경별로 별도 코드 작성
B. 조건문으로 모든 환경 처리
C. 변수 파일을 환경별로 분리
D. 하드코딩된 값 사용

**정답:** C
**해설:** 환경별 변수 파일(dev.tfvars, prod.tfvars 등)을 분리하면 코드 재사용성과 관리 효율성이 높아집니다.
**문제주제:** IaC 환경 관리 Best Practice
**관련링크:** https://learn.microsoft.com/ko-kr/azure/developer/terraform/create-resource-group
**난이도:** 중
**Top50:** X

### 문항 174
이책임은 N사의 Azure에서 B-series VM을 사용하려고 한다. 다음 중 B-series VM의 특징으로 틀린 것은?

A. CPU 크레딧 시스템 사용
B. 일정한 고성능 보장
C. 버스트 가능한 성능
D. 경량 워크로드에 적합

**정답:** B
**해설:** B-series는 버스터블 VM으로 일정한 고성능을 보장하지 않으며, CPU 크레딧을 사용하여 필요시 버스트합니다.
**문제주제:** B-series VM 특성
**관련링크:** https://learn.microsoft.com/ko-kr/azure/virtual-machines/sizes-b-series-burstable
**난이도:** 중
**Top50:** X

### 문항 175
김선임은 O사의 MSP 운영 중 고객의 Azure DevOps에서 YAML Pipeline을 작성하고 있다. 다음 중 YAML Pipeline의 이점이 아닌 것은?

A. 코드로 관리 가능
B. 버전 관리 가능
C. GUI만으로 편집 가능
D. 템플릿 재사용 가능

**정답:** C
**해설:** YAML Pipeline은 코드 기반이며, GUI 편집은 제한적입니다. Classic Pipeline이 GUI 중심입니다.
**문제주제:** YAML vs Classic Pipeline
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/get-started/pipelines-get-started
**난이도:** 중
**Top50:** X

### 문항 176
장전임은 P사의 Azure 환경에서 Dev/Test 구독 혜택을 활용하려고 한다. 다음 중 Dev/Test 구독의 이점이 아닌 것은?

A. Windows VM 라이선스 비용 면제
B. 특정 서비스 할인
C. 프로덕션 워크로드 실행 가능
D. Visual Studio 구독자 전용

**정답:** C
**해설:** Dev/Test 구독은 개발/테스트 전용이며, 프로덕션 워크로드 실행은 라이선스 위반입니다.
**문제주제:** Azure Dev/Test 구독 제약
**관련링크:** https://azure.microsoft.com/ko-kr/pricing/dev-test/
**난이도:** 중
**Top50:** X

### 문항 177
송팀장은 Q사의 GitHub Actions에서 Self-hosted Runner를 구성하려고 한다. 다음 중 Self-hosted Runner의 이점이 아닌 것은?

A. 사용자 정의 하드웨어 사용
B. 무료 무제한 빌드 시간
C. 자동 보안 업데이트
D. 온프레미스 리소스 접근

**정답:** C
**해설:** Self-hosted Runner는 사용자가 직접 관리해야 하므로 보안 업데이트도 수동으로 수행해야 합니다.
**문제주제:** GitHub Self-hosted Runner
**관련링크:** https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners
**난이도:** 중
**Top50:** X

### 문항 178
이책임은 R사의 MSP 운영 중 고객의 Azure Cost Alert를 구성하고 있다. 다음 중 비용 알림 유형이 아닌 것은?

A. 예산 알림
B. 크레딧 소진 알림
C. 실시간 비용 알림
D. 부서별 지출 알림

**정답:** C
**해설:** Azure 비용 데이터는 8-24시간 지연되므로 실시간 알림은 불가능합니다.
**문제주제:** Azure Cost Alert 유형
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending
**난이도:** 중
**Top50:** X

### 문항 179
김선임은 S사의 Azure DevOps에서 Service Connection을 구성하고 있다. 다음 중 가장 안전한 인증 방법은?

A. 사용자 이름/암호
B. Service Principal with Certificate
C. Personal Access Token
D. 공유 Access Key

**정답:** B
**해설:** Service Principal with Certificate는 비밀번호보다 안전하며, 자동 갱신이 불필요한 인증서 기반 인증을 제공합니다.
**문제주제:** Azure DevOps Service Connection 보안
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/library/service-endpoints
**난이도:** 중
**Top50:** X

### 문항 180
장전임은 T사의 Azure 환경에서 Reserved Capacity를 구매하려고 한다. 다음 중 Reserved Capacity를 지원하지 않는 서비스는?

A. Azure SQL Database
B. Cosmos DB
C. Azure Functions Consumption Plan
D. Azure Synapse Analytics

**정답:** C
**해설:** Functions Consumption Plan은 사용량 기반 과금이므로 예약 구매가 불가능합니다. Premium Plan은 가능합니다.
**문제주제:** Azure Reserved Capacity 지원 서비스
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/reservations/save-compute-costs-reservations
**난이도:** 중
**Top50:** X

### 문항 181
송팀장은 U사의 MSP 운영 중 고객의 CI/CD 파이프라인 성능을 개선하려고 한다. 다음 중 빌드 시간 단축 방법으로 적절하지 않은 것은?

A. 빌드 캐시 활용
B. 병렬 작업 실행
C. 불필요한 테스트 제거
D. 모든 의존성을 매번 다운로드

**정답:** D
**해설:** 의존성을 매번 다운로드하면 빌드 시간이 증가하므로, 캐싱을 통해 재사용해야 합니다.
**문제주제:** CI/CD 파이프라인 최적화
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/caching
**난이도:** 중
**Top50:** X

### 문항 182
이책임은 V사의 Terraform에서 민감한 변수를 관리하려고 한다. 다음 중 권장되는 방법은?

A. terraform.tfvars에 평문 저장
B. 환경 변수 사용
C. 코드에 하드코딩
D. 공개 리포지토리에 저장

**정답:** B
**해설:** 민감한 변수는 환경 변수나 Key Vault 같은 보안 저장소를 사용해야 하며, 평문 저장은 피해야 합니다.
**문제주제:** Terraform 보안 변수 관리
**관련링크:** https://learn.microsoft.com/ko-kr/azure/developer/terraform/store-secrets-in-key-vault
**난이도:** 중
**Top50:** O

### 문항 183
김선임은 W사의 Azure 환경에서 Hybrid Benefit을 적용하려고 한다. 다음 중 Hybrid Benefit을 적용할 수 없는 것은?

A. Windows Server VM
B. SQL Server VM
C. Red Hat Enterprise Linux
D. Linux VM with SQL Server

**정답:** C
**해설:** Azure Hybrid Benefit은 Windows Server와 SQL Server 라이선스에만 적용되며, RHEL은 별도 프로그램이 있습니다.
**문제주제:** Azure Hybrid Benefit 적용 범위
**관련링크:** https://azure.microsoft.com/ko-kr/pricing/hybrid-benefit/
**난이도:** 중
**Top50:** O

### 문항 184
장전임은 X사의 MSP 운영 중 고객의 Azure DevOps에서 Deployment Group을 구성하고 있다. 다음 중 Deployment Group의 용도는?

A. 개발자 그룹 관리
B. 타겟 머신 집합 관리
C. 소스 코드 그룹화
D. 테스트 케이스 그룹화

**정답:** B
**해설:** Deployment Group은 배포 대상이 되는 물리적/가상 머신들의 논리적 그룹입니다.
**문제주제:** Azure DevOps Deployment Group
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/release/deployment-groups
**난이도:** 중
**Top50:** X

### 문항 185
송팀장은 Y사의 GitHub Actions에서 Composite Action을 만들려고 한다. 다음 중 Composite Action의 특징으로 틀린 것은?

A. 여러 Step을 하나로 묶을 수 있다.
B. 재사용 가능하다.
C. Docker 컨테이너가 필수다.
D. 입력 매개변수를 받을 수 있다.

**정답:** C
**해설:** Composite Action은 YAML 기반으로 Docker 없이도 생성 가능합니다. Docker는 Docker Action에 필요합니다.
**문제주제:** GitHub Composite Action
**관련링크:** https://docs.github.com/en/actions/creating-actions/creating-a-composite-action
**난이도:** 상
**Top50:** X

### 문항 186
이책임은 Z사의 Azure 환경에서 Azure Advisor Cost 권장사항을 검토하고 있다. 다음 중 Advisor가 제공하는 비용 절감 권장사항이 아닌 것은?

A. 사용하지 않는 ExpressRoute 회선 제거
B. 적절한 VM 크기 조정
C. Reserved Instance 구매
D. 개발자 급여 절감

**정답:** D
**해설:** Azure Advisor는 Azure 리소스 최적화에 대한 권장사항만 제공하며, 인건비 같은 외부 비용은 다루지 않습니다.
**문제주제:** Azure Advisor Cost 권장사항
**관련링크:** https://learn.microsoft.com/ko-kr/azure/advisor/advisor-cost-recommendations
**난이도:** 하
**Top50:** X

### 문항 187
김선임은 AA사의 MSP 운영 중 고객의 Azure DevOps에서 Conditional Deployment를 구성하려고 한다. 다음 중 조건으로 사용할 수 없는 것은?

A. Branch 이름
B. 변수 값
C. 이전 스테이지 결과
D. 현재 날씨

**정답:** D
**해설:** Azure DevOps는 파이프라인 내부 상태와 변수를 조건으로 사용할 수 있지만, 외부 날씨 정보는 직접 사용할 수 없습니다.
**문제주제:** Azure DevOps 조건부 배포
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/process/conditions
**난이도:** 중
**Top50:** X

### 문항 188
장전임은 AB사의 Terraform에서 Azure Provider를 구성하고 있다. 다음 중 Provider 인증 방법으로 권장되지 않는 것은?

A. Service Principal with Certificate
B. Managed Identity
C. Azure CLI
D. 하드코딩된 Client Secret

**정답:** D
**해설:** Client Secret을 코드에 하드코딩하는 것은 보안 위험이 있으며, 환경 변수나 Key Vault를 사용해야 합니다.
**문제주제:** Terraform Azure Provider 인증
**관련링크:** https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/service_principal_client_secret
**난이도:** 중
**Top50:** X

### 문항 189
송팀장은 AC사의 Azure 환경에서 Cost Anomaly Detection을 설정하려고 한다. 다음 중 이상 비용 감지 방법이 아닌 것은?

A. 기계 학습 기반 감지
B. 수동 임계값 설정
C. 과거 패턴 분석
D. 타사 신용카드 모니터링

**정답:** D
**해설:** Azure Cost Management는 Azure 사용량 기반 이상 감지를 제공하며, 신용카드 모니터링은 범위 밖입니다.
**문제주제:** Azure Cost Anomaly Detection
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/understand/analyze-unexpected-charges
**난이도:** 중
**Top50:** X

### 문항 190
이책임은 AD사의 MSP 운영 중 고객의 GitHub Actions에서 Artifact를 관리하고 있다. 다음 중 Artifact 보존 기간의 최대값은?

A. 30일
B. 90일
C. 400일
D. 무제한

**정답:** C
**해설:** GitHub Actions Artifact의 최대 보존 기간은 400일이며, 기본값은 90일입니다.
**문제주제:** GitHub Actions Artifact 관리
**관련링크:** https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts
**난이도:** 중
**Top50:** X

### 문항 191
김선임은 AE사의 Azure 환경에서 ARM Template을 Bicep으로 변환하려고 한다. 다음 중 사용할 명령어는?

A. az bicep convert
B. az bicep decompile
C. az bicep build
D. az bicep transform

**정답:** B
**해설:** 'az bicep decompile' 명령어를 사용하여 기존 ARM Template을 Bicep 파일로 변환할 수 있습니다.
**문제주제:** ARM to Bicep 변환
**관련링크:** https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/bicep/decompile
**난이도:** 중
**Top50:** X

### 문항 192
장전임은 AF사의 Azure DevOps에서 Variable Group을 구성하고 있다. 다음 중 Variable Group의 용도로 적절하지 않은 것은?

A. 파이프라인 간 변수 공유
B. Key Vault 연동
C. 환경별 구성 관리
D. 소스 코드 버전 관리

**정답:** D
**해설:** Variable Group은 변수 관리용이며, 소스 코드 버전 관리는 Git 등의 VCS를 사용해야 합니다.
**문제주제:** Azure DevOps Variable Group
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/library/variable-groups
**난이도:** 중
**Top50:** X

### 문항 193
송팀장은 AG사의 MSP 운영 중 고객의 Azure 비용 최적화를 위해 Orphaned Resources를 찾고 있다. 다음 중 일반적인 Orphaned Resource가 아닌 것은?

A. 연결되지 않은 Managed Disk
B. 할당되지 않은 Public IP
C. 사용 중인 VM
D. 빈 Resource Group

**정답:** C
**해설:** 사용 중인 VM은 활성 리소스이며, Orphaned Resource는 사용되지 않지만 비용이 발생하는 리소스를 의미합니다.
**문제주제:** Azure Orphaned Resources
**관련링크:** https://learn.microsoft.com/ko-kr/azure/advisor/advisor-cost-recommendations
**난이도:** 중
**Top50:** O

### 문항 194
이책임은 AH사의 GitHub Actions에서 Environment를 구성하려고 한다. 다음 중 Environment 기능이 아닌 것은?

A. 배포 보호 규칙
B. 환경별 Secret 관리
C. 배포 이력 추적
D. 자동 코드 생성

**정답:** D
**해설:** Environment는 배포 관리 기능이며, 자동 코드 생성은 제공하지 않습니다.
**문제주제:** GitHub Actions Environment
**관련링크:** https://docs.github.com/en/actions/deployment/targeting-different-environments
**난이도:** 중
**Top50:** X

### 문항 195
김선임은 AI사의 Azure 환경에서 Consumption Budget을 설정하려고 한다. 다음 중 예산 초과 시 자동으로 수행할 수 없는 작업은?

A. 이메일 알림 발송
B. Action Group 트리거
C. 구독 자동 삭제
D. Webhook 호출

**정답:** C
**해설:** 예산 초과 시 알림과 자동화는 가능하지만, 구독 삭제 같은 파괴적 작업은 자동으로 수행되지 않습니다.
**문제주제:** Azure Budget Actions
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/tutorial-acm-create-budgets
**난이도:** 중
**Top50:** X

### 문항 196
장전임은 AJ사의 MSP 운영 중 고객의 Terraform에서 Remote State Locking을 구성하려고 한다. 다음 중 Azure에서 State Lock을 지원하는 Backend는?

A. Local
B. Azure Storage with Blob Lease
C. S3
D. HTTP

**정답:** B
**해설:** Azure Storage Backend는 Blob Lease를 사용하여 State Locking을 지원하여 동시 수정을 방지합니다.
**문제주제:** Terraform State Locking
**관련링크:** https://www.terraform.io/language/settings/backends/azurerm
**난이도:** 상
**Top50:** X

### 문항 197
송팀장은 AK사의 Azure DevOps에서 Multi-stage Pipeline을 구성하고 있다. 다음 중 Stage 간 종속성 설정 방법이 아닌 것은?

A. dependsOn
B. condition
C. trigger
D. variables

**정답:** D
**해설:** variables는 변수 정의용이며, Stage 간 종속성은 dependsOn, condition으로 설정합니다. trigger는 파이프라인 시작 조건입니다.
**문제주제:** Azure DevOps Multi-stage Pipeline
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/process/stages
**난이도:** 중
**Top50:** X

### 문항 198
이책임은 AL사의 Azure 환경에서 Cost Export를 구성하려고 한다. 다음 중 Export 가능한 형식이 아닌 것은?

A. CSV
B. JSON
C. XML
D. Parquet

**정답:** C
**해설:** Azure Cost Export는 CSV와 Parquet 형식만 지원하며, XML은 지원하지 않습니다.
**문제주제:** Azure Cost Export 형식
**관련링크:** https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/tutorial-export-acm-data
**난이도:** 중
**Top50:** X

### 문항 199
김선임은 AM사의 MSP 운영 중 고객의 Azure DevOps에서 Package Vulnerability Scanning을 구성하려고 한다. 다음 중 스캔 대상이 아닌 것은?

A. NuGet 패키지
B. npm 패키지
C. Container 이미지
D. 팀원 이력서

**정답:** D
**해설:** Package Vulnerability Scanning은 소프트웨어 의존성의 보안 취약점을 스캔하며, 인사 문서는 대상이 아닙니다.
**문제주제:** DevOps Security Scanning
**관련링크:** https://learn.microsoft.com/ko-kr/azure/devops/pipelines/tasks/reference/whitesource
**난이도:** 하
**Top50:** X

### 문항 200
장전임은 AN사의 Azure 환경에서 FinOps 문화를 구축하려고 한다. 다음 중 FinOps 원칙이 아닌 것은?

A. 팀 간 협업
B. 실시간 의사결정
C. 비용 책임 분산
D. 무조건적인 비용 절감

**정답:** D
**해설:** FinOps는 무조건적인 비용 절감이 아닌 비즈니스 가치 대비 최적화를 추구합니다. 때로는 성능이나 혁신을 위해 비용 증가가 필요할 수 있습니다.
**문제주제:** FinOps 원칙
**관련링크:** https://www.finops.org/framework/principles/
**난이도:** 중
**Top50:** O

---

# 문제 생성 완료

총 200문항이 생성되었습니다.

## 카테고리별 분포:
- Azure 기본 서비스 & 거버넌스: 40문항
- 스토리지 & 데이터 관리: 40문항  
- 네트워크 & 보안: 40문항
- AKS / Kubernetes: 40문항
- CI/CD & 비용 최적화: 40문항

## 난이도 분포:
- 상: 약 20%
- 중: 약 70%
- 하: 약 10%

## Top50 선정:
출제빈도가 높고 실무에서 중요한 50개 문항을 선별하여 표시했습니다.