---
title: 일괄처리 집합 사전 설정
description: Dynamic Media에서 일괄처리 집합 사전 설정을 사용하여 이미지 세트 및 스핀 세트 생성을 자동화하는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: 이미지 사전 설정,뷰어 사전 설정
topic: 비즈니스 전문가
role: Business Practitioner
exl-id: 022ee347-54ec-4cec-b808-9eb3a9e51424
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '3446'
ht-degree: 1%

---

# 배치 집합 사전 설정 정보 {#about-bsp}

자산 파일을 개별 또는 일괄 처리를 사용하여 폴더에 업로드할 때 이미지 세트 또는 스핀 세트에 여러 자산을 만들고 구성하려면 **[!UICONTROL 일괄 세트 사전 설정]**&#x200B;을 사용합니다. 사전 설정을 [!DNL Dynamic Media]에서 예약한 자산 가져오기 작업과 함께 실행할 수 있습니다. 각 사전 설정은 사전 설정 레서피에서 정의된 이름 지정 규칙과 일치하는 이미지를 사용하여 이미지 세트 또는 스핀 세트를 구성하는 방법을 정의하는 고유한 이름 지정 지침 세트입니다.

>[!IMPORTANT]
>
>[!DNL Dynamic Media Classic]에서 일괄 세트 사전 설정을 사용하고 Cloud Service으로 [!DNL Dynamic Media Classic]에서 Adobe Experience Manager으로 마이그레이션하는 경우 [!DNL Adobe Experience Manager as a Cloud Service] 내에 일괄 세트 사전 설정 정의를 수동으로 다시 만드십시오.

**우수 사례**  - 일괄 처리 세트 사전 설정 작업을 할 때 Adobe은 다음 작업 과정을 권장합니다.

