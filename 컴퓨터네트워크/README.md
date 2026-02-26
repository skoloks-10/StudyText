# 🌐 컴퓨터 네트워크 학습 기록

> 네트워크 통신의 기초부터 HTTP, TCP/IP까지 웹 개발에 필수적인 네트워크 지식을 학습합니다.

## 📖 학습 로드맵

### 🌍 네트워크 기초 개념 (001~002강)
- **001. 네트워크 개론** - 네트워크의 정의, 노드와 링크, OSI 계층, 프로토콜 스택
- **002. 네트워크 크게 살펴보기** - ISP, 인터넷 백본, 데이터센터, CDN 개념

### 🔗 링크 계층 (003~004강)
- **003. 이더넷** - 이더넷 프레임 구조, MAC 주소, 충돌 감지 (CSMA/CD)
- **004. NIC와 케이블, 허브** - 네트워크 인터페이스 카드, 케이블 종류 (UTP, 광섬유), 허브 동작 원리

### 🖇️ 네트워크 계층과 스위칭 (005~006강)
- **005. 스위치, VLAN, IP 프로토콜** - 스위치 동작, VLAN으로 네트워크 분할, IP 프로토콜 개요
- **006. IP 주소** - IPv4 주소 체계, 서브넷 마스크, CIDR, IPv6 개요

### 📍 라우팅 (007강)
- **007. 라우팅** - 라우팅 테이블, 정적 라우팅, 동적 라우팅 (RIP, OSPF, BGP)

### 🚀 전송 계층 (008~010강)
- **008. 전송 계층 개요** - TCP와 UDP의 차이, 포트 번호, 소켓
- **009. TCP와 UDP** - TCP 신뢰성 (3-way handshake, 흐름 제어), UDP의 빠른 전송
- **010. TCP 흐름 제어 & 혼잡 제어** - 윈도우 크기 조정, AIMD, Slow Start, Fast Recovery

### 📛 응용 계층 (011~015강)
- **011. DNS와 URL** - DNS 쿼리, 도메인 계층, URL 구조, IPv4/IPv6 변환
- **012. HTTP** - HTTP/1.1, HTTP/2, HTTP/3, 메서드 (GET, POST, PUT, DELETE), 상태코드
- **013. HTTP 헤더와 HTTP 기반 기술** - 요청/응답 헤더, 쿠키, 세션, HTTPS, CORS
- **014. 네트워크 심화** - WebSocket, Server-Sent Events, QUIC, mTLS
- **015. 무선 네트워크** - Wi-Fi, 802.11, 셀룰러 네트워크, 5G

---

## 🎯 OSI 모델과 계층별 학습

| 계층 | 주요 프로토콜 | 핵심 개념 | 강의 |
|------|-------------|---------|------|
| **1. 물리 계층** | - | 신호, 케이블, 허브 | 004 |
| **2. 데이터링크** | Ethernet, MAC | MAC 주소, 프레임 | 003, 004 |
| **3. 네트워크** | IP, ICMP | IP 주소, 라우팅 | 005, 006, 007 |
| **4. 전송** | TCP, UDP | 포트, 신뢰성, 속도 | 008, 009, 010 |
| **5. 세션** | - | 연결 관리 | - |
| **6. 표현** | - | 데이터 형식, 암호화 | 013 |
| **7. 응용** | HTTP, DNS | 서비스, 요청/응답 | 011, 012, 013 |

---

## 💡 핵심 개념 정리

### 1. TCP 3-Way Handshake (연결 수립)
```
Client                                Server
   |                                    |
   |------- SYN (seq=x) ------------>   |
   |                                    |
   |   <------ SYN-ACK (seq=y, ack=x+1) |
   |                                    |
   |------- ACK (seq=x+1, ack=y+1) --> |
   |                                    |
   |---------- 데이터 전송 ----------->  |
```

### 2. IP 주소 체계
```
IPv4: 192.168.1.100 (32비트, 4옥텟)
  - 클래스 A: 0.0.0.0 ~ 127.255.255.255 (대규모 네트워크)
  - 클래스 B: 128.0.0.0 ~ 191.255.255.255 (중규모 네트워크)
  - 클래스 C: 192.0.0.0 ~ 223.255.255.255 (소규모 네트워크)

서브넷 마스크: 192.168.1.0/24
  - /24 = 255.255.255.0 (앞 24비트가 네트워크 주소, 뒤 8비트가 호스트 주소)
```

