---
title: AEM 기술 재단
description: AEM이 구조화되고 JCR, Sling 및 OSGi와 같은 기본 기술이 포함된 AEM의 기술 기반에 대한 개요입니다.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '2144'
ht-degree: 1%

---

# AEM 기술 재단 {#aem-technical-foundations}

AEM은 입증되고 확장 가능하며 유연한 기술을 기반으로 구축된 강력한 플랫폼입니다. 이 문서는 AEM을 구성하는 다양한 부분에 대한 자세한 개요를 제공하며 전체 스택 AEM 개발자를 위한 기술 부록으로 작성되었습니다. 이 안내서는 시작 안내서가 아닙니다. AEM 개발을 처음 사용하는 경우 다음을 참조하십시오 [AEM Sites 개발 시작 - WKND 자습서](develop-wknd-tutorial.md) 첫 번째 단계로

>[!TIP]
>
>AEM의 핵심 기술로 이동하기 전에 Adobe은 [AEM Sites 개발 시작 - WKND 자습서.](develop-wknd-tutorial.md)

## 기본 사항 {#fundamentals}

최신 컨텐츠 관리 시스템인 AEM은 표준 웹 기술을 사용합니다.

* 요청-응답(XMLHttpRequest / XMLHttpResponse) 주기
* HTML
* CSS
* JavaScript

기본 콘텐츠 저장소 및 비즈니스 논리 계층은 Java™ 기술을 기반으로 구축됩니다.

* JCR
* 슬링
* OSGi

## Java™ 콘텐츠 저장소 {#java-content-repository}

JCR(Java™ Content Repository) 표준 [JSR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)는 콘텐츠 저장소 내의 세분화된 수준에서 양방향으로 콘텐츠에 액세스할 수 있는 공급업체 독립적 및 구현 독립적 방법을 지정합니다. 사양 리드는 Adobe 리서치(스위스) AG가 담당합니다.

다음 [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) 패키지, `javax.jcr.*` 저장소 콘텐츠에 직접 액세스하고 조작하는 데 사용됩니다.

AEM은 JCR을 기반으로 구축됩니다.

## 아파치 잭래빗 오크 {#jackrabbit-oak}

