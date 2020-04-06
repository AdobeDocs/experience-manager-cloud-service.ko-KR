---
title: 자산, 폴더 및 컬렉션을 링크로 공유
description: 이 문서에서는 Experience Manager 자산 내에서 자산, 폴더 및 컬렉션을 하이퍼링크로 공유하는 방법에 대해 설명합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Adobe Experience Manager에서 관리하는 에셋 공유 및 배포 {#share-assets-from-aem}

AEM(Adobe Experience Manager) 자산을 사용하면 자산, 폴더 및 컬렉션을 조직 및 외부 개체(파트너 및 공급업체 등)의 멤버와 공유할 수 있습니다. 다음 방법을 사용하여 Experience Manager Assets의 자산을 클라우드 서비스로 공유할 수 있습니다.

* 링크로 공유
* 자산 다운로드
* AEM 데스크탑 앱을 통해 공유
* Adobe Asset Link를 통해 공유
* (향후 기능) 브랜드 포털을 사용하여 공유

## 링크로 자산 공유 {#sharelink}

사용자와 공유할 에셋의 URL을 생성하려면 링크 공유 대화 상자를 사용합니다. 관리자 권한이 있거나 읽기 권한이 있는 사용자는 `/var/dam/share` 해당 사용자와 공유된 링크를 볼 수 있습니다. 링크를 통해 자산을 공유하는 것은 AEM 자산에 먼저 로그인하지 않고도 외부 당사자가 리소스를 사용할 수 있도록 하는 편리한 방법입니다.

>[!NOTE]
>
>* 링크로 공유할 폴더나 자산에 대해 ACL 편집 권한이 필요합니다.
>* 사용자와 링크를 공유하기 전에 요일 CQ 메일 서비스가 구성되어 있는지 확인합니다. 그렇지 않으면 오류가 발생합니다.


1. 자산 사용자 인터페이스에서 링크로 공유할 자산을 선택합니다.
1. 도구 모음에서 링크 공유를 클릭/ **[!UICONTROL 탭합니다]**.

   [링크 공유] 필드에 자산 링크가 자동으로 **[!UICONTROL 만들어집니다]** . 이 링크를 복사하고 사용자와 공유합니다. 링크의 기본 만료 시간은 하루입니다.

   또는 이 절차의 3-7단계를 수행하여 이메일 수신자를 추가하고 링크의 만료 시간을 구성한 다음 대화 상자에서 보냅니다.

   >[!NOTE]
   >
   >공유 에셋이 다른 위치로 이동하면 해당 링크가 작동하지 않습니다. 링크를 다시 만들고 사용자와 다시 공유합니다.

1. 웹 콘솔에서 Day CQ Link **[!UICONTROL Externalizer]** 구성을 열고 도메인 **[!UICONTROL 필드에서 다음]** 속성을 수정하여각각에 대해 언급된 값을 사용합니다.

   * 로컬
   * 작성자
   * 페이지를
   로컬 및 작성자 속성의 경우 로컬 및 작성자 인스턴스의 URL을 각각 제공합니다. 단일 AEM 작성자 인스턴스를 실행하는 경우 로컬 및 작성자 속성은 모두 동일한 값을 갖습니다. 게시의 경우 게시 인스턴스의 URL을 제공합니다.

1. [링크 공유] **[!UICONTROL 대화 상자의]** 이메일 주소 상자에 링크를 공유할 사용자의 이메일 ID를 입력합니다. 여러 사용자와 링크를 공유할 수도 있습니다.

   사용자가 조직의 구성원인 경우 입력 영역 아래 목록에 표시되는 제안된 이메일 ID에서 사용자의 이메일 ID를 선택합니다. 외부 사용자의 경우 전체 이메일 ID를 입력한 다음 목록에서 선택합니다.

   사용자에게 보낼 이메일을 활성화하려면 요일 CQ 메일 서비스에서 SMTP 서버 [세부 사항을 구성합니다](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >조직의 구성원이 아닌 사용자의 이메일 ID를 입력하면 &quot;외부 사용자&quot;라는 단어 앞에 사용자의 이메일 ID가 붙습니다.

1. 제목 **[!UICONTROL 상자에]** 공유할 자산의 제목을 입력합니다.
1. 메시지 **[!UICONTROL 상자에]** 선택적 메시지를 입력합니다.
1. 만료 **[!UICONTROL 필드에서]** 날짜 선택기를 사용하여 링크의 만료 날짜 및 시간을 지정합니다. 기본적으로 만료 날짜는 링크를 공유하는 날짜로부터 일주일 동안 설정됩니다.
1. 사용자가 변환과 함께 원본 이미지를 다운로드할 수 있도록 하려면 원본 파일 **[!UICONTROL 다운로드 허용을 선택합니다]**.

   >[!NOTE]
   >
   >기본적으로 사용자는 링크로 공유하는 자산의 표현물만 다운로드할 수 있습니다.

1. **[!UICONTROL 공유]**&#x200B;를 클릭합니다. 링크가 이메일을 통해 사용자와 공유됨을 확인하는 메시지가 표시됩니다.
1. 공유 자산을 보려면 사용자에게 전송되는 이메일의 링크를 클릭/탭합니다. 공유 자산은 Adobe Marketing Cloud **[!UICONTROL 페이지에 표시됩니다]** .

   목록 보기로 전환하려면 도구 모음에서 레이아웃 아이콘을 클릭/탭합니다.

1. 자산의 미리 보기를 생성하려면 공유 자산을 클릭/탭합니다. 미리 보기를 닫고 Marketing Cloud **[!UICONTROL 페이지로 돌아가려면]** 도구 모음에서 뒤로를 클릭/ **[!UICONTROL 탭합니다]** . 폴더를 공유한 경우 상위 폴더를 클릭/탭하여 **[!UICONTROL 상위]** 폴더로 돌아갑니다.

   >[!NOTE]
   >
   >AEM 파섹JPG, PNG, GIF, BMP, INDD, PDF 및 PPT입니다. 다른 MIME 유형의 자산만 다운로드할 수 있습니다.

1. 공유 자산을 다운로드하려면 도구 **[!UICONTROL 모음에서 선택을]** 클릭/탭하고 자산을 클릭/탭한 다음 도구 **[!UICONTROL 모음에서 다운로드를 클릭/탭]** 탭합니다.
1. 링크로 공유한 자산을 보려면 자산 UI로 이동하고 전역 탐색 아이콘을 클릭/탭합니다. 목록에서 **[!UICONTROL 내비게이션을]** 선택하여 탐색 창을 표시합니다.
1. 탐색 창에서 공유 **[!UICONTROL 링크를]** 선택하여 공유 에셋 목록을 표시합니다.
1. 자산 공유를 취소하려면 자산을 선택하고 도구 모음에서 **[!UICONTROL 공유]** 해제를 탭/클릭합니다.

자산 공유를 해제한다는 메시지가 나타납니다. 또한 자산 항목이 목록에서 제거됩니다.

## 에셋 다운로드 및 공유 {#download-and-share-assets}

사용자는 일부 에셋을 다운로드하고 Experience Manager 외부에서 공유할 수 있습니다. 자세한 내용은 자산 [검색](/help/assets/search-assets.md)방법, 자산 [다운로드](/help/assets/download-assets-from-aem.md)방법 및 컬렉션 다운로드 [방법을 참조하십시오.](manage-collections.md#download-a-collection)

## 크리에이티브 전문가와 에셋 공유 {#share-with-creatives}

마케터와 비즈니스 라인 사용자는 승인된 자산을 자신의 크리에이티브 전문가와 손쉽게 공유할 수 있습니다.

* **AEM 데스크탑 앱**:이 앱은 Windows 및 Mac에서 작동합니다. 데스크탑 [앱 개요를](https://docs.adobe.com/content/help/ko-KR/experience-manager-desktop-app/using/introduction.html)참조하십시오. 권한이 있는 모든 데스크탑 사용자가 공유 에셋에 손쉽게 액세스할 수 있는 방법을 알아보려면 에셋을 [검색하고 미리](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets)보십시오. 데스크톱 사용자는 새 자산을 만들고 새 이미지를 업로드하여 AEM 사용자와 다시 공유할 수 있습니다. 데스크탑 앱을 [사용하여 자산](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem)업로드를 참조하십시오.

* **Adobe Asset 링크**:크리에이티브 전문가는 Adobe InDesign, Adobe Illustrator 및 Adobe Photoshop에서 바로 에셋을 검색하고 사용할 수 있습니다.

### Best practices and troubleshooting {#bestpractices}

* 이름에 공백이 포함된 자산 폴더 또는 컬렉션은 공유되지 않을 수 있습니다.
* 사용자가 공유 자산을 다운로드할 수 없는 경우 AEM 관리자에게 [다운로드 제한이](/help/assets/configure-asset-sharing.md#maxdatasize) 무엇인지 확인하십시오.
* 공유 자산에 대한 링크가 포함된 이메일을 보낼 수 없거나 다른 사용자가 이메일을 받을 수 없는 경우 [이메일 서비스가](/help/assets/configure-asset-sharing.md#configmailservice) 구성되었는지 여부를 AEM 관리자에게 문의하십시오.
* 링크 공유 기능을 사용하여 자산을 공유할 수 없는 경우 적절한 권한이 있는지 확인하십시오. 자산 [공유를 참조하십시오](#sharelink).

<!--
Add content or link about how to share using BP, DA, AAL, etc.
-->
