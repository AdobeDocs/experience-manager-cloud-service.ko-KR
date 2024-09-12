---
title: Dynamic Media 여정, 1부
description: Dynamic Media 여정은 Dynamic Media의 기본 사항, 작동 방식, 무엇을 수행할 수 있으며 작업 및 고객에게 어떤 가치를 제공하는지 다룹니다.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles,Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: f3472006-d5ae-4f70-af3e-44e73aee85cc
source-git-commit: 74172fe7fcf9a22837645a154f2e85fd6fa6b40e
workflow-type: tm+mt
source-wordcount: '3615'
ht-degree: 0%

---

# Dynamic Media 여정: 기본 사항, 1부 {#dm-journey-part1}

{{see-also-dm}}

Dynamic Media 여정에 오신 것을 환영합니다.

이 여정은 Dynamic Media의 기본 사항, 작동 방식, 사용자에게 제공할 수 있는 기능 및 작업 및 고객에게 제공하는 가치를 다룹니다.

**_전제 조건_**

* 이미지 및 비디오 형식에 대한 기본 이해
* HTML 및 CSS에 대한 기본 이해
* Adobe Illustrator, Adobe Photoshop, Adobe XD 등의 디자인 도구에 대한 기본 이해
* Experience Manager에서 Dynamic Media에 액세스하는 것은 유용하지만 필수는 아닙니다

**_배울 내용_**

_파트 I_

* Dynamic Media란 무엇이며 어떤 도움을 줄 수 있습니까?
* Dynamic Media 사용 사례
* Dynamic Media 시스템을 통한 에셋 흐름

_파트 II_

* Dynamic Media URL 구조 및 Dynamic Media에서 콘텐츠를 제공하는 방법
* 자산 렌더링용 이미지 사전 설정 만들기의 기본 사항
* 이미지 세트, 스핀 세트 및 혼합 미디어 세트

**_대상자_**
이 여정의 독자에게 가장 적합한 대상은 Experience Manager에서 Dynamic Media을 처음 사용하는 다음과 같습니다.

* 관리자
* 비즈니스 분석가
* 콘텐츠 설계자
* 콘텐츠 작성자
* Designer
* 개발자
* 마케팅
* 제품 관리자/소유자

>[!TIP]
>
>Adobe 최상의 결과를 얻으려면 데스크톱 컴퓨터에서 이 Dynamic Media 여정을 읽고 볼 것을 권장합니다.

## Dynamic Media란 무엇이며 어떤 도움을 줄 수 있습니까? {#dm-journey-a}

Dynamic Media을 사용하면 다양한 시각적 머천다이징 및 마케팅 자산을 온디맨드로 제공할 수 있습니다. 또한 확대/축소, 360도 회전 및 비디오를 비롯한 대화형 보기 환경을 만들고 제공하는 데 도움이 됩니다. 자산은 웹, 모바일 및 소셜 사이트에서 사용할 수 있도록 동적으로 크기가 조정됩니다. Dynamic Media은 이미지, 비디오 및 3D와 같은 기본 소스 자산 세트를 사용하여 글로벌, 확장 가능 및 성능 최적화 CDN(Content Delivery Network)을 통해 실시간으로 이 풍부한 컨텐츠의 여러 변형을 생성하고 전달합니다.

Dynamic Media은 디지털 캠페인 관리 프로세스를 간소화하고 간소화하기 위해 Adobe Experience Manager Assets 디지털 에셋 관리 솔루션의 워크플로를 통합합니다.

### 무한한 가능성이 있는 하나의 파일

Dynamic Media에 대해 이해할 수 있는 주요 사항 중 하나는 _가능성이 무한한 기본 에셋 파일 하나_&#x200B;의 개념입니다.

