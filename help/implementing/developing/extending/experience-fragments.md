---
title: 경험 조각 개요
description: Adobe Experience Manager as a Cloud Service용 경험 조각 확장
exl-id: bd4ea763-d17c-40a6-9a86-a24d7600229e
source-git-commit: 433e95366a8cc0baebb1ccd02a64603ab26dfb86
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 0%

---

# 경험 조각{#experience-fragments}

## 기본 사항 {#the-basics}

An [경험 조각](/help/sites-cloud/authoring/fragments/content-fragments.md) 는 페이지 내에서 참조할 수 있는 컨텐츠 및 레이아웃을 포함한 하나 이상의 구성 요소 그룹입니다.

경험 조각 기본, 변형 또는 두 가지 모두 는 다음을 사용합니다.

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

왜냐면.. `/libs/cq/experience-fragments/components/xfpage/xfpage.html`, 로 되돌아갑니다.

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## 일반 HTML 렌디션 {#the-plain-html-rendition}

사용 `.plain.` 선택기 URL에서 일반 HTML 렌디션에 액세스할 수 있습니다.

이 렌디션은 브라우저에서 사용할 수 있습니다. 그러나 주요 목적은 다른 애플리케이션(예: 서드파티 웹 앱, 사용자 지정 모바일 구현)이 URL만 사용하여 경험 조각의 콘텐츠에 직접 액세스할 수 있도록 하는 것입니다.

일반 HTML 렌디션은 다음과 같은 경로에 프로토콜, 호스트 및 컨텍스트 경로를 추가합니다.

* 유형: `src`, `href`, 또는 `action`

* 또는 다음으로 끝남: `-src`, 또는 `-href`

예:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>링크는 항상 게시 인스턴스를 참조합니다. 이 링크는 서드파티가 사용하도록 만들었으므로 작성자 인스턴스가 아닌 게시 인스턴스에서 항상 호출됩니다.
>
>자세한 내용은 [URL 표면화](/help/implementing/developing/tools/externalizer.md).

![일반 HTML 렌디션](assets/xf-14.png)

일반 렌디션 선택기에서는 추가 스크립트와 반대로 변환기를 사용합니다. 다음 [Sling 재작성기](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) 변환기로 사용됩니다. 이 변환기는 다음 위치에 구성됩니다.

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### HTML 렌디션 생성 구성 {#configuring-html-rendition-generation}

HTML 렌디션은 Sling 재작성기 파이프라인을 사용하여 생성됩니다. 파이프라인은에 정의되어 있습니다. `/libs/experience-fragments/config/rewriter/experiencefragments`. HTML 변환기는 다음 옵션을 지원합니다.

* `allowedCssClasses`
   * 최종 렌디션에 남겨야 하는 CSS 클래스와 일치하는 RegEx 표현식입니다.
   * 이 옵션은 고객이 특정 CSS 클래스를 삭제하려는 경우에 유용합니다
* `allowedTags`
   * 최종 렌디션에서 사용할 수 있는 HTML 태그 목록입니다.
   * 기본적으로 html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, noscript, div, link 및 script 태그가 허용됩니다(구성 불필요).

Adobe은 오버레이를 사용하여 재작성기를 구성할 것을 권장합니다. 다음을 참조하십시오 [AEM의 오버레이 as a Cloud Service](/help/implementing/developing/introduction/overlays.md).

## 경험 조각용 템플릿 {#templates-for-experience-fragments}

>[!CAUTION]
>
>***전용*** 편집 가능한 템플릿은 경험 조각에서 지원됩니다.
>
>경험 조각은 편집 가능한 템플릿을 기반으로 하는 페이지에서만 사용할 수 있습니다.

<!-- >***Only*** [editable templates](/help/sites-developing/page-templates-editable.md) are supported for Experience Fragments.
-->

경험 조각용 새 템플릿을 개발할 때 편집 가능한 템플릿에 대한 표준 사례를 따를 수 있습니다.

<!-- When developing a new template for Experience Fragments you can follow the standard practices for an [editable template](/help/sites-developing/page-templates-editable.md).
-->

