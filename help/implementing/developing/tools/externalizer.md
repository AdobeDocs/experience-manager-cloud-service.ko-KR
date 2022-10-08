---
title: URL 표면화
description: Externalizer는 리소스 경로를 프로그래밍 방식으로 외부 및 절대 URL로 변환할 수 있는 OSGi 서비스입니다.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# URL 표면화 {#externalizing-urls}

AEM에서 **외부 도우미** 은 리소스 경로를 프로그래밍 방식으로 변환할 수 있는 OSGi 서비스입니다(예: `/path/to/my/page`)을 외부 및 절대 URL에 넣습니다(예: `https://www.mycompany.com/path/to/my/page`) 접두사가 있는 DNS로 경로를 고정합니다.

AEM as a Cloud Service 인스턴스는 외부에 표시되는 URL을 알 수 없고, 경우에 따라 요청 범위 외부에서 링크를 만들어야 하기 때문에 이 서비스는 이러한 외부 URL을 구성하고 빌드할 수 있는 중앙 위치를 제공합니다.

이 문서에서는 Externalizer 서비스를 구성하는 방법 및 이를 사용하는 방법에 대해 설명합니다. 서비스에 대한 자세한 내용은 [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).

## Externalizer의 기본 동작 및 무시 방법 {#default-behavior}

기본적으로 Externalizer 서비스는 소수의 도메인 식별자를 환경에 대해 생성된 AEM 서비스 URL과 일치하는 절대 URL 접두사에 매핑합니다(예: ) `author https://author-p12345-e6789.adobeaemcloud.com` 및 `publish https://publish-p12345-e6789.adobeaemcloud.com`. 이러한 각 기본 도메인의 기본 URL은 Cloud Manager에서 정의한 환경 변수에서 읽습니다.

참조용 의 기본 OSGi 구성 `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` 효과적으로 다음을 수행할 수 있습니다.

```json
{
   "externalizer.domains": [
      "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
      "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
      "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]",
      "preview $[env:AEM_EXTERNALIZER_PREVIEW;default=http://localhost:4503]"
   ]
}
```

>[!CAUTION]
>
>기본값 `local`, `author`, `preview`, 및 `publish` OSGi 구성의 외부 도우미 도메인 매핑은 원본과 함께 유지되어야 합니다 `$[env:...]` 위에 나열된 값.
>
>사용자 지정 배포 `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` 파일을 AEM에 as a Cloud Service 로 전송하면 이러한 기본 도메인 매핑을 생략하면 응용 프로그램 동작을 예측할 수 있습니다.

를 재정의하려면 `preview` 및 `publish` 값에서 설명한 대로 Cloud Manager 환경 변수를 사용합니다 [AEM as a Cloud Service OSGi 구성](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) 및 `AEM_CDN_DOMAIN_PUBLISH` 및 `AEM_CDN_DOMAIN_PREVIEW` 변수를 채우는 방법을 설명합니다.

## 외부 도우미 서비스 구성 {#configuring-the-externalizer-service}

Externalizer 서비스를 사용하면 프로그래밍 방식으로 리소스 경로를 접두사로 추가하는 데 사용할 수 있는 도메인을 중앙에서 정의할 수 있습니다. Externalizer 서비스는 단일 도메인이 있는 응용 프로그램에만 사용해야 합니다.

>[!NOTE]
>
>적용할 때 [AEM as a Cloud Service용 OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration) 로컬 개발자 인스턴스에서 다음 단계를 수행한 다음 배포를 위해 프로젝트 코드에 커밋해야 합니다.

Externalizer 서비스에 대한 도메인 매핑을 정의하려면

1. 다음을 통해 구성 관리자로 이동합니다.

   `https://<host>:<port>/system/console/configMgr`

1. 클릭 **Day CQ Link Externalizer** 구성 대화 상자를 열려면 다음을 수행하십시오.

   ![Externalizer OSGi 구성](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >구성에 대한 직접 링크는 다음과 같습니다 `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. 정의 **도메인** 매핑. 매핑은 코드에서 도메인, 공간 및 도메인을 참조하는 데 사용할 수 있는 고유한 이름으로 구성됩니다.

   `<unique-name> [scheme://]server[:port][/contextpath]`

   위치:

   * **`scheme`** 는 일반적으로 http 또는 https이지만 다른 프로토콜일 수 있습니다.

      * https 링크를 적용하려면 https를 사용하는 것이 좋습니다.
      * URL의 외부화를 요청할 때 클라이언트 코드가 스키마를 재정의하지 않는 경우 사용됩니다.
   * **`server`** 호스트 이름(도메인 이름 또는 ip 주소)입니다.
   * **`port`** (선택 사항)은 포트 번호입니다.
   * **`contextpath`** (선택 사항) AEM이 다른 컨텍스트 경로 아래에 웹 앱으로 설치된 경우에만 설정됩니다.

   예를 들어`production https://my.production.instance`

   다음 매핑 이름은 사전 정의되어 있으며, AEM이 매핑 이름을 사용함에 따라 항상 설정되어야 합니다.

   * `local` - 로컬 인스턴스
   * `author` - 작성 시스템 DNS
   * `publish` - 공개 웹 사이트 DNS

   >[!NOTE]
   >
   >사용자 지정 구성에서는 다음과 같은 새 카테고리를 추가할 수 있습니다. `production`, `staging` 또는 외부 비 AEM 시스템(예: `my-internal-webservice`. 이러한 URL은 프로젝트 코드 베이스의 여러 위치에서 하드 코딩하지 않도록 하는 데 유용합니다.

1. 클릭 **저장** 변경 사항을 저장하려면 을 클릭합니다.

### 외부 도우미 서비스 사용 {#using-the-externalizer-service}

이 섹션에서는 Externalizer 서비스를 사용할 수 있는 방법에 대한 몇 가지 예를 보여줍니다.

>[!NOTE]
>
>HTML 컨텍스트에서는 절대 링크를 만들 수 없습니다. 따라서 이러한 경우에는 이 유틸리티를 사용하지 않아야 합니다.

* **&#39;publish&#39; 도메인으로 경로를 구체화하려면**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   도메인 매핑이 다음과 같다고 가정합니다.

   * `publish https://www.website.com`

   * `myExternalizedUrl` 다음으로 끝남 값:

   * `https://www.website.com/contextpath/my/page.html`

* **&#39;author&#39; 도메인으로 경로를 표면화하려면**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   도메인 매핑이 다음과 같다고 가정합니다.

   * `author https://author.website.com`

   * `myExternalizedUrl` 다음으로 끝남 값:

   * `https://author.website.com/contextpath/my/page.html`

* **&#39;local&#39; 도메인으로 경로를 표면화하려면**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   도메인 매핑이 다음과 같다고 가정합니다.

   * `local https://publish-3.internal`

   * `myExternalizedUrl` 다음으로 끝남 값:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>자세한 예제는 [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).
