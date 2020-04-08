---
title: 2020.4.0용 클라우드 서비스 릴리스 노트로 Adobe Experience Manager
description: 2020.4.0용 Adobe Experience Manager 릴리스 노트
translation-type: tm+mt
source-git-commit: b05fe7e9150649b49fc5dae2e33955afc6a1acab

---


# Release Notes for Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

The following section outlines the general release notes for [!DNL Experience Manager] as a Cloud Service 2020.4.0.

## Release Date {#release-date}

클라우드 서비스 2020.4.0 [!DNL Experience Manager] 의 릴리스 날짜는 2020년 4월 9일입니다.

## 자산의 새로운 기능 {#assets}

현재 릴리스와 관련된 새로운 기능, 개선 사항 및 버그 수정에 대해 [!DNL Experience Manager Assets] 알아보십시오 [!DNL Dynamic Media] .

* [브랜드](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) 포털은 Experience Manager 자산에 대한 자산 배포 사용 사례를 지원합니다. [!DNL Brand Portal] 승인된 브랜드 및 제품 자산을 외부 에이전시, 파트너, 내부 팀 및 리셀러에 안전하게 배포하여 조직의 마케팅 요구 사항을 충족할 수 있도록 지원합니다.
   * [!DNL Brand Portal] 구성은 [!DNL Adobe I/O] 콘솔을 통해 완료됩니다.
   * Adobe Experience Manager에서 Cloud Service [!DNL Brand Portal] 로 자산 [!DNLE] 소싱은 아직 지원되지 않습니다.

* [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) v2.0은 클라우드 [!DNL Experience Manager] 서비스로 작동합니다. [!DNL Adobe Asset Link] 데스크탑 앱 [!DNL Experience Manager Assets] 및 인앱 [!DNL Creative Cloud] [!DNL Adobe Photoshop][!DNL Adobe Illustrator][!DNL Adobe InDesign] [!DNL Asset Link] 패널을 통해 콘텐츠 제작 프로세스를 통해 크리에이티브와 마케터 간의 협업을 간소화할 수 있습니다.
   * [!DNL Experience Manager] 에 대해 사전 구성된 [!DNL Adobe Asset Link]경우 [손쉽게 구성할](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) 수 있고 크리에이티브 전문가에게 보다 신속하게 롤아웃할 수 있습니다.
   * [!DNL Asset Link] 이제 크리에이티브 [사용자가 다른](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) [!DNL Experience Manager] 환경에 손쉽게 연결할 수 있는 Experience Manager 환경 전환기를 지원합니다. 이 기능이 유용한 예로, 서로 다른 [!DNL Experience Manager Assets] 배포를 사용하여 여러 클라이언트와 함께 작업하는 에이전시 디자이너가 여기에 포함됩니다.

* 사용자는 특정 폴더 계층 구조에 대해 폴더 속성 [사용자 인터페이스에서 자동으로 시작하도록](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)  사후 처리 워크플로우를 구성할 수 있습니다.
   * 폴더 [!UICONTROL 속성] 사용자 인터페이스는 메타데이터 프로필, 처리 [!UICONTROL 프로필] 및 새로운 자동 시작 워크플로우 구성이 포함된 새로운 자산 처리 탭으로 간소화됩니다.
   * 자산 재처리 대화 상자에서는 특정 처리 프로필을 선택하고 하위 폴더에서 다시 처리할 수 있습니다.
   * [!DNL Dynamic Media]:안전한 미리 보기용으로 에셋이 자동 게시되도록 선택적 게시 구성을 추가했습니다. 또한 공개 도메인에 제공하기 위해 DMS7에 게시하지 않고도 Experience Manager에 자산을 명시적으로 게시할 수 있습니다.

* 다음 문제가 해결되었습니다.
   * 자산 처리 문제에 대한 수정 사항.
   * 구성 및 자산 게시가 [!DNL Dynamic Media] [!DNL Dynamic Media] 배달 서비스에 수정되었습니다.

>[!MORELIKETHIS]
>
>* [Adobe Asset 링크 정보](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [브랜드 포털 구성](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Experience Manager가 자산 링크와 연동되도록 구성](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Adobe Experience Manager에서 자산 마이크로 서비스를 사용하여 워크플로우 제작](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)