에서 감지한 경험 조각 템플릿을 만들려면 **경험 조각 만들기** 마법사에서는 다음 규칙 세트 중 하나를 따라야 합니다.

1. 두 가지 모두:

   1. 템플릿의 리소스 유형(초기 노드)은 다음 항목에서 상속해야 합니다.
      `cq/experience-fragments/components/xfpage`

   1. 그리고 템플릿 이름은 다음으로 시작해야 합니다.
      `experience-fragments`
이 패턴을 통해 사용자는 /content/experience-fragments에서 경험 조각을 다음과 같이 만들 수 있습니다. `cq:allowedTemplates` 이 폴더의 속성에는 다음으로 시작하는 이름이 있는 모든 템플릿이 포함됩니다. `experience-fragment`. 고객은 이 속성을 업데이트하여 자체 명명 구성표 또는 템플릿 위치를 포함할 수 있습니다.

1. [허용된 템플릿](/help/sites-cloud/authoring/fragments/content-fragments.md#configure-allowed-templates-folder) 경험 조각 콘솔에서 구성할 수 있습니다.

<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## 경험 조각용 구성 요소 {#components-for-experience-fragments}

경험 조각과 함께/에서 사용할 구성 요소를 개발하는 것은 표준 사례를 따릅니다.

유일한 추가 구성은 구성 요소가 템플릿에서 허용되는지 확인하는 것입니다. 이 허용은 콘텐츠 정책을 통해 달성됩니다.

<!--
[Developing components](/help/sites-developing/components.md) for use with/in Experience Fragments follow standard practices.

The only additional configuration is to ensure that the components are [allowed on the template, this is achieved with the Content Policy](/help/sites-developing/page-templates-editable.md#content-policies).
-->

## 경험 조각 링크 재작성기 공급자 - HTML {#the-experience-fragment-link-rewriter-provider-html}

AEM에서는 경험 조각을 만들 수 있습니다. 경험 조각:

* 레이아웃과 함께 구성 요소 그룹으로 구성됩니다.
* 은 AEM 페이지와 별도로 존재할 수 있습니다.

이러한 그룹에 대한 사용 사례 중 하나는 Adobe Target과 같은 서드파티 터치포인트에 콘텐츠를 포함하는 것입니다.

### 기본 링크 재작성 {#default-link-rewriting}

<!--Using the [Export to Target](/help/sites-administering/experience-fragments-target.md) feature, you can:
-->

Export to Target 기능을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 경험 조각 만들기,
* 구성 요소를 추가합니다.
* 그런 다음 HTML 형식 또는 JSON 형식으로 Adobe Target 오퍼로 내보냅니다.

이 기능은 AEM의 작성자 인스턴스에서 활성화할 수 있습니다. 유효한 Adobe Target 구성 및 링크 외부화에 대한 구성이 필요합니다.

<!--
This feature can be [enabled on an author instance of AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). It requires a valid Adobe Target Configuration, and configurations for the Link Externalizer.
-->

링크 외부화는 Target 오퍼의 HTML 버전을 생성할 때 필요한 올바른 URL을 결정하고 이를 Adobe Target으로 전송하는 데 사용됩니다. Adobe Target에서는 Target HTML 오퍼 내의 모든 링크에 공개적으로 액세스할 수 있어야 하므로 이 프로세스가 필요합니다. 즉, 링크가 참조하는 모든 리소스 및 경험 조각 자체를 사용하려면 먼저 게시해야 합니다.

기본적으로 Target HTML 오퍼를 구성하면 요청이 AEM의 사용자 지정 Sling 선택기로 전송됩니다. 이 선택기를 호출합니다. `.nocloudconfigs.html`. 이름에서 알 수 있듯이, 경험 조각의 일반 HTML 렌더링을 만들지만, 클라우드 구성(불필요한 정보)은 포함하지 않습니다.

HTML 페이지를 생성하면 Sling 재작성기 파이프라인이 출력으로 수정됩니다.

1. 다음 `html`, `head`, 및 `body` 요소가 (으)로 대체됨 `div` 요소. 다음 `meta`, `noscript`, 및 `title` 요소가 제거됩니다(원본 요소의 하위 요소입니다). `head` 요소를 사용하고, 로 대체할 때 고려되지 않습니다. `div` element).

   이 프로세스는 HTML Target 오퍼가 Target 활동에 포함될 수 있도록 하기 위해 수행됩니다.

2. AEM은 HTML에 있는 모든 내부 링크를 수정하여 게시된 리소스를 가리키도록 합니다.

   수정할 링크를 판별하기 위해 AEM은 HTML 요소의 속성에 대해 다음 패턴을 따릅니다.

   1. `src` 속성
   2. `href` 속성
   3. `*-src` 속성(예: `data-src`, 및 `custom-src`)
   4. `*-href` 속성(예: `data-href`, `custom-href`, 및 `img-href`)

   >[!NOTE]
   >
   >HTML의 내부 링크는 상대 링크이지만 사용자 지정 구성 요소가 HTML에 전체 URL을 제공하는 경우가 있을 수 있습니다. 기본적으로 AEM은 이러한 완전한 URL을 무시하고 수정하지 않습니다.

   이러한 속성의 링크는 AEM 링크 외부화를 통해 실행됩니다 `publishLink()` 게시된 인스턴스에 있는 것처럼 URL을 다시 만들고 공개적으로 사용할 수 있도록 합니다.

기본 구현을 사용하는 경우 위에 설명된 프로세스로 경험 조각에서 Target 오퍼를 생성한 다음 Adobe Target으로 내보내기에 충분해야 합니다. 그러나 이 프로세스에서 설명되지 않는 사용 사례도 있습니다. 설명되지 않는 이러한 사례의 일부는 다음과 같습니다.

* 게시 인스턴스에서만 사용할 수 있는 Sling 매핑
* Dispatcher 리디렉션

이러한 사용 사례에 대해 AEM은 링크 재작성기 공급자 인터페이스를 제공합니다.

### 링크 재작성기 공급자 인터페이스 {#link-rewriter-provider-interface}

보다 복잡한 경우에는 다음을 포함하지 않습니다. [기본값](#default-link-rewriting), AEM은 링크 재작성기 공급자 인터페이스를 제공합니다. 이 인터페이스는 `ConsumerType` 번들에 서비스로 구현할 수 있는 인터페이스입니다. AEM이 경험 조각에서 렌더링한 대로 HTML 오퍼의 내부 링크에 대해 수행하는 수정 사항을 무시합니다. 이 인터페이스를 사용하면 비즈니스 요구 사항에 맞게 내부 HTML 링크를 다시 작성하는 프로세스를 사용자 지정할 수 있습니다.

이 인터페이스를 서비스로 구현하는 사용 사례의 예는 다음과 같습니다.

* Sling 매핑은 게시 인스턴스에서는 활성화되지만 작성자 인스턴스에서는 활성화되지 않습니다
* Dispatcher 또는 유사한 기술은 URL을 내부적으로 리디렉션하는 데 사용됩니다
* 다음 `sling:alias mechanisms` 리소스를 위한 위치

>[!NOTE]
>
>이 인터페이스는 생성된 Target 오퍼의 내부 HTML 링크만 처리합니다.

링크 재작성기 공급자 인터페이스( `ExperienceFragmentLinkRewriterProvider`)는 다음과 같습니다.

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### 링크 재작성기 공급자 인터페이스를 사용하는 방법 {#how-to-use-the-link-rewriter-provider-interface}

인터페이스를 사용하려면 먼저 링크 재작성기 공급자 인터페이스를 구현하는 새 서비스 구성 요소가 포함된 번들을 만들어야 합니다.

이 서비스는 다양한 링크에 액세스할 수 있도록 경험 조각을 Target으로 내보내기 재작성에 연결하는 데 사용됩니다.

예를 들어, `ComponentService`:

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

이제 서비스가 작동하려면 서비스 내에서 구현해야 하는 세 가지 방법이 있습니다.

* `[shouldRewrite](#shouldrewrite)`
* `[rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* `[getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

특정 경험 조각 변형에서 Target으로 내보내기에 대한 호출이 수행될 때 링크를 다시 작성해야 하는지 여부를 시스템에 표시합니다. 다음 메서드를 구현할 수 있습니다.

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

예:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

이 메서드는 Target으로 내보내기 시스템이 다시 작성하는 경험 조각 변형을 매개 변수로 수신합니다.

위의 예에서 다음을 다시 작성하려고 합니다.

* 링크 위치 `src`

* `href` 속성만

* 특정 경험 조각:
  `/content/experience-fragment/master`

Target으로 내보내기 시스템을 통과한 다른 경험 조각은 무시되며 이 서비스에서 구현한 변경 사항의 영향을 받지 않습니다.

#### rewriteLink {#rewritelink}

재작성 프로세스의 영향을 받는 경험 조각 변형의 경우 서비스가 링크 재작성을 처리하도록 계속 진행합니다. 내부 HTML에서 링크가 발견될 때마다 다음 메서드가 호출됩니다.

`rewriteLink(String link, String tag, String attribute)`

이 메서드는 를 입력할 때 매개 변수를 수신합니다.

* `link`
다음 `String` 처리 중인 링크의 표현입니다. 이 표현은 일반적으로 작성자 인스턴스의 리소스를 가리키는 상대 URL입니다.

* `tag`
처리 중인 HTML 요소의 이름입니다.

* `attribute`
정확한 속성 이름입니다.

예를 들어 Target으로 내보내기 시스템에서 이 요소를 처리하는 경우 다음을 정의할 수 있습니다 `CSSInclude` 다음으로:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

에 대한 호출 `rewriteLink()` 메서드는 다음 매개 변수를 사용하여 수행됩니다.

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

서비스를 만들 때, 의사 결정은 주어진 입력을 기반으로 하며 그에 따라 링크를 다시 작성합니다.

예를 들어 `/etc.clientlibs` 을(를) url의 일부로 추가하고 적절한 외부 도메인을 추가합니다. 작업을 간단하게 하려면 다음과 같이 서비스에 대한 Resource Resolver에 액세스할 수 있는 권한이 있는지 고려하십시오. `rewriteLinkExample2`:

>[!NOTE]
>
>서비스 사용자를 통해 리소스 확인자를 가져오는 방법에 대한 자세한 내용은 AEM의 서비스 사용자 를 참조하십시오.

<!--
>For more information on how to get a resource resolver through a service user see [Service Users in AEM](/help/sites-administering/security-service-users.md).
-->

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>위의 메서드가 를 반환하는 경우 `null`를 클릭한 다음 Target으로 내보내기 시스템은 리소스에 대한 상대 링크인 링크를 그대로 둡니다.

#### 우선 순위 - getPriority {#priorities-getpriority}

서로 다른 종류의 경험 조각을 만족하기 위해 여러 서비스가 필요하거나, 모든 경험 조각에 대한 외부화 및 매핑을 처리하는 일반 서비스가 있는 경우가 드물지 않습니다. 이러한 경우 사용할 서비스에 대한 충돌이 발생할 수 있으므로 AEM에서 다음을 정의할 수 있습니다. **우선 순위** 다른 서비스용. 우선 순위는 다음 방법을 사용하여 지정합니다.

* `getPriority()`

이 방법을 사용하면 다음과 같은 여러 서비스를 사용할 수 있습니다. `shouldRewrite()` 메서드는 동일한 경험 조각에 대해 true를 반환합니다. 에서 가장 높은 숫자를 반환하는 서비스 `getPriority()`메서드는 경험 조각 변형을 처리하는 서비스입니다.

예를 들어 `GenericLinkRewriterProvider` 모든 경험 조각에 대한 기본 매핑을 처리하고 `shouldRewrite()` 메서드 반환 `true` 모든 경험 조각 변형에 사용할 수 있습니다. 여러 특정 경험 조각의 경우 특수 처리가 필요할 수 있으므로 이 경우 다음을 제공할 수 있습니다. `SpecificLinkRewriterProvider` 대상 `shouldRewrite()` 메서드는 일부 경험 조각 변형에 대해서만 true를 반환합니다. 다음을 확인하십시오. `SpecificLinkRewriterProvider` 은(는) 이러한 경험 조각 변형을 처리하도록 선택되므로 에서 반환해야 합니다. `getPriority()` 메서드보다 높은 숫자 `GenericLinkRewriterProvider.`
