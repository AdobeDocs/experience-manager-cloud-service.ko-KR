---
title: 콘텐츠 작성을 위한 사이트 인증 구성
description: AEM Live에서 토큰 기반 인증을 지원하는 방법 및 WYSIWYG 작성에서 인증을 사용하도록 AEM을 구성하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
source-git-commit: 7b46af35b202446fdea67e4125d74c3965d302d9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 2%

---

# 콘텐츠 작성을 위한 사이트 인증 구성 {#site-authentication}

AEM Live에서 토큰 기반 인증을 지원하는 방법 및 WYSIWYG 작성에서 인증을 사용하도록 AEM을 구성하는 방법에 대해 알아봅니다.

## 개요 {#overview}

AEM Live는 토큰 기반 인증을 지원합니다. 사이트 인증은 일반적으로 미리보기 사이트와 게시 사이트 모두에 적용되지만 한 사이트만 개별적으로 보호하도록 구성할 수도 있습니다.

>[!NOTE]
>
>사이트 인증을 활성화하려면 AEM 작성 환경에서도 사이트 인증을 구성해야 합니다

## 요구 사항 {#requirements}

컨텐츠 작성에 사용할 사이트 인증을 구성하려면 먼저 다음 작업을 완료해야 합니다.

* 이 문서에서는 사용자가 Edge Delivery Services을 사용하여 WYSIWYG 작성을 위한 [개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 기반으로 이미 프로젝트 사이트를 만들었다고 가정합니다.
* 이미 [프로젝트에 대해 리디렉션 기능을 활성화한 상태여야 합니다.](/help/edge/wysiwyg-authoring/repoless.md)

## 사이트 인증 구성 {#configure-authentication}

사이트 인증을 구성하는 방법에 대한 자세한 내용은 [사이트 인증 구성](https://www.aem.live/docs/authentication-setup-site) 문서를 참조하십시오.

인증을 구성할 때 다음 정보를 참고하십시오.

* 기술 계정의 ID
* 사이트 인증 토큰

이러한 항목은 AEM 작성 환경에 대한 사이트 인증 구성을 완료하는 데 필요합니다.

## 작성 환경 구성 {#authoring-environment}

사이트 인증이 구성되면 AEM 작성 환경에서 활성화할 수 있습니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**(으)로 이동한 다음 사이트에 대해 자동으로 만들어진 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서 **인증** 탭을 선택하고 이전에 복사한 **사이트 인증 토큰**&#x200B;을(를) 제공합니다.

   ![Edge Delivery Services 구성](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. **기술 계정 ID**&#x200B;가 이전에 복사한 ID와 일치하는지 확인하십시오.

   * 이 필드는 읽기 전용이며 사전 정의됩니다.
   * 기술 계정은 단일 AEM 작성 환경의 모든 사이트에 대해 동일합니다.

1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
