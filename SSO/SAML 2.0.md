[https://en.wikipedia.org/wiki/SAML_2.0](https://en.wikipedia.org/wiki/SAML_2.0)

Security Assertion Markup Language 2.0 (SAML 2.0)

XML-based protocol
SAML은 같은 네트워크 내의 인증과 권한에 관한 데이터를 서로 교환하기 위한 표준임.

SAML을 이용하면 사용자를 인증을 위한 IdP(Identity Provider) 서버와 SP(Service Provider)간에 안전하게 인증 정보를 교환할 수 있음.

- 암호 피로(Password fatigue) 감소

    사용자가 여러 개의 비밀번호와 유저 네임의 쌍을 외워야하는 정신적인 피로도를 의미하는 암호피로의 감소

- 인증 위임

    다수의 Service Provider 와 단 하나의 IdP간의 CoT(Circle of Trust) 를 생성하여 IdP로 인증 위임되므로 사용자는 단 한번의 로그인으로 다수의 SP를 사용할 수 있음

- 안전한 인증 정보의 보호

    IdP,SP,사용자 사이에서 교환되는 인증 정보를 암호화

- 개인 생산성 향상

    지속적으로 패스워드를 재입력하는 과정이 생략되고, 패스워드 재설정 및 복구에 따른 과정이 필요 없음

IdP와 Service Providor 간에 메타데이타를 교환하여 신뢰 관계 설립한 후 SAML 2.0 은 다음과 같이 동작합니다.

[https://t1.daumcdn.net/cfile/tistory/24058D43573DE1C834](https://t1.daumcdn.net/cfile/tistory/24058D43573DE1C834)

SAML 기반의 인증 과정은 다음과 같습니다.

1. 클라이언트 웹브라우저 또는 단말
2. Service Provider클라이언트가 접근하려는 애플리케이션 또는 서비스 (웹엑스 또는 재버)
3. Identity Provider(IdP)사용자 크리덴셜 (사용자명과 패스워드)을 인증하고 SAML Assertion을 발행
4. SAML Assertion사용자 인증을 위해 IdP로 부터 SP로 전달되는 보안 정보 사용자명, 권한 등의 내용을 적은 XML 문서로 변조를 막기위해 전자서명됨
5. SAML Request (인증 요청)Service Provider 가 생성하는 인증 요청으로 IdP로 인증 위임
6. Circle of Trust (CoT)하나의 IdP를 공유하는 Service Provider 들로 구성
7. MetadataSSO를 활성화하는 Service Provider 및 IdP 가 생성하는 XML 파일메타데이타의 교환으로 신뢰 관계 설립
8. Assertion Consumer Service (ACS) URLACS URL은 IdP가 특정 URL로 최종 SAML 응답을 포스트하도록 요구

출처:

[https://nexpert.tistory.com/606](https://nexpert.tistory.com/606)

## SAML 2.0 protocols

The following protocols are specified in SAMLCore

- Assertion Query and Request Protocol
- [Authentication Request Protocol](https://en.wikipedia.org/wiki/SAML_2.0#Authentication_Request_Protocol)
- [Artifact Resolution Protocol](https://en.wikipedia.org/wiki/SAML_2.0#Artifact_Resolution_Protocol)
- Name Identifier Management Protocol
- Single Logout Protocol
- Name Identifier Mapping Protocol

# SAML 2.0 웹 브라우저 싱글 사인온
[출처] [https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/cwlp_saml_web_sso.html](https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/cwlp_saml_web_sso.html)


웹 싱글 사인온의 핵심 개념

![https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_actor.gif](https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_actor.gif)

1. 사용자는 서비스 제공자(SP)에서 서비스를 요청합니다.
2. SP는 요청을 통해 ID 제공자(IdP)에서 사용자 ID(SAML)를 요청합니다.
3. 이 사용자가 이미 인증되지 않은 경우에는 IdP에서 사용자에게 로그인하도록 요청합니다.
4. SP가 SAML을 가져옵니다.
5. SP는 SAML 어설션을 기반으로 액세스 제어 의사결정을 합니다.

## **Liberty SAML 웹 브라우저 SSO 시나리오**

*그림 2. 시나리오 1: SP-시작 요청 웹 SSO(SP에서 시작 중인 일반 사용자)*

![https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_sp_sso.gif](https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_sp_sso.gif)

1. 일반 사용자가 SP를 방문합니다.
2. SP가 사용자를 IdP에 경로 재지정합니다.
3. 일반 사용자가 IdP에 대해 인증합니다.
4. IdP가 SAML 응답 및 어설션을 SP에 전송합니다.
5. SP가 SAML 응답을 확인하고 사용자 요청을 권한 부여합니다.

*그림 3. 시나리오 2: IdP-시작 비요청 웹 SSO(IdP에서 시작 중인 일반 사용자)*

![https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_idp_sso.gif](https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_idp_sso.gif)

1. 사용자 에이전트가 SAML IdP에 액세스합니다.
2. IdP가 사용자를 인증하고 SAML 어설션을 발행합니다.
3. IdP가 사용자를 SAMLResponse로 SP에 경로 재지정합니다.
4. SP가 SAML 응답을 확인하고 사용자의 요청을 권한 부여합니다.

*그림 4. 시나리오 3: OpenID Connect 제공자 및 SAML 서비스 제공자*

![https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_oidc.gif](https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_liberty/com.ibm.websphere.wlp.doc/images/saml_oidc.gif)

1. 일반 사용자가 OpenID Connect RP(Relying Party)를 방문합니다.
2. RP가 일반 사용자를 OpenID Connect 제공자(OP)에 경로 재지정합니다.
3. OP(또한 SAML SP)가 일반 사용자를 SAML IdP에 경로 재지정합니다.
4. 일반 사용자가 SAML IdP에 대해 인증합니다.
5. IdP가 일반 사용자를 SAMLResponse와 함께 OP 또는 SP에 경로 재지정합니다.
6. OP/SP가 SAML을 확인하고 권한 부여 코드를 RP에 전송합니다.
7. RP가 `id_token` 및 `access_token`에 대한 코드를 교환합니다.
8. RP가 `id_token`을 확인하고 일반 사용자를 권한 부여합니다.
