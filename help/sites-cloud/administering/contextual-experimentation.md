---
title: AEM as a Cloud Service의 컨텍스트 기반 실험
description: 실험 플러그인을 사용하여 사이트에 실험 기능을 추가하는 방법을 알아봅니다.
feature: Administering
role: Admin
source-git-commit: 1bb86516328d1405c1761f3c8b0494cc9cb64553
workflow-type: tm+mt
source-wordcount: '1797'
ht-degree: 0%

---


# 개요 {#overview}

>[!NOTE]
>현재 상황별 실험 기능은 Beta 프로그램을 통해서만 사용할 수 있습니다. Beta 프로그램에 액세스하려면 Adobe 지원 센터 또는 계정 관리자에게 문의하십시오.

실험은 성능을 개선하고 사이트를 보다 효율적이고 능률적으로 만들기 위해 사이트의 디자인, 기능 및 코드를 테스트하는 방법입니다. 이는 콘텐츠 또는 기능을 변경하고 결과를 이전 버전과 비교하고 측정 가능한 효과가 있는 개선 사항을 선택하여 수행됩니다.

이를 올바르게 수행하면 전환, 참여 및 방문자 경험을 개선하는 강력한 패턴입니다. 일반적으로 이 방법을 채택하려고 할 때 피해야 할 두 가지 문제가 있습니다.

* **너무 적음**: 대부분의 회사에서는 충분한 실험을 하지 않고 있으며, 충분한 실험을 하면 의미 있는 결과를 얻기 위해 너무 적은 트래픽으로 실험합니다.
* **너무 느림**: 많은 실험 프레임워크는 사이트 속도가 너무 느려져서 새로운 전환 가능성이 느린 렌더링으로 인해 손실된 트래픽을 만회할 수 없고 바운스됩니다.
* **너무 복잡함**: 새 실험을 설정하는 데 시간이 너무 오래 걸리면 더 적은 수의 실험이 실행됩니다.

Adobe Experience Manager에서 실행 중인 사이트의 경우 개발자가 사이트에 실험 기능을 추가할 수 있도록 하는 &quot;즉시 사용 가능한&quot; **실험 플러그인**&#x200B;이 있습니다. 이 접근 방식은 다른 실험 프레임워크와 다릅니다.

* 작성자가 이미 잘 알고 있는 도구를 사용하여 쉽게 테스트를 설정할 수 있으며 별도의 로그인이 필요하지 않습니다.
* AEM 전달 시스템에 긴밀하게 통합되어 있으며 사이트 속도가 느려지지 않고 코드 및 콘텐츠 변경에 탄력적입니다.
* 이를 통해 간단한 콘텐츠 변경 사항과 디자인, 기능 및 코드에 대한 실험을 테스트할 수 있습니다.

## 시작하기 전 {#before-start}

