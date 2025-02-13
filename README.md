# RFC 6749 한국어 번역 문서

이 저장소는 OAuth 2.0 Authorization Framework를 정의하는 **RFC 6749** 문서를 한국어로 번역하는 프로젝트입니다.
OAuth 2.0은 웹, 모바일, API 인증을 위한 표준 프로토콜이며, 본 문서의 정확한 번역을 통해 한국어 사용자가 쉽게 접근할 수 있도록 돕는 것을 목표로 합니다.

## 📖 번역 진행 현황
| 섹션 | 원문 (RFC 6749) | 번역본                                                 |
|------|---------------|-----------------------------------------------------|
| **1. Introduction** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1) | [🔗 번역본](./translated_ko.md#1-소개)                   |
| **1.1. Roles** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.1) | [🔗 번역본](./translated_ko.md#11-역할)                  |
| **1.2. Protocol Flow** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.2) | [🔗 번역본](./translated_ko.md#12-프로토콜-흐름)             |
| **1.3. Authorization Grant** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3) | [🔗 번역본](./translated_ko.md#13-인가-승인)               |
| **1.3.1. Authorization Code** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3.1) | [🔗 번역본](./translated_ko.md#131-인가-코드)              |
| **1.3.2. Implicit** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3.2) | [🔗 번역본](./translated_ko.md#132-암묵적-승인)             |
| **1.3.3. Resource Owner Password Credentials** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3.3) | [🔗 번역본](./translated_ko.md#133-리소스-소유자-비밀번호-자격-증명) |
| **1.3.4. Client Credentials** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.3.4) | [🔗 번역본](./translated_ko.md#134-클라이언트-자격-증명)        |
| **1.4. Access Token** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.4) | [🔗 번역본](./translated_ko.md#14-액세스-토큰)              |
| **1.5. Refresh Token** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.5) | [🔗 번역본](./translated_ko.md#15-리프레시-토큰)             |
| **1.6. TLS Version** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.6) | [🔗 번역본](./translated_ko.md#16-tls-버전)              |
| **1.7. HTTP Redirections** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.7) | [🔗 번역본](./translated_ko.md#17-http-리디렉션)           |
| **1.8. Interoperability** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.8) | [🔗 번역본](./translated_ko.md#18-상호-운용성)              |
| **1.9. Notational Conventions** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-1.9) | [🔗 번역본](./translated_ko.md#19-표기-규칙)               |
| **2. Client Registration** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2) | [🔗 번역본](./translated_ko.md#2-클라이언트-등록)                |
| **2.1. Client Types** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.1) | [🔗 번역본](./translated_ko.md#21-클라이언트-유형)                                              |
| **2.2. Client Identifier** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.2) | [🔗 번역본](./translated_ko.md#22-클라이언트-식별자)                                              |
| **2.3. Client Authentication** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.3) | [🔗 번역본](./translated_ko.md#23-클라이언트-인증)                                              |
| **2.3.1. Client Password** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.3.1) | [🔗 번역본](./translated_ko.md#231-클라이언트-비밀번호)                                              |
| **2.3.2. Other Authentication Methods** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.3.2) | [🔗 번역본](./translated_ko.md#232-기타-인증-방법)                                              |
| **2.4. Unregistered Clients** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-2.4) | [🔗 번역본](./translated_ko.md#24-미등록-클라이언트)                                              |
| **3. Protocol Endpoints** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3) | [🔗 번역본](./translated_ko.md#3-프로토콜-엔드포인트)           |
| **3.1. Authorization Endpoint** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.1) | [🔗 번역본](./translated_ko.md#31-인가-엔드포인트)            |
| **3.1.1. Response Type** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.1.1) | [🔗 번역본](./translated_ko.md#311-응답-유형)              |
| **3.1.2. Redirection Endpoint** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.1.2) | [🔗 번역본](./translated_ko.md#312-리디렉션-엔드포인트)         |
| **3.2. Token Endpoint** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.2) | [🔗 번역본](./translated_ko.md#32-토큰-엔드포인트)            |
| **3.2.1. Client Authentication** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.2.1) | [🔗 번역본](./translated_ko.md#321-클라이언트-인증)           |
| **3.3. Access Token Scope** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-3.3) | [🔗 번역본](./translated_ko.md#33-액세스-토큰-범위)           |
| **4. Obtaining Authorization** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4) | ⏳ 번역 중                                              |
| **4.1. Authorization Code Grant** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1) | ⏳ 번역 중                                              |
| **4.1.1. Authorization Request** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.1) | ⏳ 번역 중                                              |
| **4.1.2. Authorization Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.2) | ⏳ 번역 중                                              |
| **4.1.3. Access Token Request** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.3) | ⏳ 번역 중                                              |
| **4.1.4. Access Token Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.4) | ⏳ 번역 중                                              |
| **4.2. Implicit Grant** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.2) | ⏳ 번역 중                                              |
| **4.2.1. Authorization Request** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.2.1) | ⏳ 번역 중                                              |
| **4.2.2. Access Token Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.2.2) | ⏳ 번역 중                                              |
| **4.3. Resource Owner Password Credentials Grant** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.3) | [🔗 번역본](./translated_ko.md#43-리소스-소유자-비밀번호-자격-증명-승인) |
| **4.3.1. Authorization Request and Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.3.1) | [🔗 번역본](./translated_ko.md#431-인가-요청-및-응답) |
| **4.3.2. Access Token Request** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.3.2) | [🔗 번역본](./translated_ko.md#432-액세스-토큰-요청) |
| **4.3.3. Access Token Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.3.3) | [🔗 번역본](./translated_ko.md#433-액세스-토큰-응답) |
| **4.4. Client Credentials Grant** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4) | [🔗 번역본](./translated_ko.md#44-클라이언트-자격-증명-승인) |
| **4.4.1. Authorization Request and Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4.1) | [🔗 번역본](./translated_ko.md#441-인가-요청-및-응답) |
| **4.4.2. Access Token Request** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4.2) | [🔗 번역본](./translated_ko.md#442-액세스-토큰-요청) |
| **4.4.3. Access Token Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4.3) | [🔗 번역본](./translated_ko.md#443-액세스-토큰-응답) |
| **4.5. Extension Grants** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-4.5) | [🔗 번역본](./translated_ko.md#45-확장-승인) |
| **5. Issuing an Access Token** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-5) | ⏳ 번역 중                                              |
| **5.1. Successful Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-5.1) | ⏳ 번역 중                                              |
| **5.2. Error Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-5.2) | ⏳ 번역 중                                              |
| **6. Refreshing an Access Token** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-6) | ⏳ 번역 중                                              |
| **7. Accessing Protected Resources** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-7) | ⏳ 번역 중                                              |
| **7.1. Access Token Types** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-7.1) | ⏳ 번역 중                                              |
| **7.2. Error Response** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-7.2) | ⏳ 번역 중                                              |
| **8. Extensibility** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8) | ⏳ 번역 중                                              |
| **8.1. Defining Access Token Types** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8.1) | ⏳ 번역 중                                              |
| **8.2. Defining New Endpoint Parameters** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8.2) | ⏳ 번역 중                                              |
| **8.3. Defining New Authorization Grant Types** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8.3) | ⏳ 번역 중                                              |
| **8.4. Defining New Authorization Endpoint Response Types** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8.4) | ⏳ 번역 중                                              |
| **8.5. Defining Additional Error Codes** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-8.5) | ⏳ 번역 중                                              |
| **9. Native Applications** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-9) | [🔗 번역본](./translated_ko.md#9-네이티브-애플리케이션) |
| **10. Security Considerations** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10) | ⏳ 번역 중                                              |
| **10.1. Client Authentication** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.1) | ⏳ 번역 중                                              |
| **10.2. Client Impersonation** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.2) | ⏳ 번역 중                                              |
| **10.3. Access Tokens** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.3) | ⏳ 번역 중                                              |
| **10.4. Refresh Tokens** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.4) | ⏳ 번역 중                                              |
| **10.5. Authorization Codes** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.5) | ⏳ 번역 중                                              |
| **10.6. Authorization Code Redirection URI Manipulation** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.6) | ⏳ 번역 중                                              |
| **10.7. Resource Owner Password Credentials** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.7) | ⏳ 번역 중                                              |
| **10.8. Request Confidentiality** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.8) | ⏳ 번역 중                                              |
| **10.9. Ensuring Endpoint Authenticity** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.9) | ⏳ 번역 중                                              |
| **10.10. Credentials-Guessing Attacks** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.10) | ⏳ 번역 중                                              |
| **10.11. Phishing Attacks** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.11) | ⏳ 번역 중                                              |
| **10.12. Cross-Site Request Forgery** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.12) | ⏳ 번역 중                                              |
| **10.13. Clickjacking** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.13) | ⏳ 번역 중                                              |
| **10.14. Code Injection and Input Validation** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.14) | ⏳ 번역 중                                              |
| **10.15. Open Redirectors** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.15) | ⏳ 번역 중                                              |
| **10.16. Misuse of Access Token to Impersonate Resource Owner in Implicit Flow** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-10.16) | ⏳ 번역 중                                              |
| **11. IANA Considerations** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11) | ⏳ 번역 중                                              |
| **11.1. OAuth Access Token Types Registry** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.1) | ⏳ 번역 중                                              |
| **11.1.1. Registration Template** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.1.1) | ⏳ 번역 중                                              |
| **11.2. OAuth Parameters Registry** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.2) | ⏳ 번역 중                                              |
| **11.2.1. Registration Template** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.2.1) | ⏳ 번역 중                                              |
| **11.2.2. Initial Registry Contents** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.2.2) | ⏳ 번역 중                                              |
| **11.3. OAuth Authorization Endpoint Response Types Registry** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.3) | ⏳ 번역 중                                              |
| **11.3.1. Registration Template** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.3.1) | ⏳ 번역 중                                              |
| **11.3.2. Initial Registry Contents** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.3.2) | ⏳ 번역 중                                              |
| **11.4. OAuth Extensions Error Registry** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.4) | ⏳ 번역 중                                              |
| **11.4.1. Registration Template** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-11.4.1) | ⏳ 번역 중                                              |
| **12. References** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-12) | ⏳ 번역 중                                              |
| **12.1. Normative References** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-12.1) | ⏳ 번역 중                                              |
| **12.2. Informative References** | [🔗 원문](https://datatracker.ietf.org/doc/html/rfc6749#section-12.2) | ⏳ 번역 중                                              |


✅ **번역 참고 자료**
- [RFC 6749 원문](https://datatracker.ietf.org/doc/html/rfc6749#autoid-14)

## 👥 번역자
- **[@w0nder-official](https://github.com/w0nder-official)**
- **[@EarthlyZ9](https://github.com/EarthlyZ9)**
- **[@Carrole](https://github.com/Carrole)**

## 📜 라이선스
본 번역문은 [MIT 라이선스](./LICENSE)를 따릅니다.
RFC 원문은 IETF의 정책에 따라 공개된 문서이며, 본 번역 프로젝트는 비공식 번역을 제공하는 것입니다.

---

🚀 **Team Unchained** 🚀
