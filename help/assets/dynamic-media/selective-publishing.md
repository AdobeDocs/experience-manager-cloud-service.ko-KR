---
title: Dynamic Media의 선택적 게시 작업
description: Dynamic Media에서 선택적 게시로 작업하는 방법을 알아봅니다.
contentOwner: Rick Brough
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner
exl-id: a5a2df68-be13-45a6-ad80-09fbd2fea8f2
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 4%

---

# Dynamic Media {#selective-publish-configure-folder}의 폴더 수준에서 선택적 게시 구성

Adobe Experience Manager 또는 Dynamic Media에서 자산을 게시하거나 게시 취소하도록 선택할 수 있습니다. **[!UICONTROL 게시 관리]** 또는 **[!UICONTROL 빠른 게시]**&#x200B;를 사용하여 폴더 수준에서 그렇게 할 수 있습니다. 이 게시 방법은 Dynamic Media 인스턴스의 모든 폴더에 설정이 전역 설정인 **[!UICONTROL Dynamic Media 구성]**&#x200B;에만 의존하지 않기 때문에 유용합니다.

예를 들어, 선택적 게시에서는 아직 라이브가 아닌 제품의 자산으로 작업할 수 있습니다. 이러한 경우 마케팅 팀은 Dynamic Media에 동기화된 스마트 자르기 이미지 및 동적 표현물에 액세스할 수 있습니다. 글로벌 전달을 위해 이러한 에셋을 Dynamic Media에 게시하지 않고도 홍보 자료를 제작할 수 있습니다.

<!-- 
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*폴더* 에 자산을 복사하거나 폴더에서 자산을 복사하면 해당 자산의 게시 상태가 지워집니다. 그러나 폴더 속성이 **[!UICONTROL 선택적 게시]**&#x200B;로 설정된 폴더의 에셋을 *이동* 시 해당 에셋의 게시 상태가 유지됩니다.

나중에 폴더에서 **[!UICONTROL 선택적 게시]** 설정을 변경하기로 결정한 경우 이러한 변경 사항은 해당 시점부터 해당 폴더에 업로드하는 새 자산에만 영향을 줍니다. **[!UICONTROL 빠른 게시]** 또는 **[!UICONTROL 발행물 관리]** 대화 상자에서 수동으로 변경할 때까지 폴더의 기존 자산의 게시 상태는 그대로 유지됩니다.

폴더 수준 **[!UICONTROL Dynamic Media 게시 모드]** 옵션은 항상 **[!UICONTROL Dynamic Media Configuration]**&#x200B;의 **[!UICONTROL 자산 게시]** 설정에 있는 값으로 기본 설정됩니다. 하지만 이 항목의 다음 단계에서는 폴더 수준에서 이 기본값을 수동으로 변경(다음 단계에 설명됨)하여 **[!UICONTROL Dynamic Media Configuration]** 값을 재정의하는 방법을 보여 줍니다.

사용 여부에 상관없이

* **[!UICONTROL Dynamic Media 구성]**&#x200B;에 설정된 **[!UICONTROL 자산 게시]** 값
* 또는 폴더 수준 속성에 설정된 **[!UICONTROL Dynamic Media 게시 모드]** 값

**[!UICONTROL 즉시]**, **[!UICONTROL 활성화 시]** 또는 **[!UICONTROL 선택적 게시]**&#x200B;를 선택할 수 있습니다. 예를 들어 **[!UICONTROL Dynamic Media 구성]**&#x200B;의 **[!UICONTROL 자산 게시]** 값을 **[!UICONTROL 활성화 시]**&#x200B;으로 설정할 수 있습니다. 또한 폴더 수준에서 **[!UICONTROL Dynamic Media 게시]** 모드 값을 **[!UICONTROL 선택적 게시]**&#x200B;로 설정할 수 있습니다. 반대로

폴더에서 선택적 게시를 구성한 후 다음 중 하나를 수행할 수 있습니다.

