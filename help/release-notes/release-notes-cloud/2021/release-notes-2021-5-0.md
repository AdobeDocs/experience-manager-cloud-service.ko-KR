---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.5.0 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 2021.5.0 릴리스 정보입니다.'
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
source-git-commit: af5eb5aeb34e2f0ead98e0a0acb412b19bcfe517
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 29%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 일반 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>여기에서 이전 버전의 릴리스 정보로 이동할 수 있습니다. 예를 들어, 2020년, 2021년 등의 경우입니다.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 날짜 {#release-date}

에 대한 릴리스 날짜 [!DNL Adobe Experience Manager] as a Cloud Service 2021.5.0은 2021년 5월 27일입니다.
다음 릴리스(2021.6.0)는 2021년 6월 28일에 있습니다.

## AEM as a Cloud Service 기반 {#foundation}

### AEM as a Cloud Service Foundation의 새로운 기능 {#what-is-new-foundation}

* [사전 릴리스 채널](/help/release-notes/prerelease.md): 프로덕션에서 라이브로 전환되기 전에 한 달 동안 예정된 기능을 미리 봅니다!

* [API 사용 중단](/help/release-notes/deprecated-apis.md): 더 이상 사용되지 않는 최신 AEM as a Cloud Service API 목록을 사용할 수 있습니다.

* [AEM as a Cloud Service SDK Build Analyzer Maven 플러그인](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): 더 이상 사용되지 않는 Java API 확인 및 기타 개선 사항이 포함된 전문 프로젝트를 최신 버전으로 업데이트합니다.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Sites]의 새로운 기능 {#what-is-new-sites}

* 곧 새 항목에서 콘텐츠를 확인할 수 있습니다 [미리 보기 계층](/help/sites-cloud/authoring/fundamentals/previewing-content.md) 최종 경험의 모양과 느낌을 시뮬레이션하려면 게시 계층에서 시뮬레이션 합니다. 이 기능은 AEM Sites 관리 게시 마법사에서 활성화됩니다. 이 마법사를 사용하면 이제 게시 또는 미리 보기 간에 게시 대상을 선택할 수 있습니다. 그런 다음 미리 보기에서 경험에 전용 URL을 통해 액세스할 수 있습니다. 미리 보기에서 유효성 검사 후 평소대로 컨텐츠를 작성자에서 게시로 게시할 수 있습니다. AEM as a Cloud Service 환경에서 미리 보기 서비스 활성화는 다음 몇 주 후에 점진적으로 롤아웃됩니다.

## [!DNL Adobe Experience Manager Assets] 로서의 [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#what-is-new-assets}

* 링크 공유 기능을 사용하여 공유된 자산을 다운로드할 수 있습니다. 이제 이 다운로드에서는 매우 큰 다운로드에서도 빠르고 중단되지 않은 다운로드를 제공하는 비동기 서비스를 사용합니다. 자세한 내용은 [자산 다운로드](/help/assets/download-assets-from-aem.md#link-share-download).

   ![받은 편지함 다운로드](/help/assets/assets/download-inbox.png)

### 사전 릴리스 채널에서 사용할 수 있는 새로운 기능 {#what-is-new-assets-prerelease}

* 메타데이터 스키마는 폴더 속성에 직접 적용할 수 있습니다.

   ![폴더 속성에서 메타데이터 스키마 추가](/help/assets/assets/metadata-schema-folder-properties.png)

* 자산 일괄 수집 도구를 사용하여 일괄 수집 중에 메타데이터를 추가할 수 있습니다.

* 사용자 경험 개선 사항은 폴더에 있는 자산 수를 표시합니다. 폴더에 있는 1000개 이상의 자산의 경우, [!DNL Assets] 1000 이상을 표시합니다.

   ![인터페이스에 폴더의 자산 수가 표시됩니다](/help/assets/assets/browse-folder-number-of-assets.png)

### [!DNL Assets]의 수정된 버그 {#assets-bugs-fixed}

* 매우 큰 파일을 업로드하면 [!DNL Experience Manager desktop app]. (CQ-4320942)
* 도구 모음 옵션은 폴더 내에서 동일한 컬렉션을 선택하고 검색 결과에서 선택되면 다릅니다. (CQ-4321406)

#### Dynamic Media의 새로운 기능 {#what-is-new-dm}

* 스마트 이미징 DPR(Device Pixel Ratio) 및 네트워크 대역폭 최적화를 사용하면 고해상도 디스플레이와 제한된 네트워크 대역폭을 사용하는 장치에서 고품질 이미지를 효율적으로 제공할 수 있습니다. 자세한 내용은 [스마트 이미징 FAQ](/help/assets/dynamic-media/imaging-faq.md) 및 [차세대 이미지 포맷인 WebP 및 AVIF를 사용한 이미지 최적화.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)
* Dynamic Media 게재에서 차세대 이미지 형식 AVIF에 대한 지원이 도입되었습니다(fmt URL 수정자).

## [!DNL Adobe Experience Manager Forms] 로서의 [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms}

* **상황별 도움말**: 작성자가 편집기의 다양한 기능을 더 잘 이해하도록 돕기 위해 적응형 양식 편집기, 템플릿 편집기, 테마 편집기에 대한 상황별 도움말을 추가했습니다.
* **속성 브라우저의 오류 메시지**: 적응형 양식 속성 브라우저에서 각 속성에 대한 오류 메시지를 추가했습니다. 이러한 메시지는 필드의 허용 값을 이해하는 데 도움이 됩니다.

### [!DNL Forms]의 예정된 베타 기능 {#what-is-new-forms-prerelease}

Output as a Cloud service: Output 서비스는 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있도록 합니다. 이 서비스를 사용하면 동기화 모드와 비동기화 배치 모드에서 문서를 생성할 수 있습니다. Output 서비스를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

* XML 데이터로 템플릿 파일을 채워 최종 양식 문서를 생성합니다.
* 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
* XFA 양식 PDF에서 인쇄 PDF를 생성합니다.

Beta 프로그램에 등록하려면 formscsbeta@adobe.com에 문의하십시오.

### [!DNL Forms]의 수정된 버그 {#forms-bugs-fixed}

* AEM Forms Workflow의 작업 할당 단계에서 액션 버튼의 기본값 아이콘을 코랄 아이콘으로 대체할 때 워크플로우가 작동을 멈추고 예외 사항을 기록합니다. 기본값 아이콘을 사용하면 워크플로가 원래대로 작동합니다.
* 레이아웃 레이어에서 열의 수를 바꾸고 레이어 편집기를 열어 패널에서 일부 구성 요소를 드래그하면 적응형 양식 편집기의 콘텐츠 영역에 사각형의 파란색 상자가 나타나기 시작하고 편집기가 응답하지 않습니다.
* 적응형 또는 외부 애셋의 URL 제공과 관련된 규칙 편집기 옵션의 오류 메시지가 너무 길고 사용자 친화적이지 않습니다.


## Cloud Manager {#cloud-manager}

이 섹션에서는 AEM as a Cloud Service 2021.5.0의 Cloud Manager 릴리스 정보에 대해 간략히 소개합니다.

### 릴리스 날짜 {#release-date-cm-may}

AEM as a Cloud Service 2021.5.0의 Cloud Manager 릴리스 날짜는 2021년 5월 6일입니다.
다음 릴리스는 2021년 6월 3일에 예정되어 있습니다.

### 새로운 기능 {#what-is-new-may}

* 이제 PackageOverlap 품질 규칙은 동일한 패키지가 동일한 배포된 패키지 세트에서 여러 포함된 위치에 여러 번 배포된 사례를 검색합니다.

* 이제 공용 API의 저장소 끝점에 Git URL이 포함됩니다.

* Cloud Manager 사용자가 다운로드한 배포 로그는 더 통찰력 있게 작성되며 이제는 실패 및 성공 시나리오에 대한 세부 정보를 포함합니다.

* 이제 코드를 Adobe git으로 푸시하는 동안 발생한 간헐적인 오류가 해결되었습니다.

* 이제 프로그램 편집 워크플로우 동안 샌드박스 프로그램에 상거래 추가 기능을 적용할 수 있습니다.

* 프로그램 편집 경험이 새로 고침되었습니다.

* 환경 세부 사항 페이지의 도메인 이름 테이블에는 페이지 매김을 통해 최대 250개의 도메인 이름이 표시됩니다.

* 프로그램 추가 및 프로그램 편집 워크플로우의 솔루션 탭에는 프로그램에 사용할 수 있는 솔루션이 하나만 있어도 솔루션이 표시됩니다.

* 빌드가 배포된 컨텐츠 패키지를 생성하지 않은 경우 빌드 단계 로그에 오류 메시지가 표시되지 않았습니다.

### 버그 수정 {#bug-fixes-cm-may}

* 경우에 따라 해당 구성이 배포되지 않은 경우에도 IP 허용 목록 옆에 녹색 &quot;활성&quot; 상태가 표시될 수 있습니다.

* 파이프라인 변수 API는 &#39;삭제됨&#39; 변수를 제거하는 대신 상태로만 표시합니다 **삭제됨**.

* 일부 코드 냄새 유형 품질 문제가 안정성 등급에 잘못 영향을 주었습니다.

* 와일드카드 도메인은 지원되지 않으므로 사용자가 와일드카드 도메인을 제출할 수 없도록 UI에서 합니다.

* 자정~오전 1UTC 사이에 파이프라인 실행이 시작되면 Cloud Manager에서 생성한 아티팩트 버전이 전날 작성된 버전보다 클 수 없습니다.

* 샌드박스 프로그램 설정 중에 샘플 코드가 있는 프로젝트가 성공적으로 만들어지면 개요 페이지에서 Git 관리 가 대표 카드의 링크로 표시됩니다.

## 콘텐츠 전송 도구 {#content-transfer-tool}

### 릴리스 날짜 {#release-date-ctt-latest}

컨텐츠 전송 도구 v1.4.6의 릴리스 날짜는 2021년 5월 27일입니다.

### 새로운 기능 {#what-is-new-ctt-latest}

* 사용자에게 Java 실행 파일에 대한 실행 권한이 없는 경우 빠른 시작의 오류 로그에 새 로깅 문이 추가되었습니다.

* 사용자가 추출을 수행한 CTT UI에서 마이그레이션 세트를 삭제하면 `tmp` 해당 마이그레이션 세트와 연결된 폴더가 삭제되어 공간을 저장합니다.

### 버그 수정 {#bug-fixes-ctt-latest}

* 마이그레이션 세트를 삭제할 때 간혹 CTT UI에 도움이 되지 않는 오류 메시지가 표시됩니다. 이 문제가 해결되었습니다.

* 사용자 매핑을 실행하는 동안 사용자에게 타겟 및 호스트에 동일한 이메일 주소가 있지만 다른 사용자 이름이 있는 경우 전체 수집이 실패합니다. 이 문제가 해결되었습니다. 이러한 충돌하는 시나리오에서는 사용자/그룹을 건너뛰고 로그 파일에서 충돌로 기록됩니다.

### 릴리스 날짜 {#release-date-ctt}

컨텐츠 전송 도구 v1.4.0의 릴리스 날짜는 2021년 5월 11일입니다.

### 새로운 기능 {#what-is-new-ctt-may}

* 이 버전의 컨텐츠 전송 도구는 Cloud Service으로 마이그레이션되는 자산에 대한 텍스트 표현물을 만듭니다. 수집된 자산에 대한 전체 텍스트 검색을 지원하려면 텍스트 표현물이 필요합니다.
* 사용자가 만들 수 있는 최대 컨텐츠 전송 도구 마이그레이션 세트 수가 4개에서 10개로 증가했습니다.

### 버그 수정 {#bug-fixes-ctt-may}

* 컨텐츠 전송 도구 UI의 자동 새로 고침 기능과 관련된 여러 버그 수정.
* 컨텐츠 전송 도구 `wipe=true` 타겟에 잘못된 카운터 인덱스가 있습니다. 이 문제가 해결되었습니다.

## 상거래 추가 기능 {#cloud-services-commerce}

### 새로운 기능 {#what-is-new-commerce}

* 제품 콘솔 속성의 관련 콘텐츠에 대한 페이지 매김 지원

### 버그 수정 {#bug-fixes-commerce}

* 제품 속성의 자산 탭에 자산 축소판이 표시되지 않음

* 탐색 표시 는 제품 콘솔에서 미리 보기 데이터를 재설정합니다