1. 배치 집합 사전 설정을 만듭니다. 이미지 세트 또는 스핀 세트](#creating-bsp)에 대한 배치 집합 사전 설정 만들기를 참조하십시오.[
1. 자산 폴더를 만들거나 기존 자산 폴더를 사용하고 [!DNL Dynamic Media]에 동기화되었는지 확인합니다. [폴더 만들기](/help/assets/manage-digital-assets.md#creating-folders)를 참조하십시오.
1. 자산 폴더에 일괄 세트 사전 설정을 적용합니다. [폴더](#apply-bsp)에 일괄 세트 사전 설정 적용 정보를 참조하십시오.
1. 이미지를 자산 폴더에 업로드합니다. [이미지 세트에 대한 자산 업로드](/help/assets/dynamic-media/image-sets.md#uploading-assets-in-image-sets), [스핀 세트에 대한 자산 업로드](/help/assets/dynamic-media/spin-sets.md#uploading-assets-for-spin-sets) 또는 [Adobe Experience Manager에 디지털 자산 추가](/help/assets/add-assets.md#add-assets-to-experience-manager)를 참조하십시오.
1. 이미지 세트 또는 스핀 세트는 원하는 폴더에 자동으로 생성됩니다.
1. 이미지 세트 또는 스핀 세트를 게시합니다. [Dynamic Media 자산 게시](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)를 참조하십시오.

## 이미지 세트 또는 스핀 세트 {#creating-bsp} 일괄 집합 사전 설정 만들기

[일괄 처리 집합 사전 설정]을 만들려면 일반 표현식에 대해 잘 알고 이해하는 것이 좋습니다.

가장 좋은 방법은 자산이 세트로 그룹화되는 방식에 대한 명명 규칙을 회사에서 이미 정의한 것입니다.
명명 규칙 사용의 중요성을 이해하려면 회사의 정의된 이름 지정 규칙이 `<style>-<color>-<view>`이라고 가정합니다. 또한 세트의 기본 이름은 항상 `<style>-<color>`이어야 하며 설정된 이름 확장자는 `-SET`이어야 합니다. `0123-RED-01` 이미지를 업로드하면 `0123-RED-SET` 이라는 이름의 세트가 생성됩니다. 나중에 이미지 `0123-RED-03` 및 `0123-BLUE-01`을 업로드하면 `RED-03` 이미지가 `01`보다 낮게 정렬되어 두 번째 위치의 세트에 추가됩니다. 그러나 `BLUE-01` 이미지는 `0123-BLUE-SET`이라는 새 세트의 일부가 됩니다. 다음 에셋 업로드를 위해 `0123-RED-02` 및 `0123-BLUE-02` 파일을 추가합니다. 각 자산이 해당 세트에 추가됩니다. 정렬 순서 때문에 `RED-02` 이미지는 기존 `01`과 `03` 이미지 간에 자동으로 정렬됩니다.

[!DNL Dynamic Media]의 **[!UICONTROL 일괄 세트 사전 설정]** 페이지에서 일괄 세트 사전 설정을 생성, 편집 또는 삭제하고, 일괄 처리 집합 사전 설정을 자산 폴더에 적용하거나 자산 폴더에서 제거할 수 있습니다. 양식 필드 드롭다운 목록을 사용하여 일괄 처리 세트 사전 설정을 정의하거나 일반 표현식 구문을 입력할 수 있는 **[!UICONTROL 원시 코드]** 필드를 사용할 수 있습니다.

필요한 만큼 일괄 세트 사전 설정을 만들어 필요한 모든 에셋 인제스트 작업을 처리할 수 있습니다.

**자산 이름 지정 규칙 정보**

**[!UICONTROL 일괄 세트 사전 설정]** 페이지의 **[!UICONTROL 자산 이름 지정 규칙]** 영역에는 일괄 세트 사전 설정을 정의하는 데 사용할 수 있는 두 개의 요소가 있습니다.**[!UICONTROL 일치]** 및 **[!UICONTROL 기본 이름]**&#x200B;입니다. 이러한 요소를 사용하면 이름 지정 규칙을 정의하고 해당 규칙이 포함된 세트의 이름을 지정하는 데 사용되는 규칙의 일부를 식별할 수 있습니다.<!-- While **[!UICONTROL Match]** is required, **[!UICONTROL Base Name]** is mandatory only if the **[!UICONTROL Match]** field does not already specify a base name through the use of a bracket grouping. -->

회사의 개별 명명 규칙에서는 이러한 두 요소 각각에 대해 하나 이상의 정의 라인을 사용하는 경우가 많습니다. 고유 정의에 많은 선을 사용하고 기본 이미지, 색상 요소, 대체 보기 요소 및 견본 요소와 같은 별개의 요소로 그룹화할 수 있습니다.

예를 들어 리터럴 일치 정규 표현식의 구문은 다음과 같을 수 있습니다.

`(\w+)-\w+-\w+`

**시퀀스 순서 정보**

이미지 세트 또는 스핀 세트가 [!DNL Dynamic Media]으로 그룹화된 후 이미지가 표시되는 순서를 선택적으로 정의할 수 있습니다. 기본적으로 자산은 영숫자 순서로 정렬됩니다. 그러나, 정규 표현식의 쉼표로 구분된 목록을 사용하여 순서를 정의할 수 있습니다.

시퀀스 순서 자동화와 관련하여 필요한 경우 자산을 특정 방식으로 강제 정렬하는 규칙을 지정합니다. 예를 들어 첫 번째 에셋의 이름이 항상 `_main`이고 그 뒤에 `_alt1`, `_alt2`, `_alt3` 등이 있다고 가정해 보십시오. 이러한 경우 다음 구문을 사용하여 시퀀스 순서 지정 규칙을 만들 수 있습니다.

`.*_main,.*_alt[0-9]`

강제 정렬 시퀀스는 가능하지만, 가능한 한 시퀀스 순서에 영숫자 번호를 사용하는 것이 가장 좋습니다. 또한 [!DNL Dynamic Media]의 이미지 세트 또는 스핀 세트 편집기 도구를 사용하여 에셋의 순서 순서를 다시 정렬하거나, 드래그 앤 드롭 작업을 사용하여 세트에서 새 에셋을 추가 및 삭제할 수 있습니다.

일괄 처리 세트 사전 설정 만들기를 완료하면 만든 하나 이상의 폴더에 해당 사전 설정을 적용합니다. [폴더](#apply-bsp)에 일괄 세트 사전 설정 적용 정보를 참조하십시오.

<!-- See also [Creating a batch set preset for the auto generation of a 2D Spin Set](application-setup.md#creating_a_batch_set_preset_for_the_auto_generation_of_a_2d_spin_set). -->

**이미지 세트 또는 스핀 세트에 대한 일괄 세트 사전 설정을 만들려면:**

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.

   ![bsp-create1.png](/help/assets/assets-dm/bsp-create1.png)

1. 오른쪽 위 모서리 근처에 있는 **[!UICONTROL 일괄 세트 사전 설정]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 탭합니다.
1. **[!UICONTROL 일괄 처리 세트 사전 설정 만들기]** 대화 상자의 **[!UICONTROL 사전 설정 이름]** 텍스트 필드에 설명형 이름을 입력합니다. 사전 설정 이름을 나중에 변경하려는 경우 편집할 수 없습니다.

1. **[!UICONTROL 사전 설정 유형]** 드롭다운 목록에서 **[!UICONTROL ImageSet]** 또는 **[!UICONTROL SpinSet]**&#x200B;을 선택합니다. 올바른 사전 설정 유형을 선택해야 합니다.나중에 편집할 수 없습니다.
1. **[!UICONTROL 만들기]**&#x200B;를 누릅니다.
1. **[!UICONTROL 배치 집합 사전 설정 편집]** 페이지의 오른쪽에서 **[!UICONTROL 사전 설정 세부 정보]** 및 **[!UICONTROL 이름 지정 규칙 설정]** 머리글 아래에서 원하는 편집 가능한 옵션을 설정합니다.
사용 가능한 편집 가능한 옵션에 대한 자세한 내용은 [사전 설정 세부 사항, 이름 지정 규칙 설정 및 규칙 결과 - RegX 옵션](#features-options-bsp)을 참조하십시오.

   ![bsp-create4.png](/help/assets/assets-dm/bsp-create4.png)

1. 하나 이상의 정규 표현식 그룹을 만듭니다.

   * **[!UICONTROL 배치 집합 사전 설정 편집]** 페이지의 왼쪽에서 **[!UICONTROL 일치]**, **[!UICONTROL 기본 이름]** 또는 **[!UICONTROL 시퀀스 순서 지정]**&#x200B;에서 **[!UICONTROL 그룹 추가]**&#x200B;를 탭합니다.
   * **[!UICONTROL 일치]** 필드가 필요합니다. **[!UICONTROL 기준]** 이름은 대괄호 그룹을 사용하여  **** 일치 필드가 기본 이름을 아직 지정하지 않은 경우에만 필수입니다. **[!UICONTROL 시퀀스]** 순서는 선택 사항입니다.
   * 그룹 양식의 드롭다운 목록 및 텍스트 상자를 사용하여 이미지 세트 또는 스핀 세트 자산 구성원의 이름 지정 기준을 정의하는 데 사용할 표현식 그룹을 지정합니다.
      * 그룹의 표현식을 선택하고 지정하면 실제 정규 표현식 구문이 페이지의 오른쪽 아래에 반영됩니다(**[!UICONTROL 규칙 결과 - RegX]** 머리글 아래). 오른쪽 하단에 업데이트된 일반 표현식 문자열을 보려면 양식 영역 바깥쪽을 누릅니다. 이러한 일반 표현식 문자열은 이미지 세트 또는 회전 집합을 만들기 위해 [!DNL Dynamic Media] 에셋 검색에서 일치시킬 패턴을 나타냅니다.
      * 추가한 그룹을 제거하려면 **[!UICONTROL X]**&#x200B;을(를) 누릅니다.
   * 두 개 이상의 그룹을 추가할 때 **[!UICONTROL And]** 드롭다운 목록에서 **[!UICONTROL And]**&#x200B;을 선택하여 새로 추가한 그룹을 이전에 추가한 표현식 그룹과 결합합니다. 또는 **[!UICONTROL Or]**&#x200B;을 선택하여 이전 표현식 그룹과 새로 만든 그룹 사이에 대체 요소를 추가합니다. **[!UICONTROL Or]** 피연산자는 일반 표현식 구문 자체에서 세로 줄 문자 `|`를 사용하여 정의됩니다.

1. 다음 중 하나를 수행하십시오.

   * 다른 새 그룹을 추가하려면 **[!UICONTROL 일치]**, **[!UICONTROL 기본 이름]** 또는 **[!UICONTROL 시퀀스 순서]**&#x200B;에서 **[!UICONTROL 그룹 추가]**&#x200B;를 탭합니다. 이전 단계에서와 같이 다른 일반 표현식 그룹을 만듭니다.
   * **[!UICONTROL 규칙 결과 - RegX]** 영역에서 정규 표현식 구문을 검토합니다. 구문을 변경해야 하는 경우 페이지 왼쪽의 각 그룹에서 편집합니다.
   * 표현식 그룹 만들기를 완료한 경우 다음 단계로 진행합니다.

1. 페이지 상단 오른쪽에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

이제 자산 폴더에 일괄 세트 사전 설정을 적용할 준비가 되었습니다. 그런 다음 해당 폴더에 자산을 업로드합니다. 이 워크플로우에서는 이미지 세트 또는 스핀 세트의 자동 생성이 이루어집니다. 자산 폴더](#apply-bsp)에 배치 집합 사전 설정 적용 정보를 참조하십시오.[

### 사전 설정 세부 사항, 이름 지정 규칙 설정 및 규칙 결과 - RegX 옵션 {#features-options-bsp}

이러한 옵션은 일괄 세트 사전 설정을 만들거나 편집할 때 **[!UICONTROL 일괄 세트 사전 설정 편집]** 페이지에서 사용할 수 있습니다.

[이미지 세트 또는 스핀 세트](#creating-bsp) 또는 [일괄 세트 사전 설정 편집](#edit-bsp)을 참조하십시오.

| **[!UICONTROL 사전 설정 세부 사항]** | 설명 |
| --- | --- |
| 사전 설정 이름 | 읽기 전용. 배치 세트를 처음 만들 때 지정한 이름입니다. 사전 설정의 이름을 변경해야 하는 경우 기존 일괄 세트 사전 설정을 복사하고 새 이름을 지정할 수 있습니다. [기존 배치 집합 사전 설정 복사](#copy-bsp)를 참조하십시오. |
| 유형 | 읽기 전용. 배치 세트를 처음 만들 때 유형이 지정되었습니다. 기존 배치 집합 사전 설정을 복사해도 [!UICONTROL Type];을 변경할 수 없습니다.대신 사전 설정을 만들어야 합니다. |
| 파생된 자산 포함 | 선택 사항입니다. [!DNL Dynamic Media]의 IPS(이미지 프로덕션 시스템)에 스핀 세트 또는 이미지 세트와 함께 생성 또는 &quot;파생&quot; 이미지가 포함되게 하려면 **[!UICONTROL Yes]**(기본값)을 선택합니다. 파생된 자산은 사용자가 직접 업로드하지 않은 이미지입니다. 대신, 마스터 자산이 업로드될 때 IPS에 의해 자산이 생성되었습니다. 예를 들어 PDF가 [!DNL Dynamic Media]에 업로드될 때 PDF의 페이지에서 IPS가 생성된 이미지 자산은 파생된 자산으로 간주됩니다. |
| 대상 폴더 | 선택 사항입니다. 많은 수의 이미지 세트 또는 스핀 세트를 정의할 경우 Adobe은 이러한 세트를 자산 자체가 포함된 폴더와 구분하도록 권장합니다. 이와 같이 이미지 세트 또는 스핀 세트 폴더를 만들고 응용 프로그램을 리디렉션하여 여기에서 생성된 일괄 세트 세트를 배치합니다.<br>이러한 경우 Experience Manager 자산 폴더 구조(`/content/dam`)에 일괄 세트 사전 설정이 활성 상태인 폴더를 지정합니다. 폴더가 대상 폴더로 허용하도록 [!DNL Dynamic Media] 동기화를 활성화해야 합니다. Dynamic Media](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)의 폴더 수준에서 [선택적 게시 구성을 참조하십시오.<br>폴더의 속성을 통해 사전 설정을 적용하는 경우 두 개 이상의 폴더에 주어진 일괄 세트 사전 설정이 할당될 수  **[!UICONTROL 있습니다]**. 자산 폴더의 속성 페이지](#apply-bsp-to-folders-via-properties)에서 배치 집합 사전 설정 적용을 참조하십시오.[<br>폴더를 지정하지 않으면 업로드한 자산 폴더와 동일한 폴더에 일괄 세트 사전 설정 생성 이미지 세트 또는 스핀 세트가 만들어집니다. |
| **[!UICONTROL 명명 규칙 설정]** |  |
| 접두어<br>또는<br>접미어 | 선택 사항입니다. 각 필드에 접두어, 접미어 또는 두 가지 모두를 입력합니다.<br>접두어 및 접미어 필드를 사용하면 특정 컨텐츠 세트에 대한 대체 사용자 정의 파일 이름 지정 규칙을 사용하여 일괄 세트 사전 설정을 여러 개 만들 수 있습니다. 이 방법은 회사의 정의된 기본 이름 지정 체계에 대한 예외가 있는 경우에 특히 유용합니다.<br>접두어나 접미어는 [에셋 이름 지정]  **** 규칙에서 정의하는  **[!UICONTROL 기준 이름에]** 추가됩니다. 접두어나 접미어를 추가하면 이미지 세트 또는 스핀 세트가 다른 자산과 독립적으로 단독 및 만들어지도록 할 수 있습니다. 또한 다른 사람이 파일 유형을 파악하는 데 도움이 될 수 있습니다. 예를 들어 사용된 색상 모드를 결정하려면 접두어 또는 접미어 `rgb` 또는 `cmyk`로 추가할 수 있습니다.<br>배치 집합 사전 설정 기능을 사용하는 데 집합 이름 지정 규칙을 지정할 필요는 없지만 세트 이름 지정 규칙을 사용하는 것이 좋습니다. 이 방법을 사용하면 묶음 세트 생성을 간소화하기 위해 세트로 그룹화할 이름 지정 규칙의 요소를 수만큼 정의할 수 있습니다. |
| **[!UICONTROL 규칙 결과 - RegX]** |  |
| 자산 이름 지정 규칙 - 일치 | 읽기 전용. 선택한 일치 양식 옵션 또는 입력한 원시 코드를 기반으로 정규 표현식 구문을 표시합니다. |
| 자산 이름 지정 규칙 - 기본 이름 | 읽기 전용. 선택한 기본 이름 양식 옵션 또는 입력한 원시 코드를 기반으로 정규 표현식 구문을 표시합니다. |
| 시퀀스 순서 지정 - 일치 | 읽기 전용. 선택한 양식 옵션 또는 입력한 원시 코드를 기반으로 정규 표현식 구문을 표시합니다. |

## 자산 폴더 {#apply-bsp}에 일괄 세트 사전 설정 적용 정보

하나 이상의 자산 폴더에 일괄 세트 사전 설정을 할당하면 모든 하위 폴더는 해당 상위 폴더에서 사전 설정을 자동으로 상속합니다.

자산 폴더에 여러 일괄 세트 사전 설정을 적용할 수 있습니다.

배치 사전 설정이 할당된 폴더는 **[!UICONTROL 카드]** 보기에서 폴더에 있는 사전 설정의 이름으로 사용자 인터페이스에 표시됩니다.

자산 폴더에 일괄 처리 집합 사전 설정을 적용하려면 다음 두 방법 중 하나를 사용합니다.

* [[배치 집합 사전 설정] 페이지의 자산 폴더에 일괄 집합 사전 설정 적용](#apply-bsp-to-folders-via-bsp-page)  - 이 방법을 사용하면 가장 유연하게 작업할 수 있습니다. 하나의 사전 설정 또는 여러 사전 설정을 하나의 폴더 또는 여러 폴더에 적용할 수 있습니다.
* [자산 폴더의 속성 페이지에서](#apply-bsp-to-folders-via-properties)  일괄 세트 사전 설정 적용 - 이 방법을 사용하면 하나 이상의 일괄 세트 사전 설정을 단일 폴더에 적용할 수 있습니다.

가장 좋은 방법은 자산 폴더가 [!DNL Dynamic Media]과 동기화된 다음 원하는 사전 설정을 적용하는 것입니다.

다음 두 가지 시나리오 중 하나가 발생하는 경우 폴더의 에셋을 재처리합니다.

* 이미 업로드된 자산이 있는 기존 자산 폴더에서 배치 집합 사전 설정을 실행하려 합니다.
* 나중에 이전에 에셋 폴더에 적용된 기존 일괄 세트 사전 설정을 편집할 수 있습니다.

<!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->

### 배치 집합 사전 설정 페이지 {#apply-bsp-to-folders-via-bsp-page}에서 자산 폴더에 일괄 집합 사전 설정 적용

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 일괄 세트 사전 설정]** 페이지의 **[!UICONTROL 사전 설정 이름]** 열 왼쪽에 있는 폴더에 적용할 각 일괄 세트 사전 설정의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 폴더]**&#x200B;에 배치 사전 설정 적용을 누릅니다.
1. **[!UICONTROL 폴더 선택]** 페이지에서 일괄 세트 사전 설정을 적용할 각 폴더의 확인란을 선택합니다.
1. **[!UICONTROL 폴더 선택]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 적용]**&#x200B;을 탭합니다.

### 자산 폴더의 속성 페이지 {#apply-bsp-to-folders-via-properties}에서 일괄 세트 사전 설정 적용

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;으로 이동합니다.
1. 하나 이상의 일괄 세트 사전 설정을 적용할 폴더로 이동합니다.
1. 페이지에서 **[!UICONTROL 이름]** 열의 왼쪽에 있는 폴더의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 탭합니다.
1. 폴더의 속성 페이지에서 **[!UICONTROL Dynamic Media 처리]** 탭을 누릅니다.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-apply-via-properties2a.png)

1. **[!UICONTROL 배치 집합 사전 설정]**&#x200B;의 **[!UICONTROL 사전 설정 이름]** 드롭다운 목록 상자에서 적용할 일괄 처리 집합 사전 설정의 이름을 선택합니다. 위의 스크린샷은 자산 폴더에 적용된 두 개의 선택한 일괄 세트 사전 설정을 보여줍니다.

   **[!UICONTROL 사전 설정 이름]** 드롭다운 목록 상자에 일괄 세트 사전 설정 이름이 없는 경우, 아직 일괄 세트 사전 설정을 만들지 않았음을 의미합니다. 이미지 세트 또는 스핀 세트](#creating-bsp)에 대한 배치 집합 사전 설정 만들기를 참조하십시오.[

   적용된 일괄 처리 집합 사전 설정을 제거하려면 사전 설정 유형의 오른쪽에 있는 **[!UICONTROL X]**&#x200B;을 누릅니다.

1. 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭합니다.

## 배치 집합 사전 설정 {#edit-bsp} 편집

만든 기존 배치 집합 사전 설정을 편집할 수 있습니다. 자산 이름 지정 규칙 또는 순서 순서에 대해 만든 표현식 그룹을 변경할 수 있습니다. 필요한 경우 대상 폴더를 업데이트하고 이름 지정 규칙을 설정할 수도 있습니다.

그러나 사전 설정의 이름 또는 사전 설정 유형(이미지 세트 또는 회전 세트)은 변경할 수 없습니다. 사전 설정의 이름을 변경해야 할 경우 기존 사전 설정을 복사하고 새 이름을 지정합니다. [배치 집합 사전 설정 복사](#copy-bsp)를 참조하십시오.

이전에 폴더에 적용된 일괄 처리 세트 사전 설정을 편집하는 경우 새로 편집한 일괄 세트 사전 설정은 해당 폴더에 업로드된 새 자산에만 적용됩니다.

새로 편집한 사전 설정을 폴더의 기존 자산에 다시 적용하려면 폴더를 다시 처리해야 합니다. <!-- See [Reprocessing assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). -->이러한 방식으로 기존 에셋은 이제 이미지 세트 또는 스핀 세트에 포함되고 추가될 수 있습니다. 또한 사용된 이전 일괄 세트 사전 설정을 기반으로 이미지 세트 또는 스핀 세트에 이미 포함된 기존 에셋은 그대로 표시되고 제거되지 않습니다. 이 시나리오에서는 새로 편집한 사전 설정을 기반으로 더 이상 자격이 부여되지 않는다고 가정합니다.

**배치 집합 사전 설정을 편집하려면:**

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 일괄 세트 사전 설정]** 페이지의 **[!UICONTROL 사전 설정 이름]** 열 왼쪽에 있는 변경 세트 사전 설정을 확인합니다.
1. 도구 모음에서 **[!UICONTROL 일괄 세트 사전 설정 편집]**&#x200B;을 누릅니다.
1. 필요에 따라 사전 설정을 편집합니다.
1. **[!UICONTROL 일괄 세트 사전 설정]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장]**&#x200B;을 탭합니다.

## 기존 배치 집합 사전 설정 {#copy-bsp} 복사

복잡한 사전 설정을 수동으로 다시 만들지 않고 사전 설정의 이름을 바꾸려는 경우를 방지하기 위해 기존 일괄 세트 사전 설정을 복사할 수 있습니다. 그러나 사용된 사전 설정 유형(이미지 세트 또는 스핀 세트)은 변경할 수 없습니다.

자산 폴더에서 참조하는 기존 사전 설정을 복사하는 경우 해당 폴더는 영향을 받지 않습니다.

**기존 배치 집합 사전 설정을 복사하려면:**

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 배치 집합 사전 설정]** 페이지의 **[!UICONTROL 사전 설정 이름]** 열 왼쪽에 있는 복사할 배치 집합 사전 설정의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 복사]**&#x200B;를 누릅니다.
1. **[!UICONTROL 배치 집합 사전 설정 복사]** 대화 상자의 **[!UICONTROL 제목]** 텍스트 상자에 사전 설정의 새 이름을 입력합니다.

   ![bsp-copy2.png](/help/assets/assets-dm/bsp-copy2.png)

1. **[!UICONTROL 복사]**&#x200B;를 누릅니다.

## {#remove-bsp-from-folder} 폴더에서 일괄 세트 사전 설정 제거 정보

폴더에서 일괄 처리 세트 사전 설정을 제거하면 이러한 폴더에 업로드하는 모든 새 자산에는 일괄 처리 세트 사전 설정이 적용되지 않습니다. 이미 이미지 세트에 추가된 폴더의 기존 에셋 또는 폴더에 적용된 일괄 세트 사전 설정을 기반으로 spint 세트를 기반으로 하는 기존 에셋은 그대로 표시됩니다.

대신 *폴더에서* 사전 설정을 삭제하려면 [일괄 처리 세트 사전 설정 삭제](#delete-bsp)를 참조하십시오.

폴더에서 일괄 세트 사전 설정을 제거하는 데 사용할 수 있는 방법에는 두 가지가 있습니다.

* [[일괄 처리 집합 사전 설정] 페이지를](#remove-bsp-from-folders-via-bsp-page)  통해 폴더에서 일괄 세트 사전 설정 제거 - 이 방법을 사용하면 가장 유연하게 수행할 수 있습니다. 단일 폴더 또는 여러 폴더에서 단일 사전 설정 또는 여러 사전 설정을 제거할 수 있습니다.
* [폴더의 속성 페이지에서](#remove-bsp-from-folders-via-properties)  일괄 세트 사전 설정 제거 - 이 방법을 사용하면 하나의 폴더에서만 하나 이상의 일괄 세트 사전 설정을 제거할 수 있습니다.

### 배치 집합 사전 설정 페이지 {#remove-bsp-from-folders-via-bsp-page}을(를) 통해 폴더에서 배치 집합 사전 설정 제거

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 일괄 세트 사전 설정]** 페이지의 **[!UICONTROL 사전 설정 이름]** 열 왼쪽에 있는 하나 이상의 폴더에서 제거할 하나 이상의 일괄 세트 사전 설정의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 폴더에서 일괄 처리 사전 설정 제거]**&#x200B;를 누릅니다.

1. **[!UICONTROL 폴더 선택]** 페이지에서 일괄 세트 사전 설정을 제거할 폴더를 하나 이상 선택합니다.
1. **[!UICONTROL 폴더 선택]** 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 제거]**&#x200B;를 탭합니다.

   ![bsp-remove-from-folders3.png](/help/assets/assets-dm/bsp-remove-from-folders3.png)

1. **[!UICONTROL 프로필 제거]** 대화 상자에서 **[!UICONTROL 제거]**&#x200B;를 누릅니다.

### 폴더의 속성 페이지 {#remove-bsp-from-folders-via-properties}에서 일괄 세트 사전 설정 제거

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 자산]** > **[!UICONTROL 파일]**&#x200B;으로 이동합니다.
1. 하나 이상의 일괄 세트 사전 설정을 제거할 폴더로 이동합니다.
1. 페이지에서 **[!UICONTROL 이름]** 열의 왼쪽에 있는 폴더의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 속성]**&#x200B;을 탭합니다.
1. 폴더의 속성 페이지에서 **[!UICONTROL Dynamic Media 처리]**&#x200B;를 탭합니다.

   ![bsp-apply-via-properties2.png](/help/assets/assets-dm/bsp-remove-via-properties2.png)

1. **[!UICONTROL 일괄 세트 사전 설정]** 아래에서 사전 설정 유형의 오른쪽에 있는 **[!UICONTROL X]**&#x200B;을 탭합니다.

1. 페이지의 오른쪽 위 모서리에서 **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭합니다.

## 배치 집합 사전 설정 삭제 중 {#delete-bsp}

배치 집합 사전 설정을 삭제하여 [!DNL Dynamic Media]에서 영구적으로 제거할 수 있습니다. 즉, 폴더의 **[!UICONTROL 속성]** 페이지에 있는 **[!UICONTROL Dynamic Media 처리]** 탭의 **[!UICONTROL 일괄 세트 사전 설정]** 드롭다운 목록에 해당 사전 설정이 더 이상 표시되지 않습니다.  따라서 사전 설정은 폴더 재처리 과정의 기존 에셋에 적용되지 않거나 새 에셋이 폴더에 업로드될 때 적용되지 않습니다.

이전에 하나 이상의 폴더에 적용된 사전 설정을 삭제하면 해당 폴더의 자산에서 만들어진 이미지 세트 또는 스핀 세트가 그대로 계속 표시됩니다.

대신 *폴더에서* 사전 설정을 제거하려면 [폴더에서 일괄 세트 사전 설정 제거](#remove-bsp-from-folder)를 참조하십시오.

**배치 집합 사전 설정을 삭제하려면 다음을 수행하십시오.**

1. Adobe Experience Manager 로고를 누르고 **[!UICONTROL 도구]** > **[!UICONTROL 자산]** > **[!UICONTROL 배치 집합 사전 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL 일괄 세트 사전 설정]** 페이지의 **[!UICONTROL 사전 설정 이름]** 열 왼쪽에 있는 삭제할 하나 이상의 일괄 세트 사전 설정의 확인란을 선택합니다.
1. 도구 모음에서 **[!UICONTROL 일괄 세트 사전 설정 삭제]**&#x200B;를 누릅니다.

   ![bsp-delete2.png](/help/assets/assets-dm/bsp-delete2.png)

1. **[!UICONTROL 배치 집합 사전 설정 삭제]** 대화 상자에서 **[!UICONTROL 삭제]**&#x200B;를 탭합니다.

   삭제하려는 사전 설정이 자산 폴더에서 참조되는 경우 대신 **[!UICONTROL 강제 삭제]**&#x200B;를 탭합니다.

   ![bsp-delete3.png](/help/assets/assets-dm/bsp-delete3.png)

>[!MORELIKETHIS]
>
>* [이미지 세트](/help/assets/dynamic-media/image-sets.md)
>* [스핀 세트](/help/assets/dynamic-media/spin-sets.md)
>* [Dynamic Media의 폴더 수준에서 선택적 게시 구성](/help/assets/dynamic-media/selective-publishing.md#selective-publish-configure-folder)  - 단일 폴더를 동기화하여 주는 방법에 대한 자세한 내용은 주제의 &quot;동기화 모드&quot;를 참조하십시오 [!DNL Dynamic Media].
>* [Cloud Services에서 Dynamic Media 구성 만들기](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services)  - 모든 폴더를 동기화하 [!DNL Dynamic Media]는 방법에 대한 자세한 내용은 주제의 &quot;Dynamic Media 동기화 모드&quot;를 참조하십시오.

