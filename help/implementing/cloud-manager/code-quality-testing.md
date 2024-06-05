---
title: 코드 품질 테스트
description: 파이프라인의 코드 품질 테스트가 어떻게 작동하고 배포 품질을 어떻게 개선할 수 있는지 알아봅니다.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 96%

---

# 코드 품질 테스트 {#code-quality-testing}

파이프라인의 코드 품질 테스트가 어떻게 작동하고 배포 품질을 어떻게 개선할 수 있는지 알아봅니다.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="코드 품질 테스트"
>abstract="코드 품질 테스트는 일련의 품질 규칙을 기반으로 애플리케이션 코드를 평가합니다. 코드 품질 전용 파이프라인의 주요 목적이며 모든 프로덕션 및 비프로덕션 파이프라인에서 빌드 단계 직후에 실행됩니다."

## 소개 {#introduction}

코드 품질 테스트는 일련의 품질 규칙을 기반으로 애플리케이션 코드를 평가합니다. 코드 품질 전용 파이프라인의 주요 목적이며 모든 프로덕션 및 비프로덕션 파이프라인에서 빌드 단계 직후에 실행됩니다.

다양한 파이프라인 유형에 대한 자세한 내용은 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 참조하십시오.

## 코드 품질 규칙 {#understanding-code-quality-rules}

코드 품질 테스트는 소스 코드를 스캔하여 특정 품질 기준을 충족하는지 확인합니다. 이는 SonarQube 및 OakPAL을 사용한 콘텐츠 패키지 수준 검사의 조합으로 구현됩니다. 일반적인 Java 규칙과 AEM별 규칙을 결합한 100개 이상의 규칙이 있습니다. AEM 관련 규칙 중 일부는 AEM 엔지니어링의 모범 사례를 기반으로 생성되며 [사용자 정의 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md)이라고 합니다.

>[!NOTE]
>
>[이 링크를 사용](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)하여 전체 규칙 목록을 다운로드할 수 있습니다.

### 3계층 등급 {#three-tiered-gate}

코드 품질 테스트를 통해 식별된 문제는 세 가지 범주 중 하나에 할당됩니다.

* **심각** - 파이프라인의 즉각적인 실패를 초래하는 문제입니다.

* **중요** - 파이프라인을 일시 중지 상태로의 전환을 초래하는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 재정의하거나 파이프라인이 오류로 중단되는 경우 문제를 수락할 수 있습니다.

* **정보** - 순전히 정보 제공 목적으로 제공되며 파이프라인 실행에 영향을 미치지 않는 문제입니다.

>[!NOTE]
>
>코드 품질 전용 파이프라인에서는 코드 품질 테스트 단계가 파이프라인의 최종 단계이기 때문에 코드 품질 게이트의 중요 오류를 재정의할 수 없습니다.

### 등급 {#ratings}

이 단계의 결과는 **등급**&#x200B;으로 전달됩니다.

다음 표에는 심각, 중요 및 정보 범주 각각에 대한 등급 및 오류 임계값이 요약되어 있습니다.

| 이름 | 정의 | 범주 | 오류 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 취약점 없음 <br/>B = 1개 이상의 사소한 취약점<br/> C = 1개 이상의 주요 취약점 <br/>D = 1개 이상의 심각한 취약점 <br/>E = 1개 이상의 차단 취약점 | 심각 | &lt; B |
| 안정성 등급 | A = 버그 없음 <br/>B = 1개 이상의 사소한 버그 <br/>C = 1개 이상의 주요 버그 <br/>D = 1개 이상의 심각한 버그<br>E = 1개 이상의 차단 버그 | 심각 | &lt; D |
| 유지 가능성 등급 | 코드 스멜에 대한 미해결 교정 비용으로 정의되며, 애플리케이션에 이미 들어간 시간의 백분율입니다.<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | 중요 | &lt; A |
| 범위 | 다음 공식을 사용하여 단위 테스트 라인 범위와 조건 범위의 혼합으로 정의됩니다. <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = 단위 테스트를 실행하는 동안 한 번 이상 `true`로 평가된 조건</li><li>`CF` = 단위 테스트를 실행하는 동안 한 번 이상 `false`로 평가된 조건</li><li>`LC` = 적용 라인 = lines_to_cover - uncovered_lines</li><li>`B` = 총 조건 수</li><li>`EL` = 총 실행 가능한 라인 수 (lines_to_cover)</li></ul> | 중요 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수 | 정보 | > 1 |
| 미해결 문제 | 전반적인 문제 유형 - 취약점, 버그 및 코드 스멜 | 정보 | > 0 |
| 중복 라인 | 중복된 블록과 관련된 라인의 수로 정의됩니다. 다음 조건에서는 코드 블록이 중복된 것으로 간주됩니다.<br>비 Java 프로젝트:<ul><li>연속 토큰과 중복 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 최소한 다음과 같이 분산되어야 합니다. </li><li>COBOL의 경우 30개 코드 라인 </li><li>ABAP의 경우 20개 코드 라인 </li><li>기타 언어의 경우 10개 코드 라인</li></ul>Java 프로젝트:<ul></li><li> 토큰과 라인 수에 관계없이 연속적이고 중복된 문이 10개 이상 있어야 합니다.</li></ul>중복 요소를 감지할 때 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수 | 정보 | > 0 |

