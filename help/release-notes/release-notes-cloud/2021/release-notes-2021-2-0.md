---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.2.0 릴리스 정보입니다.'
description: "[!DNL Adobe Experience Manager] 2021.2.0용 as a Cloud Service 릴리스 노트"
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 8%

---


# [!DNL Adobe Experience Manager] as a Cloud Service 릴리스 노트  {#release-notes}

다음 섹션에서는 다음에 대한 일반 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0은 2021년 2월 25일입니다.
다음 릴리스(2021.3.0)는 2021년 3월 25일에 있습니다.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### 헤드리스 컨텐츠 관리 {#headless}

* **[컨텐츠 조각 전달을 위한 GraphQL API](/help/headless/graphql-api/content-fragments.md)**: GraphQL 구문을 사용하여 컨텐츠 조각을 쿼리하고 컨텐츠 조각 모델을 기반으로 하여 JSON 형식으로 출력하는 기능입니다.

* **[GraphQL API 요청에 대한 인증 지원](/help/headless/security/authentication.md)**: 서버측 API에 대한 액세스 토큰을 사용하여 GraphQL API 요청을 인증할 수 있습니다.

* **[RemotePage 구성 요소](/help/implementing/developing/hybrid/remote-page.md)**: AEM 내에서 을 사용하여 외부 SPA을 보고 편집하는 지원을 추가했습니다.

* **[AEM 내에서 외부 SPA 편집](/help/implementing/developing/hybrid/editing-external-spa.md)**: 독립형 단일 페이지 애플리케이션을 AEM 인스턴스에 업로드하고, 편집 가능한 컨텐츠 섹션을 추가하고, 작성을 활성화하는 기능이 추가되었습니다.

* JSON 형식 및 로케일로 리치 텍스트를 출력하는 기능을 포함하여 GraphQL API에서 JSON 출력이 향상되었습니다.

* 전용 컨텐츠 조각 참조 데이터 유형 또는 여러 줄 텍스트 필드에서 인라인으로 컨텐츠 조각 참조를 통해 중첩된 컨텐츠 조각 구조를 만들 수 있도록 컨텐츠 조각 모델 중첩을 지원합니다.

* &quot;고유함&quot;, &quot;필수&quot; 및 &quot;번역 가능한&quot; 등 컨텐츠 조각 모델 데이터 유형에서 사용할 수 있는 추가 유효성 검사 규칙입니다.

* 컨텐츠 조각 모델에 태그를 지정하고 태그 또는 경로별 정책이 있는 폴더에서 컨텐츠 조각을 만들 수 있습니다.

* 조각 기반의 모델 게시 작업 및 표시를 포함하여 컨텐츠 조각 편집기의 유용성 개선 사항.

* 컨텐츠 조각 편집기에서 직접 JSON 출력을 미리 볼 수 있습니다.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 자산을 [!DNL Experience Manager Assets Brand Portal]. 새로운 마케팅 캠페인, 사진 촬영 및 프로젝트에 대해 에이전시 사용자의 자산을 가져오는 데 도움이 됩니다.

* [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] 는 사전 구성된 [!DNL Brand Portal] 인스턴스. 다음 [!DNL Cloud Manager] 사용자 활성화 가능 [!DNL Brand Portal] on [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service]. 자세한 내용은 [Brand Portal 활성화](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=ko-KR).

