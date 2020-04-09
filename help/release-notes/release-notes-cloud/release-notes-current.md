---
title: 2020.4.0용 클라우드 서비스 릴리스 노트로 Adobe Experience Manager
description: 2020.4.0용 Adobe Experience Manager 릴리스 노트
translation-type: tm+mt
source-git-commit: 2258cc72d10fa85d89832b63016ccb393f453bff

---


# Release Notes for Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

The following section outlines the general release notes for [!DNL Experience Manager] as a Cloud Service 2020.4.0.

## Release Date {#release-date}

클라우드 서비스 2020.4.0 [!DNL Experience Manager] 의 릴리스 날짜는 2020년 4월 9일입니다.

## 자산의 새로운 기능 {#assets}

현재 릴리스와 관련된 새로운 기능, 개선 사항 및 버그 수정에 대해 [!DNL Experience Manager Assets] 알아보십시오 [!DNL Dynamic Media] .

* [브랜드](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) 포털은 Experience Manager 자산에 대한 자산 배포 사용 사례를 지원합니다. [!DNL Brand Portal] 승인된 브랜드 및 제품 자산을 외부 에이전시, 파트너, 내부 팀 및 리셀러에 안전하게 배포하여 조직의 마케팅 요구 사항을 충족할 수 있도록 지원합니다.
   * [!DNL Brand Portal] 구성은 [!DNL Adobe I/O] 콘솔을 통해 완료됩니다.
   * 의 자산 소싱은 아직 클라우드 서비스로 지원되지 [!DNL Brand Portal] 않습니다 [!DNL Experience Manager] .

* [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) v2.0은 클라우드 [!DNL Experience Manager] 서비스로 작동합니다. [!DNL Adobe Asset Link] 데스크탑 앱 [!DNL Experience Manager Assets] 및 인앱 [!DNL Creative Cloud] [!DNL Adobe Photoshop][!DNL Adobe Illustrator][!DNL Adobe InDesign] [!DNL Asset Link] 패널을 통해 콘텐츠 제작 프로세스를 통해 크리에이티브와 마케터 간의 협업을 간소화할 수 있습니다.
   * [!DNL Experience Manager] 에 대해 사전 구성된 [!DNL Adobe Asset Link]경우 [손쉽게 구성할](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) 수 있고 크리에이티브 전문가에게 보다 신속하게 롤아웃할 수 있습니다.
   * [!DNL Asset Link] 이제 크리에이티브 [사용자가 다른](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) [!DNL Experience Manager] 환경에 손쉽게 연결할 수 있는 Experience Manager 환경 전환기를 지원합니다. 이 기능이 유용한 예로, 서로 다른 [!DNL Experience Manager Assets] 배포를 사용하여 여러 클라이언트와 함께 작업하는 에이전시 디자이너가 여기에 포함됩니다.

* 사용자는 특정 폴더 계층 구조에 대해 폴더 속성 [사용자 인터페이스에서 자동으로 시작하도록](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows)  사후 처리 워크플로우를 구성할 수 있습니다.
   * 폴더 [!UICONTROL 속성] 사용자 인터페이스는 메타데이터 프로필, 처리 [!UICONTROL 프로필] 및 새로운 자동 시작 워크플로우 구성이 포함된 새로운 자산 처리 탭으로 간소화됩니다.
   * 자산 재처리 대화 상자에서는 특정 처리 프로필을 선택하고 하위 폴더에서 다시 처리할 수 있습니다.
   * [!DNL Dynamic Media]:안전한 미리 보기용으로 에셋이 자동 게시되도록 선택적 게시 구성을 추가했습니다. 또한 공개 도메인에 제공하기 위해 DMS7에 게시하지 않고도 Experience Manager에 자산을 명시적으로 게시할 수 있습니다.

### 버그 수정 {#assets-bug-fixes}

* 자산 처리 문제에 대한 수정 사항.
* 구성 및 자산 게시가 [!DNL Dynamic Media] [!DNL Dynamic Media] 배달 서비스에 수정되었습니다.

>[!MORELIKETHIS]
>
>* [Adobe Asset 링크 정보](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [브랜드 포털 구성](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Experience Manager가 자산 링크와 연동되도록 구성](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Adobe Experience Manager에서 자산 마이크로 서비스를 사용하여 워크플로우 제작](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)


## Cloud Manager의 새로운 기능 {#whats-new-cloud-manager}

* 이제 Cloud Manager UI의 환경 페이지에서 게시자 URL을 사용할 수 있습니다.
* 사용자가 Cloud Manager 개요 페이지에서 프로그램을 편집, 전환 또는 추가할 수 있도록 탐색이 변경되었습니다.
* 사용자가 Cloud Manager 랜딩 페이지의 프로그램 카드에서 프로그램을 편집할 수 있도록 하는 변경 사항입니다.
* 새 파이프라인 상태 **파이프라인** 실행 중 연결된 환경에 대해 표시됩니다.
* 파이프라인 실행 페이지 이해 기능이 개선되었습니다. 여기에는 파이프라인 이름(비프로덕션 파이프라인 전용) 및 유형, 파이프라인 상태가 진행 중/취소됨/실패인지 여부를 나타내는 배지가 포함됩니다.
* 프로그램/환경 추가 단추가 비활성화된 이유에 대한 사용자 경험과 이해를 돕기 위한 도구 팁입니다.
* 이제 UI 및 API를 통해 실패한 환경을 삭제할 수 있습니다.
* Git 암호를 생성하는 데 사용되는 프로세스는 기본 서비스 레이어의 문제에 보다 탄력적으로 적용됩니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 파이프라인 실행 세부 정보 페이지의 스테이지 환경에 대한 링크가 올바른 위치로 일관되게 이동하지 않았습니다.
* 환경 생성 프로세스 내의 개별 단계가 필요 이상으로 빨리 시간 초과되어 프로세스가 실패합니다.
* 빌드 컨테이너에 사용된 Maven 구성이 아티팩트 메타데이터를 다운로드할 때 교착 상태를 방지하기 위해 업데이트되었습니다.
* 경우에 따라 이미지 작성 단계가 고객 패키지를 다운로드하지 못할 수 있습니다.
* 특정 자주 발생하는 조건은 환경을 삭제하지 못하게 합니다.
* Experience Cloud 알림을 일관되게 받지 못했습니다.