실험 플러그인이 [Edge Delivery Services](/help/edge/overview.md)의 컨텍스트 내에서 사용되므로 Github 계정이나 SharePoint 또는 Google 드라이브와 같은 콘텐츠 저장소가 필요하고 [AEM Sidekick](https://www.aem.live/docs/sidekick)도 필요합니다. [시작하기 - 유니버설 편집기 개발자 자습서 페이지](https://www.aem.live/developer/tutorial) 및 [시작하기 - 개발자 자습서](https://www.aem.live/developer/tutorial)를 참조하십시오.

설정이 모두 완료되면 **이 비디오를 시청하십시오** 제목 [즉시 실험](https://business.adobe.com/products/experience-manager/sites/testing-optimization.html)을 통해 실험 플러그인의 작동 방식에 대한 간단한 데모를 살펴보십시오.

## 자주 사용하는 용어 {#frequently-used-terms}

안내서의 나머지 부분을 따라 첫 번째 실험을 설정하기 전에 자주 사용하는 몇 가지 용어를 숙지해야 합니다.

* **제어**: 실험을 실행하기 전의 경험입니다. 모든 실험에서는 제어 경험에 대한 개선 사항을 테스트하고 보여 주려고 합니다.
* **챌린저**: 제어 경험과 다르며 이에 대해 또는 제어 경험과 함께 &quot;테스트됨&quot;인 경험입니다.
* **변형**: 컨트롤 및 도전자는 모두 실험의 변형입니다.
* **통계적 유의성**: 도전자가 실제 통제 수준보다 나은지 평가합니다. 통계적 유의성 계산을 통해 행운을 배제하고 실제적인 효과가 있는 결과에 집중할 수 있다.

## 실험 변형 및 일반 워크플로우 {#experiment-variants-workflow}

일반적으로 실험을 설정할 때는 기존 페이지를 컨트롤 페이지로 사용합니다. 그런 다음 일부 방문자에 대한 제어 페이지를 대체할 챌린저 페이지를 만듭니다. 챌린저 페이지에서 컨텐츠 변형, 다양한 페이지 레이아웃, call-to-action(CTA) 등과 같은 다양한 항목을 테스트할 수 있습니다. 컨트롤 페이지(아래 참조)에서 메타데이터 매개 변수를 추가하여 이러한 실험 변형을 구성할 수 있습니다.

그런 다음 [작동 원격 분석 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)에서 제어 페이지와 챌린저 페이지의 방문자 수 등의 데이터를 수집합니다. 그런 다음 이 데이터를 사용하여 사이트에 필요한 개선 사항을 선택합니다. 웹 사이트의 확립된 디자인 언어를 사용하고 기존 블록 기능을 사용하는 한 몇 분 안에 실험 변형을 설정하고 프로덕션으로 전송할 수 있어야 합니다.

>[!NOTE]
>플러그인은 식별될 수 있는 최종 사용자 데이터를 사용하거나 지속하지 않습니다. AEM as a Cloud Service에서 [Operational Telemetry 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)를 사용하는 기본 구성을 사용할 때는 최종 사용자 옵트인과 쿠키 동의가 필요하지 않습니다.

### 실험 식별자 {#experiment-identifier}

시작하기 전에 모든 실험에는 추적 및 분석 목적으로 자체 식별자가 있어야 합니다. 좋은 시작점은 &quot;실험 ID&quot;가 될 실험에 대한 좋고 고유한 식별자를 마련하는 것입니다. 실험에는 종종 문제 추적기 또는 관리 시스템에서 해당 문제 ID에 선형적으로 번호가 매겨지거나 상관 관계가 있습니다. 실험 ID는 종종 프로젝트 접두사를 사용합니다(예: OPT-0134, EXP0004 또는 CCX0076).

### 챌린저 페이지 만들기 {#create-challenger-page}

규칙에 따라 `/experiments/ folder`에 소문자 실험 ID를 가진 폴더를 만드는 것이 좋습니다(예: /experiments/ccx0076/). 챌린저 변형의 모든 페이지가 이 폴더에 있습니다. 이 폴더는 로컬 저장소(예: Sharepoint 또는 Goggle Drive)에 만듭니다.

실험 폴더는 다음과 같아야 합니다.

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

폴더가 만들어지면 제어 페이지의 사본을 해당 폴더에 넣고 테스트하려는 페이지의 변경 사항을 실험 변형의 일부로 적용합니다(위의 비디오 참조). 예를 들어 웹 사이트에 실험을 실행하려는 다음 페이지가 있다고 가정해 보겠습니다.

![control-page](/help/sites-cloud/administering/assets/control-page.png)

`experiments/<experiment-id>` 폴더에 배치된 도전자의 복사본은 다음과 같습니다.

![challenger-page](/help/sites-cloud/administering/assets/challenger-page.png)

사이드 킥을 사용하여 챌린저 페이지를 미리 보고 게시하며, 챌린저 페이지 작성이 완료되면 게시할 수 있습니다. 게시된 도전자의 URL은 다음 섹션( 실험 구성)에서 사용됩니다.

### 실험 구성 {#configure-experiment}

챌린저 페이지를 전송할 준비가 되면 제어 페이지로 돌아가 페이지가 이제 테스트의 일부임을 나타내는 메타데이터를 추가해야 합니다.

실험 변형을 위해 추가해야 하는 두 개의 메타데이터 행이 있습니다.

* **실험**: 실험 ID를 포함하고 있습니다.

* **실험 변형**: 도전자가 두 명 이상인 경우 줄 바꿈으로 구분된 이 페이지의 모든 도전자에 대한 URL을 포함합니다.

아래 예를 참조하십시오.

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

각 실험에 대해 트래픽은 모든 변형(제어와 챌린저) 간에 분할되고 자동으로 균등 분포로 설정됩니다. 이와 같이 도전자가 한 명일 경우 자동으로 제어와 도전자 간에 50/50씩 분할이 이루어집니다. 도전자가 두 명일 경우 제어 및 각 도전자에게 할당된 트래픽의 1/3을 자동으로 볼 수 있습니다.

메타데이터를 구성하여 트래픽 분할을 재정의할 수 있습니다. 실험에 사용되는 메타데이터를 사용자 지정하는 방법에 대한 자세한 내용은 다음 [페이지](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring)를 참조하십시오

### 실험 변형 미리 보기 및 스테이징 {#preview-stage-experiment}

실험을 미리 보고 스테이징할 준비가 되면 왼쪽 상단의 사이드 킥에서 미리 보기 를 클릭합니다. 실행 중인 실험이 있는 페이지를 미리 볼 때마다 `.aem.page` 미리 보기 환경에 실험 오버레이가 표시됩니다. 실험 오버레이를 사용하면 실험 변형 간을 전환할 수 있으며 트래픽 데이터도 제공합니다.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

각 변형의 효과를 측정하기 위한 데이터 수집은 [AEM as a Cloud Service의 Operational Telemetry 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)를 기반으로 합니다.

### 실험에 대한 변형을 프로덕션에 보내기 {#production-experiment}

실험 페이지를 선택하고 사이드 킥에서 게시 를 클릭하여 제어 및 챌린저 변형을 라이브로 모두 푸시합니다.

### 사용 사례 예 {#use-case-examples}

다음은 실험 변형에 대한 몇 가지 사용 사례입니다. 일반적으로 기본 워크플로우는 위에서 설명한 워크플로와 유사하며, 각 사용 사례에 대한 특정 변경 사항(예: 챌린저 페이지 또는 메타데이터 변경 사항)이 있습니다.

#### 전체 페이지 실험 {#full-page}

전체 페이지 실험을 사용하여 동일한 페이지의 두 변형 간을 테스트합니다. 컨트롤 및 챌린저 페이지가 있는 a/b 테스트의 전체 페이지 변형입니다. 챌린저 변형에 있는 &quot;원본&quot; 컨트롤 페이지의 전체 콘텐츠를 다른 유형의 콘텐츠로 교체합니다. 기본적으로 고객 트래픽은 균등하게(50/50) 분할되지만 원하는 경우 사용자 정의 분할을 생성할 수 있습니다.

<!--The metadata on the control page should look like this:

METADATA SETUP

#### Sections of the page Experiment {#sections-of-the-page}

This is experiment is similar to the full page one presented above but now the a/b test will contain changes to a section of the page instead of the whole content. For example, you can modify and test a carousel element, the call to action element and so on. As such, you will have a control and a challenger page, with the challenger page containing the modified elements. The metadata on the control page should look like this:

METADATA SETUP

#### Multi-path Experiment {#multi-path}

By leveraging the experimentation plug-in, you can set up a/b tests on several pages of your website at once. For example, on all product pages, photo galleries, all blog posts and so on.

The configuration logic is the same as above - you will create a control page and one or more challenger variants of that page. What changes in the multi-page use-case, is the following:

• You will create multiple control pages each with one or more variants.
• The control pages must have the same experiment ID in metadata field.

For example: We have 5 different production pages for which we need to set up an a/b test. We create 5 control pages (as detailed in the chapters above) and 5 (or more) challenger variants.

We then create an experiment ID, let’s say `prod-exp` and add this ID in the experiment metadata field for each control page. This basically means that all pages with the same ID are now “grouped”. We then assign the challenger variants for each control page, taking care to sequence them properly in case we have more than one variant for each control.

The metadata on the control page should look like this:

METADATA SETUP

#### Code-level experiments {#code-level}

Note that the examples above assume you have different content variants to serve, but if you want to run a pure code-based a/b test, this is achievable via:

Metadata

Experiment    Hero Test
Experiment Variants    2

This will create just two variants, without touching the content, and you'll be able to target those based on the `experiment-hero-test` and `variant-control/variant-challenger-1/variant-challenger-`2 CSS classes that will be set on the `<body>` element.

#### Browser based audience experiment {#browser-based}

You can create browser based experiments, where you deliver separate challenger pages depending on the browser used. You can, for example, serve a different challenger page to a Firefox user as opposed to a Chrome user. This is achieved by leveraging the audience parameter.

Once you configure the experiment, the target audience will be evaluated based on the context of the browser (client side) and limited to the browser APIs available. As such, you do not need to use server side third-party systems or customer profile data for your experiment.

Before you start authoring this experiment variant, the audience parameter needs to be defined in the project codebase. For more details, see ee the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

Once the audiences have been defined you are ready to author the experiment. As stated previously, let’s say you want to create a Firefox versus Chrome experiment where you will serve different pages depending on the browser.

You need two different challenger pages, so set up the experiment as follows:

1.Duplicate the Control page by right-clicking and copying it to the experiment folder. You need to copies, one for Firefox and one for Chrome.
2.Rename the copies. Give them specific names like “page-for-firefox”.
3.Change the content of the pages depending on what you need to serve on Firefox versus Chrome.
4.Change the metadata as explained in the section below.
5.Click Preview from the side-kick in the upper left side, to preview the changes.

The most important part when authoring this experiment is to change the metadata in the control page. Let’s say you defined the browser audiences in the codebase as: Audience: Firefox and Audience: Chrome. You need to edit the control page and add these audiences and point to the appropriate challenge page you set up previously. It should look similar to this:

Metadata
Title Control Page
Description This is the control page.
Experiment ExpBrowser
Experiment Variants `https://{ref}--{repo}--{org}.hlx.page/my-page-for-firefox https://{ref}--{repo}--{org}.hlx.page/my-page-for-chrome`
Audience: Firefox `https://{ref}--{repo}--{org}.hlx.page/page-for-firefox`
Audience: Chrome `https://{ref}--{repo}--{org}.hlx.page/page-for-chrome`

After this configuration, the users will be triaged based on the browser they connect with and the appropriate challenger page will be served.

Please keep in mind that the names above are only for illustration purposes. You can define the Audiences parameter and the challenger pages according to your needs, for example: Audience (Firefox) or Audience Firefox.-->

## 기타 고려 사항 {#other-considerations}

다음은 컨텍스트 실험을 사용할 때 고려해야 하는 몇 가지 다른 측면입니다.

### 전환 {#conversion}

실험은 전환을 처리하도록 설정됩니다(페이지에서 클릭 가능한 요소를 추적합니다). 모든 실험은 다음에 대해 정의되어야 합니다.

* 실험 유형
* 실험이 적용될 경험 차단
* 실험에 포함될 변형 수
* 각 변형의 구성은 무엇입니까

### 실험 변형이 색인화되지 않았는지 확인합니다. {#experiment-not-indexed}

실험을 실행할 때 일반적으로 사이트 맵에서 변형을 제외하고 검색 엔진에서 인덱싱되지 않도록 하는 것이 좋습니다. 변형 페이지가 중복된 콘텐츠로 인식되어 SEO에 부정적인 영향을 줄 수 있기 때문입니다.

다음 두 가지 방법 중 하나를 사용하여 이 작업을 수행할 수 있습니다.

* `/experiments`과(와) 같은 전용 폴더에서 모든 실험을 중앙 집중화하는 경우: 벌크 `metadata.xlsx` 시트에 `/experiments/**`이(가) 경로로 포함된 행과 `noindex`, `nofollow` 값이 있는 로봇 열이 있는지 확인하십시오.
* 정규 콘텐츠로 실험 제어와 변형을 유지하는 경우: 각 변형의 페이지 메타데이터에 값이 `noindex`, `nofollow`인 로봇 항목을 추가합니다.

## 개발자 및 기술 리소스 {#dev-resources}

Adobe Experience Manager에서 [운영 원격 분석] 사용(/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md

)를 사용하여 Adobe Experience Manager 기반 사이트에서 기능 및 성능 문제를 검색하고 수정하는 데 절대적으로 필요한 작업 데이터를 수집할 수 있습니다. 운영 원격 분석 데이터를 사용하여 성능 문제를 진단할 수 있습니다. 운영 원격 분석은 샘플링을 통해 방문자의 개인 정보를 보존합니다(모든 페이지 보기 중 일부만 모니터링됨).

### 개인 정보 {#privacy-experimentation}

[AEM as a Cloud Service의 작동 원격 분석 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)는 방문자 개인 정보를 유지하고 데이터 수집을 최소화하도록 설계되었습니다. 이는 Adobe이 방문자로서 귀하에 대한 개인 정보나 귀하에게 다시 추적할 수 있는 정보를 수집하려고 시도하지 않음을 의미합니다. 사이트 운영자는 아래 수집된 데이터 항목을 검토하여 동의가 필요한지 파악합니다.
AEM Operational Telemetry에서는 사용 지표를 수집하기 위해 쿠키나 `localStorage`, `sessionStorage` 등과 같은 클라이언트측 상태 또는 ID를 사용하지 않습니다. 데이터는 픽셀이나 유사한 기술을 통해서가 아니라 `Navigator.sendBeacon` 호출을 통해 투명하게 제출됩니다. 샘플링된 데이터를 캡처할 목적으로 IP 주소, 사용자 에이전트 문자열 또는 기타 모든 데이터를 통해 장치 또는 개인을 &quot;지문&quot;으로 인쇄할 수 없습니다.

운영 원격 분석 데이터 수집에 개인 데이터를 추가하는 것은 허용되지 않으며, 운영 원격 분석 데이터를 꼭 필요한 경우를 초과하는 사용 사례에 사용할 수도 없습니다.

### FAQ {#faq}

다음은 FAQ 목록입니다.

Q: 제어의 경우 10%, 도전의 경우 90%와 같은 내 실험의 변형 간 분할 비율을 조정할 수 있습니까?

예. 분할 비율은 [메타데이터](#configure-experiment)를 통해 구성할 수 있습니다.

Q: 텍스트와 이미지 모두에서 실험할 수 있습니까?

예. 변형은 완전히 다른 페이지일 수 있으므로 레이아웃 변경을 테스트할 수도 있습니다.
