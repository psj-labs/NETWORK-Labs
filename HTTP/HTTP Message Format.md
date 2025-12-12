```text
================================================================================
                              HTTP TRANSACTION FLOW
================================================================================

[ Client(Browser) ]
        │
        │   HTTP Request Message
        ▼
[ Server ]
        │
        │   HTTP Response Message
        ▼
[ Client Rendering ]


================================================================================
                           HTTP REQUEST MESSAGE FORMAT
================================================================================

[ Request Line ]
--------------------------------------------------------------------------------
Method SP Request-URI SP HTTP-Version CRLF

예)
GET /login HTTP/1.1


[ Request Headers ]
--------------------------------------------------------------------------------

+-------------------------------------------+----------------------------------+
| Header                                    | Description                      |
+-------------------------------------------+----------------------------------+
| Host                                      | 대상 서버 도메인                                     
| User-Agent                                | 브라우저 / OS 정보                                  
| Referer                                   | 요청 발생 이전 URL                                  
| Origin                                    | CORS 출처 검증                                      
| Accept                                    | 허용 응답 타입                                       
| Accept-Language                           | 선호 언어                                           
| Accept-Encoding                           | 압축 지원 방식                                       
| Connection                                | 연결 관리 (keep-alive, close)                       
| Cookie                                    | 세션 값 전달                                         
| Authorization                             | 사용자 인증 토큰                                     
| Content-Type                              | 요청 바디 데이터 형식                                 
| Content-Length                            | 바디 크기(Byte)                                     
| Cache-Control                             | 캐시 정책 제어                                      
| Upgrade-Insecure-Requests                 | HTTPS 요청 강화                                      
| X-Requested-With                          | Ajax 요청 식별                                       
+-------------------------------------------+----------------------------------+


[ Blank Line ]
--------------------------------------------------------------------------------

[ Request Body ]
--------------------------------------------------------------------------------
POST / PUT 시 전달 데이터

예)
username=admin&password=1234



================================================================================
                           HTTP RESPONSE MESSAGE FORMAT
================================================================================

[ Status Line ]
--------------------------------------------------------------------------------
HTTP-Version SP Status-Code SP Reason-Phrase CRLF

예)
HTTP/1.1 200 OK


[ Response Headers ]
----------------------------------------------------------------------------------

+-------------------------------------------+------------------------------------+
| Header                                    | Description                        |
+-------------------------------------------+------------------------------------+
| Date                                      | 응답 생성 시각                                    
| Server                                    | 웹서버 종류                                          
| Content-Type                              | 응답 데이터 타입                                   
| Content-Length                            | 응답 크기(Byte)                                   
| Set-Cookie                                | 쿠키 저장                                          
| Cache-Control                             | 캐시 정책                                          
| Expires                                   | 캐시 만료 시각                                    
| Location                                  | 리다이렉트 주소                                   
| Transfer-Encoding                         | Chunked 데이터 전송                               
| Access-Control-Allow-Origin               | CORS 허용 출처                                    
| Access-Control-Allow-Credentials          | 인증 허용 여부                                    
| Strict-Transport-Security                 | HTTPS 강제 정책                                   
| Content-Security-Policy                   | XSS 차단 정책                                     
| X-Content-Type-Options                    | MIME Sniffing 방어                                
| X-Frame-Options                           | Clickjacking 방어                                 
| Referrer-Policy                           | Referer 제어 정책                                 
| Permissions-Policy                        | 브라우저 권한 제어                                
+-------------------------------------------+-----------------------------------+


[ Blank Line ]
--------------------------------------------------------------------------------

[ Response Body ]
--------------------------------------------------------------------------------
HTML / JSON / File Binary Data



================================================================================
                       HTTP STATUS LINE COMPLETE TABLE
================================================================================

1xx INFORMATIONAL
--------------------------------------------------------------------------------
100 Continue - 요청 계속 보내도 됨
101 Switching Protocols - 프로토콜 전환
102 Processing - 처리 중임


2xx SUCCESS
--------------------------------------------------------------------------------
200 OK - 정상 처리 완료
201 Created - 새 리소스 생성됨
202 Accepted - 처리 요청 접수됨
204 No Content - 응답 바디 없음
206 Partial Content - 부분 데이터 전송


3xx REDIRECTION
--------------------------------------------------------------------------------
301 Moved Permanently - 영구 이동
302 Found - 임시 이동
303 See Other - 다른 위치 조회
304 Not Modified - 변경 없음 (캐시 사용)
307 Temporary Redirect - 임시 리다이렉트 유지
308 Permanent Redirect - 영구 리다이렉트 유지


4xx CLIENT ERROR
--------------------------------------------------------------------------------
400 Bad Request - 요청 형식 오류
401 Unauthorized - 인증 필요
403 Forbidden - 권한 없음
404 Not Found - 대상 리소스 없음
405 Method Not Allowed - 허용 안 된 메서드
408 Request Timeout - 요청 시간 초과
409 Conflict - 리소스 충돌
410 Gone - 리소스 삭제됨
413 Payload Too Large - 전송 데이터 과다
414 URI Too Long - URL 길이 초과
415 Unsupported Media Type - 미지원 데이터 형식
429 Too Many Requests - 요청 과다 제한


5xx SERVER ERROR
--------------------------------------------------------------------------------
500 Internal Server Error - 서버 내부 오류
501 Not Implemented - 기능 미구현
502 Bad Gateway - 게이트웨이 오류
503 Service Unavailable - 서비스 불가
504 Gateway Timeout - 서버 응답 지연



================================================================================
                       HTTP HEADER SECURITY ATTACK MAP
================================================================================

+----------------------+-------------------------------------------------------+
| Header               | Common Attacks                                        |
+----------------------+-------------------------------------------------------+
| Cookie               | Session Hijacking                                     |
| Authorization        | Token Forgery / Privilege Escalation                  |
| Origin               | CORS Bypass                                           |
| Referer              | Referer Spoofing                                      |
| Content-Type         | File Upload Evasion                                   |
| X-Requested-With     | Ajax Security Bypass                                  |
| Host                 | SSRF / Host Header Injection                          |
+----------------------+-------------------------------------------------------+
```
