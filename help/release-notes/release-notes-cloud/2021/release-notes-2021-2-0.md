---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.2.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2021.2.0용 as a Cloud Service 릴리스 노트"
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 34%

---


# [!DNL Adobe Experience Manager]as a Cloud Service 릴리스 정보 {#release-notes}

다음 섹션에서는 의 일반 릴리스 정보에 대해 간략히 소개합니다. [!DNL Experience Manager] as a Cloud Service.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0은 2021년 2월 25일입니다.
다음 릴리스(2021.3.0) 날짜는 2021년 3월 25일입니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### 헤드리스 콘텐츠 관리 {#headless}

* **[컨텐츠 조각 전달을 위한 GraphQL API](/help/headless/graphql-api/content-fragments.md)**: JSON 형식의 출력을 위해 GraphQL 구문 및 콘텐츠 조각 모델을 기반으로 하는 스키마를 사용하여 콘텐츠 조각을 쿼리하는 기능입니다.

* **[GraphQL API 요청에 대한 인증 지원](/help/headless/security/authentication.md)**: 서버측 API에 대한 액세스 토큰을 사용하여 GraphQL API 요청을 인증하는 기능입니다.

* **[RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)**: AEM 내에서 외부 SPA을 보고 편집할 수 있는 지원이 추가되었습니다.

* **[AEM 내에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)**: 독립 실행형 단일 페이지 애플리케이션을 AEM 인스턴스에 업로드하고, 편집 가능한 콘텐츠 섹션을 추가하고, 저작을 활성화할 수 있는 기능이 추가되었습니다.

* 리치 텍스트를 JSON 형식 및 로케일로 출력하는 기능을 포함하여 GraphQL API의 JSON 출력이 향상되었습니다.

* 전용 콘텐츠 조각 참조 데이터 유형 또는 여러 줄 텍스트 필드에 인라인으로 콘텐츠 조각 참조를 통해 중첩된 콘텐츠 조각 구조를 만들 수 있도록 콘텐츠 조각 모델을 중첩하는 기능을 지원합니다.

* &quot;고유&quot;, &quot;필수&quot; 및 &quot;변환 가능&quot;을 포함하여 콘텐츠 조각 모델 데이터 유형에서 사용할 수 있는 추가 유효성 검사 규칙입니다.

* 콘텐츠 조각 모델에 태그를 지정하고 태그 또는 경로별 정책이 있는 폴더에서 콘텐츠 조각을 만들 수 있습니다.

* 조각이 기반으로 하는 모델의 게시 작업 및 표시를 포함하여 콘텐츠 조각 편집기의 사용성이 개선되었습니다.

* 콘텐츠 조각 편집기에서 직접 JSON 출력을 미리 볼 수 있습니다.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 에셋은 다음을 사용하여 소싱 할 수 있습니다. [!DNL Experience Manager Assets Brand Portal]. 새로운 마케팅 캠페인, 사진 촬영 및 프로젝트를 위해 에이전시 사용자로부터 에셋을 소싱하는 데 도움이 됩니다.

* [!DNL Experience Manager Assets] as a [!DNL Cloud Service] 은(는) 사전 구성된 을(를) 가질 수 있습니다 [!DNL Brand Portal] 인스턴스. 다음 [!DNL Cloud Manager] 사용자가 활성화 가능 [!DNL Brand Portal] 날짜 [!DNL Experience Manager Assets] as a [!DNL Cloud Service]. 다음을 참조하십시오 [Brand Portal 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=ko-KR).

