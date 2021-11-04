---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.9.0 릴리스의 릴리스 노트'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 2021.9.0 릴리스의 릴리스 노트'
source-git-commit: bef02a7e72d54b7c9eb5726bb046460c5902fb84
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 4%

---



# 의 현재 릴리스 노트 [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

다음 섹션에서는 현재(최신) 버전의 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>자세한 내용은 [최근 설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) 릴리스 정보와 직접 관련이 없는 설명서 업데이트 세부 정보는

## 릴리스 날짜 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 현재 릴리스(2021.9.0)는 2021년 10월 6일입니다.
다음 릴리스(2021.10.0)은 2021년 11월 4일에 있습니다.

## 릴리스 비디오 {#release-video}

을(를) 보십시오. [2021년 9월 릴리스 개요](https://video.tv.adobe.com/v/337381) 비디오 를 참조하십시오.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### 의 새로운 기능 [!DNL Sites] 사전 릴리스 채널 {#sites-prerelease-features}

* 이제 컨텐츠 조각 모델은 게시된 후 읽기 전용 상태로 자동 설정되므로, 편집된 모델을 다시 게시한 후 라이브 API 쿼리를 일시적으로 중단하지 않습니다. 게시된 모델을 편집하려고 하면 사용자에게 경고가 표시됩니다. 경고를 수락하면 편집할 수 있습니다.

## [!DNL Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### 의 새로운 기능 [!DNL Assets] {#assets-features}

* 이제 사용자는 열 및 카드 보기에서 검색 결과에 표시된 자산을 정렬할 수 있습니다. 정렬은 이름, 작성, 수정 또는 없음 열에서 작동합니다.

   ![검색 결과 정렬 위치 [!DNL Assets] 열 및 카드 보기에서](/help/assets/assets/sort-searched-assets.png)
   *그림: 검색 결과 정렬 위치 [!DNL Assets] 열 및 카드 보기에서 다음을 수행합니다.*

* 자산 마이크로서비스를 사용하여 처리를 프로그래밍 방식으로 호출하려면 새 API가 도입됩니다. 이제 개발자는 폴더의 하나 이상의 특정 자산에 기존 폴더 수준 처리 프로필을 적용할 수 있습니다. 처리 프로필은 사용자 지정 메타데이터 속성 업데이트를 기반으로 적용됩니다. 자세한 내용은 `AssetProcessor` 에서 [[!DNL Experience Manager] API 참조](https://www.adobe.io/experience-manager/reference-materials/). 전과 마찬가지로 [사용자 인터페이스에서 자산 마이크로서비스 사용](/help/assets/asset-microservices-configure-and-use.md).

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature via CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms-sep-2021}

* **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준용 Adobe Sign은 서명자 외에 계약 수신자의 역할을 확장하여 워크플로우 요구 사항에 보다 잘 부합할 수 있는 옵션을 제공합니다. 이제 다음을 수행할 수 있습니다 [각 동의 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있도록 설정](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform)서명자가 기본 역할인 경우

* **응용 Forms용 Analytics**: 이제 Adobe Analytics for Adaptive Forms을 통해 최종 사용자 행동을 캡처하고 추적하여 최종 사용자 통찰력을 수집할 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

* **Microsoft Dynamics 및 Salesforce와 AEM Forms을 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce용 기본 데이터 소스 구성 및 데이터 모델을 제공하여 만듭니다 [개발자가 적응형 양식의 데이터 소스로 Microsoft Dynamics 및 Salesforce를 구성할 수 있는 빠르고 쉬운 방법](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en).

* **DocuSign을 사용하여 적응형 양식에 전자 서명:** DocuSign을 사용하여 적응형 양식에 전자 서명할 수 있습니다. 이 서비스는 적응형 양식과 함께 DocuSign을 사용하기 위한 사용자 지정 제출 작업을 제공합니다. 소프트웨어 배포에 있는 패키지를 설치하여 제출 작업을 가져올 수 있습니다.

### 의 베타 기능 [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **통합 스토리지 커넥터:** Unified Storage Connector를 사용하여 고객 관리 리포지토리에서 처리 중인 데이터를 외부화할 수 있습니다. 예를 들어 다음 작업을 수행할 수 있습니다.
   * Forms Portal의 저장 및 재개 기능을 활성화하고 고객 관리 데이터 저장소에 적응형 양식 초안을 저장합니다.
   * 고객 관리 저장소에 SPD(중요 개인 데이터)가 포함된 처리 중인 AEM 워크플로우 데이터(AEM Workflow 변수 데이터)를 저장합니다.

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성하는 데 도움이 됩니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   * XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   * XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 사이트 편집기의 새로운 &quot;관련 전자 상거래 컨텐츠&quot; 탭은 현재 컨텍스트에 대한 관련 AEM 제품 컨텐츠에 빠르게 액세스함으로써 작성자 효율성을 높입니다

   ![관련 상거래 콘텐츠](/help/assets/CIF/associated-commerce-content.png)

* 제품 선택기 UI를 개선하여 사용자 경험 향상, 효율성 향상 및 복잡한 제품 카탈로그에 대한 지원

   ![새 제품 선택기](/help/assets/CIF/product-picker.png)

* 탐색 구성 요소에서 &quot;include_in_menu&quot; 속성을 준수합니다.

### 버그 수정 {#bug-fixes-cif}

* 메뉴 캐시 플러시가 예상대로 작동하지 않습니다.

* AEM CS 배포 단계 중 및 클라이언트측 구성 요소를 사용하지 않는 경우 JS 오류가 발생합니다

* sling:configs 노드가 있는 폴더에서 CIF 클라우드 구성을 만들 수 없습니다

## [!DNL Experience Manager Screens] 로서의 [!DNL Cloud Service] {#screens}

### 새로운 기능 {#what-is-new-screens}

* 이제 Screens as a Cloud Service에서 기본 재생 모니터링을 지원합니다. 이제 플레이어는 각 ping을 사용하여 다양한 재생 지표를 보고합니다(기본값 30초). 지표를 기반으로 다양한 에지 사례(멈춤 경험, 빈 화면, 예약 문제 등)를 탐지하는 기능을 제공합니다. 이 기능을 사용하면 팀이 플레이어가 제대로 컨텐츠를 재생하는지 원격으로 모니터링할 수 있고, 필드의 빈 화면이나 손상된 경험에 대한 반응성을 개선하며, 최종 사용자에게 손상된 경험을 표시할 위험을 줄일 수 있습니다.
자세한 내용은 [기본 재생 모니터링](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) 자세한 내용

* 의 비디오에 대한 축소판 지원은 이제 Screens에서 as a Cloud Service으로 지원됩니다. 컨텐츠 작성자는 해당 팀이 실제 비디오를 마무리하는 동안 이미지를 자리 표시자로 사용하고 컨텐츠 재생 및 타깃팅을 적절히 테스트할 수 있도록 비디오의 축소판을 정의할 수 있습니다. 비디오를 재생하지 못할 경우에 이미지를 사용할 수도 있습니다.
자세한 내용은 [비디오에 대한 축소판 지원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) 자세한 내용

### 버그 수정 {#bug-fixes-screens}

* 플레이어가 포함된 페이지의 콘텐츠를 표시할 수 없으며 이 문제가 해결되었습니다.

* 성공적으로 로그인하면 기본 페이지(채널)로 이동한 후 내부 서버 오류 페이지로 끝납니다.

* 재생 목록을 제거할 때 연결된 태그 항목이 제거되지 않았습니다.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### New features in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Advanced Networking**

>[!INFO]
>
>고급 네트워킹 기능은 2021.9.0 릴리스의 일부이며, 10월 중순에 고객이 사용할 수 있도록 제공됩니다.

[!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 이제 다음과 같은 여러 유형의 고급 네트워킹 기능을 제공합니다.

* 비표준 포트에서 트래픽을 내보내기 위한 유연한 포트 송신 이제 Adobe 지원에 문의하지 않고도 가능합니다.
* 전용 송신 IP 주소 를 사용하여 고유한 IP에서 AEM as a Cloud Service으로 트래픽을 내보내고 이제 모든 포트를 지원합니다.
* VPN을 통해 인프라와 AEM as a Cloud Service 간의 트래픽을 보호할 수 있습니다.

다음 문서를 참조하십시오. [설명서](/help/security/configuring-advanced-networking.md) Cloud Manager API를 사용하여 고급 네트워킹을 자체 제공하는 방법 등 자세한 정보를 확인하십시오.

**인덱스 최적화**

검색 쿼리 및 색인 생성 성능을 개선하기 위해 전체 텍스트 인덱스 lucene-2는 더 이상 기본 제공 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 아래와 같이 변경하는 것을 의미합니다. AEM 고객에 따라 AEM 환경에서 이 전체 텍스트 인덱스를 제거하기 위해 Adobe 엔지니어링 팀은 개별적으로 그리고 적극적으로 고객과 작업하여 Lucene 전체 텍스트 인덱스를 완화하고 지속적으로 제거합니다. 다음 사이트를 방문하십시오. [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] [설명서](/help/operations/indexing.md#index-optimizations) 자세한 내용은 고객 지원 센터에 직접 문의하시기 바랍니다.

## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.9.0 및 2021.8.0에서 Cloud Manager에 대한 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date-cm-sept}

AEM as a Cloud Service 2021.9.0의 Cloud Manager 릴리스 날짜는 2021년 9월 9일입니다.
다음 릴리스는 2021년 10월 7일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm-sept}

* Cloud Manager에서 사용하는 AEM Project Archetype 버전이 버전 30으로 업데이트되었습니다.

* Cloud Manager 랜딩 페이지의 프로그램 카드 및 관련 경험이 새로 고침되었습니다.

* 이제 코드 품질 단계 로그에 OakPal 검색 프로세스에 대한 자세한 로깅 정보가 포함됩니다.

* 이제 활동 페이지 메뉴 옵션에 다음 옵션이 포함됩니다 **다운로드 로그** 코드 생성기 실행을 완료했습니다. 이를 선택하면 빌드 단계의 로그가 다운로드됩니다.

* 프로그램 카드에서 바로 을 클릭하면 이제 Cloud Manager 개요 페이지로 이동합니다.

### 버그 수정 {#bug-fixes-sept}

* 이제 사용자는 구성할 수 있는 최대 허용 IP 허용 목록 수에 도달한 프로그램에서 새 IP 허용 목록을 추가하려고 하면 더 이해할 수 있는 메시지가 표시됩니다.

* 저장소 화면에서 URL 복사 메뉴 옵션을 선택할 때 잘못된 URL이 복사되었습니다.

## Cloud Acceleration Manager {#cam}

### 릴리스 날짜 {#release-date-october-cam}

Cloud Acceleration Manager 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-cam}

* 이제 Cloud Acceleration Manager에서 BPA 보고서를 인쇄 가능한 미리 보기로 볼 수 있으므로 인쇄하거나 인쇄하여 PDF에 인쇄하여 공유하기 쉽게 할 수 있습니다. 의 6단계 및 7단계를 참조하십시오 [우수 사례 분석 카드 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## 컨텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.6.0의 릴리스 날짜는 2021년 10월 4일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 아래 나열된 다음 기능을 포함하여 간소화된 사용자 경험을 통해 사용자 매핑이 개선되었습니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool).
   * 사용자 매핑을 실행하기 전에 사용자 관리 API에 대한 연결을 테스트합니다
   * 오류를 올바르게 건너뛰고 사용자 매핑 활동을 계속 진행합니다
   * 액세스 토큰이 만료된 경우(24시간 후) 사용자 매핑이 더 이상 실패하지 않습니다. 사용자 매핑은 마지막으로 중지된 위치에서 다시 실행할 수 있습니다.

* CTT 견고성을 높이기 위해 컨텐츠를 한 번에 작성자 인스턴스 또는 게시 인스턴스에 수집할 수 있습니다.

* 버전이 포함되면 경로는 `/var/audit` 은 감사 이벤트를 마이그레이션하기 위해 자동으로 포함됩니다.

## 모범 사례 분석기 {#best-practices-analyzer}

### 릴리스 날짜 {#release-date-bpa-latest}

Best Practices Analyzer v2.1.18 릴리스 날짜는 2021년 9월 2일입니다.

### 새로운 기능 {#what-is-new}

* 총 노드 수를 검색하고 보고하는 기능

* 노드 저장소 유형 및 크기를 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA가 Commerce Integration Framework의 존재를 잘못 감지했습니다.
