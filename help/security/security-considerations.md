---
title: AEM as a Cloud Service 보안 고려 사항
description: AEM as a Cloud Service를 사용할 때 중요한 보안 고려 사항에 대해 알아보겠습니다.
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: ht
source-wordcount: '229'
ht-degree: 100%

---

# AEM as a Cloud Service 보안 고려 사항 {#security-considerations}

## AEM Trust Store {#aem-trust-store}

AEM은 비대칭 암호화 작업을 지원하기 위해 글로벌 Trust Store의 콘텐츠 저장소 내부에 인증서를 저장합니다. 콘텐츠는 공개되며 기본적으로 게시자 인스턴스의 모든 사람이 익명으로 액세스할 수 있습니다.

### Trust Store의 특징 {#truststore-characteristics}

* Trust Store는 `/etc/truststore` 아래에 있으며 Java 키 저장소 파일, 키 저장소 암호 및 저장소 메타데이터로 구성됩니다. 포함된 인증서는 기본적으로 API를 통해 모든 사람이 액세스할 수 있지만 암호와 키 저장소 자체는 기술적인 이유로 암호화됩니다.
* 기본 제공 인증서는 HTTPS 및 SAML 지원에만 사용되며 먼저 저장소를 수동으로 생성해야 합니다.
* 고객은 [키 저장소 API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)를 통해 자신의 코드에서 사용할 수 있습니다.
* Trust Store는 아래와 같이 **도구** -**보안** -**Trust Store**&#x200B;의 UI를 통해서 또는 *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*&#x200B;에 액세스하여 관리할 수 있습니다.

  ![Trust Store 관리](/help/security/assets/global-trust-store-modified.png)

* Trust Store에 대한 액세스는 사용 사례에 따라 저장소 액세스 제어에 의해 추가로 제한될 수 있습니다.

>[!NOTE]
>
>Adobe는 Trust Store를 위해 기본 액세스 제어를 사용할 것을 권장합니다. 이는 공개적으로 액세스할 수 있음을 의미합니다. 가장 안전한 구성을 위해 모든 사람에 대해 jcr:all 거부 정책을 사용할 수 있습니다.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, see [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
