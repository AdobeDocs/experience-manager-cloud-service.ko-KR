---
title: 렌더링용 구성 요소를 구성하는 콘텐츠 조각
description: 렌더링용 구성 요소를 구성하는 콘텐츠 조각
exl-id: 6606dc3b-f1b8-4941-8fd0-f69cbd414afa
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 6%

---

# 렌더링용 구성 요소를 구성하는 콘텐츠 조각{#content-fragments-configuring-components-for-rendering}

몇 개 있습니다 [고급 서비스](#definition-of-advanced-services-that-need-configuration) 콘텐츠 조각 렌더링과 관련이 있습니다. 이러한 서비스를 사용하려면 이러한 구성 요소의 리소스 유형을 콘텐츠 조각 프레임워크에 알려야 합니다.

이 작업은 다음을 구성하여 수행합니다 [OSGi 서비스 - 콘텐츠 조각 구성 요소 구성](#osgi-service-content-fragment-component-configuration).

이 정보는 다음과 같은 경우에 필요합니다.

* 고유한 콘텐츠 조각 기반 구성 요소 를 구현해야 합니다.
* 또한 고급 서비스를 사용해야 합니다.

핵심 구성 요소를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>* **필요하지 않은 경우 [고급 서비스](#definition-of-advanced-services-that-need-configuration)** 아래에 설명되어 있으므로 이 구성을 무시할 수 있습니다.
>
>* **를 확장하거나 기본 제공 구성 요소를 사용하는 경우** OSGi 구성을 변경하지 않는 것이 좋습니다.
>
>* **고급 서비스 없이 콘텐츠 조각 API만 사용하는 구성 요소를 처음부터 작성할 수 있습니다**. 그러나 이러한 경우 구성 요소가 적절한 처리를 수행하도록 개발해야 합니다.
>
>따라서 핵심 구성 요소를 사용하는 것이 좋습니다.

## 구성이 필요한 고급 서비스의 정의 {#definition-of-advanced-services-that-need-configuration}

구성 요소를 등록해야 하는 서비스는 다음과 같습니다.

* 게시 도중 종속성을 올바르게 결정(즉, 조각 및 모델이 마지막 게시 이후 변경된 경우 페이지와 함께 자동으로 게시될 수 있는지 확인).
* 전체 텍스트 검색에서 컨텐츠 조각 지원.
* 의 관리/처리 *중간 콘텐츠.*
* 의 관리/처리 *혼합 미디어 에셋.*
* 참조된 조각에 대한 Dispatcher 플러시(조각이 포함된 페이지가 다시 게시되는 경우).
* 단락 기반 렌더링 사용.

이러한 기능 중 하나 이상이 필요한 경우 (일반적으로) 처음부터 개발하는 대신 즉시 사용 가능한 고급 서비스를 사용하는 것이 더 쉽습니다.

## OSGi 서비스 - 콘텐츠 조각 구성 요소 구성 {#osgi-service-content-fragment-component-configuration}

구성은 OSGi 서비스에 바인딩되어야 합니다. **콘텐츠 조각 구성 요소 구성**:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>다음을 참조하십시오 [OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration) 을 참조하십시오.

예:

![OSGi 구성 콘텐츠 조각 구성 요소 구성](assets/cf-component-configuration-osgi.png)

OSGi 구성은 다음과 같습니다.

<table>
 <thead>
  <tr>
   <td>레이블</td>
   <td>OSGi 구성<br /> </td>
   <td>설명</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><strong>리소스 유형</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>등록할 리소스 유형(예: ) <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>참조 속성</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>조각에 대한 참조가 포함된 속성의 이름입니다(예: ). <code>fragmentPath</code> 또는 <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>요소 속성</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>렌더링할 요소의 이름이 포함된 속성의 이름입니다. 예:<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>변화 속성</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>렌더링할 변형의 이름을 포함하는 속성의 이름입니다. 예:<code>variationName</code></td>
  </tr>
 </tbody>
</table>

일부 기능의 경우 구성 요소는 사전 정의된 규칙을 준수해야 합니다. 다음 표에서는 각 단락에 대해 구성 요소에서 정의해야 하는 속성을 자세히 설명합니다(즉, `jcr:paragraph` (각 구성 요소 인스턴스에 대해) 서비스를 통해 올바르게 감지하고 처리할 수 있습니다.

<table>
 <thead>
  <tr>
   <td>속성 이름</td>
   <td>설명</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>다음과 같은 경우 단락이 출력되는 방법을 정의하는 문자열 속성 <em>단일 요소 렌더링 모드</em>.</p> <p>값:</p>
    <ul>
     <li><code>all</code> : 모든 단락을 렌더링합니다</li>
     <li><code>range</code> : 제공된 단락의 범위를 렌더링합니다. <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>다음과 같은 경우 출력할 단락 범위를 정의하는 문자열 속성입니다. <em>단일 요소 렌더링 모드</em>.</p> <p>형식:</p>
    <ul>
     <li><code>1</code> 또는 <code>1-3</code> 또는 <code>1-3;6;7-8</code> 또는 <code>*-3;5-*</code>
     <ul>
       <li><code>-</code> 범위 표시기</li>
       <li><code>;</code> 목록 구분 기호</li>
       <li><code>*</code> 와일드카드</li>
     </ul>
     </li>
     <li>다음과 같은 경우에만 평가됨 <code>paragraphScope</code> 이(가) (으)로 설정됨 <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>머리글의 정의(예: <code>h1</code>, <code>h2</code>, <code>h3</code>)는 단락( )으로 계산됩니다<code>true</code>) 여부를 불문한다(<code>false</code>)</td>
  </tr>
 </tbody>
</table>

## 예 {#example}

예를 들어 다음을 참조하십시오(기본 AEM 인스턴스에서).

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

여기에는 다음이 포함됩니다.

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```