[아파치 잭래빗 오크](https://jackrabbit.apache.org/oak/docs/) 는 JCR 표준을 준수하는 최신 세계적 수준의 웹 사이트 및 기타 까다로운 콘텐츠 애플리케이션의 기반으로 사용할 수 있도록 확장 가능하고 성능이 뛰어난 계층형 콘텐츠 저장소의 구현입니다.

Jackrabbit Oak(간단히 Oak라고도 함)는 AEM이 구축된 JCR 표준의 구현입니다.

## Sling 요청 처리 {#sling-request-processing}

AEM은 다음을 사용하여 빌드되었습니다. [슬링](https://sling.apache.org/index.html)는 콘텐츠 중심 애플리케이션을 쉽게 개발할 수 있도록 해주는 REST 원칙을 기반으로 한 웹 애플리케이션 프레임워크입니다. Sling은 Apache Jackrabbit Oak와 같은 JCR 저장소를 데이터 저장소로 사용합니다. Sling은 Apache Software Foundation에 기여했습니다. 자세한 내용은 Apache에서 확인할 수 있습니다.

### Sling 소개 {#introduction-to-sling}

Sling을 사용하면 렌더링되는 콘텐츠 유형이 첫 번째 처리 고려 사항이 아닙니다. 대신 URL이 렌더링을 수행하는 스크립트를 찾을 수 있는 콘텐츠 객체로 확인되는지 여부가 주요 고려 사항입니다. 이 프로세스는 웹 콘텐츠 작성자가 자신의 요구 사항에 맞게 쉽게 사용자 지정된 페이지를 작성할 수 있도록 우수한 지원을 제공합니다.

이러한 유연성의 장점은 다양한 콘텐츠 요소의 범위가 있는 응용 프로그램이나 쉽게 사용자 지정할 수 있는 페이지가 필요한 경우에 명확하게 나타납니다. 특히 AEM과 같은 웹 컨텐츠 관리 시스템을 구현할 때 사용합니다.

다음을 참조하십시오 [15분 안에 Sling 살펴보기](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) Sling을 사용하여 개발하는 첫 번째 단계입니다.

다음 다이어그램에서는 Sling 스크립트 해상도를 설명합니다. HTTP 요청에서 콘텐츠 노드로, 콘텐츠 노드에서 리소스 유형으로, 리소스 유형에서 스크립트로 가져오는 방법과 사용 가능한 스크립팅 변수를 보여 줍니다.

![Apache Sling 스크립트 해상도 이해](assets/sling-cheatsheet-01.png)

다음 다이어그램에서는 사용할 수 있는 숨겨져 있지만 강력한 요청 매개 변수를 설명합니다 `SlingPostServlet`모든 POST 요청에 대한 기본 핸들러입니다. 처리기는 저장소에서 노드를 생성, 수정, 삭제, 복사 및 이동할 수 있는 무한한 옵션을 제공합니다.

![SlingPostServlet 사용](assets/sling-cheatsheet-02.png)

### Sling은 콘텐츠 중심적입니다. {#sling-is-content-centric}

Sling은 *내용 중심*. 즉, 각 (HTTP) 요청이 JCR 리소스(저장소 노드) 형태로 콘텐츠에 매핑되므로 콘텐츠에 처리가 집중됩니다.

* 첫 번째 타겟은 콘텐츠를 보유하는 리소스(JCR 노드)입니다
* 두 번째로, 표시 또는 스크립트는 요청의 특정 부분(예: 선택기 및/또는 확장)이 있는 리소스 속성에서 가져옵니다

### RESTful Sling {#restful-sling}

Sling은 콘텐츠 중심의 철학을 바탕으로 REST 기반 서버를 구축하여 웹 애플리케이션 프레임워크에 새로운 개념을 도입했습니다. 장점은 다음과 같습니다.

* 표면뿐만 아니라 RESTful입니다. 리소스와 표현은 서버 내부에서 올바르게 모델링됩니다.
* 하나 이상의 데이터 모델 제거
   * 리소스에 액세스하려면 다른 컨텐츠 관리 프레임워크에서 URL 구조, 비즈니스 객체, DB 스키마가 필요할 수 있습니다.
   * Sling을 사용하면 다음과 같이 줄어듭니다. URL = resource = JCR 구조

### URL 분해 {#url-decomposition}

Sling에서 처리는 사용자 요청의 URL에 의해 결정됩니다. 적절한 스크립트로 표시할 콘텐츠를 정의하고 URL에서 정보를 추출합니다.

다음 URL 분석:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

이를 복합 부품으로 분류할 수 있습니다.

| 프로토콜 | 호스트 |  | 콘텐츠 경로 | 선택기 | 확장 |  | 접미사 |  | 매개 변수 |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **프로토콜** - HTTPS
* **호스트** - 사이트의 도메인
* **콘텐츠 경로** - 렌더링할 콘텐츠를 지정하고 확장과 함께 사용되는 경로입니다. 이 예에서 는 로 변환됩니다. `tools/spy.html`
* **선택기** - 콘텐츠를 렌더링하는 대체 방법에 사용됩니다. 이 예에서는 프린터에 적합한 A4 버전.
* **확장** - 콘텐츠 형식 - 렌더링에 사용할 스크립트도 지정합니다.
* **접미사** - 추가 정보를 지정하는 데 사용할 수 있습니다.
* **매개 변수** - 다이내믹 컨텐츠에 필요한 모든 매개 변수

#### URL에서 컨텐츠 및 스크립트로 {#from-url-to-content-and-scripts}

URL 분해의 원칙 사용:

* 매핑은 요청에서 추출된 콘텐츠 경로를 사용하여 리소스를 찾습니다.
* 적절한 리소스가 있으면 sling 리소스 유형이 추출되고, 콘텐츠 렌더링에 사용할 스크립트를 찾는 데 사용됩니다.

다음 그림은 사용된 메커니즘을 보여 줍니다. 이 메커니즘에 대해서는 다음 섹션에서 자세히 설명합니다.

![URL 매핑 메커니즘](assets/url-mapping.png)

Sling을 사용하여 특정 엔티티를 렌더링하는 스크립트를 지정합니다( `sling:resourceType` JCR 노드의 속성). 이 메커니즘은 리소스가 여러 변환을 가질 수 있으므로 스크립트가 데이터 엔티티에 액세스하는 것(PHP 스크립트의 SQL 문처럼)보다 더 많은 자유를 제공합니다.

#### 리소스에 요청 매핑 {#mapping-requests-to-resources}

요청이 분류되고 필요한 정보가 추출됩니다. 요청된 리소스(컨텐츠 노드)에 대해 저장소가 검색됩니다.

* 첫 번째 Sling은 노드가 요청에 지정된 위치에 있는지 확인합니다. 예: `../content/corporate/jobs/developer.html`
* 노드를 찾을 수 없으면 확장이 삭제되고 검색이 반복됩니다. 예를 들면 다음과 같습니다. `../content/corporate/jobs/developer`
* 노드를 찾을 수 없으면 Sling은 http 코드 404(찾을 수 없음)를 반환합니다.

또한 Sling을 사용하면 JCR 노드 이외의 항목을 리소스가 될 수 있지만 이 기능은 고급 기능입니다.

### 스크립트 찾기 {#locating-the-script}

적절한 리소스(콘텐츠 노드)가 있는 경우 **sling 리소스 유형** 가 추출됩니다. 이 경로는 콘텐츠를 렌더링하는 데 사용할 스크립트를 찾습니다.

에 의해 지정된 경로 `sling:resourceType` 다음 중 하나일 수 있습니다.

* 절대
* 구성 매개 변수 관련

>[!TIP]
>
>상대 경로는 이동성을 높이므로 Adobe에서 권장합니다.

모든 Sling 스크립트는 다음 중 하나의 하위 폴더에 저장됩니다. `/apps` (변경 가능, 사용자 스크립트) 또는 `/libs` (변경할 수 없음, 시스템 스크립트) - 이 순서로 검색됩니다.

몇 가지 주목할 사항은 다음과 같습니다.

* 메서드(GET, POST)가 필요한 경우 예를 들어 HTTP 사양에 따라 대문자로 지정됩니다. `jobs.POST.esp`
* 다양한 스크립트 엔진이 지원되지만, 일반적인 권장 스크립트는 HTL 및 JavaScript입니다.

지정된 AEM 인스턴스에서 지원하는 스크립트 엔진 목록이 Felix 관리 콘솔( `http://<host>:<port>/system/console/slingscripting`).

앞의 예를 사용하여 `sling:resourceType` 은(는) `hr/jobs` 다음 기간:

* 다음으로 끝나는 GET/HEAD 요청 및 URL `.html` (기본 요청 유형, 기본 형식)
   * 스크립트는 `/apps/hr/jobs/jobs.esp`; 의 마지막 섹션 `sling:resourceType` 는 파일 이름을 생성합니다.
* POST 요청(GET/HEAD을 제외한 모든 요청 유형, 메서드 이름은 대문자로 지정)
   * POST은 스크립트 이름에 사용됩니다.
   * 스크립트는 `/apps/hr/jobs/jobs.POST.esp`.
* 다음으로 끝나지 않는 다른 형식의 URL `.html`
   * 예, `../content/corporate/jobs/developer.pdf`
   * 스크립트는 `/apps/hr/jobs/jobs.pdf.esp`; 접미사가 스크립트 이름에 추가됩니다.
* 선택기가 있는 URL
   * 선택기를 사용하여 동일한 콘텐츠를 대체 형식으로 표시할 수 있습니다. 예를 들어 프린터에 친숙한 버전, rss 피드 또는 요약이 있습니다.
   * 선택기가 다음과 같을 수 있는 프린터용 버전을 보는 경우 `print`에서와 같이 `../content/corporate/jobs/developer.print.html`
   * 스크립트는 `/apps/hr/jobs/jobs.print.esp`; 선택기가 스크립트 이름에 추가됩니다.
* 없는 경우 `sling:resourceType` 을 정의한 다음:
   * 컨텐츠 경로는 적절한 스크립트를 검색하는 데 사용됩니다(경로 기반 의 경우) `ResourceTypeProvider` 활성).
   * 예를 들어 다음 스크립트 `../content/corporate/jobs/developer.html` 에서 검색을 생성합니다. `/apps/content/corporate/jobs/`.
   * 기본 노드 유형이 사용됩니다.
* 스크립트가 전혀 없으면 기본 스크립트가 사용됩니다.
   * 기본 렌디션은 일반 텍스트(`.txt`), HTML(`.html`) 및 JSON(`.json`)를 입력하면 노드의 속성(적절하게 형식이 지정된)이 표시됩니다. 확장에 대한 기본 렌디션 `.res`또는 요청 확장이 없는 요청은 리소스를 스풀 처리하는 것입니다(가능한 경우).
* HTTP 오류 처리(코드 403 또는 404)의 경우 Sling은 다음 중 하나에서 스크립트를 찾습니다.
   * 위치 `/apps/sling/servlet/errorhandler` 사용자 지정된 스크립트용
   * 또는 표준 스크립트의 위치 `/libs/sling/servlet/errorhandler/404.jsp`

주어진 요청에 여러 스크립트가 적용되는 경우 가장 일치하는 스크립트를 선택합니다. 일치가 구체적일수록 더 좋습니다. 즉, 요청 확장이나 메서드 이름 일치에 관계없이 더 많은 선택기가 더 잘 일치합니다.

예를 들어 리소스에 대한 액세스 요청을 고려해 보십시오

* `/content/corporate/jobs/developer.print.a4.html`

유형

* `sling:resourceType="hr/jobs"`

올바른 위치에 다음 스크립트 목록이 있다고 가정합니다.

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

기본 설정 순서는 (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1)입니다.

리소스 유형(주로 로 정의됨) 외에도 `sling:resourceType` 속성)을 입력하면 리소스 슈퍼 유형도 있습니다. 이 유형은 `sling:resourceSuperType` 속성. 이러한 슈퍼 유형은 스크립트를 찾으려고 할 때도 고려됩니다. 리소스 슈퍼 유형의 장점은 기본 리소스 유형이 있는 리소스의 계층 구조를 형성할 수 있다는 것입니다 `sling/servlet/default` (기본 서블릿에서 사용)는 사실상 루트입니다.

