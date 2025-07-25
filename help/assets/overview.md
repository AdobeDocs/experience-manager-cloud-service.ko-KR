---
title: AEM의 디지털 에셋 관리를 위한 Assets as a Cloud Service 소개
description: AEM의 디지털 에셋 관리를 위한 Assets as a Cloud Service 소개
source-git-commit: 707c2125b3a5401cd5b0ebe19f3bc9c46302b697
workflow-type: tm+mt
source-wordcount: '5032'
ht-degree: 29%

---


# AEM의 디지털 에셋 관리를 위한 Assets as a Cloud Service 소개 {#assets-as-cloud-service-digital-asset-management-aem}

Adobe Experience Manager Assets as a Cloud Service는 클라우드 기반의 비즈니스용 PaaS 솔루션을 제공하여 빠르고 효과적으로 디지털 자산 관리 및 Dynamic Media 작업을 수행할 뿐만 아니라 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에서 AI/ML과 같은 차세대 스마트 기능도 사용합니다.

Adobe는 디지털 자산을 최대한 활용할 수 있는 강력한 DAM(디지털 자산 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 요구 사항에 맞게 동일한 Cloud Services 저장소를 사용하는 두 개의 별도 경험이 있습니다. AEM Assets의 사용자 기반 경험에 대한 자세한 내용은 [디지털 자산 관리에 사용 가능한 사용자 기반 경험](#persona-based-experiences)을 참조하십시오.

AEM Assets Ultimate 및 AEM Assets Prime 오퍼링에 대한 자세한 내용은 [Assets as a Cloud Service Ultimate](/help/assets/assets-ultimate-overview.md) 및 [Assets as a Cloud Service Prime](/help/assets/assets-prime.md)를 참조하십시오.

Adobe 디지털 자산 관리의 주요 기능 중 일부는 다음과 같습니다.

![add-tags](assets/aem-assets-features-landing-page.png)


>[!BEGINTABS]

>[!TAB 자산 수집]

## 에셋 수집 {#asset-ingestion}

일괄 가져오기 기능을 사용하여 Azure, AWS, Google Cloud, Dropbox 및 OneDrive와 같은 데이터 소스에서 Assets as a Cloud Service으로 직접 많은 수의 자산을 가져옵니다.

관리 보기 또는 Assets 보기를 사용하여 일괄 가져오기 작업을 수행할 수 있습니다. Assets 보기는 관리자 보기에 비해 더 많은 데이터 소스 옵션을 제공합니다.

웹 브라우저 사용자 인터페이스 외에도 Experience Manager은 데스크탑에서 다른 클라이언트를 지원합니다. 또한 웹 브라우저로 이동할 필요 없이 업로드 환경을 제공합니다.

* Adobe Asset Link는 Adobe Photoshop, Adobe Illustrator 및 Adobe InDesign 데스크톱 애플리케이션에서 Experience Manager의 자산에 대한 액세스를 제공합니다. 이러한 데스크탑 애플리케이션 내에서 Adobe Asset Link 사용자 인터페이스에서 현재 열려 있는 문서를 Experience Manager에 직접 업로드할 수 있습니다.

* Experience Manager 데스크탑 앱은 파일 유형 또는 자산을 처리하는 기본 애플리케이션에 관계없이 데스크탑에서 자산 작업을 단순화합니다. 브라우저 업로드는 플랫 파일 목록 업로드만 지원하므로 로컬 파일 시스템에서 중첩된 폴더 계층의 파일을 업로드하는 것이 유용합니다.

다음 링크를 사용하여 이러한 에셋 수집 도구에 대한 자세한 설명서에 액세스합니다.

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
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using">
   <img alt="AEM 데스크탑 앱 사용" src="./assets/desktop-app-upload.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using">
      <strong>AEM 데스크톱 앱 사용</strong>
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
      <strong>Adobe 자산 링크 사용</strong>
      </a>
   </div>
   <p>
      <em>Creative Cloud 애플리케이션을 사용하여 Experience Manager에 에셋을 업로드하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

>[!TAB AI 기반 기능]

**스마트 태그**: 스마트 태그는 Adobe Sensei의 인공 지능 프레임워크를 사용하여 태그 구조 및 비즈니스 분류에 대한 이미지 인식 알고리즘을 교육합니다. 그런 다음 이 콘텐츠 인텔리전스를 사용하여 다른 에셋 세트에 관련 태그를 적용합니다. AEM은 기본적으로 업로드된 에셋에 스마트 태그를 자동으로 적용합니다.

**지능형 색상 기반 태그 지정 및 검색**: AEM Assets은 Adobe Sensei AI 기능을 사용하여 이미지의 색상을 구분하고 수집 시 이러한 색상을 자동으로 태그로 적용합니다. 이러한 태그를 사용하면 이미지 색상 구성에 따라 향상된 검색 환경을 사용할 수 있습니다.

**AI 생성 메타데이터**: AEM Assets은 AI를 사용하여 제목, 설명 및 키워드를 포함한 메타데이터를 자동으로 생성합니다. 이러한 AI 생성 필드는 메타데이터의 정확도를 높여 자산을 검색, 분류 및 추천하기 쉽게 만듭니다. 이 접근 방식은 수동 태그 지정을 제거하여 효율성을 향상시킬 뿐만 아니라 방대한 양의 디지털 콘텐츠에 대한 일관성과 확장성을 보장합니다.

**AI 기반 에셋 일괄 이름 바꾸기**: [Assets 보기를 사용하면 인공 지능을 사용하여 여러 에셋의 이름을 한 번에 바꿀 수 있습니다](/help/assets/bulk-rename-assets-view.md). 여러 파일을 한 번에 선택하고 이름을 모두 바꿀 수 있습니다. 일부 대화 이름 바꾸기 프롬프트에는 *모든 파일을 &#39;my-file&#39;로 변경하고 증분 번호를 추가합니다* 및 *001, 002 등으로 파일 접두사를 추가합니다. 영어로 번역*&#x200B;합니다.

<table>
<td>
   <a href="/help/assets/smart-tags.md">
   <img alt="AEM Assets의 스마트 태그" src="./assets/smart-tags-ai.jpeg" />
   </a>
   <div>
      <a href="/help/assets/smart-tags.md">
      <strong>에셋에 AI 스마트 태그 추가</strong>
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
      <em>수집 시 색상 기반 태그를 자동으로 적용하는 방법에 대해 알아봅니다.</em>
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
      <em>AI를 사용하여 제목 및 설명 같은 에셋 메타데이터를 생성합니다. </em>
   </p>
</td>
</table>

**상황별 검색**: AEM Assets에서는 텍스트 프롬프트를 정의하여 저장소에서 사용할 수 있는 에셋을 검색할 수 있습니다. Experience Manager Assets는 해당 텍스트 프롬프트를 검색 필터로 자동 변환하고 검색 결과를 표시합니다. 필터 창을 사용하여 자동 필터를 보고 수정하여 검색 결과의 범위를 좁힐 수 있습니다. 대화형 텍스트 프롬프트 예제 중 일부는 *높이가 200px 이상이고 너비가 100px이고 하늘이 맑음* 및 *1500 및 2500픽셀 높이이며 만료되지 않고 승인된 지난 달에 만든 푸른 하늘의 이미지가 필요합니다*.

**AEM 내에서 Adobe Firefly을 사용하여 에셋 생성**: AEM Assets을 사용하면 검색 쿼리에서 결과를 반환하지 않는 경우 Adobe Firefly을 실시간으로 사용하여 에셋을 생성할 수 있습니다. AEM Assets을 사용하면 AEM Assets 사용자 인터페이스 내에서 생성된 이미지를 AEM Assets 저장소로 업로드할 수도 있습니다.

**Adobe Express과 통합**: AEM Assets은 기본적으로 Adobe Express과 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. 또한 Express 내의 Adobe Firefly Artifical Intelligence를 사용하여 간단한 텍스트 프롬프트를 사용하여 이미지를 생성하고 Express 캔버스에 배치할 수 있습니다. 그런 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다.

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
      <em>간단한 텍스트 프롬프트를 사용하여 에셋을 검색하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-view.md#search-firefly">
   <img alt="Adobe Firefly을 사용하여 에셋 생성" src="./assets/adobe-firefly.jpg" />
   </a>
   <div>
      <a href="/help/assets/search-assets-view.md#search-firefly">
      <strong>Adobe Firefly을 사용하여 에셋 생성</strong>
      </a>
   </div>
   <p>
      <em>Adobe Firefly을 사용하여 실시간으로 자산을 생성합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Adobe Express와 통합" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Adobe Express과 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 사용자 인터페이스 내에서 Adobe Express AI 기능을 사용합니다.</em>
   </p>
</td>
</table>

**스마트 이미징**: 스마트 이미징은 고객의 브라우저 기능에 따라 이미지의 형식과 파일 크기를 자동으로 최적화하여 더 나은 이미지 에셋 전달 성능을 제공합니다. 기존 이미지 사전 설정에서 작동하며 전달 시 인텔리전스를 사용합니다. 이 인텔리전스는 브라우저 및 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다.

**스마트 자르기**: 모든 이미지 또는 비디오에서 초점을 자동으로 감지하고 자르기 방식으로 유지하는 Adobe Sensei AI 기능입니다. 화면 크기에 상관없이 의도한 관심 영역을 캡처하므로 번거로운 수작업을 없애고 모든 장치 또는 화면에서 보기 좋은 고품질의 빠른 로딩 이미지 및 비디오를 제공합니다.

**AI 생성 비디오 캡션**: Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 사용하여 비디오 컨텐츠의 캡션을 자동으로 생성합니다. 이 기능은 정확한 캡션을 제공하여 접근성을 개선하고 사용자 경험을 향상시킬 수 있도록 설계되었습니다. 원본 오디오, 추가 오디오 트랙 또는 추가 캡션은 비디오 속성 페이지의 `Captions and Audio` 탭에서 생성됩니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.
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
      <em>사용자의 브라우저 기능 및 네트워크 속도에 따라 이미지의 형식과 파일 크기를 최적화합니다.</em>
   </p>
</td>


<td>
   <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html">
   <img alt="스마트 자르기" src="./assets/smart-cropping.jpg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html">
      <strong>스마트 자르기</strong>
      </a>
   </div>
   <p>
      <em>AI를 사용하여 이미지 또는 비디오에서 초점을 자동으로 감지하고 자르기 하여 유지 관리</em>
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

AEM Assets은 AI 생성 태그 지정(스마트 태그), 사용자 지정된 메타데이터 및 검색 환경을 향상시키는 기능과 같이 빠른 시일 내에 적절한 에셋으로 이동할 수 있도록 하는 기능을 제공합니다.

**메타데이터 관리**: 메타데이터는 에셋 관리 여정을 시작하는 동안 가장 중요한 측면입니다. 에셋이 사용자에게 배포되면 메타데이터 관리는 관리자의 제어를 완전히 벗어납니다. 효과적인 에셋 메타데이터는 더 나은 검색을 보장하며, 이는 모든 DAM 도구의 궁극적인 목적지입니다.


**메타데이터 Forms**: Assets as a Cloud Service은 기본적으로 많은 표준 메타데이터 필드를 제공합니다. 추가 메타데이터 요구 사항이 있고 비즈니스별 메타데이터를 추가하려면 더 많은 메타데이터 필드가 필요한 경우. 메타데이터 양식을 통해 기업은 자산의 [세부 정보] 페이지에 사용자 정의 메타데이터 필드를 추가할 수 있습니다. 비즈니스별 메타데이터는 자산의 거버넌스 및 검색 기능을 개선합니다. 양식을 처음부터 만들거나 기존 양식의 용도를 변경할 수 있습니다.

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
      <em>Assets 보기를 사용하여 메타데이터 및 메타데이터 양식을 관리하는 방법을 알아봅니다.</em>
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
      <em>자산을 AEM으로 마이그레이션하기 전후에 메타데이터를 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-metadata.md">
   <img alt="Adobe Asset Link 사용" src="./assets/metadata-management-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-metadata.md">
      <strong>관리자 보기에서 메타데이터 관리</strong>
      </a>
   </div>
   <p>
      <em>관리 보기를 사용하여 메타데이터 및 메타데이터 양식을 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

**스마트 태그**: 스마트 태그는 Adobe Sensei의 인공 지능 프레임워크를 사용하여 태그 구조 및 비즈니스 분류에 대한 이미지 인식 알고리즘을 교육합니다. 그런 다음 이 콘텐츠 인텔리전스를 사용하여 다른 에셋 세트에 관련 태그를 적용합니다. AEM은 기본적으로 업로드된 에셋에 스마트 태그를 자동으로 적용합니다.

**에셋 검색**: 적절한 메타데이터가 준비되면 AEM Assets에서 다양한 연산자, 와일드카드, 고급 쿼리 및 사용자 지정 필터를 사용하여 검색할 수 있습니다.

**컨텍스트 검색**: AEM Assets에서는 텍스트 프롬프트를 정의하여 저장소에서 사용할 수 있는 에셋을 검색할 수 있는 컨텍스트 검색 기능도 제공합니다. Experience Manager Assets는 해당 텍스트 프롬프트를 검색 필터로 자동 변환하고 검색 결과를 표시합니다. 필터 창을 사용하여 자동 필터를 확인하여 수정하고 검색 결과의 범위를 더 좁힐 수 있습니다.

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
      <em>Assets 보기에서 컨텍스트 검색 및 기타 검색 기능을 효과적으로 사용하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/search-best-practices.md">
   <img alt="모범 사례 검색" src="./assets/search-best-practices.jpeg" />
   </a>
   <div>
      <a href="/help/assets/search-best-practices.md">
      <strong>검색 모범 사례</strong>
      </a>
   </div>
   <p>
      <em>AEM 사용자가 기본 수준부터 고급 수준까지 검색할 수 있도록 지원하는 다양한 시나리오를 설명합니다.</em>
   </p>
</td>
</table>

>[!TAB 자산 거버넌스]

## 자산 관리 및 거버넌스 {#asset-management-governance}

에셋을 AEM Assets에 업로드하고 더 나은 검색 기능을 위해 메타데이터를 설정한 후에는 Assets 보기의 사용자 친화적인 인터페이스를 사용하여 다양한 디지털 에셋 관리 작업을 수행할 수 있습니다.

**자산 관리 작업**: 일부 기본 작업에는 검색, 다운로드, 이동, 복사, 이름 변경, 삭제, 업데이트 및 편집 작업이 포함됩니다.

에셋 버전을 유지 관리하고 에셋 상태를 설정하며 에셋 만료를 설정할 수도 있습니다.

**내 Workspace**: Assets 보기에는 Assets 사용자 인터페이스의 주요 영역에 편리하게 액세스할 수 있는 위젯과 사용자와 가장 관련이 있는 정보를 제공하는 사용자 지정 가능한 작업 영역도 포함되어 있습니다. 이 페이지는 작업 항목에 대한 개요 및 주요 워크플로에 대한 빠른 액세스를 제공하는 종합적인 솔루션 역할을 합니다.

**Content Credentials**: AEM Assets에서 지원하는 또 다른 강력한 기능은 Content Credentials입니다. 브랜드는 콘텐츠 투명성, AI 공시, 자산 변조 방지에 어느 때보다 신경이 쓰인다. Adobe의 Content Authenticity Initiative(CAI)는 C2PA(Coalition for Content Provenance and Authenticity) 기술 표준을 준수하는 도구를 빌드합니다. Content Credentials은 새롭고 암호화된 변조 불가능한 메타데이터로서 시청자가 콘텐츠 계보를 이해하고 브랜드 자산의 무결성을 확인하는 데 도움이 될 수 있습니다. 여기에는 insight을 디지털 에셋의 역사에 제공하는 광범위한 조달 데이터가 포함될 수 있습니다.

<table>
<td>
   <a href="/help/assets/manage-organize-assets-view.md">
   <img alt="에셋 관리 작업" src="./assets/asset-management.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-organize-assets-view.md">
      <strong>자산 관리 작업</strong>
      </a>
   </div>
   <p>
      <em>일부 기본 및 고급 에셋 관리 작업을 수행하는 방법을 알아봅니다.</em>
   </p>
</td>


<td>
   <a href="/help/assets/my-workspace-assets-view.md">
   <img alt="Workspace 산" src="./assets/my-workspace.jpeg" />
   </a>
   <div>
      <a href="/help/assets/my-workspace-assets-view.md">
      <strong>내 Workspace</strong>
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
      <em>Content Credentials을 사용하여 디지털 에셋의 기록에 대한 통찰력을 얻으십시오.</em>
   </p>
</td>
</table>

**컬렉션**: AEM Assets을 사용하면 에셋을 컬렉션으로 구성할 수도 있습니다. 컬렉션은 Adobe Experience Manager Assets 보기 내의 에셋, 폴더 또는 기타 컬렉션 세트입니다. 컬렉션을 사용하여 사용자 간에 자산을 공유합니다. 폴더와 달리 컬렉션에는 서로 다른 위치의 자산이 포함될 수 있습니다. 사용자와 여러 컬렉션을 공유할 수 있습니다. 각 컬렉션에는 자산에 대한 참조가 포함되어 있습니다. 자산의 참조 무결성은 컬렉션에 간에 유지됩니다.

**알림**: Assets 보기 알림을 사용하면 저장소에서 사용할 수 있는 에셋, 폴더 또는 컬렉션에서 수행된 작업을 모니터링할 수 있습니다. 알림을 받을 콘텐츠를 선택하고 구독해야 합니다. 알림을 받을 범주를 구성할 수도 있습니다.

**중복 에셋 감지**: AEM Assets에서는 중복 에셋 감지도 지원합니다. DAM 사용자가 저장소에 이미 존재하는 에셋을 하나 이상 업로드하는 경우 Experience Manager이 중복을 감지하여 사용자에게 알립니다.



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
      <em>자산을 효율적으로 공유하기 위해 자산을 컬렉션으로 구성하는 방법에 대해 알아봅니다.</em>
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
      <em>자산, 폴더 또는 컬렉션에서 수행된 작업을 모니터링하기 위해 알림을 설정하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/detect-duplicate-assets.md">
   <img alt="중복 자산 감지" src="./assets/duplicate-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/detect-duplicate-assets.md">
      <strong>중복 에셋 감지</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets에 업로드된 중복 에셋을 검색하고 사용자에게 알립니다.</em>
   </p>
</td>
</table>

>[!TAB 통합]

## Adobe 및 비 Adobe 애플리케이션과 통합 {#integration-adobe-non-adode-apps}

AEM Assets은 다양한 Adobe 및 비 Adobe 애플리케이션과 원활하게 통합할 수 있습니다. 다음은 사용 가능한 통합에 대한 요약 보기입니다.

+++**Adobe 및 Adobe 이외의 애플리케이션과 통합**

* **OpenAPI 기능이 있는 다이내믹 미디어**: [OpenAPI 기능이 있는 다이내믹 미디어](/help/assets/dynamic-media-open-apis-overview.md)에서는 [검색](/help/assets/search-assets-api.md) 및 [배달](/help/assets/deliver-assets-apis.md) API의 포괄적인 집합을 제공합니다. 개발자가 자산 전달을 애플리케이션과 쉽게 통합할 수 있습니다. 이러한 애플리케이션에는 Adobe 및 서드파티 애플리케이션이 포함됩니다. 승인된 에셋을 검색하고 선택할 수 있는 Micro Frontend 에셋 선택기 사용자 인터페이스를 제공합니다. 선택기는 React JS, Angular JS, Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 쉽게 통합할 수 있습니다.

* **마이크로 프론트엔드 에셋 선택기**: 마이크로 프론트엔드 에셋 선택기는 Experience Manager Assets 리포지토리와 쉽게 통합되는 사용자 인터페이스를 제공하므로 리포지토리에서 사용 가능한 디지털 에셋을 찾아보거나 검색하고 응용 프로그램 작성 환경에서 사용할 수 있습니다.
에셋 선택기를 Adobe 또는 Adobe이 아닌 애플리케이션과 통합할 수 있습니다.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="OpenAPI 기능을 사용하는 Dynamic Media 개요" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>OpenAPI 기능을 사용하는 Dynamic Media 개요</strong>
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
      <em> 역할을 구성하여 승인된 자산에 대한 액세스를 제한합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="자산 선택기" src="./assets/integration-asset-selector.jpeg" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Micro-Frontend 자산 선택기</strong>
      </a>
   </div>
   <p>
      <em>Micro-Frontend Asset Selector를 Adobe 또는 Adobe이 아닌 애플리케이션과 통합하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

+++

+++**Adobe 애플리케이션과 네이티브 통합**

* **Adobe Workfront과 통합**: [!DNL Adobe Workfront]은(는) 업무의 전체 라이프사이클을 한 곳에서 관리할 수 있도록 도와주는 작업 관리 애플리케이션입니다. [!DNL Workfront]과(와) [!DNL Adobe Experience Manager Assets] 간의 통합을 통해 조직은 작업과 디지털 에셋 관리를 본질적으로 연결하여 콘텐츠 속도와 마켓 출시 속도를 개선할 수 있습니다. Workfront에서 작업을 관리하는 맥락에서 사용자는 필요한 문서 및 이미지에 액세스할 수 있습니다.

  Adobe은 [통합 [!DNL Workfront] 및 [!DNL Adobe Experience Manager Assets] 기본적으로](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html)에 제공합니다.

* **Figma와 통합**: AEM Assets은 기본적으로 Figma와 통합되어 디자이너가 Figma 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Figma 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다. Figma 커뮤니티 페이지에서 제공되는 AEM Assets Connector에 액세스하려면 [여기](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector)를 클릭하십시오.

* **Adobe Express과 네이티브 통합**: AEM Assets은 기본적으로 Adobe Express과 통합되므로 Adobe Express 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 직접 액세스할 수 있습니다. AEM Assets에서 관리되는 콘텐츠를 Express 캔버스에 배치한 다음 AEM Assets 저장소에 새 콘텐츠 또는 편집된 콘텐츠를 저장할 수 있습니다.

* **AEM Assets을 Creative Cloud에 연결**: Experience Manager Assets에는 다른 IMS 조직에 프로비저닝된 Creative Cloud 권한에 연결하여 Express 및 Creative Cloud Libraries을 비롯한 AEM Assets의 최신 Creative Cloud 통합을 쉽게 사용할 수 있는 기능이 있습니다. Creative Cloud 제품 및 AEM Assets가 별도의 IMS 조직에 프로비저닝된 경우 다른 Creative Cloud 조직에 연결하여 두 솔루션 간의 통합 워크플로를 실행할 수 있습니다.

<table>
<td>
   <a href="/help/assets/workfront-integrations.md">
   <img alt="Adobe Workfront와 통합" src="./assets/integration-adobe-workfront.jpeg" />
   </a>
   <div>
      <a href="/help/assets/workfront-integrations.md">
      <strong>Adobe Workfront과 통합</strong>
      </a>
   </div>
   <p>
      <em>Adobe Workfront과 통합하여 전체 작업 주기를 한 곳에서 관리합니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/manage-collections-assets-view.md">
   <img alt="Figma와의 통합" src="./assets/integration-commerce.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-collections-assets-view.md">
      <strong>Figma와 통합</strong>
      </a>
   </div>
   <p>
      <em>Figma 사용자 인터페이스 내에서 AEM Assets에 저장된 자산에 액세스</em>
   </p>
</td>
<td>
   <a href="/help/assets/native-integration-adobe-express.md">
   <img alt="Adobe Express과의 기본 통합" src="./assets/integration-adobe-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/native-integration-adobe-express.md">
      <strong>Adobe Express과 네이티브 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets 내에서 사용할 수 있는 자산을 빠른 캔버스에 배치하고 업데이트된 자산을 AEM에 저장합니다. </em>
   </p>
</td>


</table>


* **Adobe Journey Optimizer과 통합**: Adobe Experience Manager Assets을 사용하여 마케팅 및 크리에이티브 워크플로우를 결합합니다. 기본적으로 Adobe Journey Optimizer과 통합되어 Assets as a Cloud Service에 액세스하여 디지털 에셋을 저장, 관리, 검색 및 배포합니다. 메시지를 채우는 데 사용할 수 있는 자산의 단일 중앙 집중식 저장소입니다.

* **Commerce과 통합**: Adobe Experience Manager(AEM) Commerce용 Assets 통합은 AEM as a Digital Asset Management(DAM) 시스템의 강력한 기능을 Adobe Commerce과 결합하여 eCommerce 경험을 향상시킵니다. Commerce 프로젝트를 AEM의 강력한 자산 관리 환경에 연결하여 이러한 기능을 제공함으로써 상거래 상점 전반에서 자산을 원활하고 확장 가능하며 효율적으로 관리 및 제공할 수 있습니다.
* **Edge Delivery Services의 문서 기반 작성 흐름과 AEM Assets 통합**: [!DNL AEM Assets]이(가) [!DNL Microsoft Word] 또는 [!DNL Google Docs]과(와) 같은 문서 기반 작성 도구와 통합되면 작성 도구에 자산 선택기가 제공됩니다. 이 자산 선택기를 사용하여 [!DNL AEM Assets]에 액세스하고 승인된 자산을 콘텐츠에 삽입합니다.
[!DNL Edge Delivery Services] 웹 사이트가 이미 있는 경우 [[!DNL AEM Assets] plugin](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md) 설명서를 참조하여 [!DNL AEM Assets]을(를) 기존 [!DNL AEM] 프로젝트와 통합하는 방법에 대해 알아보십시오.

* **[!DNL AEM Assets]에 대해 [!DNL Universal Editor]을(를)[!DNL Edge Delivery Services]** 기반 작성 흐름과 통합: [!DNL Universal Editor]과(와) 통합하도록 [!DNL AEM Assets]을(를) 설정합니다. 이 통합을 통해 [!DNL Dynamic Media with OpenAPI capabilities]을(를) 사용하여 자산을 전달할 수 있습니다.

   * [에서 사용자 지정 자산 선택 함수를 추가하는 방법에 대해 알아보려면  [!DNL Edge Delivery] Configuration in](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site)Site[!DNL Universal Editor]을 참조하세요. 사용자 지정 에셋 선택기를 사용하면 에셋을 [!DNL Universal Editor] 콘텐츠에 직접 삽입할 수 있습니다.
   * [에서 작성하는 동안 ](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview)에 액세스하고 자산을 삽입하는 방법을 알아보려면 [!DNL AEM Assets]확장 개요[!DNL Universal Editor]를 참조하십시오.

<table>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
   <img alt="Adobe Journey Optimizer와 통합" src="./assets/integration-figma.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/combine/assets">
      <strong>Adobe Journey Optimizer과 통합</strong>
      </a>
   </div>
   <p>
      <em>AJO과의 통합을 사용하여 마케팅 및 크리에이티브 워크플로 통합</em>
   </p>
</td>
<td>
   <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/aem-assets-integration">
   <img alt="Commerce과 통합" src="./assets/integration-ajo.jpeg" />
   </a>
   <div>
      <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/aem-assets-integration">
      <strong>Commerce과 통합</strong>
      </a>
   </div>
   <p>
      <em>AEM Assets을 Commerce과 통합하여 전자 상거래 경험을 향상시킵니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
   <img alt="EDS와 AEM Assets 통합" src="./assets/integrate-ue-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md">
      <strong>EDS와 AEM Assets 통합</strong>
      </a>
   </div>
   <p>
      <em>문서 기반 및 유니버설 편집기 기반의 작성 흐름과 AEM Assets을 통합합니다.</em>
   </p>
</td>
</table>

+++

>[!TAB 자산 활성화]

## 자산 활성화 {#asset-activation}

강력한 OpenAPI 기능을 포함하여 Content Hub을 Dynamic Media에 사용한 AEM Assets을 통해 디지털 에셋의 잠재력을 최대한 활용할 수 있습니다. AEM Assets은 에셋 변환을 간소화하고 다양한 채널에서 게재를 최적화하도록 설계된 포괄적인 솔루션 제품군을 제공합니다.

+++**Content Hub**

Content Hub는 Experience Manager Assets as a Cloud Service의 일부로 제공되며, 이를 통해 조직과 비즈니스 파트너는 브랜드 콘텐츠를 더 간편하게 이용할 수 있습니다. 대규모 활성화를 위한 자산을 배포하고 마케팅 민첩성을 개선하기 위한 온브랜드 콘텐츠 변형을 만드는 데 중점을 둡니다.

Content Hub는 다음과 같은 주요 이점을 제공합니다.

* **직관적인 포털에서 사용할 수 있는 모든 브랜드 승인 에셋을 찾아서 공유**: AEM Assets은 신뢰할 수 있는 단일 소스 역할을 하며 검색 환경을 개선하기 위해 모든 승인 에셋을 Content Hub에서 플랫 계층 구조로 자동으로 사용할 수 있습니다.

* **구성 가능한 사용자 인터페이스**: 검색을 위한 필터, 자산을 추가하거나 가져오는 동안 사용할 수 있는 필드, 자산 속성, 브랜딩을 위한 배너 콘텐츠와 같은 Content Hub 내의 가장 일반적인 속성을 구성할 수 있으며 관리자는 해당 요구 사항에 따라 Content Hub 사용자 인터페이스를 쉽게 구성할 수 있습니다.

* **브랜드를 사용하는 동안 크리에이티브가 아닌 사용자에게 콘텐츠를 편집하고 다시 혼합할 수 있는 권한을 부여합니다**: Content Hub에서는 Adobe Express 권한이 있는 경우 Adobe Express을 사용하여 새 콘텐츠를 만들 수 있습니다. 사용하기 쉬운 도구로 기존 콘텐츠를 편집하고, 템플릿과 브랜드 요소로 브랜드에 맞는 변형을 만들고, Adobe Firefly의 최신 생성형 AI 기능으로 새로운 콘텐츠를 만들 수 있습니다.

* **팀 간에 콘텐츠를 사용하는 방법에 대한 통찰력을 얻으십시오**: [!DNL Content Hub]에서는 마케팅 캠페인, 채널 및 다른 지역에서 사용되는 자산 사용 통계와 같이 마케팅 이해 당사자가 자주 직면하는 일반적인 문제를 해결하면서 자산에 대한 중요한 통찰력을 제공합니다. 자산의 성과와 인기를 명확하게 이해함으로써 사용자 경험 향상에 필수적인 실행 가능한 인사이트를 제공합니다.

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
      <em>Content Hub, 주요 이점 및 액세스 방법에 대해 자세히 알아봅니다. </em>
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
   <img alt="Adobe Express을 사용하여 편집" src="./assets/content-hub-express.jpeg" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
      <strong>Adobe Express을 사용하여 편집</strong>
      </a>
   </div>
   <p>
      <em>Adobe Express을 사용하여 Content Hub에서 이미지를 편집하는 방법을 알아봅니다.</em>
   </p>
</td>
</table>

+++

+++**Dynamic Media**

Dynamic Media를 사용하면 다양한 시각적 머천다이징 및 마케팅 자산을 온디맨드로 제공할 수 있습니다. 또한 확대/축소, 360도 회전 및 비디오를 비롯한 대화형 보기 환경을 만들고 제공하는 데 도움이 됩니다. 자산은 웹, 모바일 및 소셜 사이트에서 사용할 수 있도록 동적으로 크기가 조정됩니다. 이미지, 비디오 및 3D와 같은 기본 소스 자산 세트를 사용하는 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 CDN(Content Delivery Network)을 통해 실시간으로 이 풍부한 컨텐츠의 여러 변형을 생성하고 전달합니다.

Dynamic Media는 다음과 같은 주요 기능을 제공합니다.

* **스마트 이미징**: 스마트 이미징은 고객의 브라우저 기능에 따라 이미지의 형식과 파일 크기를 자동으로 최적화하여 더 나은 이미지 에셋 전달 성능을 제공합니다. 기존 이미지 사전 설정에서 작동하며 전달 시 인텔리전스를 사용합니다. 이 인텔리전스는 브라우저 및 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다.

* **응용 비디오 집합**: 응용 비디오 집합은 다른 비트 전송률과 형식으로 인코딩된 동일한 비디오의 버전을 그룹화합니다. 시스템에 업로드하는 원본 기본 비디오부터 시작합니다. Dynamic Media는 해당 비디오를 자동으로 크기 조정하거나 여러 비디오로 코드 변환합니다. 그런 다음, 배송 시 어떤 비디오 화면, 어떤 품질, 어떤 포맷을 사용할 것인지 지능적으로 결정하여 전화, 태블릿, 데스크탑 컴퓨터 중 하나로 전달한다.

* **스마트 자르기**: 모든 이미지 또는 비디오에서 초점을 자동으로 감지하고 자르기 방식으로 유지하는 Adobe Sensei AI 기능입니다. 화면 크기에 상관없이 의도한 관심 영역을 캡처하므로 번거로운 수작업을 없애고 모든 장치 또는 화면에서 보기 좋은 고품질의 빠른 로딩 이미지 및 비디오를 제공합니다.

* **Dynamic Media 템플릿**: WYSIWYG 템플릿 편집기인 Dynamic Media 템플릿을 사용하여 배너 및 전단에 대한 사용자 지정 가능한 실시간 템플릿을 만듭니다. Dynamic Media 템플릿을 게시하고 다운스트림 애플리케이션에서 사용합니다. Dynamic Media 템플릿에는 이미지 및 텍스트 레이어가 포함됩니다. 템플릿의 이미지 및 텍스트 레이어에 매개 변수를 추가하고 Dynamic Media URL을 사용하여 레이어의 위치를 변경하고 크기를 조정하며 실시간으로 해당 콘텐츠를 업데이트합니다.

* **다중 오디오 및 캡션**: 기본 비디오에 여러 캡션 및 여러 오디오 트랙을 추가합니다. 즉, 이러한 기능을 통해 글로벌 대상자는 비디오에 액세스할 수 있습니다. 여러 언어로 글로벌 대상자에게 게시된 하나의 기본 비디오를 사용자 정의하고 지역별 액세스 가능성 가이드라인을 준수할 수 있습니다. 작성자는 사용자 인터페이스의 단일 탭에서 캡션 및 오디오 트랙을 관리할 수도 있습니다.

* **DASH(Dynamic Adaptive Streaming over HTTP) 지원**: Dynamic Media는 Dynamic Media 비디오 게재(CMAF가 활성화됨)에서 적응형 스트리밍을 지원하므로 비디오에 대한 사용자 보기 환경이 향상됩니다. DASH는 응용 비디오 스트리밍에 대한 국제 표준 프로토콜로서 업계에서 널리 채택되고 있다.

* **AI 생성 비디오 캡션**: Adobe Dynamic Media의 AI 생성 비디오 캡션은 인공 지능을 사용하여 비디오 컨텐츠의 캡션을 자동으로 생성합니다. 60개 이상의 언어를 지원하므로 비디오를 게시하기 전에 캡션을 검토하고 미리 볼 수 있습니다.

사용 가능한 Dynamic Media 제품에 대한 자세한 내용은 [Dynamic Media Prime 및 Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md)을(를) 참조하십시오.



<table>
<td>
   <a href="/help/assets/dynamic-media/dynamic-media.md">
   <img alt="Dynamic Media를 사용하여 작업" src="./assets/work-with-dynamic-media.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media/dynamic-media.md">
      <strong>Dynamic Media 작업</strong>
      </a>
   </div>
   <p>
      <em>웹, 모바일 및 소셜 사이트에서 사용할 자산을 전달하는 방법을 알아봅니다. </em>
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
      <em>Dynamic Media가 어떻게 작업에 가치를 제공하는지 알아보세요.</em>
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
      <em>이미지, 비디오 및 뷰어로 작업하는 동안의 모범 사례입니다.</em>
   </p>
</td>
</table>

+++

+++**OpenAPI 기능이 포함된 Dynamic Media**

빠르게 변화하는 오늘날의 디지털 세계에서 브랜드 디지털 자산의 잠재력을 최대한 활용하는 것은 경쟁에서 앞서 나가기 위해 매우 중요합니다. 총체적인 디지털 자산 관리(DAM) 솔루션은 자산 거버넌스를 촉진하고, 브랜드 일관성을 촉진하며, 콘텐츠 게재를 가속화하는 동시에 브랜드 무결성과 탁월한 고객 경험을 보장합니다.

OpenAPI 기능 포함 Dynamic Media는 민첩하고 효율적인 콘텐츠 공급망 생태계의 핵심에 DAM을 배치하여 자산 거버넌스와 게재를 보장합니다.

OpenAPI 기능이 포함된 Dynamic Media는 다음과 같은 주요 이점을 제공합니다.

* **원활한 통합**: OpenAPI 기능이 포함된 Dynamic Media는 포괄적인 검색 및 게재 API 세트를 제공합니다. 이를 통해 개발자가 [자산 게재를 애플리케이션과 쉽게 통합](/help/assets/integrate-dynamic-media-open-apis.md)할 수 있습니다. 이러한 애플리케이션에는 Adobe 및 서드파티 애플리케이션이 포함됩니다. 승인된 자산을 검색하고 선택할 수 있는 [마이크로 프론트엔드 자산 선택기 사용자 인터페이스](/help/assets/overview-asset-selector.md)를 제공합니다. 선택기는 React JS, Angular JS, Vanilla JS와 같은 JavaScript 프레임워크를 기반으로 하는 모든 애플리케이션과 쉽게 통합할 수 있습니다.

* **디지털 자산의 중앙 관리**: DAM은 모든 디지털 자산에 대한 단일 정보 소스입니다. 디지털 자산은 AEM Assets에서 중앙 집중식으로 관리되며, 자산 바이너리를 복사하지 않고 게재 URL을 사용한 참조를 통해 소비 애플리케이션에 전달됩니다.

* **실시간 업데이트**: 버전 업데이트 및 메타데이터 수정을 포함하여 DAM에서 승인된 자산에 대한 변경 사항은 게재 URL에 자동으로 반영됩니다. CDN을 통해 OpenAPI 기능이 갖춘 Dynamic Media에 대해 10분이라는 짧은 TTL(Time-to-Live) 값을 구성하면 모든 작성 및 게시 인터페이스에서 10분 이내에 업데이트가 표시됩니다.

* **브랜드 일관성**: [브랜드 승인 자산](/help/assets/approve-assets.md)만 다운스트림 애플리케이션에 노출됩니다. [브랜드 관리자 및 마케터는 브랜드 자산에 대한 엄격한 통제권을 유지합니다](/help/assets/restrict-assets-delivery.md). 승인된 최신 버전의 자산만 사용할 수 있어 모든 채널과 애플리케이션에서 브랜드 일관성을 보장합니다.

* **웹에 최적화된 게재**: 디지털 자산은 웹에 최적화된 형식으로 제공되어 디지털 경험의 핵심 웹 바이탈을 향상시킵니다. 여기에는 이미지에 대한 WebP 렌디션 지원, 비디오에 대한 HLS 또는 DASH 프로토콜을 통한 적응형 스트리밍, 문서에 대한 원본 렌디션이 포함됩니다.

* **동적 자산 변환**: 당사 시스템은 이미지 수정자로 알려진 URL 매개변수를 사용하여 즉석에서 이미지를 변환할 수 있습니다. [예: 폭, 높이, 회전, 뒤집기, 품질, 자르기, 포맷 및 스마트 자르기](/help/assets/deliver-assets-apis.md). 변환된 렌디션은 동적으로 생성되며 CDN을 통해 원활하게 게재됩니다.

* **자산의 안전한 게재**: OpenAPI 기능 포함 Dynamic Media는 디지털 자산에 대한 액세스를 제어할 수 있는 메커니즘을 제공합니다. 보안 대상 자산의 메타데이터로 사용자 역할 또는 그룹을 지정하고 [승인된 사용자만 이러한 자산에 액세스](/help/assets/restrict-assets-delivery.md)할 수 있는 사전 정의 기간을 설정할 수 있습니다. 보안 자산의 게재 URL은 제한된 기간 동안 승인되지 않은 사용자가 접근할 수 없습니다.

사용 가능한 Dynamic Media 제품에 대한 자세한 내용은 [Dynamic Media Prime 및 Ultimate](/help/assets/dynamic-media/dm-prime-ultimate.md)을(를) 참조하십시오.

<table>
<td>
   <a href="/help/assets/dynamic-media-open-apis-overview.md">
   <img alt="OpenAPI 기능을 사용하는 Dynamic Media 개요" src="./assets/dm-openapi-uses.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-overview.md">
      <strong>OpenAPI 기능을 사용하는 Dynamic Media 개요</strong>
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
      <em> 역할을 구성하여 승인된 자산에 대한 액세스를 제한합니다.</em>
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
      <em>원격 AEM Assets을 AEM Sites 환경과 통합합니다. </em>
   </p>
</td>
</table>

+++

>[!TAB Insights]

## Asset Insights {#asset-insights}

에셋 보고는 관리자가 Adobe Experience Manager Assets 보기 환경의 활동을 볼 수 있도록 합니다. 이 데이터는 사용자가 콘텐츠 및 제품과 상호 작용하는 방법에 대한 유용한 정보를 제공합니다. 모든 사용자는 인사이트 대시보드에 액세스할 수 있으며 관리자 제품 프로필에 할당된 사용자는 사용자 정의 보고서를 만들 수 있습니다.

업로드, 다운로드 및 Dynamic Media 게재 등 다양한 유형의 보고서를 생성할 수 있습니다.

* **Assets 보기의 인사이트**: Assets 보기를 사용하면 인사이트 대시보드를 사용하여 Assets 보기 환경에 대한 실시간 데이터를 볼 수 있습니다. 지난 30일 동안 또는 지난 12개월 동안의 실시간 이벤트 지표를 볼 수 있습니다. 이벤트에는 다운로드, 업로드, 저장소 사용, 최상위 검색, 크기별 에셋 수 및 에셋 유형별 에셋 수가 포함됩니다.

* **관리 보기의 Adobe Analytics 통합**: Assets Insights 기능을 사용하면 타사 웹 사이트, 마케팅 캠페인 및 Adobe의 광고 솔루션에서 사용되는 이미지의 사용자 등급 및 사용 통계를 추적할 수 있습니다. 이는 이미지의 성능 및 인기에 대한 통찰력을 제공하는 데 도움이 됩니다. Assets Insights는 이미지에 대한 등급, 클릭 횟수 및 노출 횟수(이미지가 웹 사이트에 로드되는 횟수) 등 사용자 활동 세부 정보를 캡처합니다. 이러한 통계를 기반으로 이미지에 점수를 할당합니다. 점수 및 성과 통계를 사용하여 카탈로그, 마케팅 캠페인 등에 포함할 인기 있는 이미지를 선택할 수 있습니다. 이러한 통계를 기반으로 아카이브 및 라이선스 갱신 정책을 수립할 수도 있습니다. Assets Insights를 통해 에셋에 대한 사용 통계를 표시하도록 하려면 먼저 Adobe Analytics에서 보고 데이터를 가져오도록 기능을 구성합니다.

* **Content Hub 인사이트**: Content Hub은 마케팅 캠페인, 채널 및 다른 지역에서 사용되는 자산 사용 통계와 같이 마케팅 이해 당사자가 자주 직면하는 일반적인 문제를 해결하면서 자산에 대한 중요한 인사이트를 제공합니다. 자산의 성과와 인기를 명확하게 이해함으로써 사용자 경험 향상에 필수적인 실행 가능한 인사이트를 제공합니다.

<table>
<td>
   <a href="/help/assets/manage-reports-assets-view.md">
   <img alt="Assets 보기에서 태그 관리" src="./assets/assets-insights-assets-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/manage-reports-assets-view.md">
      <strong>Assets 보기에서 보고서 관리</strong>
      </a>
   </div>
   <p>
      <em>Assets 보기를 사용하여 주요 성공 지표에 대한 통찰력을 얻습니다. </em>
   </p>
</td>


<td>
   <a href="/help/assets/asset-reports.md">
   <img alt="관리자 보기에서 보고서 관리" src="./assets/assets-insights-admin-view.jpeg" />
   </a>
   <div>
      <a href="/help/assets/asset-reports.md">
      <strong>관리자 보기에서 보고서 관리</strong>
      </a>
   </div>
   <p>
      <em>관리자 보기에서 Adobe Analytics 통합 보고서를 관리하는 방법을 알아봅니다.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Content Hub의 Assets 통찰력" src="./assets/asset-insights-content-hub.jpeg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
      Content Hub의 <strong>Assets 인사이트</strong>
      </a>
   </div>
   <p>
      <em>Content Hub에서 자산 통찰력을 보는 방법에 대해 알아봅니다.</em>
   </p>
</td>
</table>

>[!ENDTABS]

## 디지털 자산 관리에 대해 사용 가능한 페르소나 기반 경험 {#persona-based-experiences}

Adobe는 디지털 자산을 최대한 활용할 수 있는 강력한 DAM(디지털 자산 관리) 솔루션을 제공합니다. Adobe Experience Manager Assets에는 동일한 클라우드 서비스 저장소를 사용하는 서로 다른 두 가지 환경이 있습니다.

* **관리자 보기**: 기존의 Assets as a Cloud Service 사용자 인터페이스입니다. 통합, 워크플로, 콘텐츠 자동화, 게시 등을 포함한 모든 고급 디지털 자산 관리 기능에 대해 관리자 보기를 사용합니다.

* **Assets 보기**: 디지털 자산을 저장, 관리, 검색 및 사용할 수 있는 가벼운 버전의 Adobe 자산 관리 경험입니다. 필수 디지털 자산 관리 기능이 포함된 간소화된 사용자 인터페이스입니다. 업로드, 메타데이터 관리, 검색, 다운로드 및 공유에 중점을 둔 가벼운 버전의 DAM 사용자를 위해 설계되었습니다.

![add-tags](assets/newui-overview.svg)

관리자 보기에 대한 액세스 권한이 있는 사용자는 Assets 보기에도 액세스할 수 있습니다. Assets 보기는 간소화된 사용자 인터페이스를 통해 디지털 자산을 쉽게 관리, 검색 및 배포할 수 있습니다. 크리에이티브, 마케팅 및 사업 부문 팀 등 다양한 직무의 광범위한 사용자가 자산에 대해 공동 작업하고 필요한 시간과 장소에서 올바른 승인된 자산에 액세스할 수 있습니다. 많은 일반 DAM 사용자는 기능의 하위 집합만 포함하는 Assets 보기를 선호합니다. 이 경험은 크리에이티브, 읽기 전용 자산 소비자 및 더 가벼운 DAM 사용자를 대상으로 합니다.

DAM 라이브러리 관리자, 개발자 및 상위 사용자는 계속해서 관리자 보기를 사용하거나 필요에 따라 사용자 인터페이스 간에 전환할 수 있습니다. 역할에 가장 적합한 환경을 선택할 수 있습니다.

Assets 보기에 액세스하는 방법 및 관리자 보기에서 제공하는 일부 간소화에 대한 자세한 내용은 [Assets 보기 소개](/help/assets/assets-view-introduction.md)를 참조하십시오.


