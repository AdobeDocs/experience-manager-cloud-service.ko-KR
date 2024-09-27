---
title: 에지측 포함
description: 이제 Adobe 관리 CDN은 에지 수준의 동적 웹 컨텐츠 어셈블리용 마크업 언어인 ESI(Edge Side Includes)를 지원합니다.
feature: Dispatcher
exl-id: 35093477-2788-4f69-80a9-899f43567cae
role: Admin
source-git-commit: d70a8030ca6687b1839adc0ce1becdf366ec7170
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# 에지측 포함 {#edge-side-includes}

컨텐츠 전달 속도는 높은 TTL(Time to Live) 값으로 캐시 헤더를 설정하여 적극적으로 페이지를 캐싱할 때 도움이 됩니다. 페이지에 동적 콘텐츠가 포함되어 있어 자주 새로 고쳐야 하거나 캐시할 수 없는 경우에는 문제가 될 수 있습니다. 다행히도 포함된 HTML 페이지를 높은 TTL로 캐시할 수 있어 클라이언트측 Javascript를 통해 또는 CDN에서 보다 동적 콘텐츠 스니펫 가져오기를 지연할 수 있는 전략이 있습니다. 후자의 접근 방식은 AEM 게시로 렌더링된 사이트에 대해 지원되는 ESI(Edge Side Includes)라는 표준입니다. HTML은 CDN이 이러한 태그를 평가할 때까지 브라우저에 대한 페이지 제공을 지연하도록 지시하는 ESI 태그를 포함하여 원본(또는 TTL이 만료되지 않은 경우 CDN 캐시)에서 추가적인 더 동적인(더 낮은 TTL) 콘텐츠를 검색합니다.

Edge Side Includes가 유용한 사용 사례는 다음과 같습니다.

* 최종 사용자의 이름 또는 최종 사용자에 고유한 기타 정보를 표시합니다.
* 뉴스 기사 또는 주가와 같은 최근 정보 목록 표시

## ESI 구문 {#esi-syntax}

상위 페이지 `/content/page.html`에 코드 조각 `content/snippets/mysnippet.html`이(가) 포함된 경우 ESI 구문은 다음과 같습니다.

```
<html>
  <head>
      <title>My Site</title>
  </head>
  <body>
    <div id="content">
      <esi:include src="/content/snippets/mysnippet.html" />
    </div>
  </body>
</html>
```

자세한 내용은 [ESI 사양](https://www.w3.org/TR/esi-lang/)을 참조하십시오.

### 고려 사항 {#esi-syntax-considerations}

* 지원되는 ESI 태그는 다음과 같습니다. include, comment, remove.
* ESI 태그는 동시에 처리되지 않고 CDN에서 순차적으로 처리되므로 TTL이 낮은 페이지의 많은 ESI 태그는 최종 사용자의 경험에 지연을 추가할 수 있습니다.
* ESI의 최대 깊이(include processing)는 5입니다.
* 최대 총 ESI: 처리 조각 포함은 256입니다.


## Apache 구성 {#esi-apache}

ESI 태그가 있는 페이지가 있는 경우 Apache 구성에 다음 속성을 선언해야 합니다.

```
<LocationMatch "/parent-pages/*content/page.html">
   # disable dispatcher compression
   SetEnv no-gzip 1
   # enable esi processing 
   Header set x-aem-esi "on"
   # enable edgeCDN compression
   Header set x-aem-compress "on"

   # typically the main page is cached at the CDN
   Header always set Cache-Control "max-age=300"
 </LocationMatch>


<LocationMatch "/content/snippets/mysnippet.html">
  SetEnv no-gzip 1

  # typically the included page is either set to a lower TTL than the parent page, or not cached at all, as these 2 commented declarations show, respectively:
  #Header always set Cache-Control "no-cache"
  #Header always set Cache-Control "max-age=50"
 </LocationMatch> 
```

구성된 속성에는 다음과 같은 동작이 있습니다.

| 속성 | 동작 |
|-----------|--------------------------|
| **no-gzip** | 1로 설정하면 HTML 페이지가 apache에서 CDN으로 압축되지 않은 상태로 전송됩니다. CDN이 ESI 태그를 보고 평가할 수 있도록 압축되지 않은 CDN으로 콘텐츠를 보내야 하기 때문에 ESI에 필요합니다.<br/><br/>상위 페이지와 포함된 코드 조각 모두 no-gzip을 1로 설정해야 합니다.<br/><br/>이 설정은 요청의 `Accept-Encoding` 값을 기준으로 Apache가 다른 방법으로 사용했을 수 있는 압축 설정을 무시합니다. |
| **x-aem-esi** | &quot;on&quot;으로 설정하면 CDN이 상위 HTML 페이지의 ESI 태그를 평가합니다.  기본적으로 헤더는 설정되지 않습니다. |
| **x-aem-compress** | &quot;on&quot;으로 설정하면 CDN이 CDN의 콘텐츠를 브라우저로 압축합니다. ESI가 작동하려면 Apache에서 CDN으로 상위 페이지 전송이 압축 해제되어야 하므로(`no-gzip`이(가) 1로 설정됨) 지연이 줄어들 수 있습니다.<br/><br/>이 헤더가 설정되지 않은 경우 CDN이 원본 콘텐츠를 압축되지 않은 상태로 검색하면 콘텐츠를 압축되지 않은 상태로 클라이언트에 제공합니다. 따라서 `no-gzip`이(가) 1로 설정되어 있고(ESI에 필요) CDN에서 압축된 콘텐츠를 브라우저에 제공하려는 경우 이 헤더를 설정해야 합니다. |

## Sling Dynamic 포함 항목 {#esi-sdi}

필요하지 않지만 [Sling Dynamic Include](https://sling.apache.org/documentation/bundles/dynamic-includes.html)(SDI)을 사용하여 CDN에서 해석되는 ESI 스니펫을 생성할 수 있습니다.
