## 파트너 제공 SAML 기반 SSO에 대한 이해

다음 과정은 사용자가 파트너 제공 SAML 기반 SSO 서비스를 통해 호스팅된 Google 애플리케이션에 로그인하는 방법을 설명합니다.

아래 표시된 바와 같이, 그림 1은 사용자가 SAML 기반 SSO 서비스를 통해 Gmail과 같은 Google 애플리케이션에 로그인하는 과정을 보여줍니다. 이미지에 표시된 번호 목록은 각 단계를 더 자세하게 설명합니다.

**참고:** 이 과정이 시작되려면 파트너가 Google이 SAML 응답을 확인할 때 사용해야 하는 공개 키와 SSO 서비스 URL을 제공해야 합니다.

**그림 1: 파트너 제공 SAML 기반 SSO 서비스를 사용하여 Google에 로그인**
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9edccb13-cd5a-4106-bf29-1e2af3f8e4de/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9edccb13-cd5a-4106-bf29-1e2af3f8e4de/Untitled.png)

![https://lh3.googleusercontent.com/ijxXNNLYFPLlMEjBf5yWS2xRiLDRRXUcYyX8mY61dPa1wfxpWExmdMazM7kEWWVjf6s=w661](https://lh3.googleusercontent.com/ijxXNNLYFPLlMEjBf5yWS2xRiLDRRXUcYyX8mY61dPa1wfxpWExmdMazM7kEWWVjf6s=w661)

이 이미지는 다음 단계를 설명합니다.

1. 사용자가 Gmail, 시작 페이지 또는 기타 Google 서비스와 같은 호스팅된 Google 애플리케이션에 도달하려고 시도합니다.
2. SAML 인증 요청이 생성됩니다. SAML 요청은 인코딩되어 파트너 SSO 서비스를 위한 URL에 삽입됩니다. 사용자가 도달하려는 Google 애플리케이션의 인코딩된 URL을 포함하는 RelayState 매개변수가 또한 SSO URL에 삽입됩니다. 이 RelayState 매개변수는 수정 또는 검사 없이 되돌려 보내지는 불투명한 식별자가 됩니다.
3. 사용자 브라우저로 리디렉션이 전송됩니다. 리디렉션 URL에는 파트너의 SSO 서비스에 제출되어야 하는 인코딩된 SAML 인증 요청이 포함됩니다.
4. 파트너는 SAML 요청을 디코딩하여 Google ACS(어설션 소비자 서비스)와 사용자의 대상 URL(RelayState 매개변수) 모두를 위한 URL을 추출합니다. 그런 다음 파트너가 사용자를 인증합니다. 파트너는 유효한 로그인 사용자 인증 정보를 요청하거나 유효한 세션 쿠키를 검사하여 사용자를 인증할 수 있습니다.
5. 파트너가 인증된 사용자의 사용자 이름을 포함하는 SAML 응답을 생성합니다. 이 응답은 SAML 2.0 사양에 따라 파트너의 공개 및 비공개 DSA/RSA 키로 디지털 서명됩니다.
6. 파트너가 SAML 응답 및 RelayState 매개변수를 인코딩하여 정보를 사용자 브라우저로 반환합니다. 파트너는 브라우저가 정보를 Google ACS에 전달할 수 있는 메커니즘을 제공합니다. 예를 들어, 파트너는 양식에 SAML 응답 및 대상 URL을 삽입하고 사용자가 양식을 Google에 제출하기 위해 클릭할 수 있는 버튼을 제공할 수 있습니다. 또한 파트너는 자동으로 양식을 Google에 제출할 수 있는 페이지에 자바스크립트를 포함할 수 있습니다.
7. Google ACS가 파트너의 공개 키를 사용하여 SAML 응답을 확인합니다. 응답이 성공적으로 확인되면 ACS에서 사용자를 대상 URL로 리디렉션합니다.
8. 사용자가 대상 URL로 리디렉션되고 Google에 로그인됩니다.

[참조]

[https://support.google.com/cloudidentity/answer/6262987?hl=ko](https://support.google.com/cloudidentity/answer/6262987?hl=ko)

## 비즈니스 문제

대기업에서 사용하는 클라우드 앱이 점점 증가하고 있습니다. 싱글 사인온(SSO)을 클라우드 앱에 확장 적용하면 직원들이 회사의 사용자 인증 정보를 사용하여 서비스로서의 소프트웨어(SaaS) 앱이나 클라우드에서 호스팅되는 회사 자체 앱에 로그인할 수 있습니다.

SSO는 ID 공급업체(IdP)를 통해 단일 인증 지점을 제공합니다. 사용자가 타사 클라우드 앱에 액세스할 수 있지만 사용자 인증 정보는 타사 앱에 저장되지 않습니다. 대다수의 경우 타사 앱의 사용자 인증 정보는 존재하지 않습니다.

귀사에서 SSO를 적용하여 사용자에게 편의를 제공하면서 보안도 높이려고 한다고 가정해 보겠습니다. IdP는 기업에 있는 모든 클라우드 앱에 대한 액세스를 인증해야 합니다.

## 솔루션

사용자가 SSO를 통해 일부 클라우드 앱에 액세스할 수 있도록 IdP 역할을 하는 Cloud ID는 OpenID Connect(OIDC) 및 보안 보장 마크업 언어(SAML) 2.0 프로토콜을 지원합니다.

Cloud ID는 대규모의 SAML 앱 카탈로그를 지원합니다. G Suite 사용자는 G Suite Marketplace에서 OIDC 앱을 받을 수 있습니다. 대부분의 클라우드 앱은 이러한 프로토콜 중 하나만 지원하지만 둘 다 지원하는 앱도 몇 개 있습니다.

### SAML 카탈로그 앱

**장점**

- SAML은 기업 환경에서 안정적으로 사용되고 있습니다.
- 관리자만 앱을 설치할 수 있으므로 직원이 사용할 수 있는 앱을 관리자가 제어할 수 있습니다.
- 타사 SaaS 공급업체와 Google은 커넥터와 관련해 협력하며 Google은 카탈로그의 앱을 검증합니다.
- 설치 과정이 빠르고 순조롭습니다.

**단점**

- SAML 앱은 OIDC 앱보다 설정하기가 좀 더 번거롭습니다.
- 일부 기업 앱은 SAML을 지원하지 않으며 SAML 기능에 더 많은 요금을 청구하는 기업 앱도 있습니다.

### OIDC G Suite Marketplace 앱

**장점**

- OIDC는 SAML보다 간단하고 더 최근에 나온 프로토콜입니다.
- 관리자와 사용자가 앱을 설치할 수 있지만 사용자는 관리자가 허용한 앱만 설치할 수 있습니다.
- G Suite Marketplace 앱은 G Suite의 기능을 확장합니다. 이 앱은 Core Google Services API를 사용하므로 Google 제품과 원활하게 통합됩니다. 또한 G Suite Marketplace 요구 사항을 준수하는지 확인을 거칩니다.

**단점**

- OIDC가 도입된 기업 앱은 아직 많지 않습니다.

## 권장사항

SAML 및 G Suite Marketplace 카탈로그를 살펴보세요. 일부 앱은 두 카탈로그 모두에 표시됩니다. G Suite를 사용 중이며 회사 IT 정책에서 OIDC를 지원한다면 G Suite Marketplace 앱을 사용하는 것이 좋습니다.

원하는 앱이 카탈로그에 없고 SAML을 지원한다면 커스텀 SAML 앱으로 설치하세요. 커스텀 SAML 앱은 앱을 설치하는 조직에 맞게 구성되므로 일반적인 SAML 카탈로그에는 없습니다.

회사의 여러 조직에 필요한 앱을 설치한 후 각 앱을 꼭 필요한 조직에만 할당하세요.

### 타사 ID 공급업체

타사 IdP를 사용하고 있어도 Cloud ID 카탈로그에서 타사 앱에 SSO를 구성할 수 있습니다. 사용자 인증은 타사 IdP 내에서 이루어지며 Cloud ID는 클라우드 앱을 관리합니다.

SSO에 Cloud ID를 사용하려면 사용자에게 Cloud ID 계정이 있어야 합니다. 사용자는 타사 IdP를 통해 로그인하거나 자신의 Cloud ID 계정에 설정된 비밀번호를 사용하여 로그인합니다.

## 예

회사 A의 직원들은 비즈니스 계열 앱 외에 여러 가지 클라우드 앱을 일상적인 업무에 사용합니다.

- 공동작업 제품군
- 메시징 및 커뮤니케이션
- 회의
- 고객 관계 관리(CRM)
- 인사 관리(HR)
- 고객지원

회사 A는 자체적으로 호스팅하는 온프레미스 IdP를 사용했는데 보안을 강화하고 지원 비용을 줄이며 확장성을 높이기 위해 Cloud ID를 기본 IdP로 전환하고자 합니다. 직원들은 단일 로그인 사용자 인증 정보 세트를 사용해 모든 클라우드 앱에 액세스하기를 원합니다. 회사에서는 SAML 및 OIDC를 사용하여 모든 클라우드 앱에 Google ID로 인증할 계획입니다.

IT 부서는 클라우드 앱에 SSO를 설정합니다.

- 직원들이 사용하는 클라우드 앱의 목록을 작성합니다.
- G Suite Marketplace 또는 SAML 카탈로그에서 이러한 앱을 찾습니다.
- 앱별로 SSO를 설정합니다.
- 다음과 같이 조직별로 적절한 앱을 할당합니다.
    - 상위 조직에 메시징, HR, 공동작업 앱 할당(모든 직원이 사용 가능)
    - 영업 조직에 CRM 할당
    - 지원 조직에 고객지원 앱 할당

![https://cloud.google.com/identity/solutions/images/ou.svg?hl=ko](https://cloud.google.com/identity/solutions/images/ou.svg?hl=ko)

직원은 Cloud ID에 로그인합니다. SSO에 Cloud ID 사용자 인증 정보를 사용하여 필요한 클라우드 앱에 액세스할 수 있습니다.

![https://cloud.google.com/identity/solutions/images/sso.svg?hl=ko](https://cloud.google.com/identity/solutions/images/sso.svg?hl=ko)

[참조]

[https://cloud.google.com/identity/solutions/enable-sso?hl=ko#business_problem](https://cloud.google.com/identity/solutions/enable-sso?hl=ko#business_problem)