리소스의 리소스 슈퍼 타입은 두 가지 방식으로 정의될 수 있다:

* 작성자 `sling:resourceSuperType` 리소스의 속성입니다.
* 작성자 `sling:resourceSuperType` 이 속한 노드의 속성 `sling:resourceType` 포인트.

예:

* `/`
   * `a`
   * `b`
      * `sling:resourceSuperType = a`
   * `c`
      * `sling:resourceSuperType = b`
   * `x`
      * `sling:resourceType = c`
   * `y`
      * `sling:resourceType = c`
      * `sling:resourceSuperType = a`

유형 계층:

* `/x`
   * 다음과 같음 `[ c, b, a, <default>]`
* 동안 `/y`
   * 계층 구조는 `[ c, a, <default>]`

이유는 `/y` 이(가) `sling:resourceSuperType` 반면, 속성 `/x` 에서 지원되지 않으므로 해당 슈퍼타입을 리소스 유형에서 가져옵니다.

#### Sling 스크립트를 직접 호출할 수 없음 {#sling-scripts-cannot-be-called-directly}

Sling 내에서 스크립트는 REST 서버의 엄격한 개념을 손상시킬 수 있으므로 직접 호출할 수 없습니다. 리소스와 표현을 혼합해야 합니다.

표현(스크립트)을 직접 호출하는 경우 스크립트 내에 리소스를 숨김으로써 프레임워크(Sling)가 더 이상 해당 리소스를 알지 못합니다. 따라서 다음과 같은 특정 기능이 손실됩니다.

