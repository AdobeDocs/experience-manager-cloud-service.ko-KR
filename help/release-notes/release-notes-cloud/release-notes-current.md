---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 23%

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

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.11.0)는 2023년 11월 30일입니다. 다음 기능 릴리스(2023.12.0)는 2023년 12월 14일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2023년 11월 릴리스 개요 비디오를 통해 2023.11.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 얼리 어답터 프로그램 {#sites-early-adopter}

**[콘텐츠 조각에서 문자열 찾기 및 바꾸기](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: 콘텐츠 조각 콘솔 은 사용자가 여러 콘텐츠 조각에 표시되는 문자열을 한 번에 쉽고 직관적으로 대체할 수 있는 방법을 제공하여 콘텐츠 속도를 가속화합니다.

![찾기 및 바꾸기](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

기능을 사용해 보고 피드백을 공유하고 싶으십니까? 다음으로 이메일 보내기 **aemcs-headless-adopter@adobe.com** 얼리어답터 프로그램에 대한 자세한 내용은 공식 이메일 ID에서 확인하십시오.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Assets 보기의 새로운 기능 {#assets-view-features}

* **AEM Assets에 임베드된 Adobe Express 편집기**: 이제 Express에 액세스할 수 있는 사용자가 AEM Assets 내에서 직접 Adobe Express 및 Adobe Firefly의 통합 이미지 편집 및 제작 도구를 사용하여 콘텐츠를 재사용할 수 있고 콘텐츠 속도를 높일 수 있습니다.

  ![폴더에 메타데이터 양식 할당](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Insights의 저장소 사용 보고서**: 이제 관리자는 Insights의 일부로 사용할 수 있는 스토리지 사용량 보고서를 볼 수 있습니다.

  ![스토리지 사용 인사이트](/help/assets/assets/storage-usage-insights.png)

* **첫 번째 홈 페이지 구성 검색**: 이제 Experience Manager Assets을 사용하여 조직에 대한 홈 페이지 경험을 구성할 수 있습니다. 홈 페이지로 먼저 검색을 선택하는 경우 조직의 검색 창 정렬, 배경 이미지 및 로고를 구성할 수 있습니다.

  ![첫 번째 구성 검색](/help/assets/assets/search-first-configuration.png)

### 관리자 보기 프리릴리스의 새로운 기능 {#admin-view-features-prerelease}

**비디오 미리 보기**: 이제 AEM Assets은 처리 프로필을 구성할 필요 없이 기본적으로 지원되는 모든 비디오 형식의 미리 보기 렌디션을 생성합니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Experience Manager Forms]의 새로운 기능 {#forms-features}

* **[확인란 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: 이제 핵심 구성 요소 기반의 적응형 Forms에 확인란 구성 요소를 포함할 수 있습니다. 이를 통해 사용자는 특정 옵션을 선택하거나 선택 취소하는 바이너리 선택을 할 수 있습니다. 일반적으로 이 상자는 클릭하거나 탭하여 선택 및 선택 취소의 두 상태 간에 전환할 수 있는 작은 상자로 표시됩니다. 확인란은 예/아니요 또는 true/false 선택을 표시하는 데 사용되는 일반적인 양식 요소입니다.

* **[사용 약관 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: 이제 핵심 구성 요소 기반의 적응형 Forms에 약관 구성 요소가 포함될 수 있습니다. 양식 작성자는 양식 내에서 서비스, 제품 또는 플랫폼 사용과 관련된 약관, 조건 또는 법적 계약서를 사용자에게 제시하는 특정 섹션을 도입할 수 있습니다. 이 구성 요소는 양식을 제출하여 사용자가 동의하는 규칙, 규정 및 의무에 대해 알리도록 설계되었습니다.

  ![확인란, 약관 및 세로 탭 구성 요소](/help/forms/assets/forms-components.png)

* **[세로 탭 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: 이제 핵심 구성 요소를 기반으로 하는 적응형 Forms에서 양식 콘텐츠를 세로 탭 목록으로 구성하여 구조화되고 탐색 가능한 레이아웃을 제공할 수 있습니다. 양식에 수직 탭을 사용하면 특히 양식에 여러 섹션이나 복잡한 정보가 포함된 경우 탐색을 단순화하고 양식 콘텐츠 구성을 개선하여 전반적인 사용자 경험을 향상시킬 수 있습니다.



### [!DNL Forms] 프리릴리스의 새로운 기능 {#prerelease-features-forms}

* **[Microsoft® SharePoint 목록과 적응형 Forms 연결](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms은 SharePoint의 목록 기능을 사용할 수 있도록 양식 데이터를 SharePoint 목록에 직접 제출할 수 있는 OOTB 통합을 제공합니다. Microsoft SharePoint 목록을 양식 데이터 모델에 대한 데이터 소스로 구성하고 **양식 데이터 모델을 사용하여 제출** 제출 액션을 사용하여 적응형 양식을 SharePoint 목록과 연결합니다.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[Adobe Workfront Fusion 시나리오에 적응형 양식 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service에서는 적응형 양식을 Adobe Workfront에 쉽게 연결할 수 있는 획기적인 옵션을 제공합니다. 이렇게 하면 적응형 양식을 Adobe Workfront 시나리오에 제출하는 프로세스가 간소화되므로 적응형 양식 제출 시 Workfront Fusion 시나리오를 트리거할 수 있습니다.

* **[오른쪽에서 왼쪽 언어 지원](/help/forms/supporting-new-language-localization-core-components.md)**: 핵심 구성 요소에 빌드된 적응형 Forms은 이제 아랍어, 페르시아어 및 우르두와 같은 오른쪽에서 왼쪽 쓰기(RTL) 언어로 제공될 수 있습니다. RTL 언어는 전 세계 20억 명 이상의 사람들이 사용하고 있습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 다양한 대상자를 만족시키고 RTL 시장에 진출할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것도 법적 의무입니다. 현지 언어를 수용함으로써, 광범위한 대상자에게 문호를 개방할 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

  ![오른쪽에서 왼쪽 언어 지원](/help/forms/assets/right-to-left-language-support.png)

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-early-adopter-program@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 이제 WAF 트래픽 필터 규칙에 라이선스를 제공할 수 있습니다. {#cdn-waf-license}

트래픽 필터 규칙은 10월에 릴리스되었으며, 사이트 및 Forms 고객이 이미 사용할 수 있는 규칙을 보완하기 위해 올해 말에 WAF(Web Application Firewall) 규칙의 특수 카테고리를 사용할 수 있다는 참고 사항이 포함되어 있습니다. 업데이트로, 이제 WAF-DDoS Protection 제품에 라이센스를 부여할 수 있습니다.

라이센스가 부여되면 Cloud Manager 구성 파이프라인을 사용하여 CDN에 이러한 고급 WAF 규칙을 배포하여 웹 공격으로부터 추가 보호 계층을 추가할 수 있습니다.

읽어보기 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md), WAF 포함. WAF-DDoS Protection 또는 Enhanced Security 라이선싱에 대한 자세한 내용은 AEM 계정 팀에 문의하십시오.

### CDN 구성 얼리 어답터 프로그램 {#cdn-config-early-adopter}

최근에 릴리스된 외에도 [트래픽 필터 규칙(WAF 포함)](/help/security/traffic-filter-rules-including-waf.md)를 통해 구성 파이프라인을 사용하여 다른 유형의 CDN 구성을 선언하고 배포할 수 있습니다. 다음을 포함한 사용 사례에 대해 알고 싶습니다.
* 301/302 클라이언트측 리디렉션
* 에지의 요청을 임의 출처로 프록시 설정
* URL 변형
* 요청 또는 응답 헤더 설정 또는 수정
* cdn이 AEM에 연결할 수 없을 때의 사용자 지정 오류 페이지
* 사용자 이름/암호로 인증
* 기타 유용한 CDN 구성

다음으로 이메일 보내기 **aemcs-cdn-config-adopter@adobe.com** (피드백이 포함된 공식 이메일 ID).

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.

## 알려진 문제 {#known-issues}

* 핵심 구성 요소를 기반으로 하는 적응형 Forms을 제출할 수 없습니다. 이 문제는 핵심 구성 요소 버전 2.0.38 - 2.0.60을 사용하여 빌드된 적응형 Forms에 대해 발생합니다.

  문제를 해결했습니다. 적응형 양식 핵심 구성 요소 버전 2.0.62 이상으로 이동할 수 있습니다. 환경에 맞는 적응형 Forms 핵심 구성 요소 버전을 설정하려면 다음을 수행하십시오. [core.forms.components.version, core.forms.components.af.version 및 core.wcm.components.version 구성 요소의 버전을 설정합니다.](/help/forms/enable-adaptive-forms-core-components.md#2-add-adaptive-forms-core-components-dependencies-to-your-git-repository) Forms as a Cloud Service 저장소 또는 AEM Archetype 기반 프로젝트의 종속성 및 [Forms as a Cloud Service 환경에 변경 사항 배포](/help/forms/enable-adaptive-forms-core-components.md#build-and-deploy-updated-code-on-an-aem-forms-as-a-cloud-service-environment). 다음 위치에서 최신 버전의 적응형 Forms 핵심 구성 요소 종속성을 찾을 수 있습니다. [적응형 Forms 핵심 구성 요소 Git 저장소](https://github.com/adobe/aem-core-forms-components#system-requirements).
