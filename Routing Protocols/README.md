# Routing protocols

#### A routing protocol allows routers to exchange route information and automatically calculate the optimal path based on that information. All documentation is provided in Korean.

![RoutingProtocols](/Routing%20Protocols/RoutingProtocols.png)

| Protocol | Type | Scope | Routing Method | Metric / Criteria | Convergence | Scalability | Typical Use |
|----------|------|-------|----------------|-------------------|-------------|-------------|-------------|
| **RIP** | IGP | Intra-AS | Distance-Vector | Hop Count | Slow | Low | Small networks |
| **OSPF** | IGP | Intra-AS | Link-State | Cost (Bandwidth) | Fast | High | Enterprise networks |
| **IS-IS** | IGP | Intra-AS | Link-State | Cost | Very Fast | Very High | ISP / Carrier backbone |
| **BGP** | EGP | Inter-AS | Path-Vector | Policy / Attributes | Slow | Very High | Internet backbone |

---

## 한국어 원문

#### 라우팅 프로토콜은 라우터들이 서로 경로 정보를 교환하고 그 정보를 기반으로 최적의 경로를 자동으로 계산하도록 해주는 프로토콜입니다. 모든 문서는 한국어로 제공됩니다.

| 프로토콜 | 분류 | 사용 범위 | 라우팅 방식 | 메트릭 / 기준 | 수렴 속도 | 확장성 | 주요 사용처 |
|---------|------|-----------|-------------|---------------|-----------|--------|-------------|
| **RIP** | IGP | AS 내부 | Distance-Vector | Hop Count | 느림 | 낮음 | 소규모 네트워크 |
| **OSPF** | IGP | AS 내부 | Link-State | Cost (대역폭) | 빠름 | 높음 | 기업/엔터프라이즈 |
| **IS-IS** | IGP | AS 내부 | Link-State | Cost | 매우 빠름 | 매우 높음 | ISP/통신사 백본 |
| **BGP** | EGP | AS 간 | Path-Vector | Policy / Attribute | 느림 | 매우 높음 | 인터넷 백본 |
