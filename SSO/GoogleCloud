[https://cloud.google.com/identity/solutions/enable-sso?hl=ko#business_problem](https://cloud.google.com/identity/solutions/enable-sso?hl=ko#business_problem)

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
