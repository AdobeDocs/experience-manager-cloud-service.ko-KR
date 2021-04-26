---
title: URL 표면화
description: Externalizer는 리소스 경로를 프로그래밍 방식으로 외부 및 절대 URL로 변환할 수 있는 OSGi 서비스입니다.
translation-type: tm+mt
source-git-commit: 4c584ceadaa358120d1d4b4cabd7e21ced814b31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 1%

---


# URL 표면화 {#externalizing-urls}

AEM에서 **Externalizer**&#x200B;는 프로그래밍 방식으로 리소스 경로(예:사전 구성된 DNS로 경로를 접두사로 사용하여 외부 및 절대 URL(예: `https://www.mycompany.com/path/to/my/page`)에 `/path/to/my/page`) 추가

Cloud Service 인스턴스로 AEM은 외부에서 보이는 URL을 알 수 없고 경우에 따라 요청 범위 외부에서 링크를 만들어야 하므로 이 서비스는 외부 URL을 구성하고 작성할 수 있는 중앙 위치를 제공합니다.

이 문서에서는 Externalizer 서비스를 구성하는 방법과 이 서비스를 사용하는 방법에 대해 설명합니다. 서비스에 대한 자세한 내용은 [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html)를 참조하십시오.

## Externalizer의 기본 비헤이비어 및 {#default-behavior}을(를) 재정의하는 방법

기본적으로 Externalizer 서비스는 `author-p12345-e6789.adobeaemcloud.com` 및 `publish-p12345-e6789.adobeaemcloud.com`과 같은 값이 이미 설정되어 있어 개입이 없는 경우 Cloud Service 설치으로 AEM에서 사용자 정의 도메인을 사용합니다.

이러한 값을 무시하려면 [AEM용 OSGi 구성을 Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties)로 구성하고 사전 정의된 `AEM_CDN_DOMAIN_AUTHOR` 및 `AEM_CDN_DOMAIN_PUBLISH` 변수를 설정하는 문서에 설명된 대로 Cloud Manager 환경 변수를 사용하십시오.

## Externalizer 서비스 {#configuring-the-externalizer-service} 구성

Externalizer 서비스를 사용하여 프로그래밍 방식으로 리소스 경로에 접두사를 지정하는 데 사용할 수 있는 도메인을 중앙에서 정의할 수 있습니다. Externalizer 서비스는 단일 도메인이 있는 응용 프로그램에만 사용해야 합니다.

>[!NOTE]
>
>AEM용 [OSGi 구성을 Cloud Service으로 적용할 때와 마찬가지로, ](/help/implementing/deploying/overview.md#osgi-configuration) 로컬 개발자 인스턴스에서 다음 단계를 수행한 다음 배포를 위해 프로젝트 코드에 커밋해야 합니다.

Externalizer 서비스에 대한 도메인 매핑을 정의하려면

1. 다음을 통해 구성 관리자로 이동합니다.

   `https://<host>:<port>/system/console/configMgr`

1. **Day CQ Link Externalizer**&#x200B;를 클릭하여 구성 대화 상자를 엽니다.

   ![Externalizer OSGi 구성](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >구성에 대한 직접 링크는 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`입니다.

1. **도메인** 매핑을 정의합니다. 매핑은 코드에서 도메인, 공간 및 도메인을 참조하기 위해 사용할 수 있는 고유한 이름으로 구성됩니다.

   `<unique-name> [scheme://]server[:port][/contextpath]`

   위치:

   * **`scheme`** 은 일반적으로 http 또는 https이지만 다른 프로토콜일 수 있습니다.

      * https 링크를 적용하려면 https를 사용하는 것이 좋습니다.
      * URL의 외부화를 요청할 때 클라이언트 코드가 스키마를 무시하지 않는 경우에 사용됩니다.
   * **`server`** 은 호스트 이름(도메인 이름 또는 ip 주소)입니다.
   * **`port`** (선택 사항)은 포트 번호입니다.
   * **`contextpath`** (선택 사항)은 AEM이 다른 컨텍스트 경로 아래에 웹 앱으로 설치된 경우에만 설정됩니다.

   예를 들어,`production https://my.production.instance`

   다음 매핑 이름은 미리 정의되며 AEM이 매핑 이름에 의존할 때 항상 설정해야 합니다.

   * `local` - 로컬 인스턴스
   * `author` - 제작 시스템 DNS
   * `publish` - 공개 웹 사이트 DNS

   >[!NOTE]
   >
   >사용자 지정 구성을 사용하면 `production`, `staging` 등의 새 카테고리나, `my-internal-webservice` 같은 외부 AEM이 아닌 시스템까지 추가할 수 있습니다. 프로젝트 코드 베이스의 여러 위치에서 이러한 URL을 하드 코딩하지 않는 것이 유용합니다.

1. **저장**&#x200B;을 클릭하여 변경 내용을 저장합니다.

### Externalizer 서비스 사용 {#using-the-externalizer-service}

이 섹션에서는 Externalizer 서비스를 사용할 수 있는 방법의 몇 가지 예를 보여 줍니다.

>[!NOTE]
>
>HTML 컨텍스트에서 절대 링크를 만들 필요가 없습니다. 따라서 이러한 경우에는 이 유틸리티를 사용할 수 없습니다.

* **&#39;게시&#39; 도메인으로 경로를 외부화하려면:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   도메인 매핑을 가정할 때:

   * `publish https://www.website.com`

   * `myExternalizedUrl` 다음으로 끝남:

   * `https://www.website.com/contextpath/my/page.html`

* **&#39;author&#39; 도메인으로 경로를 외부화하는 방법:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   도메인 매핑을 가정할 때:

   * `author https://author.website.com`

   * `myExternalizedUrl` 다음으로 끝남:

   * `https://author.website.com/contextpath/my/page.html`

* **&#39;local&#39; 도메인으로 경로를 외부화하려면:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   도메인 매핑을 가정할 때:

   * `local https://publish-3.internal`

   * `myExternalizedUrl` 다음으로 끝남:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>[Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html)에서 더 많은 예를 찾을 수 있습니다.
