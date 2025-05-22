---
title: 콘텐츠 작성을 위한 사이트 인증 구성
description: AEM Live가 토큰 기반 인증을 지원하는 방법과 WYSIWYG 작성을 통해 인증을 사용하도록 AEM을 구성하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: b2838da2-79c7-49b1-a101-15c21e80197e
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '324'
ht-degree: 100%

---

# 콘텐츠 작성을 위한 사이트 인증 구성 {#site-authentication}

AEM Live가 토큰 기반 인증을 지원하는 방법과 WYSIWYG 작성을 통해 인증을 사용하도록 AEM을 구성하는 방법을 알아봅니다.

## 개요 {#overview}

AEM Live는 토큰 기반 인증을 지원합니다. 사이트 인증은 일반적으로 미리 보기 사이트와 게시 사이트 모두에 적용되지만, 두 사이트 중 하나만 개별적으로 보호하도록 구성할 수도 있습니다.

>[!NOTE]
>
>사이트 인증을 활성화하도록 선택한 경우 AEM 작성 환경에서도 해당 인증을 구성해야 합니다.

## 요구 사항 {#requirements}

콘텐츠 작성에 사용할 사이트 인증을 구성하려면 먼저 다음 작업을 완료해야 합니다.

* 이 문서에서는 [Edge Delivery Services를 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 기반으로 프로젝트 사이트를 이미 만들었다고 가정합니다.
* [프로젝트에 대해 저장소 없는 구성 설정 기능을 이미 활성화](/help/edge/wysiwyg-authoring/repoless.md)했어야 합니다.

## 사이트 인증 구성 {#configure-authentication}

사이트 인증을 구성하는 방법에 대한 자세한 내용은 [사이트 인증 구성](https://www.aem.live/docs/authentication-setup-site) 문서를 참조하십시오.

인증을 구성할 때 다음 정보를 기록해 둡니다.

* 기술 계정 ID
* 사이트 인증 토큰

해당 항목은 AEM 작성 환경에 대한 사이트 인증 구성을 완료하는 데 필요합니다.

## 작성 환경 구성 {#authoring-environment}

사이트 인증이 구성되면 AEM 작성 환경에서 해당 인증을 활성화할 수 있습니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**&#x200B;으로 이동한 후 사이트에 대해 자동으로 생성된 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서 **인증** 탭을 선택하고 이전에 복사한 **사이트 인증 토큰**&#x200B;을 입력합니다.

   ![Edge Delivery Services 구성](/help/edge/wysiwyg-authoring/assets/site-authentication/configure-aem-author.png)

1. **기술 계정 ID**&#x200B;가 이전에 복사한 ID와 일치하는지 확인합니다.

   * 이 필드는 읽기 전용이며 미리 정의되어 있습니다.
   * 기술 계정은 단일 AEM 작성자 환경의 모든 사이트에서 동일합니다.

1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.
