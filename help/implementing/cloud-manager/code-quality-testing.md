---
title: 코드 품질 테스트 - Cloud Services
description: 코드 품질 테스트 - Cloud Services
translation-type: tm+mt
source-git-commit: 3bf7defc9aa36c831e061e7209a765f2d60cfb33
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---


# 코드 품질 테스트 {#code-quality-testing}

코드 품질 테스트는 애플리케이션 코드의 품질을 평가합니다. 코드 품질만 파이프라인의 핵심 목표이며 비프로덕션 및 프로덕션 파이프라인에서 빌드 단계 바로 다음에 실행됩니다.

다른 유형의 파이프라인에 대한 자세한 내용은 [CI-CD 파이프라인 구성](/help/implementing/cloud-manager/configure-pipeline.md)을 참조하십시오.

## 코드 품질 규칙 이해 {#understanding-code-quality-rules}

코드 품질 테스트에서 소스 코드가 특정 품질 기준을 충족하는지 확인하기 위해 스캔됩니다. 현재 SonarQube와 OakPAL을 사용하여 컨텐츠 패키지 레벨 검사를 조합하여 구현됩니다. 일반 Java 규칙과 AEM 관련 규칙을 결합하는 100개 이상의 규칙이 있습니다. AEM 관련 규칙 중 일부는 AEM 엔지니어링 우수 사례를 기반으로 만들어지며 [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md)이라고 합니다.

>[!NOTE]
>[여기에서 규칙 전체 목록을 다운로드할 수 있습니다](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

**3층 게이트**

식별된 문제에 대한 이 코드 품질 테스트 단계에는 3계층 구조가 있습니다.

* **중요**:이러한 문제는 파이프라인의 즉각적인 실패를 초래하는 게이트로 확인되는 문제입니다.

* **중요**:파이프라인이 일시 중지된 상태로 전환되도록 하는 게이트로 식별되는 문제입니다. 배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자는 파이프라인이 진행되는 경우 문제를 무시하거나 해당 문제를 허용할 수 있습니다. 이 경우 파이프라인이 오류로 인해 중단됩니다.

* **정보**:이러한 문제는 정보 제공용으로만 제공되며 파이프라인 실행에 영향을 주지 않는 게이트로 식별되는 문제입니다.

이 단계의 결과는 *등급*&#x200B;으로 전달됩니다.

다음 테이블에는 중요한, 중요 및 정보 범주에 대한 각 등급 및 실패 임계값이 요약되어 있습니다.

| 이름 | 정의 | 카테고리 | 실패 임계값 |
|--- |--- |--- |--- |
| 보안 등급 | A = 0 취약점 <br/>B = 최소 1개의 작은 취약점<br/> C = 최소 1개의 주요 취약점 <br/>D = 최소 1개의 중요 취약점 <br/>E = 최소 1개의 차단기 취약점 | 중요 | &lt; B |
| 신뢰성 등급 | A = 0 버그 <br/>B = 최소 1개의 경미한 버그 <br/>C = 최소 1개의 주요 버그 <br/>D = 최소 1개의 중요 버그 E = 최소 1개의 차단기 버그 | 중요 사항 | &lt; C |
| 유지 관리 등급 | 코드 냄새에 대한 뛰어난 교정 비용은 다음과 같습니다.<br/><ul><li>&lt;> </li><li>평점은 6~10% 사이의 B입니다. </li><li>평점은 11~20% 사이입니다. </li><li>평점은 21~50% 사이에서 D</li><li>50% 이상의 것은 E입니다.</li></ul> | 중요 사항 | &lt; A |
| 범위 | 이 공식을 사용하여 단위 테스트 라인 적용 범위 및 조건 적용 범위를 혼합합니다.<br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>여기서:CT = 단위 테스트를 실행하는 동안 최소 한 번 &#39;true&#39;로 평가된 조건 <br/>CF = 장치 테스트를 실행하는 동안 최소 한 번 &#39;false&#39;로 평가된 조건 <br/>LC = 적용 라인 = lines_to_cover - inded_lines <br/><br/> B = 총 실행 라인 수 <br/>줄 수(lines_to_cover) | 중요 사항 | &lt; 50% |
| 건너뛴 단위 테스트 | 건너뛴 단위 테스트 수입니다. | 정보 | > 1 |
| 미해결 문제 | 전체 문제 유형 - 취약점, 버그 및 코드 냄새 | 정보 | > 0 |
| 중복된 선 | 중복된 블록에 포함된 줄 수입니다. <br/>코드 블록을 중복으로 간주하는 경우:  <br/><ul><li>**Java가 아닌 프로젝트:**</li><li>연속된 토큰이 100개 이상 있어야 합니다.</li><li>이러한 토큰은 다음과 같은 경우에 배포해야 합니다. </li><li>COBOL을 위한 코드 줄 30개 </li><li>ABAP용 코드 20줄 </li><li>다른 언어용 코드 10줄</li><li>**Java 프로젝트:**</li><li> 토큰 및 줄 수에 관계없이 10개 이상의 연속된 명령문과 중복되는 명령문이 있어야 합니다.</li></ul> <br/>중복 여부를 감지할 때 들여쓰기와 문자열 리터럴의 차이는 무시됩니다. | 정보 | > 1% |
| Cloud Service 호환성 | 식별된 Cloud Service 호환성 문제 수입니다. | 정보 | > 0 |

>[!NOTE]
>
>자세한 정의는 [지표 정의](https://docs.sonarqube.org/display/SONAR/Metric+Definitions)를 참조하십시오.


>[!NOTE]
>
>[!UICONTROL Cloud Manager]에서 실행하는 사용자 지정 코드 품질 규칙에 대한 자세한 내용은 [사용자 지정 코드 품질 규칙](/help/implementing/cloud-manager/custom-code-quality-rules.md)을 참조하십시오.

## 잘못된 포지션 처리 {#dealing-with-false-positives}

품질 스캔 프로세스는 완벽하지 않으며 실제로 문제가 되지 않는 문제를 잘못 식별하기도 합니다. 이를 *false positive*&#x200B;라고 합니다.

이러한 경우 규칙 ID를 주석 속성으로 지정하는 표준 Java `@SuppressWarnings` 주석으로 소스 코드에 주석을 달 수 있습니다. 예를 들어, 한 가지 일반적인 문제는 하드코딩된 암호를 감지하는 SonarQube 규칙이 하드 코딩된 암호를 식별하는 방법에 대해 공격적일 수 있다는 것입니다.

특정 예제를 보려면, 이 코드는 일부 외부 서비스에 연결할 코드가 있는 AEM 프로젝트에서 매우 일반적입니다.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube는 Blocker 취약점을 해결합니다. 코드를 검토한 후 이 취약점이 아님을 확인하고 적절한 규칙 ID로 이 코드에 주석을 달 수 있습니다.

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

그런 다음 하드 코딩된 암호를 제거하는 것이 좋습니다.

>[!NOTE]
>
>`@SuppressWarnings` 주석을 가능한 구체적으로 만드는 것이 가장 좋지만, 예를 들어 문제를 일으키는 특정 문이나 블록에만 주석을 다는 것은 클래스 수준에서 주석을 달 수 있습니다.

>[!NOTE]
>명시적 보안 테스트 단계는 없지만 코드 품질 단계 동안 평가된 보안 관련 코드 품질 규칙은 여전히 있습니다. Cloud Service의 보안에 대한 자세한 내용은 [AEM에 대한 보안 개요를 Cloud Service](/help/security/cloud-service-security-overview.md)로 참조하십시오.
