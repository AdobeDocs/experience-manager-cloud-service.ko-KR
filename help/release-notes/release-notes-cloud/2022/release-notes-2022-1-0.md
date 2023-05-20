---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.1.0 릴리스 정보.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2022.1.0 릴리스 정보.'
exl-id: 1c40ab67-8fd7-4f29-b8c9-dd98b6d5b490
source-git-commit: a66215277ca83c011f2f4df621d055049c4c93a7
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 98%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 2022.1.0 릴리스 정보 {#release-notes}

다음 섹션에서는 의 2022.1.0 버전에 대한 기능 릴리스 노트를 간략하게 설명합니다 [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>여기에서 2020, 2021 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=ko-KR)를 참조하십시오.

## 릴리스 일자 {#release-date}

[!DNL Adobe Experience Manager]인 [!DNL Cloud Service]의 현재 릴리스(2022.1.0)의 날짜는 2022년 2월 3일입니다.
다음 릴리스(2022.3.0) 날짜는 2022년 3월 31일입니다.

## 릴리스 비디오 {#release-video}

[2022년 1월 릴리스 개요](https://video.tv.adobe.com/v/340120) 비디오를 통해 2022.1.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* **[프론트 엔드 파이프라인 활성화](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** 버튼은 페이지 핵심 구성 요소의 v2를 사용하는 사이트를 위한 Sites 콘솔의 **Site** 레일에서 사용할 수 있습니다. 이 버튼은 기존 클라이언트 라이브러리 위에 프런트 엔드 파이프라인과 함께 배포된 테마를 로드하도록 사이트를 구성합니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* [!DNL Dynamic Media] - 이제 Dynamic Media Classic 데스크탑 애플리케이션을 사용하지 않고도 AEM Dynamic Media 인터페이스를 사용하여 일반 설정 및 게시 설정을 구성할 수 있습니다.

* [!DNL Dynamic Media]는 이제 MXF 비디오에 대해 수집, 미리보기, 재생 및 게시 기능을 지원합니다. MXF에 대한 주석 및 구매 가능한 비디오는 아직 지원되지 않습니다.

* 원격 DAM 및 Sites 배포 간의 연결을 구성한 후에는 Sites 배포에서 원격 DAM의 에셋을 사용할 수 있습니다. 이제 원격 DAM 에셋 또는 폴더에서의 [작업을 업데이트하고, 삭제하고, 이름을 바꾸고, 이동](/help/assets/use-assets-across-connected-assets-instances.md)할 수 있습니다. 업데이트는 약간의 지연과 함께 Sites 배포에서 자동으로 사용할 수 있습니다.

### [!DNL Assets] 프리릴리스 채널의 새로운 기능 {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] 이제 즉시 사용 가능한 Dynamic Media URL 및 뷰어 임베드 코드를 업데이트하도록 사용자 인터페이스에서 [하나의 별칭 계정](/help/assets/dynamic-media/dm-alias-account.md)을 구성할 수 있습니다. 이는 리브랜딩과 같은 비즈니스 컨텍스트에 대한 업데이트를 반영하여 SEO에 긍정적인 영향을 미칩니다.

* 이제 [!DNL Experience Manager Assets] 사용자 인터페이스를 사용하여 다음을 수행할 수 있습니다.

   * 저장소에서 중복 에셋 감지를 구성합니다.

   * 이미지에 디지털 워터마크 추가를 구성합니다.

* 이제 관리자는 대량 다운로드를 위한 이메일 서비스를 구성할 수 있습니다. 이를 통해 사용자는 [!DNL Experience Manager Assets] 인터페이스에서 [대량 다운로드에 대한 이메일 알림](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads)을 활성화할 수 있습니다. 사용자는 다운로드 프로세스가 완료되면 아카이브된 zip 폴더의 다운로드 링크가 포함된 이메일 알림을 수신하게 됩니다.


* [게시 관리](/help/assets/manage-publication.md) 기능은 개선된 사용자 인터페이스로 향상되었습니다. 사용자는 선택한 대상에 콘텐츠를 게시하거나 게시를 취소하고, DAM 저장소의 게시 목록에 [콘텐츠를 추가](/help/assets/manage-publication.md#add-content)하고, [폴더 설정을 포함하여](/help/assets/manage-publication.md#include-folder-settings) 선택한 폴더의 콘텐츠를 게시하고 필터를 적용하고, 나중에 게시할 날짜 또는 시간에 [게시 일정](/help/assets/manage-publication.md#publish-assets-later)을 지정할 수 있습니다.

### 버그 수정 {#bug-fixes}

* 원본 렌디션이 없는 처리되지 않은 에셋은 AEM on-premise에서 클라우드 서비스로 에셋을 마이그레이션하는 동안 처리를 위해 Asset Compute로 전송됩니다.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=ko-KR)를 통해 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드와 배치 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   * XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   * 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 양식을 생성합니다.
   * XFA 양식 PDF에서 인쇄 PDF를 생성합니다.
   * 여러 데이터 세트를 소스 템플릿과 병합하여 PDF, PostScript, PCL 및 ZPL 문서를 대량으로 생성합니다.

* **커뮤니케이션 API로 생성된 기록 문서 및 PDF 문서에 대한 맞춤형 글꼴**: 이제 커뮤니케이션 API를 사용하여 생성된 PDF 문서의 브랜드 승인 글꼴을 사용하여 조직 요구 사항을 맞출 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms}

* **[어셈블러 API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: PDF 문서에 대한 정보를 결합, 재배열, 보강 및 얻을 수 있는 어셈블러 API입니다.


## CIF 추가 기능 {#cloud-services-cif}

### 새로운 기능 {#what-is-new-cif}

* 향상된 myAccount 구성 요소
* 제품 추천 구성 요소는 추가 페이지 유형(홈 페이지, 장바구니, 주문 확인)을 지원합니다.
* **위시리스트**
   * 로그인한 방문자는 위시리스트에 제품을 추가할 수 있습니다.
   * myAccount를 통해 위시리스트 및 해당 제품을 관리할 수 있습니다.
   * “위시리스트에 추가” 버튼은 정책을 통해 구성 요소 수준에서 활성화/비활성화할 수 있습니다(예: 제품 티저, 제품 세부 사항).
   * 핵심 구성 요소 및 AEM Venia Storefront에서 사용 가능

![위시리스트](/help/assets/CIF/wishlist.png)

## Cloud Manager {#cloud-manager}

### 릴리스 날짜 {#release-date-cm}

AEM as a Cloud Service 2022.01.0의 Cloud Manager 릴리스 날짜는 2022년 1월 20일입니다. 다음 릴리스는 2022년 2월 10일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-cm}

* Cloud Manager는 [동일한 Git Commit이 여러 전체 스택 파이프라인 실행에 사용되는 것을 감지하면 코드 베이스를 다시 빌드하지 않습니다](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse).
* 이제 AEM 환경 로그에 액세스하려면 **Deployment Manager** 제품 프로필이 필요합니다. 이 프로필이 없는 사용자에게는 사용자 인터페이스에서 비활성화된 버튼이 표시됩니다.
* UI는 Sites가 솔루션으로 활성화되지 않은 프로그램에 대한 프론트엔드 파이프라인 구성을 허용하지 않습니다.
* Git 암호 생성 시 만료 날짜가 표시됩니다.

### 버그 수정 {#bug-fixes-cm}

* 일부 프론트엔드 파이프라인 배포에서 발생한 Null 포인터 예외가 수정되었습니다.
* 이제 환경에서 오래된 버전의 AEM을 실행할 때 환경 변수를 추가, 업데이트 및 삭제할 수 있습니다.
* 드문 경우지만 예약된 단계를 사용한 파이프라인에 대해 빌드 이미지 단계가 더 이상 오류로 표시되지 않습니다.
* 저장소가 하나만 있는 프로그램의 경우 이제 파이프라인 실행 화면에 저장소 이름이 표시됩니다.

## 콘텐츠 전송 도구 {#ctt-release}

### 릴리스 날짜 {#release-date-ctt}

콘텐츠 전송 도구 v1.8.6의 릴리스 날짜는 2022년 2월 3일입니다.

### 새로운 기능 {#what-is-new-ctt}

* 콘텐츠 유효성 검사 - 사용자는 콘텐츠 전송 도구에서 추출한 모든 콘텐츠가 대상 인스턴스에 성공적으로 수집되었는지 확인할 수 있습니다. 이 기능을 사용하려면 소스 AEM 환경의 `System Console`에서 활성화해야 합니다. 자세한 내용은 [콘텐츠 전송 확인 - 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=ko-KR#getting-started)를 참조하십시오.

### 버그 수정 {#bug-fixes-ctt}

* 사용자 매핑이 대소문자를 구분하기 때문에 일부 사용자가 매핑되지 않았습니다. 이 문제가 해결되었습니다. 사용자 매핑은 더 이상 대소문자를 구분하지 않습니다.

## Best Practices Analyzer {#bpa-release}

### 릴리스 날짜 {#release-date-bpa}

우수 사례 분석기 v2.1.24의 릴리스 날짜는 2022년 2월 1일입니다.

### 새로운 기능 {#what-is-new-bpa}

* 스마트 태그가 있거나 없는 에셋 수를 감지하고 보고하는 기능.
* 사용된 핵심 구성 요소 버전 감지 및 보고 기능.
* BPA가 실행된 소스 계층 유형(작성자 또는 게시)을 감지하고 보고하는 기능.

### 버그 수정 {#bug-fixes-bpa}

* BPA 크기 조정 논리는 더 빠르고 효율적으로 만들어졌습니다.
* 일부 시나리오에서는 BPA가 실행될 때 분석된 수를 증가시키지 않았습니다. 이 문제가 해결되었습니다.
