---
title: CDN 자격 증명 및 인증 구성
description: Cloud Manager 구성 파이프라인을 사용하여 배포되는 구성 파일에서 규칙을 선언하여 CDN 자격 증명 및 인증을 구성하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
source-git-commit: e6059a1109ca93452f80440744338b809279db9b
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 3%

---

# CDN 자격 증명 및 인증 구성 {#cdn-credentials-authentication}

>[!NOTE]
>이 기능은 아직 일반적으로 사용할 수 없습니다. 얼리어답터 프로그램에 참여하려면 다음 이메일을 보내십시오. `aemcs-cdn-config-adopter@adobe.com`.

Adobe 제공 CDN에는 몇 가지 기능과 서비스가 있으며, 그중 일부는 적절한 수준의 엔터프라이즈 보안을 보장하기 위해 자격 증명과 인증에 의존합니다. 를 사용하여 배포된 구성 파일에서 규칙을 선언하여 [Cloud Manager 구성 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline), 고객은 셀프서비스 방식으로 다음을 구성할 수 있습니다.

* Adobe CDN이 고객 관리 CDN에서 오는 요청의 유효성을 검사하는 데 사용하는 HTTP 헤더 값입니다.
* CDN 캐시에서 리소스를 제거하는 데 사용되는 API 토큰입니다.

구성 구문을 포함한 이러한 각 요소에 대해서는 아래 해당 섹션에 설명되어 있습니다. 다음 [공통 설정](#common-setup) 섹션은 두 가지 모두와 배포에 공통되는 설정을 보여 줍니다. 마지막으로 다음 방법에 대한 섹션이 있습니다 [키 회전](#rotating-secrets)를 사용하는 것이 좋습니다.

## 고객 관리 CDN HTTP 헤더 값 {#CDN-HTTP-value}

에 설명된 대로 [AEM의 CDN as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) 페이지에서 고객은 자체 CDN(Customer CDN 또는 BYOCDN)을 통해 트래픽을 라우팅하도록 선택할 수 있습니다.

설정의 일부로, Adobe CDN과 고객 CDN은 의 값에 동의해야 합니다. `X-AEM-Edge-Key` HTTP 헤더. 이 값은 Adobe CDN으로 라우팅되기 전에 고객 CDN의 각 요청에 대해 설정되고, 이 값은 값이 예상대로 맞는지 검증하므로 요청을 적절한 AEM 소스로 라우팅하는 데 도움이 되는 헤더를 포함하여 다른 HTTP 헤더를 신뢰할 수 있습니다.

다음 `X-AEM-Edge-Key` 값은 아래 구문으로 선언됩니다. 다음을 참조하십시오. [공통 설정](#common-setup) 섹션 을 참조하여 배포 방법을 알아보십시오.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
      - name: edge-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_052824}}
        edgeKey2: ${{CDN_EDGEKEY_041425}}
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

구문 `X-AEM-Edge-Key` 값에는 다음이 포함됩니다.