### 3. HTTP 메서드와 상태코드
```
메서드:
- GET: 데이터 조회 (캐시 가능)
- POST: 데이터 생성 (바디에 담음)
- PUT: 데이터 수정 (전체 교체)
- DELETE: 데이터 삭제
- PATCH: 데이터 부분 수정

상태코드:
- 2xx: 성공 (200 OK, 201 Created)
- 3xx: 리다이렉션 (301 Moved, 304 Not Modified)
- 4xx: 클라이언트 오류 (400 Bad Request, 404 Not Found)
- 5xx: 서버 오류 (500 Internal Server Error, 503 Service Unavailable)
```

### 4. DNS 쿼리 프로세스
```
사용자 컴퓨터
    |
    v
로컬 DNS 리졸버 (운영체제)
    |
    v
재귀적 리졸버 (ISP DNS 서버)
    |
    v
루트 네임서버 → TLD 네임서버 → 권한있는 네임서버
    |
    v
IP 주소 반환
```

### 5. TCP vs UDP 비교
| 특성 | TCP | UDP |
|------|-----|-----|
| **신뢰성** | ✓ (오류 검사, 재전송) | ✗ |
| **순서** | ✓ (순서대로) | ✗ |
| **속도** | 느림 | 빠름 |
| **오버헤드** | 많음 | 적음 |
| **사용처** | 파일 전송, 이메일, 웹 | 스트리밍, 게임, VoIP |

---

## 🛠️ 네트워크 도구와 명령어

```bash
# IP 주소 확인
ipconfig              # Windows
ifconfig              # Mac/Linux

# DNS 조회
nslookup google.com
dig google.com

# 핑 테스트 (연결 여부 확인)
ping google.com

# 경로 추적 (홉 확인)
tracert google.com    # Windows
traceroute google.com # Mac/Linux

# 포트 확인
netstat -an           # 열린 포트 확인
ss -tlnp              # Linux 소켓 상태

# 네트워크 패킷 캡처
wireshark             # GUI 도구
tcpdump               # CLI 도구

# HTTP 요청
curl https://api.github.com/users/github
wget https://example.com
```

---

## 🌐 웹 개발과의 연결

### 요청-응답 흐름
```
1. 사용자가 브라우저에 URL 입력
2. DNS 쿼리 → IP 주소 획득
3. TCP 3-way handshake로 연결 수립
4. HTTPS로 TLS 핸드셰이크 (암호화)
5. HTTP 요청 전송 (GET, POST 등)
6. 서버에서 HTTP 응답 반환 (HTML, JSON 등)
7. 브라우저가 응답 렌더링
8. TCP 4-way handshake로 연결 종료 (또는 Keep-Alive)
```

### HTTP 요청/응답 예시
```http
# 요청
GET /api/users HTTP/1.1
Host: api.example.com
User-Agent: Mozilla/5.0
Accept: application/json
Authorization: Bearer token123

# 응답
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 256
Set-Cookie: session_id=abc123

[
  {"id": 1, "name": "John Doe"}
]
```

---

## 📚 학습 방법

1. **순차 학습**: 001강부터 차례대로 진행 (계층별 이해)
2. **시각화**: 각 강의의 개념을 그림으로 그려보기
3. **네트워크 도구 실습**: 실제로 ping, nslookup, wireshark 사용해보기
4. **복습 계획**:
   - 1주일 후: TCP/IP 핵심 (3-way, IP 주소)
   - 1달 후: 전체 OSI 계층 체계 정리

---

## 🎓 웹 개발 연계 학습

### 필수 이해 분야
- **프론트엔드**: HTTP, DNS, HTTPS, CORS, WebSocket
- **백엔드**: TCP/UDP, 포트, 소켓 프로그래밍, DNS
- **DevOps**: 라우팅, VLAN, 로드 밸런싱, CDN

### 다음 단계
- **웹 서버**: Nginx, Apache 구성
- **보안**: SSL/TLS, HSTS, CORS, WAF
- **성능 최적화**: HTTP/2, HTTP/3, 압축, 캐싱

---

## 📖 참고 자료

- MDN Web Docs - HTTP: https://developer.mozilla.org/en-US/docs/Web/HTTP
- CompTIA Network+ 공부 가이드
- Wireshark 사용 가이드: https://www.wireshark.org/
- TCP/IP 일러스트 가이드: Stevens의 저작

---

**마지막 업데이트**: 2026-02-26

