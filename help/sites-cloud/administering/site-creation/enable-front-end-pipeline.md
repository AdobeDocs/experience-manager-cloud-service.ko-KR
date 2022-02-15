---
title: 프런트엔드 파이프라인 활성화
description: 기존 사이트의 프런트엔드 파이프라인이 사이트 테마를 활용하여 사이트를 보다 신속하게 사용자 정의할 수 있는 방법을 알아봅니다.
feature: Administering
role: Admin
source-git-commit: 4771bb075e41f420d0d51d8cb1a4809dc72e55e5
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# 프런트엔드 파이프라인 활성화 {#enable-front-end-pipeline}

기존 사이트의 프런트엔드 파이프라인이 사이트 테마를 활용하여 사이트를 보다 신속하게 사용자 정의할 수 있는 방법을 알아봅니다.

## 개요 {#overview}

프런트엔드 파이프라인은 웹 사이트의 프런트엔드 코드만 을 기반으로 하여 빠르게 배포할 수 있는 메커니즘입니다 [사이트 테마](site-themes.md) 및 [사이트 템플릿.](site-templates.md)

전체 스택을 배포하는 대신 이 파이프라인에 의해 프런트 엔드 코드만 처리되므로 프로세스를 보다 신속하게 수행할 수 있고 프런트 엔드 개발자는 AEM에 대한 지식이 없어도 사이트를 쉽고 빠르게 사용자 지정할 수 있습니다.

사이트 템플릿을 기반으로 하는 사이트는 기본적으로 프런트 엔드 파이프라인을 활용할 수 있습니다. 이 문서에서는 프런트 엔드 파이프라인을 활용하기 위해 기존 사이트를 수정하는 방법을 설명합니다.

>[!TIP]
>
>프런트 엔드 파이프라인과 이 파이프라인과 사이트 템플릿을 사용하여 사이트를 빠르게 배포하는 방법을 잘 모르는 경우 다음을 검토하십시오 [빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) 소개

사이트 템플릿 및 테마를 기반으로 기존 사이트를 만들지 않은 경우 AEM에서는 기존 클라이언트 라이브러리 맨 위에 프런트엔드 파이프라인과 함께 배포되는 테마를 로드하도록 사이트를 구성할 수 있습니다.

## 기술 세부 사항 {#technical-details}

사이트에 대한 프런트 엔드 파이프라인을 활성화하면 AEM에서 사이트 구조를 다음과 같이 변경합니다.

* 사이트의 모든 페이지에는 전용 Cloud Manager 프런트 엔드 파이프라인을 통해 업데이트를 배포하여 수정할 수 있는 한 개의 추가 CSS 및 JS 파일이 포함되어 있습니다.
* 추가된 CSS 및 JS 파일은 처음에 비어 있지만 &quot;테마 소스&quot; 폴더를 다운로드하여 해당 파이프라인을 통해 CSS 및 JS 코드 업데이트를 배포할 수 있는 폴더 구조를 부트스트랩할 수 있습니다.
* 이 변경 사항은 개발자가 삭제한 다음 `SiteConfig` 및 `HtmlPageItemsConfig` 이 작업이 아래에 생성하는 노드 `/conf/<site-name>/sling:configs`.

>[!NOTE]
>
>이 작업은 사이트의 기존 클라이언트 라이브러리를 글꼴 끝 파이프라인을 사용하도록 자동으로 변환하지 않습니다. 이러한 소스를 클라이언트 라이브러리 폴더에서 프런트 엔드 파이프라인 폴더로 이동하는 것은 프런트 엔드 개발자가 수동으로 작업해야 하는 작업입니다.

## 요구 사항 {#requirements}

AEM은 프런트엔드 파이프라인을 사용하도록 기존 사이트를 자동으로 조정할 수 있습니다. 이를 수행하려면 사이트에서 를 사용해야 합니다 [핵심 구성 요소의 페이지 구성 요소 v2 이상](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## 프런트엔드 파이프라인 활성화 {#enabling}

사이트 활성화는 사이트 콘솔에서 수행됩니다.

1. 를 통해 AEM에 로그인하고 사이트로 이동합니다 **전역 탐색** > **Sites**.
1. 콘솔에서 사이트를 선택합니다. 하위 페이지가 아닌 사이트의 루트를 선택해야 합니다.
1. 사이트를 선택한 채 [레일 선택기](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) 왼쪽에서 **사이트**.
1. 에서 **사이트** 레일, 단추를 클릭합니다. **프런트엔드 파이프라인 활성화**.

   ![프런트엔드 파이프라인 활성화](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM에서 수행할 변경 사항에 대한 개요를 확인하는 메시지가 표시됩니다. 사이트가 수정되었는지 확인합니다.

이제 사이트가 프런트엔드 파이프라인을 사용할 준비가 되었습니다. 프런트엔드 파이프라인에 대한 자세한 내용은 다음을 참조하십시오.

* [빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) - 이 설명서 여정은 프런트엔드 파이프라인과 빠른 사이트 생성 도구를 사용하여 사이트를 신속하게 배포하는 프로세스에 대한 처음부터 끝까지 개요를 제공합니다.
* [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - 이 문서에서는 전체 스택 및 웹 계층 파이프라인의 컨텍스트에서 프런트엔드 파이프라인에 대해 설명합니다.
