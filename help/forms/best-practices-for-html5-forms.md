---
title: HTML5 양식 우수 사례
description: 최상의 성능을 얻으려면 XFA 기반 HTML5 Forms을 조정하십시오.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
content-type: reference
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 62ff6306-9989-43b0-abaf-b0a811f0a6a4
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 0%

---

# HTML5 양식 우수 사례{#best-practices-for-html-forms}

<span class="preview"> HTML5 Forms 기능은 조기 액세스 프로그램의 일부로 제공됩니다. 액세스 권한을 요청하려면 공식(회사) 이메일 ID에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오.
</span>

## 개요 {#overview}

AEM Forms에는 HTML5 forms라는 구성 요소가 있습니다. 기존 XFA 기반 PDF forms(XDP 파일)를 HTML5 형식으로 렌더링하는 데 도움이 됩니다. 이 문서에서는 로드 시간을 줄이고 모바일 장치에서 HTML5 Forms의 성능을 개선하기 위한 지침 및 권장 사항을 제공합니다.

대부분의 모바일 장치에는 제한된 처리 능력 및 메모리 기능이 있습니다. 모바일 기기의 대기 시간을 개선하는 데 도움이 된다. 모바일 디바이스에서 실행되는 웹 브라우저는 제한된 리소스(제한된 메모리 및 처리 기능)에 액세스할 수 있습니다. 한도에 도달하면 브라우저 동작이 느리게 바뀝니다. 이 문서에서는 HTML5 양식의 크기를 확인할 수 있는 권장 사항을 제공합니다. 더 작은 형태는 장치의 메모리 및 처리 전력 제한을 위반하지 않으며 원활한 경험을 제공한다.

이 문서에서 설명하는 권장 사항은 HTML 5 양식을 대상으로 하지만 이는 XFA 기반 PDF forms에도 동일하게 적용할 수 있습니다. 이러한 모범 사례는 전체적으로 HTML5 양식의 전반적인 성능에 기여합니다. 효율적이고 생산적인 양식을 개발하기 위한 신중한 계획이 필요하다. 시작하겠습니다.

## 노드는 HTML5 양식의 통화이며 현명하게 지출하십시오. {#nodes-are-currency-of-html-forms-spend-them-wisely}

일반적으로 XFA 양식에는 여러 요소가 있습니다. 예: 표, 텍스트 필드 및 이미지 모든 요소에는 요소의 동작과 모양을 제어하는 몇 가지 속성이 있습니다. XFA 양식이 HTML5 형식으로 렌더링되면 모든 XFA 요소와 해당 속성이 모델 또는 HTML DOM 노드로 변환됩니다. 이러한 노드는 DOM의 크기와 복잡성을 가중시킵니다. HTML5 양식을 렌더링하기 느리게 만듭니다.

브라우저가 학습자 DOM을 렌더링하는 것이 더 쉽습니다. 따라서 XFA 양식에서 다음 최적화를 수행하여 노드 수를 줄일 수 있습니다. 따라서 린 DOM 구조를 생성합니다.

* 캡션 속성을 사용하여 필드에 레이블을 추가합니다. 레이블을 추가할 때 별도의 Text 요소를 사용하지 마십시오. 추가 체중을 줄이는 데 도움이 되어 성능 향상으로 이어집니다. 또한 레이아웃 문제를 방지하는 데 도움이 됩니다.
* 양식의 그리기 텍스트 요소 수를 최소한으로 유지합니다. 그리기 요소는 가독성과 모양을 개선하는 데 도움이 되지만 정보 저장 기능이 없습니다. 여러 Draw 텍스트 요소를 하나의 Draw 텍스트 요소로 병합하는 것이 좋습니다. 양식을 더 익히기 위해 모든 수단을 다 써라.

## Lite Forms는 성능을 향상시키고 리소스를 압축합니다. {#lite-forms-perform-better-keep-the-resources-compressed}

HTML5 양식에는 이미지, JavaScript 및 CSS 파일과 같은 여러 외부 리소스가 포함될 수 있습니다. 브라우저가 양식을 요청할 때마다 외부 리소스가 네트워크를 통해 전송됩니다. 네트워크를 통해 이동하는 데 필요한 시간은 파일 크기에 정비례합니다.