이 개념을 더 잘 이해하려면 일반적으로 이미지나 비디오와 같은 단일 에셋으로 작업하는 방법을 생각해 보십시오. 일반적으로 1개의 기본 자산을 만듭니다. 그런 다음 모든 경험, 필요한 모든 장치, 모든 웹 페이지 및 해당 에셋이 사용되는 모든 속성에 대해 동일한 에셋의 버전을 수동으로 만듭니다. 시간이 지남에 따라 해당 단일 자산은 버전 내역이 첨부되지 않은 20개, 30개 이상의 버전으로 늘어날 수 있습니다. 이제, 여러분이 가지고 있는 모든 이미지나 비디오에 대해 그렇게 한다고 상상해 보세요. 에셋 버전의 수는 스토리지 비용의 증가뿐 아니라 유지 관리 및 업데이트를 위한 과부하가 될 수 있습니다.

그러나 Dynamic Media을 사용하여 단일 기본 자산 및 URL 호출에서 미디어 _동적으로_&#x200B;을(를) 제공하기 때문에 다른 시스템과 근본적으로 다릅니다. 요청하는 Dynamic Media URL 경로에는 에셋이 고객의 화면에 전달될 때 Adobe 게시 서버에 에셋을 표시하는 방법을 알려 주는 지침이 포함되어 있습니다. 예를 들어 동일한 단일 기본 에셋을 사용하여 크기, 형식, 해상도, 두께, 색상, 자르기 및 확대/축소 보기와 같은 효과를 변경하여 표현물을 무제한으로 즉시 전달할 수 있습니다.

이러한 고유한 전달 방법을 사용하면 크기나 대역폭에 관계없이 모든 화면에 일관된 품질 경험을 전달할 수 있습니다. 또한 풀 사이즈 비디오는 모든 화면 유형에 최적화되어 적응적으로 스트리밍되어 일관되고 고품질의 사용자 경험을 보장합니다.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![Adobe Dynamic Media은 서로 다른 크기 및 형식의 다른 미디어에 동일한 1차 이미지를 제공합니다](/help/assets/dynamic-media/assets/dm-oneasset-multioutput.png)
_Adobe Dynamic Media은 크기나 대역폭에 관계없이 모든 화면에 일관된 품질 환경을 제공합니다._

계속해서 읽으면서 &quot;하나의 기본 에셋 파일, 무궁한 가능성&quot;이라는 개념이 중요한 이유에 대해 자세히 알아볼 것입니다.

### 컨텐츠 전달 네트워크

이미지 에셋 또는 비디오 에셋으로 라이브를 시작할 준비가 되면 강력한 최상위 계층 전달 네트워크로 구성된 Dynamic Media의 백본에서 지원합니다. 이 네트워크는 매일 전 세계 수백 개의 클라이언트를 서비스합니다. 자산은 Akamai가 호스팅하는 콘텐츠 전송 네트워크(CDN)에서 배포됩니다. CDN은 네트워크로 연결된 컴퓨터 서비스 시스템으로서, 최종 사용자에게 컨텐츠, 특히 대용량 리치 미디어 컨텐츠를 전달하기 위해 투명하게 협력합니다.

CDN 시스템에서 웹 콘텐츠는 인터넷의 웹 캐시에 저장됩니다. 그런 다음 더 빠른 전달을 위해 웹 캐시에서 최종 사용자에게 전달됩니다. 따라서 누군가가 웹 페이지를 처음 다운로드하면 표시되는 자산이 CDN 캐시로 전달됩니다. 이러한 파일은 서버에 저장되므로 같은 영역에 있는 사용자가 다음에 웹 페이지에 액세스할 때 캐시된 동일한 콘텐츠가 더 빨리 전달됩니다. 콘텐츠가 사용자에게 더 가까이 위치하기 때문에 더 빠르게 전달됩니다. CDN은 웹 페이지 표시 속도를 향상시키지만 모든 인스턴스의 중앙 서버가 아닌 캐시 네트워크에서 콘텐츠가 전달되므로 중앙 서버의 대역폭 요구량을 줄입니다. 이러한 최적화된 흐름은 사용자 경험이 향상되었음을 의미하며 매출 증가로 연결됩니다.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