* 종류, 버전 및 메타데이터
* 하위 항목이 포함된 데이터 노드 `experimental_authentication` 노드(기능이 릴리즈되면 실험 접두사가 제거됨).
* experiment_authentication에서 인증자 노드와 규칙 노드가 하나씩 있으며, 둘 다 배열입니다.
* 인증자: 토큰 또는 자격 증명의 유형을 선언할 수 있습니다. 이 경우 토큰은 에지 키입니다. 여기에는 다음 속성이 포함됩니다.
   * name - 설명 문자열입니다.
   * type - edge여야 합니다.
   * edgeKey1 - 해당 값은 비밀 토큰을 참조해야 하며, git에 저장되어서는 안 되고 대신 로 선언되어야 합니다. [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 암호 유형. 서비스 적용 필드에서 모두를 선택합니다. 값(예: )이 권장됩니다.`${{CDN_EDGEKEY_052824}}`)는 추가된 날짜를 반영합니다.
   * edgeKey2 - 다음에 설명된 암호 회전에 사용됩니다. [회전 비밀 섹션](#rotating-secrets) 아래요. 하나 이상의 `edgeKey1` 및 `edgeKey2` 선언해야 합니다.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* 규칙: 사용해야 하는 인증자와 게시 및/또는 미리보기 계층 여부를 선언할 수 있습니다.  여기에는 다음이 포함됩니다.
   * name - 설명 문자열입니다.
   * when - 의 구문에 따라 규칙을 언제 평가해야 하는지 결정하는 조건 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 기사. 일반적으로 여기에는 현재 계층(예: 게시)의 비교가 포함되므로 모든 라이브 트래픽이 고객 CDN을 통한 라우팅으로 검증됩니다.
   * 작업 - 의도한 인증자가 참조된 &quot;인증&quot;을 지정해야 합니다.

>[!NOTE]
>Edge 키는 다음으로 구성해야 합니다. [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 유형의 변수 `secret`를 참조한 구성이 배포되기 전에 배포됩니다.

## API 토큰 제거 {#purge-API-token}

고객은 다음을 수행할 수 있습니다. [cdn 캐시 제거](/help/implementing/dispatcher/cdn-cache-purge.md) 선언된 Purge API 토큰을 사용하여 토큰은 아래 구문으로 선언됩니다.  다음을 참조하십시오. [공통 설정](#common-setup) 섹션 을 참조하여 배포 방법을 알아보십시오.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
       - name: purge-auth
         type: purge
         purgeKey1: ${{CDN_PURGEKEY_031224}}
         purgeKey2: ${{CDN_PURGEKEY_021225}}
    rules:
     - name: purge-auth-rule
       when: { reqProperty: tier, equals: "publish" }
       action:
         type: authenticate
         authenticator: purge-auth
```

구문은

* 종류, 버전 및 메타데이터
* 하위 항목이 포함된 데이터 노드 `experimental_authentication` 노드(기능이 릴리즈되면 실험 접두사가 제거됨).
* 아래 `experimental_authentication`와 함께 사용할 수 있습니다.
* 인증자: 토큰 또는 자격 증명의 유형을 선언할 수 있습니다. 이 경우 삭제 키입니다. 여기에는 다음 속성이 포함됩니다.
   * name - 설명 문자열입니다.
   * 유형 - 은(는) 삭제여야 합니다.
   * purgeKey1 - 해당 값은 비밀 토큰을 참조해야 하며, 이 토큰을 git에 저장하면 안 되고 대신 로 선언해야 합니다. [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 유형 `secret`.
   * 서비스 적용 필드에서 모두를 선택합니다. 값(예: )이 권장됩니다. `${{CDN_PURGEKEY_031224}}`)는 추가된 날짜를 반영합니다.
   * purgeKey2 - 다음에 설명된 암호 회전에 사용됩니다. [회전 비밀 섹션](#rotating-secrets) 아래 섹션. 하나 이상의 `purgeKey1` 및 `purgeKey2` 선언해야 합니다.
* 규칙: 사용해야 하는 인증자와 게시 및/또는 미리보기 계층 여부를 선언할 수 있습니다.  여기에는 다음이 포함됩니다.
   * name - 설명 문자열
   * when - 의 구문에 따라 규칙을 언제 평가해야 하는지 결정하는 조건 [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 기사. 일반적으로 현재 계층의 비교(예: 게시)가 포함됩니다.
   * 작업 - 의도한 인증자가 참조된 &quot;인증&quot;을 지정해야 합니다.

>[!NOTE]
>Edge 키는 다음으로 구성해야 합니다. [Cloud Manager 환경 변수](/help/implementing/cloud-manager/environment-variables.md) 유형의 변수 `secret`를 참조한 구성이 배포되기 전에 배포됩니다.

## 공통 설정 {#common-setup}

모든 인증자는 다음과 같이 설정됩니다.

* 먼저 Git 프로젝트의 최상위 수준 폴더에 다음 폴더 및 파일 구조를 만듭니다.

```
config/
     cdn.yaml
```

* 두 번째로, `cdn.yaml` 구성 파일에는 아래 예제에 설명된 노드가 포함되어야 합니다. 다음 `kind` 속성을 다음으로 설정해야 합니다. `CDN` 및 버전은 현재 인 스키마 버전으로 설정해야 합니다. `1`. 메타데이터 노드에는 이 구성을 평가할 환경 유형(개발, 스테이지, 프로덕션)을 나타내는 &quot;envTypes&quot; 속성이 있습니다.

* 마지막으로 Cloud Manager에서 타깃팅된 배포 구성 파이프라인을 만듭니다. 다음을 참조하십시오 [프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) 및 [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

참고:

* RDE는 현재 구성 파이프라인을 지원하지 않습니다.
* `yq`을 사용하여 구성 파일(예: `yq cdn.yaml`)의 YAML 서식을 로컬에서 확인할 수 있습니다.

## 회전 비밀 {#rotating-secrets}

경우에 따라 자격 증명을 변경하는 것이 좋습니다. 이는 비록 퍼지 키들에 대해 동일한 전략이 사용되지만, 에지 키의 예를 사용하여 이하에 예시된 바와 같이 달성될 수 있다.

* 처음에는 `edgeKey1` 이(가) 정의되었습니다. 이 경우 (으)로 참조됨 `${{CDN_EDGEKEY_052824}}`는 권장 규칙으로 작성 날짜를 반영합니다.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* 키를 회전할 때가 되면 새 Cloud Manager 암호를 만드십시오. 예 `${{CDN_EDGEKEY_041425}}`.
* 구성에서 다음을 참조합니다. `edgeKey2` 배포.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* 이전 에지 키가 더 이상 사용되지 않는 것이 확인되면 을 제거하여 제거합니다 `edgeKey1` 을 참조하십시오.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* 이전 비밀 참조(`${{CDN_EDGEKEY_052824}}`)을 클릭하여 Cloud Manager에서 배포합니다.
* 다음 순환에 대한 준비가 되면 동일한 절차를 따르되, 이번에는 추가합니다 `edgeKey1` 구성을 위해 라는 새 Cloud Manager 환경 암호를 참조합니다. 예: `${{CDN_EDGEKEY_031426}}`.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
