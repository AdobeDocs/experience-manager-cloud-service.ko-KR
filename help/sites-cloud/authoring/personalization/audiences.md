---
title: 대상자 관리
description: 대상자 콘솔을 사용하면 Adobe Target 계정용 대상자를 생성, 구성 및 관리하거나 ContextHub용 세그먼트를 관리할 수 있습니다.
exl-id: dff72c15-afcd-4b16-a711-e9ca3010e3ec
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 85%

---

# 대상자 관리{#managing-audiences}

대상자 콘솔을 사용하면 Adobe Target 계정용 대상자를 생성, 구성 및 관리하거나 ContextHub용 세그먼트를 관리할 수 있습니다.

* 대상자 추가 - Adobe Target 대상 또는 ContextHub 세그먼트 중 하나.
* 대상자 관리.

ContextHub에서 *세그먼트*&#x200B;라고 하는 대상자는 특정 기준에 정의된 방문자 클래스로, 타깃팅된 활동을 보는 사용자를 결정합니다. 활동을 타깃팅할 때 타깃팅 프로세스에서 바로 대상을 선택하거나 대상 콘솔에서 새 대상을 만들 수 있습니다.

대상 콘솔에서 대상은 브랜드별로 구성됩니다.

대상자는 [타깃팅된 컨텐츠를 작성](/help/sites-cloud/authoring/personalization/targeted-content.md)하는 타깃팅 모드에서 사용할 수 있으며, 이 모드에서는 대상자를 만들 수도 있습니다(하지만 대상자 콘솔에서 Adobe Target 대상자를 만들어야 함). 타깃팅 모드에서 만드는 대상은 대상 콘솔에 표시됩니다.

대상은 정의된 대상 종류를 설명하는 레이블로 표시됩니다.

* CH - ContextHub 세그먼트
* AT - Adobe Target 대상

## 대상 콘솔에서 ContextHub 세그먼트 만들기 {#creating-a-contexthub-segment-in-the-audiences-console}

대상자 콘솔에서 또는 타깃팅 프로세스 중에 ContextHub 세그먼트를 만들 수 있습니다.

대상자 콘솔에서 ContextHub 세그먼트를 만들려면 다음을 수행하십시오.

