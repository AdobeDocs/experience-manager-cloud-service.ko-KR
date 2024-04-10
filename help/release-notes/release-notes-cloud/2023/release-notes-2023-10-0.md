---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.10.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2023.10.0 릴리스 정보입니다.'
exl-id: 81a6cbd2-7101-429b-8572-2650c5bea963
source-git-commit: 559b4afa975dcd2204cd06c95f19ed38da00033e
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 91%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2023.10.0 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 2023.10.0 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021년 또는 2022년과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.10.0)의 릴리스 일자는 2023년 10월 26일입니다. 다음 기능 릴리스(2023.11.0)는 2023년 11월 30일에 예정되어 있습니다.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## 릴리스 비디오 {#release-video}

2023년 10월 릴리스 개요 비디오를 통해 2023.10.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### 새로운 기능 {#assets-features}

**Adobe Express을 위한 AEM Assets 추가 기능**: 이제 Experience Manager Assets에서 Adobe Express을 위한 추가 기능을 제공합니다. 이 추가 기능을 사용하여 Adobe Express 사용자 인터페이스 내에서 Experience Manager Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다. 추가 기능은 다음과 같은 주요 이점을 제공합니다.

* AEM의 새 자산을 편집 및 저장하여 콘텐츠 재사용이 늘어남

* 새로운 자산 또는 새로운 버전의 기존 자산을 만드는 데 소요되는 전반적인 시간과 노력이 단축됨

  ![Assets 추가 기능에서 자산 포함](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Assets 보기의 새로운 기능 {#assets-view-features}

* **OneDrive 데이터 원본에서 자산 일괄 가져오기**: 관리자는 이제 다음 작업을 수행할 수 있습니다 [OneDrive에서 AEM Assets으로 많은 자산 가져오기](/help/assets/bulk-import-assets-view.md#onedrive-developer-application). 일괄 가져오기가 지원되는 데이터 소스의 업데이트된 목록에는 Azure, AWS, Google Cloud, Dropbox 및 OneDrive가 포함됩니다.

  ![폴더에 메타데이터 양식 할당](/help/assets/assets/bulk-import-source-details-onedrive.png)

* **라이브러리에 대한 교차 조직 권한 부여 지원**: 이제 Experience Manager Assets을 사용하여 다른 IMS 조직의 Creative Cloud 라이브러리에 대한 액세스를 구성할 수 있습니다. Creative Cloud와 Experience Manager 간의 최신 제품 간 워크플로에 더 쉽게 액세스할 수 있으며 크리에이티브에 소요되는 시간과 노력이 줄어듭니다.

### [!DNL Experience Manager Assets]에서 사용할 수 있는 프리릴리스 기능 {#prerelease-features-assets}

* **Dynamic Media**: [Dynamic Media로 비디오의 다중 자막 및 다중 오디오 트랙 지원](/help/assets/dynamic-media/video.md#about-msma) —이제 기본 비디오에 여러 개의 자막과 오디오 트랙을 손쉽게 추가할 수 있습니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 자막 및 오디오 트랙을 관리할 수도 있습니다.

  ![선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭입니다.](/help/release-notes/assets/msma-aem-cs.png)*선택한 비디오 자산의 속성 페이지에 있는 자막 및 오디오 트랙 탭입니다.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Experience Manager Forms]의 새로운 기능 {#forms-features}

* **[적응형 양식의 사용자 정의 속성](/help/forms/template-editor-core-components.md#add-a-custom-group-name-in-the-policy-of-template-editor)**: 사용자 정의 속성(키-값 쌍)을 양식 템플릿 또는 적응형 양식 구성 요소와 연결하여 양식 개발자가 사용자 정의 속성의 값에 따라 적응하는 동적 양식 동작을 제공하도록 지원할 수 있습니다. 예를 들어 개발자가 사용자 정의 속성 값을 기반으로 모바일, 데스크탑 또는 웹 플랫폼에서 Headless Forms 구성 요소의 다양한 렌디션을 제작할 수 있어, 다양한 장치의 사용자 경험을 크게 개선할 수 있습니다.

* **테마 및 템플릿**: 바로 사용할 수 있으며 노련한 전문가와 초보 양식 작성자 모두의 역량을 강화하도록 맞춤화된 새로운 테마 및 템플릿으로 양식 작성 프로세스를 시작하십시오. 적응형 양식 핵심 구성 요소를 사용하여 원활하게 구축되었으며 세심하게 선별된 이 테마 및 템플릿을 사용하면 일반적인 사용 사례에 대한 양식을 신속하게 작성할 수 있습니다.

  ![기본 제공 템플릿](/help/forms/assets/form-templates-ootb.png)


### 얼리 어답터 프로그램 {#forms-early-adopter}

* **[DocAssurance API(Communication API의 일부)로 문서 보호](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: DocAssurance API를 사용하여 문서에 서명하고 암호화하여 민감한 정보를 보호할 수 있습니다. 문서의 콘텐츠는 암호화를 통해 읽을 수 없는 포맷으로 변환되어 권한이 있는 사용자만 액세스할 수 있습니다. 이 보호 계층이 강화되면 중요 데이터를 승인되지 않은 사용자로부터 보호할 뿐만 아니라 고객들이 안심할 수 있습니다. 서명 API를 통해 조직에서 배포하고 수신하는 Adobe PDF 문서의 보안 및 개인정보를 보호할 수 있습니다. 이 서비스는 의도한 수신자만 문서를 변경할 수 있도록 디지털 서명과 인증을 사용합니다.

  공식 이메일 ID에서 “`aem-forms-ea@adobe.com`”으로 이메일을 보내 얼리 어답터 프로그램에 참여하여 기능에 대한 액세스 권한을 요청할 수 있습니다.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### WAF가 포함된 트래픽 필터 규칙 {#traffic-filter-rules-waf}

URL, IP 주소 및 사용자 에이전트 등의 속성별로 웹 사이트 트래픽과 일치하는 규칙을 선언하여 [Adobe Managed CDN에서 트래픽을 필터링하거나](/help/security/traffic-filter-rules-including-waf.md) DoS 공격으로부터 보호하기 위해 사용자 정의 트래픽 속도 제한을 설정합니다. 또한 고객이 정교한 웹 사이트 위협을 대비하는 추가적인 보호를 위해 고급 WAF(웹 애플리케이션 방화벽) 규칙 세트에 라이선스를 부여할 수도 있습니다.

다음을 통해 트래픽 필터 규칙을 숙지할 것을 권장합니다. [튜토리얼 시험 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html)! 새로운 Cloud Manager 구성 파이프라인을 설정하고, 구성 파일에 규칙을 선언하고, 악성 트래픽에 대한 CDN 로그를 분석하는 과정을 이해할 수 있습니다.

트래픽 필터 규칙은 이제 개발 환경에서 이용할 수 있으며, 11월에는 스테이지 및 프로덕션 환경에 점진적으로 롤아웃됩니다. **aemcs-waf-adopter@adobe.com**&#x200B;으로 이메일을 보내어 스테이지 및 프로덕션에 대한 조기 액세스를 요청할 수 있습니다.

고급 WAF 트래픽 필터 규칙은 향상된 보안 또는 WAF-DDoS 보호 제품을 통해 올해 말에 사용이 허가될 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
