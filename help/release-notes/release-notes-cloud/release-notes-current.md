---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: a5121436b2e48302fcf14478764aede1495e089c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

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
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.12.0)는 2023년 12월 14일입니다. 다음 기능 릴리스(2024.1.0)는 2023년 1월 25일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 얼리 어답터 프로그램 {#sites-early-adopter}

**다음을 활용할 수 있습니다. [RUM(Real User Monitoring) 데이터 서비스](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** 클라이언트측 컬렉션을 AEM as a Cloud Service으로 활성화하려면

RUM(Real User Monitoring) 데이터 서비스는 사용자 상호 작용을 보다 정확하게 반영하여 웹 사이트 참여를 안정적으로 측정합니다. 페이지 성능에 대한 고급 통찰력을 얻을 수 있는 좋은 기회입니다. 이는 Adobe 관리 CDN 또는 Adobe 비관리 CDN을 사용하는 고객에게 유용합니다. 또한 비 Adobe 관리 CDN을 사용하는 고객의 경우 이제 자동화된 트래픽 보고를 사용할 수 있으므로 트래픽 보고서를 Adobe과 공유할 필요가 없습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `aemcs-rum-adopter@adobe.com`, Adobe ID과 연결된 이메일 주소에서 프로덕션, 스테이징 및 개발 환경의 도메인 이름과 함께 그런 다음 Adobe의 제품 팀이 RUM(Real User Monitoring) 데이터 서비스를 활성화합니다.


<!--

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### New Features in Admin View {#admin-view-features}



* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)


**Video Preview**: AEM Assets now generates preview renditions of all supported video formats by default, without the need to configure a processing profile.

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### 의 새로운 기능 [!DNL Experience Manager Forms] {#forms-features}

* **[Microsoft® SharePoint 목록을 사용하여 적응형 양식 연결](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms는 양식 데이터를 SharePoint 목록에 직접 제출하는 OOTB 통합을 제공하므로, SharePoint의 목록 기능을 사용할 수 있습니다. Microsoft SharePoint List를 양식 데이터 모델의 데이터 소스로 구성하고 **양식 데이터 모델을 사용하여 제출** 제출 작업을 사용하여 적응형 양식을 SharePoint 목록과 연결할 수 있습니다.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[Adobe Workfront Fusion 시나리오에 적응형 양식 제출](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service는 적응형 양식을 Adobe Workfront와 쉽게 연결할 수 있는 기본 옵션을 제공합니다. 이를 통해 적응형 양식을 Adobe Workfront 시나리오에 제출하는 프로세스가 단순화되며, 적응형 양식 제출 시 Workfront Fusion 시나리오를 트리거할 수 있습니다.

* **[오른쪽에서 왼쪽 방향 언어 지원](/help/forms/supporting-new-language-localization-core-components.md)**: 이제 핵심 구성 요소를 기반으로 구축된 적응형 양식을 아랍어, 페르시아어, 우르두어와 같은 오른쪽에서 왼쪽 방향(RTL) 언어로 표시할 수 있습니다. RTL 언어의 사용자는 전 세계적으로 20억 명이 넘습니다. RTL 언어로 된 양식을 사용하면 적응형 양식의 범위를 확장하여 더 다양성 높게 대상자를 수용하고 RTL 시장을 선택할 수 있습니다. 특정 지역에서는 현지 언어로 양식을 제공하는 것이 법적 의무이기도 합니다. 현지 언어를 수용함으로써 더 많은 대상자에게 접근할 수 있을 뿐만 아니라 관련 법률 및 규정을 준수할 수 있습니다.

  ![오른쪽에서 왼쪽 방향 언어 지원](/help/forms/assets/right-to-left-language-support.png)

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-early-adopter-program@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN 구성 얼리 어답터 프로그램 {#cdn-config-early-adopter}

최근에 릴리스된 외에도 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md)선택적 라이센스 가능한 WAF(Web Application Firewall) 규칙이 포함된 를 사용하면 구성 파이프라인을 사용하여 다른 유형의 CDN 구성을 선언하고 배포할 수 있습니다. 다음을 포함한 사용 사례에 대해 의견을 들려 주시기 바랍니다.
* 301/302 클라이언트측 리디렉션
* 에지의 요청을 임의의 출처로 프록시 처리
* URL 변환
* 요청 또는 응답 헤더 설정 또는 수정
* CDN이 AEM에 연결할 수 없는 경우의 사용자 정의 오류 페이지
* 사용자 이름/암호로 인증
* 기타 유용한 CDN 구성

공식 이메일 ID에서 **aemcs-cdn-config-adopter@adobe.com**&#x200B;으로 이메일을 보내 피드백을 알려 주십시오.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
