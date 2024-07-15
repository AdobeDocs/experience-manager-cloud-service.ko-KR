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

이 문서에서는 사용자 지정 조건자 평가기를 구현하여 [Query Builder](query-builder-api.md)을(를) 확장하는 방법을 설명합니다.

## 개요 {#overview}

[쿼리 빌더](query-builder-api.md)를 사용하면 콘텐츠 리포지토리를 손쉽게 쿼리할 수 있습니다. AEM에는 데이터를 쿼리하는 데 도움이 되는 [조건자 평가자 집합](#query-builder-predicates.md)이 포함되어 있습니다.

그러나 일부 복잡성을 숨기고 더 나은 의미 체계를 보장하는 사용자 지정 술어 평가기를 구현하여 쿼리를 단순화할 수 있습니다.

사용자 지정 조건자는 XPath를 사용하여 직접 수행할 수 없는 다른 작업을 수행할 수도 있습니다. 예를 들면 다음과 같습니다.

* 다른 서비스에서 데이터 쿼리
* 계산을 기반으로 한 사용자 정의 필터링

>[!NOTE]
>
>사용자 지정 술어를 구현할 때는 성능 문제를 고려해야 합니다.

>[!TIP]
>
>[쿼리 빌더](query-builder-api.md) 문서에서 쿼리의 예를 찾을 수 있습니다.

>[!TIP]
>
>GitHub에서 이 페이지의 코드를 확인할 수 있습니다
>
>* [GitHub에서 aem-search-custom-predicate-evaluator 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
>* 프로젝트를 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)(으)로 다운로드

>[!NOTE]
>
>GitHub에 연결된 이 코드와 이 문서의 코드 조각은 데모용으로만 제공됩니다.

### 술어 평가기 세부 정보 {#predicate-evaluator-in-detail}

술어 평가기는 쿼리의 정의 제약 조건인 특정 술어의 평가를 처리합니다.

실제 콘텐츠 모델(예: `metadata/@width > 200`)에 맞는 특정 JCR 쿼리에 더 높은 수준의 검색 제약 조건(예: `width>200`)을 매핑합니다. 또는 수동으로 노드를 필터링하고 제약 조건을 확인할 수 있습니다.

>[!TIP]
>
>`PredicateEvaluator` 및 `com.day.cq.search` 패키지에 대한 자세한 내용은 [Java 설명서](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html?com/day/cq/search/package-summary.html)를 참조하십시오.

### 복제 메타데이터에 대한 사용자 지정 설명 평가기 구현 {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

이 섹션에서는 복제 메타데이터를 기반으로 데이터를 지원하는 사용자 정의 술어 평가기를 만드는 방법에 대해 설명합니다.

* 마지막 복제 작업의 날짜를 저장하는 `cq:lastReplicated`
* 마지막 복제 작업을 트리거한 사용자의 id를 저장하는 `cq:lastReplicatedBy`
* 마지막 복제 작업(예: 활성화, 비활성화)을 저장하는 `cq:lastReplicationAction`

#### 기본 술어 평가자를 사용하여 복제 메타데이터 쿼리 {#querying-replication-metadata-with-default-predicate-evaluators}

다음 쿼리는 `admin`이(가) 연도 시작 이후 활성화한 `/content` 분기의 노드 목록을 가져옵니다.

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

`ReplicationPredicateEvaluator`의 목표는 다음 구문을 사용하여 위의 쿼리를 지원하는 것입니다.

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
>Maven 사용을 포함한 새 AEM 프로젝트 설정에 대해서는 [WKND 튜토리얼](develop-wknd-tutorial.md)에서 자세히 설명합니다.

먼저 프로젝트의 Maven 종속성을 업데이트해야 합니다. `PredicateEvaluator`은(는) `cq-search` 아티팩트의 일부이므로 Maven pom 파일에 추가해야 합니다.

>[!NOTE]
>
>`cq-search`이(가) `OSGi` 컨테이너에서 제공되므로 `cq-search` 종속성의 범위가 `provided`(으)로 설정됩니다.

다음 코드 조각은 `pom.xml` 파일의 차이점을 [통합 차이점 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)으로 보여줍니다

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

`cq-search` 프로젝트에 `AbstractPredicateEvaluator` 추상 클래스가 포함되어 있습니다. 몇 가지 단계를 통해 사용자 지정 조건자 평가기 `(PredicateEvaluator`을(를) 구현하면 이를 확장할 수 있습니다.

>[!NOTE]
>
>다음 절차에서는 데이터를 필터링하기 위해 `Xpath` 식을 만드는 방법을 설명합니다. 행 단위로 데이터를 선택하는 `includes` 메서드를 구현하는 방법도 있습니다. 자세한 내용은 [Java 설명서](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)를 참조하세요.

1. `com.day.cq.search.eval.AbstractPredicateEvaluator`을(를) 확장하는 새 Java 클래스 만들기
1. [통합 비교 형식](https://en.wikipedia.org/wiki/Diff#Unified_format)으로 표시되는 코드 조각과 같은 `@Component`(으)로 클래스에 주석을 답니다.

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
   >`factory`은(는) `com.day.cq.search.eval.PredicateEvaluator/`(으)로 시작하고 사용자 지정 `PredicateEvaluator` 이름으로 끝나는 고유한 문자열이어야 합니다.

   >[!NOTE]
   >
   >`PredicateEvaluator`의 이름은 쿼리를 작성할 때 사용되는 조건자 이름입니다.

1. 재정의:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   재정의 메서드에서 인수에 지정된 `Predicate`을(를) 기반으로 `Xpath` 식을 만듭니다.

### 복제 메타데이터에 대한 사용자 지정 설명 평가기의 예 {#example-of-a-custom-predicate-evaluator-for-replication-metadata}

이 `PredicateEvaluator`의 전체 구현은 다음 클래스와 유사할 수 있습니다.

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
