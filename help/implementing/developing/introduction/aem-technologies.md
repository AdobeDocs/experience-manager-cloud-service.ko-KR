---
title: AEM 기술 기반
description: AEM이 JCR, Sling 및 OSGi와 같은 구조화되고 기본적인 기술을 제공하는 방법을 포함하여 AEM의 기술 기반에 대한 개요입니다.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
source-git-commit: 8ba7968ee7f4d3c808740054bf841dbaf9dd4254
workflow-type: tm+mt
source-wordcount: '2188'
ht-degree: 0%

---

# AEM 기술 기본 사항 {#aem-technical-foundations}

AEM은 검증된 확장성과 유연한 기술을 기반으로 구축된 강력한 플랫폼입니다. 이 문서에서는 AEM을 구성하는 다양한 부품에 대한 세부 개요를 제공하며 전체 스택 AEM 개발자를 위한 기술 부록으로 작성됩니다. 시작하기 안내서로 의도된 것이 아닙니다. AEM 개발을 처음 사용하는 경우 첫 번째 단계로 [AEM Sites 개발 시작 - WKND 자습서](develop-wknd-tutorial.md)를 참조하십시오.

>[!TIP]
>
>AEM의 핵심 기술로 이동하기 전에 Adobe은 [AEM Sites 개발 시작 - WKND 자습서를 완료하는 것이 좋습니다.](develop-wknd-tutorial.md)

## 기본 사항 {#fundamentals}

AEM은 최신 컨텐츠 관리 시스템으로 표준 웹 기술을 사용합니다.

* request-response(XMLHttpRequest / XMLHttpResponse) 주기
* HTML
* CSS
* JavaScript

기본 컨텐츠 저장소 및 비즈니스 논리 계층은 Java 기술을 기반으로 구축됩니다.

* JCR
* 슬링
* OSGi

## Java 컨텐츠 저장소 {#java-content-repository}

JCR(Java Content Repository) 표준 [JSR 283](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/index.html) 은 컨텐츠 리포지토리 내의 세부 수준에서 양방향 컨텐츠에 액세스할 수 있도록 공급업체에 독립적이고 구현에 독립적인 방법을 지정합니다. 사양 리드는 Adobe 리서치(스위스) AG에 의해 소유됩니다.

