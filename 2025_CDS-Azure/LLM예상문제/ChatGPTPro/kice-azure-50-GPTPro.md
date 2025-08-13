# Azure Basic Services & Governance (10)

**Q1. (올바른 것)**
 RBAC 스코프 설계에 대한 설명 중 올바른 것을 고르시오. (회사 리전은 Korea Central, DR은 Korea South만 사용)
 A. 사용자에게 리소스 그룹보다 구독 스코프에 먼저 권한을 주는 것이 최소 권한 원칙이다.
 B. 관리그룹에 권한을 주면 테넌트 내 모든 리소스에 자동 상속된다.
 C. 역할 할당은 관리그룹→구독→리소스 그룹→리소스 순으로 ‘필요 최소 스코프’에서 부여한다.
 D. Reader 권한은 데이터 쓰기 작업 일부를 허용한다.
 **정답**: C
 **해설**: RBAC는 스코프가 좁을수록 안전합니다. 관리그룹/구독/리소스 그룹/리소스 중 실제 필요한 최소 스코프에 역할을 부여해야 하며 Reader는 읽기 전용입니다. (주제: RBAC 스코프, 링크: https://learn.microsoft.com/ko-kr/azure/role-based-access-control/scope-overview)

**Q2. (부적절한 것)**
 Azure Policy 효과(Effect) 설명 중 적절하지 않은 것을 고르시오.
 A. deny는 배포 자체를 거부한다.
 B. audit는 비준수 리소스를 탐지만 한다.
 C. modify는 배포 시 리소스 속성을 교체/추가할 수 있다.
 D. Policy는 audit만 지원하며 다른 효과는 없다.
 **정답**: D
 **해설**: Policy는 deny, audit, append, modify 등 다양한 효과를 지원합니다. (주제: Policy 효과, 링크: https://learn.microsoft.com/ko-kr/azure/governance/policy/concepts/effects)

**Q3. (시나리오/올바른 것)**
 김선임은 관리그룹에 표준 태깅 정책을 적용하고 준수 현황을 보고하려 한다. 올바른 방법을 고르시오.
 A. 각 리소스에 수동으로 태그를 넣고 엑셀로 집계한다.
 B. Policy Initiative로 태깅 강제/자동수정 규칙을 묶어 관리그룹에 할당한다.
 C. 리소스 이동만으로 태그가 자동 보완된다.
 D. 예산(Budget) 경보가 태깅을 자동으로 채운다.
 **정답**: B
 **해설**: Initiative(정책 세트)로 표준 정책을 일괄 적용·감사·수정이 가능합니다. (주제: Policy 이니셔티브, 링크: https://learn.microsoft.com/ko-kr/azure/governance/policy/concepts/initiative-definition)

**Q4. (올바른 것)**
 Resource Graph를 활용한 거버넌스 점검으로 올바른 설명은?
 A. 구독별 비용 한도를 직접 변경한다.
 B. 여러 구독의 리소스 상태를 Kusto 쿼리로 집계·조회한다.
 C. VM 크기 변경을 강제한다.
 D. 태그를 자동 보정한다.
 **정답**: B
 **해설**: Resource Graph는 대규모 쿼리/현황 조회에 특화됩니다. (주제: Resource Graph, 링크: https://learn.microsoft.com/ko-kr/azure/governance/resource-graph/overview)

**Q5. (부적절한 것)**
 리소스 잠금 설명 중 부적절한 것은?
 A. Delete 잠금은 삭제를 방지한다.
 B. ReadOnly 잠금은 데이터 평면 쓰기까지 금지한다.
 C. 잠금은 실수 방지에 유용하지만 운영 절차를 고려해야 한다.
 D. 잠금을 걸면 모든 역할이 무시된다.
 **정답**: D
 **해설**: 잠금은 RBAC를 무시하지 않습니다. Owner라도 해제 후 수정해야 합니다. (주제: 리소스 잠금, 링크: https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/lock-resources)

**Q6. (올바른 것)**
 Deny assignment와 RBAC의 차이에 대한 올바른 설명은?
 A. Deny는 허용을 무시하고 특정 작업을 금지한다.
 B. Deny는 RBAC와 동일하다.
 C. Deny는 구독에서만 쓸 수 있다.
 D. Deny는 사용자에만 적용된다.
 **정답**: A
 **해설**: Deny assignment는 허용(Role)보다 강력하게 특정 작업을 차단합니다. (주제: Deny vs RBAC, 링크: https://learn.microsoft.com/ko-kr/azure/role-based-access-control/deny-assignments)

**Q7. (시나리오/부적절한 것)**
 이책임은 Korea South로 리소스를 이동한다. 올바르지 않은 판단은?
 A. 일부 리소스는 구독/리전 이동 제약이 있다.
 B. 종속 리소스 관계를 확인해야 한다.
 C. 이동하면 리소스 ID가 항상 유지된다.
 D. 정책/잠금/권한 영향도 검토가 필요하다.
 **정답**: C
 **해설**: 이동 시 리소스 ID가 바뀌는 경우가 있습니다. (주제: 리소스 이동 제약, 링크: https://learn.microsoft.com/ko-kr/azure/azure-resource-manager/management/move-resource-group-and-subscription)

**Q8. (올바른 것)**
 PIM(Privileged Identity Management) 활용으로 올바른 것은?
 A. 상시 Owner를 기본으로 부여한다.
 B. 필요 시 승인 기반으로 일시적 권한을 상승시킨다.
 C. 승인/알림이 없다.
 D. 비밀번호 만료 연장 기능만 있다.
 **정답**: B
 **해설**: PIM은 Just-In-Time 방식으로 고권한을 최소 기간·승인 기반으로 부여합니다. (주제: PIM, 링크: https://learn.microsoft.com/ko-kr/entra/id-governance/privileged-identity-management/pim-configure)

**Q9. (부적절한 것)**
 Budget/Cost Management에 대한 설명 중 부적절한 것은?
 A. 예산 초과 예상 시 경보를 보낼 수 있다.
 B. 예산 룰로 자동 차단까지 기본 제공한다.
 C. 태그/리소스 그룹별 비용 분류가 가능하다.
 D. 지출 추세 시각화를 제공한다.
 **정답**: B
 **해설**: 예산은 경보 기반입니다(자동 차단은 별도 정책/자동화로 구현). (주제: 비용관리, 링크: https://learn.microsoft.com/ko-kr/azure/cost-management-billing/costs/tutorial-acm-create-budgets)

**Q10. (올바른 것)**
 Load Balancer SKU 선택에 대한 올바른 설명은?
 A. Basic LB는 존 중복/Private 링크 통합이 풍부하다.
 B. Standard LB는 보안 디폴트 거부 모델을 사용한다.
 C. Health Probe는 TCP만 가능하다.
 D. Standard LB는 지역 간 로드밸런싱을 기본 제공한다.
 **정답**: B
 **해설**: Standard LB는 기본 차단 모델·향상된 기능을 제공합니다(Probe는 HTTP/HTTPS 가능). (주제: LB SKU, 링크: https://learn.microsoft.com/ko-kr/azure/load-balancer/skus)

------

# Storage & Data Management (10)

**Q11. (올바른 것)**
 Blob 액세스 티어에 대한 올바른 설명은?
 A. Archive는 즉시 밀리초 수준 접근이 가능하다.
 B. Hot은 빈번 접근, Cool/Archive는 드문 접근에 적합하다.
 C. 티어 변경은 항상 무료다.
 D. Cool은 쓰기 불가다.
 **정답**: B
 **해설**: Hot/빈번, Cool/드문, Archive/장기보관 시나리오로 비용 최적화합니다. (주제: Access Tier, 링크: https://learn.microsoft.com/ko-kr/azure/storage/blobs/access-tiers-overview)

**Q12. (시나리오/부적절한 것)**
 장전임은 업로드 후 서버리스 후처리를 자동화하려 한다. 부적절한 것은?
 A. Blob 이벤트를 Event Grid로 발행한다.
 B. Logic Apps/Function으로 후처리를 연결한다.
 C. Lifecycle 정책만으로 실시간 후처리를 대체한다.
 D. 실패 재시도를 고려한다.
 **정답**: C
 **해설**: Lifecycle은 보존/티어링 자동화이며 이벤트 기반 후처리와 역할이 다릅니다. (주제: 이벤트, 링크: https://learn.microsoft.com/ko-kr/azure/storage/blobs/storage-blob-event-overview)

**Q13. (올바른 것)**
 불변(Immutable) 보존에 대한 올바른 설명은?
 A. 컨테이너/버킷 WORM 정책으로 삭제·수정이 보존 기간 동안 불가하다.
 B. WORM은 버전 관리와 함께 사용할 수 없다.
 C. 임시로 보존 기간을 줄여도 된다.
 D. 감사 목적에 적합하지 않다.
 **정답**: A
 **해설**: 규제·감사 대응에 적합하며 버전 관리와 병행 가능합니다. (주제: WORM, 링크: https://learn.microsoft.com/ko-kr/azure/storage/blobs/immutable-policy-configure-versioning)

**Q14. (부적절한 것)**
 SAS 설계 시 부적절한 것은?
 A. 만료시간을 설정한다.
 B. 필요 최소 권한만 부여한다.
 C. 클라이언트 편의를 위해 만료 없는 SAS를 발행한다.
 D. 소스 IP 제한을 고려한다.
 **정답**: C
 **해설**: 만료 없는 SAS는 위험합니다(최소권한·만료·IP 제한을 권장). (주제: SAS, 링크: https://learn.microsoft.com/ko-kr/azure/storage/common/storage-sas-overview)

**Q15. (올바른 것)**
 스토리지 복제 옵션 설명으로 올바른 것은?
 A. LRS는 단일 데이터센터 내 3중 복제다.
 B. ZRS는 지역 간 복제다.
 C. GRS는 가용영역 복제다.
 D. GZRS는 동일 존만 복제한다.
 **정답**: A
 **해설**: LRS(단일 DC 3중), ZRS(다중 존), GRS/GZRS(교차 지역)로 내결함성을 설계합니다. (주제: 복제, 링크: https://learn.microsoft.com/ko-kr/azure/storage/common/storage-redundancy)

**Q16. (올바른 것)**
 스토리지 암호화에 대한 올바른 설명은?
 A. SSE는 기본 비활성이다.
 B. 고객 관리 키(CMK)로 Key Vault 연동이 가능하다.
 C. CMK 사용 시 방화벽을 꺼야 한다.
 D. CMK는 Blob에만 가능하다.
 **정답**: B
 **해설**: SSE는 기본 활성이며 CMK/Key Vault 연동을 통해 키 관리가 가능합니다. (주제: 암호화, 링크: https://learn.microsoft.com/ko-kr/azure/storage/common/storage-service-encryption)

**Q17. (부적절한 것)**
 Soft Delete/버전 관리/스냅샷 비교에서 부적절한 설명은?
 A. Soft Delete는 삭제 복구에 유용하다.
 B. 버전 관리는 Blob 변경 이력을 유지한다.
 C. 스냅샷은 버전 관리와 동일하다.
 D. 정책 보존기간을 설계해야 한다.
 **정답**: C
 **해설**: 스냅샷과 버전 관리는 개념/기능이 다릅니다. (주제: Soft Delete, 링크: https://learn.microsoft.com/ko-kr/azure/storage/blobs/soft-delete-blob-overview)

**Q18. (시나리오/올바른 것)**
 대용량 순차 읽기 파일 제공에서 WAS 부하를 줄이는 방안으로 올바른 것은?
 A. Access Key를 노출한다.
 B. Azure Files를 계속 사용한다.
 C. Blob Storage에 SAS로 직접 다운로드하게 한다.
 D. Function으로 프록시한다.
 **정답**: C
 **해설**: 순차/대용량은 Blob이 비용·성능에 유리하고 SAS로 최소 권한 직접 접근이 안전합니다. (주제: Blob vs Files, 링크: https://learn.microsoft.com/ko-kr/azure/storage/common/storage-decide-blobs-files-disks)

**Q19. (부적절한 것)**
 Managed Disk 크기 조정 설명 중 부적절한 것은?
 A. 확장은 온라인으로 가능한 경우가 많다.
 B. 축소는 직접 불가하며 마이그레이션이 필요할 수 있다.
 C. 공유 디스크는 연결 해제 등 절차가 필요하다.
 D. 축소는 포털에서 즉시 가능하다.
 **정답**: D
 **해설**: 축소는 직접 지원되지 않아 데이터 마이그레이션이 수반됩니다. (주제: 디스크, 링크: https://learn.microsoft.com/ko-kr/azure/virtual-machines/expand-os-disk)

**Q20. (올바른 것)**
 MI/SQL Database DR 구성 설명 중 올바른 것은?
 A. Auto Failover Group으로 지역 간 단일 엔드포인트를 제공할 수 있다.
 B. Active Geo-Replication은 MI에서만 지원된다.
 C. DBLink는 SQL Database에서 완전 지원된다.
 D. Timezone은 SQL Database에서만 설정된다.
 **정답**: A
 **해설**: AFOG로 단일 엔드포인트·자동 페일오버 구성이 가능하며 MI 기능/제약을 구분해야 합니다. (주제: AFOG/MI, 링크: https://learn.microsoft.com/ko-kr/azure/azure-sql/database/auto-failover-group-overview?view=azuresql)

------

# Network & Security (10)

**Q21. (올바른 것)**
 NAT Gateway 설계로 올바른 것은?
 A. 서브넷에 여러 NAT Gateway를 연결해 가용성을 높인다.
 B. 퍼블릭 IP/Prefix를 NAT GW에 연결해 고정 아웃바운드 IP를 사용한다.
 C. NIC 단위 아웃바운드를 권장한다.
 D. LB가 있으면 NAT GW는 불필요하다.
 **정답**: B
 **해설**: NAT GW는 서브넷당 1개 연결·고정 소스 IP·대규모 SNAT을 제공합니다. (주제: NAT GW, 링크: https://learn.microsoft.com/en-us/azure/nat-gateway/nat-gateway-design)

**Q22. (시나리오/올바른 것)**
 송팀장은 온프레미스–클라우드 하이브리드 DNS를 표준화한다. 올바른 방안은?
 A. Private DNS Resolver 인바운드·아웃바운드 엔드포인트로 포워딩 체인을 구성한다.
 B. 공용 DNS만 사용한다.
 C. 각 VNet에 로컬 DNS 서버를 설치한다.
 D. 모든 존을 공용 DNS에 위임한다.
 **정답**: A
 **해설**: PDR의 In/Out Endpoint로 온프레미스↔Azure간 질의 포워딩을 표준화합니다. (주제: DNS Resolver, 링크: https://learn.microsoft.com/ko-kr/azure/dns/dns-private-resolver-overview)

**Q23. (부적절한 것)**
 ASG(Application Security Group)에 대한 부적절한 설명은?
 A. 동일 VNet 내 NIC를 논리 그룹으로 다룬다.
 B. ASG끼리 규칙으로 참조할 수 있다.
 C. 서로 다른 VNet 간에도 ASG 참조가 가능하다.
 D. NSG 규칙 소스/대상으로 활용한다.
 **정답**: C
 **해설**: ASG는 **동일 VNet 범위**에서만 유효합니다. (주제: NSG/ASG, 링크: https://learn.microsoft.com/ko-kr/azure/virtual-network/network-security-groups-overview)

**Q24. (부적절한 것)**
 ExpressRoute/On-Prem 통신 설명 중 부적절한 것은?
 A. Global Reach로 서로 다른 회선의 온프레미스 간 연결이 가능하다.
 B. Premium SKU로 지역 간 VNet 연결 폭이 넓어진다.
 C. 회선만 있으면 자동으로 VNet↔VNet 라우팅이 된다.
 D. Private Peering은 사설 IP 통신을 제공한다.
 **정답**: C
 **해설**: VNet 간 라우팅은 별도(VNet Peering 등)이며 회선만으로 자동 경로가 생기지 않습니다. (주제: ExpressRoute, 링크: https://learn.microsoft.com/ko-kr/azure/expressroute/expressroute-introduction)

**Q25. (부적절한 것)**
 WAF와 Firewall의 역할 구분에서 부적절한 것은?
 A. WAF는 L7 웹 공격 방어에 강점이 있다.
 B. Azure Firewall은 L3–L7 통합 제어·SNAT/DNAT를 제공한다.
 C. 둘은 완전히 중복되므로 하나만 있으면 된다.
 D. 경계/목적이 다르므로 병행 배치 사례가 많다.
 **정답**: C
 **해설**: 용도가 다르며 보완적으로 함께 쓰입니다. (주제: WAF/Firewall, 링크: https://learn.microsoft.com/ko-kr/azure/firewall/overview)

**Q26. (올바른 것)**
 NSG Flow Logs/Traffic Analytics에 대한 올바른 설명은?
 A. Flow Logs는 트래픽 흐름을 기록하고 분석에 사용할 수 있다.
 B. Packet Capture만 지원한다.
 C. 대상은 VM에 한정된다.
 D. 로그는 저장 불가다.
 **정답**: A
 **해설**: Flow Logs와 Traffic Analytics로 통신 가시성을 확보합니다. (주제: Flow Logs, 링크: https://learn.microsoft.com/ko-kr/azure/network-watcher/network-watcher-nsg-flow-logging-overview)

**Q27. (올바른 것)**
 Private Endpoint 네트워크 정책에 대한 올바른 설명은?
 A. 연결 서브넷에서 Private Endpoint 네트워크 정책을 해제해야 한다.
 B. NSG를 강제하면 연결이 빨라진다.
 C. Service Endpoint가 필요하다.
 D. 공용 IP를 필수로 쓴다.
 **정답**: A
 **해설**: Private Endpoint가 연결된 서브넷은 특정 네트워크 정책 비활성 절차가 필요합니다. (주제: Private Endpoint, 링크: https://learn.microsoft.com/ko-kr/azure/private-link/disable-private-endpoint-network-policy?tabs=network-policy-portal)

**Q28. (올바른 것)**
 VPN Gateway에 대한 올바른 설명은?
 A. 존 중복(Zone-redundant) SKU가 있다.
 B. NAT GW가 있으면 불필요하다.
 C. ExpressRoute와 동시 구성은 불가하다.
 D. 지역 간 연결만 가능하다.
 **정답**: A
 **해설**: VPN GW는 특정 SKU에서 Zone-redundant를 지원합니다. (주제: VPN GW, 링크: https://learn.microsoft.com/ko-kr/azure/vpn-gateway/vpn-gateway-about-vpngateways)

**Q29. (부적절한 것)**
 다수 VNet이 하나의 ExpressRoute Gateway를 공유할 때 부적절한 가정은?
 A. QoS 기능이 없어 특정 VNet이 대역폭을 독점할 수 있다.
 B. 대역폭·분리 설계를 고려해야 한다.
 C. Gateway 수준 QoS로 분할 보장이 된다.
 D. 설계/운영 가이드가 필요하다.
 **정답**: C
 **해설**: Gateway 자체에 QoS 보장이 없으므로 설계 시 주의가 필요합니다. (주제: ExpressRoute FAQ, 링크: https://learn.microsoft.com/ko-kr/azure/expressroute/expressroute-faqs)

**Q30. (올바른 것)**
 Private DNS Zone 링크에 대한 올바른 설명은?
 A. 링크 없이 모든 VNet에서 자동 해석된다.
 B. 쿼리는 공용 DNS로 포워딩된다.
 C. 연결된 VNet에서만 이름 확인이 가능하다.
 D. 퍼블릭 존과 자동 동기화된다.
 **정답**: C
 **해설**: Private DNS Zone은 링크된 VNet 범위에서만 유효합니다. (주제: Private DNS, 링크: https://learn.microsoft.com/ko-kr/azure/dns/private-dns-virtual-network-links)

------

# AKS / Kubernetes (10)

**Q31. (올바른 것)**
 Readiness/Liveness/Startup Probe의 올바른 관계는?
 A. TCP Probe만으로 충분하다.
 B. Startup이 통과되기 전 Liveness가 재시작하지 않게 보호할 수 있다.
 C. Readiness는 Pod 종료를 유도한다.
 D. Liveness는 서비스 등록 시점 제어용이다.
 **정답**: B
 **해설**: Startup은 초기 기동 보호, Readiness는 트래픽 수신 시점, Liveness는 자가 치유에 사용. (주제: Probes, 링크: https://kubernetes.io/ko/docs/tasks/run-application/)

**Q32. (시나리오/올바른 것)**
 이책임은 급증 트래픽에 대응한다. 올바른 방안은?
 A. HPA는 노드 수를 늘린다.
 B. CA는 Pod 수를 늘린다.
 C. HPA는 파드, CA는 노드를 확장한다.
 D. 둘 다 수동이다.
 **정답**: C
 **해설**: HPA=파드, CA=노드 확장입니다. (주제: 오토스케일, 링크: https://learn.microsoft.com/ko-kr/azure/aks/cluster-autoscaler?tabs=azure-cli)

**Q33. (올바른 것)**
 Node Pool 업그레이드 전략으로 올바른 것은?
 A. 단일 풀 즉시 업그레이드만 안전하다.
 B. 신규 풀 추가→드레인→검증 후 기존 풀 업그레이드가 안전하다.
 C. 드레인은 필요 없다.
 D. PDB는 무시한다.
 **정답**: B
 **해설**: 신규 풀(임시)로 워크로드 이동→검증→기존 풀 업그레이드가 무중단에 유리합니다. (주제: 업그레이드, 링크: https://learn.microsoft.com/ko-kr/azure/aks/upgrade-cluster)

**Q34. (부적절한 것)**
 프로브 구성에서 부적절한 것은?
 A. HTTP Readiness 엔드포인트로 실제 서비스 상태를 검증한다.
 B. Liveness는 자가 치유 재시작에 사용한다.
 C. TCP만으로 웹 애플리케이션 정상 동작을 충분히 검증한다.
 D. Startup으로 초기 과대 재시작을 방지한다.
 **정답**: C
 **해설**: TCP는 포트 오픈만 확인하므로 애플리케이션 레벨 검증은 HTTP/HTTPS가 바람직합니다. (주제: Probes)

**Q35. (부적절한 것)**
 네트워크 정책에 대한 부적절한 설명은?
 A. Calico/Azure NP로 Pod 간 통신을 제어한다.
 B. Default-deny로 시작해 필요한 통신만 허용한다.
 C. 공용 노출이 있어야만 정책이 동작한다.
 D. 네임스페이스/레이블로 범위를 지정한다.
 **정답**: C
 **해설**: 공용 노출과 무관합니다. 클러스터 내부 정책입니다. (주제: Network Policy, 링크: https://learn.microsoft.com/ko-kr/azure/aks/use-network-policies)

**Q36. (올바른 것)**
 PSA(Pod Security Admission)의 올바른 설명은?
 A. Baseline/Restricted 프로파일로 정책을 적용할 수 있다.
 B. Azure Policy만으로 대체된다.
 C. PSA는 권장되지 않는다.
 D. PSA는 오브젝트 삭제만 제어한다.
 **정답**: A
 **해설**: PSA는 Pod 보안 레벨을 강제하는 기본 메커니즘입니다. (주제: PSA)

**Q37. (올바른 것)**
 Secrets Store CSI의 올바른 설명은?
 A. etcd에 평문 저장된다.
 B. 외부 비밀 저장소(Key Vault 등)에서 Pod 마운트 형태로 주입한다.
 C. 코드 하드코딩을 권장한다.
 D. 감사 불가다.
 **정답**: B
 **해설**: Key Vault 등과 연동해 런타임 주입·회전이 가능한 패턴입니다. (주제: Secrets Store, 링크: https://learn.microsoft.com/ko-kr/azure/aks/csi-secrets-store-driver)

**Q38. (부적절한 것)**
 프라이빗 AKS 클러스터 설명 중 부적절한 것은?
 A. API 서버는 사설 엔드포인트로만 접근한다.
 B. 점프/프록시 경로를 통한 접근 설계가 필요하다.
 C. 인터넷에서 직접 kube-api에 접근할 수 있다.
 D. 프라이빗 링크/네트워크 경로를 설계한다.
 **정답**: C
 **해설**: Private cluster는 공용 API 노출이 없습니다. (주제: Private AKS, 링크: https://learn.microsoft.com/ko-kr/azure/aks/private-clusters)

**Q39. (시나리오/올바른 것)**
 ACR 이미지를 AKS에서 끌어오려 한다. 올바른 방법은?
 A. ACR 방화벽을 해제한다.
 B. `az aks update --attach-acr`로 풀 권한을 연결한다.
 C. 이미지 Pull Secret을 코드에 하드코딩한다.
 D. 공용으로 ACR을 공개한다.
 **정답**: B
 **해설**: AKS-ACR 연결로 안전한 이미지 풀 권한을 부여합니다. (주제: ACR 통합, 링크: https://learn.microsoft.com/ko-kr/azure/aks/cluster-container-registry-integration)

**Q40. (올바른 것)**
 OOMKilled가 잦을 때 올바른 조치는?
 A. Limit을 줄여서 더 빨리 죽게 한다.
 B. Limit≥Heap(+오버헤드)로 맞추고 요청/할당량을 조정한다.
 C. Probe만 조정한다.
 D. 스왑을 크게 쓴다.
 **정답**: B
 **해설**: 리소스 요청/제한을 워크로드 특성에 맞게 설계해야 OOM을 방지합니다. (주제: 리소스 설정)

------

# CI/CD & Cost Optimization (10)

**Q41. (올바른 것)**
 GitHub Actions Job 간 산출물 전달의 올바른 방법은?
 A. 리포지토리에 바이너리를 커밋한다.
 B. Upload/Download Artifact 액션을 사용한다.
 C. 로그에서 복사/붙여넣기 한다.
 D. 환경 변수로 파일을 담는다.
 **정답**: B
 **해설**: 파일은 아티팩트 기능으로 전달합니다. (파일럿과 동일 형태, 링크: https://docs.github.com/ko/actions/reference/workflow-syntax-for-github-actions) 2024-KICE기출문제

**Q42. (올바른 것)**
 OIDC 기반 클라우드 로그인 보안으로 올바른 것은?
 A. SP 비밀을 레포지토리에 저장한다.
 B. OIDC로 단기 토큰을 교환해 비밀 노출을 줄인다.
 C. 환경 시크릿을 공개 저장소에 둔다.
 D. 브랜치 보호와는 무관하다.
 **정답**: B
 **해설**: OIDC는 시크릿 무저장·단기 자격증명으로 하드코딩 위험을 줄입니다. (주제: OIDC, 링크: https://docs.github.com/ko/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect)

**Q43. (올바른 것)**
 배포 승인/환경 보호에 대한 올바른 설명은?
 A. 환경 보호 규칙으로 승인·대기·비밀 범위를 제어한다.
 B. 승인은 브랜치 보호와 양립 불가다.
 C. 승인은 PR 템플릿으로 대체한다.
 D. 환경은 로그만 남긴다.
 **정답**: A
 **해설**: Environments는 승인·비밀 바인딩 등 배포 보호를 제공합니다. (주제: Environments, 링크: https://docs.github.com/ko/actions/deployment/targeting-different-environments/using-environments-for-deployment)

**Q44. (올바른 것)**
 비밀 스캐닝에 대한 올바른 설명은?
 A. 커밋된 비밀 탐지를 자동화한다.
 B. SP 비밀은 코드에 두어도 된다.
 C. 공개 저장소에만 동작한다.
 D. 민감정보 패턴은 수동만 지원한다.
 **정답**: A
 **해설**: Secret Scanning으로 유출 조기 탐지/조치를 합니다. (주제: Secret Scanning, 링크: https://docs.github.com/ko/code-security/secret-scanning/about-secret-scanning)

**Q45. (부적절한 것)**
 캐시 액션 사용에 대한 부적절한 설명은?
 A. 캐시 키 전략이 빌드 시간을 좌우한다.
 B. 민감정보를 캐시에 넣어도 된다.
 C. 종속성 캐시로 시간·요금을 절감할 수 있다.
 D. 캐시 무결성에 유의한다.
 **정답**: B
 **해설**: 캐시는 민감정보 저장 용도가 아닙니다. (주제: 캐시, 링크: https://docs.github.com/ko/actions/using-workflows/caching-dependencies-to-speed-up-workflows)

**Q46. (올바른 것)**
 Savings Plan/예약(Reserved Instance)에 대한 올바른 설명은?
 A. 장기 약정으로 컴퓨팅 비용을 절감한다.
 B. 사용량과 무관하게 동일 요율이 과금된다.
 C. 스팟보다 항상 싸다.
 D. 교환/환불이 전혀 불가하다.
 **정답**: A
 **해설**: 약정 기반으로 비용을 절감하며 교환/환불 정책은 제한적으로 지원됩니다. (주제: Savings Plan, 링크: https://learn.microsoft.com/ko-kr/azure/cost-management-billing/savings-plan/overview-savings-plan)

**Q47. (올바른 것)**
 Log Analytics 데이터 보존/아카이브 최적화의 올바른 설명은?
 A. 단일 보존만 가능하다.
 B. 보존과 아카이브를 조합해 비용을 줄일 수 있다.
 C. 보존 기간은 비용과 무관하다.
 D. 수집 중단이 기본이다.
 **정답**: B
 **해설**: 보존/아카이브 조합으로 저장비용을 최적화합니다. (주제: 로그 보존, 링크: https://learn.microsoft.com/ko-kr/azure/azure-monitor/logs/logs-data-retention-archive)

**Q48. (부적절한 것)**
 스팟 노드 활용에 대한 부적절한 설명은?
 A. 중단 허용 워크로드에 적합하다.
 B. 핵심 운영 워크로드에도 항상 적합하다.
 C. 선점 시 종료 신호를 처리해야 한다.
 D. 비용 절감에 유리하다.
 **정답**: B
 **해설**: 스팟은 선점 가능성이 있어 핵심 운영 워크로드에는 부적합합니다. (주제: 스팟, 링크: https://learn.microsoft.com/ko-kr/azure/virtual-machine-scale-sets/use-spot)

**Q49. (올바른 것)**
 스케줄링 종료/자동시작을 통한 비용 절감으로 올바른 것은?
 A. Automation/Runbook으로 야간 종료·업무시간 시작을 구현한다.
 B. 포털 접속만으로 자동화된다.
 C. 강제 종료만 있다.
 D. 태깅과 연계 불가다.
 **정답**: A
 **해설**: Automation·태그·Webhook 등으로 유연한 스케줄 제어가 가능합니다. (주제: VM 스케줄, 링크: https://learn.microsoft.com/ko-kr/azure/automation/automation-solution-vm-management)

**Q50. (올바른 것)**
 Terraform 상태/백엔드 보안에 대한 올바른 설명은?
 A. 상태 파일에 비밀이 없으므로 공개 저장소에 둔다.
 B. 원격 백엔드와 잠금/버전관리를 활용한다.
 C. 로컬만 권장한다.
 D. 상태 잠금은 필요 없다.
 **정답**: B
 **해설**: 원격 백엔드+잠금으로 충돌/유실/유출을 방지합니다. (주제: 상태/백엔드, 링크: https://developer.hashicorp.com/terraform/language/settings/backends/configuration)