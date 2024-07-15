---
title: AEM Forms as a Cloud Service 환경의 설치 및 구성 문제를 해결하는 방법
description: AEM Forms as a Cloud Service 환경 설치 및 구성 문제 해결.
contentOwner: khsingh
feature: Adaptive Forms
role: User
exl-id: 249ec8f2-4176-428a-bfcf-80b381ec7263
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# 구성 {#installation-and-configuration}

Cloud Service 환경을 구성하는 동안 다음 문제 중 일부가 발생할 수 있습니다.

## Forms 옵션을 사용할 수 없음

**[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL Forms]** 옵션을 사용할 수 없습니다.

![Forms 옵션을 사용할 수 없습니다](assets/installation-configuration-forms-option-unavailable-troubleshooting.png)

**[!UICONTROL Forms]** 옵션을 활성화하려면:

1. [Cloud Manager](https://experience.adobe.com/)에 로그인
1. 프로그램을 찾은 다음 ![Forms 옵션을 사용할 수 없음](assets/Smock_Edit_18_N.svg) 아이콘을 클릭합니다. 프로그램의 프로그램 편집 페이지가 열립니다.
1. **[!UICONTROL 솔루션 및 추가 기능]** 탭을 엽니다.
1. **[!UICONTROL Forms]** 옵션을 선택하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![Forms 옵션 선택](assets/installation-configuration-select-forms-option.png)
1. 프로덕션 파이프라인과 비프로덕션 파이프라인 모두 [만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) 및 [실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)합니다.

파이프라인이 빌드되고 배포되면 **[!UICONTROL 탐색]** 페이지의 **[!UICONTROL Forms]** 옵션이 표시됩니다.

<!--  
## Environment creation fails {#environment-creation-fails}

Users are unable to create an [!DNL AEM Forms] as a Cloud Service environment. The environment creation fails after running for some time.

A missing profile can lead to environment creation failure. Check that the profile exists in Admin Console. If the profile does not exist, perform the following steps to create the profile:

1. Log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not any other ID or Federated ID to login.
1. Click the **[!UICONTROL Automated Forms Conversion Service]** option.
1. Click **[!UICONTROL New Profile]** in the Products tab.
1. Specify Name, Display Name, and Description for the profile. Click **[!UICONTROL Done]**. A profile is created.

If the profile exists and issues still persist, contact Adobe Support. -->

## 파이프라인 빌드 실패 {#build-pipeline-fails}

사용자가 빌드 파이프라인을 실행할 수 없습니다. 파이프라인이 일정 시간 동안 실행된 후 실패합니다.

이 문제를 해결하려면 Cloud Manager을 열고 환경에 대한 **[!UICONTROL 업데이트]** 옵션을 선택한 다음 파이프라인을 실행하십시오.


## 번들이 활성 상태가 아닙니다. {#bundles-inactive-state}

이 문제를 해결하려면 다음 단계를 수행하십시오.

1. AEM을 시작하고 모든 번들이 시작될 때까지 완전히 시작될 때까지 기다립니다.
1. AEM 중지(Ctrl + C).
1. Forms `.far` 파일을 설치 폴더에 넣습니다.
1. AEM 서버를 다시 시작합니다.