[JCR API 2.0](https://docs.adobe.com/content/docs/en/spec/javax.jcr/javadocs/jcr-2.0/index.html) 패키지, `javax.jcr.*`는 저장소 컨텐츠의 직접 액세스 및 조작에 사용됩니다.

AEM은 JCR을 기반으로 구축됩니다.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit ](https://jackrabbit.apache.org/oak/) Oak는 JCR 표준을 준수하는 최신 세계적 수준의 웹 사이트 및 기타 까다로운 컨텐츠 애플리케이션의 기반으로서 사용하기 위한 확장 가능하고 고성능 계층 컨텐츠 리포지토리의 구현입니다.

Jackrabbit Oak(Oak라고도 함)는 AEM이 빌드되는 JCR 표준의 구현입니다.

## Sling 요청 처리 {#sling-request-processing}

AEM은 컨텐츠 중심 애플리케이션을 쉽게 개발할 수 있도록 REST 원칙을 기반으로 하는 웹 애플리케이션 프레임워크인 [Sling](https://sling.apache.org/site/index.html)을 사용하여 구축됩니다. Sling은 Apache Jackrabbit Oak와 같은 JCR 저장소를 데이터 저장소로 사용합니다. Sling은 Apache Software Foundation에 기여하여 Apache에서 추가 정보를 찾을 수 있습니다.

### Sling 소개 {#introduction-to-sling}

Sling을 사용하면 렌더링할 컨텐츠의 유형이 첫 번째 처리 고려 사항이 아닙니다. 대신 기본 고려 사항은 URL이 렌더링을 수행할 스크립트를 찾을 수 있는 콘텐츠 개체로 확인되는지 여부입니다. 이 기능은 웹 컨텐츠 작성자가 요구 사항에 맞게 쉽게 사용자 지정된 페이지를 작성할 수 있도록 지원합니다.

이러한 유연성의 장점은 다양한 컨텐츠 요소를 사용하는 애플리케이션이나 사용자 지정할 수 있는 페이지를 필요로 할 때 두드러집니다. 특히 AEM과 같은 웹 컨텐츠 관리 시스템을 구현할 때

Sling을 사용하여 개발하는 첫 번째 단계는 [15분 내에 Sling 검색](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html)을 참조하십시오.

다음 다이어그램에서는 Sling 스크립트 해상도에 대해 설명합니다.이 보고서는 HTTP 요청에서 컨텐츠 노드로, 컨텐츠 노드에서 리소스 유형으로, 리소스 유형에서 스크립트로 가져오는 방법과 사용 가능한 스크립팅 변수를 보여줍니다.

![Apache Sling 스크립트 해상도 이해](assets/sling-cheatsheet-01.png)

다음 다이어그램은 저장소에서 노드를 만들기, 수정, 삭제, 복사 및 이동하기 위한 무제한 옵션을 제공하는 모든 POST 요청에 대한 기본 처리기인 `SlingPostServlet`을 처리할 때 사용할 수 있는 숨겨진 모든 강력한 요청 매개 변수에 대해 설명합니다.

![SlingPostServlet 사용](assets/sling-cheatsheet-02.png)

### Sling은 컨텐츠 중심 {#sling-is-content-centric}

Sling은 *컨텐츠 중심의*&#x200B;입니다. 즉, 각(HTTP) 요청이 JCR 리소스(저장소 노드) 형식의 컨텐츠에 매핑될 때 처리에 중점을 둡니다.

* 첫 번째 타겟은 컨텐츠를 포함하는 리소스(JCR 노드)입니다
* 둘째, 표현 또는 스크립트는 요청의 특정 부분(예: 선택기 및/또는 확장)과 함께 리소스 속성에서 배치됩니다

### RESTful Sling {#restful-sling}

Sling은 컨텐츠 중심 철학으로 REST 기반 서버를 구현하므로 웹 애플리케이션 프레임워크에 새로운 개념을 제공합니다. 장점은 다음과 같습니다.

* 표면에만 있는 것이 아니라 매우 RESTful;리소스 및 표현은 서버 내부에서 올바르게 모델링됩니다
* 하나 이상의 데이터 모델 제거
   * 다른 컨텐츠 관리 프레임워크를 사용하려면 리소스에 액세스하려면 URL 구조, 비즈니스 객체, DB 스키마가 필요할 수 있습니다.
   * Sling을 사용하면 다음과 같이 줄어듭니다.URL = resource = JCR 구조

### URL 분해 {#url-decomposition}

Sling에서 처리는 사용자 요청의 URL에 의해 결정됩니다. 적절한 스크립트로 표시할 컨텐츠를 정의합니다. 이를 위해 URL에서 정보가 추출됩니다.

다음 URL을 분석하는 경우:

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

우리는 그것을 그것의 복합 부분으로 나눌 수 있습니다.

| 프로토콜 | 호스트 |  | 컨텐츠 경로 | 선택기 | 확장 |  | 접미사 |  | 매개 변수 |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **프로토콜**  - HTTPS
* **호스트**  - 사이트의 도메인
* **컨텐츠 경로**  - 렌더링할 컨텐츠를 지정하는 경로 및 확장과 함께 사용됩니다.이 예제에서는  `tools/spy.html`
* **선택기**  - 컨텐츠를 렌더링하는 대체 방법에 사용됩니다.이 예에서는 A4 형식의 프린터 친화적인 버전
* **확장**  - 컨텐츠 형식;렌더링에 사용할 스크립트도 지정합니다
* **접미사**  - 추가 정보를 지정하는 데 사용할 수 있음
* **매개 변수**  - 동적 컨텐츠에 필요한 모든 매개 변수

#### URL에서 컨텐츠 및 스크립트 {#from-url-to-content-and-scripts} 까지입니다.

URL 분해의 원칙 사용:

* 매핑은 요청에서 추출된 컨텐츠 경로를 사용하여 리소스를 찾습니다.
* 해당 리소스가 있으면 sling 리소스 유형이 추출되어 컨텐츠 렌더링에 사용할 스크립트를 찾는 데 사용됩니다.

다음 그림은 사용된 메커니즘을 보여 줍니다. 이 메커니즘은 다음 섹션에서 자세히 설명합니다.

![URL 매핑 메커니즘](assets/url-mapping.png)

Sling을 사용하면 특정 엔티티를 렌더링하는 스크립트를 지정합니다(JCR 노드에서 `sling:resourceType` 속성을 설정하여). 이 메커니즘은 리소스가 여러 변환을 가질 수 있으므로 스크립트가 데이터 엔티티에 액세스하는 것보다 더 자유롭게 제공합니다(PHP 스크립트의 SQL 문처럼).

#### 요청에 요청 매핑 {#mapping-requests-to-resources}

요청이 분류되고 필요한 정보가 추출됩니다. 저장소가 요청된 리소스(컨텐츠 노드)에 대해 검색됩니다.

* 첫 번째 Sling은 요청에 지정된 위치에 노드가 있는지 확인합니다.예`../content/corporate/jobs/developer.html`
* 노드를 찾을 수 없으면 확장이 삭제되고 검색이 반복됩니다.예`../content/corporate/jobs/developer`
* 노드를 찾을 수 없으면 Sling은 http 코드 404(찾을 수 없음)를 반환합니다.

Sling은 JCR 노드 이외의 항목을 리소스화할 수도 있지만 고급 기능입니다.

### 스크립트 {#locating-the-script} 찾기

적절한 리소스(컨텐츠 노드)가 있으면 **sling 리소스 유형**&#x200B;이 추출됩니다. 컨텐츠 렌더링에 사용할 스크립트를 찾는 경로입니다.

`sling:resourceType`에 의해 지정된 경로는 다음 중 하나일 수 있습니다.

* 절대
* 구성 매개 변수에 상대적인

>[!TIP]
>
>상대 경로는 Adobe이 휴대성을 높이기 때문에 권장합니다.

모든 Sling 스크립트는 `/apps`(변경 가능, 사용자 스크립트) 또는 `/libs`(변경할 수 없는 시스템 스크립트)의 하위 폴더에 저장되며 이 순서로 검색됩니다.

주목할 다른 몇 가지 사항은 다음과 같습니다.

* 메서드(GET, POST)이 필요한 경우 HTTP 사양에 따라 대문자로 지정됩니다(예: ).`jobs.POST.esp`
* 다양한 스크립트 엔진이 지원되지만 일반적으로 권장되는 스크립트는 HTL 및 JavaScript입니다.

지정된 AEM 인스턴스에서 지원하는 스크립트 엔진 목록은 Felix Management Console( `http://<host>:<port>/system/console/slingscripting`)에 나열되어 있습니다.

앞의 예를 사용하여 `sling:resourceType`이 `hr/jobs`인 경우 다음을 수행합니다.

* `.html`(기본 요청 유형, 기본 형식)으로 끝나는 GET/HEAD 요청 및 URL
   * 스크립트는 `/apps/hr/jobs/jobs.esp`;`sling:resourceType` 의 마지막 섹션에서 파일 이름을 구성합니다.
* POST 요청(GET/HEAD을 제외한 모든 요청 유형, 메서드 이름은 대문자여야 함)
   * POST은 스크립트 이름에 사용됩니다.
   * 스크립트는 `/apps/hr/jobs/jobs.POST.esp`입니다.
* `.html`으로 끝나지 않고 다른 형식의 URL입니다.
   * 예 `../content/corporate/jobs/developer.pdf`
   * 스크립트는 `/apps/hr/jobs/jobs.pdf.esp`;접미사가 스크립트 이름에 추가됩니다.
* 선택기가 있는 URL
   * 선택기를 사용하여 동일한 콘텐츠를 대체 형식으로 표시할 수 있습니다. 예를 들어 프린터에 적합한 버전, rss 피드 또는 요약이 있습니다.
   * 선택기가 `print`일 수 있는 프린터 친화형 버전을 살펴보는 경우`../content/corporate/jobs/developer.print.html`
   * 스크립트는 `/apps/hr/jobs/jobs.print.esp`;선택기가 스크립트 이름에 추가됩니다.
* `sling:resourceType`이 정의되지 않은 경우:
   * 컨텐츠 경로는 적절한 스크립트를 검색하는 데 사용됩니다(경로 기반 `ResourceTypeProvider`이 활성화된 경우).
   * 예를 들어 `../content/corporate/jobs/developer.html`에 대한 스크립트는 `/apps/content/corporate/jobs/`에 검색을 생성합니다.
   * 기본 노드 유형이 사용됩니다.
* 스크립트를 전혀 찾을 수 없으면 기본 스크립트가 사용됩니다.
   * 기본 표현물은 현재 일반 텍스트(`.txt`), HTML(`.html`) 및 JSON(`.json`)으로 지원되며, 이 모든 표현물이 노드의 속성(적절한 형식)을 나열할 수 있습니다. 확장 `.res` 또는 요청 확장 없이 요청에 대한 기본 변환은 리소스를 스풀(가능한 경우)하는 것입니다.
* http 오류 처리(코드 403 또는 404)의 경우 Sling은 다음 중 하나에서 스크립트를 찾습니다.
   * 사용자 지정된 스크립트의 `/apps/sling/servlet/errorhandler` 위치
   * 또는 표준 스크립트 `/libs/sling/servlet/errorhandler/404.jsp`의 위치

지정된 요청에 여러 스크립트가 적용되는 경우 가장 일치하는 스크립트가 선택됩니다. 매치가 구체적일수록 효과적이다.즉, 요청 확장이나 메서드 이름이 일치하는 것과 관계없이 더 많은 선택기가 더 잘 일치합니다.

예를 들어 리소스에 액세스하기 위한 요청을 고려합니다

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

그런 다음 기본 설정의 순서는 (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1)입니다.

리소스 유형(주로 `sling:resourceType` 속성으로 정의됨) 외에도 리소스 슈퍼 유형도 있습니다. 일반적으로 `sling:resourceSuperType` 속성으로 표시됩니다. 이러한 수퍼 유형은 스크립트를 찾으려고 할 때도 고려됩니다. 리소스 슈퍼 유형의 장점은 기본 리소스 유형 `sling/servlet/default`(기본 서블릿에서 사용)이 효과적으로 루트인 리소스 계층을 형성할 수 있다는 것입니다.

리소스의 리소스 슈퍼 유형은 다음 두 가지 방법으로 정의할 수 있습니다.

* 리소스 `sling:resourceSuperType` 속성에 의해 결정됩니다.
* `sling:resourceType`이 가리키는 노드의 `sling:resourceSuperType` 속성에 의해 결정됩니다.

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

유형 계층 구조:

* `/x`
   * `[ c, b, a, <default>]`입니다.
* `/y`에 대해
   * 계층은 `[ c, a, <default>]`입니다.

이것은 `/y`에 `sling:resourceSuperType` 속성이 있지만 `/x`은 이 없으므로 해당 리소스 유형에서 상위 형식이 가져오므로 발생합니다.

#### Sling 스크립트를 직접 {#sling-scripts-cannot-be-called-directly} 호출할 수 없습니다.

Sling 내에서 스크립트를 직접 호출할 수 없습니다. 이렇게 하면 REST 서버의 엄격한 개념이 중단됩니다.리소스와 표현을 혼합합니다.

표현(스크립트)을 직접 호출하는 경우 스크립트 내에 리소스를 숨겨 프레임워크(Sling)가 더 이상 이 리소스에 대해 알지 못합니다. 따라서 특정 기능을 잃게 됩니다.

* 다음을 포함하여 GET 이외의 http 메서드 자동 처리:
   * sling 기본 구현으로 처리되는 POST, PUT, DELETE
   * `sling:resourceType` 위치의 `POST.jsp` 스크립트
* 코드 아키텍처는 더 이상 깨끗하거나 구조화되지 않습니다.대규모 개발을 위한 가장 중요한 요소

### Sling API {#sling-api}

Sling API 패키지, `org.apache.sling.*` 및 태그 라이브러리를 사용합니다.

### sling:include {#referencing-existing-elements-using-sling-include} 를 사용하여 기존 요소 참조

마지막으로 고려해야 할 사항은 스크립트 내에 기존 요소를 참조해야 하는 것입니다.

더 복잡한 스크립트(집계 스크립트)는 여러 리소스(예: 탐색, 사이드바, 바닥글, 목록의 요소)에 액세스해야 하며 *리소스*&#x200B;를 포함하여 액세스해야 할 수 있습니다.

이렇게 하려면 `sling:include("/<path>/<resource>")` 명령을 사용할 수 있습니다. 여기에는 참조된 리소스의 정의가 효과적으로 포함됩니다.

## OSGi {#osgi}

OSGi(Open Services Gateway Initiative)는 모듈식 애플리케이션 및 라이브러리(Java용 Dynamic Module System)를 개발 및 배포하는 아키텍처를 정의합니다. OSGi 컨테이너를 사용하면 애플리케이션을 개별 모듈(추가 메타 정보가 있는 jar 파일이며 OSGi 용어에서 번들이라고 함)로 분류하고 다음 기능을 사용하여 애플리케이션 간의 상호 종속성을 관리할 수 있습니다.

* 컨테이너 내에 구현된 서비스
* 컨테이너와 애플리케이션 간의 계약

이러한 서비스 및 계약은 개별 요소가 협업을 위해 동적으로 서로를 검색할 수 있도록 하는 아키텍처를 제공합니다.

그런 다음 OSGi 프레임워크를 통해 다시 시작할 필요 없이 이러한 번들을 동적으로 로드/언로드, 구성 및 제어할 수 있습니다.

>[!NOTE]
>
>OSGi 기술에 대한 전체 정보는 [OSGi 웹 사이트](https://www.osgi.org)에서 찾을 수 있습니다.
>
>특히, 기본 교육 페이지에는 프레젠테이션 및 자습서 컬렉션이 포함되어 있습니다.

이 아키텍처를 통해 Sling을 애플리케이션별 모듈로 확장할 수 있습니다. 따라서 AEM에서는 OSGi의 [Apache Felix](https://felix.apache.org/) 구현을 사용합니다. 둘 다 OSGi 프레임워크 내에서 실행되는 OSGi 번들 컬렉션입니다.

이렇게 하면 설치 내의 패키지에 대해 다음 작업을 수행할 수 있습니다.

*  설치
* 시작
* 중지
* 업데이트
* 제거
* 현재 상태를 참조하십시오
* 특정 번들에 대한 자세한 정보(예: 기호 이름, 버전, 위치 등)에 액세스합니다

자세한 내용은 [AEM as a Cloud Service에 대한 OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 참조하십시오.

## 저장소 내의 구조 {#structure-within-the-repository}

다음 목록은 리포지토리 내에 표시되는 구조에 대한 개요를 제공합니다.

* `/apps` - 응용 프로그램 관련웹 사이트와 관련된 구성 요소 정의를 포함합니다. 개발하는 구성 요소는 `/libs/core/wcm/components`에서 사용할 수 있는 기본 구성 요소를 기반으로 할 수 있습니다.
* `/content` - 웹 사이트용으로 만든 컨텐츠.
* `/etc`
* `/home` - 사용자 및 그룹 정보.
* `/libs` - AEM의 핵심에 속하는 라이브러리 및 정의. `/libs`의 하위 폴더는 기본 제공 AEM 기능을 나타냅니다. `/libs`의 컨텐츠는 수정할 수 없습니다. 웹 사이트에 대한 기능은 `/apps` 아래에 있어야 합니다.
* `/tmp` - 임시 작업장
* `/var` - 시스템에 의해 변경되고 업데이트되는 파일감사 로그, 통계, 이벤트 처리 등.

>[!CAUTION]
>
>이 구조 또는 그 안에 있는 파일을 신중하게 변경해야 합니다. 변경한 내용이 미치는 영향을 완전히 이해하도록 하십시오.
>
>`/libs` 경로에서 아무 것도 변경하면 안 됩니다. 구성 및 기타 변경 사항에 대해 `/libs`에서 `/apps`로 항목을 복사하고 `/apps` 내에서 변경합니다.
