---
title: AEM에서의 디지털 자산 관리를 위한 Assets as a Cloud Service 소개
description: AEM에서의 디지털 자산 관리를 위한 Assets as a Cloud Service 소개
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: f72f72e87dabe89cafc0a56feb35f58ae1a97dfb
workflow-type: tm+mt
source-wordcount: '5078'
ht-degree: 74%

---

# AEM에서의 디지털 자산 관리를 위한 Assets as a Cloud Service 소개 {#assets-as-cloud-service-digital-asset-management-aem}

AEM Assets as a Cloud Service은 비즈니스를 위한 클라우드 기반의 PaaS 솔루션을 제공하여 Digital Asset Management 및 Dynamic Media 작업을 수행할 뿐만 아니라 AI/ML과 같은 차세대 스마트 기능도 사용합니다. 시스템 내에서 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 모든 것이 가능합니다.

Adobe는 디지털 자산을 최대한 활용할 수 있는 강력한 DAM(디지털 자산 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 동일한 클라우드 서비스 저장소를 사용하여 사용자의 요구 사항을 충족시킬 수 있는 두 가지 환경이 있습니다. AEM Assets의 페르소나 기반 경험에 대한 자세한 내용은 [디지털 자산 관리에서 사용 가능한 페르소나 기반 경험](#persona-based-experiences)을 참조하십시오.

AEM Assets Ultimate 및 AEM Assets Prime 서비스에 대한 자세한 내용은 [Assets as a Cloud Service Ultimate](/help/assets/assets-ultimate-overview.md) 및 [Assets as a Cloud Service Prime](/help/assets/assets-prime.md)을 참조합시오.

Adobe 디지털 자산 관리의 주요 기능은 다음과 같습니다.

![add-tags](assets/aem-assets-features-landing-page.png)


>[!BEGINTABS]

>[!TAB 자산 수집]

## 자산 수집 {#asset-ingestion}

일괄 가져오기 기능을 사용하여 Azure, AWS, Google Cloud, Dropbox 및 OneDrive와 같은 데이터 소스에서 Assets as a Cloud Service으로 직접 많은 수의 자산을 가져옵니다.

관리 보기 또는 Assets 보기를 사용하여 일괄 가져오기 작업을 수행할 수 있습니다. Assets 보기는 관리 보기에 비해 더 많은 데이터 소스 옵션을 제공합니다.

웹 브라우저 사용자 인터페이스 외에도 Experience Manager은 데스크탑에서 다른 클라이언트를 지원합니다. 또한 웹 브라우저로 이동할 필요 없이 업로드 환경을 제공합니다.

* Adobe Asset Link를 사용하면 Adobe Photoshop, Adobe Illustrator 및 Adobe InDesign 데스크탑 애플리케이션에서 Experience Manager의 자산에 액세스할 수 있습니다. 열려 있는 문서를 Experience Manager에 업로드할 수 있습니다. 이러한 데스크탑 애플리케이션에 있는 Adobe Asset Link 인터페이스를 통해 직접 액세스할 수 있습니다.

* Experience Manager 데스크탑 앱은 파일 유형 또는 자산을 처리하는 기본 애플리케이션에 관계없이 데스크탑에서 자산 작업을 단순화합니다. 브라우저 업로드는 플랫 파일 목록 업로드만 지원하므로 로컬 파일 시스템에서 중첩된 폴더 계층으로 파일을 업로드하는 것이 유용합니다.

자산 수집 도구에 대한 자세한 설명서는 다음 링크에서 확인하십시오.

<table>
<td>
   <a href="/help/assets/bulk-import-assets-view.md">
   <img alt="일괄 가져오기 도구" src="./assets/bulk-images.jpeg" />
   </a>
   <div>
      <a href="/help/assets/bulk-import-assets-view.md">
      <strong>일괄 가져오기 도구 사용</strong>
      </a>
   </div>
   <p>
      <em>데이터 원본에서 직접 많은 자산을 가져오는 방법을 알아보세요</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/get-started">
   <img alt="AEM 데스크탑 앱 사용" src="./assets/desktop-app-upload.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/get-started">
      <strong>AEM 데스크탑 앱 사용</strong>
      </a>
   </div>
   <p>
      <em>AEM 데스크톱 앱을 사용하여 로컬 파일 시스템에서 중첩된 폴더 계층의 파일을 업로드하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html">
   <img alt="Adobe Asset Link 사용" src="./assets/adobe-asset-link.jpeg" />
   </a>
   <div>
      <a href="https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html">
      <strong>Adobe Asset Link 사용</strong>
      </a>
   </div>
   <p>
      <em>Creative Cloud 애플리케이션을 사용하여 Experience Manager에 자산을 업로드하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

>[!TAB AI 기반 기능]

**스마트 태그**: 스마트 태그는 Adobe Sensei의 AI 프레임워크를 사용하여 태그 구조 및 비즈니스 분류에 대한 이미지 인식 알고리즘을 학습합니다. 이 콘텐츠 인텔리전스는 다른 자산 세트에 관련 태그를 적용하는 데 사용됩니다. AEM은 기본적으로 업로드된 자산에 스마트 태그를 자동 적용합니다.

**지능형 색상 기반 태그 지정 및 검색**: AEM Assets은 Adobe Sensei AI 기능을 사용하여 이미지의 색상을 구분하고 수집 시 이러한 트레이트를 자동으로 태그로 적용합니다. 이러한 태그를 통해 이미지 색상 컴포지션에 따라 향상된 검색 경험이 가능합니다.

**AI 생성 메타데이터**: AEM Assets은 AI를 사용하여 제목, 설명 및 키워드를 포함한 메타데이터를 자동으로 생성합니다. 이러한 AI 생성 필드는 메타데이터의 정확도를 높여 자산을 검색, 분류 및 추천하기 쉽게 만듭니다. 이 접근 방식은 수동 태그 지정을 제거하여 효율성을 향상시킬 뿐만 아니라 방대한 양의 디지털 콘텐츠에 대한 일관성과 확장성을 보장합니다.

**AI 기반 자산 일괄 이름 바꾸기**: [Assets 보기에서 인공 지능을 사용하여 여러 자산의 이름을 한 번에 바꿀 수 있습니다](/help/assets/bulk-rename-assets-view.md). 여러 파일을 한 번에 선택하여 모두 이름을 바꿀 수 있습니다. 대화형 이름 바꾸기 프롬프트 예시에는 *모든 파일을 “my-file”로 변경하고 증가하는 숫자 추가*&#x200B;와 *001, 002 등으로 파일에 접두사 삽입하고 영어로 번역합니다*&#x200B;가 있습니다.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="AEM Assets의 스마트 태그" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong>자산에 AI 스마트 태그 추가</strong>
      </a>
   </div>
   <p>
      <em>업로드된 자산에 스마트 태그를 자동으로 적용하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/color-tag-images.md">
   <img alt="지능형 색상 기반 태그 추가" src="./assets/color-tags.jpg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong>지능형 색상 기반 태그 추가</strong>
      </a>
   </div>
   <p>
      <em>수집 시 색상 기반 태그를 자동으로 적용하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="AI 생성 메타데이터" src="./assets/ai-generated-metadata-landing.jpg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong>AI 생성 메타데이터</strong>
      </a>
   </div>
   <p>
      <em>AI를 사용하여 제목, 설명 등의 자산 메타데이터를 생성합니다. </em>
   </p>
</td>
</table>

**상황별 검색**: AEM Assets을 사용하면 텍스트 프롬프트를 정의하여 저장소에서 사용할 수 있는 에셋을 검색할 수 있습니다. Experience Manager Assets은 텍스트 프롬프트를 검색 필터로 자동 변환하고 검색 결과를 표시합니다. 필터 창을 사용하여 자동 필터를 보고 수정하여 검색 결과의 범위를 더 좁힐 수 있습니다. 대화형 텍스트 프롬프트 예제 중 일부는 다음과 같습니다.

* *해변과 맑은 하늘이 있는 높이 200px, 너비 100px 이상의 이미지* 및
* *1500픽셀 및 2500픽셀 높이의 파랑 하늘 이미지가 필요하며 만료되지 않고 승인된 지난 달에 만들어졌습니다*.

**AEM 내에서 Adobe Firefly를 사용하여 자산 생성**: AEM Assets에서는 검색 쿼리에 대한 결과가 반환되지 않을 경우 Adobe Firefly를 실시간으로 사용하여 자산을 생성할 수 있습니다. 그런 다음 AEM Assets을 사용하면 AEM Assets 사용자 인터페이스 내에서 생성된 이미지를 AEM Assets 저장소로 업로드할 수도 있습니다.

**Adobe Express과 통합**: AEM Assets은 기본적으로 Adobe Express과 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 직접 저장된 자산에 액세스할 수 있습니다. Express 내의 Adobe Firefly 인공 지능을 사용하여 간단한 텍스트 프롬프트를 사용하여 이미지를 생성하고 Express 캔버스에 배치할 수도 있습니다. 그런 다음 새 콘텐츠나 편집한 콘텐츠를 AEM Assets 저장소에 저장할 수 있습니다.

<table>
<td>
   <a href="/help/assets/search-assets-view.md#contextual-search">
   <img alt="상황별 검색" src="./assets/ai-based-search.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#contextual-search">
      <strong>상황별 검색</strong>
      </a>
   </div>
   <p>
      <em>간단한 텍스트 프롬프트를 사용하여 자산을 검색하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md#search-firefly">
   <img alt="Adobe Firefly를 사용하여 자산 생성" src="./assets/adobe-firefly.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#search-firefly">
      <strong>Adobe Firefly를 사용하여 자산 생성</strong>
      </a>
   </div>
   <p>
      <em>Adobe Firefly를 사용하여 실시간으로 자산을 생성합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Adobe Express와 통합" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Adobe Express와 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 사용자 인터페이스 내에서 Adobe Express AI 기능을 사용합니다.</em>
   </p>
</td>
</table>

**스마트 이미징**: 스마트 이미징은 고객의 브라우저 기능에 따라 이미지의 포맷과 파일 크기를 자동으로 최적화하여 이미지 자산 게재 성능을 더욱 향상시킵니다. 기존 이미지 사전 설정과 함께 작동하며 게재 시 인텔리전스를 사용합니다. 이 인텔리전스는 브라우저와 네트워크 연결 속도에 따라 이미지 파일 크기를 더욱 줄여 줍니다.

**스마트 자르기**: 모든 이미지 또는 비디오에서 자동으로 초점을 감지하고 자르기 유지 기능을 제공하는 Adobe Sensei AI 기능입니다. 화면 크기에 상관없이 원하는 관심 지점을 포착하여 번거로운 수작업을 할 필요가 없고, 어떤 디바이스나 화면에서도 보기 좋은 고품질로 빠르게 로딩되는 이미지와 비디오를 제공합니다.

**AI 생성 비디오 캡션**: Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 사용하여 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 이 기능은 정확한 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. 캡션은 원본 오디오, 추가 오디오 트랙 또는 비디오 속성 페이지의 `Captions and Audio` 탭에서 제공된 추가 캡션에서 생성됩니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.
<table>
<td>
   <a href="/help/assets/dynamic-media/imaging-faq.md">
   <img alt="스마트 이미징" src="./assets/smart-imaging.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/imaging-faq.md">
      <strong>스마트 이미징</strong>
      </a>
   </div>
   <p>
      <em>사용자 브라우저 성능과 네트워크 속도에 따라 이미지 포맷과 파일 크기를 최적화합니다.</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/ko/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video">
   <img alt="스마트 자르기" src="./assets/smart-cropping.jpg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/ko/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video">
      <strong>스마트 자르기</strong>
      </a>
   </div>
   <p>
      <em>AI를 사용하여 모든 이미지 또는 비디오에서 자동으로 초점을 감지하고 자르기 하여 유지 관리</em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/video.md">
   <img alt="AI 생성 비디오 캡션" src="./assets/videos-with-captions.jpg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/video.md">
      <strong>AI 생성 비디오 캡션</strong>
      </a>
   </div>
   <p>
      <em>비디오 컨텐츠의 캡션을 자동으로 생성하려면 인공 지능을 사용하십시오. </em>
   </p>
</td>
</table>

>[!TAB 자산 검색]

## 자산 검색 {#asset-discovery}

에셋을 AEM Assets으로 가져온 후에는 이러한 대규모 컬렉션에서 적합한 에셋을 빠르게 찾는 것이 과제입니다.

AEM Assets은 적합한 에셋을 빠르게 찾는 데 도움이 되는 기능을 제공합니다. 이러한 기능에는 AI가 생성한 태그 지정(스마트 태그), 사용자 지정된 메타데이터 및 향상된 검색 기능이 포함됩니다.

**메타데이터 관리**: 자산 관리 여정을 시작할 때 가장 중요한 부분은 메타데이터입니다. 자산이 사용자에게 배포되면 메타데이터 관리는 관리자가 전혀 통제할 수 없게 됩니다. 효과적인 자산 메타데이터는 모든 DAM 도구의 궁극적인 목표이기도 한 더 나은 검색을 보장합니다.


**메타데이터 양식**: Assets as a Cloud Service는 기본적으로 많은 표준 메타데이터 필드를 제공합니다. 추가 메타데이터가 필요하고 비즈니스별 메타데이터를 추가하려면 메타데이터 필드가 더 필요한 경우. 메타데이터 양식을 통해 기업은 자산의 [세부 정보] 페이지에 사용자 정의 메타데이터 필드를 추가할 수 있습니다. 비즈니스별 메타데이터는 자산의 거버넌스 및 검색 기능을 개선합니다. 양식을 처음부터 만들거나 기존 양식의 용도를 변경할 수 있습니다.

<table>
<td>
   <a href="/help/assets/metadata-assets-view.md">
   <img alt="메타데이터 Assets 보기 관리" src="./assets/manage-metadata-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/metadata-assets-view.md">
      <strong>Assets 보기에서 메타데이터 관리</strong>
      </a>
   </div>
   <p>
      <em>Assets 보기를 사용하여 메타데이터와 메타데이터 양식을 관리하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
   <img alt="메타데이터 관리 모범 사례" src="./assets/metadata-best-practices.jpeg" />
   </a>
   <div>
      <a href="https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager-blogs/how-to-manage-metadata-before-and-after-migrating-to-aem-assets/ba-p/744298">
      <strong>메타데이터 관리 모범 사례</strong>
      </a>
   </div>
   <p>
      <em>자산을 AEM으로 마이그레이션하기 전과 후에 메타데이터를 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-metadata.md">
   <img alt="Adobe Asset Link 사용" src="./assets/metadata-management-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-metadata.md">
      <strong>Admin 보기에서 메타데이터 관리</strong>
      </a>
   </div>
   <p>
      <em>관리자 보기를 사용하여 메타데이터 및 메타데이터 양식을 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

**스마트 태그**: 스마트 태그는 Adobe Sensei의 AI 프레임워크를 사용하여 태그 구조 및 비즈니스 분류에 대한 이미지 인식 알고리즘을 학습합니다. 이 콘텐츠 인텔리전스는 다른 자산 세트에 관련 태그를 적용하는 데 사용됩니다. AEM은 기본적으로 업로드된 자산에 스마트 태그를 자동 적용합니다.

**자산 검색**: 적절한 메타데이터가 있으면 AEM Assets에서 다양한 연산자, 와일드카드, 고급 쿼리 및 사용자 정의 필터를 사용하여 검색할 수 있습니다.

**상황별 검색**: AEM Assets는 또한 텍스트 프롬프트를 정의하여 저장소에서 사용 가능한 자산을 검색할 수 있는 상황별 검색 기능을 제공합니다. Experience Manager Assets은 텍스트 프롬프트를 검색 필터로 자동 변환하고 검색 결과를 표시합니다. 필터 창을 사용하여 자동 필터를 보고 수정하여 검색 결과의 범위를 더 좁힐 수 있습니다.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="AEM Assets의 스마트 태그" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong>자산에 스마트 태그 추가</strong>
      </a>
   </div>
   <p>
      <em>업로드된 자산에 스마트 태그를 자동으로 적용하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md">
   <img alt="Assets 보기 검색" src="./assets/search-assets-view-landing.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md">
      <strong>Assets 보기에서 자산 검색</strong>
      </a>
   </div>
   <p>
      <em>상황별 검색을 효과적으로 사용하는 방법과 Assets 보기에서 다른 검색 기능을 사용하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/search-best-practices.md">
   <img alt="모범 사례 검색" src="./assets/search-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-best-practices.md">
      <strong>모범 사례 검색</strong>
      </a>
   </div>
   <p>
      <em>AEM 사용자가 기본 수준부터 고급 수준까지 검색할 수 있도록 지원하기 위한 다양한 시나리오에 대해 알아봅니다.</em>
   </p>
</td>
</table>

>[!TAB 자산 거버넌스]

## 자산 관리 및 거버넌스 {#asset-management-governance}

자산을 AEM Assets에 업로드하고 메타데이터를 설정하여 검색 가능성을 높인 후 사용자 친화적인 Assets 보기 인터페이스를 사용하여 다양한 디지털 자산 관리 작업을 수행할 수 있습니다.

**자산 관리 업무**: 기본 작업에는 검색, 다운로드, 이동, 복사, 이름 바꾸기, 삭제, 업데이트 및 편집 작업이 포함됩니다.

자산 버전을 유지 관리하고, 자산 상태를 설정하며, 자산 만료일을 설정할 수도 있습니다.

**내 Workspace**: Assets 보기에는 위젯을 제공하는 사용자 지정 작업 영역도 포함됩니다. 이러한 위젯은 Assets 사용자 인터페이스의 주요 영역과 사용자와 가장 관련이 있는 정보에 간편하게 액세스할 수 있도록 합니다. 이 페이지는 작업 항목에 대한 개요 및 주요 워크플로에 대한 바로 가기를 제공하는 종합적인 솔루션 역할을 합니다.

**Content Credentials**: AEM Assets가 지원하는 또 다른 강력한 기능은 Content Credentials입니다. 브랜드에 대한 콘텐츠 투명성, AI 공개, 자산 변조 방지가 그 어느 때보다 우려되고 있습니다. Adobe의 Content Authenticity Initiative(CAI)는 Coalition for Content Provenance and Authenticity(C2PA) 기술 표준을 준수하는 도구를 빌드합니다. Content Credentials는 암호화되어 변조 방지 기능을 갖춘 새로운 유형의 메타데이터로, 뷰어들이 콘텐츠의 계보를 이해하고 브랜드 자산의 무결성을 보장하는 데 도움이 될 수 있습니다. 여기에는 디지털 자산의 기록에 대한 인사이트를 제공하는 다양한 출처의 데이터가 포함될 수 있습니다.

<table>
<td>
   <a href="/help/assets/manage-organize-assets-view.md">
   <img alt="자산 관리 작업" src="./assets/asset-management.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-organize-assets-view.md">
      <strong>자산 관리 작업</strong>
      </a>
   </div>
   <p>
      <em>기본 및 고급 자산 관리 작업을 수행하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/my-workspace-assets-view.md">
   <img alt="내 작업 영역" src="./assets/my-workspace.jpeg" />
   </a>
   <div>
      <a href="/help/assets/my-workspace-assets-view.md">
      <strong>내 작업 영역</strong>
      </a>
   </div>
   <p>
      <em>My Workspace을 사용하여 Assets 사용자 인터페이스의 주요 영역에 빠르게 액세스하는 방법에 대해 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/content-credentials.md">
   <img alt="Content Credentials" src="./assets/content-credentials.jpeg" />
   </a>
   <div>
      <a href="/help/assets/content-credentials.md">
      <strong>Content Credentials</strong>
      </a>
   </div>
   <p>
      <em>Content Credentials를 사용하여 디지털 자산의 기록에 대한 인사이트를 얻습니다.</em>
   </p>
</td>
</table>

**컬렉션**: AEM Assets를 사용하면 자산을 컬렉션으로 구성할 수도 있습니다. 컬렉션은 Adobe Experience Manager Assets 보기 내의 에셋, 폴더 또는 기타 컬렉션 세트입니다. 컬렉션을 사용하여 사용자 간에 자산을 공유합니다. 폴더와 달리 컬렉션에는 서로 다른 위치의 자산이 포함될 수 있습니다. 사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 자산에 대한 참조가 포함되어 있습니다. 자산의 참조 무결성은 컬렉션에 간에 유지됩니다.

**알림**: Assets 보기 알림을 사용하여 저장소에서 사용할 수 있는 자산, 폴더 또는 컬렉션에 수행된 작업을 모니터링할 수 있습니다. 알림을 받을 콘텐츠를 선택하고 구독해야 합니다. 알림을 받을 범주를 구성할 수도 있습니다.

**중복 자산 감지**: AEM Assets는 중복 자산 감지도 지원합니다. DAM 사용자가 저장소에 이미 있는 자산을 하나 이상 업로드하는 경우 Experience Manager가 중복을 감지하고 사용자에게 알립니다.



<table>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="컬렉션 관리" src="./assets/manage-collections.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong>컬렉션 관리</strong>
      </a>
   </div>
   <p>
      <em>자산을 효율적으로 공유하기 위해 자산을 컬렉션으로 구성하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/manage-notifications-assets-view.md">
   <img alt="알림 설정" src="./assets/manage-notifications.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-notifications-assets-view.md">
      <strong>알림 설정</strong>
      </a>
   </div>
   <p>
      <em>자산, 폴더 또는 컬렉션에서 수행되는 작업을 모니터링하기 위해 알림을 설정하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/detect-duplicate-assets.md">
   <img alt="중복 자산 감지" src="./assets/duplicate-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/detect-duplicate-assets.md">
      <strong>중복 자산 감지</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets에 업로드된 중복된 자산을 감지하여 사용자에게 알립니다.</em>
   </p>
</td>
</table>

>[!TAB 통합]

## Adobe 및 비 Adobe 애플리케이션과의 통합 {#integration-adobe-non-adode-apps}

AEM Assets는 다양한 Adobe 및 비 Adobe 애플리케이션과 원활하게 통합될 수 있습니다. 사용 가능한 통합에 대한 요약은 다음과 같습니다.

+++**Adobe 및 비 Adobe 애플리케이션과의 통합**

* **OpenAPI 기능이 포함된 Dynamic Media**: [OpenAPI 기능이 포함된 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md)는 포괄적인 [검색](/help/assets/search-assets-api.md) 및 [게재](/help/assets/deliver-assets-apis.md) API 세트를 제공합니다. 이를 통해 개발자는 에셋 전달을 애플리케이션과 쉽게 통합할 수 있습니다. 이러한 애플리케이션에는 Adobe 및 서드파티 애플리케이션이 포함됩니다. 승인된 자산을 검색하고 선택할 수 있는 마이크로 프론트엔드 자산 선택기 사용자 인터페이스를 제공합니다. 선택기는 React JS, Angular JS, Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 쉽게 통합할 수 있습니다.

* **마이크로 프론트엔드 에셋 선택기**: 마이크로 프론트엔드 에셋 선택기는 저장소에서 사용 가능한 디지털 에셋을 찾아보거나 검색할 수 있도록 Experience Manager Assets 리포지토리와 통합되는 사용자 인터페이스를 제공합니다. 그런 다음 애플리케이션 작성 환경에서 사용할 수 있습니다.
자산 선택기를 Adobe 또는 비 Adobe 애플리케이션과 통합할 수 있습니다.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="OpenAPI 기능이 포함된 Dynamic Media 개요" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>OpenAPI 기능이 포함된 Dynamic Media 개요</strong>
      </a>
   </div>
   <p>
      <em>주요 이점 및 활성화 방법을 알아봅니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Experience Manager에서 자산에 대한 액세스 제한" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Experience Manager에서 자산에 대한 액세스 제한</strong>
      </a>
   </div>
   <p>
      <em> 승인된 자산에 대한 액세스를 제한하는 역할을 구성합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="자산 선택기" src="./assets/integration-asset-selector.jpeg" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>마이크로 프론트엔드 자산 선택기</strong>
      </a>
   </div>
   <p>
      <em>마이크로 프론트엔드 자산 선택기를 Adobe 또는 비 Adobe 애플리케이션과 통합하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

+++

+++**Adobe 애플리케이션과 네이티브 통합**

* **Adobe Workfront와 통합**: [!DNL Adobe Workfront]는 업무의 전체 라이프사이클을 한 곳에서 관리할 수 있도록 도와주는 작업 관리 애플리케이션입니다. [!DNL Workfront]와 [!DNL Adobe Experience Manager Assets] 간의 통합을 통해 조직은 작업과 디지털 자산 관리를 본질적으로 연결하여 콘텐츠 제작과 시장 출시 기간을 개선할 수 있습니다. Workfront 작업 관리의 맥락에서 사용자는 필수 문서와 이미지에 액세스할 수 있습니다.

  Adobe는 [ [!DNL Workfront] 및 [!DNL Adobe Experience Manager Assets] 네이티브 통합](https://experienceleague.adobe.com/en/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations)을 제공합니다.

* **Figma와 통합**: AEM Assets은 기본적으로 Figma와 통합되어 디자이너가 Figma 사용자 인터페이스 내에서 AEM Assets에 직접 저장된 자산에 액세스할 수 있습니다. AEM Assets에서 관리하는 컨텐츠를 그림 캔버스에 배치한 다음 AEM Assets 저장소에 새 컨텐츠 또는 편집된 컨텐츠를 저장할 수 있습니다. Figma 커뮤니티 페이지에서 제공되는 AEM Assets Connector에 액세스하려면 [여기](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector)를 클릭하십시오.

* **Adobe Express과 네이티브 통합**: AEM Assets은 기본적으로 Adobe Express과 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 직접 저장된 자산에 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다.

* **AEM Assets을 Creative Cloud에 연결**: Experience Manager Assets은 다른 IMS 조직에서 프로비저닝된 Creative Cloud 권한에 연결할 수 있습니다. 이 기능을 사용하면 Express 및 Creative Cloud Libraries을 포함하여 AEM Assets의 최신 Creative Cloud 통합을 사용할 수 있습니다. Creative Cloud 제품 및 AEM Assets가 별도의 IMS 조직에 프로비저닝된 경우 다른 Creative Cloud 조직에 연결하여 두 솔루션 간의 통합 워크플로를 실행할 수 있습니다.

<table>
<td>
   <a href="/help/assets/workfront-integrations.md">
   <img alt="Adobe Workfront와 통합" src="./assets/integration-adobe-workfront.jpeg" />
   </a>
   <div>
      <a href="/help/assets/workfront-integrations.md">
      <strong>Adobe Workfront와 통합</strong>
      </a>
   </div>
   <p>
      <em>Adobe Workfront와 통합하여 한 곳에서 전체 작업 라이프사이클 관리.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Figma와의 통합" src="./assets/integration-commerce.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong>Figma와의 통합</strong>
      </a>
   </div>
   <p>
      <em>Access Figma 사용자 인터페이스 내의 AEM Assets에 저장된 자산에 액세스</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Adobe Express와의 네이티브 통합" src="./assets/integration-adobe-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Adobe Express와의 네이티브 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 내에서 사용 가능한 자산을 Express 캔버스에 배치하고 업데이트된 자산을 AEM에 저장합니다. </em>
   </p>
</td>


</table>


* **Adobe Journey Optimizer와의 통합**: Adobe Experience Manager Assets를 사용하여 마케팅과 크리에이티브 워크플로를 통합합니다. Adobe Journey Optimizer와 기본적으로 통합되어 Assets as a Cloud Service에 액세스하여 디지털 자산을 저장, 관리, 검색 및 배포할 수 있습니다. 이 통합은 메시지의 내용을 채우는 데 사용할 수 있는 단일 중앙 집중식 자산 저장소 역할을 합니다.

* **Commerce와의 통합**: Adobe Experience Manager(AEM) Assets 통합은 AEM as a Digital Asset Management(DAM) 시스템의 강력한 기능과 Adobe Commerce를 결합하여 전자 상거래 경험을 향상시킵니다. 이러한 기능은 Commerce 프로젝트를 AEM의 강력한 자산 관리 환경에 연결하여 상거래 상점 전반에 걸쳐 자산을 원활하고 확장 가능하며 효율적으로 관리합니다.
* **Edge Delivery Services의 문서 기반 작성 흐름과 AEM Assets 통합**: [!DNL AEM Assets]이(가) [!DNL Microsoft Word] 또는 [!DNL Google Docs]과(와) 같은 문서 기반 작성 도구와 통합되면 작성 도구에 자산 선택기가 제공됩니다. 이 자산 선택기를 사용하여 [!DNL AEM Assets]에 액세스하고 승인된 자산을 콘텐츠에 삽입합니다.
이미 [!DNL Edge Delivery Services] 웹 사이트가 있는 경우 [[!DNL AEM Assets] 플러그인](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) 문서를 참조하여 기존 [!DNL AEM] 프로젝트와 [!DNL AEM Assets]를 통합하는 방법을 알아보십시오.

* **[!DNL Edge Delivery Services]**&#x200B;를 위한 [!DNL Universal Editor] 기반 작성 흐름과 [!DNL AEM Assets] 통합: [!DNL Universal Editor]를 설정하여 [!DNL AEM Assets]와 통합합니다. 이 통합으로 [!DNL Dynamic Media with OpenAPI capabilities]를 사용하여 자산을 게재할 수 있습니다.

   * [!DNL Universal Editor]의 사용자 정의 자산 선택기 기능을 추가하는 방법을 알아보려면 [ [!DNL Edge Delivery] 사이트의 구성](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site)을 참조하십시오. 사용자 정의 자산 선택기를 사용하면 자산을 [!DNL Universal Editor] 콘텐츠에 직접 삽입할 수 있습니다.
   * [에서 작성하는 동안 ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)에 액세스하고 자산을 삽입하는 방법을 알아보려면 [!DNL AEM Assets]확장 개요[!DNL Universal Editor]를 참조하세요.

<table>
<td>
   <a href="https://experienceleague.adobe.com/ko/docs/journey-optimizer/using/content-management/combine/assets">
   <img alt="Adobe Journey Optimizer와 통합" src="./assets/integration-figma.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/ko/docs/journey-optimizer/using/content-management/combine/assets">
      <strong>Adobe Journey Optimizer와 통합</strong>
      </a>
   </div>
   <p>
      <em>AJO와의 통합을 사용하여 마케팅 및 크리에이티브 워크플로 통합</em>
   </p>
</td>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/overview">
   <img alt="Commerce와의 통합" src="./assets/integration-ajo.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/overview">
      <strong>Commerce와의 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets를 Commerce와 통합하여 전자 상거래 경험을 향상시킵니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
   <img alt="AEM Assets를 EDS와 통합" src="./assets/integrate-ue-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
      <strong>AEM Assets를 EDS와 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets를 문서 기반 및 Universal Editor 기반 작성 흐름과 통합합니다.</em>
   </p>
</td>
</table>

+++

>[!TAB 자산 활성화]

## 자산 활성화 {#asset-activation}

강력한 OpenAPI 기능을 포함하여 Content Hub을 Dynamic Media에 사용한 AEM Assets을 통해 디지털 에셋의 잠재력을 최대한 활용할 수 있습니다. AEM Assets는 자산 변환을 간소화하고 다양한 채널에서의 게재를 최적화하도록 설계된 포괄적인 솔루션 제품군을 제공합니다.

+++**Content Hub**

Content Hub는 Experience Manager Assets as a Cloud Service의 일부로 제공되며, 이를 통해 조직과 비즈니스 파트너는 브랜드 콘텐츠를 더 간편하게 이용할 수 있습니다. 대규모 활성화를 위한 자산을 배포하고 마케팅 민첩성을 개선하기 위한 온브랜드 콘텐츠 변형을 만드는 데 중점을 둡니다.

Content Hub는 다음과 같은 주요 이점을 제공합니다.

* **직관적인 포털에서 사용할 수 있는 모든 브랜드 승인 자산 찾기 및 공유**: AEM Assets는 단일 정보 소스 역할을 하며, 모든 승인된 자산은 검색 환경을 개선하기 위해 Content Hub에서 평면 계층 구조로 자동 제공됩니다.

* **구성 가능한 사용자 인터페이스**: 검색 필터, 자산을 추가하거나 가져오는 동안 사용할 수 있는 필드, 자산 속성, 브랜딩용 배너 콘텐츠 등 Content Hub 내에서 가장 일반적인 속성을 구성할 수 있으며 관리자가 요구 사항에 따라 Content Hub 사용자 인터페이스를 쉽게 구성할 수 있습니다.

* **비창의적인 사용자 또한 브랜드를 유지하면서 콘텐츠를 편집하고 리믹스할 수 있도록 지원**: Content Hub를 사용하여 Adobe Express로 새 콘텐츠를 만들 수 있습니다(Adobe Express 권한이 있는 경우). 사용하기 쉬운 도구로 기존 콘텐츠를 편집하고, 템플릿과 브랜드 요소로 브랜드에 맞는 변형을 만들고, Adobe Firefly의 최신 생성형 AI 기능으로 새로운 콘텐츠를 만들 수 있습니다.

* **팀 전체의 콘텐츠 사용 방식에 대한 인사이트 확보**: [!DNL Content Hub]는 자산에 대한 귀중한 인사이트를 제공하여 마케팅 관련자들이 자주 직면하는 일반적인 문제인 마케팅 캠페인, 채널 및 다양한 지역에서 사용되는 자산 사용 통계를 해결합니다. 자산의 성과와 인기를 명확하게 이해함으로써 사용자 경험 향상에 필수적인 실행 가능한 인사이트를 제공합니다.

<table>
<td>
   <a href="/help/assets/product-overview.md">
   <img alt="Content Hub 개요" src="./assets/content-hub-overview.jpeg" />
   </a>
   <div>
      <a href="/help/assets/product-overview.md">
      <strong>Content Hub 개요</strong>
      </a>
   </div>
   <p>
      <em>Content Hub와, 주요 이점과 액세스 방법에 대해 알아봅니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Content Hub 사용자 인터페이스 구성" src="./assets/content-hub-configuration.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
      <strong>Content Hub 사용자 인터페이스 구성</strong>
      </a>
   </div>
   <p>
      <em>Content Hub 사용자 인터페이스에서 사용 가능한 옵션을 구성하는 방법에 대해 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Adobe Express를 사용하여 편집" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong>Adobe Express를 사용하여 편집</strong>
      </a>
   </div>
   <p>
      <em>Adobe Express를 사용하여 Content Hub에서 이미지를 편집하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

+++

+++**Dynamic Media**

Dynamic Media는 풍부한 비주얼 머천다이징 및 마케팅 자산을 온디맨드로 게재할 수 있게 합니다. 또한 확대/축소, 360도 회전, 비디오 등 대화형 시청 환경을 만들고 제공하는 데 도움이 됩니다. 자산을 웹, 모바일 및 소셜 사이트에서 소비할 수 있도록 동적으로 확정합니다. 이미지, 비디오, 3D 등 기본 소스 자산 세트를 사용하면 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 CDN(콘텐츠 전송 네트워크)을 통해 실시간으로 다양한 유형의 풍부한 콘텐츠를 생성하고 전달합니다

Dynamic Media는 다음과 같은 주요 기능을 제공합니다.

* **스마트 이미징**: 스마트 이미징은 고객의 브라우저 기능에 따라 이미지의 포맷과 파일 크기를 자동으로 최적화하여 이미지 자산 게재 성능을 더욱 향상시킵니다. 기존 이미지 사전 설정과 함께 작동하며 게재 시 인텔리전스를 사용합니다. 이 인텔리전스는 브라우저와 네트워크 연결 속도에 따라 이미지 파일 크기를 더욱 줄여 줍니다.

* **적응형 비디오 세트**: 적응형 비디오 세트는 동일한 비디오 버전을 서로 다른 비트 전송률과 포맷으로 인코딩하여 그룹화합니다. 먼저 시스템에 업로드한 원본 기본 비디오부터 시작합니다. Dynamic Media는 자동으로 해당 비디오의 크기를 조정하거나 여러 비디오로 변환합니다. 그런 다음 게재 시 어떤 비디오 화면, 어떤 품질, 어떤 포맷을 사용할지 지능적으로 결정하여 휴대폰, 태블릿 또는 데스크탑 컴퓨터에 전달합니다.

* **스마트 자르기**: 이미지나 비디오에서 초점을 자동으로 감지하고 이를 유지하기 위해 자르는 Adobe Sensei AI 기능. 화면 크기에 상관없이 원하는 관심 지점을 포착하여 번거로운 수작업을 할 필요가 없고, 어떤 디바이스나 화면에서도 보기 좋은 고품질로 빠르게 로딩되는 이미지와 비디오를 제공합니다.

* **Dynamic Media 템플릿**: WYSIWYG 템플릿 편집기인 Dynamic Media 템플릿을 사용하여 배너와 전단지에 맞는 실시간 사용자 정의 템플릿을 만듭니다. Dynamic Media 템플릿을 게시하고 다운스트림 애플리케이션에서 사용합니다. Dynamic Media 템플릿에는 이미지와 텍스트 레이어가 포함됩니다. 템플릿의 이미지 및 텍스트 레이어에 매개변수를 추가하고 Dynamic Media URL을 사용하여 레이어의 위치를 변경하고 크기를 조정한 후 실시간으로 콘텐츠를 업데이트합니다.

* **다중 오디오 및 캡션**: 기본 비디오에 여러 개의 캡션과 여러 개의 오디오 트랙을 추가합니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 캡션 및 오디오 트랙을 관리할 수도 있습니다.

* **DASH(Dynamic Adaptive Streaming over HTTP) 지원**: Dynamic Media는 Dynamic Media 비디오 게재(CMAF가 활성화됨)에서 적응형 스트리밍을 지원하므로 비디오를 더 잘 볼 수 있습니다. DASH는 적응형 비디오 스트리밍을 위한 국제 표준 프로토콜이며 업계에서 널리 채택되고 있습니다.

* **AI 생성 비디오 캡션**: Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 사용하여 비디오 콘텐츠에 대한 캡션을 자동으로 생성합니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.

사용 가능한 Dynamic Media 서비스에 대한 정보는 [Dynamic Media Prime 및 Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md)을 참조하십시오.



<table>
<td>
   <a href="/help/assets/dynamic-media/dynamic-media.md">
   <img alt="Dynamic Media를 사용하여 작업" src="./assets/work-with-dynamic-media.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dynamic-media.md">
      <strong>Dynamic Media를 사용하여 작업</strong>
      </a>
   </div>
   <p>
      <em>웹, 모바일, 소셜 사이트에서 소비할 수 있도록 자산을 게재하는 방법을 알아봅니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/dynamic-media/dm-journey-part1.md">
   <img alt="Dynamic Media 여정" src="./assets/dm-journey.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-journey-part1.md">
      <strong>Dynamic Media 여정</strong>
      </a>
   </div>
   <p>
      <em>Dynamic Media가 업무에 어떻게 가치를 더하는지 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media/dm-best-practices.md">
   <img alt="AEM Assets를 Creative Cloud에 연결" src="./assets/dm-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dm-best-practices.md">
      <strong>Dynamic Media 모범 사례</strong>
      </a>
   </div>
   <p>
      <em>이미지, 비디오 및 뷰어로 작업할 때의 모범 사례.</em>
   </p>
</td>
</table>

+++

+++**OpenAPI 기능이 포함된 Dynamic Media**

빠르게 변화하는 오늘날의 디지털 세계에서 브랜드 디지털 자산의 잠재력을 최대한 활용하는 것은 경쟁에서 앞서 나가기 위해 매우 중요합니다. 총체적인 디지털 자산 관리(DAM) 솔루션은 자산 거버넌스를 촉진하고, 브랜드 일관성을 촉진하며, 콘텐츠 게재를 가속화하는 동시에 브랜드 무결성과 탁월한 고객 경험을 보장합니다.

OpenAPI 기능 포함 Dynamic Media는 민첩하고 효율적인 콘텐츠 공급망 생태계의 핵심에 DAM을 배치하여 자산 거버넌스와 게재를 보장합니다.

OpenAPI 기능이 포함된 Dynamic Media는 다음과 같은 주요 이점을 제공합니다.

* **원활한 통합**: OpenAPI 기능이 포함된 Dynamic Media는 포괄적인 검색 및 게재 API 세트를 제공합니다. 이를 통해 개발자는 쉽게 [자산 배달을 해당 애플리케이션과 통합](/help/assets/integrate-dynamic-media-open-apis.md)할 수 있습니다. 이러한 애플리케이션에는 Adobe 및 서드파티 애플리케이션이 포함됩니다. 승인된 자산을 검색하고 선택할 수 있는 [마이크로 프론트엔드 자산 선택기 사용자 인터페이스](/help/assets/overview-asset-selector.md)를 제공합니다. 선택기는 React JS, Angular JS, Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 쉽게 통합할 수 있습니다.

* **디지털 자산의 중앙 관리**: DAM은 모든 디지털 자산에 대한 단일 정보 소스입니다. 디지털 자산은 AEM Assets에서 중앙 집중식으로 관리되며, 자산 바이너리를 복사하지 않고 게재 URL을 사용한 참조를 통해 소비 애플리케이션에 전달됩니다.

* **실시간 업데이트**: 버전 업데이트 및 메타데이터 수정을 포함하여 DAM에서 승인된 자산에 대한 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 갖춘 Dynamic Media에 대해 10분이라는 짧은 TTL(Time-to-Live) 값을 구성하면 모든 작성 및 게시 인터페이스에서 10분 이내에 업데이트가 표시됩니다.

* **브랜드 일관성**: [브랜드 승인 자산](/help/assets/approve-assets.md)만 다운스트림 애플리케이션에 노출됩니다. [브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 통제권을 유지합니다](/help/assets/restrict-assets-delivery.md). 모든 채널 및 애플리케이션에서 브랜드 일관성을 보장하기 위해 승인된 최신 버전의 자산만 사용할 수 있습니다.

* **웹에 최적화된 게재**: 디지털 자산은 웹에 최적화된 포맷으로 제공되어 디지털 경험의 핵심 웹 바이탈을 향상시킵니다. 이 최적화는 이미지에 대한 WebP 렌디션, 비디오에 대한 HLS 또는 DASH 프로토콜을 통한 적응형 스트리밍 및 문서에 대한 원본 렌디션을 지원합니다.

* **동적 자산 변환**: 시스템에서 이미지 수정자로 알려진 URL 매개 변수를 사용하여 즉시 이미지 변환을 허용합니다. [예: 폭, 높이, 회전, 뒤집기, 품질, 자르기, 포맷 및 스마트 자르기](/help/assets/deliver-assets-apis.md). 변환된 렌디션은 동적으로 생성되며 CDN을 통해 원활하게 게재됩니다.

* **자산의 안전한 게재**: OpenAPI 기능 포함 Dynamic Media는 디지털 자산에 대한 액세스를 제어할 수 있는 메커니즘을 제공합니다. 보안 대상 자산의 메타데이터로 사용자 역할 또는 그룹을 지정하고 [승인된 사용자만 이러한 자산에 액세스](/help/assets/restrict-assets-delivery.md)할 수 있는 사전 정의 기간을 설정할 수 있습니다. 보안 자산의 게재 URL은 제한된 기간 동안 승인되지 않은 사용자가 접근할 수 없습니다.

사용 가능한 Dynamic Media 서비스에 대한 정보는 [Dynamic Media Prime 및 Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md)을 참조하십시오.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="OpenAPI 기능이 포함된 Dynamic Media 개요" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>OpenAPI 기능이 포함된 Dynamic Media 개요</strong>
      </a>
   </div>
   <p>
      <em>주요 이점 및 활성화 방법을 알아봅니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Experience Manager에서 자산에 대한 액세스 제한" src="./assets/restrict-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Experience Manager에서 자산에 대한 액세스 제한</strong>
      </a>
   </div>
   <p>
      <em> 승인된 자산에 대한 액세스를 제한하는 역할을 구성합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="원격 AEM Assets를 AEM Sites와 통합" src="./assets/integration-aem-sites.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
      <strong>원격 AEM Assets를 AEM Sites와 통합</strong>
      </a>
   </div>
   <p>
      <em>원격 AEM Assets를 AEM Sites 환경과 통합합니다. </em>
   </p>
</td>
</table>

+++

>[!TAB Insights]

## Asset Insights {#asset-insights}

자산 보고는 관리자가 Adobe Experience Manager Assets 보기 환경의 활동을 조회할 수 있도록 해 줍니다. 이 데이터는 사용자가 콘텐츠 및 제품과 상호 작용하는 방법에 대한 유용한 정보를 제공합니다. 모든 사용자는 Insights 대시보드에 액세스할 수 있으며 관리자의 제품 프로필에 할당된 사용자는 사용자 정의 보고서를 만들 수 있습니다.

업로드, 다운로드, Dynamic Media 게재 등 다양한 유형의 보고서를 생성할 수 있습니다.

* **Assets 보기의 인사이트**: Assets 보기를 통해 인사이트 대시보드에서 Assets 보기 환경에 대한 실시간 데이터를 볼 수 있습니다. 지난 30일 동안 또는 지난 12개월 동안의 실시간 이벤트 지표를 볼 수 있습니다. 이벤트에는 다운로드, 업로드, 저장 공간 사용량, 인기 검색어, 크기별 자산 수, 자산 유형별 자산 수가 포함됩니다.

* **Admin 보기에서 Adobe Analytics 통합**: Assets Insights 기능을 사용하여 서드파티 웹 사이트, 마케팅 캠페인, Adobe의 크리에이티브 솔루션에 사용되는 이미지의 사용자 평가와 사용 통계를 추적할 수 있습니다. 이는 이미지의 성능 및 인기에 대한 통찰력을 제공하는 데 도움이 됩니다. Assets Insights는 이미지가 평가된 횟수, 클릭된 횟수, 노출 횟수(웹 사이트에 이미지가 로드된 횟수) 등 사용자 활동 세부 정보를 수집합니다. 이 통계를 바탕으로 이미지에 점수를 부여합니다. 점수와 성과 통계를 활용해 카탈로그, 마케팅 캠페인 등에 포함할 인기 있는 이미지를 선택할 수 있습니다. 이러한 통계를 기반으로 보관 및 라이선스 갱신 정책을 수립할 수도 있습니다. Assets Insights에 자산 사용 통계를 표시하려면 먼저 Adobe Analytics에서 보고 데이터를 가져오도록 기능을 구성합니다.

* **Content Hub 인사이트**: Content Hub는 자산에 대한 귀중한 인사이트를 제공하여 마케팅 관련자들이 자주 직면하는 일반적인 문제인 마케팅 캠페인, 채널 및 다양한 지역에서 사용되는 자산 사용 통계를 해결합니다. 자산의 성과와 인기를 명확하게 이해함으로써 사용자 경험 향상에 필수적인 실행 가능한 인사이트를 제공합니다.

<table>
<td>
   <a href="/help/assets/manage-reports-assets-view.md">
   <img alt="Assets 보기에서 태그 관리" src="./assets/assets-insights-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-reports-assets-view.md">
      <strong>Assets 보기에서 태그 관리</strong>
      </a>
   </div>
   <p>
      <em>Assets 보기를 사용하여 주요 성공 지표에 대한 인사이트를 얻습니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/asset-reports.md">
   <img alt="Admin 보기에서 태그 관리" src="./assets/assets-insights-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/asset-reports.md">
      <strong>Admin 보기에서 태그 관리</strong>
      </a>
   </div>
   <p>
      <em>관리자 보기에서 Adobe Analytics 통합 보고서를 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Content Hub의 Assets Insights" src="./assets/asset-insights-content-hub.jpeg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      <strong>Content Hub의 Assets Insights</strong>
      </a>
   </div>
   <p>
      <em>Content Hub에서 자산 인사이트를 보는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

>[!ENDTABS]

## 디지털 자산 관리에 대해 사용 가능한 페르소나 기반 경험 {#persona-based-experiences}

Adobe는 디지털 자산을 최대한 활용할 수 있는 강력한 DAM(디지털 자산 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 동일한 클라우드 서비스 저장소를 사용하는 서로 다른 두 가지 환경이 있습니다.

* **Admin 보기**: 기존의 Assets as a Cloud Service 사용자 인터페이스입니다. 통합, 워크플로우, 콘텐츠 자동화, 게시 등을 포함한 모든 고급 디지털 에셋 관리 기능에 대해 관리 보기를 사용하십시오.

* **Assets 보기**: 디지털 자산을 저장, 관리, 검색 및 사용할 수 있는 가벼운 버전의 Adobe 자산 관리 경험입니다. 필수 디지털 자산 관리 기능이 포함된 간소화된 사용자 인터페이스입니다. 업로드, 메타데이터 관리, 검색, 다운로드 및 공유에 중점을 둔 가벼운 버전의 DAM 사용자를 위해 설계되었습니다.

![add-tags](assets/newui-overview.svg)

관리Admin보기에 대한 액세스 권한이 있는 사용자는 Assets 보기에도 액세스할 수 있습니다. Assets View는 디지털 에셋을 쉽게 관리, 검색 및 배포할 수 있도록 해주는 간소화된 사용자 인터페이스를 제공합니다. 크리에이티브, 마케팅 및 사업 부문 팀을 비롯한 다양한 기능의 광범위한 사용자가 에셋에 대해 공동 작업을 수행하고 필요한 시간과 장소에서 올바른 승인된 에셋에 액세스할 수 있습니다. 많은 일반 DAM 사용자는 기능의 하위 집합만 포함하는 Assets 보기를 선호합니다. 이 경험은 크리에이티브, 읽기 전용 자산 소비자 및 더 가벼운 DAM 사용자를 대상으로 합니다.

DAM 라이브러리 관리자, 개발자 및 상위 사용자는 계속해서 Admin 보기를 사용하거나 필요에 따라 사용자 인터페이스 간에 전환할 수 있습니다. 역할에 가장 적합한 환경을 선택할 수 있습니다.

Assets 보기에 액세스하는 방법과 관리자 보기를 통해 제공되는 몇 가지 간단한 사항에 대한 자세한 내용은 [Assets 보기 소개](/help/assets/assets-view-introduction.md)를 참조하십시오.

## AEM의 AI 지원

[필수 조건을 완료](/help/implementing/cloud-manager/ai-assistant-in-aem.md#get-access)한 고객의 경우 AEM의 AI 도우미를 해당 조직의 사용자가 사용할 수 있습니다. AEM의 [AI 길잡이](/help/implementing/cloud-manager/ai-assistant-in-aem.md)를 참조하세요.
