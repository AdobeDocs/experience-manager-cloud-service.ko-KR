---
title: 프론트엔드 파이프라인 활성화
description: 게시 게재를 통해 기존 AEM 작성 사이트에 대한 프론트엔드 파이프라인을 활성화하여 사이트 테마를 사용하여 사이트를 보다 신속하게 맞춤화하는 방법에 대해 알아봅니다.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: 6ee55bed8ca09470291e0488321732beed7bab42
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 24%

---


# 프론트엔드 파이프라인 활성화 {#enable-front-end-pipeline}

{{traditional-aem}}

게시 게재를 통해 기존 AEM 작성 사이트에 대한 프론트엔드 파이프라인을 활성화하여 사이트 테마를 사용하여 사이트를 보다 신속하게 맞춤화하는 방법에 대해 알아봅니다.

## 개요 {#overview}

프론트엔드 파이프라인은 [게시 게재](/help/sites-cloud/authoring/author-publish.md)를 사용하는 기존 AEM 제작 프로젝트를 위한 메커니즘으로, [사이트 테마](site-themes.md) 및 [사이트 템플릿](site-templates.md)을 기반으로 웹 사이트의 프론트엔드 코드만 빠르게 배포할 수 있습니다.

이 파이프라인은 프론트엔드 코드만 처리하므로 전체 스택 배포보다 배포 프로세스가 더 빠릅니다. 따라서 프론트엔드 개발자는 AEM에 대한 지식 없이도 사이트를 손쉽게 맞춤화할 수 있습니다.

사이트 템플릿을 기반으로 하는 사이트는 기본적으로 프론트엔드 파이프라인을 사용할 수 있습니다. 이 문서에서는 기존 사이트를 조정하여 프론트엔드 파이프라인을 활용하는 방법에 대해 설명합니다.

>[!TIP]
>
>프론트엔드 파이프라인 및 사이트 템플릿을 사용하여 사이트를 빠르게 배포하는 방법에 익숙하지 않은 경우 [빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)을 참조하세요.

AEM은 기존 클라이언트 라이브러리 위에 사이트를 계층화하여 사이트 템플릿 및 테마를 사용하여 사이트를 만들지 않았더라도 프론트엔드 파이프라인과 함께 배포된 테마를 로드하도록 사이트를 구성할 수 있습니다.

## 기술 세부 사항 {#technical-details}

사이트에 대해 프론트엔드 파이프라인을 활성화하면 AEM은 사이트 구조에 다음과 같은 변경 내용을 적용합니다.

* 사이트의 모든 페이지에는 한 개의 추가 CSS 및 JS 파일이 포함되어 있으며, 이는 전용 Cloud Manager 프론트엔드 파이프라인을 통해 업데이트를 배포하여 수정할 수 있습니다.
* 추가된 CSS 및 JS 파일은 처음에 비어 있습니다. 그러나 &quot;테마 소스&quot; 폴더를 다운로드하여 파이프라인을 통해 CSS 및 JS 코드 업데이트를 배포하는 데 필요한 폴더 구조를 설정할 수 있습니다.
* 개발자만 이 작업에서 `SiteConfig` 아래에 만드는 `HtmlPageItemsConfig` 및 `/conf/<site-name>/sling:configs` 노드를 삭제하여 변경 내용을 실행 취소할 수 있습니다.

>[!NOTE]
>
>이 작업은 사이트의 기존 클라이언트 라이브러리를 프론트엔드 파이프라인을 사용하도록 자동으로 변환하지 않습니다. 이러한 소스를 클라이언트 라이브러리 폴더에서 프론트엔드 파이프라인 폴더로 이동하려면 프론트엔드 개발자의 수동 작업이 필요합니다.

## 요구 사항 {#requirements}

