---
title: AEM Forms에서 양식 및 문서를 게시하고 게시 취소하는 방법
description: 적응형 Forms의 게시 및 게시 취소를 예약합니다. 게시된 양식은 게시 인스턴스에 복제됩니다.
content-type: reference
topic-tags: publish
discoiquuid: 32a7a50c-74f4-49bc-a0bd-a9ec142527cb
feature: Adaptive Forms
role: User
hide: true
hidefromtoc: true
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 0%

---


# 양식 및 문서 게시 및 게시 취소{#publishing-and-unpublishing-forms-and-documents}

[!DNL AEM Forms]을(를) 사용하면 양식을 쉽게 만들고 게시하고 게시 취소할 수 있습니다. [!DNL AEM Forms] 서버는 Author와 Publish의 두 인스턴스를 제공합니다. 작성자 인스턴스는 양식 에셋 및 리소스를 만들고 관리하기 위한 것입니다. Publish 인스턴스는 최종 사용자가 사용할 수 있는 에셋 및 관련 리소스를 보관하기 위한 것입니다.

## 지원되는 에셋   {#supported-assets-nbsp}

[!DNL AEM Forms]에서 지원하는 자산 유형은 다음과 같습니다.

* 적응형 양식
* 적응형 문서
* 적응형 양식 단편
* 테마
* 양식 서식 파일 <!-- (XFA forms) -->
* PDF forms
* 문서(플랫 PDF 문서)
* 양식 세트
* 리소스(이미지, 스키마 및 스타일시트)

처음에는 모든 에셋을 작성자 인스턴스에서만 사용할 수 있습니다. 관리자 또는 양식 작성자는 리소스를 제외한 모든 에셋을 게시할 수 있습니다.

양식을 선택하고 게시하면 관련 에셋과 리소스도 게시됩니다. 그러나 종속 자산은 게시되지 않습니다. 이러한 맥락에서 관련 에셋 및 리소스는 게시된 에셋이 사용하거나 참조하는 에셋입니다. 종속 에셋은 게시된 에셋을 참조하는 에셋입니다.

적응형 Forms은 자동으로 게시되지 않는 일부 구성, 설정 및 사용자 지정을 활용할 수 있습니다. 적응형 양식을 게시하기 전에 이러한 리소스를 게시하거나 활성화하는 것이 좋습니다.

* 편집 가능한 적응형 양식 템플릿
* Adobe Sign, Typekit, reCAPTCHA 및 양식 데이터 모델(FDM)에 대한 Cloud Service 구성
* 다른 Cloud Services 구성은 사용자에게 관리자 권한이 있는 경우에만 활성화됩니다.
* 사용자 지정. 여기에는 다음이 포함되지만 이에 국한되지 않습니다.

   * 사용자 정의 레이아웃
   * 사용자 지정 모양
   * CSS 파일 - 적응형 양식 컨테이너 속성 대화 상자에서 입력으로 취함
   * 클라이언트 라이브러리 카테고리 - 적응형 양식 컨테이너 속성 대화 상자에서 입력으로 취함
   * 적응형 양식 템플릿의 일부로 포함될 수 있는 다른 모든 클라이언트 라이브러리.
   * 디자인 경로

## 자산 상태 {#asset-states}

자산은 다음과 같은 상태를 가질 수 있습니다.

* **게시 취소됨:** 게시된 적이 없는 에셋(게시되지 않은 상태는 Forms 에셋에만 적용됩니다. 서신 관리 에셋에 게시 취소 상태가 없습니다.)
* **게시됨**: 게시되었으며 Publish 인스턴스에서 사용할 수 있는 에셋입니다.
* **수정됨**: 게시된 후 수정된 에셋입니다.

## Publish an 에셋 {#publish-an-asset}

1. [!DNL AEM Forms] 서버에 로그인합니다.
1. 다음 중 하나를 사용하여 자산을 선택하고 게시합니다.

   1. 자산 위로 포인터를 이동하고 **[!UICONTROL Publish]** ![aem6forms_globe](assets/aem6forms_globe.pngasset.png)을(를) 선택합니다.
   1. 다음 중 하나를 수행한 다음 Publish을 선택합니다.

      * 카드 보기를 사용하는 경우 **[!UICONTROL 선택 항목 입력]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png)을 선택하고 자산을 선택합니다. 에셋이 선택되어 있습니다.
      * 목록 보기에 있는 경우 에셋의 확인란을 선택합니다. 에셋이 선택되어 있습니다.
      * 세부 정보를 표시할 자산을 선택하십시오.
      * 보기 속성 ![보기 속성](assets/viewproperties.png)을 탭하여 에셋의 속성을 표시합니다.

      >[!NOTE]
      >
      >여러 에셋을 선택하지 마십시오. 한 번에 여러 자산을 게시할 수 없습니다.

