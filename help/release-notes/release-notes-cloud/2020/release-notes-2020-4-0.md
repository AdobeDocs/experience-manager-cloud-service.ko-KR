---
title: Adobe Experience Manager as a Cloud Service 2020.4.0용 릴리스 노트
description: "[!DNL Adobe Experience Manager] 2020.4.0용 as a Cloud Service 릴리스 노트"
exl-id: d98a3862-76fa-4b5b-b81a-333f5f532b67
source-git-commit: 9ceec0401b91bba2408bda89d4f2c486e2d51eec
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 93%

---

# Adobe Experience Manager as a Cloud Service 2020.4.0 릴리스 노트 {#release-notes}

이 페이지에서는 [!DNL Experience Manager] as a Cloud Service 2020.4.0 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 일자 {#release-date}

[!DNL Experience Manager] as a Cloud Service 2020.4.0의 출시일은 2020년 4월 9일입니다.

## Assets의 새로운 기능 {#assets}

현재 릴리스에 있는 [!DNL Experience Manager Assets] 및 [!DNL Dynamic Media]의 새로운 기능, 개선 사항 및 버그 수정에 대해 알아보십시오.

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)은 Experience Manager Assets에 대한 자산 분배 사용 사례를 지원합니다. [!DNL Brand Portal]은 승인된 브랜드 및 제품 자산을 외부 에이전시, 파트너, 내부 팀 및 리셀러에게 다운로드하도록 안전하게 분배하여 조직의 마케팅 요구 사항을 충족할 수 있도록 지원합니다.
   * [!DNL Brand Portal] 구성은 [!DNL Adobe I/O] 콘솔을 통해 완료됩니다. [Brand Portal 구성](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)을 참조하십시오.
   * [!DNL Brand Portal]의 Asset 소싱은 아직 [!DNL Experience Manager] as a Cloud Service에서 지원되지 않습니다.

* [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) v2.0은 [!DNL Experience Manager] as a Cloud Service에서 작동합니다. [!DNL Adobe Asset Link]는 인앱 [!DNL Asset Link] 패널을 통해 [!DNL Experience Manager Assets]을 [!DNL Creative Cloud] 데스크탑 앱인 [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] 및 [!DNL Adobe InDesign]과 연결하여 컨텐츠 제작 프로세스에서 크리에이티브와 마케터 간의 협업을 간소화합니다.
   * [!DNL Experience Manager]는 [!DNL Adobe Asset Link]용으로 사전 구성되어 있어서 크리에이티브 전문가가 [쉽게 구성](https://helpx.adobe.com/kr/enterprise/using/configure-aem-assets-for-asset-link.html)하고 더 빠른 롤아웃을 수행할 수 있습니다.
   * [!DNL Asset Link]는 이제 크리에이티브 사용자가 다른 [!DNL Experience Manager] 환경에 쉽게 연결할 수 있도록 해주는 [Experience Manager 환경 전환기](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink)를 지원합니다. 이 기능은 예를 들어 다양한 [!DNL Experience Manager Assets] 배포를 사용하여 여러 고객과 작업하는 에이전시 디자이너에게 유용합니다.

* 사용자는 특정 폴더 계층 구조에 대한 폴더 [!UICONTROL 속성] 사용자 인터페이스에서 [사후 처리 워크플로우](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)를 자동으로 시작하도록 구성할 수 있습니다.
   * 폴더 [!UICONTROL 속성] 사용자 인터페이스는 메타데이터 프로필, 처리 프로필 및 새로운 자동 시작 워크플로우 구성을 포함하는 새로운 [!UICONTROL 자산 처리] 탭을 사용하여 단순화되었습니다.

     ![처리 프로필은 폴더에 쉽게 적용할 수 있으며 폴더에 업로드된 모든 자산은 이러한 프로필을 사용하여 처리 중입니다](/help/assets/assets/asset-processing-folder-properties.png)

   * 자산 재처리 옵션을 사용하면 특정 처리 프로필을 선택하여 하위 폴더에서 사용자가 선택한 자산을 재처리할 수 있습니다.

     ![특정 처리 프로필을 사용하여 선택한 자산 재처리](/help/assets/assets/fpo-existing-asset-reprocess.gif)

   * [!DNL Dynamic Media]: 자산이 보안 미리 보기용으로만 자동 게시되도록 선택적 게시 구성을 추가했습니다. 또한 공중영역에서 전달하기 위해 DMS7에 게시하지 않고 자산을 Experience Manager에 명시적으로 게시할 수 있습니다.

### 버그 수정 {#assets-bug-fixes}

* 자산 처리 문제에 대한 수정 사항.
* [!DNL Dynamic Media] 구성 및 [!DNL Dynamic Media] 전달 서비스에 대한 자산 게시의 수정 사항.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link에 대하여](https://www.adobe.com/kr/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Brand Portal 구성](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Asset Link를 사용하도록 Experience Manager 구성](https://helpx.adobe.com/kr/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [에셋 마이크로서비스를 사용하여 Experience Manager에서 워크플로 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)

## Cloud Manager의 새로운 기능 {#whats-new-cloud-manager}

* 이제 Cloud Manager UI의 환경 페이지에서 게시자 URL을 사용할 수 있습니다.
* 사용자가 Cloud Manager 개요 페이지에서 프로그램을 편집, 전환 또는 추가할 수 있도록 탐색 기능이 변경되었습니다.
* 사용자가 Cloud Manager 랜딩 페이지의 프로그램 카드에서 프로그램을 편집할 수 있도록 변경되었습니다.
* 연관된 환경에 대해 새로운 파이프라인 상태 **파이프라인 실행 중**&#x200B;이 표시됩니다.
* 파이프라인 실행 페이지 이해도가 개선되었습니다. 여기에는 파이프라인 이름(비프로덕션 파이프라인만) 및 유형 표시와 파이프라인 상태가 진행 중/취소됨/실패인지를 나타내는 배지가 포함됩니다.
* 프로그램/환경 추가 버튼이 비활성화된 이유와 관련한 사용자 경험 및 이해도를 개선하기 위한 도구 설명이 추가되었습니다.
* 이제 UI 및 API를 통해 실패한 환경을 삭제할 수 있습니다.
* git 암호를 생성하는 데 사용되는 프로세스가 기본 서비스 계층의 문제에 대해보다 탄력적으로 만들어졌습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 파이프라인 실행 세부 사항 페이지의 스테이징 환경에 대한 링크가 올바른 위치로 일관되게 이동하지 않았습니다.
* 환경 생성 프로세스 내의 개별 단계가 필요한 시간보다 빨리 종료되어 프로세스가 실패합니다.
* 아티팩트 메타데이터를 다운로드할 때 교착 상태를 피하기 위해 빌드 컨테이너에 사용된 Maven 구성을 업데이트했습니다.
* 일부 경우, 이미지 작성 단계에서 고객 패키지를 제대로 다운로드하지 못했습니다.
* 드물게 발생하는 특정 조건으로 인해 환경이 삭제되지 않는 경우가 있습니다.
* Experience Cloud 알림이 일관되게 수신되지 않았습니다.