>[!NOTE]
>
>자세한 정의는 [SonarQube의 지표 정의](https://docs.sonarqube.org/latest/user-guide/metric-definitions/)를 참조하십시오.

>[!NOTE]
>
>[!UICONTROL Cloud Manager]에서 실행한 사용자 정의 코드 품질 규칙에 대한 자세한 내용은 [사용자 정의 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md)을 참조하십시오.

## 긍정 오류 처리 {#dealing-with-false-positives}

품질 검사 프로세스는 완벽하지 않으며 실제로 문제가 아닌 문제를 잘못 식별하기도 합니다. 이를 **긍정 오류(false positive)**&#x200B;라고 합니다.

이러한 경우 소스 코드는 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 추가할 수 있습니다. 예를 들어 한 가지 일반적인 긍정 오류는 하드코딩된 암호를 탐지하는 SonarQube 규칙이 하드코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

다음 코드는 일부 외부 서비스에 연결하는 코드가 있는 AEM 프로젝트에서 상당히 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러면 SonarQube에 차단 취약점이 발생합니다. 그러나 코드를 검토한 후 이것이 취약점이 아니며 적절한 규칙 ID로 코드에 주석을 달 수 있다는 것을 알게 됩니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

이때 하드 코딩된 암호를 제거하는 것이 올바른 해결 방법입니다.

>[!NOTE]
>
>`@SuppressWarnings` 주석을 가능한 구체적으로 만드는 것이 모범 사례이지만(즉, 문제를 일으키는 특정 문이나 블록에만 주석 추가) 클래스 수준에서 주석을 추가하는 것은 가능합니다.

>[!NOTE]
>명시적인 보안 테스트 단계는 없지만 코드 품질 단계에서 보안 관련 코드 품질 규칙이 평가됩니다. Cloud Service 보안에 대한 자세한 내용은 [AEM as a Cloud Service 보안 개요](/help/security/cloud-service-security-overview.md)를 참조하십시오.

## 콘텐츠 패키지 검색 최적화 {#content-package-scanning-optimization}

품질 분석 프로세스의 일환으로 Cloud Manager는 Maven 빌드에서 생성된 콘텐츠 패키지에 대한 분석을 수행합니다. Cloud Manager는 이 프로세스를 가속화하기 위한 최적화를 제공하며, 이는 특정 패키징 제한이 관찰될 때 효과적입니다. 가장 중요한 것은 일반적으로 &quot;모든&quot; 패키지라고 하는 단일 콘텐츠 패키지를 출력하는 프로젝트에 대해 수행되는 최적화입니다. 이 패키지에는 빌드에 의해 생성된 여러 다른 콘텐츠 패키지가 포함되어 있으며, 이 패키지는 건너뛰기로 표시됩니다. Cloud Manager가 이 시나리오를 감지하면 “모든” 패키지의 압축을 푸는 대신 개별 콘텐츠 패키지가 직접 스캔되고 종속성에 따라 정렬됩니다. 예를 들어 다음 빌드 출력을 고려해 보십시오.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

`myco-all-1.0.0-SNAPSHOT.zip` 내에 있는 항목만 건너뛴 두 개의 콘텐츠 패키지인 경우, “모든” 콘텐츠 패키지 대신 임베드된 두 개의 패키지가 스캔됩니다.

수십 개의 임베드된 패키지를 생성하는 프로젝트의 경우, 이 최적화는 파이프라인 실행당 10분 이상 절약되는 것으로 나타났습니다.

“모든” 콘텐츠 패키지에 건너뛴 콘텐츠 패키지와 OSGi 번들의 조합이 포함된 경우 특별한 경우가 발생할 수 있습니다. 예를 들어 `myco-all-1.0.0-SNAPSHOT.zip`에 앞서 언급한 두 개의 임베드된 패키지가 포함된 경우, 하나 이상의 OSGi 번들로만 구성된 새로운 최소 콘텐츠 패키지가 구성됩니다. 이 패키지의 이름은 항상 `cloudmanager-synthetic-jar-package`이고 포함된 번들은 `/apps/cloudmanager-synthetic-installer/install`에 배치됩니다.

>[!NOTE]
>
>* 이 최적화는 AEM에 배포된 패키지에 영향을 주지 않습니다.
>* 임베드된 콘텐츠 패키지와 건너뛴 콘텐츠 패키지 간의 일치는 파일 이름을 기반으로 하므로 여러 건너뛴 콘텐츠 패키지의 파일 이름이 정확히 동일하거나 임베드하는 동안 파일 이름이 변경된 경우에는 이 최적화를 수행할 수 없습니다.
