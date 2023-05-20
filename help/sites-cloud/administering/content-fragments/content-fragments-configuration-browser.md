---
title: 콘텐츠 조각 - 구성 브라우저
description: 구성 브라우저에서 콘텐츠 조각 및 GraphQL 기능을 활성화하여 AEM Headless 게재 기능을 활용하는 방법에 대해 알아봅니다.
feature: Content Fragments
role: User
exl-id: 55d442ae-ae06-4dfa-8e4e-b415385ccea5
source-git-commit: 34574fdc7f246499bd238fef388671d2287e62bc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 100%

---

# 콘텐츠 조각 - 구성 브라우저{#content-fragments-configuration-browser}

구성 브라우저에서 특정 콘텐츠 조각 기능을 활성화하는 방법에 대해 알아봅니다.

## 인스턴스에 대해 콘텐츠 조각 기능 활성화 {#enable-content-fragment-functionality-instance}

콘텐츠 조각을 사용하기 전에 **구성 브라우저**&#x200B;를 사용하여 다음을 활성화해야 합니다.

* **콘텐츠 조각 모델** - 필수
* **GraphQL 지속 쿼리** - 선택 사항

>[!CAUTION]
>
>**콘텐츠 조각 모델**&#x200B;을 활성화하지 않는 경우
>
>* 새 모델을 만들 때 **만들기** 옵션을 사용할 수 없습니다.
>* [사이트 구성을 선택하여 관련 끝점을 생성](/help/headless/graphql-api/graphql-endpoint.md)할 수 없습니다.


콘텐츠 조각 기능 활성화하려면 다음 작업을 수행해야 합니다.

* 구성 브라우저를 통해 콘텐츠 조각 기능을 사용할 수 있도록 설정
* 에셋 폴더에 구성 적용

### 구성 브라우저에서 콘텐츠 조각 기능 활성화 {#enable-content-fragment-functionality-in-configuration-browser}

[특정 콘텐츠 조각 기능을 사용](#creating-a-content-fragment-model)하려면 먼저 **구성 브라우저**&#x200B;를 통해 이를 **활성화해야 합니다**.

>[!NOTE]
>
>또한 자세한 내용은 [구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)를 참조하십시오.

>[!NOTE]
>
>[하위 구성](/help/implementing/developing/introduction/configurations.md#configuration-resolution)(다른 구성 내에 중첩된 구성)은 콘텐츠 조각, 콘텐츠 조각 모델 및 GraphQL 쿼리와 함께 사용할 수 있도록 완전히 지원됩니다.
>
>다음을 참고하십시오.
>
>
>* 하위 구성에서 모델을 생성한 후에는 해당 모델을 다른 하위 구성으로 이동하거나 복사할 수 없습니다.
>
>* GraphQL 끝점은 상위(루트) 구성을 기반으로 합니다.
>
>* 지속 쿼리는 상위(루트) 구성과 관련하여 저장됩니다.



1. **도구**, **일반**&#x200B;으로 이동한 다음 **구성 브라우저**&#x200B;를 엽니다.

1. **만들기**&#x200B;를 사용하여 대화 상자를 열고 여기에서

   1. **제목**&#x200B;을 지정합니다.
   1. **이름**&#x200B;은 저장소의 노드 이름이 됩니다.
      * 제목을 기반으로 자동으로 생성되고 [AEM 명명 규칙](/help/implementing/developing/introduction/naming-conventions.md)에 따라 조정됩니다.
      * 필요한 경우 조정할 수 있습니다.
   1. 사용을 활성화하려면 다음을 선택합니다.
      * **콘텐츠 조각 모델**
      * **GraphQL 지속 쿼리**

      ![구성 정의](assets/cfm-conf-01.png)


1. **만들기**&#x200B;를 선택하여 정의를 저장합니다.

<!-- 1. Select the location appropriate to your website. -->

### 폴더에 구성 적용 {#apply-the-configuration-to-your-folder}

**전역** 구성이 콘텐츠 조각 구성에 대해 활성화된 경우, 이는 **에셋** 콘솔을 통해 액세스할 수 있는 모든 에셋 폴더에 적용됩니다.

비슷한 에셋 폴더와 함께 다른 구성(전역 제외)을 사용하려면 연결을 정의해야 합니다. This is done by selecting the appropriate **Configuration** in the **Cloud Services** tab of the **Folder Properties** of the appropriate folder.

![구성 적용](assets/cfm-conf-02.png)
