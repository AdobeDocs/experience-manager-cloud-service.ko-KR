---
title: 컨텐츠 조각 - 구성 브라우저
description: AEM의 강력한 헤드리스 전달 기능을 활용할 수 있도록 구성 브라우저에서 특정 컨텐츠 조각 기능을 활성화하는 방법을 알아봅니다.
feature: 콘텐츠 조각
role: Business Practitioner
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
translation-type: tm+mt
source-git-commit: f0e484dbe8549dadc48cc82713861c591a1c5661
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 22%

---

# 콘텐츠 조각 - 구성 브라우저{#content-fragments-configuration-browser}

AEM의 강력한 헤드리스 전달 기능을 활용할 수 있도록 구성 브라우저에서 특정 컨텐츠 조각 기능을 활성화하는 방법을 알아봅니다.

## 인스턴스 {#enable-content-fragment-functionality-instance}에 대한 컨텐츠 조각 기능 활성화

컨텐츠 조각을 사용하기 전에 **구성 브라우저**&#x200B;를 사용하여 다음을 활성화해야 합니다.

* **컨텐츠 조각 모델**  - 필수
* **GraphQL 영구 쿼리**  - 선택 사항

>[!CAUTION]
>
>**컨텐츠 조각 모델**&#x200B;을(를) 활성화하지 않는 경우:
>
>* **만들기** 옵션은 새 모델을 만드는 데 사용할 수 없습니다.
>* [테넌트를 선택하여 관련 끝점](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)을(를) 만들 수 없습니다.


컨텐츠 조각 기능을 활성화하려면 다음을 수행해야 합니다.

* 구성 브라우저를 통해 컨텐츠 조각 기능 사용 가능
* 자산 폴더에 구성 적용

### 구성 브라우저에서 컨텐츠 조각 기능 사용 {#enable-content-fragment-functionality-in-configuration-browser}

[특정 컨텐츠 조각 기능을 사용하려면 **먼저**&#x200B;이(가) **구성 브라우저**&#x200B;를 통해 사용하도록 설정해야 합니다.](#creating-a-content-fragment-model)

>[!NOTE]
>
>자세한 내용은 [구성 브라우저:](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)를 참조하십시오.

>[!CAUTION]
>
>하위 구성(구성 내에 중첩된 구성)은 컨텐츠 조각에서 사용할 수 없습니다.

1. **도구**, **일반**&#x200B;으로 이동한 후 **Configuration Browser**&#x200B;를 엽니다.

1. **만들기**&#x200B;를 사용하여 대화 상자를 열고 여기에서

   1. **제목**&#x200B;을 지정합니다.
   1. 사용자가 사용할 수 있도록 하려면
      * **콘텐츠 조각 모델**
      * **GraphQL 영구 쿼리**

      ![구성 정의](assets/cfm-conf-01.png)


1. **만들기**&#x200B;를 선택하여 정의를 저장합니다.

<!-- 1. Select the location appropriate to your website. -->

### 자산 폴더에 구성 적용 {#apply-the-configuration-to-your-assets-folder}

구성 **global**&#x200B;이(가) 컨텐츠 조각 기능에 대해 활성화되면 모든 자산 폴더에 적용됩니다.

비교 가능한 자산 폴더와 함께 다른 구성(즉, 전역 제외)을 사용하려면 연결을 정의해야 합니다. 이 작업은 해당 폴더의 **폴더 속성**&#x200B;의 **Cloud Services** 탭에서 적절한 **구성**&#x200B;을 선택하여 수행합니다.

![구성 적용](assets/cfm-conf-02.png)
