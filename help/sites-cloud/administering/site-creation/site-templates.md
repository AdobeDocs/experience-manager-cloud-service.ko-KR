---
title: 사이트 템플릿
description: AEM 사이트 템플릿을 사용하여 사이트 구조 및 초기 컨텐츠를 미리 정의하여 사이트를 신속하게 만들 수 있는 방법을 알아봅니다.
feature: Administering
role: Admin
source-git-commit: 5e1a89743c5ac36635a139ada690849507813c30
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 1%

---


# 사이트 템플릿 {#site-templates}

AEM 사이트 템플릿을 사용하여 사이트 구조 및 초기 컨텐츠를 미리 정의하여 사이트를 신속하게 만들 수 있는 방법을 알아봅니다.

## 개요 {#overview}

사전 정의된 구조를 사용하여 기존 표준 세트를 기반으로 새 사이트를 빠르게 배포할 수 있으므로 편리합니다. 사이트 템플릿은 기본 사이트 컨텐츠를 간편하고 재사용 가능한 패키지로 결합하는 방법입니다.

사이트 템플릿에는 일반적으로 기본 사이트 콘텐츠 및 구조와 사이트 스타일링 정보를 포함합니다 [사이트 테마,](site-themes.md) 새 사이트를 빠르게 시작하려면 다음을 수행하십시오. 관리자는 사이트를 기반으로 할 사이트 템플릿을 선택합니다 [사이트 만들기 프로세스 중에](create-site.md)

템플릿은 사용자 지정 가능 할 뿐만 아니라 재사용할 수 있으므로 강력합니다. 또한 AEM 설치에서 여러 템플릿을 사용할 수 있으므로 다양한 비즈니스 요구 사항을 충족하는 다양한 사이트를 유연하게 만들 수 있습니다.

>[!NOTE]
>
>AEM 사이트 템플릿을 [페이지 템플릿.](/help/sites-cloud/authoring/features/templates.md) 사이트 템플릿은 사이트의 전체 구조를 정의합니다. 페이지 템플릿은 개별 페이지의 구조 및 초기 컨텐츠를 정의합니다.
>
>AEM 사이트 템플릿을 [AEM 사이트 테마.](site-themes.md) AEM 사이트 테마에 AEM 사이트에 대한 스타일 정보만 포함됩니다. AEM 사이트 템플릿은 다음을 위해 사이트 구조 및 초기 컨텐츠를 정의하며 AEM 사이트 테마를 포함합니다 [빠른 사이트 만들기](create-site.md)

## AEM에 사이트 템플릿 추가 {#adding}

여러 템플릿을 AEM에 추가할 수 있으며, 이를 사용하여 [사이트를 만듭니다.](create-site.md)

1. AEM 작성 환경에 로그인하고 사이트 콘솔로 이동합니다

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. 탭 또는 클릭 **만들기** 화면의 오른쪽 상단에서 을(를) 선택하고 드롭다운 메뉴에서 을(를) 선택합니다 **템플릿의 사이트**.

   ![템플릿에서 사이트 만들기](../assets/create-site-from-template.png)

1. 사이트 만들기 마법사에서 을 탭하거나 클릭합니다 **가져오기** 를 클릭합니다.

   ![사이트 만들기 마법사](../assets/site-creation-wizard.png)

1. 파일 브라우저에서 사용할 템플릿을 찾아 탭하거나 클릭합니다 **업로드**.

1. 업로드되면 사용 가능한 템플릿 목록에 표시됩니다.

템플릿이 업로드되고 다음 용도로 사용할 수 있습니다. [새 사이트를 만듭니다.](create-site.md)

기존 템플릿을 선택하면 오른쪽 열에 템플릿에 대한 정보가 표시됩니다.

![템플릿을 선택합니다](../assets/select-site-template.png)

## 사이트 템플릿 구조 {#structure}

사이트 템플릿은 패키지 컨텐츠의 목적을 명확하게 반영하는 논리 구조의 패키지입니다. 사이트 템플릿의 구조는 다음과 같습니다.

* `files`: UI 키트, XD 파일 및 기타 파일이 있는 폴더
* `previews`: 사이트 템플릿의 스크린샷이 있는 폴더
* `site`: 페이지 템플릿, 페이지 등과 같이 이 템플릿에서 만든 각 사이트에 대해 복사되는 컨텐츠의 컨텐츠 패키지
* `theme`: 의 소스 [사이트 테마](site-themes.md) css, JavaScript 등을 포함하여 사이트가 보이는 방식을 수정하려면.

## 표준 사이트 템플릿 {#standard-site-template}

Adobe은 자신만의 템플릿을 만드는 기준으로 사용할 수 있는 모범 사례 참조 템플릿을 제공합니다. [표준 사이트 템플릿은 GitHub에서 사용할 수 있습니다.](https://github.com/adobe/aem-site-template-standard)

[표준 사이트 템플릿의 최신 릴리스입니다](https://github.com/adobe/aem-site-template-standard/releases) 에 대해 바로 다운로드 및 사용할 수 있습니다. [새 사이트 만들기](create-site.md)

## 사이트 템플릿 개발 {#developing-templates}

Adobe은 새 사이트 템플릿을 만드는 스크립트 세트로 및 AEM Site Template Builder를 제공합니다.

[AEM 사이트 템플릿 빌더는 GitHub의 사용 설명서와 함께 사용할 수 있습니다.](https://github.com/adobe/aem-site-template-builder) 를 사용자 지정하는 데 프런트 엔드 개발자 경험이 필요합니다. [사이트 테마](site-themes.md) 사이트 구조 및 컨텐츠를 사용자 지정하는 데 AEM 개발자 지식이 필요합니다.