* [게시 관리를 사용하여 선택적으로 Dynamic Media 또는 Experience Manager에 자산을 게시할 수 있습니다](#selective-publish-manage-publication).
* [게시 관리를 사용하여 Dynamic Media 또는 Experience Manager에서 선택적으로 자산을 게시 취소합니다](#selective-unpublish-manage-publication).
* [빠른 게시를 사용하여 Dynamic Media 또는 Experience Manager에 자산 게시](#quick-publish-aem-dm).
* [검색 결과를 통해 선택적으로 자산을 게시하거나 게시 취소합니다](#selective-publish-unpublish-search-results).

**Dynamic Media의 폴더 수준에서 선택적 게시를 구성하려면:**

1. Experience Manager에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. 다음 중 하나를 수행하십시오.
   * 기존 폴더의 속성 편집 - **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;에서 속성을 편집할 폴더를 탐색합니다. 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 누릅니다.
   * 새 폴더의 속성 편집 - 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;에서 **[!UICONTROL 만들기 > 폴더]**&#x200B;을 탭합니다. **[!UICONTROL 폴더 만들기]** 대화 상자에서 폴더의 제목(필수)을 입력한 다음 **[!UICONTROL 만들기]**&#x200B;를 누릅니다. 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 누릅니다.

1. **[!UICONTROL 동기화 모드]** 드롭다운 목록에서 다음 중 하나를 선택합니다.

   | 동기화 모드 | 설명 |
   | --- | --- |
   | **[!UICONTROL 상속됨]** | 폴더에 명시적 동기화 값이 없습니다.대신 폴더는 상위 폴더 중 하나에서 동기화 값을 상속하거나 **[!UICONTROL Dynamic Media Configuration]**&#x200B;에 설정된 기본 모드에서 동기화 값을 상속합니다. **[!UICONTROL 상속됨]**&#x200B;에 대한 세부 상태가 도구 설명을 통해 표시됩니다. |
   | **[!UICONTROL 이 폴더 하위 트리의 모든 항목을 Dynamic Media에 동기화]** | 성공적으로 Dynamic Media에 게시하려면 에셋을 Dynamic Media에 동기화해야 합니다. 이 옵션을 선택하면 Dynamic Media에 동기화하기 위해 이 하위 트리에 있는 모든 자산이 포함됩니다. 폴더 특정 설정은 **[!UICONTROL Dynamic Media Configuration]**&#x200B;의 기본 설정을 무시합니다. |
   | **[!UICONTROL Dynamic Media 동기화에서 이 폴더 하위 트리의 모든 항목 제외]** | 이 하위 트리에 있는 모든 자산을 Dynamic Media과 동기화하지 않도록 제외합니다. |

   ![폴더 수준 선택적 게시](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. **[!UICONTROL Dynamic Media 게시 모드]** 드롭다운 목록에서 옵션을 선택합니다. **[!UICONTROL Dynamic Media 게시 모드]** 옵션은 항상 **[!UICONTROL Dynamic Media 구성]**&#x200B;에 설정된 값으로 기본 설정됩니다. 그러나 다음 옵션 중 하나를 사용하여 이 기본값 **[!UICONTROL Dynamic Media Configuration]** 값을 수동으로 재정의할 수 있습니다.

   >[!IMPORTANT]
   >
   >선택한 Dynamic Media 게시 모드 옵션에 관계없이 나중에 *이미*&#x200B;게시된 자산에 대해 업데이트한 모든 업데이트는 추가 사용자 작업 없이 즉시 게시됩니다.

   | Dynamic Media 게시 모드 옵션 | 설명 |
   | --- | --- |
   | **[!UICONTROL 즉시]** | 에셋이 이 폴더에 업로드되면 시스템은 에셋을 Experience Manager에 인제스트하고 URL/포함을 즉시 제공합니다. 이 옵션은 Experience Manager 게시에만 연결되어 있고 자산을 게시하는 데 필요한 사용자 개입은 없습니다.<br>이전 단계에서 Dynamic Media 동기화 모드 ** 에서 이 폴더  **[!UICONTROL 하위 트리에 있는 모든 항목 제외를 선택한 경우 이 옵션]** 을 사용할 수  **** 없습니다. |
   | **[!UICONTROL 활성화 시]** | 에셋이 이 폴더에 업로드되면 URL/포함 링크를 제공하기 전에 먼저 명시적으로 에셋을 게시해야 합니다. 이 옵션은 Experience Manager 게시에만 연결되어 있습니다.<br>이전 단계에서 Dynamic Media 동기화 모드 ** 에서 이 폴더  **[!UICONTROL 하위 트리에 있는 모든 항목 제외를 선택한 경우 이 옵션]** 을 사용할 수  **** 없습니다. |
   | **[!UICONTROL 선택적 게시]** | 자산은 공개 도메인에 제공하기 위해 Experience Manager 또는 Dynamic Media에서 선택한 항목에 게시됩니다. 두 게시 방법 모두 서로 배타적입니다. 즉, 스마트 자르기 또는 동적 표현물과 같은 기능을 사용할 수 있도록 자산을 DMS7에 게시할 수 있습니다. 또는 안전한 미리 보기를 위해 Experience Manager에만 에셋을 게시할 수 있습니다.동일한 자산은 공개 도메인에 배달을 위해 DMS7에 게시된 *이 아닌*&#x200B;입니다. 이전 단계에서 **[!UICONTROL 동기화 모드]**&#x200B;에서 Dynamic Media 동기화&#x200B;]**의 이 폴더 하위 트리에서**[!UICONTROL &#x200B;모든 항목을 제외하도록 선택한 경우에는 이 옵션을 사용할 수 없습니다. |

1. 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 누른 다음 **[!UICONTROL 확인]**&#x200B;을 눌러 Experience Manager 자산으로 돌아갑니다.

## 게시 관리{#selective-publish-manage-publication}를 사용하여 선택적으로 Dynamic Media 또는 Experience Manager에 자산 게시

**[!UICONTROL 게시 관리]**&#x200B;를 사용하여 Dynamic Media 또는 Experience Manager에 자산을 선택적으로 게시하려면 먼저 다음 중 하나를 완료했는지 확인하십시오.

* **[!UICONTROL Dynamic Media 구성]**&#x200B;의 **[!UICONTROL 자산 게시]** 옵션을 **[!UICONTROL 선택적 게시]**&#x200B;로 설정합니다.
* 또는 폴더 수준에서 선택적 게시를 구성했습니다.

Dynamic Media](#selective-publish-configure-folder)의 폴더 수준에서 [Dynamic Media 구성 만들기](#configuring-dynamic-media-cloud-services) 또는 [선택적 게시 구성을 참조하십시오.

<!--
>[!IMPORTANT]
>
>Selective Publish is only available in Dynamic Media - Scene7 mode.
-->

>[!NOTE]
>
>*폴더* 에 자산을 복사하거나 폴더에서 자산을 복사하면 해당 자산의 게시 상태가 지워집니다. 그러나 폴더 속성이 **[!UICONTROL 선택적 게시]**&#x200B;로 설정된 폴더의 에셋을 *이동* 시 해당 에셋의 게시 상태가 유지됩니다.

**게시 관리를 사용하여 선택적으로 Dynamic Media 또는 Experience Manager에 자산을 Cloud Service으로 게시하려면:**

1. Experience Manager에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;에서 다음 중 하나를 수행합니다.
   * 자산을 게시할 폴더로 이동합니다. 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 누릅니다. 특정 폴더의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.
   * 자산을 게시할 폴더로 이동합니다. 폴더를 연 다음 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 누릅니다. 특정 자산의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.

      >[!NOTE]
      >
      >도구 모음에 **[!UICONTROL 게시 관리]**&#x200B;가 표시되지 않으면 줄임표 단추를 대신 누른 다음 목록 메뉴에서 **[!UICONTROL 발행물 관리]**&#x200B;를 선택합니다.

1. **[!UICONTROL 게시 관리 - 옵션]** 페이지의 **[!UICONTROL 작업]**&#x200B;에서 원하는 활성화 유형을 선택합니다.

   | 작업 | 설명 |
   | --- | --- |
   | **[!UICONTROL 게시]** (Experience Manager에) | 보안 미리 보기를 위해 Experience Manager에 자산을 게시하려면 이 옵션을 선택합니다. |
   | **[!UICONTROL Dynamic Media에 게시]** | 공용 도메인에 제공하기 위해 Dynamic Media에 에셋을 게시하거나 스마트 자르기 또는 동적 표현물과 같은 기능을 사용할 수 있도록 하려면 이 옵션을 선택합니다.<br>이 옵션은 폴더 속성 **[!UICONTROL 에서]** Dynamic Media 게시 모드 **[!UICONTROL 를]** 선택적 게시로 설정한 경우에만 사용할 수 있습니다. |

1. **[!UICONTROL 예약]**&#x200B;에서 게시 시간을 설정합니다.

   | 일정 | 설명 |
   | --- | --- |
   | **[!UICONTROL 지금]** | 자산을 즉시 게시하려면 선택합니다. |
   | **[!UICONTROL 나중에]** | 특정 날짜 및 시간에 자산을 게시하려면 선택합니다. |

1. **[!UICONTROL 발행물 관리]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 다음]**&#x200B;을 탭합니다.
1. **[!UICONTROL 게시 관리 - 범위]** 페이지에서 다음 중 하나를 수행합니다.
   * 필요한 경우 게시에서 제거할 자산을 하나 이상 선택합니다.
   * **[!UICONTROL 게시 관리 - 범위]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 게시]** 또는 **[!UICONTROL Dynamic Media에 게시]**&#x200B;를 탭합니다.
1. **[!UICONTROL OK]**&#x200B;을 누릅니다.

### 게시 관리 {#selective-unpublish-manage-publication}를 사용하여 Dynamic Media 또는 Experience Manager에서 선택적으로 자산 게시 취소

1. Experience Manager에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;에서 다음 중 하나를 수행합니다.
   * 게시를 취소하려는 에셋이 있는 폴더로 이동합니다. 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 누릅니다. 특정 폴더의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.
   * 게시를 취소하려는 에셋이 있는 폴더로 이동합니다. 폴더를 연 다음 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 누릅니다. 특정 자산의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.

      >[!NOTE]
      >
      >도구 모음에 **[!UICONTROL 게시 관리]**&#x200B;가 표시되지 않으면 줄임표 단추를 대신 누른 다음 목록 메뉴에서 **[!UICONTROL 발행물 관리]**&#x200B;를 선택합니다.

1. **[!UICONTROL 게시 관리 - 옵션]** 페이지의 **[!UICONTROL 작업]**&#x200B;에서 원하는 비활성화 유형을 선택합니다.

   | 작업 | 설명 |
   | --- | --- |
   | **[!UICONTROL 게시 취소]** (Experience Manager에서) | Experience Manager에서 자산 게시를 취소하려면 이 옵션을 선택합니다. |
   | **[!UICONTROL Dynamic Media에서 게시 취소]** | Dynamic Media에서 자산을 게시 취소하려면 이 옵션을 선택합니다.<br>이 옵션은 폴더 속성 **[!UICONTROL 에서]** Dynamic Media 게시 모드 **[!UICONTROL 를]** 선택적 게시로 설정한 경우에만 사용할 수 있습니다. |

1. **[!UICONTROL 예약]**&#x200B;에서 비활성화 시간을 설정합니다.

   | 일정 | 설명 |
   | --- | --- |
   | **[!UICONTROL 지금]** | 자산을 즉시 게시 취소하려면 선택합니다. |
   | **[!UICONTROL 나중에]** | 특정 날짜 및 시간에 자산을 게시 취소하도록 선택합니다. |

1. **[!UICONTROL 발행물 관리]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 다음]**&#x200B;을 탭합니다.
1. **[!UICONTROL 게시 관리 - 범위]** 페이지에서 다음 중 하나를 수행합니다.
   * 게시 취소에서 제거할 자산을 하나 이상 선택합니다.
   * **[!UICONTROL 게시 관리 - 범위]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 게시 취소]** 또는 **[!UICONTROL Dynamic Media]**&#x200B;에서 게시 취소를 탭합니다.
1. **[!UICONTROL OK]**&#x200B;을 누릅니다.

## 빠른 게시 {#quick-publish-aem-dm}을(를) 사용하여 Dynamic Media 또는 Experience Manager에 자산 게시

단순 자산 활성화 경우에는 **[!UICONTROL 빠른 게시]**&#x200B;를 사용할 수 있습니다. **[!UICONTROL 빠른 게시]** 는 추가 사용자 상호 작용 없이 선택한 자산을 즉시 게시합니다. 게시되지 않은 참조도 자동으로 게시됩니다.

>[!NOTE]
>
>**[!UICONTROL 빠른 게시]**&#x200B;를 사용하여 Dynamic Media 또는 Experience Manager에 자산을 게시하려면 **[!UICONTROL Dynamic Media 구성]** 또는 선택한 폴더의 폴더 속성에서 **[!UICONTROL 선택적 게시]**&#x200B;이(가) 활성화되어 있는지 확인합니다.

**빠른 게시를 사용하여 Dynamic Media 또는 Experience Manager에 자산을 게시하려면:**

1. Experience Manager에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 페이지 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 페이지 오른쪽에서 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**&#x200B;에서 다음 중 하나를 수행합니다.
   * 자산을 게시할 폴더로 이동합니다. 폴더를 선택한 다음 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 누릅니다. 특정 폴더의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.
   * 자산을 게시할 폴더로 이동합니다. 폴더를 연 다음 하나 이상의 자산을 선택합니다. 도구 모음에서 **[!UICONTROL 빠른 게시]**&#x200B;를 누릅니다. 특정 자산의 게시 상태를 보다 쉽게 확인할 수 있도록 **[!UICONTROL 목록 보기]**&#x200B;를 사용합니다.

      >[!NOTE]
      >
      >도구 모음에 **[!UICONTROL 빠른 게시]**&#x200B;가 표시되지 않으면 줄임표 단추를 대신 누른 다음 목록 메뉴에서 **[!UICONTROL 빠른 게시]**&#x200B;를 선택합니다.

      ![Dynamic Media에 폴더 수준 빠른 게시](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. **[!UICONTROL 빠른 게시]** 메뉴 목록에서 다음 옵션 중 하나를 선택합니다.

   | 빠른 게시 옵션 | 기능 |
   | --- | --- | 
   | Experience Manager에 게시 | 선택한 자산을 Experience Manager에 즉시 게시합니다. |
   | Brand Portal에 게시 | 선택한 자산을 **[!UICONTROL 브랜드 포털]**&#x200B;에 즉시 게시합니다.<br>이 옵션은 Experience Manager 자산 인스턴스에 이미 브랜드  **[!UICONTROL 포털이 구성된 경우에만 사용할]** 수 있습니다. |
   | Dynamic Media에 게시 | 선택한 자산을 즉시 Dynamic Media에 게시합니다.<br>자산은 이미 Dynamic Media에 동기화되어야 합니다. 필요한 경우 폴더 속성에 있는 **[!UICONTROL 동기화 모드]**&#x200B;가 이미 **[!UICONTROL 이 폴더 하위 트리에 있는 모든 것을 Dynamic Media]**&#x200B;에 동기화하도록 설정되어 있는지 확인합니다. |

1. **[!UICONTROL 확인]**&#x200B;을 누른 다음 **[!UICONTROL 닫기]**&#x200B;를 누릅니다.

## 검색 결과를 통해 선택적으로 에셋 게시 또는 게시 취소 {#selective-publish-unpublish-search-results}

검색 결과에 Dynamic Media 제작 설정이 다른 자산 폴더 전체의 자산이 표시될 수 있습니다. 검색 결과에서 하나 이상의 에셋을 선택했고 에셋에 다른 Dynamic Media 게시 모드 설정이 있는 경우 도구 모음에서 **[!UICONTROL 발행물 관리]**&#x200B;를 트리거하여 게시하거나 게시를 취소할 수 있습니다.

Experience Manager](/help/assets/search-assets.md)에서 자산 검색을 참조하십시오.[

**검색 결과를 통해 선택적으로 자산을 게시하거나 게시 취소하려면 다음을 수행하십시오.**

1. Experience Manager의 페이지 왼쪽 위 모서리에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 페이지 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. 페이지의 오른쪽 위 모서리 근처에 있는 도구 모음에서 검색 아이콘(확대경)을 탭합니다.
1. **[!UICONTROL Type to search]** 텍스트 필드에 키워드를 입력한 다음 **[!UICONTROL Enter]**&#x200B;를 누릅니다.
1. 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 목록 보기]** 아이콘을 탭합니다.
1. 페이지의 왼쪽 위 모서리 근처에 있는 **[!UICONTROL 필터]** 아이콘을 탭합니다.

   ![검색 결과의 목록 보기 및 필터](/help/assets/assets-dm/select-publish-search-result.png)

1. 왼쪽 패널에서 **[!UICONTROL 상태]**&#x200B;를 확장한 다음 **[!UICONTROL Dynamic Media]** 검색 조건자를 확장합니다.
1. 게시된 Dynamic Media 자산의 상태를 기반으로 검색 결과를 더 세분화하려면 **[!UICONTROL 게시된]** 및 **[!UICONTROL 게시 취소된]** 확인란을 사용합니다.
원할 경우, **[!UICONTROL 게시]** 검색 조건자와 함께 이러한 확인란을 사용하여 **[!UICONTROL 게시된]** 및 **[!UICONTROL 게시되지 않은 Experience Manager 에셋의 검색 결과를 구체화할 수 있습니다.]**
1. 다음 중 하나를 수행하십시오.
   * 게시하거나 게시를 취소할 자산을 하나 이상 선택합니다.
   * **[!UICONTROL 검색 결과]** 페이지의 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 모두 선택]**&#x200B;을 탭합니다.