* 이제 기업은 다음을 사용하여 자산을 소싱할 수 있습니다. [!DNL Brand Portal]. 에셋 소싱 기능 사용 [!DNL Brand Portal] 고객이 에이전시 사용자와 협력하여 새로운 마케팅 캠페인, 사진 촬영 및 프로젝트에 대한 에셋을 소싱할 수 있도록 지원합니다. 다음을 참조하십시오 [에서 에셋 소싱 [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* 다음 [!DNL Brand Portal] 이제 사용량 보고서에 활성 사용자만 표시됩니다. 비활성 사용자는 현재 표시되지 않습니다. 활성 사용자는에서 제품 프로필에 계정이 할당된 사용자입니다. [!DNL Admin Console]. 다음을 참조하십시오 [[!DNL Brand Portal] 보고서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* 위치 [!DNL Brand Portal], 폴더, 컬렉션 등을 다운로드할 때 각 에셋에 대해 별도의 폴더를 만들 수 있는 새로운 다운로드 설정이 도입되었습니다. 다음을 참조하십시오 [다운로드 설정](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

## [!DNL Assets]에서 수정된 버그 {#bug-fixes-assets}

* 속성을 업데이트하기 위해 여러 에셋을 선택한 경우 오류가 발생하거나 선택하지 않은 에셋의 속성이 업데이트되는 경우가 있습니다. (CQ-4316532)
* 열려고 할 때 [!UICONTROL 에셋 관리자 검색 레일], 페이지가 비어 있는 상태로 클릭 [!UICONTROL 편집] > [!UICONTROL 설정] 는 오류를 생성합니다. (CQ-4315079)
* 이름 지정 충돌을 해결한 후 기존 에셋의 새 버전을 만들면 원래 에셋의 메타데이터를 덮어씁니다. (CQ-4313594)
* 주석 텍스트가 긴 에셋을 인쇄하면 공백을 사용할 수 있더라도 주석 텍스트가 잘립니다. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리: 경험 조각을 사용하여 제품 카탈로그 페이지를 개별적으로 풍성하게 만듭니다.

* 연결된 콘텐츠로 빠르게 이동하는 작업을 포함하여 연결된 에셋 및 경험 조각을 표시하도록 제품 콘솔 속성을 확장했습니다.

* 최신 CIF 코어 구성 요소 버전 v1.8.0이 포함된 CIF Venia 참조 사이트 - 2021.02.24가 릴리스되었습니다. 다음을 참조하십시오 [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24) 을 참조하십시오.

* CIF 코어 구성 요소 v1.8.0이 릴리스되었습니다. 다음을 참조하십시오 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) 을 참조하십시오.

## Cloud Manager {#cloud-manager}

### 릴리스 일자 {#release-date-cm}

AEM as a Cloud Service 2021.2.0의 Cloud Manager 릴리스 일자는 2021년 2월 11일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}


* 이제 Assets 고객은 Cloud Manager UI를 통해 셀프서비스 방식으로 Brand Portal 인스턴스를 배포할 시기와 위치를 선택할 수 있습니다. Assets 솔루션이 포함된 일반(샌드박스가 아닌) 프로그램의 경우 이제 Brand Portal을 프로덕션 환경에서 프로비저닝할 수 있습니다. 프로비저닝은 프로덕션 환경에서 한 번만 수행할 수 있습니다.

* 프로젝트 및 샌드박스 만들기에 사용되는 AEM Project Archetype이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 더 이상 사용되지 않는 API 목록이 최신 Cloud Service SDK 릴리스에서 더 이상 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* Cloud Manager용 SonarQube 프로필이 업데이트되어 Sonar 규칙 squid:S2142가 제거되었습니다. 더 이상 스레드 중단 검사와 충돌하지 않습니다.

* Cloud Manager UI는 연결된 환경에 실행 중인 파이프라인이 연결되어 있거나 현재 승인 단계를 기다리고 있기 때문에 일시적으로 도메인 이름을 추가/업데이트할 수 없는 사용자에게 알립니다.

* sonar 접두사가 붙은 고객 `pom.xml` 파일에 설정된 속성은 이제 빌드 및 품질 스캔 실패를 방지하고자 동적으로 제거됩니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름에서 SSL 인증서를 사용 중이기 때문에 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* Cloud Service 호환성 문제를 다루기 위해 추가 코드 품질 규칙이 추가되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* SSL 인증서를 도메인 이름과 일치시킬 때 더 이상 대소문자를 구분하지 않습니다.

* 이제 Cloud Manager UI는 인증서 개인 키가 2048비트 제한을 충족하지 않는 경우 적절한 오류 메시지와 함께 사용자에게 알립니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름에서 SSL 인증서를 사용 중이기 때문에 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알립니다.

* 경우에 따라 내부 문제로 인해 환경 삭제가 중단될 수 있습니다.

* 일부 파이프라인 실패가 파이프라인 오류로 잘못 보고되었습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.2.4의 릴리스 날짜는 2021년 2월 10일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 여러 사용자를 매핑할 때 일부 사용자의 IMS ID가 잘못 매핑되었습니다. 이 문제가 해결되었습니다.

### 릴리스 일자 {#release-date-ctt-feb}

콘텐츠 전송 도구 v1.2.2의 릴리스 날짜는 2021년 2월 01일입니다.

### 컨텐츠 전송 도구의 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 새로운 기능과 UI가 추가되었습니다. 이 기능은 콘텐츠 마이그레이션 활동의 일부로 기존 사용자 및 그룹을 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다.
자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html)을 참조하십시오.
* 이제 콘텐츠 전송 도구는 하위 그룹을 포함하여 마이그레이션 세트에서 참조된 모든 그룹과 사용자를 마이그레이션합니다.
* 사용자는 아래에서 특정 경로를 선택할 수 있습니다. `/etc` 마이그레이션 세트를 생성할 때.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.2의 릴리스 날짜는 2021년 2월 18일입니다.

### Best Practices Analyzer 의 새로운 기능 {#what-is-new-bpa}

* AEM Forms 및 AEM Forms 구현의 사용을 감지하고 AEM Forms as a Cloud Service으로의 마이그레이션과 관련된 영역을 표시하는 기능.
* 사용자 지정 구성 요소 및 템플릿의 사용 및 개수를 감지하고 보고하는 기능.
* 사용된 노드 저장소 및 데이터 저장소 유형을 감지하는 기능.
* Dynamic Media 사용을 감지하는 기능.
* 사용된 Java 버전을 감지하는 기능.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### 코드 리팩터링 도구의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 Repository Modernizer에 대한 몇 가지 버그 수정이 포함되어 있습니다.
다음을 참조하십시오 [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) 이 플러그인에 대해 자세히 알아보십시오.

### 버그 수정 {#bug-fixes-crt}

* Repository Modernizer에서 몇 가지 버그 수정이 수행되었습니다.
다음을 참조하십시오 [GitHub 리소스: aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 을 참조하십시오.
