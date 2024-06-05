---
title: Query Builder의 사용자 지정 설명 평가기 구현
description: AEM의 Query Builder는 사용자 정의가 가능한 간편한 방법으로 콘텐츠 저장소를 쿼리합니다
exl-id: 8c2f8c22-1851-4313-a1c9-10d6d9b65824
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Query Builder의 사용자 지정 설명 평가기 구현 {#implementing-a-custom-predicate-evaluator-for-the-query-builder}

이 문서에서는 를 확장하는 방법을 설명합니다. [Query Builder](query-builder-api.md) 사용자 지정 술어 평가기를 구현합니다.

## 개요 {#overview}

다음 [Query Builder](query-builder-api.md) 는 콘텐츠 저장소를 손쉽게 쿼리할 수 있는 방법을 제공합니다. AEM에는 다음이 포함됩니다. [술어 평가자 집합](#query-builder-predicates.md) 데이터를 쿼리하는 데 도움이 됩니다.

그러나 일부 복잡성을 숨기고 더 나은 의미 체계를 보장하는 사용자 지정 술어 평가기를 구현하여 쿼리를 단순화할 수 있습니다.

사용자 지정 조건자는 XPath를 사용하여 직접 수행할 수 없는 다른 작업을 수행할 수도 있습니다. 예를 들면 다음과 같습니다.

* 다른 서비스에서 데이터 쿼리
* 계산을 기반으로 한 사용자 정의 필터링

>[!NOTE]
>
>사용자 지정 술어를 구현할 때는 성능 문제를 고려해야 합니다.

>[!TIP]
>
>다음에서 쿼리의 예를 찾을 수 있습니다. [Query Builder](query-builder-api.md) 문서.

>[!TIP]
>
>GitHub에서 이 페이지의 코드를 확인할 수 있습니다
>
>* [GitHub에서 aem-search-custom-predicate-evaluator 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
>* 다음으로 프로젝트 다운로드 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)

>[!NOTE]
>
>GitHub에 연결된 이 코드와 이 문서의 코드 조각은 데모용으로만 제공됩니다.

### 술어 평가기 세부 정보 {#predicate-evaluator-in-detail}

술어 평가기는 쿼리의 정의 제약 조건인 특정 술어의 평가를 처리합니다.

더 높은 수준의 검색 제약 조건(예: `width>200`)를 실제 콘텐츠 모델에 맞는 특정 JCR 쿼리(예: `metadata/@width > 200`). 또는 수동으로 노드를 필터링하고 제약 조건을 확인할 수 있습니다.

>[!TIP]
>
>에 대한 자세한 내용은 `PredicateEvaluator` 및 `com.day.cq.search` 패키지 참조 [Java 설명서](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html?com/day/cq/search/package-summary.html).

### 복제 메타데이터에 대한 사용자 지정 설명 평가기 구현 {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

이 섹션에서는 복제 메타데이터를 기반으로 데이터를 지원하는 사용자 정의 술어 평가기를 만드는 방법에 대해 설명합니다.

* `cq:lastReplicated` 마지막 복제 작업의 날짜를 저장하는 날짜
* `cq:lastReplicatedBy` 마지막 복제 작업을 트리거한 사용자의 id를 저장합니다.
* `cq:lastReplicationAction` 마지막 복제 작업(예: 활성화, 비활성화)을 저장하는 작업

#### 기본 술어 평가자를 사용하여 복제 메타데이터 쿼리 {#querying-replication-metadata-with-default-predicate-evaluators}

다음 쿼리는 의 노드 목록을 가져옵니다. `/content` 에 의해 활성화된 분기 `admin` 연초부터.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

이 쿼리는 유효하지만 읽기가 어려우며 세 가지 복제 속성 간의 관계를 강조 표시하지 않습니다. 사용자 지정 술어 평가기를 구현하면 복잡성이 줄어들고 이 쿼리의 의미 체계가 향상됩니다.

#### 목표 {#objectives}

의 목표 `ReplicationPredicateEvaluator` 는 다음 구문을 사용하여 위의 쿼리를 지원합니다.

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

복제 메타데이터 술어를 사용자 지정 술어 평가기와 그룹화하면 의미 있는 쿼리를 만드는 데 도움이 됩니다.

#### Maven 종속성 업데이트 중 {#updating-maven-dependencies}

>[!TIP]
>
>Maven 사용을 포함한 새 AEM 프로젝트 설정은에서 자세히 설명합니다. [wknd 튜토리얼.](develop-wknd-tutorial.md)

먼저 프로젝트의 Maven 종속성을 업데이트해야 합니다. 다음 `PredicateEvaluator` 의 일부임 `cq-search` Maven pom 파일에 추가해야 합니다.

>[!NOTE]
>
>의 범위 `cq-search` 종속성이 다음으로 설정됨 `provided` 이유 `cq-search` 에서 제공합니다. `OSGi` 컨테이너.

다음 코드 조각은 의 차이점을 보여 줍니다. `pom.xml` 파일, 위치 [통합 비교 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)

```text
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

#### ReplicationPredicateEvaluator 작성 {#writing-the-replicationpredicateevaluator}

다음 `cq-search` 이 프로젝트에는 `AbstractPredicateEvaluator` 추상 클래스입니다. 이를 몇 가지 단계를 통해 확장하여 자신만의 맞춤형 술어 평가기를 구현할 수 있습니다 `(PredicateEvaluator`).

>[!NOTE]
>
>다음 절차에서는 `Xpath` 데이터를 필터링할 표현식입니다. 다른 옵션은 를 구현하는 것입니다. `includes` 행 단위로 데이터를 선택하는 메서드입니다. 다음을 참조하십시오. [Java 설명서](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) 추가 정보.

1. 를 확장하는 새 Java 클래스를 만듭니다. `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. 을(를) 사용하여 클래스에 주석 달기 `@Component` 다음에 표시되는 코드 조각과 유사 [통합 비교 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)

   ```text
   @@ -19,8 +19,11 @@
     */
    package com.adobe.aem.docs.search;
   
   +import org.apache.felix.scr.annotations.Component;
   +import com.day.cq.search.eval.AbstractPredicateEvaluator;
   
   +@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
    public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {
   
    }
   ```

   >[!NOTE]
   >
   >다음 `factory`은(는) 다음으로 시작하는 고유한 문자열이어야 합니다. `com.day.cq.search.eval.PredicateEvaluator/`사용자 정의 이름으로 끝나는 경우 `PredicateEvaluator`.

   >[!NOTE]
   >
   >의 이름입니다. `PredicateEvaluator` 는 쿼리를 작성할 때 사용되는 술어 이름입니다.

1. 재정의:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   override 메서드에서 `Xpath` 를 기반으로 한 표현식 `Predicate` 논쟁 중에 주어집니다.

### 복제 메타데이터에 대한 사용자 지정 설명 평가기의 예 {#example-of-a-custom-predicate-evaluator-for-replication-metadata}

이에 대한 완전한 구현 `PredicateEvaluator` 다음 클래스와 비슷할 수 있습니다.

```java
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.search.Predicate;
import com.day.cq.search.eval.AbstractPredicateEvaluator;
import com.day.cq.search.eval.EvaluationContext;

@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";


    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";
    static final String PN_LAST_REPLICATED = "cq:lastReplicated";
    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";
    static final String PREDICATE_SINCE = "since";
    static final String PREDICATE_SINCE_OP = " >= ";
    static final String PREDICATE_ACTION = "action";

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,
            EvaluationContext context) {

        log.debug("predicate {}", predicate);

        String date = predicate.get(PREDICATE_SINCE);
        String user = predicate.get(PREDICATE_BY);
        String action = predicate.get(PREDICATE_ACTION);

        StringBuilder sb = new StringBuilder();

        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);
            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_BY);
            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_ACTION);
            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```
