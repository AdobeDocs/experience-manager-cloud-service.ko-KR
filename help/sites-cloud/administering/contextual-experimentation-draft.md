---
title: AEM as a Cloud Service의 컨텍스트 기반 실험
description: 실험 레일을 사용하여 사이트에 실험 기능을 추가하는 방법을 알아봅니다.
feature: Administering
role: Admin
source-git-commit: c948abf5391e61f01912f769b17e1ac0bd81a745
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 2%

---

# AEM as a Cloud Service의 컨텍스트 기반 실험 {#contextual-experimentation}

실험은 성능을 개선하고 사이트를 보다 효율적이고 능률적으로 만들기 위해 사이트의 디자인, 기능 및 코드를 테스트하는 방법입니다. 이는 콘텐츠 또는 기능을 변경하고 결과를 이전 버전과 비교하고 측정 가능한 효과가 있는 개선 사항을 선택하여 수행됩니다.

이를 올바르게 수행하면 전환, 참여 및 방문자 경험을 개선하는 강력한 패턴입니다. 일반적으로 이 방법을 채택하려고 할 때 피해야 할 두 가지 문제가 있습니다.

* **너무 적음**: 대부분의 회사에서는 충분한 실험을 하지 않고 있으며, 충분한 실험을 하면 의미 있는 결과를 얻기 위해 너무 적은 트래픽으로 실험합니다.
* **너무 느림**: 많은 실험 프레임워크는 사이트 속도가 너무 느려져서 새로운 전환 가능성이 느린 렌더링으로 인해 손실된 트래픽을 메우지 못하고 바운스됩니다.
* **너무 복잡함**: 새 실험을 설정하는 데 시간이 너무 오래 걸리면 더 적은 수의 실험이 실행됩니다.

Adobe Experience Manager에서 실행되는 사이트의 경우 개발자는 해당 사이트에 새로운 실험 기능을 추가할 수 있습니다. 이 접근 방식은 다른 실험 프레임워크와 다릅니다.

* 작성자가 이미 잘 알고 있는 도구를 사용하여 쉽게 테스트를 설정할 수 있으며 별도의 로그인이 필요하지 않습니다.
* AEM 전달 시스템에 긴밀하게 통합되어 있으며 사이트 속도가 느려지지 않고 코드 및 콘텐츠 변경에 탄력적입니다.
* 이를 통해 간단한 콘텐츠 변경 사항과 디자인, 기능 및 코드에 대한 실험을 테스트할 수 있습니다.

## 실험 레일 {#experimentation-rail}

