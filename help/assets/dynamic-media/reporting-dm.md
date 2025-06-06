---
title: Dynamic Media에서 보고
description: Dynamic Media 게재 URL에 대한 오류 보고서를 요청할 수 없는 방법을 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 실패한 Dynamic Media 게재 URL에 대한 오류 보고서 요청

게재 시 실패한 Dynamic Media URL을 식별하는 오류 보고서를 요청할 수 있습니다. 보고서는 최대 5일의 데이터 집계이며 CSV 형식으로 사용할 수 있습니다. 오류 보고서에는 다음 정보가 포함됩니다.

* 실패한 Dynamic Media 게재 URL - 실패 URL은 게재 시 콘텐츠를 생성할 수 없는 Dynamic Media 생성 URL입니다.
* 레퍼러 URL - 실패한 게재 URL이 호출되는 레퍼러 URL.
* 실패 횟수 - 게재 URL이 로드되어 오류가 발생한 횟수입니다.

오류 보고서를 요청하면 Adobe Dynamic Media 팀이 보고서를 CSV 형식으로 이메일로 보냅니다. 이 기간은 요청을 한 날로부터 5일을 포함합니다.

특정 회사에 대해 한 달에 한 번 오류 보고서를 요청할 수 있습니다.

**실패한 Dynamic Media 게재 URL에 대한 오류 보고서를 요청하려면:**

1. [Dynamic Media 계정과 연결된 회사 이름으로 reports-dynamic-media@adobe.com](mailto:reports-dynamic-media@adobe.com)에 전자 메일을 보냅니다.

   회사 이름을 모르는 경우 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 도구]** > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL 다이내믹 미디어 구성]**&#x200B;에서 [다이내믹 미디어 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=ko#configuring-dynamic-media-cloud-services) 페이지를 참조하십시오. Dynamic Media 구성 브라우저 페이지에서 **[!UICONTROL 전역]**&#x200B;을 클릭하고 *[Dynamic_Media_folder_icon]* 확인란을 선택한 다음 **[!UICONTROL 편집]**&#x200B;을 선택합니다. Dynamic Media 구성 페이지에 액세스하려면 AEM에 관리자 권한이 있어야 합니다.

   ![Dynamic Media 구성 페이지에 액세스합니다.](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
