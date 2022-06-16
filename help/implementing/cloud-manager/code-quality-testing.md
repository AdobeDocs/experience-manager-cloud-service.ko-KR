---
title: 코드 품질 테스트
description: 파이프라인의 코드 품질 테스트 작동 방식과 배포 품질을 향상시키는 방법을 알아봅니다.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: 8eada48aaef62aa942b98981a3510a2c64ea582b
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 2%

---

# 코드 품질 테스트 {#code-quality-testing}

파이프라인의 코드 품질 테스트 작동 방식과 배포 품질을 향상시키는 방법을 알아봅니다.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="코드 품질 테스트"
>abstract="코드 품질 테스트는 품질 규칙 세트를 기반으로 애플리케이션 코드를 평가합니다. 이는 코드 품질 전용 파이프라인의 기본 목적이며 모든 프로덕션 및 비프로덕션 파이프라인에서 빌드 단계에 따라 즉시 실행됩니다."

## 소개 {#introduction}

코드 품질 테스트는 품질 규칙 세트를 기반으로 애플리케이션 코드를 평가합니다. 이는 코드 품질 전용 파이프라인의 기본 목적이며 모든 프로덕션 및 비프로덕션 파이프라인에서 빌드 단계에 따라 즉시 실행됩니다.

문서를 참조하십시오 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 다른 유형의 파이프라인에 대해 자세히 알아보십시오.

## 코드 품질 규칙 {#understanding-code-quality-rules}

