---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: e75c957e8e791ed991117f5cd54012c3a24a2958
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 26%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.8.0)는 2023년 8월 31일입니다. 다음 기능 릴리스(2023.9.0)는 2023년 9월 28일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 8월 릴리스 개요 비디오를 통해 2023.8.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 이제 사용자는 [콘텐츠 조각 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=ko)을 사용하여 콘텐츠 조각에 메타데이터로 적용된 태그를 보고 검색할 수 있습니다. 사용자가 더 이상 이 기능을 사용하기 위해 자산 UI로 전환할 필요가 없으므로 컨텍스트 전환이 줄어들고 효율성이 향상됩니다.

  ![콘텐츠 조각 콘솔에서 태그 지정](/help/assets/content-fragments-console-tags.png)
* 이제 새로운 콘텐츠 조각 편집기를 AEM에서 as a Cloud Service으로 사용할 수 있습니다. 작성 작업을 간소화하고 컨텐츠를 편집하는 동안 서로 다른 앱 간에 전환할 필요성을 줄여 컨텐츠 작성자가 보다 생산성을 발휘할 수 있도록 합니다.
  ![새 콘텐츠 조각 편집기](/help/release-notes/assets/newCFEditor.png)

새로운 콘텐츠 조각 편집기는 원래 편집기에서 사용할 수 없는 다음과 같은 이점을 제공합니다.
* 자동 저장 기능을 통해 작성 효율성을 높이고 실수로 편집이 손실되는 것을 방지할 수 있습니다.
* 깊게 구조화된 조각 내에서 빠른 탐색을 위해 구조 트리를 사용하는 콘텐츠 조각 및 해당 참조에 대한 계층 구조 보기.
  ![콘텐츠 조각 편집기의 구조 트리](/help/release-notes/assets/newCFEditor_StructureTree.png)