* 이제 기업은 [!DNL Brand Portal]. 자산 소싱 기능이 활용 [!DNL Brand Portal] 고객이 에이전시 사용자와 협력하여 새로운 마케팅 캠페인, 사진 촬영 및 프로젝트를 위한 자산을 제공할 수 있도록 지원합니다. 자세한 내용은 [자산 소싱의 [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=ko).

* 다음 [!DNL Brand Portal] 이제 사용량 보고서에는 활성 사용자만 표시됩니다. 비활성 사용자는 현재 표시되지 않습니다. 활성 사용자는 [!DNL Admin Console]. 자세한 내용은 [[!DNL Brand Portal] 보고서](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* in [!DNL Brand Portal]에 폴더, 컬렉션 등을 다운로드할 때 각 자산에 대해 별도의 폴더를 만들 수 있는 새 다운로드 설정이 도입되었습니다. 자세한 내용은 [다운로드 설정](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

## [!DNL Assets]에서 수정된 버그 {#bug-fixes-assets}

* 속성을 업데이트하기 위해 여러 자산을 선택하면 오류가 발생하거나 선택되지 않은 자산의 속성이 업데이트되는 경우가 있습니다. (CQ-4316532)
* 열려고 할 때 [!UICONTROL Assets 관리 검색 레일]를 눌러도 페이지가 공백으로 남아 있고 [!UICONTROL 편집] > [!UICONTROL 설정] 오류가 생성됩니다. (CQ-4315079)
* 이름 지정 충돌을 해결한 후 기존 자산의 새 버전을 만들면 원래 자산의 메타데이터를 덮어씁니다. (CQ-4313594)
* 긴 주석 텍스트가 있는 자산을 인쇄하면 공간이 있어도 주석 텍스트가 트림됩니다. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 경험 관리: 경험 조각을 사용하여 제품 카탈로그 페이지를 개별적으로 보강합니다.

* 연결된 컨텐츠로 빠르게 이동하는 작업을 포함하여 연결된 자산 및 경험 조각을 표시하도록 확장된 제품 콘솔 속성입니다.

* 최신 CIF 코어 구성 요소 버전 v1.8.0이 포함된 CIF Venia 참조 사이트 - 2021.02.24이 출시되었습니다. 다음을 참조하십시오. [CIF Venia 참조 사이트](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24) 자세한 내용

* CIF 코어 구성 요소 v1.8.0이 출시되었습니다. 자세한 내용은 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0) 자세한 내용

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM as a Cloud Service 2021.2.0의 Cloud Manager 릴리스 날짜는 2021년 2월 11일입니다.

### 새로운 기능 {#what-is-new-cloud-manager}


* 이제 자산 고객은 Cloud Manager UI를 통해 셀프 서비스 방식으로 Brand Portal 인스턴스를 배포할 시기 및 위치를 선택할 수 있습니다. 자산 솔루션이 있는 일반(샌드박스 아님) 프로그램의 경우 이제 프로덕션 환경에서 Brand Portal을 프로비저닝할 수 있습니다. 프로비저닝은 프로덕션 환경에서 한 번만 수행할 수 있습니다.

* 프로젝트 및 샌드박스 만들기에 사용된 AEM 프로젝트 원형이 버전 25로 업데이트되었습니다.

* 코드 스캔 중에 식별된 더 이상 사용되지 않는 API 목록은 최신 Cloud Service SDK 릴리스에서 더 이상 사용되지 않는 추가 클래스 및 메서드를 포함하도록 개선되었습니다.

* Cloud Manager용 SonarQube 프로필이 Sonar 규칙 squid:S2142를 제거하도록 업데이트되었습니다. 스레드 중단 확인과 더 이상 충돌하지 않습니다.

* Cloud Manager UI는 연관된 환경에 연결된 실행 중인 파이프라인이 있거나 현재 승인 단계를 기다리는 중이므로 도메인 이름을 일시적으로 추가/업데이트할 수 없는 사용자에게 알려줍니다.

* 고객에 설정된 속성 `pom.xml` 이제 sonar가 접두사로 추가된 파일이 빌드 및 품질 스캔 오류를 방지하기 위해 동적으로 제거됩니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알려줍니다.

* Cloud Service 호환성 문제를 다루는 추가적인 코드 품질 규칙이 추가되었습니다.

### 버그 수정 {#bug-fixes-cloud-manager}

* 도메인 이름과 일치하는 SSL 인증서는 더 이상 대/소문자를 구분하지 않습니다.

* 이제 Cloud Manager UI에서 인증서 개인 키가 적절한 오류 메시지와 함께 2048비트 제한을 충족하지 않는지 사용자에게 알려줍니다.

* Cloud Manager UI는 현재 배포 중인 도메인 이름으로 사용 중인 경우 일시적으로 SSL 인증서를 선택할 수 없는 사용자에게 알려줍니다.

* 경우에 따라 내부 문제로 인해 환경 삭제가 중단될 수 있습니다.

* 일부 파이프라인 오류가 파이프라인 오류로 잘못 보고되었습니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.2.4의 릴리스 날짜는 2021년 2월 10일입니다.

### 버그 수정 {#bug-fixes-ctt}

* 여러 사용자를 매핑할 때 일부 사용자의 IMS ID가 잘못 매핑되었습니다. 이 문제가 해결되었습니다.

### 릴리스 날짜 {#release-date-ctt-feb}

콘텐츠 전송 도구 v1.2.2의 릴리스 날짜는 2021년 2월 01일입니다.

### 컨텐츠 전송 도구의 새로운 기능 {#what-is-new-ctt}

* 컨텐츠 전송 도구 - 사용자 매핑 도구에 추가된 새로운 기능 및 UI입니다. 이 기능은 기존 사용자 및 그룹을 컨텐츠 마이그레이션 활동의 일부로 Adobe Identity Management 시스템 ID에 자동으로 매핑합니다.
을(를) 참조하십시오. [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html) 자세한 내용
* 이제 컨텐츠 전송 도구는 하위 항목을 포함하여 마이그레이션 세트에서 참조되는 모든 그룹 및 사용자를 마이그레이션합니다.
* 사용자는 `/etc` 마이그레이션 세트를 만들 때.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa}

Best Practices Analyzer v2.1.2의 출시일은 2021년 2월 18일입니다.

### 모범 사례 분석기의 새로운 기능 {#what-is-new-bpa}

* AEM Forms 및 AEM Forms 구현의 사용을 감지하고 AEM Forms as a Cloud Service로의 마이그레이션과 관련된 영역을 표시하는 기능.
* 사용자 지정 구성 요소 및 템플릿의 사용 및 수를 감지하고 보고할 수 있습니다.
* 사용된 노드 저장소 및 데이터 저장소 유형을 감지하는 기능.
* Dynamic Media의 사용을 감지하는 기능.
* 사용된 Java 버전을 감지하는 기능.

## 코드 리팩터링 도구 {#code-refactoring-tools}

### 코드 리팩터링 도구의 새로운 기능 {#what-is-new-crt}

* 새로운 버전의 AIO-CLI 플러그인이 출시되었습니다. 이 플러그인의 최신 버전에는 Repository Modernizer에 대한 몇 가지 버그 수정이 포함되어 있습니다.
을(를) 참조하십시오. [통합 경험](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) 추가 정보

### 버그 수정 {#bug-fixes-crt}

* Repository Modernizer에 대해 몇 가지 버그 수정이 수행되었습니다.
을(를) 참조하십시오. [GitHub 리소스: aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) 자세한 내용
