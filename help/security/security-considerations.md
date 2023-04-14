---
title: AEM as a Cloud Service 보안 고려 사항
description: AEM as a Cloud Service 사용 시 중요한 보안 고려 사항에 대해 알아봅니다
hidefromtoc: true
hide: true
source-git-commit: 39ffd826f5d1e9cea2e6a03a74f39c16647b45fa
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# AEM as a Cloud Service 보안 고려 사항 {#security-considerations}

## AEM Trust Store {#aem-trust-store}

비대칭 암호화 작업을 지원하기 위해 AEM은 컨텐츠 저장소 내에 글로벌 신뢰 저장소에 인증서를 저장합니다. 해당 컨텐츠는 공개적이며 기본적으로 게시자 인스턴스의 모든 사람이 익명으로 액세스할 수 있습니다.

### 신탁점포의 특성 {#truststore-characteristics}

* 신탁점은 아래에 있습니다 `/etc/truststore` 및 는 Java 키 저장소 파일, 키 저장소 암호 및 저장소 메타데이터로 구성됩니다. 포함된 인증서는 기본적으로 API를 통해 모든 사람이 액세스할 수 있지만, 암호와 키 저장소 자체는 기술적인 이유로 암호화되어 있습니다
* 기본적으로 인증서는 HTTPS 및 SAML 지원에만 사용되며 스토어를 수동으로 만들어야 합니다
* 고객은 를 통해 고유한 코드에서 이 코드를 사용할 수 있습니다. [키 저장소 API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* 신뢰 저장소는 의 UI를 통해 관리할 수 있습니다 **도구** - **보안** - **Trust Store** 또는 *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*&#x200B;를 아래와 같이 표시합니다.

   ![Trust Store Management](/help/security/assets/global-trust-store-modified.png)

* 트러스트 저장소에 대한 액세스는 사용 사례에 따라 저장소 액세스 제어에 의해 추가로 제한될 수 있습니다.

>[!NOTE]
>
>Adobe은 신뢰 저장소에 기본 액세스 컨트롤을 사용할 것을 권장합니다. 즉, 공개적으로 액세스할 수 있습니다. 가장 안전한 구성을 위해 모든 사용자에 대해 거부 jcr:all 정책을 사용할 수 있습니다.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, please see the [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
