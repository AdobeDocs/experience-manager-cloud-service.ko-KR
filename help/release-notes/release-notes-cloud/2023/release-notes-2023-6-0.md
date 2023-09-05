---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.6.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.6.0 릴리스 정보입니다.'
source-git-commit: 7d09cafc4f8518fee185d3f9efc76c33ec20f9a3
workflow-type: ht
source-wordcount: '1409'
ht-degree: 100%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 2023.6.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.6.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.6.0)의 릴리스 일자는 2023년 6월 29일입니다. 다음 기능 릴리스(2023.7.0)는 2023년 7월 27일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 6월 릴리스 개요 비디오를 통해 2023.6.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 이제 [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console)을 사용하여 콘텐츠 조각 및 해당 참조를 [AEM 미리보기 서비스](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)에 게시하게 되면 사용자는 시작하기 전에 분리된 미리보기 애플리케이션을 통해 최종 경험을 미리 볼 수 있습니다.

![콘텐츠 조각 콘솔에서 미리보기](/help/assets/content-fragments-console-preview.png)

* 이제 AEM GraphQL을 사용하여 Headless 시나리오에서 웹 게재를 위해 이미지를 동적으로 최적화할 수 있습니다. GraphQL 쿼리에서 [쿼리 변수](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=ko#query-variables)를 정의하여 분리된 클라이언트 애플리케이션으로 AEM에서 최적화된 이미지를 요청할 수 있습니다.
* 이제 [콘텐츠 조각 변형](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=ko)에 있는 태그를 AEM GraphQL 콘텐츠 게재 API를 사용하여 JSON으로 출력할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

**새 Assets 보기의 가용성**

이제 Experience Manager Assets에서 [새 Assets 보기](/help/assets/assets-view-introduction.md)를 사용할 수 있습니다. Assets 보기는 간소화된 사용자 인터페이스를 통해 디지털 자산을 쉽게 관리, 검색 및 배포할 수 있습니다. 이 경험은 크리에이티브, 읽기 전용 자산 소비자 및 더 가벼운 DAM 사용자를 대상으로 합니다.

![태그 지정 관리](/help/assets/assets/my-workspace.png)

**검색 경험 개선 사항**

이제 Experience Manager Assets를 통해 검색 결과 사용자 인터페이스에서 다음과 같은 더 많은 작업을 수행할 수 있습니다.

* [전체 저장소에서 키워드를 검색하는 대신 기본적으로 현재 저장소 위치 내에서 검색을 수행합니다.](/help/assets/search-assets.md)

* [검색 결과에 표시되는 자산의 폴더 위치로 이동합니다.](/help/assets/search-assets.md#aftersearch)

**3D 자산의 썸네일 미리보기**

[!DNL Experience Manager Assets]는 이제 gLB, USDz, FBX, 3DS, OBJ, SBSAR을 포함한 [일반적인 3D 파일 형식에 대한 썸네일 미리보기](/help/assets/file-format-support.md)를 생성합니다. 해당 파일을 업로드하면 기본적으로 썸네일이 자동 생성됩니다.

**링크 공유 구성**

관리자가 사용자를 위해 이 기능의 기본 동작을 사용자 정의할 수 있는 새로운 구성 집합과 함께 [링크 공유를 만드는](/help/assets/share-assets.md) 향상된 새로운 사용자 환경입니다.

![태그 지정 관리](/help/assets/assets/config-email-service.png)

**Dynamic Media: 이미지 프로필의 업데이트된 스마트 자르기 관련된 필드**

이미지 프로필의 일부 스마트 자르기 관련 필드에 대한 사용자 인터페이스가 이제 스마트 자르기를 정의하기 위한 현재 지침을 반영하도록 업데이트되었습니다. [자르기 옵션](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=ko#crop-options)을 참조하십시오.

### Assets 보기의 새로운 기능 {#assets-view-features}

**빠른 검색 경험을 위한 자산의 계층적 태그 지정**

제어된 어휘의 단순 목록은 시간이 지남에 따라 관리하기 까다로워집니다. 이제 Assets 보기는 관련 메타데이터의 적용, 자산 분류, 검색 지원, 태그 재사용, 검색 기능 개선 등을 용이하게 하는 [계층적 태그 지정 구조](/help/assets/tagging-management-assets-view.md)를 지원합니다.

![태그 지정 관리](/help/assets/assets/tags-hierarchy.png)

**빠른 액세스를 위해 파일, 폴더 및 컬렉션 고정**

이제 나중에 필요할 때 [파일, 폴더 및 컬렉션에 더 빠르게 액세스할 수 있도록 이러한 항목을 고정](/help/assets/my-workspace-assets-view.md)할 수 있습니다. 고정된 항목은 내 작업 영역의 **빠른 액세스** 섹션에 표시됩니다. 저장소 내에서 저장된 위치로 이동하는 대신 내 작업 영역을 사용하여 액세스할 수 있습니다.

![작업 영역의 작업](/help/assets/assets/quick-access.png)

**휴지통 폴더의 자산 필터링**

Assets 보기에서는 이제 [휴지통 폴더에서 자산을 필터링](/help/assets/navigate-assets-view.md)할 수 있습니다. 표준 또는 사용자 정의 필터를 적용하여 휴지통 폴더 내에서 적절한 자산을 검색해 복원하거나 영구적으로 삭제할 수 있습니다.

**3D 자산의 썸네일 미리보기**

Assets 보기는 이제 gLB, USDz, FBX, 3DS, OBJ, SBSAR을 포함한 일반적인 3D 파일 형식에 대한 썸네일 미리보기를 생성합니다. 이러한 파일이 Assets 보기에 업로드되면 기본적으로 썸네일이 시스템에서 자동으로 생성됩니다.

![작업 영역의 작업](/help/assets/assets/3d-preview.png)

**가장 많이 검색된 용어 보기**

Assets 보기는 이제 내 작업 영역의 **인사이트** 섹션을 사용하여 [배포 내에서 가장 많이 검색된 용어 보기](/help/assets/my-workspace-assets-view.md)를 지원합니다. 세부 인사이트로 이동하여 지난 30일 또는 12개월 동안의 인기 검색어를 볼 수도 있습니다.

![작업 영역의 작업](/help/assets/assets/insights-top-searches.png)

**메타데이터 양식 개선 사항**

Assets 보기에서는 이제 [다중 값 텍스트 및 드롭다운 목록 속성 구성 요소](/help/assets/metadata-assets-view.md#property-components)를 메타데이터 양식에 추가할 수 있습니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* [AEM 페이지 편집기 내 적응형 양식](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): 이제 AEM 페이지 편집기를 사용하여 여러 양식을 빠르게 만들고 사이트 페이지에 추가할 수 있습니다. 이 기능을 통해 콘텐츠 작성자는 동적 비헤이비어, 유효성 검사, 데이터 통합, 기록 문서 생성 및 비즈니스 프로세스 자동화 등 적응형 양식 구성 요소의 기능을 사용하여 Sites 페이지에서 원활한 데이터 캡처 경험을 만들 수 있습니다. 다음과 같은 작업을 수행할 수 있습니다.

   * AEM Sites 편집기 또는 경험 조각에서 양식 구성 요소를 적응형 양식 컨테이너 구성 요소로 드래그 앤 드롭하여 적응형 양식을 만듭니다.
   * AEM Sites 편집기 내에서 적응형 양식 마법사를 사용하여 Sites 페이지와는 별개로 양식을 만들게 되면 여러 페이지에서 해당 양식을 자유롭게 재사용할 수 있습니다.
   * Sites 페이지에 여러 양식을 추가하여 사용자 경험을 간소화하고 더 많은 유연성을 제공합니다.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [공공기관용 Adobe Acrobat Sign Solutions](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms는 공공기관용 Adobe Acrobat Sign Solutions와 통합합니다. 이 통합은 공공기관 관련 계정(정부 부서 및 기관)에 대한 적응형 양식 제출과 함께 전자 서명의 고급 규정 준수 및 보안을 제공합니다.

  공공기관용 Adobe Acrobat Sign Solutions와 통합하여 Adobe의 파트너와 공공기관 고객들은 가장 중요하고 민감한 비즈니스 라인에서 적응형 양식 전자 서명을 사용할 수 있습니다. 이 보안 계층이 추가되면 Adobe의 공공기관 고객들이 안심할 수 있도록 모든 전자 서명은 FedRAMP Moderate 규정을 완전히 준수해야 합니다.

* [규칙 편집기의 사용자 정의 오류 핸들러로 오류 처리 개선](/help/forms/add-custom-error-handler-adaptive-forms.md): 이제 외부 서비스에서 반환되는 오류에 따라 사용자 정의 함수(클라이언트 라이브러리 사용)를 호출하여 맞춤형 응답을 최종 사용자에게 제공할 수 있습니다. 서비스에서 반환된 오류에 대해 특정 작업을 수행할 수도 있습니다. 예를 들어 특정 오류 코드의 백엔드에서 사용자 정의 워크플로를 호출하거나 서비스가 중단되었음을 고객에게 알려 줄 수 있습니다.

  이 기능을 통해 OOTB 오류 핸들러와 역으로 호환되는 표준 기반 오류 응답을 도입하여 보다 높은 유연성과 제어 기능을 제공함으로써 전체 오류 처리 기능을 개선할 수 있습니다.

* [양식 데이터 모델에 대한 향상된 인증 방법](/help/forms/configure-data-sources.md): AEM Forms를 호환되는 데이터 소스와 연결하기 위한 클라이언트 자격 증명 기반 인증을 도입하여 보안 경험을 강화합니다. 이 향상된 기능을 통해 가장 또는 사용자 로그인을 사용하지 않고도 데이터 보호 기능을 강화합니다.

* [반복 가능한 섹션으로 적응형 양식 만들기](/help/forms/create-forms-repeatable-sections.md): 이제 적응형 양식 기반 핵심 구성 요소에서 [아코디언](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [마법사](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [패널](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html) 및 [가로 탭](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) 구성 요소를 만들어 반복 가능한 섹션을 만들 수 있습니다.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  반복 가능한 이런 섹션을 사용하면 고정된 필드 수 없이 무제한의 항목을 제공할 수 있습니다. 필요한 데이터 인스턴스를 미리 알 수 없는 경우에 유용합니다. Forms 사용자는 섹션을 쉽게 추가하거나 제거할 수 있으므로, 양식을 다양한 데이터 입력 시나리오에 맞게 조정하고 동일한 데이터의 여러 항목 수집을 단순화할 수 있습니다.

* **[적응형 양식을 Microsoft® SharePoint 및 Microsoft® OneDrive에 제출](/help/forms/configuring-submit-actions.md)**: 비즈니스 사용자 민첩성을 개선하여 새로운 양식을 빠르게 시작하고, Microsoft® SharePoint 사이트 또는 OneDrive 폴더와 같이 일상적으로 사용하는 도구에 제출된 데이터를 저장합니다.

### Headless 적응형 양식 얼리 어답터 프로그램 {#forms-early-adopter}

[Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

* 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
* 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 기능 사용

공식 이메일 ID에서 `aem-forms-headless@adobe.com`으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