1. 도구 모음에서 **[!UICONTROL 게시 관리]**&#x200B;를 누릅니다. 필요한 경우 도구 모음의 줄임표 아이콘을 눌러 **[!UICONTROL 발행물 관리]**&#x200B;를 봅니다.
1. **[!UICONTROL 게시 관리 - 옵션]** 페이지에서 원하는 작업을 선택합니다.

   | 선택한 작업 | Dynamic Media 구성에서 자산 게시 설정 | 자산은 |
   | --- | --- | --- |
   | 게시 | 활성화 시 즉시 또는 즉시 | Experience Manager 및 Dynamic Media에 게시되었습니다. |
   | 게시 | 선택적 게시 | Experience Manager에만 게시됨. |
   | 게시 취소 | 활성화 시 즉시 또는 즉시 | Experience Manager 및 Dynamic Media에서 게시 취소되었습니다. |
   | 게시 취소 | 선택적 게시 | Experience Manager 전용 게시 취소. |
   | Dynamic Media에 게시 | 활성화 시 즉시 또는 즉시 | Experience Manager, Dynamic Media 또는 둘 다에 게시되지 않았습니다. |
   | Dynamic Media에 게시 | 선택적 게시 | Dynamic Media에만 게시됨. |
   | Dynamic Media에서 게시 취소 | 활성화 시 즉시 또는 즉시 | Experience Manager, Dynamic Media 또는 두 가지 모두에서 게시 취소되지 않습니다. |
   | Dynamic Media에서 게시 취소 | 선택적 게시 | Dynamic Media 전용 게시 취소. |

