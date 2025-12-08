```text
################################################################################
                               MIME HEADER STRUCTURE
################################################################################

┌──────────────────────────────────────────────────────────────────────────────┐
│ MIME-Version: 1.0                                                            │
│ → MIME 규격 사용 선언 (항상 1.0 고정)                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│ Content-Type: <type>/<subtype>; charset="UTF-8"; boundary="BOUNDARY"         │
│ → MIME 데이터 타입 및 서브타입 지정                                                 │
├──────────────────────────────────────────────────────────────────────────────┤
│ Content-Transfer-Encoding: <encoding>                                        │
│ → 데이터 전송 인코딩 방식 지정                                                      │
├──────────────────────────────────────────────────────────────────────────────┤
│ Content-Disposition: <disposition>; filename="file.ext"                      │
│ → 첨부파일 여부 및 파일 이름 지정                                                   │
├──────────────────────────────────────────────────────────────────────────────┤
│ Content-ID: <id>                                                             │
│ → 메시지 내부 참조용 식별자 (cid 내장 이미지 등)                                       │
├──────────────────────────────────────────────────────────────────────────────┤
│ Content-Description: <text>                                                  │
│ → 본문 또는 첨부 데이터 설명                                                       │
└──────────────────────────────────────────────────────────────────────────────┘



################################################################################
                       MIME DATA TYPE / SUBTYPE TABLE
################################################################################

text
 ├── plain          → 일반 텍스트 메일
 ├── html           → HTML 메일
 ├── css            → 스타일시트

image
 ├── jpeg           → JPEG 이미지
 ├── png            → PNG 이미지
 ├── gif            → GIF 이미지
 ├── bmp            → BMP 이미지
 ├── webp           → WEBP 이미지
 ├── svg+xml        → SVG 벡터 이미지

audio
 ├── mpeg           → MP3 오디오
 ├── wav            → WAV 오디오
 ├── ogg            → OGG 오디오

video
 ├── mp4            → MP4 비디오
 ├── webm           → WEBM 비디오
 ├── ogg            → OGG 비디오

application
 ├── pdf                          → PDF 문서
 ├── zip                          → ZIP 압축파일
 ├── gzip                         → GZIP 압축
 ├── json                         → JSON 데이터
 ├── xml                          → XML 데이터
 ├── msword                       → Word (.doc)
 ├── vnd.ms-excel                 → Excel (.xls)
 ├── vnd.ms-powerpoint            → PPT (.ppt)
 ├── vnd.openxmlformats-officedocument.wordprocessingml.document
 │                                 → Word (.docx)
 ├── vnd.openxmlformats-officedocument.spreadsheetml.sheet
 │                                 → Excel (.xlsx)
 ├── vnd.openxmlformats-officedocument.presentationml.presentation
 │                                 → PPT (.pptx)
 ├── octet-stream                 → 일반 이진 파일(위험 첨부 기본형)
 ├── x-msdownload                 → 실행파일 (.exe)
 ├── javascript                   → JavaScript 파일

multipart
 ├── mixed        → 기본 첨부 구조(텍스트 + 파일 혼합)
 ├── alternative  → text/plain + text/html 대체 형식
 ├── related      → HTML 본문 + 내부 리소스 묶음
 └── form-data    → 폼 전송 데이터

message
 ├── rfc822       → 첨부된 이메일 원문
 └── partial      → 분할 이메일 조각



################################################################################
                   MIME TRANSFER ENCODING METHODS
################################################################################

7bit
 → 기본 ASCII 인코딩

8bit
 → 확장 ASCII 인코딩

base64
 → 이진파일 인코딩 표준 (첨부파일 대부분 사용)

quoted-printable
 → 텍스트 압축 인코딩 (한글 깨짐 방지)

binary
 → 원본 이진 데이터 (거의 미사용)
