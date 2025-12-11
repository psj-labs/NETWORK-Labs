# 1. OSPF 개요

→ **OSPF는 링크 상태 정보를 기반으로 네트워크 전체 토폴로지를 구성하고, SPF 알고리즘으로 최단 경로를 계산하는 IGP이다.**

- 프로토콜 번호: **IP Protocol 89**  
- 동적 라우팅 프로토콜  
- Link-State 기반  
- 대규모 네트워크에 적합  
- 계층적 구조(Area) 지원


# 2. OSPF 동작 과정

1. **Hello 패킷 교환 → Neighbor 관계 형성**  
2. **DBD(데이터베이스 설명) 교환 → LSDB 비교**  
3. **LSR/LSU로 LSA 동기화**  
4. **LSA Flooding** – Area 전체로 링크 상태 정보 전파  
5. **LSDB(Link-State Database) 완성**  
6. **SPF(Dijkstra) 알고리즘 실행 → 최단경로 계산**  
7. **라우팅 테이블(RIB)에 반영**  
8. Topology 변경 발생 시 즉각 재계산  
9. LSA Refresh 주기: **30분**


# 3. OSPF 링크 유형

1. **Point-to-Point Link**  
   - 두 라우터가 직접 1:1 연결  
   - DR/BDR 불필요

2. **Transit Link**  
   - Ethernet 등 멀티액세스 네트워크  
   - DR/BDR 선출

3. **Stub Link**  
   - 호스트처럼 끝단에 연결되는 구조

4. **Virtual Link**  
   - Area 0(Backbone)과 직접 연결되지 못한 Area를  
     **임시로 Backbone에 우회 연결**하는 논리적 링크  
   - 예외적인 연결 방식


# 4. OSPF Area 구조

## ■ Area 개념
OSPF는 네트워크를 Area로 나누어 **계층적 구조**로 운영한다.

## ■ Area 0 (Backbone Area)
- 모든 Area는 **Area 0과 직접 또는 Virtual Link로 연결**  
- OSPF 전체의 중심  
- 라우팅 정보의 집결 지점

### “모든 트래픽이 백본을 지나냐?”  
→ **라우팅 정보는 백본을 경유하지만, 실제 데이터 패킷은 최적 경로로 이동한다.**


## ■ ABR (Area Border Router)
- 서로 다른 Area를 연결하는 라우터  
- 한 인터페이스는 반드시 Area 0  
- Summary LSA(Type 3) 생성


## ■ ASBR (Autonomous System Boundary Router)
- 외부 라우팅 프로토콜(BGP, RIP 등)과 연결  
- External LSA(Type 5) 생성


# 5. OSPF LSA 종류 

| Type | 이름 | 설명 |
|------|------|------|
| **1** | Router LSA | Area 내부 라우터의 링크 상태 정보 |
| **2** | Network LSA | DR이 생성, 멀티액세스 네트워크 구조 |
| **3** | Summary LSA | ABR이 다른 Area에 경로 전달 |
| **4** | ASBR Summary LSA | ASBR의 위치 정보 전달 |
| **5** | AS External LSA | OSPF 외부에서 온 경로 (ASBR 생성) |
| **7** | NSSA External LSA | NSSA 내부에서 외부 경로 전달 |

※ Type 6, 8, 9~11은 특별 목적이라 일반 OSPF에서 거의 사용되지 않음.


# 6. DR / BDR (Designated Router)

## ■ 왜 필요한가?
멀티액세스 네트워크(Ethernet 등)에서  
라우터들이 서로 모든 LSA를 교환하면 **LSA 폭발(LSA Storm)** 발생  
→ DR이 대신 정리해서 전달함.

## ■ 역할
- DR: 멀티액세스 네트워크 대표  
- BDR: DR 백업

## ■ 선출 기준
1) **OSPF Priority** (높을수록 우선)  
2) **Router ID** (숫자가 클수록 우선)


# 7. OSPF Cost 계산
```text
OSPF는 경로를 "Cost" 기반으로 선택한다.
```

- 기본 Reference BW = 100Mbps (Cisco)  
- 대역폭이 높을수록 Cost가 낮고 → 경로 선호도 ↑


# 8. OSPF LSDB(Link-State Database)

- OSPF의 두뇌 역할  
- Area 내 모든 라우터가 **동일한 LSDB를 공유**  
- LSDB 기반으로 SPF 계산을 수행


# 9. OSPF Neighbor 상태 (전체 상태)

1) **Down**  
2) **Init**  
3) **2-Way**  
4) **ExStart**  
5) **Exchange**  
6) **Loading**  
7) **Full**

Full 상태가 되면 LSDB가 완전히 동기화된 것.


# 10. OSPF Hello Packet

Hello 패킷은 Neighbor 형성 및 유지에 사용됨.

- Hello Interval  
- Dead Interval  
- Router Priority  
- DR/BDR 정보  
- Neighbor 리스트 포함

Hello 설정이 다르면 Neighbor 형성이 되지 않음.


# 11. OSPF 주요 특징 요약

- Link-State 기반  
- Loop-free 구조(SPF)  
- Area 기반 계층도 지원  
- 빠른 수렴  
- 대규모 네트워크 적합  
- 멀티패스 지원(ECMP)