실험 레일은 실험을 설정하는 기본 방법입니다. [Edge Delivery Services](/help/edge/overview.md) 컨텍스트 또는 [유니버설 편집기](/help/implementing/universal-editor/introduction.md)에서 프로젝트와 함께 사용할 수 있습니다. 따라서 Github 계정, SharePoint 또는 Google 드라이브와 같은 콘텐츠 저장소가 필요하며 [AEM Sidekick](https://www.aem.live/docs/sidekick) 플러그인도 필요합니다. 범용 편집기를 사용하려면 [AEM as a Cloud Service 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)에 액세스해야 합니다. [시작하기 - 유니버설 편집기 개발자 튜토리얼 페이지](https://www.aem.live/developer/tutorial)도 참조하세요.

>[!WARNING]
>실험 능력을 사용하기 위해서는 실험 엔진이 필요하다. 아래 단계를 구현하기 전에 엔진이 올바르게 설치되고 업데이트되었는지 확인하십시오. 자세한 내용은 다음 [설치 페이지](https://github.com/adobe/aem-experimentation/tree/v2?tab=readme-ov-file#installation)를 참조하세요.

### Edge Delivery Services에서 AEM Sidekick을 사용하여 실험 설정

Edge Delivery Services 프로젝트 내의 실험 레일 기능에 액세스하려면 [AEM Sidekick](https://www.aem.live/docs/sidekick) 플러그인이 필요합니다. 사이드 킥을 설정하려면 다음 단계를 따르십시오.

1. [AEM 사이드 킥 확장](https://chromewebstore.google.com/search/AEM%20Sidekick?hl=en-US&utm_source=ext_sidebar)을 추가하고 브라우저에 고정합니다.
1. 프로젝트 페이지를 미리 보기 모드로 엽니다.
1. AEM Sidekick 모음에서 설정 아이콘 ![설정](/help/sites-cloud/administering/assets/settings-1.png)을 클릭하고 **이 프로젝트 추가**&#x200B;를 선택합니다.
1. 실험 탭을 클릭하여 실험 레일을 엽니다.

### 유니버설 편집기에서 실험 설정

실험을 설정하기 전에 AEM 사이트를 콘텐츠 소스로 사용하여 범용 편집기에서 작성해야 한다는 점을 유의하십시오. 필요한 경우 [AEM을 컨텐츠 소스로 설정](https://www.aem.live/developer/ue-tutorial) 페이지에 나와 있는 자습서에 따라 기존 프로젝트를 컨텐츠 소스로 AEM Sites 사이트로 변환할 수 있습니다. 유니버설 편집기에서 실험을 설정할 준비가 되면 다음 단계를 따르십시오.

1. 유니버설 편집기에서 프로젝트를 열고 **A/B** 아이콘 확장을 확인합니다. 아이콘이 보이지 않는 경우 확장 관리자에서 기능을 활성화했는지 확인합니다. 활성화되지 않은 경우 활성화하거나 액세스를 요청하십시오.
   <!--1. Open your GitHub repository and check if the `plugins/experimention` folder exists. If not, you will need to set up the experimentation engine and MFE first (see the note above).-->
1. `fstab.yaml` 구성을 프로젝트 구성으로 지정하고 AEM 작성자 인스턴스에 연결합니다. [콘텐츠에 코드 연결](https://www.aem.live/developer/ue-tutorial#connect-your-code-to-your-content)도 참조하세요.
1. AEM 인스턴스를 열고 프로젝트가 준비되면 유니버설 편집기에서 직접 엽니다.
1. 실험을 실행할 프로젝트 및 인덱스 페이지를 열고 상단 막대에서 **편집**&#x200B;을 클릭합니다.
1. A/B 아이콘을 클릭하여 실험 확장을 엽니다.

>[!NOTE]
>프로젝트에 대한 실험을 설정하는 데 문제가 있는 경우 `aem-contextual-experimentation@adobe.com`에 문의하세요.

>[!NOTE]
>실험 엔진 설정 및 구성 방법에 대한 자세한 내용은 다음 [repository](https://github.com/adobe/aem-experimentation/tree/v2-ui)의 설명서 섹션을 참조하십시오.

## 실험 변형 및 일반 워크플로우 {#experiment-variants-workflow}

안내서의 나머지 부분을 따라 첫 번째 실험을 구성하기 전에 자주 사용되는 용어 중 일부는 익숙해야 합니다.

* **제어**: 실험을 실행하기 전의 경험입니다. 모든 실험에서는 제어 경험에 대한 개선 사항을 테스트하고 보여 주려고 합니다.
* **챌린저**: 제어 경험과 다르며 이에 대해 또는 제어 경험과 함께 &quot;테스트됨&quot;인 경험입니다.
* **변형**: 컨트롤 및 도전자는 모두 실험의 변형입니다.
* **통계적 유의성**: 도전자가 실제 통제 수준보다 나은지 평가합니다. 통계적 유의성 계산을 통해 행운을 배제하고 실제적인 효과가 있는 결과에 집중할 수 있다.

일반적으로 실험을 설정할 때는 기존 페이지를 컨트롤 페이지로 사용합니다. 그런 다음 실험 레일을 사용하여 처음에 제어 페이지의 사본인 챌린저 페이지를 만듭니다. 챌린저 페이지에서 컨텐츠 변형, 다양한 페이지 레이아웃, call-to-action(CTA) 등과 같은 다양한 항목을 테스트할 수 있습니다. 실험 레일에서 **변형 생성** 기능을 사용하여 AI에서 생성한 변형을 사용할 수도 있습니다.

각 실험에 대해 트래픽은 초기에 제어와 챌린저 간에 50/50으로 분할되지만 필요에 따라 트래픽이 분할되는 방법을 구성할 수 있습니다. 실험을 활성화하면 Operational Telemetry 서비스를 통해 데이터를 받습니다.

[작동 원격 분석 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)에서 제어 페이지와 챌린저 페이지의 방문자 수 등의 데이터를 수집합니다. 그런 다음 이 데이터를 사용하여 사이트에 필요한 개선 사항을 선택합니다. 웹 사이트의 확립된 디자인 언어를 사용하고 기존 기능을 사용하는 한 몇 분 안에 실험 변형을 설정하고 프로덕션으로 보낼 수 있어야 합니다.

>[!NOTE]
>플러그인은 식별될 수 있는 최종 사용자 데이터를 사용하거나 지속하지 않습니다. AEM as a Cloud Service에서 [Operational Telemetry 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)를 사용하는 기본 구성을 사용할 때는 최종 사용자 옵트인과 쿠키 동의가 필요하지 않습니다.

<!--### Frequently used terms {#frequently-used-terms}

Before following the rest of the guide to set up your first experiment, there are a few frequently used terms that you should be familiar with:

* **Control**: the experience prior to running the experiment. All experiments try to test and demonstrate an improvement over the control experience.
* **Challenger**: an experience that is different from the control experience and is "tested" against it or alongside it.
* **Variants**: control and challenger are all variants of an experiment.
* **Statistical Significance**: Evaluating if your challenger is really better than the control. Calculating statistical significance allows you to rule out luck and concentrate on the results that have a real effect. -->

### 유니버설 편집기에서 실험 만들기

유니버설 편집기에서 실험 기능을 사용하려면 먼저 위에 제시된 장에 설명된 대로 실험 레일을 설정하고 AEM 사이트를 콘텐츠 소스로 사용하는지 확인해야 합니다. 모든 것이 설정되면 다음 단계를 수행합니다.

### 유니버설 편집기에서 프로젝트 편집 시작

AEM 인스턴스를 열고 프로젝트가 준비되면 유니버설 편집기에서 직접 엽니다. 프로젝트를 준비하지 않았으며 AEM 사이트를 콘텐츠 소스로 설정한 경우 제공된 템플릿에서 새 표준 템플릿 프로젝트를 만듭니다. 리포지토리 또는 샘플 리포지토리를 연결하여 [https://github.com/sudo-buddy/ue-experimentation](https://github.com/sudo-buddy/ue-experimentation)할 수 있습니다. [AEM Sites을 콘텐츠로 설정](https://www.aem.live/developer/ue-tutorial) 페이지도 참조하십시오. 프로젝트가 설정되면 실험을 실행할 인덱스 페이지와 프로젝트를 열고 상단 막대에서 **편집**&#x200B;을 클릭합니다.

### A/B 확장 실행

**A/B** 아이콘을 클릭하여 실험 확장을 엽니다. 처음 사용할 때 인터페이스는 비어 있게 됩니다. 새 실험을 시작하려면 **새로 만들기**&#x200B;를 클릭하세요.

![a-b](/help/sites-cloud/administering/assets/a-b.png)

### 실험 세부 정보 구성

실험 값 중 일부는 다음과 같이 미리 정의됩니다.

**실험 유형**: A/B 테스트(현재는 지원된 유형만)
**최적화 중**: 전환(현재 지원되는 유형만)

실험의 이름을 `homepage-head-experiment`과 같이 좀 더 설명적인 이름으로 바꿀 수도 있습니다.

![실험-세부 정보](/help/sites-cloud/administering/assets/exp-values.png)

### 변형 추가 및 편집

계속하기 전에 위에 제시된 챌린저 및 변형 개념을 이해하십시오. 챌린저 변형을 만들려면 **새로 추가**&#x200B;를 클릭하세요.

* 동일한 탭의 챌린저 페이지로 이동합니다. 처음에는 컨트롤의 복사본일 뿐입니다.
* AI 지원을 사용하려면 직접 컨텍스트에서 페이지를 편집하거나 **변형 생성**&#x200B;을 클릭하세요.
* 변경한 후 확장으로 돌아가서 계속 진행하십시오.

![제어 변형](/help/sites-cloud/administering/assets/control-variant.png)

### 다른 속성 정의 및 초안으로 저장

실험 레일에서 시작 및 종료 날짜를 설정할 수 있습니다(둘 다 선택 사항). 시작 날짜가 제공되지 않으면 테스트가 게시되면 시작됩니다. 종료 날짜를 지정하지 않으면 테스트가 무기한 실행됩니다. 트래픽 분할을 조정할 수도 있습니다. 짝수 50/50 분할부터 시작하는 것이 좋습니다.

완료되면 **저장**&#x200B;을 클릭합니다. 이렇게 하면 실험이 초안으로 저장됩니다. 실험이 아직 활성화되지 않았습니다. **실험으로 돌아가기**&#x200B;를 클릭하여 개요로 돌아가거나 편집 인터페이스에 남아 실험을 활성화할 수 있습니다.

![초안](/help/sites-cloud/administering/assets/draft-save.png)

### 실험 활성화

준비가 되면 **활성화**&#x200B;를 클릭하여 실험을 시작하고 실험 페이지를 게시합니다. 테스트가 RUM(Operational Telemetry) 데이터 수집을 시작합니다(아래 장에서 자세한 내용 참조).

![활성화](/help/sites-cloud/administering/assets/activate.png)

### 모니터링 및 홍보

실험이 통계적 중요도에 도달하면 **승격**&#x200B;을 클릭하여 원하는 변형을 새 컨트롤로 만듭니다. 통계적 유의성에 도달하지 않더라도 활성화 후 언제든지 실험 변형을 홍보할 수 있다는 점을 명심하십시오.

### Edge Delivery Services에서 AEM Sidekick 실험 사용

AEM 사이드 킥이 설치되어 있는 경우 범용 편집기를 사용하지 않고 Edge Delivery 서비스에서 직접 프로젝트 실험 레일을 사용할 수 있습니다. 기능은 기본적으로 위에 설명된 A/B 테스트와 동일하지만 테스트를 편집하고 구성하려면 **미리 보기** 모드여야 합니다. 테스트 구성을 완료한 후 **활성화**&#x200B;를 클릭하여 제어와 챌린저 변형을 라이브로 푸시하고 원격 분석 데이터 수집을 시작합니다.

<!-- ### Experiment Identifier {#experiment-identifier}

Before you start, every experiment should have its own identifier for tracking and analytics purposes. A good starting point is to come up with a good, unique identifier for your experiment which will be the “Experiment ID”. Experiments are often numbered linearly or correlated to their Issue ID in an issue tracker or management system. Experiment IDs often use a prefix for the project, for example: `OPT-0134`, `EXP0004` or `CCX0076`.

### Create your Challenger Page {#create-challenger-page}

By convention, it is recommended to create a folder with a lowercase experiment ID in your `/experiments/ folder` (for example /experiments/ccx0076/). All the pages for the challenger variants are located in this folder. You create this folder in your local repository, for example, Sharepoint or Goggle Drive.

Your experiments folder should look something like this:

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

Once the folder is created, put a copy of your control page into that folder, and apply the changes on the page that you would like to test as part of your experiment variant (see video above). As an example let’s assume we have the following page on the website that we want to run an experiment on:

![control-page](/help/sites-cloud/administering/assets/control-page.png)

Your copy of the challenger placed in the experiments/experiment-id folder might look like this:

![challenger-page](/help/sites-cloud/administering/assets/challenger-page.png)

Preview and publish the challenger page using the sidekick and when you are done authoring the challenger page. The URL of the published challenger will be used in the next section - configuring the experiment.

### Configuring the experiment {#configure-experiment}

As soon as the challenger pages are ready to go, you need to go back to the control page and add metadata indicating that the page(s) are now part of the test.

There are two metadata rows that need to be added for an experiment variant.

* **Experiment**: containing your experiment ID.

* **Experiment Variants**: containing URLs for all the challengers of this page, separated by line breaks if you have more than one challenger.

See the example below:

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

For each experiment, the traffic is split between all the variants (control and challengers) and is automatically set to an even distribution. As such, if you have one challenger, there will automatically be an even 50/50 split between control and the challenger. If you have two challengers, you will automatically see a third of the traffic allocated to control and each challenger and so on.

You can override the traffic split by configuring the metadata. For more information on how you can customize the metadata used in your experiments, see the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Preview and Stage your Experiment Variants {#preview-stage-experiment}

As soon as you are ready to preview and stage your experiment, click Preview from the side-kick in the upper left side. Whenever you are previewing a page that has a running experiment, you will see the experimentation overlay in your `.aem.page` preview environment. The experimentation overlay lets you switch between the experiment variants and also provides traffic data.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

<!--- The data collection to measure the effectiveness of each variant is based on the [Operational Telemetry service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md). -->

<!--- ### Send your Experiment Variant to Production {#production-experiment}

Select the experiment pages and click Publish from the side-kick to push both the control and the challenger variant(s) live.

### Use Case Examples {#use-case-examples}

Presented below are several use case examples for experiment variants. Generally speaking, the basic worklflow will be similar to the one described above, with particular changes for each use case (like the number of challenger pages or metadata changes).

#### Full Page Experiment {#full-page}

You use a full page experiment to test between two variants of the same page. This is a full page variant of an a/b test where you have a control and a challenger page. You will replace the whole content of the "original" control page in the challenger variant with a different type of content. Keep in mind that by default the customer traffic is split evenly (50/50), but you can create custom splits if you like. -->

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

다음은 컨텍스트 실험을 사용할 때 고려해야 하는 몇 가지 측면입니다.

### 전환 {#conversion}

실험은 전환을 처리하도록 설정됩니다(페이지에서 클릭 가능한 요소를 추적합니다). 현재 페이지당 한 개의 실험으로 페이지 수준 실험을 지원합니다.

<!--### Make sure experiment Variants are not indexed {#experiment-not-indexed}

When running experiments, it is usually best practice to exclude the variants from the sitemap and ensure they are not indexed by search engines. This is because the variant page could be seen as duplicate content and negatively impact SEO.

You can do this by using either of the following two methods:

* If you centralize all experiments in a dedicated folder, like `/experiments`: make sure your bulk `metadata.xlsx` sheet contains a row with `/experiments/**` as path, and a robots column with the values `noindex`, `nofollow`.
* If you keep the experiment control and variants with the regular content: add a robots entry in the page metadata for each variant, with the value `noindex`, `nofollow`.-->

## 개발자 및 기술 리소스 {#dev-resources}

Adobe Experience Manager는 [운영 원격 측정](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)을 사용해 Adobe Experience Manager 기반 사이트의 기능 및 성능 문제의 발견 및 해결에 필요한 운영 데이터를 수집합니다. 운영 원격 분석 데이터를 사용하여 성능 문제를 진단할 수 있습니다. 운영 원격 분석은 샘플링을 통해 방문자의 개인 정보를 보존합니다(모든 페이지 보기 중 일부만 모니터링됨).

### 개인 정보 {#privacy-experimentation}

[AEM as a Cloud Service의 작동 원격 분석 서비스](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)는 방문자 개인 정보를 유지하고 데이터 수집을 최소화하도록 설계되었습니다. 이는 Adobe이 방문자로서 귀하에 대한 개인 정보나 귀하에게 다시 추적할 수 있는 정보를 수집하려고 시도하지 않음을 의미합니다. 사이트 운영자는 아래 수집된 데이터 항목을 검토하여 동의가 필요한지 파악합니다.
AEM Operational Telemetry에서는 사용 지표를 수집하기 위해 쿠키나 `localStorage`, `sessionStorage` 등과 같은 클라이언트측 상태 또는 ID를 사용하지 않습니다. 데이터는 픽셀이나 유사한 기술을 통해서가 아니라 `Navigator.sendBeacon` 호출을 통해 투명하게 제출됩니다. 샘플링된 데이터를 캡처할 목적으로 IP 주소, 사용자 에이전트 문자열 또는 기타 모든 데이터를 통해 장치 또는 개인을 &quot;지문&quot;으로 인쇄할 수 없습니다.

운영 원격 분석 데이터 수집에 개인 데이터를 추가하는 것은 허용되지 않으며, 운영 원격 분석 데이터를 꼭 필요한 경우를 초과하는 사용 사례에 사용할 수도 없습니다.
