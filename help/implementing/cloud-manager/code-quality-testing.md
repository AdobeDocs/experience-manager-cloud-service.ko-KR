---
title: 코드 품질 테스트 - Cloud Services
description: 코드 품질 테스트 - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---


# 코드 품질 테스트 {#code-quality-testing}

코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다. 코드 품질만 파이프라인의 핵심 목표이며 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다.

다양한 유형의 파이프라인에 [대한 자세한 내용은 CI-CD 파이프라인](/help/implementing/cloud-manager/configure-pipeline.md) 구성을 참조하십시오.

## 사용자 지정 코드 품질 규칙 이해 {#understanding-code-quality-rules}

코드 품질 테스트에서 소스 코드가 특정 품질 기준을 충족하는지 확인하기 위해 스캔됩니다. 현재 이 기능은 SonarQube와 OakPAL을 사용한 컨텐츠 패키지 레벨 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM별 규칙을 결합하는 규칙이 100개 이상 있습니다. AEM별 규칙 중 일부는 AEM Engineering의 모범 사례를 기반으로 생성되며 [사용자 지정 코드 품질 규칙이라고 합니다](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>전체 규칙 목록을 [여기에서 다운로드할 수 있습니다](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx).

이 단계의 결과는 *평등으로 전달됩니다*. 다음 표에 테스트 기준에 대한 등급이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 <br/>D = 최소 1개의 치명적인 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 보조 버그 <br/>C = 최소 1개의 주요 버그 <br/>D = 최소 1개의 중요 버그 E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 수정 비용은 다음과 같습니다. <br/><ul><li>애플리케이션 사용 시간의 &lt;=5%, 평점은 A </li><li>평점 6~10% 사이의 B </li><li>평점은 11~20% </li><li>평점은 21~50%</li><li>50% 이상이 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용하여 단위 테스트 라인 적용 범위와 조건 적용 범위를 혼합합니다. <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where:CT = 장치 테스트를 실행하는 동안 최소 한 번 &#39;true&#39;로 평가된 조건 <br/>CF = 장치 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건 <br/>LC = 적용 라인 = lines = lines_to_cover - inded_lines <br/><br/> B = 총 조건 수 <br/>EL = 실행 라인의 총 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 라인 | 중복된 블록에 포함된 라인 수입니다. <br/>코드 블록을 중복으로 간주하는 경우: <br/><ul><li>**Java가 아닌 프로젝트:**</li><li>연속된 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 다음과 같은 경우에 배포해야 합니다. </li><li>COBOL을 위한 30줄의 코드 </li><li>ABAP용 20줄의 코드 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰과 줄 수에 관계없이 10개 이상의 연속문과 중복 문이 있어야 합니다.</li></ul> <br/>중복 여부를 검색하는 동안 들여쓰기 및 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수입니다. | 정보 | > 0 |

>[!NOTE]
>
>자세한 [정의는 지표 정의를](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) 참조하십시오.


>[!NOTE]
>
>Cloud [!UICONTROL Manager에서]실행되는 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 [사용자 지정 코드 품질 규칙을 참조하십시오](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## 잘못된 양질 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며, 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 &#39;거짓 긍정&#39;이라고 한다.

이러한 경우, 소스 코드에 주석 달기 시 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 주석을 달 수 있습니다. 예를 들어, 한 가지 일반적인 문제는 하드코딩된 암호를 검색하는 SonarQube 규칙이 하드 코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예를 살펴보려면, 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 이 코드가 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube가 Blocker 취약점을 발생시킵니다. 코드를 검토한 후 이 취약점이 아님을 확인하고 적절한 규칙 ID로 이 코드에 주석을 달 수 있습니다.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러나, 반면에 코드가 실제로 다음과 같은 경우:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

그러면 하드 코딩된 암호를 제거하는 것이 좋습니다.

>[!NOTE]
>
>주석을 가능한 구체적으로 지정하는 것이 가장 좋은 방법이지만, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 다는 것은 클래스 수준에서 주석을 달 수 있습니다. `@SuppressWarnings`

>[!NOTE]
>명시적 보안 테스트 단계는 없지만 코드 품질 단계 동안 평가된 보안 관련 코드 품질 규칙은 여전히 있습니다. Cloud Service의 보안에 대한 자세한 내용은 [AEM용 보안](/help/security/cloud-service-security-overview.md) 개요를 Cloud Service으로 참조하십시오.
