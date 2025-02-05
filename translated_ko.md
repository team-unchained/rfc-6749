# The OAuth 2.0 Authorization Framework

### 초록 (Abstract)

OAuth 2.0 인증 프레임워크는 서드파티 애플리케이션이 HTTP 서비스에 제한적인 접근 권한을 얻을 수 있도록 합니다. 이는 리소스 소유자(Resource Owner)를 대신하여 리소스 소유자와 HTTP 서비스 간의 승인 절차를 조정함으로써 이루어질 수도 있으며, 또는 서드파티 애플리케이션이 독자적으로 접근 권한을 획득할 수도 있습니다. 본 사양은 RFC 5849에서 정의된 OAuth 1.0 프로토콜을 대체하며, 이를 폐기합니다.

### 이 문서의 상태 (Status of This Memo)

이 문서는 인터넷 표준 트랙(Internet Standards Track) 문서입니다.

본 문서는 **인터넷 엔지니어링 태스크 포스(IETF)** 의 산출물로, IETF 커뮤니티의 합의를 반영하고 있습니다. 또한, 공공 검토를 거쳤으며, **인터넷 엔지니어링 지도 그룹(IESG)** 에 의해 공식적으로 출판이 승인되었습니다. 인터넷 표준에 대한 추가 정보는 RFC 5741의 2장에서 확인할 수 있습니다.

이 문서의 현재 상태, 정정(errata) 사항, 그리고 피드백 제공 방법에 대한 정보는 다음 링크에서 확인할 수 있습니다:
🔗 http://www.rfc-editor.org/info/rfc6749

### 저작권 공지 (Copyright Notice)

이 문서의 저작권은 2012년 IETF Trust 및 문서의 저자로 명시된 개인들에게 있습니다. 모든 권리는 보호됩니다.

