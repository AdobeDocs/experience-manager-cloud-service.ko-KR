---
title: 코드 품질 테스트 - Cloud Services
description: 코드 품질 테스트 - Cloud Services
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: f8695dd8fdc9ffb203bab943c335ab2957df6251
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 2%

---

# 코드 품질 테스트 {#code-quality-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="코드 품질 테스트"
>abstract="코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다. 이는 코드 품질 전용 파이프라인의 핵심 목표이며, 모든 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다."

코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다. 이는 코드 품질 전용 파이프라인의 핵심 목표이며, 모든 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다.

을(를) 참조하십시오. [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 다른 유형의 파이프라인에 대해 자세히 알아보십시오.

## 코드 품질 규칙 이해 {#understanding-code-quality-rules}

코드 품질 테스트에서 소스 코드가 특정 품질 기준을 충족하는지 검사합니다. 현재 SonarQube와 OakPAL을 사용하는 컨텐츠 패키지 수준 검사가 결합된 방식으로 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 규칙이 100개 이상 있습니다. 일부 AEM 관련 규칙은 AEM Engineering의 우수 사례를 기반으로 작성되며, 다음과 같이 부릅니다 [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>전체 규칙 목록을 다운로드할 수 있습니다 [여기](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

**3층 게이트**

식별된 문제에 대한 이 코드 품질 테스트 단계에서는 3계층 구조가 있습니다.

* **중요**: 이러한 문제는 파이프라인의 즉각적인 실패를 야기하는 게이트에서 식별되는 문제입니다.

* **중요 사항**: 게이트에서 식별된 문제로 인해 파이프라인이 일시 중지 상태로 전환됩니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중단됩니다.

* **정보**: 이러한 문제는 정보 제공용으로만 제공되며 파이프라인 실행에 영향을 주지 않는 게이트에서 식별되는 문제입니다

이 단계의 결과는 다음과 같이 전달됩니다 *등급*.

다음 테이블에는 [위기], [중요] 및 [정보] 범주 각각에 대한 측정 및 실패 임계값이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약성 <br/>B = 최소 1개의 작은 취약성<br/> C = 최소 1개의 주요 취약성 <br/>D = 1개 이상의 중요 취약성 <br/>E = 1개 이상의 차단기 취약성 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 작은 버그 <br/>C = 최소 1개의 주 버그 <br/>D = 1개 이상의 중요 버그 E = 1개 이상의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 치료 비용은 다음과 같습니다. <br/><ul><li>&lt;=5%의 시간이 이미 애플리케이션에 투입되어 등급이 A입니다. </li><li>6~10% 사이의 등급은 B입니다 </li><li>11~20% 평가 </li><li>평점은 21~50% 사이에서 D</li><li>50%가 넘는 것은 E입니다</li></ul> | 중요 사항 | &lt; A |
| 범위 | 다음 공식을 사용하여 단위 테스트 라인 커버리지 및 조건 커버리지의 혼합입니다. <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>위치: CT = 단위 테스트를 실행하는 동안 적어도 한 번 &#39;true&#39;로 평가된 조건 <br/>CF = 단위 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건입니다. <br/>LC = 적용 라인 = lines_to_cover - indexed_lines <br/><br/> B = 총 조건 수 <br/>EL = 실행 라인의 총 수(line_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 열린 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 선 | 중복 블록에 관련된 라인 수입니다. <br/>중복으로 간주되는 코드 블록의 경우: <br/><ul><li>**비 Java 프로젝트:**</li><li>연속되는 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 적어도 다음에 배포해야 합니다. </li><li>COBOL용 코드 30줄 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰 및 줄 수에 관계없이 10개 이상의 연속된 문과 중복되는 문이 있어야 합니다.</li></ul> <br/>중복을 검색하는 동안 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수입니다. | 정보 | > 0 |

>[!NOTE]
>
>을(를) 참조하십시오. [지표 정의](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) 를 참조하십시오.


>[!NOTE]
>
>에서 실행되는 사용자 지정 코드 품질 규칙에 대해 자세히 알아보려면 [!UICONTROL Cloud Manager]을(를) 참조하십시오. [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## 긍정 오류 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며, 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 *긍정 오류*.

이러한 경우 소스 코드에 표준 Java로 주석을 달 수 있습니다 `@SuppressWarnings` 규칙 ID를 주석 속성으로 지정하는 주석. 예를 들어, 하나의 일반적인 문제는 하드코딩된 암호를 검색하는 SonarQube 규칙이 하드코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예를 보려면, 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 이 코드가 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러면 SonarQube가 차단기 취약성을 높입니다. 코드를 검토한 후 취약점이 아님을 식별하고 적절한 규칙 ID로 여기에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나 반면에 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그런 다음 하드코딩된 암호를 제거하는 것이 올바른 방법입니다.

>[!NOTE]
>
>반면에, 이것은 `@SuppressWarnings` 가능한 한 구체적이고, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 달고, 클래스 수준에서 주석을 달 수 있습니다.

>[!NOTE]
>명시적 보안 테스트 단계는 없지만 코드 품질 단계 동안 평가된 보안 관련 코드 품질 규칙이 있습니다. 을(를) 참조하십시오. [AEM as a Cloud Service 보안 개요](/help/security/cloud-service-security-overview.md) Cloud Service의 보안에 대한 자세한 내용을 살펴보십시오.