지금까지 CDN은 매달 3.5페타바이트의 트래픽을 고객에게 전달했습니다. 이 시스템은 하루에 520억 개의 자산을 제공할 수 있습니다. 이 숫자는 고객에게 제공된 864,000개의 이미지와 비디오에 해당합니다. _매초_.

### 스마트 이미징

Dynamic Media은 이미 CDN을 통해 에셋을 최적화하고 각 에셋이 모바일 및 데스크탑 시스템에서 빠르게 로드되도록 하는 훌륭한 작업을 수행합니다. 이를 위해 Dynamic Media에서는 이미지 사전 설정을 사용하여 이미지 품질을 정의합니다. 또한 전송하는 이미지 유형, 선명도 및 경험이나 페이지의 다양한 부분에 대한 기타 조각을 정의합니다.

하지만 이미지 사전 설정 외에 Dynamic Media에 값을 더 추가하려면 _스마트 이미징_&#x200B;을 사용하세요.

스마트 이미징은 고객의 브라우저 기능에 따라 이미지의 형식 및 파일 크기를 자동으로 최적화하여 더 나은 이미지 자산 전달 성능을 제공합니다. 기존 이미지 사전 설정에서 작동하며(이미지 사전 설정은 이 여정의 II부에서 논의됨) 게재 시 인텔리전스를 사용합니다.

이 인텔리전스는 브라우저 및 네트워크 연결 속도에 따라 이미지 파일 크기를 더 줄입니다. 이미지 자산은 페이지의 로드 시간 대부분을 차지하기 때문에 성능 향상은 다음과 같은 주요 비즈니스 지표에 철저한 영향을 줄 수 있습니다.

* 높은 전환
* 사이트에서 보낸 시간
* 사이트 바운스 비율 낮음

전체적으로 스마트 이미징을 사용하면 기존 이미지 사전 설정 설정 및 특정 최종 사용자 특성에 따라 22%~47%의 성능 향상을 기대할 수 있습니다. 마치 만지지 않은 것처럼 이미지 품질을 유지하면서 모든 것을 수행할 수 있습니다.