* 다음을 포함한 GET 이외의 http 메서드 자동 처리:
   * sling 기본 구현으로 처리되는 POST, PUT, DELETE
   * 다음 `POST.jsp` 의 스크립트 `sling:resourceType` 위치
* 코드 아키텍처가 더 이상 깔끔하거나 구조화되지 않으므로 대규모 개발의 경우 매우 중요합니다

### Sling API {#sling-api}

Sling API 패키지 사용, `org.apache.sling.*`및 태그 라이브러리를 추가합니다.

### sling:include를 사용하여 기존 요소 참조 {#referencing-existing-elements-using-sling-include}

마지막으로 스크립트 내의 기존 요소를 참조해야 한다는 점을 고려해야 합니다.

보다 복잡한 스크립트(집계 스크립트)는 여러 리소스(예: 탐색, 사이드바, 바닥글, 목록 요소)에 액세스하고 *리소스*.

이 경우 `sling:include("/<path>/<resource>")` 명령입니다. 참조된 리소스의 정의를 효과적으로 포함합니다.

## OSGi {#osgi}

OSGi(Open Services Gateway Initiative)는 모듈식 애플리케이션과 라이브러리(Java™용 동적 모듈 시스템이라고도 함)를 개발 및 배포하기 위한 아키텍처를 정의합니다. OSGi 컨테이너를 사용하여 애플리케이션을 개별 모듈(추가 메타 정보가 있는 jar 파일이며 OSGi 용어로 번들이라고 함)로 분류하고 다음과 같이 애플리케이션 간의 상호 종속성을 관리할 수 있습니다.