1. 탐색 콘솔에서 **개인화**&#x200B;를 클릭하거나 탭합니다. **대상자**&#x200B;를 클릭하거나 탭합니다.
1. **ContextHub 세그먼트 만들기**&#x200B;를 탭하거나 클릭합니다.

   ![세그먼트 만들기](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. **새 ContextHub 세그먼트** 대화 상자에서 제목을 입력하고 증폭을 조정하고 **만들기**&#x200B;를 클릭합니다. 새 ContextHub 세그먼트가 대상 목록에 나타납니다.

   >[!NOTE]
   >
   >**수정됨**&#x200B;을 탭하거나 클릭하여 수정된 목록을 정렬하면 새로 만들어진 대상자를 내림차순으로 정렬하여 볼 수 있습니다.

ContextHub을 사용하여 세그먼트를 만드는 방법에 대한 자세히 알려면 ContextHub을 사용한 세그멘테이션 구성 설명서를 참조하십시오. <!--For further detail about creating segments using ContextHub, please see the [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md) documentation.-->

## 대상 콘솔을 사용하여 Adobe Target 대상 만들기 {#creating-an-adobe-target-audience-using-the-audience-console}

대상 콘솔을 사용하여 AEM에서 바로 Adobe Target 대상을 만들 수 있습니다.

대상은 타겟 활동에 포함된 사용자를 판별하는 규칙으로 정의됩니다. 대상 정의는 여러 규칙을 포함할 수 있으며 각 규칙은 여러 개의 매개 변수를 포함할 수 있습니다.

두 개 이상의 규칙을 사용할 때에는 이러한 규칙들이 부울 연산자 AND로 결합되며 이는 잠재적인 대상 구성원이라면 활동에 포함할 정의된 조건을 모두 충족해야 함을 의미합니다. 예를 들어, &#39;OS 규칙 AND 브라우저 규칙&#39;을 정의하는 경우 정의된 OS와(AND) 정의된 브라우저를 모두 사용하는 방문자만 활동에 포함됩니다.

>[!NOTE]
>
>**만들기** 메뉴에 **타겟 대상자 만들기**&#x200B;가 표시되지 않으면 대상을 만드는 데 필요한 권한이 없는 것입니다. 대상자를 만들 수 있으려면 `/etc/segmentation` 아래에 쓰기 권한이 있어야 합니다. content-authors 그룹에는 기본적으로 쓰기 권한이 있습니다.

Adobe Target 대상자를 만들려면 다음을 수행하십시오.

1. 탐색 콘솔에서 **개인화**&#x200B;를 클릭하거나 탭합니다. **대상자**&#x200B;를 클릭하거나 탭합니다.

   ![대상으로 이동](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. 대상 콘솔에서 **만들기**&#x200B;와 **타겟 대상자 만들기**&#x200B;를 차례로 클릭하거나 탭합니다.

   ![Target 대상자 만들기](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. **Adobe Target 구성** 대화 상자에서 타겟 구성을 선택하고 **확인**&#x200B;을 탭하거나 클릭합니다.
1. 규칙#1 영역에서 속성 유형을 탭하거나 클릭하고 사용 가능한 필드에 특성 정보를 입력합니다. 끝나면 속성의 오른쪽에 있는 확인 표시를 선택하여 저장하십시오. 모든 속성에 대해 알려면 [속성 및 속성 선택 사항](#attributes-and-their-options)을 참조하십시오.
1. **규칙 추가**&#x200B;를 클릭하여 다른 규칙을 추가합니다. 규칙을 필요한 만큼 입력하십시오. 규칙들은 부울 연산자 AND를 사용하여 결합되며 이는 대상이 각 규칙의 모든 요구 사항을 충족해야 활동에 대한 자격이 있음을 의미합니다.
1. **다음**&#x200B;을 탭하거나 클릭합니다.
1. 대상에 사용할 이름을 입력하고 **저장**&#x200B;을 탭하거나 클릭합니다.
1. **저장**&#x200B;을 탭하거나 클릭합니다. 대상이 대상 목록에 표시됩니다.

### 속성 및 해당 선택 사항  {#attributes-and-their-options}

다음 각 속성에 대해 타깃팅 규칙을 만들 수 있습니다.

| **특성** | **설명** | **추가 정보** |
|---|---|---|
| **모바일** | 모바일 장치, 장치 유형, 장치 공급업체, 화면 차원(픽셀) 등의 매개 변수를 기반으로 하는 Target 모바일 장치입니다. | Adobe Target에서 [모바일 설명서](https://docs.adobe.com/content/help/ko-KR/target/using/audiences/create-audiences/categories-audiences/mobile.html)를 참조하십시오. |
| **사용자 지정** | 사용자 지정 매개 변수는 mbox 매개 변수입니다. 임의의 mbox 매개 변수를 mbox에 전달하거나 targetPageParams 함수를 사용하는 경우 이러한 매개 변수는 대상자에서 사용할 수 있도록 여기에 표시됩니다. | Adobe Target에서 [사용자 지정 매개 변수 설명서](https://docs.adobe.com/content/help/ko-KR/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html)를 참조하십시오. |
| **OS** | 특정 운영 체제를 사용하는 방문자를 타깃팅할 수 있습니다. | Linux, Macintosh 또는 Windows를 사용하는 사용자를 타깃팅합니다. |
| **사이트 페이지** | 특정 페이지에 있거나 특정 mbox 매개 변수를 가진 방문자를 타깃팅합니다. | Adobe Target에서 [사이트 페이지 설명서](https://docs.adobe.com/content/help/ko-KR/target/using/audiences/create-audiences/categories-audiences/site-pages.html)를 참조하십시오. |
| **브라우저** | 페이지를 방문할 때 특정 브라우저나 특정 브라우저 선택 사항을 사용하는 사용자를 타깃팅할 수 있습니다. | Adobe Target에서 [브라우저 옵션 설명서](https://docs.adobe.com/help/ko-KR/target/using/audiences/create-audiences/categories-audiences/browser.html)를 참조하십시오. |
| **방문자 프로필** | 특정 프로필 매개 변수를 충족하는 Target 방문자입니다. | Adobe Target에서 [방문자 프로필 설명서](https://docs.adobe.com/content/help/ko-KR/target/using/audiences/visitor-profiles/visitor-profile.html)를 참조하십시오. |
| **트래픽 소스** | 사이트 방문 시 사용한 검색 엔진 또는 랜딩 페이지에 따라 방문자를 타깃팅합니다. | Adobe Target에서 [트래픽 소스 설명서](https://docs.adobe.com/content/help/ko-KR/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html)를 참조하십시오. |

## 대상자 콘솔에서 대상 수정 {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>편집 중인 것과 동일한 AEM 인스턴스에서 만들어진 Adobe Target 대상만 편집할 수 있습니다. 다른 AEM 환경에서 만들어진 타겟 대상은 편집할 수 없습니다.

대상자 콘솔에서 모든 ContextHub 대상자를 편집할 수 있습니다. Adobe Target 대상을 편집할 수도 있지만 AEM에서 만들어진 대상만 편집할 수 있습니다.

1. 탐색 콘솔에서 **개인화**&#x200B;를 클릭하거나 탭합니다. **대상자**&#x200B;를 클릭하거나 탭합니다.
1. 편집할 ContextHub 세그먼트 옆의 아이콘을 탭하거나 클릭하고 **편집**&#x200B;을 탭하거나 클릭합니다.
1. 세그먼트 편집기에서 편집을 수행합니다. 자세한 내용은 ContextHub 설명서 를 참조하십시오.<!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