1. **[!UICONTROL 예약]**&#x200B;에서 비활성화 시간을 설정합니다.

   | 선택한 일정 | 어떻게 됩니까 |
   | --- | --- |
   | 지금 | 선택한 작업이 즉시 수행됩니다. |
   | 나중에 | 선택한 작업은 선택한 특정 날짜와 시간에 실행됩니다. |

1. **[!UICONTROL 게시 관리 - 옵션]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 다음]**&#x200B;을 탭합니다.
1. (선택 사항) **[!UICONTROL 게시 관리 - 범위]** 페이지에서 선택한 자산에 대한 테이블의 **[!UICONTROL Target 게시]** 열을 검토하십시오.

   | Dynamic Media 구성에서 자산 게시 설정 | 선택한 작업 | 게시 대상 |
   | --- | --- | --- |
   | 즉시 또는 <br>활성화 시 | 게시 | Experience Manager 및 Dynamic Media |
   | 즉시 또는 <br>활성화 시 | Dynamic Media에 게시 | 없음 |
   | 선택적 게시 | 게시 | Experience Manager |
   | 선택적 게시 | Dynamic Media에 게시 | 다이내믹 미디어 |
   | 즉시 또는 <br>활성화 시 | 게시 취소 | Experience Manager 및 Dynamic Media |
   | 즉시 또는 <br>활성화 시 | Dynamic Media에서 게시 취소 | 없음 |
   | 선택적 게시 | 게시 취소 | Experience Manager |
   | 선택적 게시 | Dynamic Media에서 게시 취소 | 다이내믹 미디어 |