* 컨테이너 내에 구현된 서비스
* 컨테이너와 애플리케이션 간의 계약

이러한 서비스 및 계약은 개별 요소가 협업을 위해 서로를 동적으로 발견할 수 있도록 하는 아키텍처를 제공합니다.

그런 다음 OSGi 프레임워크는 다시 시작할 필요 없이 이러한 번들의 동적 로딩/언로딩, 구성 및 제어를 제공합니다.

>[!NOTE]
>
>OSGi 기술에 대한 전체 정보는 [OSGi 웹사이트](https://www.osgi.org).
>
>특히 그들의 기초학력페이지에는 발표와 자습서 모음집이 실려 있다.

이 아키텍처를 사용하면 애플리케이션별 모듈로 Sling을 확장할 수 있습니다. Sling이므로 AEM은 [Apache Felix](https://felix.apache.org/documentation/index.html) osgi 구현. 둘 다 OSGi 프레임워크 내에서 실행되는 OSGi 번들의 컬렉션입니다.

이 기능을 사용하면 설치 내의 모든 패키지에 대해 다음 작업을 수행할 수 있습니다.

* 설치
* 시작
* 중지
* 업데이트
* 제거
* 최신 상태 보기
* 기호 이름, 버전 및 위치 등 특정 번들에 대한 자세한 정보에 액세스합니다

다음을 참조하십시오 [AEM에 대한 OSGi 구성 as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) 추가 정보.

## 저장소 내의 구조 {#structure-within-the-repository}

다음 목록은 저장소 내에 표시되는 구조에 대한 개요를 제공합니다.

* `/apps` - 애플리케이션 관련. 웹 사이트와 관련된 구성 요소 정의를 포함합니다. 개발하는 구성 요소는에서 사용할 수 있는 기본 구성 요소를 기반으로 할 수 있습니다. `/libs/core/wcm/components`.
* `/content` - 웹 사이트용으로 생성된 콘텐츠.
* `/etc`
* `/home` - 사용자 및 그룹 정보.
* `/libs` - AEM의 핵에 속하는 라이브러리 및 정의입니다. 의 하위 폴더 `/libs` 는 기본 AEM 기능을 나타냅니다. 의 콘텐츠 `/libs` 은(는) 수정할 수 없습니다. 웹 사이트별 기능은 다음과 같이 지정해야 합니다. `/apps`.
* `/tmp` - 임시 작업장
* `/var` - 감사 로그, 통계, 이벤트 처리 등 시스템에서 변경 및 업데이트되는 파일.

>[!CAUTION]
>
>이 구조 또는 구조 내의 파일에 대한 변경은 신중하게 이루어져야 합니다. 모든 변경 사항의 영향을 완전히 이해했는지 확인하십시오.
>
>의 아무 것도 변경하지 마십시오. `/libs` 경로. 구성 및 기타 변경 사항의 경우 다음에서 항목을 복사합니다. `/libs` 끝 `/apps` 내 모든 변경 내용 적용 `/apps`.