따라서 외부 리소스의 크기를 줄이고 절대적으로 필요한 리소스만 사용하는 것이 양식의 성능을 향상시키는 데 선호되는 방법입니다. XFA 양식에서 다음 최적화를 수행하여 양식의 외부 리소스 크기를 줄일 수 있습니다.

* [압축된 이미지](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)를 사용합니다. 양식을 렌더링하는 데 필요한 네트워크 활동 및 메모리의 양을 줄입니다. 따라서, 폼 로드 시간이 크게 줄어들게 된다.
* AEM 구성 관리자(일별 CQ HTML 라이브러리 관리자)의 축소 옵션을 사용하여 JavaScript 및 CSS 파일을 압축합니다. 자세한 내용은 [OSGi 구성 설정](/help/implementing/deploying/configuring-osgi.md)을 참조하십시오.
* 웹 압축을 활성화합니다. 양식에서 시작된 요청 및 응답의 크기를 줄입니다. 자세한 내용은 [AEM Forms 서버의 성능 조정](https://helpx.adobe.com/kr/aem-forms/6-3/performance-tuning-aem-forms.html)을 참조하십시오.

## 관심 영역 유지, 필수 필드만 표시  {#keep-the-interest-alive-show-only-required-fields}

HTML5 양식은 수백 개의 페이지로 실행될 수 있습니다. 필드 수가 많은 양식은 브라우저에서 로드되는 속도가 느립니다. XFA 양식에서 다음 최적화를 수행하여 필드 및 페이지의 수가 많은 양식을 최적화할 수 있습니다.

* 큰 양식을 여러 양식으로 분할할 것을 평가합니다. 또한 양식 세트를 사용하여 작은 모든 양식을 함께 그룹화하여 단일 단위로 표시할 수도 있습니다. 양식 세트는 필요한 양식만 로드합니다. 또한 양식 집합에서 데이터 바인딩을 공유하도록 다른 양식의 공통 필드를 구성할 수 있습니다. 데이터 바인딩을 사용하면 일반 정보를 한 번만 채우는 데 도움이 됩니다. 이후 양식에서 정보가 자동으로 채워지므로 성능이 크게 향상됩니다. 양식 설정에 대한 자세한 내용은 [AEM 양식의 양식 집합](https://helpx.adobe.com/kr/aem-forms/6-3/formset-in-aem-forms.html)을 참조하십시오.
* 섹션을 분할하고 각 섹션을 다른 페이지로 이동하는 것이 좋습니다. HTML5 forms는 페이지 스크롤 요청 시 각 페이지를 동적으로 로드합니다. 스크롤된 페이지(표시되는 페이지 및 그 이전 페이지)만 메모리에 저장됩니다. 나머지 페이지는 필요에 따라 로드됩니다. 따라서 페이지에서 섹션을 분할하여 이동하면 양식을 로드하는 데 필요한 시간이 줄어듭니다. 양식의 첫 페이지를 랜딩 페이지로 사용할 수도 있습니다. 이는 책의 목차(TOC)와 유사하다. 양식의 랜딩 페이지에는 양식의 다른 섹션에 대한 링크만 포함되어 있습니다. 양식의 첫 번째 페이지에 대한 로드 시간을 크게 향상시키고 사용자 경험을 향상시킵니다.
* 기본적으로 조건부 섹션을 숨깁니다. 특정 조건이 충족될 때만 이러한 섹션을 볼 수 있도록 합니다. DOM의 크기를 최소한으로 유지하는 데 도움이 됩니다. 탭 탐색을 사용하여 한 번에 한 섹션만 표시할 수도 있습니다.

## 적을수록 더 많음, 페이지 수 감소 {#less-is-more-reduce-the-number-of-pages}

HTML5 양식에는 데이터 기반 필드(테이블 및 하위 양식)가 포함될 수 있습니다. 이러한 필드는 런타임 시 양식 크기를 확장합니다. 예를 들어 HTML5 양식의 데이터 기반 테이블은 수천 개의 행에 걸쳐 있을 수 있습니다. 이러한 테이블은 레이아웃 및 성능 저하를 초래할 수 있습니다. 아래에 제시된 최적화는 데이터 기반 필드가 있는 HTML5 양식의 로드 시간을 줄이는 데 도움이 될 수 있습니다.

* XFA 스크립팅을 사용하여 페이징된 탐색을 수행하여 데이터 기반 필드(테이블 및 하위 양식)를 표시할 수 있습니다. 페이지 탐색에서는 특정 데이터만 페이지에 표시됩니다. 브라우저 그리기 작업을 한 번에 표시되는 필드로 제한하여 양식을 더 쉽게 탐색할 수 있습니다. 더욱이, 모바일 디바이스들 상의 사용자들은 데이터의 서브세트에만 관심이 있다. 이는 우수한 사용자 경험을 제공하고 필요한 데이터를 로드하는 데 필요한 시간을 줄이는 데 도움이 됩니다. 하나의 가격에 두 개의 솔루션을 얻을 수 있습니다.  또한 페이지 탐색은 즉시 사용할 수 없습니다. XFA 스크립팅을 사용하여 페이징된 탐색을 개발할 수 있습니다.

* 여러 읽기 전용 열을 단일 열로 병합하는 것을 평가합니다. 양식을 표시하는 데 필요한 메모리를 줄입니다. 또한 사용자의 입력이 필요하지 않은 열을 표시하지 마십시오.
* 위의 제안 사항이 많이 개선되지 않으면 데이터 기반 양식을 [양식 집합](https://helpx.adobe.com/kr/aem-forms/6-3/formset-in-aem-forms.html)&#x200B;(으)로 분할해야 합니다. 예를 들어 테이블에 1000개가 넘는 행이 있는 경우 100개 행마다 다른 양식으로 이동합니다. 양식의 로드 시간과 성능을 개선하는 데 도움이 됩니다.  또한 양식 세트는 모든 양식에 대해 통합된 제출 XML을 생성합니다. 모든 양식의 데이터를 구분하려면 다른 데이터 루트를 사용하십시오. 자세한 내용은 [AEM Forms에 설정된 양식](https://helpx.adobe.com/kr/aem-forms/6-3/formset-in-aem-forms.html)을 참조하세요.

## 기록 문서(DOR)에 대한 2의 거듭제곱 {#power-of-two-for-document-of-record-dor}

XFA 양식에는 DOR(기록 문서)에 대해서만 많은 섹션이 있을 수 있습니다. 노드 수를 줄이고 이러한 양식의 성능을 향상시키려면 양식의 여러 사본을 유지 관리할 수 있습니다. 한 사본은 양식을 채우고 다른 사본은 서버에 기록 문서를 생성할 수 있습니다. XFA 양식을 채우기 위한 사본에 데이터 캡처에만 필요한 필드가 표시됩니다. 기록 문서 생성 XFA에서에서 양식의 인쇄된 출력에만 필요한 필드를 유지합니다. 제안된 방법을 선택하기 전에 성능 향상 및 유지 관리 오버헤드를 평가하십시오.

## 권장 읽기  {#recommended-reads}

Adobe Experience Manager(AEM) forms를 사용하면 복잡한 트랜잭션을 단순하고 즐거운 디지털 경험으로 변환할 수 있습니다. 그러나 효율적이고 생산적인 양식을 개발하기 위해서는 일치된 노력이 필요합니다. HTML5 Forms 외에도 일반적인 AEM 모범 사례에 대한 몇 가지 권장 읽기가 있습니다.


<!--

* Best practices for Deploying and maintaining AEM
* Best practices for Authoring content
* [Best practices for Administering AEM](/help/sites-administering/administer-best-practices.md)
* [Best practices for Developing solutions](/help/sites-developing/best-practices.md)
* [Best practices for working with adaptive forms](/help/forms/using/adaptive-forms-best-practices.md)
* [AEM Forms server does not embed fonts to a Dynamic PDF form](https://helpx.adobe.com/aem-forms/kb/aem-forms-server-does-not-embed-fonts-to-dynamic-pdf-form.html)

-->

## 빠른 참조 카드 {#quick-reference-card}

다음 카드(고해상도 버전을 다운로드하려면 카드를 클릭)를 인쇄하고 빠른 참조를 위해 책상에 보관할 수 있습니다.
[![HTML5 Forms 모범 사례 빠른 참조 카드](assets/best-practices_reference_card.png)](assets/html5_forms_best_practices_reference_card.pdf)
