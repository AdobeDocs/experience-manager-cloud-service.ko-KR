---
title: Sling 어댑터 사용
description: Sling은 어댑터 패턴을 제공하여 적응형 인터페이스를 구현하는 객체를 편리하게 변환합니다.
translation-type: tm+mt
source-git-commit: 639bf1add463c0e62982a44ecdca834e2c7c53fe
workflow-type: tm+mt
source-wordcount: '2234'
ht-degree: 1%

---


# Sling 어댑터 사용 {#using-sling-adapters}

[어댑터 ](https://sling.apache.org) 패턴을 사용하여  [어댑터 ](https://sling.apache.org/site/adapters.html) 인터페이스를 구현하 [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 는 개체를 편리하게변환합니다. 이 인터페이스는 인수로 전달되는 클래스 유형으로 개체를 변환할 일반 [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 메서드를 제공합니다.

예를 들어 Resource 객체를 해당 Node 객체로 변환하려면 다음을 수행하면 됩니다.

```java
Node node = resource.adaptTo(Node.class);
```

## 사용 사례 {#use-cases}

다음과 같은 사용 사례가 있습니다.

* 구현별 개체를 가져옵니다.

   예를 들어 일반 [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) 인터페이스의 JCR 기반 구현은 기본 JCR [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html)에 대한 액세스를 제공합니다.

* 내부 컨텍스트 객체를 전달해야 하는 객체의 바로 가기 만들기

   예를 들어, JCR 기반 [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html)은 요청의 [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)에 대한 참조를 보유하며, 이 참조는 [`PageManager`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/PageManager.html) 또는 [`UserManager`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/security/UserManager.html)과 같은 요청 세션을 기반으로 하는 많은 개체에 필요합니다.

* 서비스에 바로 가기.

   드문 경우이지만 `sling.getService()`도 간단합니다.

### Null 반환 값 {#null-return-value}

`adaptTo()` null을 반환할 수 있습니다.

다음과 같은 다양한 이유가 있습니다.

* 구현에서 대상 유형을 지원하지 않습니다.
* 이 케이스를 처리하는 어댑터 팩터리가 활성 상태가 아닙니다(예: 서비스 참조가 없기 때문에)
* 내부 조건 실패
* 서비스를 사용할 수 없음

null 대/소문자를 적절하게 처리해야 합니다. jsp 렌더링의 경우 jsp가 실패할 경우 빈 컨텐츠가 발생할 수 있습니다.

### {#caching} 캐싱

성능을 개선하기 위해 구현은 `obj.adaptTo()` 호출에서 반환된 객체를 캐시할 수 있습니다. `obj`이(가) 동일한 경우 반환된 객체가 동일합니다.

이 캐싱은 모든 `AdapterFactory` 기반 사례에 대해 수행됩니다.

그러나 일반 규칙이 없습니다. 객체는 새 인스턴스이거나 기존 인스턴스일 수 있습니다. 이것은 두 가지 행동에 의존할 수 없음을 의미합니다. 따라서 특히 `AdapterFactory` 내에서 이 시나리오에서 개체를 다시 사용할 수 있는 것이 중요합니다.

### 작동 방식 {#how-it-works}

`Adaptable.adaptTo()`을(를) 구현할 수 있는 방법은 다양합니다.

* 개체 자체로는;메서드 자체를 구현하고 특정 객체에 매핑을 수행합니다.
* 임의의 객체를 매핑할 수 있는 [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)에 의해.

   개체는 여전히 `Adaptable` 인터페이스를 구현해야 하며 [`SlingAdaptable`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/adapter/SlingAdaptable.html)(`adaptTo` 호출을 중앙 어댑터 관리자에 전달)을 확장해야 합니다.

   이렇게 하면 `Resource` 같은 기존 클래스에 대한 `adaptTo` 메커니즘에 연결할 수 있습니다.

* 두 가지 조합입니다.

첫 번째 경우 javadocs는 `adaptTo-targets`이(가) 가능한 것을 나타낼 수 있습니다. 그러나 JCR 기반 리소스와 같은 특정 하위 클래스의 경우 이는 종종 가능하지 않습니다. 후자의 경우, `AdapterFactory` 구현은 일반적으로 번들의 개인 클래스의 일부이므로 클라이언트 API에 노출되거나 javadocs에 나열되지 않습니다. 이론적으로, [OSGi](/help/implementing/deploying/configuring-osgi.md) 서비스 런타임에서 모든 `AdapterFactory` 구현에 액세스하여 &quot;적응형&quot;(소스 및 대상) 구성을 볼 수 있지만 서로 매핑하지 않을 수 있습니다. 결국, 이것은 문서화되어야 하는 내부 논리에 따라 다릅니다. 따라서 이 참조가 있습니다.

## 참조 {#reference}

### 슬링 {#sling}

[**리소스**](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html) 는 다음 항목에 맞게 조정됩니다.

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td>
   <td>이것이 JCR 노드 기반 리소스이거나 노드를 참조하는 JCR 속성일 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">속성</a></td>
   <td>JCR 속성 기반 리소스인 경우.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">항목</a></td>
   <td>JCR 기반 리소스(노드 또는 속성)인 경우.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">맵</a></td>
   <td>JCR 노드 기반 리소스(또는 값 맵을 지원하는 기타 리소스)인 경우 속성의 맵을 반환합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>JCR 노드 기반 리소스(또는 값 맵을 지원하는 기타 리소스)인 경우 속성의 사용하기 쉬운 맵을 반환합니다. <br /> <code><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code>(null 케이스 처리 등)를 사용하여(더욱 간단함)할 수도 있습니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>속성을 찾을 때 리소스 계층 구조를 고려할 수 있도록 하는 <a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>의 확장입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">수정 가능한 ValueMap</a></td>
   <td>해당 노드의 속성을 수정할 수 있는 <a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>의 확장입니다.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>파일 리소스의 이진 내용을 반환합니다(JCR 노드 기반 리소스이고 노드 유형이 <code>nt:file</code> 또는 <code>nt:resource</code>;번들 리소스인 경우;파일 내용(파일 시스템 리소스인 경우) 또는 바이너리 JCR 속성 리소스의 데이터입니다.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>리소스(JCR 노드 기반 리소스인 경우 이 노드의 저장소 URL;번들 리소스인 경우 jar 번들 URL;파일 시스템 리소스인 경우 파일 URL).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html">파일</a></td>
   <td>파일 시스템 리소스인 경우</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>이 리소스가 스크립트로 등록된 스크립트(예: jsp 파일)인 경우</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/products/servlet/2.2/javadoc/javax/servlet/Servlet.html">Servlet</a></td>
   <td>이 리소스가 Sling으로 스크립트 엔진이 등록되거나 Servlet 리소스인 스크립트(예: jsp 파일)인 경우</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Double.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html"></a><br /> <a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html">StringBooleanLongDoubleCalendarValueString[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html">Long[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html">Calendar[]</a><br /> <a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">값[]</a></td>
   <td>JCR 속성 기반 리소스(및 값이 맞는 경우)인 값을 반환합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>JCR 노드 기반 리소스인 경우.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/Page.html">페이지</a></td>
   <td>이 리소스가 JCR 노드 기반 리소스이고 노드가 <code>cq:Page</code>(또는 <code>cq:PseudoPage</code>)인 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/components/Component.html">구성 요소</a></td>
   <td><code>cq:Component</code> 노드 리소스인 경우</td>
  </tr>  
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/designer/Design.html">디자인</a></td>
   <td>디자인 노드인 경우(<code>cq:Page</code>).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/Template.html">템플릿</a></td>
   <td><code>cq:Template</code> 노드 리소스인 경우</td>
  </tr>  
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/msm/api/Blueprint.html">블루프린트</a></td>
   <td><code>cq:Template</code> 노드 리소스인 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/dam/api/Asset.html">자산</a></td>
   <td>dam:Asset 노드 리소스인 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/dam/api/Rendition.html">렌디션</a></td>
   <td>dam:Asset 변환(dam:Assert의 변환 폴더 아래에 nt:file)</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/tagging/Tag.html">태그</a></td>
   <td><code>cq:Tag</code> 노드 리소스인 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>JCR 기반 리소스이고 사용자에게 UserManager에 액세스할 수 있는 권한이 있는 경우 JCR 세션을 기반으로 합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">승인 가능 대상</a></td>
   <td>승인 가능 인터페이스는 사용자 및 그룹의 공통 기본 인터페이스입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/jackrabbit/api/security/user/User.html">사용자</a></td>
   <td>사용자는 인증 및 가장할 수 있는 특별한 승인 대상입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/SimpleSearch.html">단순 검색</a></td>
   <td>JCR 기반 리소스인 경우 리소스 아래에서 검색합니다(또는 setSearchIn()).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>지정된 페이지/워크플로우 페이로드 노드에 대한 워크플로우 상태입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>지정된 리소스 또는 해당 jcr:content 하위 노드의 복제 상태입니다(먼저 선택됨).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>JCR 노드 기반 리소스인 경우 특정 유형에 대해 조정된 커넥터 리소스를 반환합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/contentsync/config/package-summary.html">구성</a></td>
   <td><code>cq:ContentSyncConfig</code> 노드 리소스인 경우</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>이 값이 <code>cq:ContentSyncConfig</code> 노드 리소스 아래에 있는 경우.</td>
  </tr>
 </tbody>
</table>

[**ResourceResolution**](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/ResourceResolver.html) 이 다음 항목에 맞게 조정됩니다.

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">세션</a></td>
   <td>요청의 JCR 세션(JCR 기반 리소스 확인자(기본값)입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/designer/Designer.html">디자이너</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>JCR 기반 리소스 확인자인 경우 JCR 세션을 기반으로 합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>JCR 기반 리소스 확인자인 경우 JCR 세션을 기반으로 합니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>UserManager는 사용자 및 그룹과 같이 권한이 있는 개체를 유지 관리하기 위한 액세스 및 방법을 제공합니다. UserManager는 특정 세션에 바인딩됩니다.
   </td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">승인 가능 대상</a> </td>
   <td>현재 사용자입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/jackrabbit/api/security/user/User.html">사용자</a><br /> </td>
   <td>현재 사용자입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html">Externalizer</a></td>
   <td>절대 URL을 외부화하기 위해, 요청 개체를 제외한 경우에도 사용하십시오.<br /> </td>
  </tr>
 </tbody>
</table>

[****](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequestions는 다음 항목에 맞게 조정됩니다.

타겟이 아직 없지만 Adaptable을 구현하며 사용자 지정 AdapterFactory에서 소스로 사용할 수 있습니다.

[****](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponseadapts는 다음과 같습니다.

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>sling rewriter 응답인 경우</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[페이지](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/Page.html)** 는 다음 항목에 맞게 조정됩니다.

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html">리소스</a><br /> </td>
   <td>페이지의 리소스입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>레이블이 지정된 리소스(== 이).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td>
   <td>페이지의 노드.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>페이지 리소스를 조정할 수 있는 모든 것.</td>
  </tr>
 </tbody>
</table>

**[구성 요소](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/components/Component.html)** 는 다음 항목에 맞게 조정됩니다.

| [리소스](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html) | 구성 요소의 리소스입니다. |
|---|---|
| [LabeledResource](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/LabeledResource.html) | 레이블이 지정된 리소스(== 이). |
| [노드](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 구성 요소의 노드. |
| ... | 구성 요소의 리소스를 조정할 수 있는 모든 것. |

**[템플릿](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/Template.html)** 은 다음과 같이 적응합니다.

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html">리소스</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>템플릿의 리소스입니다.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>레이블이 지정된 리소스(== 이).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">노드</a></td>
   <td>이 템플릿의 노드입니다.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>템플릿 리소스를 조정할 수 있는 모든 것.</td>
  </tr>
 </tbody>
</table>

#### 보안 {#security}

**작성 가능**, 사용자  **** 및  **** 그룹은 다음 항목에 맞게 적용됩니다.

| [노드](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 사용자/그룹 홈 노드를 반환합니다. |
|---|---|
| [ReplicationStatus](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/replication/ReplicationStatus.html) | 사용자/그룹 홈 노드의 복제 상태를 반환합니다. |

#### DAM {#dam}

**자산** 은 다음 항목에 맞게 조정됩니다.

| [리소스](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html) | 자산의 리소스. |
|---|---|
| [노드](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 자산의 노드. |
| ... | 자산의 리소스를 조정할 수 있는 모든 것. |

#### 태깅 {#tagging}

**태그는** 다음 항목에 맞게 조정됩니다.

| [리소스](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/api/resource/Resource.html) | 태그의 리소스. |
|---|---|
| [노드](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 태그의 노드입니다. |
| ... | 태그의 리소스에 적용할 수 있는 모든 것. |

#### 기타 {#other}

또한 Sling / JCR / OCM은 사용자 지정 OCM([개체 컨텐트 매핑](https://jackrabbit.apache.org/object-content-mapping.html)) 개체에 대해 [`AdapterFactory`](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)을 제공합니다.
