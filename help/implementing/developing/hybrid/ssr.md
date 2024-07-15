---
title: SPA 및 서버측 렌더링
description: SPA에서 서버측 렌더링(SSR)을 사용하면 페이지의 초기 로드를 가속화한 다음 추가적인 렌더링을 클라이언트에 전달할 수 있습니다.
exl-id: be409559-c7ce-4bc2-87cf-77132d7c2da1
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 0%

---

# SPA 및 서버측 렌더링{#spa-and-server-side-rendering}

단일 페이지 애플리케이션(SPA)은 종종 기본 애플리케이션처럼 익숙한 방식으로 반응하고 작동하는 풍부하고 동적인 경험을 사용자에게 제공할 수 있습니다. [이 기능은 클라이언트를 통해 콘텐츠를 먼저 로드한 다음 사용자 상호 작용을 처리하는 데 필요한 작업을 수행하는 방식으로 수행됩니다](introduction.md#how-does-a-spa-work). 이 프로세스는 클라이언트와 서버 사이에 필요한 통신량을 최소화하므로 앱이 반응성이 높아집니다.

그러나 이 프로세스를 수행하면 특히 SPA의 크기가 크고 컨텐츠가 풍부한 경우 초기 로드 시간이 길어질 수 있습니다. 로드 시간을 최적화하기 위해 일부 콘텐츠를 서버측에서 렌더링할 수 있습니다. SSR(서버측 렌더링)을 사용하면 페이지의 초기 로드를 가속화한 다음 추가적인 렌더링을 클라이언트에 전달할 수 있습니다.

## SSR 사용 시기 {#when-to-use-ssr}

SSR이 모든 프로젝트에서 필수는 아닙니다. AEM은 SPAAdobe 용 JS SSR을 완전히 지원하지만 모든 프로젝트에 대해 체계적으로 구현하는 것은 권장되지 않습니다.

SSR을 구현하기로 결정할 때는 먼저 장기 유지 관리를 포함하여 SSR을 추가하는 것이 프로젝트에 현실적으로 나타내는 추가적인 복잡성, 노력 및 비용을 추정해야 합니다. SSR 아키텍처는 부가 가치가 예상 비용을 확실히 초과하는 경우에만 선택해야 합니다.

SSR은 일반적으로 다음 질문 중 하나에 명확한 &quot;예&quot;가 있을 때 일부 값을 제공합니다.

* **SEO:** 트래픽을 가져오는 검색 엔진에서 사이트를 제대로 인덱싱하려면 SSR이 계속 필요합니까? 이제 기본 검색 엔진 크롤러가 JS를 평가한다는 점을 기억하십시오.
* **페이지 속도:** SSR이 실제 환경에서 측정 가능한 속도 개선을 제공하고 전체 사용자 경험을 추가합니까?

프로젝트에 대해 이 두 가지 질문 중 하나 이상이 명확한 &quot;예&quot;로 답변되는 경우에만 SSR을 구현하는 것이 Adobe에 좋습니다. 다음 섹션에서는 [App Builder](https://developer.adobe.com/app-builder)의 일부인 Adobe I/O Runtime을 사용하여 이 작업을 수행하는 방법에 대해 설명합니다.

## Adobe I/O Runtime {#adobe-i-o-runtime}

[프로젝트에 SSR을 구현해야 한다고 확신하는 경우](#when-to-use-ssr) Adobe이 권장하는 해결 방법은 Adobe I/O Runtime을 사용하는 것입니다.

Adobe I/O Runtime에 대한 자세한 내용은 다음을 참조하십시오.

* [https://developer.adobe.com/runtime](https://developer.adobe.com/runtime) - App Builder 런타임 기능에 대한 개요입니다.
* [https://developer.adobe.com/app-builder](https://developer.adobe.com/app-builder) - 전체 App Builder 제품에 대한 세부 정보
* [https://developer.adobe.com/runtime/docs/](https://developer.adobe.com/runtime/docs) - 자세한 설명서

다음 섹션에서는 Adobe I/O Runtime을 사용하여 두 가지 다른 모델에서 SPA용 SSR을 구현하는 방법에 대해 자세히 설명합니다.

* [AEM 기반 통신 흐름](#aem-driven-communication-flow)
* [Adobe I/O Runtime 기반 통신 흐름](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe은 환경(단계, 프로덕션, 테스트 등)별로 별도의 Adobe I/O Runtime 작업공간을 권장합니다. 이렇게 하면 서로 다른 환경에 배포된 단일 애플리케이션의 서로 다른 버전을 사용하는 일반적인 SDLC(시스템 개발 수명 주기) 패턴을 사용할 수 있습니다. 자세한 내용은 [App Builder 애플리케이션용 CI/CD](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/)를 참조하십시오.
>
>인스턴스 유형별 런타임 구현에 차이가 없는 한 인스턴스(작성자, 게시)별로 별도의 작업 영역이 필요하지 않습니다.

>[!NOTE]
>
>Cloud Manager은 Adobe I/O Runtime에 대한 배포를 지원하지 않습니다. 따라서 Adobe I/O Runtime에 SSR 코드를 배포하려면 자체 인프라를 설정해야 합니다.

## 원격 렌더러 구성 {#remote-content-renderer-configuration}

AEM은 원격으로 렌더링된 콘텐츠를 검색할 수 있는 위치를 알고 있어야 합니다. [SSR에 대해 구현하도록 선택한 모델](#adobe-i-o-runtime)에 관계없이 이 원격 렌더링 서비스에 액세스하는 방법을 AEM에 지정해야 합니다.

이 서비스는 **RemoteContentRenderer - Configuration Factory OSGi 서비스**&#x200B;를 통해 수행됩니다. `http://<host>:<port>/system/console/configMgr`의 웹 콘솔 구성 콘솔에서 문자열 &quot;RemoteContentRenderer&quot;를 검색합니다.

![렌더러 구성](assets/renderer-configuration.png)

구성에 사용할 수 있는 필드는 다음과 같습니다.

* **콘텐츠 경로 패턴** - 필요한 경우 콘텐츠의 일부와 일치하는 정규 표현식
* **원격 끝점 URL** - 콘텐츠 생성을 담당하는 끝점의 URL
   * 로컬 네트워크에 없는 경우 보안 HTTPS 프로토콜을 사용합니다.
* **추가 요청 헤더** - 원격 끝점으로 전송된 요청에 추가할 추가 헤더
   * 패턴: `key=value`
* **요청 시간 초과** - 원격 호스트 요청 시간 제한(밀리초)

>[!NOTE]
>
>[AEM 기반 통신 흐름](#aem-driven-communication-flow) 또는 [Adobe I/O Runtime 기반 흐름을 구현하도록 선택했는지 여부에 관계없이 원격 콘텐츠 렌더러 구성을 정의해야 합니다.](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>이 구성은 추가 확장 및 사용자 지정 옵션을 사용할 수 있는 [원격 콘텐츠 렌더러](#remote-content-renderer)을(를) 사용합니다.

## AEM 기반 통신 흐름 {#aem-driven-communication-flow}

SSR을 사용하는 경우 AEM에서 SPA의 [구성 요소 상호 작용 워크플로](introduction.md#interaction-with-the-spa-editor)에는 앱의 초기 콘텐츠가 Adobe I/O Runtime에서 생성되는 단계가 포함됩니다.

1. 브라우저가 AEM에서 SSR 콘텐츠를 요청합니다.
1. AEM은 모델을 Adobe I/O Runtime에 게시합니다.
1. Adobe I/O Runtime은 생성된 콘텐츠를 반환합니다.
1. AEM은 백엔드 HTML 구성 요소의 HTL 템플릿을 통해 Adobe I/O Runtime에서 반환되는 페이지를 제공합니다.

![SSE CMS 기반 AEM Adobe I/O](assets/ssr-cms-drivenaemnode-adobeio.png)

## Adobe I/O Runtime 기반 통신 흐름 {#adobe-i-o-runtime-driven-communication-flow}

이전 섹션에서는 AEM에서 SPA에 대한 서버측 렌더링의 표준 및 권장 구현에 대해 설명합니다. 여기서 AEM은 콘텐츠의 부트스트래핑 및 서비스를 수행합니다.

또는 Adobe I/O Runtime이 부트스트래핑을 담당하도록 SSR을 구현하여 통신 흐름을 효과적으로 반전시킬 수 있다.

두 모델 모두 유효하며 AEM에서 지원합니다. 다만, 특정 모델을 구현하기 전에 각각의 장단점을 고려해야 한다.

<table>
 <tbody>
  <tr>
   <th><strong>부트스트랩</strong></th>
   <th><strong>장점</strong></th>
   <th><strong>단점</strong></th>
  </tr>
  <tr>
   <th><strong>AEM을 통해</strong><br /> </th>
   <td>
    <ul>
     <li>AEM은 필요한 경우 라이브러리 삽입을 관리합니다</li>
     <li>AEM에서만 리소스 유지 관리<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>SPA 개발자<br />에게 생소할 수 있음 </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>Adobe I/O Runtime을 통해<br /> </strong></th>
   <td>
    <ul>
     <li>SPA 개발자에게 더 친숙합니다<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>CSS 및 JavaScript과 같이 응용 프로그램에 필요한 Clientlib 리소스는 <code><a href="/help/implementing/developing/introduction/clientlibs.md">allowProxy</a></code> 속성을 통해 AEM 개발자가 사용할 수 있도록 해야 합니다.<br /> </li>
     <li>AEM과 Adobe I/O Runtime<br /> 간에 리소스를 동기화해야 합니다. </li>
     <li>SPA 작성을 활성화하려면 Adobe I/O Runtime용 프록시 서버가 필요할 수 있습니다</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## SSR 계획 {#planning-for-ssr}

일반적으로 응용 프로그램의 일부만 서버측에서 렌더링해야 합니다. 일반적인 예는 렌더링된 서버측에서 페이지의 초기 로드 시 접힌 부분 위에 표시되는 콘텐츠입니다. 이 프로세스는 이미 렌더링된 콘텐츠를 클라이언트에 전달하여 시간을 절약합니다. 사용자가 SPA과 상호 작용할 때 추가 콘텐츠는 클라이언트에 의해 렌더링됩니다.

SPA에 대한 서버측 렌더링을 구현할 때 필요한 앱 부분을 검토하십시오.

## SSR을 사용하여 SPA 개발 {#developing-an-spa-using-ssr}

SPA 구성 요소는 클라이언트(브라우저에서) 또는 서버측에서 렌더링할 수 있습니다. 서버측에서 렌더링될 때 창 크기 및 위치와 같은 브라우저 속성이 없습니다. 따라서 SPA 구성 요소는 렌더링되는 위치에 대한 가정을 하지 않고 동형이어야 합니다.

SSR을 사용하려면 서버측 렌더링을 담당하는 AEM 및 Adobe I/O Runtime에 코드를 배포해야 합니다. 대부분의 코드는 동일하지만 서버별 작업은 다릅니다.

## AEM의 SPA용 SSR {#ssr-for-spas-in-aem}

AEM의 SPA용 SSR에는 앱 콘텐츠 서버측 렌더링에 대해 호출되는 Adobe I/O Runtime이 필요합니다. 앱의 HTL 내에서 콘텐츠를 렌더링하기 위해 Adobe I/O Runtime의 리소스가 호출됩니다.

AEM이 Angular 및 React SPA 프레임워크를 기본적으로 지원하는 것처럼 Angular 및 React 앱에 대해서도 서버측 렌더링이 지원됩니다. 자세한 내용은 두 프레임워크에 대한 NPM 설명서 를 참조하십시오.

## 원격 콘텐츠 렌더러 {#remote-content-renderer}

AEM에서 SPA과 함께 SSR을 사용하는 데 필요한 [원격 콘텐츠 렌더러 구성](#remote-content-renderer-configuration)은(는) 요구 사항에 맞게 확장 및 사용자 지정할 수 있는 보다 일반적인 렌더링 서비스로 전환됩니다.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` Adobe I/O 등 원격 서버에서 렌더링된 콘텐츠를 검색할 OSGi 서비스입니다. 원격 서버로 전송된 콘텐츠는 전달된 요청 매개 변수를 기반으로 합니다.

추가 콘텐츠 조작이 필요한 경우 종속성 반전을 통해 사용자 지정 Sling 모델 또는 서블릿에 `RemoteContentRenderingService`을(를) 삽입할 수 있습니다.

이 서비스는 내부적으로 [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet)에 사용됩니다.

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

`RemoteContentRendererRequestHandlerServlet`은(는) 프로그래밍 방식으로 요청 구성을 설정하는 데 사용됩니다. 제공된 기본 요청 처리기 구현인 `DefaultRemoteContentRendererRequestHandlerImpl`을(를) 사용하면 콘텐츠 구조의 위치를 원격 끝점에 매핑할 수 있도록 여러 OSGi 구성을 만들 수 있습니다.

사용자 지정 요청 처리기를 추가하려면 `RemoteContentRendererRequestHandler` 인터페이스를 구현하십시오. `Constants.SERVICE_RANKING` 구성 요소 속성을 `DefaultRemoteContentRendererRequestHandlerImpl`의 순위인 100보다 큰 정수로 설정해야 합니다.

```javascript
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### 기본 핸들러의 OSGi 구성 구성 {#configure-default-handler}

[원격 콘텐츠 렌더러 구성](#remote-content-renderer-configuration) 섹션에 설명된 대로 기본 처리기의 구성을 구성해야 합니다.

### 원격 콘텐츠 렌더러 사용 {#usage}

서블릿이 페이지에 삽입된 일부 컨텐츠를 가져와서 반환하도록 합니다.

1. 원격 서버에 액세스할 수 있는지 확인합니다.
1. AEM 구성 요소의 HTL 템플릿에 다음 코드 조각 중 하나를 추가합니다.
1. OSGi 구성을 생성 또는 수정합니다(선택적).
1. 사이트 콘텐츠 검색

일반적으로 페이지 구성 요소의 HTL 템플릿은 이러한 기능의 주요 수신자입니다.

```html
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### 요구 사항 {#requirements}

서블릿은 슬링 모델 익스포터를 사용하여 구성 요소 데이터를 직렬화합니다. 기본적으로 `com.adobe.cq.export.json.ContainerExporter`과(와) `com.adobe.cq.export.json.ComponentExporter`은(는) 모두 Sling 모델 어댑터로 지원됩니다. 필요한 경우 `RemoteContentRendererServlet`을(를) 사용하고 `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses`을(를) 구현하기 위해 요청을 조정해야 하는 클래스를 추가할 수 있습니다. 추가 클래스는 `ComponentExporter`을(를) 확장해야 합니다.
