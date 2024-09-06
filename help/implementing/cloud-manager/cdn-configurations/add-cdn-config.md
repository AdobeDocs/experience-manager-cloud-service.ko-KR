---
title: CDN 구성 추가
description: Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 추가하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: e57a6ceb2482e61acabe928da0f539d26989985c
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 8%

---


# CDN 구성 추가 {#add-cdn}

SSL을 사용하여 도메인을 구성하려면 CDN 구성 추가를 완료해야 합니다.

>
>
>Adobe 관리 CDN의 경우 DV 인증서를 사용할 때 ACME 인증이 있는 사이트만 허용됩니다.

**CDN 구성을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **CDN 구성**&#x200B;을 클릭합니다.

1. CDN 구성 페이지의 오른쪽 상단 모서리에서 **추가**&#x200B;를 클릭합니다.

   ![CDN 구성 대화 상자](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

1. **CDN 구성** 대화 상자에서 필요한 정보를 제공합니다.

   * **원본** 드롭다운 목록에서 다음 중 하나를 실행하십시오.
      * **사이트:** Edge Delivery Services 사이트를 선택하십시오.
      * **환경:** Cloud Service 환경을 선택합니다.
         * **계층:** 선택한 환경에 대해 **Publish** 또는 **미리 보기** 웹 계층을 선택합니다.
   * CDN 유형을 선택하십시오. **Adobe 관리 CDN** 또는 **기타 CDN 공급자**.
   * 도메인을 선택합니다.
   * SSL 인증서를 선택합니다. **Adobe 관리 CDN**&#x200B;을(를) CDN 유형으로 선택한 경우에만 필요합니다.

1. **저장**&#x200B;을 클릭합니다.