이 문서는 BCP 78 및 IETF Trust의 법적 조항(🔗 http://trustee.ietf.org/license-info)의 적용을 받으며, 해당 문서가 출판된 날짜의 기준으로 효력이 발생합니다. 사용자는 위의 법적 조항을 신중히 검토해야 하며, 이는 본 문서의 사용 및 제한 사항을 설명하고 있습니다.

이 문서에서 추출된 코드 컴포넌트(Code Components)는 **간소화된 BSD 라이선스(Simplified BSD License)** 에 명시된 라이선스 조항을 포함해야 합니다. 해당 라이선스 조항은 Trust Legal Provisions의 4.e 항목에 설명되어 있으며, 제공되는 코드에는 보증이 적용되지 않습니다.

## 목차

**1. [소개](#1-소개)**
- [1.1. 역할](#11-역할)
  - [1.2. 프로토콜 흐름](#12-프로토콜-흐름)
  - [1.3. 인가 승인](#13-인가-승인)
      - [1.3.1. 인가 코드](#131-인가-코드)
      - [1.3.2. 암묵적 승인](#132-암묵적-승인)
      - [1.3.3. 리소스 소유자 비밀번호 자격 증명](#133-리소스-소유자-비밀번호-자격-증명)
      - [1.3.4. 클라이언트 자격 증명](#134-클라이언트-자격-증명)
  - [1.4. 액세스 토큰](#14-액세스-토큰)
  - [1.5. 리프레시 토큰](#15-리프레시-토큰)
  - [1.6. TLS 버전](#16-tls-버전)
  - [1.7. HTTP 리디렉션](#17-http-리디렉션)
  - [1.8. 상호 운용성](#18-상호-운용성)
  - [1.9. 표기 규칙](#19-표기-규칙)

**2. [클라이언트 등록](#2-클라이언트-등록)**
- [2.1. 클라이언트 유형](#21-클라이언트-유형)
- [2.2. 클라이언트 식별자](#22-클라이언트-식별자)
- [2.3. 클라이언트 인증](#23-클라이언트-인증)
    - [2.3.1. 클라이언트 비밀번호](#231-클라이언트-비밀번호)
    - [2.3.2. 기타 인증 방법](#232-기타-인증-방법)
- [2.4. 미등록 클라이언트](#24-미등록-클라이언트)

**3. [프로토콜 엔드포인트](#3-프로토콜-엔드포인트)**
- [3.1. 인증 엔드포인트](#31-인가-엔드포인트)
    - [3.1.1. 응답 유형](#311-응답-유형)
    - [3.1.2. 리디렉션 엔드포인트](#312-리디렉션-엔드포인트)
- [3.2. 토큰 엔드포인트](#32-토큰-엔드포인트)
    - [3.2.1. 클라이언트 인가](#321-클라이언트-인증)
- [3.3. 액세스 토큰 범위](#33-액세스-토큰-범위)

**4. [인가 승인 받기](#4-인가-승인-받기)**
- [4.1. 인가 코드 승인](#41-인가-코드-승인)
    - [4.1.1. 인가 요청](#411-인가-요청)
    - [4.1.2. 인가 응답](#412-인가-응답)
    - [4.1.3. 액세스 토큰 요청](#413-액세스-토큰-요청)
    - [4.1.4. 액세스 토큰 응답](#414-액세스-토큰-응답)
- [4.2. 암묵적 승인](#42-암묵적-승인)
    - [4.2.1. 인가 요청](#421-인가-요청)
    - [4.2.2. 액세스 토큰 응답](#422-액세스-토큰-응답)
- [4.3. 리소스 소유자 비밀번호 자격 증명 승인](#43-리소스-소유자-비밀번호-자격-증명-승인)
    - [4.3.1. 인가 요청 및 응답](#431-인가-요청-및-응답)
    - [4.3.2. 액세스 토큰 요청](#432-액세스-토큰-요청)
    - [4.3.3. 액세스 토큰 응답](#433-액세스-토큰-응답)
- [4.4. 클라이언트 자격 증명 승인](#44-클라이언트-자격-증명-승인)
    - [4.4.1. 인가 요청 및 응답](#441-인가-요청-및-응답)
    - [4.4.2. 액세스 토큰 요청](#442-액세스-토큰-요청)
    - [4.4.3. 액세스 토큰 응답](#443-액세스-토큰-응답)
- [4.5. 확장 승인](#45-확장-승인)


**5. [액세스 토큰 발급](#5-엑세스-토큰-발급)**
- [5.1. 성공 응답](#51-성공-응답)
- [5.2. 오류 응답](#52-오류-응답)


**6. [액세스 토큰 갱신](#5-액세스-토큰-갱신)**


**7. [보호된 리소스 접근](7-보호된-리소스-접근)**
- [7.1. 액세스 토큰 유형](#71-액세스-토큰-유형)
- [7.2. 오류 응답](#72-오류-응답)


**8. [확장성](#8-확장성)**
- [8.1. 액세스 토큰 유형 정의](#81-액세스-토큰-유형-정의)
- [8.2. 새로운 엔드포인트 매개변수 정의](#82-새로운-엔드포인트-매개변수-정의)
- [8.3. 새로운 인가 승인 유형 정의](#83-새로운-인가-승인-유형-정의)
- [8.4. 새로운 인가 엔드포인트 응답 유형 정의](#84-새로운-인가-엔드포인트-응답-유형-정의)
- [8.5. 추가 오류 코드 정의](#85-추가-오류-코드-정의)

**9. [네이티브 애플리케이션](#9-네이티브-애플리케이션)**

**10. [보안 고려 사항](#10-보안-고려-사항)**
- [10.1. 클라이언트 인증](#101-클라이언트-인증)
- [10.2. 클라이언트 사칭](#102-클라이언트-사칭)
- [10.3. 액세스 토큰](#103-액세스-토큰)
- [10.4. 리프레시 토큰](#104-리프레시-토큰)
- [10.5. 인가 코드](#105-인가-코드)
- [10.6. 인가 코드 리디렉션 URI 조작](#106-인가-코드-리디렉션-uri-조작)
- [10.7. 리소스 소유자 비밀번호 자격 증명](#107-리소스-소유자-비밀번호-자격-증명)
- [10.8. 요청 기밀성 유지](#108-요청-기밀성-유지)
- [10.9. 엔드포인트의 신뢰성 확보](#109-엔드포인트의-신뢰성-확보)
- [10.10. 자격 증명 추측 공격](#1010-자격-증명-추측-공격)
- [10.11. 피싱 공격](#1011-피싱-공격)
- [10.12. 크로스 사이트 요청 위조 (CSRF)](#1012-크로스-사이트-요청-위조-csrf)
- [10.13. 클릭재킹](#1013-클릭재킹)
- [10.14. 코드 삽입 및 입력 검증](#1014-코드-삽입-및-입력-검증)
- [10.15. 오픈 리디렉터](#1015-오픈-리디렉터)
- [10.16. 암묵적 승인 흐름에서 액세스 토큰 오용](#1016-암묵적-승인-흐름에서-액세스-토큰-오용)

**11. [IANA 고려 사항](#11-IANA-고려-사항)**
- [11.1. OAuth 액세스 토큰 유형 등록](#111-oauth-액세스-토큰-유형-등록)
    - [11.1.1. 등록 템플릿](#1111-등록-템플릿)
- [11.2. OAuth 매개변수 등록](#112-oauth-매개변수-등록)
    - [11.2.1. 등록 템플릿](#1121-등록-템플릿)
    - [11.2.2. 초기 등록 내용](#1122-초기-등록-내용)
- [11.3. OAuth 인가 엔드포인트 응답 유형 등록](#113-oauth-인가-엔드포인트-응답-유형-등록)
    - [11.3.1. 등록 템플릿](#1131-등록-템플릿)
    - [11.3.2. 초기 등록 내용](#1132-초기-등록-내용)
- [11.4. OAuth 확장 오류 등록](#114-oauth-확장-오류-등록)
    - [11.4.1. 등록 템플릿](#1141-등록-템플릿)


**12. [참고 문헌](#12-참고-문헌)**
- [12.1. 규범적 참고 문헌](#121-규범적-참고-문헌)
- [12.2. 정보성 참고 문헌](#122-정보성-참고-문헌)

## 1. 소개

## 2. 클라이언트 등록
OAuth 2.0 프로토콜을 시작하기 전, 클라이언트는 인가 서버에 등록해야 합니다. 
클라이언트가 인가 서버에 등록하는 방법은 이 명세의 범위를 벗어나지만 일반적으로 HTML 등록 양식을 통해 엔드 유저와 상호 작용하는 것을 포함합니다.

클라이언트 등록 과정은 클라이언트와 인가 서버 간의 직접적인 상호 작용을 필수로 요구하지 않습니다.
인가 서버가 지원하기만 한다면, 상호 간 신뢰를 확립하고 필요한 클라이언트 속성 (예: 리다이렉션 URI, 클라이언트 타입) 을 얻기 위해 다른 방법을 사용할 수 있습니다.
예를 들어, 클라이언트 등록 과정은 자체적으로 또는 제3자가 발급한 증명서를 사용하거나 
신뢰할 수 있는 창구를 통해 인가 서버가 클라이언트를 탐색하여 등록을 수행하는 방식이 될 수 있습니다.

클라이언트를 등록할 때, 클라이언트 개발자는 다음을 수행해야 합니다 (SHALL).

* 2.1절에서 설명한 클라이언트 유형을 지정해야 합니다.    
* 3.1.2절에서 설명한 클라이언트 리다이렉션 URI를 제공해야 합니다.
* 인가 서버가 요구하는 다른 정보를 포함해야 합니다. (예: 애플리케이션 이름, 웹사이트, 설명, 로고 이미지, 약관 동의 등)

### 2.1 클라이언트 유형
OAuth는 클라이언트가 인가 서버와 안전하게 인증할 수 있는 능력 (예: 클라이언트 자격 증명의 기밀성을 유지할 수 있는 능력) 
에 따라 두 가지 클라이언트 유형을 정의합니다.

* 신뢰할 수 있는 클라이언트 (confidential)
  * 자격 증명의 기밀성을 유지할 수 있는 클라이언트 (예: 클라이언트의 기밀 정보에 제한된 액세스를 가진 안전한 서버에 구현된 클라이언트) 
  * 또는 다른 방법을 사용하여 안전한 클라이언트 인증이 가능한 클라이언트

* 공개 클라이언트 (public) 
  * 자격 증명의 기밀성을 유지할 수 없는 클라이언트 (예: 리소스 소유자가 사용하는 장치에 설치된 네이티브 애플리케이션 또는 웹 브라우저 기반 애플리케이션)
  * 다른 방법으로 안전한 클라이언트 인증이 불가능한 클라이언트

클라이언트 유형의 지정은 
인가 서버가 정의하는 안전한 인증이 무엇인지와 클라이언트 자격 증명의 노출을 어느 정도로 허용할지의 기준에 기반합니다. 인가 서버는 클라이언트 유형에 대한 가정을 해서는 안됩니다 (SHOULD NOT).

어떤 클라이언트는 서로 다른 클라이언트 유형과 보안 컨텍스트를 가진 분산된 구성 요소들의 집합으로 구현될 수도 있습니다. 
(예: 기밀 서버 기반 구성 요소와 공개 브라우저 기반 구성 요소를 모두 가진 분산 클라이언트). 
인증 서버가 이러한 유형의 클라이언트를 지원하지 않거나 클라이언트 등록에 대한 지침을 제공하지 않는 경우,
클라이언트는 각 구성 요소를 별개의 클라이언트로 등록해야 합니다 (SHOULD).

이 명세는 다음 클라이언트 프로필을 기반으로 작성되었습니다:
* web application (웹 어플리케이션)
  * 웹 어플리케이션은 웹 서버에서 실행되는 신뢰할 수 있는 클라이언트 (confidential client) 입니다. 리소스 소유자는 리소스 소유자가 사용하는 기기의 사용자 에이전트 (user-agent) 에서 렌더링된 HTML 사용자 인터페이스를 통해 클라이언트에 접근합니다. 클라이언트 자격 증명과 클라이언트에게 발급된 액세스 토큰은 웹 서버에 저장되어 리소스 소유자에게 노출되거나 접근할 수 없습니다.
* user-agent-based application (사용자 에이전트 기반 어플리케이션)
  * 사용자 에이전트 기반 어플리케이션은 클라이언트 코드가 웹 서버로부터 다운로드되고 리소스 소유자가 사용하는 기기의 사용자 에이전트 (예: 웹 브라우저) 내에서 실행되는 공개 클라이언트 (public client) 입니다. 프로토콜 데이터와 자격 증명은 리소스 소유자에게 쉽게 접근 가능하며 때로는 보이기도 합니다. 이러한 어플리케이션은 사용자 에이전트 내에 존재하기 때문에 인가 요청 시 사용자 에이전트 기능을 원활하게 사용할 수도 있습니다.
* native application (네이티브 어플리케이션)
  *  네이티브 어플리케이션은 리소스 소유자가 사용하는 기기에 설치 및 실행되는 공개 클라이언트입니다. 프로토콜 데이터와 자격 증명은 리소스 소유자에 의해 접근 가능하며 어플리케이션 내 클라이언트 인증 자격 증명은 추출될 수 있다고 가정합니다. 반면에 동적으로 발급되는 자격 증명 (액세스 토큰 또는 리프레시 토큰)은 적절한 수준의 보호를 받을 수 있습니다. 최소한 이러한 자격 증명은 어플리케이션이 상호 작용할 수 있는 악의적인 서버로부터 보호됩니다. 일부 플랫폼에서는 이러한 자격 증명이 동일한 기기에 존재하는 다른 어플리케이션으로부터 보호될 수도 있습니다.
   
### 2.2 클라이언트 식별자
인가 서버는 등록된 클라이언트에게 클라이언트 식별자를 발급합니다. 
이는 클라이언트가 제공한 등록 정보를 나타내는 고유한 문자열입니다. 
클라이언트 식별자는 비밀이 아니며 리소스 소유자에게 노출되어 있으므로 클라이언트 식별자만으로 클라이언트를 인증해서는 안됩니다 (MUST NOT).
클라이언트 식별자는 인가 서버마다 고유합니다.

클라이언트 식별자의 문자열 크기는 이 명세에 의해 정의되지 않습니다. 클라이언트는 식별자 크기에 대해 가정하는 것을 지양해야 합니다.
인가 서버는 발급하는 식별자의 크기를 문서화해야 합니다 (SHOULD).

### 2.3 클라이언트 인증
신뢰할 수 있는 클라이언트 (confidential) 인 경우, 클라이언트와 인가 서버는 인가 서버의 보안 요구 사항에 적합한 클라이언트 인증 방법을 설정합니다.
인가 서버는 보안 요구 사항을 충족하는 클라이언트 인증 방법을 설정할 수 있습니다 (MAY).

신뢰할 수 있는 클라이언트에게는 일반적으로 인가 서버에 인증을 할 때 사용되는 클라이언트 자격 증명 세트 (예: 비밀번호, 공개/개인 키 쌍)가 발급됩니다.

인가 서버는 공개 클라이언트와도 클라이언트 인증 방법을 설정할 수 있으나 (MAY), 클라이언트를 식별하기 위해 공개 클라이언트 인증에 의존해서는 안됩니다 (MUST NOT).

클라이언트는 각 요청에 둘 이상의 인증 방법을 사용해서는 안됩니다 (MUST NOT).

#### 2.3.1 클라이언트 비밀번호
클라이언트 비밀번호를 보유한 클라이언트는 인가 서버와의 상호 작용을 위해 HTTP Basic 인증 방식을 사용할 수 있습니다. ([RFC2617](https://datatracker.ietf.org/doc/html/rfc2617) 참고)
클라이언트 식별자는 `application/x-www-form-urlencoded` 인코딩 알고리즘을 사용하여 인코딩되고 ([Appendix B](https://datatracker.ietf.org/doc/html/rfc6749#appendix-B) 참고) 인코딩된 값은 계정 이름 (계정ID, username) 으로 사용됩니다. 
클라이언트 비밀번호 역시 동일한 알고리즘을 사용하여 인코딩되고 비밀번호로 사용됩니다.
인가 서버는 클라이언트 비밀번호를 발급받은 클라이언트를 인증하기 위한 방법으로 HTTP Basic 인증 방식을 반드시 지원해야 합니다 (MUST).

예시:
```text
Authorization: Basic czZCaGRSa3F0Mzo3RmpmcDBaQnIxS3REUmJuZlZkbUl3
```

대안으로는, 아래 파라미터를 사용하여 클라이언트 자격 증명을 요청 본문에 포함하는 방식을 지원할 수도 있습니다 (MAY).

* client_id
  * 필수. 2.2절의 클라이언트 등록 과정에서 클라이언트에게 발급된 식별자 
* client_secret
  * 필수. 클라이언트 비밀번호. 클라이언트는 클라이언트 비밀번호가 빈 문자열인 경우 파라미터를 생략할 수 있습니다 (MAY).

위 파라미터의 클라이언트 자격 증명을 요청 본문에 포함하는 것은 권장되지 않으며 (NOT RECOMMENDED), 
직접적으로 HTTP Basic 인증 방식 (혹은 다른 비밀번호 기반 HTTP 인증 방식) 을 사용할 수 없는 클라이언트에게 제한적으로 사용되어야 합니다 (SHOULD). 
파라미터는 요청 본문을 통해서만 전송되어야 하며 요청 URI에 포함되어서는 안됩니다 (MUST NOT).

예시: 액세스 토큰을 새로고침하기 위해 (Section 6) 아래와 같은 바디 파라미터를 사용하는 요청

```http request
POST /token HTTP/1.1
Host: server.example.com
Content-Type: application/x-www-form-urlencoded

grant_type=refresh_token&refresh_token=tGzv3JOkF0XG5Qx2TlKWIA
&client_id=s6BhdRkqt3&client_secret=7Fjfp0ZBr1KtDRbnfVdmIw
```

1.6절에 명시한 것처럼, 인가 서버는 비밀번호 인증을 사용하는 요청에 대해 TLS 사용을 요구해야 합니다 (MUST).
     
해당 인증 방식은 비밀번호를 포함하기 때문에 인가 서버는 이러한 방식을 사용하는 엔드포인트를 무차별 공격 (bruteforce attack) 으로부터 보호해야 합니다 (MUST).

#### 2.3.2 기타 인증 방법
인가 서버는 보안 요구 사항을 충족하는 다른 HTTP 인증 방식을 지원할 수 있습니다 (MAY).
다른 인증 방식을 사용하는 경우 인가 서버는 클라이언트 식별자 (클라이언트 등록 정보) 와 인증 방식 간의 매핑을 반드시 정의해야 합니다 (MUST).

### 2.4 미등록 클라이언트
이 명세는 등록되지 않은 클라이언트의 사용을 배제하진 않으나 이러한 클라이언트의 사용은 이 명세의 범위를 벗어나며 추가적인 보안 분석과 상호 운용성 영향 검토가 필요합니다.

## 3. 프로토콜 엔드포인트

인가 프로세스는 인가 서버 측의 두 개의 엔드포인트(HTTP 리소스)를 사용합니다:

- 인가 엔드포인트 - 클라이언트가 유저 에이전트 리다이렉션을 통해 자원 소유자로부터 인가를 받기 위해 사용합니다.
- 토큰 엔드포인트 - 클라이언트가 인가 권한을 액세스 토큰으로 교환하기 위해 사용하며, 일반적으로 클라이언트 인증이 필요합니다.

또한 클라이언트 측에는 다음의 엔드포인트가 필요합니다:

- 리다이렉션 엔드포인트 - 인가 서버가 자원 소유자의 유저 에이전트를 통해 클라이언트에게 인가 자격 증명이 포함된 응답을 반환하기 위해 사용합니다.

모든 인가 허가 유형이 두 엔드포인트를 모두 사용하는 것은 아닙니다.
확장 허가 유형은 필요에 따라 추가 엔드포인트를 정의할 수 있습니다.

### 3.1 인가 엔드포인트

인가 엔드포인트는 리소스 소유자와 상호작용하고 인가 허가를 얻기 위해 사용됩니다. 인가 서버는 먼저 리소스 소유자의 신원을 확인해야 합니다. 인가 서버가 리소스 소유자를 인증하는 방법(예: 사용자 이름과 비밀번호 로그인, 세션 쿠키)은 이 명세서의 범위를 벗어납니다.

클라이언트가 인가 엔드포인트의 위치를 얻는 방법은 이 명세서의 범위를 벗어나지만, 일반적으로 서비스 문서에서 제공됩니다.

엔드포인트 URI는 `application/x-www-form-urlencoded` 형식(부록 B 참조)의 쿼리 컴포넌트([RFC3986] Section 3.4)를 포함할 수 있으며, 이는 추가 쿼리 매개변수를 추가할 때 유지되어야 합니다. 엔드포인트 URI는 프래그먼트 컴포넌트를 포함해서는 안 됩니다.

인가 엔드포인트로의 요청은 사용자 인증과 암호화되지 않은 인증 정보가 HTTP 응답으로 전송되므로, 인가 서버는 해당 엔드포인트로 요청을 보낼 때 1.6절에 설명된 대로 TLS 사용을 요구해야 합니다.

인가 서버는 인가 엔드포인트에 대해 HTTP `GET` 메서드[RFC2616]를 지원해야 하며, `POST` 메서드도 지원할 수 있습니다. 값 없이 전송된 매개변수는 요청에서 생략된 것처럼 처리되어야 합니다. 인가 서버는 인식되지 않은 요청 매개변수를 무시해야 합니다. 요청 및 응답 매개변수는 두 번 이상 포함되어서는 안 됩니다.

#### 3.1.1 응답 유형

인가 엔드포인트는 인가 코드 허가 유형과 암묵적 허가 유형 흐름에서 사용됩니다. 클라이언트는 다음 매개변수를 사용하여 원하는 허가 유형을 인가 서버에 알립니다:

`response_type`
필수. 값은 4.1.1절에 설명된 대로 인가 코드를 요청하는 `code`, 4.2.1절에 설명된 대로 액세스 토큰(암묵적 허가)을 요청하는 `token`, 또는 8.4절에 설명된 등록된 확장 값 중 하나여야 합니다.

확장 응답 유형은 공백(%x20)으로 구분된 값 목록을 포함할 수 있으며, 값의 순서는 중요하지 않습니다(예: 응답 유형 `a b`는 `b a`와 동일). 이러한 복합 응답 유형의 의미는 각각의 명세서에 의해 정의됩니다.

인가 요청에 `response_type` 매개변수가 없거나 응답 유형이 이해되지 않는 경우, 인가 서버는 4.1.2.1절에 설명된 대로 오류 응답을 반환해야 합니다.

#### 3.1.2 리디렉션 엔드포인트

리소스 소유자와의 상호 작용을 완료한 후, 인가 서버는 리소스 소유자의 유저 에이전트를 클라이언트로 다시 돌려보냅니다. 인가 서버는 유저 에이전트를 클라이언트 등록 과정 중에 또는 인가 요청을 할 때 인가 서버와 함께 이전에 설정된 클라이언트의 리디렉션 엔드포인트로 리디렉션합니다.

리디렉션 엔드포인트 URI는 [RFC3986] 4.3절에 정의된 대로 절대 URI여야 합니다. 엔드포인트 URI는 `application/x-www-form-urlencoded` 형식의 쿼리 컴포넌트를 포함할 수 있으며, 이는 추가 쿼리 매개변수를 추가할 때 유지되어야 합니다. 엔드포인트 URI는 프래그먼트 컴포넌트를 포함해서는 안 됩니다.

##### 3.1.2.1 엔드포인트 요청 기밀성

리다이렉션 엔드포인트는 요청된 응답 유형이 `code` 또는 `token`인 경우, 또는 리다이렉션 요청이 개방형 네트워크를 통해 민감한 자격 증명을 전송하게 되는 경우, 섹션 1.6에 설명된 대로 TLS 사용을 요구해야 합니다. 이 명세서가 작성되는 시점에서 클라이언트 개발자들에게 TLS 배포를 요구하는 것이 상당한 장애물이 되기 때문에, 이 명세서는 TLS 사용을 의무화하지는 않습니다. TLS를 사용할 수 없는 경우, 인가 서버는 리다이렉션 전에 리소스 소유자에게 안전하지 않은 엔드포인트에 대해 경고해야 합니다(예: 인가 요청 중 메시지 표시).

전송 계층 보안의 부재는 클라이언트와 클라이언트가 접근 권한을 부여받은 보호된 리소스의 보안에 심각한 영향을 미칠 수 있습니다. 특히 인가 프로세스가 클라이언트에 의해 위임된 최종 사용자 인증의 형태로 사용되는 경우(예: 제3자 로그인 서비스), 전송 계층 보안의 사용이 매우 중요합니다.

##### 3.1.2.2 등록 요구사항

인가 서버는 다음 클라이언트들이 그들의 리디렉션 엔드포인트를 등록하도록 요구해야 합니다:

- 공개 클라이언트
- 암묵적 허가 유형을 사용하는 기밀 클라이언트

인가 서버는 모든 클라이언트가 인가 엔드포인트를 사용하기 전에 리디렉션 엔드포인트를 등록하도록 요구해야 합니다.

인가 서버는 클라이언트가 완전한 리디렉션 URI를 제공하도록 요구해야 합니다(클라이언트는 요청별 사용자 지정을 위해 `state` 요청 매개변수를 사용할 수 있음). 완전한 리디렉션 URI의 등록을 요구하는 것이 불가능한 경우, 인가 서버는 URI 스키마, 권한, 경로의 등록을 요구해야 합니다(클라이언트가 인가를 요청할 때 리디렉션 URI의 쿼리 컴포넌트만 동적으로 변경할 수 있도록 허용).

인가 서버는 클라이언트가 여러 리디렉션 엔드포인트를 등록하는 것을 허용할 수 있습니다.

리디렉션 URI 등록 요구사항의 부재는 10.15절에 설명된 대로 공격자가 인가 엔드포인트를 오픈 리디렉터로 사용할 수 있게 할 수 있습니다.

##### 3.1.2.3 동적 구성

여러 리디렉션 URI가 등록된 경우, 리디렉션 URI의 일부만 등록된 경우, 또는 리디렉션 URI가 등록되지 않은 경우, 클라이언트는 `redirect_uri` 요청 매개변수를 사용하여 인가 요청에 리디렉션 URI를 포함해야 합니다.

리디렉션 URI가 인가 요청에 포함된 경우, 인가 서버는 받은 값을 등록된 리디렉션 URI(또는 URI 컴포넌트) 중 하나와 비교하고 일치시켜야 합니다([RFC3986] 6절에 정의된 대로). 클라이언트 등록에 완전한 리디렉션 URI가 포함된 경우, 인가 서버는 [RFC3986] 6.2.1절에 정의된 대로 단순 문자열 비교를 사용하여 두 URI를 비교해야 합니다.

##### 3.1.2.4 잘못된 엔드포인트

인가 요청이 리디렉션 URI가 누락되었거나, 잘못되었거나, 일치하지 않아 유효성 검사에 실패한 경우, 인가 서버는 리소스 소유자에게 오류를 알려야 하며 유저 에이전트를 잘못된 리디렉션 URI로 자동 리디렉션해서는 안 됩니다.

##### 3.1.2.5 엔드포인트 내용

클라이언트의 엔드포인트로의 리디렉션 요청은 일반적으로 유저 에이전트가 처리하는 HTML 문서 응답을 초래합니다. HTML 응답이 리디렉션 요청의 직접적인 결과로 제공되는 경우, HTML 문서에 포함된 모든 스크립트는 리디렉션 URI와 그 안에 포함된 자격 증명에 대한 전체 접근 권한으로 실행됩니다.

클라이언트는 리디렉션 엔드포인트 응답에 제3자 스크립트(예: 제3자 분석, 소셜 플러그인, 광고 네트워크)를 포함해서는 안 됩니다. 대신, URI에서 자격 증명을 추출하고 유저 에이전트를 자격 증명을 노출하지 않는(URI 또는 다른 곳에서) 다른 엔드포인트로 다시 리디렉션해야 합니다. 제3자 스크립트가 포함된 경우, 클라이언트는 자체 스크립트(URI에서 자격 증명을 추출하고 제거하는 데 사용됨)가 먼저 실행되도록 보장해야 합니다.

### 3.2 토큰 엔드포인트

토큰 엔드포인트는 클라이언트가 인가 허가나 리프레시 토큰을 제시하여 액세스 토큰을 얻기 위해 사용됩니다. 토큰 엔드포인트는 암묵적 허가 유형을 제외한 모든 인가 허가와 함께 사용됩니다(액세스 토큰이 직접 발급되기 때문).

클라이언트가 토큰 엔드포인트의 위치를 얻는 방법은 이 명세서의 범위를 벗어나지만, 일반적으로 서비스 문서에서 제공됩니다.

엔드포인트 URI는 `application/x-www-form-urlencoded` 형식의 쿼리 컴포넌트를 포함할 수 있으며, 이는 추가 쿼리 매개변수를 추가할 때 유지되어야 합니다. 엔드포인트 URI는 프래그먼트 컴포넌트를 포함해서는 안 됩니다.

토큰 엔드포인트에 대한 요청은 암호화되지 않은 자격 증명이 HTTP 요청과 응답으로 전송되므로, 인가 서버는 토큰 엔드포인트에 요청을 보낼 때 1.6절에 설명된 대로 TLS 사용을 요구해야 합니다.

클라이언트는 액세스 토큰 요청을 할 때 HTTP `POST` 메서드를 사용해야 합니다.

값 없이 전송된 매개변수는 요청에서 생략된 것처럼 처리되어야 합니다. 인가 서버는 인식되지 않은 요청 매개변수를 무시해야 합니다. 요청 및 응답 매개변수는 두 번 이상 포함되어서는 안 됩니다.

#### 3.2.1 클라이언트 인증

기밀 클라이언트나 클라이언트 자격 증명을 발급받은 다른 클라이언트들은 토큰 엔드포인트에 요청할 때 섹션 2.3에서 설명된 대로 반드시(MUST) 인가 서버에 대해 인증을 수행해야 합니다. 클라이언트 인증은 다음과 같은 목적으로 사용됩니다:

- 리프레시 토큰과 인가 코드가 원래 발급된 클라이언트에게만 바인딩되도록 강제합니다. 클라이언트 인증은 특히 인가 코드가 안전하지 않은 채널을 통해 리다이렉션 엔드포인트로 전송되거나, 리다이렉션 URI가 완전히 등록되지 않은 경우에 매우 중요합니다.

- 클라이언트를 비활성화하거나 자격 증명을 변경함으로써 보안이 침해된 클라이언트로부터 복구할 수 있으며, 이는 공격자가 탈취한 리프레시 토큰을 악용하는 것을 방지합니다. 단일 클라이언트 자격 증명을 변경하는 것이 전체 리프레시 토큰 세트를 취소하는 것보다 훨씬 빠릅니다.

- 주기적인 자격 증명 갱신이 필요한 인증 관리 모범 사례를 구현합니다. 전체 리프레시 토큰 세트를 갱신하는 것은 어려울 수 있지만, 단일 클라이언트 자격 증명 세트를 갱신하는 것은 상대적으로 훨씬 쉽습니다.

클라이언트는 토큰 엔드포인트에 요청을 보낼 때 자신을 식별하기 위해 `client_id` 요청 매개변수를 사용할 수 있습니다. 토큰 엔드포인트에 대한 `authorization_code` `grant_type` 요청에서, 인증되지 않은 클라이언트는 다른 `client_id`를 가진 클라이언트에게 의도된 코드를 실수로 수락하는 것을 방지하기 위해 반드시 자신의 `client_id`를 전송해야 합니다. 이는 클라이언트를 인가 코드 교체로부터 보호합니다. (단, 보호된 리소스에 대한 추가적인 보안은 제공하지 않습니다.)

### 3.3 액세스 토큰 범위

인가 및 토큰 엔드포인트는 클라이언트가 `scope` 요청 매개변수를 사용하여 액세스 요청의 범위를 지정할 수 있게 합니다. 이에 대응하여, 인가 서버는 `scope` 응답 매개변수를 사용하여 발급된 액세스 토큰의 범위를 클라이언트에 알립니다.

scope 매개변수의 값은 공백으로 구분된, 대소문자를 구분하는 문자열 목록으로 표현됩니다. 이 문자열들은 인가 서버에 의해 정의됩니다. 값이 여러 개의 공백으로 구분된 문자열을 포함하는 경우, 그 순서는 중요하지 않으며, 각 문자열은 요청된 범위에 추가적인 액세스 범위를 추가합니다.

```ABNF
scope       = scope-token *( SP scope-token )
scope-token = 1*( %x21 / %x23-5B / %x5D-7E )
```

인가 서버는 인가 서버 정책이나 리소스 소유자의 지시에 따라 클라이언트가 요청한 범위를 완전히 또는 부분적으로 무시할 수 있습니다. 발급된 액세스 토큰의 범위가 클라이언트가 요청한 것과 다른 경우, 인가 서버는 실제로 부여된 범위를 클라이언트에 알리기 위해 `scope` 응답 매개변수를 포함해야 합니다.

클라이언트가 인가를 요청할 때 scope 매개변수를 생략하는 경우, 인가 서버는 미리 정의된 기본값을 사용하여 요청을 처리하거나 유효하지 않은 범위를 나타내는 요청 실패를 해야 합니다. 인가 서버는 범위 요구사항과 기본값(정의된 경우)을 문서화해야 합니다.
