---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.9.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.9.0 릴리스 정보입니다.'
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 21%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2020 및 2021과 같은 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [최신 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]의 현재 릴리스(2021.9.0) 날짜는 2021년 10월 6일 목요일입니다.
다음 릴리스(2021.10.0) 날짜는 2021년 11월 4일 금요일입니다.

## 릴리스 비디오 {#release-video}

추가된 기능에 대한 요약을 보려면 [2021년 9월 릴리스 개요](https://video.tv.adobe.com/v/337381) 비디오를 보십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites] 프리릴리스 채널의 새로운 기능 {#sites-prerelease-features}

* 이제 콘텐츠 조각 모델은 게시된 후 읽기 전용 상태로 자동 설정되므로, 편집된 모델을 다시 게시한 후 의도하지 않게 라이브 API 쿼리가 손상되는 것을 방지할 수 있습니다. 게시된 모델을 편집하려고 할 때 사용자에게 경고 메시지가 표시됩니다. 경고를 수락하면 편집할 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* 이제 열 및 카드 보기에서 검색 결과에 표시된 에셋을 정렬할 수 있습니다. 정렬은 이름, 생성됨, 수정됨 또는 없음 열에서 작동합니다.

  ![열 및 카드 보기에서 [!DNL Assets]의 검색 결과 정렬](/help/assets/assets/sort-searched-assets.png)
  *그림: 열 및 카드 보기에서 [!DNL Assets]의 검색 결과를 정렬합니다.*

* 자산 마이크로서비스를 사용하여 처리를 프로그래밍 방식으로 호출하기 위해 새 API가 도입됩니다. 이제 개발자는 폴더에 있는 하나 이상의 특정 에셋에 기존 폴더 수준 처리 프로필을 적용할 수 있습니다. 처리 프로필은 사용자 지정 메타데이터 속성 업데이트를 기반으로 적용됩니다. [[!DNL Experience Manager] API 참조](https://developer.adobe.com/experience-manager/reference-materials/)에서 `AssetProcessor`을(를) 참조하십시오. 이전과 같이 [사용자 인터페이스에서 자산 마이크로서비스를 사용](/help/assets/asset-microservices-configure-and-use.md)할 수 있습니다.

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature by way of CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-sep-2021}

* **적응형 양식에서 Adobe Sign 역할을 사용** - 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign을 사용하면 계약 수신자의 역할을 서명자 이상으로 확장하여 워크플로 요구 사항에 보다 잘 부합하도록 할 수 있습니다. 이제 [계약의 각 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있도록 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform)할 수 있습니다. 서명자는 기본 역할입니다.

* **적응형 Forms용 Analytics** - 이제 적응형 Forms용 Adobe Analytics을 통해 최종 사용자 행동을 포착하고 추적하여 최종 사용자 인사이트를 수집할 수 있습니다. 데이터를 기반으로 정보에 입각한 결정을 내려 최종 사용자 경험을 개선할 수 있습니다.

* **Adobe Experience Manager(AEM) Forms을 Microsoft® Dynamics 및 Salesforce에 손쉽게 연결** - 이 서비스는 Microsoft® Dynamics 및 Salesforce를 위한 기본 데이터 소스 구성 및 데이터 모델을 제공합니다. 이렇게 하면 개발자가 Microsoft® Dynamics 및 Salesforce를 적응형 양식의 데이터 소스로 [더 빠르고 간편하게 구성할 수 있습니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html).

* **DocuSign을 사용하여 적응형 양식에 전자 서명하기** - DocuSign을 사용하여 적응형 양식에 전자 서명할 수 있습니다. 이 서비스는 적응형 양식에 DocuSign을 사용하는 사용자 정의 제출 액션을 제공합니다. 소프트웨어 배포에서 사용할 수 있는 패키지를 설치하여 제출 액션을 가져올 수 있습니다.

### [!DNL Forms]의 베타 기능 {#sep-what-is-new-forms-prerelease}

* **통합 스토리지 커넥터** - 통합 스토리지 커넥터를 사용하여 고객 관리 저장소에서 처리 중인 데이터를 외부화합니다. 예를 들어 다음 작업을 수행할 수 있습니다.
   * Forms 포털의 저장 및 재개 기능을 활성화하고 적응형 양식 초안을 고객 관리 데이터 저장소에 저장합니다.
   * 민감한 개인 데이터(SPD)가 포함된, 처리 중인 AEM Workflow 데이터(AEM Workflow 변수 데이터)를 고객 관리 저장소에 저장합니다.

* **[!DNL AEM Forms as a Cloud Service - Communications]** - [통신 API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* AEM Sites 편집기의 새로운 &quot;연결된 상거래 콘텐츠&quot; 탭은 현재 컨텍스트에 대한 관련 AEM 제품 콘텐츠에 빠르게 액세스하여 작성자의 효율성을 높입니다

  ![연결된 상거래 콘텐츠](/help/assets/CIF/associated-commerce-content.png)

* 향상된 사용자 경험, 향상된 효율성 및 복잡한 제품 카탈로그에 대한 지원을 위해 제품 선택기 UI가 개선되었습니다

  ![새 제품 선택기](/help/assets/CIF/product-picker.png)

* 탐색 구성 요소에서 &quot;include_in_menu&quot; 속성 준수

### 버그 수정 {#bug-fixes-cif}

* 메뉴 캐시 플러시가 예상대로 작동하지 않습니다.

* AEM CS 배포 단계 중 및 클라이언트측 구성 요소를 사용하지 않는 경우 JS 오류 발생

* sling:configs 노드가 있는 폴더에 CIF 클라우드 구성을 만들 수 없음

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### 새로운 기능 {#what-is-new-screens}

* Screensas a Cloud Service 에서 기본 재생 모니터링을 지원합니다. 이제 플레이어는 각 ping으로 다양한 재생 지표를 보고합니다(기본값은 30초). 지표를 기반으로 다양한 극단적 사례(중단 경험, 빈 화면, 일정 문제 등)를 감지할 수 있습니다. 이 기능을 통해 팀은 플레이어가 콘텐츠를 제대로 재생하는지 원격으로 모니터링할 수 있습니다. 현장에서의 빈 화면이나 깨진 경험에 대한 반응성을 향상시키고, 사용자에게 깨진 경험이 표시될 위험을 줄입니다.
자세한 내용은 [기본 재생 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html#playback-monitoring)을 참조하세요.

* 이제에서 썸네일 지원이 Screensas a Cloud Service 에서 지원됩니다. 콘텐츠 작성자는 이미지를 자리 표시자로 사용하고 적절한 팀에서 실제 비디오를 마무리하는 동안 콘텐츠 재생 및 타깃팅을 적절하게 테스트할 수 있도록 비디오의 썸네일을 정의할 수 있습니다. 비디오 재생이 실패할 경우 이미지를 사용할 수도 있습니다.
자세한 내용은 [비디오에 대한 썸네일 지원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html)을 참조하십시오.

### 버그 수정 {#bug-fixes-screens}

* 플레이어에서 임베드된 페이지의 콘텐츠를 표시할 수 없으며 이 문제는 이제 수정되었습니다.

* 로그인에 성공한 후 기본 페이지(채널)로 이동하면 내부 서버 오류 페이지가 표시됩니다.

* 재생 목록을 제거할 때 연결된 태그 항목이 제거되지 않았습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager as a Cloud Service]의 새로운 기능 {#foundation-features}

**고급 네트워킹**

>[!INFO]
>
>고급 네트워킹 기능은 2021.9.0 릴리스의 일부이며, 2021년 10월 중순에 고객에 대해 활성화되었습니다.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service]은(는) 이제 다음을 포함한 여러 유형의 고급 네트워킹 기능을 제공합니다.

* 비표준 포트의 이그레스 트래픽에 대한 유연한 포트 이그레스. 이제 Adobe 지원 센터에 문의하지 않고도 가능합니다.
* 전용 이그레스 IP 주소에서 고유 IP의 AEM as a Cloud Service 이그레스 트래픽으로, 이제 모든 포트를 지원합니다.
* 인프라와 AEM as a Cloud Service 간의 트래픽을 보호하기 위한 VPN입니다.

Cloud Manager API를 사용하여 고급 네트워킹을 셀프서비스하는 방법을 포함하여 자세한 내용은 [설명서](/help/security/configuring-advanced-networking.md)를 참조하십시오.

**색인 최적화**

검색 쿼리와 인덱싱의 성능을 개선하기 위해 전체 텍스트 인덱스 lucene-2는 더 이상 [!DNL Adobe Experience Manager]에서 이 릴리스의 [!DNL Cloud Service](으)로 즉시 사용되지 않습니다. AEM 고객에 따라 AEM 환경에서 이 전체 텍스트 색인을 제거하기 위해 Adobe 엔지니어링은 Lucene 전체 텍스트 색인을 부드럽고 지속적으로 제거하기 위해 개인적이며 적극적으로 고객과 협력합니다. 자세한 내용은 [!DNL Adobe Experience Manager]을(를) [!DNL Cloud Service] [설명서](/help/operations/indexing.md#index-optimizations)(으)로 방문하고 질문이 있는 경우 Adobe 지원에 직접 문의하십시오.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.9.0 및 2021.8.0의 Cloud Manager 릴리스 정보에 대해 간략히 설명합니다.

## 릴리스 일자 {#release-date-cm-sept}

AEM as a Cloud Service 2021.9.0의 Cloud Manager 릴리스 날짜는 2021년 9월 9일입니다.
다음 릴리스는 2021년 10월 7일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-sept}

* Cloud Manager에서 사용하는 AEM Project Archetype이 버전 30으로 업데이트되었습니다.

* Cloud Manager 랜딩 페이지 및 관련 경험의 프로그램 카드가 새로 고쳐졌습니다.

* 코드 품질 단계 로그에는 이제 OakPal 스캔 프로세스에 대한 자세한 로깅 정보가 포함됩니다.

* 활동 페이지 메뉴 옵션에는 이제 완료된 코드 생성기 실행에 대한 **로그 다운로드** 옵션이 포함되어 있습니다. 이 옵션을 선택하면 빌드 단계의 로그가 다운로드됩니다.

* Program 카드를 직접 클릭하면 이제 Cloud Manager 개요 페이지로 이동합니다.

### 버그 수정 {#bug-fixes-sept}

* 이제 구성할 수 있는 최대 허용 IP 허용 목록 수에 도달한 프로그램에서 IP 허용 목록에 추가하다를 추가하려고 할 때 보다 이해하기 쉬운 메시지가 표시됩니다.

* 저장소 화면에서 URL 복사 메뉴 옵션을 선택할 때 잘못된 URL이 복사되었습니다.

## Cloud Acceleration Manager {#cam}

### 릴리스 일자 {#release-date-october-cam}

Cloud Acceleration Manager의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-cam}

* 이제 Cloud Acceleration Manager은 인쇄 가능한 미리 보기에서 BPA 보고서를 볼 수 있는 기능을 사용자에게 제공하므로 간단한 인쇄 또는 인쇄를 PDF에 제공하여 쉽게 공유할 수 있습니다. [모범 사례 분석 카드 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#best-practices-analysis)의 6단계 및 7단계를 참조하세요.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.6.0의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 아래 나열된 기능을 포함하여 간소화된 사용자 경험으로 사용자 매핑이 개선되었습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html#using-user-mapping-tool)을 참조하세요.
   * 사용자 매핑을 실행하기 전에 사용자 관리 API에 대한 연결 테스트
   * 오류를 정상적으로 건너뛰고 사용자 매핑 활동을 계속합니다.
   * 액세스 토큰이 만료된 경우(24시간 후) 사용자 매핑이 더 이상 실패하지 않습니다. 사용자 매핑은 마지막으로 중지된 위치에서 다시 실행할 수 있습니다.

* CTT 견고성을 높이기 위해 콘텐츠를 작성자 인스턴스 또는 Publish 인스턴스로 한 번에 수집할 수 있습니다.

* 버전이 포함되면 감사 이벤트를 마이그레이션할 수 있도록 `/var/audit` 경로가 자동으로 포함됩니다.

## Best Practices Analyzer {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

모범 사례 분석기 v2.1.18의 릴리스 날짜는 2021년 9월 2일입니다.

### 새로운 기능 {#what-is-new}

* 총 노드 수를 감지하고 보고하는 기능.

* 노드 저장소 유형 및 크기를 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA는 Commerce integration framework의 존재를 거짓으로 탐지하고 있었다.