코드 품질 테스트는 소스 코드를 스캔하여 특정 품질 기준을 충족하는지 확인합니다. OakPAL을 사용하여 SonarQube와 콘텐츠 패키지 수준 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 100개 이상의 규칙이 있습니다. 일부 AEM 관련 규칙은 AEM Engineering의 우수 사례를 기반으로 작성되며, 다음과 같이 부릅니다 [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>
>전체 규칙 목록을 다운로드할 수 있습니다 [이 링크를 사용하여 메시지를 표시합니다.](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)

### 3층 등급 {#three-tiered-gate}

코드 품질 테스트로 식별된 문제는 세 가지 카테고리 중 하나에 할당됩니다.

* **중요** - 이는 파이프라인의 즉각적인 실패를 야기하는 문제입니다.

* **중요 사항** - 파이프라인이 일시 중지 상태로 전환되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중단됩니다.

* **정보** - 정보 제공용으로만 제공되며 파이프라인 실행에 영향을 주지 않는 문제입니다

>[!NOTE]
>
>코드 품질 전용 파이프라인에서 코드 품질 테스트 단계가 파이프라인의 마지막 단계이므로 코드 품질 게이트에서의 중요한 오류를 무시할 수 없습니다.

### 등급 {#ratings}

이 단계의 결과는 다음과 같이 전달됩니다 **등급**.

다음 표에는 중요한 정보 범주 각각에 대한 등급 및 실패 임계값이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 취약점 없음 <br/>B = 최소 1개의 작은 취약성<br/> C = 최소 1개의 주요 취약성 <br/>D = 1개 이상의 중요 취약성 <br/>E = 1개 이상의 차단기 취약성 | 중요 | &lt; B |
| 신뢰성 등급 | A = 버그 없음 <br/>B = 최소 1개의 작은 버그 <br/>C = 최소 1개의 주요 버그 <br/>D = 1개 이상의 중요한 버그<br>E = 1개 이상의 차단기 버그 | 중요 | &lt; D |
| 유지 관리 등급 | 코드 냄새에 대한 해결되지 않은 수정 비용으로 정의된 값은 이미 애플리케이션에 들어온 시간의 백분율로 정의됩니다<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = 50% 이상</li></ul> | 중요 사항 | &lt; A |
| 범위 | 공식을 사용하여 단위 테스트 라인 커버리지 및 조건 커버리지의 혼합으로 정의됩니다. <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = 로 평가된 조건 `true` 단위 테스트를 실행하는 동안 한 번 이상</li><li>`CF` = 로 평가된 조건 `false` 단위 테스트를 실행하는 동안 한 번 이상</li><li>`LC` = 덮힌 라인 = lines_to_cover - indexed_lines</li><li>`B` = 총 조건 수</li><li>`EL` = 총 실행 줄 수(lines_to_cover)</li></ul> | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수 | 정보 | > 1 |
| 열린 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 선 | 중복 블록에 포함된 라인의 수로 정의됩니다. 코드 블록은 다음 조건에서 중복되는 것으로 간주됩니다.<br>비 Java 프로젝트:<ul><li>연속되는 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 적어도 다음 항목에 분산되어야 합니다. </li><li>COBOL용 코드 30줄 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li></ul>Java 프로젝트:<ul></li><li> 토큰 및 줄 수에 관계없이 10개 이상의 연속문과 중복되는 문이 있어야 합니다.</li></ul>중복을 감지할 때 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 클라우드 서비스 호환성 문제 수 | 정보 | > 0 |

>[!NOTE]
>
>을(를) 참조하십시오. [SonarQube의 지표 정의](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) 를 참조하십시오.

>[!NOTE]
>
>에서 실행되는 사용자 지정 코드 품질 규칙에 대해 자세히 알아보려면 [!UICONTROL Cloud Manager]을(를) 참조하십시오. [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## 긍정 오류 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며, 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 **긍정 오류**.

이러한 경우 소스 코드에 표준 Java로 주석을 달 수 있습니다 `@SuppressWarnings` 규칙 ID를 주석 속성으로 지정하는 주석. 예를 들어, 하나의 일반적인 긍정 오류(false positive)는 하드코딩된 암호를 검색하는 SonarQube 규칙이 하드코딩된 암호가 식별되는 방식에 대해 공격적일 수 있다는 것입니다.

다음 코드는 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube는 그러면 차단제 취약성을 일으킬 것입니다. 그러나 코드를 검토한 후에는 취약성이 아니라는 것을 인식하고 적절한 규칙 ID로 코드에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 코드가 실제로 다음과 같은 경우

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드코딩된 암호를 제거하는 것이 올바른 방법입니다.

>[!NOTE]
>
>반면에, 이것은 `@SuppressWarnings` 가능한 한 구체적이고, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 달고, 클래스 수준에서 주석을 달 수 있습니다.

>[!NOTE]
>명시적 보안 테스트 단계는 아니지만 코드 품질 단계 동안 평가된 보안 관련 코드 품질 규칙이 있습니다. 문서를 참조하십시오 [AEM as a Cloud Service 보안 개요](/help/security/cloud-service-security-overview.md) Cloud Service의 보안에 대한 자세한 내용을 살펴보십시오.

## 컨텐츠 패키지 스캔 최적화 {#content-package-scanning-optimization}

품질 분석 프로세스의 일부로 Cloud Manager는 Maven 빌드에서 생성한 컨텐츠 패키지를 분석합니다. Cloud Manager는 이 프로세스를 가속화하기 위한 최적화를 제공하므로 특정 패키징 제한이 준수될 때 효과적입니다. 가장 중요한 것은 단일 컨텐츠 패키지를 출력하는 프로젝트에 대해 수행되며, 일반적으로 &quot;모두&quot; 패키지로 지칭되며, 빌드에서 생성한 다른 컨텐츠 패키지가 생략된 것으로 표시됩니다. Cloud Manager가 이 시나리오를 감지하면 &quot;모두&quot; 패키지의 압축을 풀지 않고 개별 콘텐츠 패키지를 직접 스캔하고 종속성을 기반으로 정렬됩니다. 예를 들어 다음 빌드 출력을 고려해 보십시오.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (건너뛴-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (건너뛴-content-package)

안에 있는 유일한 항목인 경우 `myco-all-1.0.0-SNAPSHOT.zip` 건너뛴 두 개의 컨텐츠 패키지인 경우 두 개의 포함된 패키지가 &quot;모든&quot; 컨텐츠 패키지 대신 검사됩니다.

수십 개의 포함된 패키지를 생성하는 프로젝트의 경우 파이프라인 실행당 이 최적화를 사용하여 최대 10분 이상을 절약했습니다.

&quot;모두&quot; 컨텐츠 패키지에 건너뛴 컨텐츠 패키지와 OSGi 번들의 조합이 포함되어 있을 때 특별한 경우가 발생할 수 있습니다. 예를 들어 `myco-all-1.0.0-SNAPSHOT.zip` 이전에 언급된 두 개의 포함된 패키지와 하나 이상의 OSGi 번들이 포함되어 있으면 OSGi 번들만 사용하여 최소 새로운 컨텐츠 패키지가 작성됩니다. 이 패키지의 이름은 항상 다음과 같습니다 `cloudmanager-synthetic-jar-package` 그리고 포함된 번들이 `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* 이 최적화는 AEM에 배포된 패키지에 영향을 주지 않습니다.
>* 포함된 컨텐츠 패키지와 건너뛴 컨텐츠 패키지 간의 일치는 파일 이름을 기반으로 하므로 건너뛴 여러 컨텐츠 패키지에 동일한 파일 이름이 있거나 포함 중에 파일 이름이 변경된 경우에는 이 최적화를 수행할 수 없습니다.