1. Publish 프로세스가 시작되면 관련 에셋 및 리소스가 모두 나열된 확인 대화 상자가 나타납니다. 관련 에셋이 포함된 대화 상자에서 **[!UICONTROL Publish]**&#x200B;을(를) 선택합니다. 에셋이 게시되고 Publish Assets 성공 대화 상자가 나타납니다.

   >[!NOTE]
   >
   >적응형 Forms의 경우 관련 에셋과 함께 적응형 양식 페이지 이름도 표시됩니다.

   ![모든 관련 에셋 및 리소스와 함께 하는 확인 대화 상자](assets/p4.png)

   모든 관련 에셋 및 리소스와 함께 하는 확인 대화 상자입니다.

   >[!NOTE]
   >
   >Forms Manager의 경우, 사용자에게 나열된 에셋을 게시할 권한이 없으면 Publish 작업이 비활성화됩니다. 추가 권한이 필요한 에셋은 빨간색으로 표시됩니다.

   에셋이 게시되면 에셋의 메타데이터 속성이 Publish 인스턴스에 복사되고 에셋의 상태가 게시됨으로 변경됩니다. 게시된 종속 에셋의 상태도 게시됨으로 변경됩니다.

   <!-- After publishing an asset, you can use the Forms Portal to display all the assets on a web page. For more information, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md).-->

## Publish 모든 서신 관리 Assets {#publish-all-the-correspondence-management-assets}

[!DNL AEM Forms]을(를) 사용하면 한 번에 모든 응답 관리 자산을 서버에 게시할 수 있습니다. 게시된 에셋에는 모든 서신 관리 에셋과 관련 의존성이 포함됩니다.

다음 단계를 완료하여 모든 서신 관리 에셋을 서버에 게시합니다.

1. [!DNL AEM Forms] 서버에 로그인합니다.
1. 전역 탐색 모음에서 **Adobe Experience Manager**&#x200B;을(를) 선택하십시오.
1. ![도구](assets/tools.png)를 선택한 다음 **Forms**&#x200B;을 선택합니다.
1. **Publish Correspondence Management Assets**&#x200B;을(를) 선택합니다.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   Publish 모든 응답 관리 Assets 페이지가 나타나고 Publish 응답 관리 Assets 프로세스가 마지막으로 시도된 시간에 대한 정보가 표시됩니다.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. **Publish**&#x200B;을(를) 선택하고 확인 메시지에서 **확인**&#x200B;을(를) 선택합니다.

   배치 프로세스가 완료되면 마지막 실행 세부 정보를 볼 수 있습니다. 여기에는 관리자 로그인 및 배치 실행 성공 또는 실패 여부 등의 정보가 포함됩니다.

   >[!NOTE]
   >
   >Publish 프로세스는 일단 시작되면 취소할 수 없습니다. 또한 Publish 작업이 진행 중일 때는 에셋을 만들거나, 삭제하거나, 수정하거나, 게시하거나, 모든 응답 관리 Assets 내보내기 작업을 시작하지 마십시오.

## Forms 및 문서에 대한 게시 및 게시 취소 자동화 {#automate-publishing-and-unpublishing-for-forms-amp-documents}

[!DNL AEM Forms]을(를) 통해 Forms 및 문서에 대한 자산 게시 및 게시 취소를 예약할 수 있습니다. 메타데이터 편집기에서 일정을 지정할 수 있습니다. 양식 메타데이터 관리에 대한 자세한 내용은 [양식 메타데이터 관리](manage-form-metadata.md)를 참조하십시오.

Forms 및 문서 에셋의 게시 및 게시 취소 날짜와 시간을 예약하려면 다음 단계를 따르십시오.

1. 자산을 선택하고 **[!UICONTROL 속성 보기]**&#x200B;를 선택합니다. 메타데이터 속성 페이지가 열립니다.
1. 메타데이터 속성 페이지에서 **[!UICONTROL 고급]**&#x200B;을 선택한 다음 **[!UICONTROL 편집]** ![illustratorcc_penciltool_cur_edit_2_17](assets/illustratorcc_penciltool_cur_edit_2_17.png)을(를) 선택합니다.
1. **[!UICONTROL Publish 설정 시간]** 및 **[!UICONTROL Publish 해제 시간]** 필드에서 날짜 및 시간을 선택합니다.\
   **[!UICONTROL 완료]** ![aem6forms_check](assets/aem6forms_check.png)를 선택합니다.

## 자산 게시 취소 {#unpublish-an-asset}