![스마트 이미징](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_스마트 이미징은 고객의 브라우저 기능과 네트워크 속도에 따라 이미지의 형식과 파일 크기를 자동으로 최적화합니다._

스마트 이미징은 사용자와 Adobe Dynamic Media 기술 지원 간에 조정된 노력이 필요하므로 기본적으로 켜져 있지 않습니다. 또한 스마트 이미징을 활성화하려면 CDN 캐시를 완전히 지워야 하며 이로 인해 시간이 다시 채워집니다. 스마트 이미징 사용에 관심이 있는 경우 기술 지원 티켓을 제출하여 Adobe과 협력하여 이 기능을 켤 수 있습니다. 그러면 기술 지원에서 스마트 이미징을 미리 시도할 수 있는 URL 매개 변수를 제공합니다. 웹 페이지 또는 이미지에서 사용할 수 있으므로 성능 및 절감 효과를 확인할 수 있습니다. 그런 다음 전체 사이트에 대해 스마트 이미징을 켤 수 있습니다.

### 응용 비디오 집합

페이지나 기본 페이지에 비디오가 있는 경우 고객이 해당 콘텐츠에 더 오래 관여하고 페이지에 더 오래 머무르는 경향이 있으므로 일반적으로 좋은 방법입니다. 이 동작은 Adobe이 수행한 분석을 통해 표시됩니다. 그러나 비디오는 복잡할 수 있습니다. 우선, 대용량 운영 파일이 있을 수 있습니다. 비디오 크기를 조정하고 전달하는 방법을 결정하는 것은 매우 복잡하며, 이러한 모든 방법은 보고 있는 장치와 대역폭에 관계없이 경험이 원활하게 실행될 수 있도록 하는 것입니다.

이 문제를 해결하기 위해 Dynamic Media에서는 _응용 비디오 집합_&#x200B;을 만들 수 있는 기능을 제공합니다.

응용 비디오 세트는 다른 비트율 및 형식으로 인코딩된 동일한 비디오 버전을 그룹화합니다.

시스템에 업로드하는 원본 기본 비디오부터 시작합니다. Dynamic Media은 자동으로 해당 비디오의 크기를 지정하거나 _코드 변환_&#x200B;합니다. 그런 다음, 배송 시 어떤 비디오 화면, 어떤 품질, 어떤 포맷을 사용할 것인지 지능적으로 결정하여 전화, 태블릿, 데스크탑 컴퓨터 중 하나로 전달한다.

예를 들어 iOS 모바일 장치에서 4G, 5G 또는 Wi-Fi와 같은 대역폭을 감지합니다. 그런 다음, 그것은 응용 비디오 세트 내의 다양한 비디오 비트 레이트 중에서 올바른 인코딩된 비디오를 자동으로 선택한다. 비디오는 모바일 장치, 태블릿 또는 데스크탑 컴퓨터로 스트리밍됩니다.

또한 네트워크 상태가 변경되면 비디오 품질이 자동으로 전환됩니다. 또한 고객이 데스크탑에서 전체 화면 모드로 전환하면 응용 비디오 세트가 더 나은 해상도를 사용하여 응답하므로 고객의 시청 환경이 향상됩니다.

응용 비디오 세트를 사용하면 여러 화면 및 장치에서 Dynamic Media 비디오를 재생하는 고객에게 부드럽고 고품질의 재생을 제공합니다. 이는 비디오에서 복잡성을 제거해 줍니다.

## Dynamic Media 사용 사례 {#dm-journey-b}

다음은 Dynamic Media이 긍정적인 고객 참여, 충성도, 전환 및 ROI 향상을 견인하는 데 도움이 되는 일반적인 사용 사례 문제 및 솔루션입니다.

### 사용 사례: 기본 파일 접근 방식

Dynamic Media의 가장 중요한 사용 사례 중 하나는 또한 가장 명백한 사용 사례 중 하나입니다. 즉, 페이지 및 경험의 가중치를 줄이고, 전달되는 이미지든 비디오든 관계없이 컨텐츠의 크기를 줄입니다.

다음은 일반적인 경험 또는 웹 페이지를 보여 줍니다. 페이지의 약 90%는 일반적으로 훨씬 무거운 파일인 이미지 및 비디오와 같은 리치 미디어로 구성됩니다.

![콘텐츠 페이지 두께](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
_일반적인 웹 페이지의 콘텐츠 페이지 가중치입니다._

나머지 10%는 HTML, CSS 코드 및 특정 태그입니다. 해당 페이지의 90% 가중치를 최적화하려고 하며 Dynamic Media이 그러한 노력에 도움이 됩니다. 앞에서 _무한한 가능성을 가진 기본 자산 파일 하나_&#x200B;의 개념에 대해 읽었습니다. 이 접근 방식은 전반적인 페이지 가중치를 줄이는 데 중요합니다. 하나의 기본 자산을 가져와서 제품 세부 사항 페이지, 썸네일 페이지, 장바구니 및 검색 그리드에서 사용할 수 있으므로 시간을 절약할 수 있습니다. 또한 경험 전반에 걸쳐 일관성을 보장합니다.

![기본 파일 접근 방식](/help/assets/dynamic-media/assets/dm-onefile.png)
_시계는 하나의 기본 에셋 파일이지만 여러 개의 렌디션이 있습니다(복사본이 아님)._

Dynamic Media이 하나의 파일로 해결하고 있는 문제와 해당 접근 방식에 대한 몇 가지 해결 방법을 자세히 살펴보겠습니다.

| **문제** | **Dynamic Media 솔루션** |
|---|---|
| 모든 자산을 만들고 저장합니다. | 단일 이미지 파일을 사용하여 전달하는 순간에만 필요한 변환을 자동으로 만들 수 있습니다. |
| 높은 스토리지 비용. | 에셋의 여러 사본을 만들고 저장할 필요가 없습니다. |
| 구속의 고리를 유지하는 데 어려움. | 장치에 최적화되고 일관된 경험의 전달을 보장합니다. |
| 버전 내역이 없습니다. | |
| 장치 간에 브랜드 경험이 일관되지 않습니다. | |
| 중복 에셋 생성에 대한 불필요한 비용입니다. | |

하나의 파일에 대해 생각하면 모든 종류의 경험에 대한 에셋을 만드는 것입니다. 시작 이미지가 한 개 있을 수 있으며 그 이미지의 변형을 20, 30 또는 40개 만들어야 하기 때문에 최종적으로 해당 저장 공간을 저장하고 비용을 지불해야 합니다.

그런 다음 올바른 이미지가 사용되고 있는지 확인해야 하며, 이는 브랜드 전반에 걸쳐 일관성을 유지하는 능력에 영향을 줄 수 있습니다. 또한 이미지를 찾을 수 없는 경우 다시 돌아가 해당 에셋을 복제해야 합니다.

Dynamic Media을 사용하면 해당 시작 이미지에서 즉석으로 이미지의 변형을 만들 수 있습니다. 이를 통해 기본 에셋으로 크리에이티브를 수행할 수 있으며 추가 콘텐츠를 만들기 위해 그래픽 디자인 아티스트나 사진 스튜디오와 왔다 갔다 할 필요가 없습니다. 그리고 그것은 돈과 시간을 절약하는 것이다.

단일 파일 접근 방식에서는 단일 기본 파일을 사용합니다. 그런 다음 사이트, 속성 및 경험에 필요한 버전 또는 렌디션을 고객이 제공하거나 확인하는 순간에만 만듭니다. 이러한 효율성으로 인해 자산에 필요한 스토리지 양이 크게 줄어들고 전반적인 워크플로우 복잡성이 줄어들 수 있습니다. 또한 Dynamic Media의 전달 시스템을 통해 모든 이미지와 비디오가 최적화되고, 빠르게 로드되며, 모든 화면과 장치에서 멋진 외관을 보장합니다.

### 사용 사례: 비디오

Dynamic Media이 해결하는 또 다른 사용 사례는 비디오입니다. 비디오는 복잡합니다. 관리가 어렵습니다. 비디오 파일은 고유한 파일 크기 때문에 저장하고 이동하기가 어렵습니다.

| **문제** | **Dynamic Media 솔루션** |
|---|---|
| 다양한 디바이스에 최적화된 비디오를 관리하고 전달하기 어렵습니다. | 모든 장치에 대해 자동으로 크기를 지정하는 단일 비디오를 사용합니다. |
| 사용자의 사용 가능한 대역폭으로 인해 비디오가 느려지거나 낮은 품질로 재생됩니다. | 사용 가능한 대역폭을 자동으로 감지하고 품질을 조정하여 고화질과 원활한 재생을 보장하는 HTML 플레이어를 통해 비디오를 제공합니다. |
| 여러 장치에서 양호한 표시 및 재생을 보장하기 위해 비디오의 모든 버전을 수동으로 만드는 것은 불가능하고 시간이 오래 걸립니다. | 간소화된 워크플로우를 통해 지루한 코드 변환 작업을 몇 시간 동안 수행할 필요가 없습니다. |
| | 가치 높은 작업을 위해 시간을 벌립니다. |

고객은 해결하고자 하는 다음과 같은 문제를 안고 Dynamic Media을 방문합니다.

&quot;_내 회사에 비디오가 있고 부서에서 비디오를 만드는 데 많은 비용을 들였지만 페이지에 비디오를 배치하거나 게재하는 것을 피했습니다. 테스트부터 영상의 질을 보장할 수 없거나, 실제 재생이 되더라도 안심할 수 없다는 이유에서였다. 그리고 궁극적으로 비즈니스의 브랜드 및 전환에 대한 해당 역할에 영향을 미칩니다._&quot;

Dynamic Media의 솔루션은 하나의 기본 비디오 파일을 가져와 Dynamic Media이 트랜스코딩 프로세스를 통해 모든 크기를 만들 수 있도록 하는 것입니다. 그런 다음 Dynamic Media의 지능형 비디오 플레이어와 페어링합니다. 이 워크플로는 기본 랜딩 페이지나 카테고리 또는 제품 세부 사항 페이지에서 해당 비디오를 사용하든 상관없이 전체적으로 일관성을 유지하고 고품질로 전달되도록 보장합니다.

다음은 고려해야 할 몇 가지 사용 사례입니다.

### 사용 사례: 신뢰할 수 있는 단일 소스

| **문제** | **Dynamic Media 솔루션** |
|---|---|
| 조직 전체에 분산되어 있는 디지털 에셋은 다른 팀 또는 비즈니스 단위로 분산되어 있습니다. | 모든 디지털 에셋을 중앙 위치에 저장하고 관리합니다. |
| 팀원은 로컬 버전을 다운로드하고 만듭니다. | 팀원은 단일 기본 파일을 사용하여 _및_&#x200B;을(를) 만들고 다양한 화면 크기 및 장치에서 필요한 모든 버전을 제공합니다. |
| 모든 경험 및 장치에 대해 생성된 단일 사용 에셋. | 일회성 자산을 제거하여 자산을 만드는 데 드는 시간과 비용을 절약할 수 있습니다. |

### 사용 사례: 리치 미디어를 위한 AI 기반 스마트 자르기

| **문제** | **Dynamic Media 솔루션** |
|---|---|
| 이미지 또는 비디오를 수동으로 그리기, 측정 및 잘라내어 초점을 강조 표시하고 모든 화면 크기 및 장치에서 적절히 표시하는 데 시간이 많이 소요되고 많은 시간이 소요됩니다. | Adobe Sensei AI 기능인 Dynamic Media의 스마트 자르기 를 사용하여 모든 이미지 또는 비디오에서 초점을 자동으로 감지하고 자르기 를 사용하여 유지합니다. |
| 영향력이 큰 경험을 만드는 데 더 잘 소요될 수 있는 손실 시간입니다. | 화면 크기에 관계없이 의도한 관심 영역을 캡처합니다. |
| 모든 경험 및 장치에 대해 생성된 단일 사용 에셋. | 번거로운 수작업을 없애고 어떤 장치나 화면에서도 보기 좋은 고품질의 빠른 로딩 이미지 및 비디오를 제공합니다. |

### 사용 사례: 대화형 미디어 작성

| **문제** | **Dynamic Media 솔루션** |
|---|---|
| 참여하거나, 충성도를 높이거나, 전환을 유도하지 않는 평평하고 정적인 고객 경험. | 기술 전문가가 아닌 사용자도 핫스팟, 회전 메뉴, 스핀 세트와 같은 대화형 요소를 쉽고 원활하게 추가하여 더욱 역동적이고 매력적인 경험을 할 수 있습니다. |
| 디지털 자산을 통한 제한된 투자 수익률 및 낮은 고객 경험. | 리치 미디어 환경에서 전환율과 투자 수익률을 높일 수 있습니다. |

## Dynamic Media 시스템을 통한 에셋 흐름 {#dm-journey-c}

다음은 Dynamic Media의 일반적인 워크플로우를 보여줍니다.

![Dynamic Media 워크플로](/help/assets/dynamic-media/assets/dm-workflow.png)
_에셋이 Dynamic Media 시스템을 통해 흐르는 방식._

생성 단계로 시작하여 끝에 기본 에셋을 갖게 하는 주요 목표를 가지고 있습니다. 이러한 기본 자산은 사진 촬영, 비디오 공급업체 또는 사용자가 만든 일부 오디오 파일일 수 있습니다. Adobe InDesign, Adobe Photoshop, Adobe Illustrator과 같은 Adobe의 Creative Suite 애플리케이션을 사용하여 콘텐츠 작업에 도움을 줄 수 있습니다.

작성 부분이 완료되면 Dynamic Media에 에셋을 업로드하여 작성 솔루션에 에셋을 넣습니다. Dynamic Media 내에서는 사이트의 다양한 웹 페이지에 대해 올바른 이미지 사전 설정과 뷰어를 배치해야 합니다.

또한 궁극적으로 이러한 모든 컨텐츠를 최적화하고 웹, 인쇄, 이메일, 데스크탑 및 모바일 디바이스에서 사용할 수 있도록 Dynamic Media 서버에 게시합니다.

### Dynamic Media에 에셋 업로드

기본 에셋 생성이 완료되면 Dynamic Media에 업로드합니다. 업로드하는 파일의 형식, 파일의 형식 및 크기는 Dynamic Media의 중요한 특성입니다. 업로드 시 하나의 파일 지원에서 최대 값을 얻어야 합니다.

예를 들어 아래 시계 이미지는 4560 x 3020픽셀입니다. 또한 해당 크기의 이미지는 사용할 수 없지만 계속 업로드할 수 있습니다. 이미지가 클수록 Dynamic Media에서 썸네일 렌디션까지 전달할 수 있는 품질이 향상됩니다. 기존 이미지의 해상도를 쉽게 _감소_&#x200B;할 수 있습니다. 그러나 이미지의 해상도를 _증가_&#x200B;하려고 하면 결과가 만족스럽지 않을 수 있습니다.

![Dynamic Media에 업로드하는 데 권장되는 형식](/help/assets/dynamic-media/assets/dm-upload-formats.png)
_자산 업로드에 대한 고려 사항._

Adobe은 자산을 무손실 형식으로 업로드하는 것을 권장합니다. 일반적으로 JPEG을 전달하거나 JPEG을 계속 저장할 때 시간이 지남에 따라 이미지 품질이 저하되기 시작하므로 JPEG을 피하는 것이 좋습니다. 사용할 수 있는 무손실 형식의 고해상도 이미지로 시작하려고 합니다. 이 형식은 일반적으로 TIFF 또는 PNG 파일입니다.

색상 공간에 대해 디지털 채널이나 웹 보기를 고려할 때 일반적으로 RGB(빨강, 녹색, 파랑)을 고려합니다.

대부분의 사용자는 CMYK에서 어떤 것을 게재하거나 CMYK에서 어떤 것을 게재하려고 하는지에 대해 전혀 생각하지 않습니다. 그 이유는 인쇄 된 물건을 배달할 때 색상 공간이 가장 많이 사용되기 때문이다. 그러나 Dynamic Media은 두 색상 공간 모두에서 전달할 수 있습니다.

창고 도매 클럽 등 아직도 인쇄를 하는 고객이 많다. 그리고 일주일에 한 번씩 전단을 인쇄하는 식료품점도 있다. 이러한 고객은 두 색상 공간 모두에 이미지가 있어야 합니다. 일반적으로 이 작업에는 RGB 이미지와 CMYK 이미지, 이렇게 두 개의 다른 이미지가 필요합니다. 그러나 CMYK 에셋을 Dynamic Media에 직접 업로드하고 Dynamic Media에서 이미지 사전 설정 또는 색상 프로필을 통해 자동으로 RGB 에셋을 게재하도록 할 수 있습니다. 여러 버전의 파일을 만들 필요가 없으므로 무한한 가능성을 가진 _하나의 기본 에셋 파일_&#x200B;의 개념을 유지할 수 있습니다.

<!-- **The Value of Renditioning??? or Demo portion** -->

### Publish 및 에셋 미리보기

Dynamic Media에 에셋을 업로드한 후에는 에셋을 선택한 다음 Dynamic Media에서 **[!UICONTROL Publish]** 또는 **[!UICONTROL 빠른 Publish]**&#x200B;을(를) 클릭하여 _게시_&#x200B;하는 것이 좋습니다. 모든 경험에서 에셋을 사용하려면 에셋을 게시해야 합니다. 에셋이 게시되면 복사하는 Dynamic Media 생성 URL을 사용하거나 페이지에 코드를 포함하여 웹 페이지에 포함할 수 있습니다.

자산을 수동으로 게시하는 것 외에도 업로드 시 사용자 개입 없이 자산을 즉시 게시하도록 Dynamic Media을 구성할 수 있습니다.

업로드 후 Dynamic Media에서 에셋의 렌디션을 미리 보는 방법은 여러 가지가 있습니다. 렌디션 미리 보기를 통해 고객이 보는 내용에 대한 아이디어를 얻을 수 있습니다. 일반적인 미리 보기 방법은 에셋을 선택한 다음 다음에 보이는 대로 _이미지 사전 설정_&#x200B;을 선택하여 해당 렌디션을 보는 것입니다.

![큰 이미지 사전 설정을 기반으로 자산의 렌디션을 미리 보는 중](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
_선택한 &quot;큰&quot; 이미지 사전 설정을 기반으로 자산의 렌디션을 미리 봅니다. URL 버튼을 클릭했습니다. 결과 URL 경로에 &quot;큰&quot; 이미지 사전 설정 이름이 포함되어 있으며 웹 페이지에서 사용할 수 있습니다._

위의 URL은 live입니다! [사용해 보기](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$){target="_blank"}.

에셋을 미리 보는 또 다른 방법은 이미지 에셋을 선택한 다음 다음에 표시된 대로 _뷰어_ 사전 설정을 선택하는 것입니다.

![확대/축소 세로 조명 뷰어 사전 설정을 기반으로 에셋 미리 보기](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
_선택한 &quot;ZoomVertical_light&quot; 뷰어 사전 설정을 기반으로 에셋을 미리 봅니다. 확대하기 위해 마우스 포인터(`+`)를 시계 위로 이동했습니다. URL 및 포함 단추를 확인합니다._

위의 렌디션은 라이브입니다! [사용해 보기](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&amp;config=jpearldemo/ZoomVertical_light){target="_blank"}.

## 선택 사항 - 자세히 알아보기

이 여정의 1부는 다양한 Dynamic Media 주제의 기본 사항을 다룹니다. 읽은 내용에 대해 자세히 알아보려면 아래 자료를 사용하여 개념을 자세히 살펴보십시오. 그렇지 않으면 여정 2부를 계속 진행할 수 있습니다. [이 Dynamic Media 여정의 다음 단계](#whats-next)를 참조하세요.

<!--
_Dynamic Media Help topics_

* [Work with Dynamic Media in Experience Manager](/help/assets/dynamic-media/dynamic-media.md)
* [About Smart Imaging](/help/assets/dynamic-media/imaging-faq.md)
* [How to create Adaptive Video Sets](/help/assets/dynamic-media/video.md)
* [Best practices for optimizing the quality of your images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)
* [How to upload assets](/help/assets/add-assets.md#upload-assets)
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to deliver Dynamic Media Assets](/help/assets/dynamic-media/delivering-dynamic-media-assets.md)
* [How to publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
* [Work with Selective Publish in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md) -->

_Dynamic Media 자습서_

* [Experience Manager Assets에서 Dynamic Media 사용](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [Adobe Experience Manager 컨텐츠 라이브러리](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager)(_Dynamic Media_&#x200B;에서 검색)

_Dynamic Media 뷰어_

* 각 뷰어의 [실시간 데모](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html)

## 이 Dynamic Media 여정의 다음 단계 {#whats-next}

이 여정의 II부분에서는 에셋이 전달될 때 무슨 일이 일어나고 있는지 더 잘 이해하기 위해 Dynamic Media URL을 면밀히 검사합니다. 또한 에셋을 렌더링할 이미지 사전 설정을 만드는 기본 사항에 대해 자세히 알아보고 이미지 세트, 스핀 세트 및 혼합 미디어 세트와 이러한 세트를 만드는 방법에 대해 알아봅니다.

[Dynamic Media 여정: 기본 사항, 파트 II](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d)(으)로 이동합니다.

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->