[https://en.wikipedia.org/wiki/SAML_2.0](https://en.wikipedia.org/wiki/SAML_2.0)

Security Assertion Markup Language 2.0 (SAML 2.0)

XML-based protocol

## SAML 2.0 protocols

The following protocols are specified in SAMLCore

- Assertion Query and Request Protocol
- [Authentication Request Protocol](https://en.wikipedia.org/wiki/SAML_2.0#Authentication_Request_Protocol)
- [Artifact Resolution Protocol](https://en.wikipedia.org/wiki/SAML_2.0#Artifact_Resolution_Protocol)
- Name Identifier Management Protocol
- Single Logout Protocol
- Name Identifier Mapping Protocol

# SAML 2.0 웹 브라우저 싱글 사인온

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