* 먼저 에셋 DAM에 업로드하지 않고도 에셋을 콘텐츠 참조로 인라인 업로드
* 콘텐츠 조각에서 제공하는 렌더링된 경험의 임시 미리 보기를 통해 작성자는 프론트엔드 앱에서 콘텐츠의 디자인을 시각화할 수 있습니다
* 편집기에서 콘텐츠 조각 게시 및 게시 취소 를 1번 클릭합니다
* 콘텐츠 조각을 편집하는 동안 언어 사본 보기 및 탐색
  ![콘텐츠 조각 편집기의 언어 사본](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* 콘텐츠 조각의 타임라인을 추적하는 데 도움이 되는 버전 보기

  ![콘텐츠 조각 편집기의 버전](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* 작성자가 편집의 영향을 이해하는 데 도움이 되는 상위 참조 보기

  ![콘텐츠 조각 편집기의 상위 참조](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **데이터 소스에서 에셋 일괄 가져오기**: 이제 관리자는 [많은 수의 에셋을 가져오는 기능](/help/assets/bulk-import-assets-view.md) 데이터 소스에서 AEM Assets으로. 관리자는 더 이상 개별 자산 또는 폴더를 AEM Assets에 업로드할 필요가 없습니다. 일괄 가져오기에 지원되는 데이터 소스에는 Azure, AWS, Google Cloud 및 Dropbox가 포함됩니다.

  ![데이터 소스에서 자산 일괄 가져오기](/help/release-notes/assets/bulk-import.png)

* **Adobe Express에서 제공하는 이미지 편집 도구**: 쉽고 직관적 [Adobe Express 기반의 이미지 편집 도구](/help/assets/edit-images-assets-view.md) AEM Assets 내에서 바로 사용할 수 있으므로 콘텐츠 재사용을 높이고 콘텐츠 속도를 가속화할 수 있습니다.

  ![Adobe Express를 사용하여 이미지 편집](/help/release-notes/assets/edit-adobe-express.png)

* **내 작업 영역 바로 가기 항목을 고정하면서 유연성 유지**: 사용자, 전체 조직 또는 그룹 목록에 대해 항목을 선택하고 고정하여 [내 작업 영역의 빠른 액세스 섹션](/help/assets/my-workspace-assets-view.md) 를 참조하십시오.

  ![그룹에 맞는 항목 고정](/help/release-notes/assets/pin-items-for-groups.png)

### 관리자 보기의 새로운 기능 {#admin-view-features}

**검색 개선 사항**

* 이제 관리자는 [자산의 배치 크기 구성](/help/assets/search-assets.md#configure-asset-batch-size) 검색을 수행할 때 표시됩니다. 결과를 로드하기 위해 아래로 더 스크롤할 때 자산 검색 결과가 구성된 배치 크기 번호의 배수로 표시됩니다. 사용 가능한 배치 크기인 200개, 500개 및 1000개의 에셋 중에서 선택할 수 있습니다. 배치 크기 수를 낮게 설정하면 검색 응답 시간이 빨라집니다.

  ![자산 배치 크기 구성](/help/release-notes/assets/assets-batch-size-configuration.png)

* 이제 Experience Manager Assets에 의 새 버전 9가 포함되어 있습니다. `damAssetLucene` 색인입니다. `damAssetLucene-9` oak 쿼리 패싯 카운트의 비헤이비어를 [facet 카운트에서 더 이상 액세스 제어를 평가하지 않음](/help/assets/search-assets.md) 기본 검색 색인에 의해 반환되어 검색 응답 시간이 빨라집니다.

### [!DNL Experience Manager Assets]에서 사용할 수 있는 프리릴리스 기능 {#prerelease-features-assets}

* **Dynamic Media**: [Dynamic Media 비디오에 대한 다중 자막 및 다중 오디오 트랙 지원](/help/assets/dynamic-media/video.md#about-msma)- 이제 여러 자막과 여러 오디오 트랙을 기본 비디오에 쉽게 추가할 수 있습니다. 이 기능은 글로벌 대상자를 통해 비디오에 액세스할 수 있음을 의미합니다. 게시된 단일 기본 비디오를 여러 언어로 글로벌 대상자에게 사용자 지정하고 다양한 지리적 영역에 대한 액세스 가능성 지침을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 자막 및 오디오 트랙을 관리할 수도 있습니다.

  ![선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭&#x200B;](/help/release-notes/assets/msma-aem-cs.png)*선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭*

* **에셋**: Experience Manager에서 관리되는 ZIP 아카이브를 선택하고 [Experience Manager으로 직접 파일 추출](/help/assets/manage-digital-assets.md#extract-zip-archives) 다운로드하지 않고

  ![그룹에 맞는 항목 고정](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]에서 사용할 수 있는 프리릴리스 기능 {#pre-release-features-available-in-forms-channel}

* [**Google reCAPTCHA 엔터프라이즈 지원**](/help/forms/captcha-adaptive-forms-core-components.md): 적응형 양식에서 Google reCAPTCHA Enterprise를 사용해 사기 행위 및 스팸 방지 기능을 강화하여 보다 안전한 사용자 환경을 제공합니다. 고급 위험 분석 및 원활한 통합을 통해 실제 사용자가 양식을 쉽게 제출할 수 있는 동시에 봇이 효과적으로 차단됩니다.

* **Forms용 Experience Cloud 설정 자동화가 포함된 Adobe Analytics**: 이제 두 개의 단추를 전환하여 Experience Cloud 설정 자동화를 통해 Adobe Analytics을 활성화할 수 있습니다. 이를 통해 Experience Platform 태그 및 Adobe Analytics과 AEM Forms as a Cloud Service으로 연결하여 게시된 양식에 대한 성능 지표를 캡처하고 추적할 수 있습니다.

* **적응형 Forms용 Adobe Analytics 보고서 템플릿**: 이제 Forms as a Cloud Service에서 Adobe Analytics 보고서 OOTB를 제공합니다. 폼의 성능을 쉽게 이해할 수 있도록 해줍니다. 양식 수준 지표를 통해 표현물, 표현물, 방문자, 제출, 평균 채우기 시간과 같은 여러 KPI(주요 성능 지표)에서 양식이 어떻게 작동하는지 파악할 수 있습니다. 사용자 동작 및 피드백을 추적하여 혼동을 일으키는 양식 영역을 식별하고 양식의 디자인 및 기능 개선을 안내할 수 있습니다.

  ![적응형 양식 사용자 참여 adobe analytics 보고서](/help/forms/assets/forms-analytics-report.png)

* **[핵심 구성 요소를 기반으로 하는 적응형 Forms의 양식 단편](/help/forms/adaptive-form-fragments-core-components.md)**: 양식 조각으로 양식 구축 경험을 향상시켜 중복에 종지부를 찍고, 디지털 인벤토리를 최적화하고, 공동 작업을 개선합니다. 이러한 재사용 가능한 구성 요소는 여러 양식에 원활하게 통합되어 일관되고 전문적인 양식을 간편하게 만들 수 있습니다. 양식 조각은 &#39;한 번 변경하고 모든 곳에 반영&#39; 기능을 통해 재사용성, 표준화 및 브랜드 일관성을 보장합니다. 이러한 조각을 활용하는 모든 양식에 한 곳에서 이루어진 업데이트가 자동으로 전파되므로 유지 관리 기능과 효율성이 향상됩니다.

* **[향상된 Adobe Sign 워크플로 단계](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Adobe Sign 워크플로 단계가 다음을 포함하도록 개선되었습니다.
   * **Adobe Sign에 대한 정부 ID 기반 인증**: Adobe Acrobat Sign의 정부 ID 기반 인증은 사용자가 정부에서 발급한 ID(운전면허증, 주민등록증, 여권)를 사용하여 신원을 인증할 수 있도록 함으로써 추가적인 인증 계층을 제공합니다. 이 향상된 기능은 신뢰할 수 있는 ID 문서를 활용함으로써 서명 프로세스에 대한 신뢰도를 더욱 높여 강화된 보안, 규정 준수 및 사용자 유효성 검사가 필요한 시나리오에 이상적입니다.

   * **Adobe Sign 문서에 대한 감사 추적**: 감사 추적 기능을 사용하여 Adobe Sign 문서의 라이프사이클에 대한 자세한 통찰력을 얻을 수 있습니다. 이제 감사 추적을 사용하여 문서와 관련된 모든 작업 및 상호 작용에 대한 포괄적인 레코드를 유지 관리할 수 있습니다. 여기에는 각 이벤트에 대한 타임스탬프와 함께 문서를 보고, 편집하고, 서명한 사람 등의 세부 정보가 포함됩니다. 이러한 개선된 기능은 규정 준수 유지, 분쟁 해결 및 디지털 계약의 무결성 보장에 매우 중요합니다.

   * **서명자 이외의 계약 수신자를 위한 새로운 역할**: Adobe Acrobat Sign에는 계약 수신자의 역할을 서명자 이상으로 확장하여 워크플로 요구 사항에 보다 잘 부합하도록 하는 옵션이 있습니다. 활성화되면 계약의 각 수신자는 자신의 역할을 개별적으로 구성할 수 있으며 기본값은 서명자입니다.

* **[Document Assurance API(통신 API의 일부)를 통해 문서 Protect](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Document Assurance API를 통해 문서에 서명 및 암호화하여 중요한 정보를 보호할 수 있습니다. 암호화를 통해 문서 내용을 읽을 수 없는 형식으로 변환하여 인가된 사용자만 액세스할 수 있도록 합니다. 이 강화된 보호 레이어는 무단 시야로부터 귀중한 데이터를 보호할 뿐만 아니라 안심할 수 있습니다. 서명 API를 사용하면 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인 정보를 보호할 수 있습니다. 이 서비스는 디지털 서명 및 인증을 사용하여 의도한 수신자만 문서를 변경할 수 있도록 합니다.

* **통신 API의 페이지 수 지원**: 이제 통신 API를 통해 문서를 검색할 뿐만 아니라 문서에 포함된 페이지 수에 대한 중요한 정보도 받을 수 있습니다.

* **[규칙 편집기의 사용자 지정 오류 처리기로 오류 처리](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: 이제 외부 서비스에서 반환한 오류에 대한 응답으로 사용자 지정 함수를 호출하고 최종 사용자에게 맞춤 응답을 제공할 수 있습니다. 예를 들어 특정 오류 코드의 백엔드에서 사용자 정의 워크플로를 호출하거나 서비스가 중단되었음을 고객에게 알려 줄 수 있습니다.

* **[64비트 버전의 AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: 64비트 버전의 AEM Forms Designer는 향상된 성능, 확장성, 메모리 관리를 제공하여 양식 생성 환경을 향상시킵니다. 64비트 아키텍처를 사용하면 훨씬 더 크고 복잡한 프로젝트를 쉽게 처리할 수 있으므로 원활한 설계 워크플로와 최적화된 효율성을 보장할 수 있습니다. 이 최신 릴리스를 통해 양식 디자인 기능을 향상시키고 AEM Forms Designer의 미래를 포용할 수 있습니다.


### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[DocAssurance API(통신 API의 일부)를 사용하여 문서 Protect](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하면 문서에 서명하고 암호화하여 중요한 정보를 보호할 수 있습니다. 암호화를 통해 문서 내용을 읽을 수 없는 형식으로 변환하여 인가된 사용자만 액세스할 수 있도록 합니다. 이 강화된 보호 레이어는 무단 시야로부터 귀중한 데이터를 보호할 뿐만 아니라 안심할 수 있습니다. 서명 API를 사용하면 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인 정보를 보호할 수 있습니다. 이 서비스는 디지털 서명 및 인증을 사용하여 의도한 수신자만 문서를 변경할 수 있도록 합니다.

  <br> 공식 이메일 주소에서 다음으로 이메일을 보낼 수 있습니다. `aem-forms-early-adopter-program@adobe.com`  를 입력하여 얼리어답터 프로그램에 참여하고 기능에 대한 액세스를 요청합니다.  <br>  <br>


* **[헤드리스 적응형 Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html)**: Headless 적응형 Forms을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고 게시하고 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

   * 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
   * 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
   * 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
   * Adobe Experience Manager Forms의 기능 사용

  공식 이메일 ID에서 `aem-forms-headless@adobe.com`으로 이메일을 보내 얼리 어답터 프로그램에 참여할 수 있습니다.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN 로그 {#cdn-logs}

캐시 적중률 최적화에 유용하고 컨텐츠 전달 흐름에 대한 가시성을 높이는 Cloud Manager에서 CDN 로그를 다운로드합니다. [다음에 대해 알아보기](/help/implementing/developing/introduction/logging.md#cdn-log) cdn 로그 형식입니다. 이 기능은 9월 초에 고객에게 점진적으로 출시될 예정입니다.

### CDN 및 WAF 규칙 얼리 어답터 프로그램 {#waf-early-adopter}

다음을 기준으로 CDN에서 트래픽을 필터링할 수 있습니다.
* 요청 헤더 및 속성(예: IP 주소)
* 악성 트래픽과 관련된 것으로 알려진 트래픽 패턴

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 공식 이메일 ID로 **aemcs-waf-adopter@adobe.com**&#x200B;에 이메일을 보내 얼리 어답터 프로그램에 대해 자세히 알아보십시오. 인원이 한정되어 있습니다.

[여기](/help/security/cdn-and-waf-rules.md)에 있는 문서에서 기능에 대해 자세히 알아보십시오.


## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
