---
title: 렌더링용 구성 요소를 구성하는 콘텐츠 조각
description: 렌더링용 구성 요소를 구성하는 콘텐츠 조각
exl-id: 6606dc3b-f1b8-4941-8fd0-f69cbd414afa
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 6%

---

# 렌더링용 구성 요소를 구성하는 콘텐츠 조각{#content-fragments-configuring-components-for-rendering}

몇 가지 있습니다 [고급 서비스](#definition-of-advanced-services-that-need-configuration) 컨텐츠 조각 렌더링과 관련되어 있습니다. 이러한 서비스를 사용하려면 이러한 구성 요소의 리소스 유형이 컨텐츠 조각 프레임워크에 알려져야 합니다.

이 작업은 다음을 구성하여 수행합니다 [OSGi 서비스 - 컨텐츠 조각 구성 요소 구성](#osgi-service-content-fragment-component-configuration).

다음 경우에 이 정보가 필요합니다.

* 컨텐츠 조각 기반 구성 요소를 구현해야 합니다.
* 그리고 고급 서비스를 사용해야 합니다.

핵심 구성 요소를 사용하는 것이 좋습니다.

>[!CAUTION]
>
>* **이 필요하지 않으면 [고급 서비스](#definition-of-advanced-services-that-need-configuration)** 아래에 설명된 대로 이 구성을 무시할 수 있습니다.
>
>* **확장 또는 기본 구성 요소를 사용하는 경우**&#x200B;를 설정하는 경우에는 OSGi 구성을 변경하지 않는 것이 좋습니다.
>
>* **고급 서비스 없이 컨텐츠 조각 API만 사용하는 구성 요소를 처음부터 작성할 수 있습니다**. 그러나 이러한 경우 적절한 처리를 수행하기 위해 구성 요소를 개발해야 합니다.
>
>따라서 코어 구성 요소를 사용하는 것이 좋습니다.

## 구성이 필요한 고급 서비스 정의 {#definition-of-advanced-services-that-need-configuration}

구성 요소를 등록해야 하는 서비스는 다음과 같습니다.

* 게시 중 종속성을 올바르게 확인합니다(즉, 마지막 게시 이후 변경된 경우 조각과 모델을 페이지에 자동으로 게시할 수 있는지 확인합니다.).
* 전체 텍스트 검색에서 컨텐츠 조각을 지원합니다.
* 관리/처리 *중간 컨텐츠.*
* 관리/처리 *혼합 미디어 자산.*
* 참조된 조각에 대한 디스패처 플러시(조각을 포함하는 페이지가 다시 게시되는 경우).
* 단락 기반 렌더링 사용.

이러한 기능 중 하나 이상이 필요한 경우(일반적으로) 처음부터 새로 개발하는 대신 기본 제공 Advanced Services를 사용하는 것이 더 쉽습니다.

## OSGi 서비스 - 컨텐츠 조각 구성 요소 구성 {#osgi-service-content-fragment-component-configuration}

구성을 OSGi 서비스에 바인딩해야 합니다 **컨텐츠 조각 구성 요소 구성**:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>자세한 내용은 [OSGi 구성](/help/implementing/deploying/overview.md#osgi-configuration) 자세한 내용

예:

![OSGi 구성 컨텐츠 조각 구성 요소 구성](assets/cf-component-configuration-osgi.png)

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
   <td>등록할 리소스 유형 예 <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>참조 속성</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>조각에 대한 참조가 포함된 속성의 이름 예 <code>fragmentPath</code> 또는 <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>요소 속성</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>렌더링할 요소의 이름이 포함된 속성의 이름입니다. 예<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>변화 속성</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>렌더링할 변형의 이름이 포함된 속성의 이름입니다. 예<code>variationName</code></td>
  </tr>
 </tbody>
</table>

일부 기능의 경우 구성 요소는 사전 정의된 규칙을 준수해야 합니다. 다음 표에서는 각 단락(예: `jcr:paragraph` 가 있어야 합니다.

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
   <td><p>인 경우 단락을 출력하는 방법을 정의하는 문자열 속성입니다. <em>단일 요소 렌더링 모드</em>.</p> <p>값:</p>
    <ul>
     <li><code>all</code> : 모든 단락을 렌더링합니다.</li>
     <li><code>range</code> : 에서 제공하는 단락 범위를 렌더링합니다. <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>인 경우 출력할 단락 범위를 정의하는 문자열 속성입니다. <em>단일 요소 렌더링 모드</em>.</p> <p>형식:</p>
    <ul>
     <li><code>1</code> 또는 <code>1-3</code> 또는 <code>1-3;6;7-8</code> 또는 <code>*-3;5-*</code>
     <ul>
       <li><code>-</code> 범위 표시기</li>
       <li><code>;</code> 목록 구분 기호</li>
       <li><code>*</code> 와일드카드</li>
     </ul>
     </li>
     <li>평가 대상 <code>paragraphScope</code> 가 로 설정되어 있습니다. <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>제목을 정의하는 부울 속성(예: <code>h1</code>, <code>h2</code>, <code>h3</code>)은 단락으로 카운트됩니다(<code>true</code>) 또는 not(<code>false</code>)</td>
  </tr>
 </tbody>
</table>

## 예 {#example}

예를 들어, 다음 (기본 제공 AEM 인스턴스에서)을 참조하십시오.

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

여기에는 다음 항목이 포함되어 있습니다.

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```