AEM은 자동으로 기존 사이트를 프론트엔드 파이프라인을 사용하도록 조정할 수 있습니다. 이 워크플로를 수행하려면 사이트에서 [v2 이상의 핵심 구성 요소 &#x200B;](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/wcm-components/page)의 페이지 구성 요소를 사용해야 합니다.

## 프론트엔드 파이프라인 활성화 {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

사이트 콘솔에서 [사이트 레일](site-rail.md)을 사용하여 사이트를 사용하도록 설정합니다.

1. AEM에 로그인한 다음 **전역 탐색** > **사이트**&#x200B;를 통해 사이트로 이동합니다.
1. 콘솔에서 사이트를 선택합니다. 하위 페이지가 아닌 사이트 루트를 선택합니다.
1. 사이트를 선택한 상태로 왼쪽의 [레일 선택기](/help/sites-cloud/authoring/basic-handling.md#rail-selector)를 연 다음 **사이트**&#x200B;를 선택합니다.
1. **사이트** 레일에서 **프론트엔드 파이프라인 활성화** 버튼을 클릭합니다.

   ![프론트엔드 파이프라인 활성화](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM에 변경 사항에 대한 개요를 확인하라는 메시지가 표시됩니다. 확인하면 사이트가 조정됩니다.

이제 사이트에서 프론트엔드 파이프라인을 사용할 수 있습니다. 프론트엔드 파이프라인 및 사이트 테마 관리에 대한 자세한 내용은 다음을 참조하십시오.

* [사이트 레일을 사용하여 사이트 테마 관리](site-rail.md)
* [빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md) - 이 설명서 여정은 프론트엔드 파이프라인 및 빠른 사이트 생성 도구를 사용하여 간편하게 사이트를 배포하는 프로세스에 대한 전체적인 개요를 제공합니다.
* [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - 이 문서에서는 전체 스택 및 웹 계층 파이프라인의 컨텍스트 내 프론트엔드 파이프라인에 대해 설명합니다.

## 프론트엔드 파이프라인 및 사용자 정의 도메인 {#custom-domains}

프론트엔드 파이프라인은 [Cloud Manager의 사용자 지정 도메인 기능 &#x200B;](/help/implementing/cloud-manager/custom-domain-names/introduction.md)과(와) 함께 사용할 수 있지만 두 기능을 함께 사용할 때는 다음 요구 사항을 염두에 두십시오.

### 정적 프론트엔드 파일 {#static-files}

프론트엔드 파이프라인을 통해 배포된 정적 프론트엔드 자산은 기본적으로 Adobe의 사전 정의된 정적 도메인에서 제공됩니다.

프론트엔드 자산에 대한 사용자 지정 도메인이 필요한 경우 게시 계층에 사용자 지정 도메인을 설치하고 Dispatcher의 정적 호스팅 위치로 특정 경로(예: `/static/`)를 라우팅하도록 Adobe을 구성할 수 있습니다. 이 메서드를 사용하려면 정적 자산에 대한 요청을 올바르게 전달하고 캐시하도록 [Dispatcher 규칙](https://experienceleague.adobe.com/ko/docs/experience-manager-dispatcher/using/dispatcher)을 업데이트해야 합니다.

사용자 정의 도메인 및 Dispatcher를 구성하면 정적 도메인에서 프론트엔드 에셋을 제공하도록 AEM을 구성할 수 있습니다.

### 구성 {#configuration}

[기술 정보](#technical-details) 섹션에 설명된 대로 사이트에 대해 프론트엔드 파이프라인 기능을 활성화하면 `SiteConfig` 아래에 `HtmlPageItemsConfig` 및 `/conf/<site-name>/sling:configs` 노드가 만들어집니다.

상태 에셋에 프론트엔드 파이프라인과 함께 사이트에 대해 Cloud Manager의 사용자 지정 도메인 기능을 사용하려면 이러한 노드에 추가 속성을 추가해야 합니다.

1. 사이트에 대해 `customFrontendPrefix`에서 `SiteConfig` 속성을 설정합니다.
   1. 다음으로 이동 `/conf/<site-name>/sling:configs/com.adobe.aem.wcm.site.manager.config.SiteConfig`.
   1. 속성 `customFrontendPrefix = "https://your-custom-domain.com/static/"`을(를) 추가하거나 업데이트합니다.
1. `prefixPath`의 `HtmlPageItemsConfig` 값을 사용자 지정 도메인으로 업데이트합니다.
   1. 다음으로 이동 `/conf/<site-name>/sling:configs/com.adobe.cq.wcm.core.components.config.HtmlPageItemsConfig`.
   1. `prefixPath`이(가) `prefixPath = "https://your-custom-domain.com/static/<hash>/..."`과(와) 같은 사용자 정의 도메인을 반영하는지 확인하십시오.
   * 이 값은 필요에 따라 수동으로 재정의할 수도 있습니다.
1. 설정을 확인합니다.
   1. 배포 후 페이지가 사용자 정의 도메인의 테마 아티팩트를 올바르게 참조하는지 확인하십시오.
   1. 브라우저의 개발자 도구를 열고 `theme.css` 및 `theme.js` 파일 경로를 검사하여 올바른 도메인에서 로드되었는지 확인합니다.

사이트 페이지는 해당 업데이트된 URL의 테마 아티팩트를 참조합니다. 그런 다음 Dispatcher는 이러한 리소스에 대한 요청을 정적 도메인으로 라우팅합니다.

## 프론트엔드 개발자를 위한 우수 사례 {#best-practices}

프론트엔드 파이프라인을 통해 배포하기 전에 로컬에서 프론트엔드 자산을 개발 및 테스트해야 하는 경우 다음 접근 방식을 고려하십시오.

* 테스트를 위해 로컬에서 테마 아티팩트를 재정의하려면 [사이트 테마 빌더의 프록시 모드](https://github.com/adobe/aem-site-theme-builder?tab=readme-ov-file#proxy)를 사용하십시오.
* 로컬 개발 서버에서 테마 파일을 수동으로 제공하고 로컬 서버 주소와 일치하도록 `prefixPath`의 `HtmlPageItemsConfig`을(를) 업데이트합니다.
* 라이브 업데이트를 확인하기 위해 테스트하는 동안 브라우저 캐싱이 비활성화되어 있는지 확인합니다.

로컬 프론트엔드 개발에 대한 자세한 내용은 [사이트 테마 빌더 설명서](https://github.com/adobe/aem-site-theme-builder)를 참조하세요.