1. **[!UICONTROL 게시 관리 - 범위]** 페이지에서 다음 중 하나를 수행합니다.
   * 게시 또는 게시 취소에서 제거할 자산을 하나 이상 선택합니다.
   * **[!UICONTROL 게시 관리 - 범위]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 게시]** 또는 **[!UICONTROL 게시 취소]**&#x200B;를 탭하여 작업을 시작합니다.
1. **[!UICONTROL OK]**&#x200B;을 누릅니다.

## 자산 {#check-publish-status-of-asset} 게시 상태 확인

에셋의 게시 상태를 빠르게 확인하려면 **[!UICONTROL 타임라인]**&#x200B;카드 보기&#x200B;]**,**[!UICONTROL &#x200B;열 보기&#x200B;]**또는**[!UICONTROL &#x200B;목록 보기&#x200B;]**를 Experience Manager에서 사용할 수 있습니다.**[!UICONTROL 

**자산의 게시 상태를 확인하려면:**

1. Experience Manager의 페이지 왼쪽 위 모서리에서 Experience Manager 로고를 눌러 글로벌 탐색 콘솔에 액세스합니다. 페이지 왼쪽에서 탐색 아이콘(도구 아이콘 바로 위)을 누른 다음 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;을 누릅니다.
1. **[!UICONTROL 카드 보기]**, **[!UICONTROL 열 보기]** 또는 **[!UICONTROL 목록 보기]**(아래 스크린샷은 **[!UICONTROL 목록 보기]**)에서 게시했거나 게시하지 않은 자산이 들어 있는 폴더를 여십시오.
1. 확인 표시와 함께 표시되도록 자산을 선택합니다. 예를 들어 아래 스크린샷을 참조하십시오.
1. 페이지의 왼쪽 위 모서리 근처에 있는 드롭다운 메뉴에서 **[!UICONTROL 타임라인]**&#x200B;을 선택합니다. 왼쪽 패널의 **[!UICONTROL 상태]** 영역에는 선택한 자산의 게시 상태가 표시됩니다.
**[!UICONTROL 목록 보기]**&#x200B;를 사용하는 경우 **[!UICONTROL Dynamic Media]** 게시 상태에 대한 추가 열이 나타납니다.
   * Dynamic Media에 동기화하도록 구성된 폴더는 기본적으로 **[!UICONTROL Dynamic Media]** 열을 표시합니다.
   * Dynamic Media에 동기화하도록 구성되지 않은 *은(는) Dynamic Media 열을 표시하지 않습니다.*
      ![목록 보기 및 타임라인](/help/assets/assets-dm/selective-publish-status-timeline.png)

## 선택적 게시 문제 해결 {#selective-publish-troubleshoot}

Dynamic Media에 동기화되지 않았지만 Dynamic Media 게시 작업이 트리거된 에셋은 다음 오류 메시지와 솔루션을 만듭니다.

![선택적 게시 오류](/help/assets/assets-dm/selective-publish-error.png)