1. 게시된 자산을 선택하고 **[!UICONTROL 게시 취소]** ![게시 취소](assets/unpublish.png)를 선택합니다.
1. 다음 중 하나를 사용하여 에셋을 선택하고 게시 취소합니다.

   1. 자산 위로 포인터를 이동하고 **[!UICONTROL 게시 취소]** ![게시 취소](assets/unpublish.png)를 선택합니다.
   1. 다음 중 하나를 수행한 다음 게시 취소를 선택합니다.

      * 카드 보기를 사용하는 경우 **[!UICONTROL 선택 항목 입력]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png)을 선택하고 자산을 선택합니다. 에셋이 선택되어 있습니다.

      * 목록 보기에 있는 경우 에셋 위로 마우스를 가져간 후 ![selectassetcheckmark](assets/selectassetcheckmark.png) 을 선택합니다. 에셋이 선택되어 있습니다.

      * 세부 정보를 표시할 자산을 선택하십시오.
      * 보기 속성 ![보기 속성](assets/viewproperties.png)을 탭하여 에셋의 속성을 표시합니다.

1. 게시 취소 프로세스가 시작되면 확인 대화 상자가 나타납니다. **[!UICONTROL 게시 취소]**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   >선택한 자산만 게시 취소되고, 하위 자산 및 참조된 자산(있는 경우)은 게시 취소되지 않습니다.

## 에셋 또는 편지를 이전에 게시한 버전으로 되돌리기 {#revert-an-asset-or-letter-to-the-previously-published-version}

에셋 또는 편지를 편집한 후 게시할 때마다 에셋 또는 편지의 버전이 만들어집니다. 에셋 또는 편지를 이전에 게시한 버전으로 되돌릴 수 있습니다. 현재 버전의 에셋 또는 문서에 문제가 있는 경우 이 작업을 수행해야 할 수 있습니다.

>[!NOTE]
>
>게시된 편지에 사용된 종속 자산이 시스템에서 삭제된 경우 편지를 마지막으로 게시된 상태로 되돌리지 마십시오.

1. 자산을 선택하고 **[!UICONTROL 이전에 게시된 버전으로 되돌리기]** ![되돌리기topreviouslypublishedversion](assets/reverttopreviouslypublishedversion.png)를 선택합니다.
1. 에셋을 되돌리기 전에 확인 대화 상자가 나타납니다. **[!UICONTROL 되돌리기]**&#x200B;를 선택합니다.

   에셋 또는 편지가 이전에 게시한 버전으로 롤백됩니다.

## 에셋 삭제 {#delete-an-asset}

>[!NOTE]
>
>자산을 삭제하면 게시 인스턴스에서 제거됩니다. 에셋을 삭제하면 기본 버전을 제외한 버전 내역도 제거됩니다.

1. 자산을 선택하고 **[!UICONTROL 삭제]** ![삭제](assets/delete.png)를 선택합니다.

   >[!NOTE]
   >
   >에셋을 탭하여 에셋 세부 정보를 표시하거나 속성 보기 ![viewproperties](assets/viewproperties.png)를 탭하여 에셋의 속성을 표시하는 경우에도 삭제 옵션을 사용할 수 있습니다.

1. 에셋이 삭제되기 전에 확인 대화 상자가 나타납니다. **[!UICONTROL 삭제]**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   >선택한 자산만 삭제되고 종속 자산은 삭제되지 않습니다. 에셋의 참조를 확인하려면 ![참조](assets/references.png)를 선택한 다음 에셋을 선택하세요.
   >
   >
   >삭제하려는 에셋이 다른 에셋의 하위 에셋인 경우 삭제되지 않습니다. 이러한 에셋을 삭제하려면 다른 에셋에서 이 에셋의 참조를 제거한 다음 다시 시도하십시오.

## 보호된 적응형 Forms {#protected-adaptive-forms}

선택한 사용자가 액세스할 양식에 대해 인증을 활성화할 수 있습니다. 양식에 대한 인증을 활성화하면 사용자가 로그인하기 전에 로그인 화면이 표시됩니다. 승인된 자격 증명을 가진 사용자만 양식에 액세스할 수 있습니다.

양식에 대한 인증을 활성화하려면 다음을 수행하십시오.

1. 브라우저에서 게시 인스턴스에서 configMgr을 엽니다.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Adobe Experience Manager 웹 콘솔 구성에서 **Apache Sling 인증 서비스**&#x200B;를 클릭하여 구성합니다.
1. 표시되는 Apache Sling 인증 서비스 대화 상자에서 **+** 단추를 사용하여 경로를 추가합니다.\
   경로를 추가하면 해당 경로의 양식에 대해 인증 서비스가 활성화됩니다.
