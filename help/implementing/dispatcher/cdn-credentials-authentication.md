---
title: CDN 자격 증명 및 인증 구성
description: Cloud Manager 구성 파이프라인을 사용하여 배포되는 구성 파일에서 규칙을 선언하여 CDN 자격 증명 및 인증을 구성하는 방법에 대해 알아봅니다.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: 37d399c63ae49ac201a01027069b25720b7550b9
workflow-type: tm+mt
source-wordcount: '1486'
ht-degree: 4%

---


# CDN 자격 증명 및 인증 구성 {#cdn-credentials-authentication}

Adobe 제공 CDN에는 몇 가지 기능과 서비스가 있으며, 그중 일부는 적절한 수준의 엔터프라이즈 보안을 보장하기 위해 자격 증명과 인증에 의존합니다. Cloud Manager [config 파이프라인을 사용하여 배포된 구성 파일에서 규칙을 선언하여 ](/help/operations/config-pipeline.md) 고객은 셀프서비스 방식으로 다음을 구성할 수 있습니다.

* Adobe CDN이 고객 관리 CDN에서 발생하는 요청의 유효성을 검사하는 데 사용하는 X-AEM-Edge-Key HTTP 헤더 값입니다.
* CDN 캐시에서 리소스를 제거하는 데 사용되는 API 토큰입니다.
* 기본 인증 양식을 제출하여 제한된 콘텐츠에 액세스할 수 있는 사용자 이름/암호 조합 목록입니다.

구성 구문을 포함한 이러한 각 요소에 대해서는 아래 해당 섹션에 설명되어 있습니다.

[키를 회전](#rotating-secrets)하는 방법에 대한 섹션이 있습니다. 이는 올바른 보안 방법입니다.

## 고객 관리 CDN HTTP 헤더 값 {#CDN-HTTP-value}

AEM as a Cloud Service의 [CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) 페이지에 설명된 대로 고객은 자체 CDN(Customer CDN(BYOCDN이라고도 함)을 통해 트래픽을 라우팅하도록 선택할 수 있습니다.

설정의 일부로 Adobe CDN과 고객 CDN은 `X-AEM-Edge-Key` HTTP 헤더의 값에 동의해야 합니다. 이 값은 Adobe CDN으로 라우팅되기 전에 고객 CDN의 각 요청에 대해 설정되고, 이 값은 값이 예상대로 맞는지 검증하므로 요청을 적절한 AEM 소스로 라우팅하는 데 도움이 되는 헤더를 포함하여 다른 HTTP 헤더를 신뢰할 수 있습니다.

*X-AEM-Edge-Key* 값은 `cdn.yaml` 또는 유사한 파일의 `edgeKey1` 및 `edgeKey2` 속성에 의해 참조되며 최상위 `config` 폴더 아래에 있습니다. 폴더 구조 및 구성 배포 방법에 대한 자세한 내용은 [구성 파이프라인 사용](/help/operations/config-pipeline.md#folder-structure)을 참조하십시오.  구문은 아래 예에 설명되어 있습니다.

>[!WARNING]
>올바른 X-AEM-Edge-Key 없이 직접 액세스가 해당 조건과 일치하는 모든 요청(아래 샘플에서 게시 계층에 대한 모든 요청을 의미)에 대해 거부됩니다. 인증을 점진적으로 도입해야 하는 경우 [트래픽 차단 위험을 줄이기 위해 안전하게 마이그레이션](#migrating-safely) 섹션을 참조하십시오.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
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

`data` 노드 위의 속성에 대한 설명은 [구성 파이프라인 사용하기](/help/operations/config-pipeline.md#common-syntax)를 참조하십시오. `kind` 속성 값은 *CDN*&#x200B;이고 `version` 속성은 `1`(으)로 설정해야 합니다.

자세한 내용은 [HTTP 헤더 유효성 검사 CDN 규칙 구성 및 배포](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/content-delivery/custom-domain-names-with-customer-managed-cdn#configure-and-deploy-http-header-validation-cdn-rule) 자습서 단계를 참조하십시오.

추가 속성은 다음과 같습니다.

* 하위 `authentication` 노드가 포함된 `Data` 노드.
* `authentication`에서 하나의 `authenticators` 노드와 하나의 `rules` 노드가 배열입니다.
* 인증자: 토큰 또는 자격 증명의 유형을 선언할 수 있습니다. 이 경우 토큰은 에지 키입니다. 여기에는 다음 속성이 포함됩니다.
   * name - 설명 문자열입니다.
   * 형식 - `edge`이어야 합니다.
   * edgeKey1 - [Cloud Manager 비밀 유형 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)을(를) 참조해야 하는 *X-AEM-Edge-Key*&#x200B;의 값. 서비스 적용 필드에서 모두를 선택합니다. 값(예: `${{CDN_EDGEKEY_052824}}`)은 추가된 날짜를 반영하는 것이 좋습니다.
   * edgeKey2 - 아래 [암호 회전 섹션](#rotating-secrets)에 설명된 대로 암호 회전에 사용됩니다. edgeKey1과 유사하게 정의합니다. `edgeKey1` 및 `edgeKey2` 중 하나 이상을 선언해야 합니다.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* 규칙: 사용해야 하는 인증자와 게시 및/또는 미리보기 계층 여부를 선언할 수 있습니다.  여기에는 다음이 포함됩니다.
   * name - 설명 문자열입니다.
   * when - [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 문서의 구문에 따라 규칙을 평가할 시기를 결정하는 조건입니다. 일반적으로 여기에는 현재 계층(예: 게시)의 비교가 포함되므로 모든 라이브 트래픽이 고객 CDN을 통한 라우팅으로 검증됩니다.
   * 작업 - 의도한 인증자가 참조된 &quot;인증&quot;을 지정해야 합니다.

>[!NOTE]
>Edge 키를 참조하는 구성을 배포하기 전에 해당 키를 [암호 형식 Cloud Manager 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)(으)로 구성해야 합니다. 최소 32바이트 길이의 고유한 임의 키를 사용하는 것이 좋습니다. 예를 들어 Open SSL 암호화 라이브러리는 `openssl rand -hex 32` 명령을 실행하여 임의 키를 생성할 수 있습니다.

### 트래픽 차단 위험을 줄이기 위해 안전하게 마이그레이션 {#migrating-safely}

사이트가 이미 라이브 상태인 경우 잘못된 구성이 공개 트래픽을 차단할 수 있으므로 고객 관리 CDN으로 마이그레이션할 때 주의하십시오. 이는 예상 X-AEM-Edge-Key 헤더 값이 있는 요청만 Adobe CDN에서 허용되기 때문입니다. 추가 조건이 일시적으로 인증 규칙에 포함되어 테스트 헤더가 포함되어 있거나 경로가 일치하는 경우에만 요청을 차단하는 접근 방식이 권장됩니다.

```
    - name: edge-auth-rule
        when:
          allOf:  
            - { reqProperty: tier, equals: "publish" }
            - { reqHeader: x-edge-test, equals: "test" }
        action:
          type: authenticate
          authenticator: edge-auth
```

```
    - name: edge-auth-rule
        when:
          allOf:
            - { reqProperty: tier, equals: "publish" }
            - { reqProperty: path, like: "/test*" }
        action:
          type: authenticate
          authenticator: edge-auth
```

다음 `curl` 요청 패턴을 사용할 수 있습니다.

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <CONFIGURED_EDGE_KEY>" -H "x-edge-test: test"
```

성공적으로 테스트한 후 추가 조건을 제거하고 구성을 다시 배포할 수 있습니다.

## API 토큰 제거 {#purge-API-token}

고객은 선언된 제거 API 토큰을 사용하여 [CDN 캐시를 제거](/help/implementing/dispatcher/cdn-cache-purge.md)할 수 있습니다. 토큰이 최상위 `config` 폴더 아래에 있는 `cdn.yaml` 또는 유사한 파일에 선언되었습니다. 폴더 구조 및 구성 배포 방법에 대한 자세한 내용은 [구성 파이프라인 사용](/help/operations/config-pipeline.md#folder-structure)을 참조하십시오.

구문은 아래에 설명되어 있습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
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

`data` 노드 위의 속성에 대한 설명은 [구성 파이프라인 사용하기](/help/operations/config-pipeline.md#common-syntax)를 참조하십시오. `kind` 속성 값은 *CDN*&#x200B;이고 `version` 속성은 `1`(으)로 설정해야 합니다.

추가 속성은 다음과 같습니다.

* 하위 `authentication` 노드가 포함된 `data` 노드.
* `authentication`에서 하나의 `authenticators` 노드와 하나의 `rules` 노드가 배열입니다.
* 인증자: 토큰 또는 자격 증명의 유형을 선언할 수 있습니다. 이 경우 삭제 키입니다. 여기에는 다음 속성이 포함됩니다.
   * name - 설명 문자열입니다.
   * 유형 - 은(는) 삭제여야 합니다.
   * purgeKey1 - 해당 값은 [Cloud Manager 비밀 유형 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)을(를) 참조해야 합니다. 서비스 적용 필드에서 모두를 선택합니다. 값(예: `${{CDN_PURGEKEY_031224}}`)은 추가된 날짜를 반영하는 것이 좋습니다.
   * purgeKey2 - 아래 [회전 비밀 섹션](#rotating-secrets) 섹션에 설명된 대로 비밀 회전에 사용됩니다. `purgeKey1` 및 `purgeKey2` 중 하나 이상을 선언해야 합니다.
* 규칙: 사용해야 하는 인증자와 게시 및/또는 미리보기 계층 여부를 선언할 수 있습니다.  여기에는 다음이 포함됩니다.
   * name - 설명 문자열
   * when - [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 문서의 구문에 따라 규칙을 평가할 시기를 결정하는 조건입니다. 일반적으로 현재 계층의 비교(예: 게시)가 포함됩니다.
   * 작업 - 의도한 인증자가 참조된 &quot;인증&quot;을 지정해야 합니다.

>[!NOTE]
>제거 키를 참조하는 구성이 배포되기 전에 제거 키를 [암호 유형 Cloud Manager 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)(으)로 구성해야 합니다. 최소 32바이트 길이의 고유한 임의 키를 사용하는 것이 좋습니다. 예를 들어 Open SSL 암호화 라이브러리는 openssl rand -hex 32 명령을 실행하여 임의 키를 생성할 수 있습니다.

제거 키를 구성하고 CDN 캐시 제거를 수행하는 데 중점을 둔 [자습서](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache)를 참조할 수 있습니다.

## 기본 인증 {#basic-auth}

사용자 이름과 암호를 요구하는 기본 인증 대화 상자를 표시하여 특정 콘텐츠 리소스를 보호합니다. 이 기능은 최종 사용자 액세스 권한에 대한 완전한 솔루션보다는 비즈니스 이해 당사자의 콘텐츠 검토와 같은 간단한 인증 사용 사례를 위한 것입니다.

최종 사용자는 다음과 같이 기본 인증 대화 상자가 표시되는 것을 경험합니다.

![basicauth-dialog](/help/implementing/dispatcher/assets/basic-auth-dialog.png)


구문은 다음과 같습니다.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  authentication:
    authenticators:
       - name: my-basic-authenticator
         type: basic
         credentials:
           - user: johndoe
             password: ${{JOHN_DOE_PASSWORD}}
           - user: janedoe
             password: ${{JANE_DOE_PASSWORD}}
    rules:
       - name: basic-auth-rule
         when: { reqProperty: path, like: "/summercampaign" }
         action:
           type: authenticate
           authenticator: my-basic-authenticator
```

`data` 노드 위의 속성에 대한 설명은 [구성 파이프라인 사용하기](/help/operations/config-pipeline.md#common-syntax)를 참조하십시오. `kind` 속성 값은 *CDN*&#x200B;이고 `version` 속성은 `1`(으)로 설정해야 합니다.

또한 구문에는 다음이 포함됩니다.

* `authentication` 노드가 포함된 `data` 노드.
* `authentication`에서 하나의 `authenticators` 노드와 하나의 `rules` 노드가 배열입니다.
* 인증자: 이 시나리오에서는 다음 구조를 갖는 기본 인증자를 선언합니다.
   * name - 설명 문자열
   * 형식은 `basic`이어야 합니다.
   * 최종 사용자가 기본 인증 대화 상자에 입력할 수 있는 다음 이름/값 쌍을 각각 포함하는 최대 10개의 자격 증명 배열입니다.
      * user - 사용자 이름
      * 암호 - 해당 값은 **모두**&#x200B;이(가) 서비스 필드로 선택된 [Cloud Manager 비밀 유형 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)을(를) 참조해야 합니다.
* 규칙: 사용해야 하는 인증자와 보호해야 하는 리소스를 선언할 수 있습니다. 각 규칙에는 다음이 포함됩니다.
   * name - 설명 문자열
   * when - [트래픽 필터 규칙](/help/security/traffic-filter-rules-including-waf.md) 문서의 구문에 따라 규칙을 평가할 시기를 결정하는 조건입니다. 일반적으로 게시 계층 또는 특정 경로의 비교가 포함됩니다.
   * 작업 - 이 시나리오에 대한 기본 인증인 의도한 인증자가 참조된 &quot;인증&quot;을 지정해야 합니다.

>[!NOTE]
>암호를 참조하는 구성이 배포되기 전에 암호를 [암호 유형 Cloud Manager 환경 변수](/help/operations/config-pipeline.md#secret-env-vars)(으)로 구성해야 합니다.

## 회전 비밀 {#rotating-secrets}

1. 경우에 따라 자격 증명을 변경하는 것이 좋습니다. 이는 비록 퍼지 키들에 대해 동일한 전략이 사용되지만, 에지 키의 예를 사용하여 이하에 예시된 바와 같이 달성될 수 있다.

1. 처음에는 `edgeKey1`만 정의되었습니다. 이 경우 `${{CDN_EDGEKEY_052824}}`(으)로 참조되며 권장 규칙으로 만들어진 날짜를 반영합니다.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
   ```
1. 키를 회전할 때가 되면 새 Cloud Manager 암호를 만드십시오(예: `${{CDN_EDGEKEY_041425}}`).
1. 구성에서 `edgeKey2`에서 참조하고 배포합니다.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey1: ${{CDN_EDGEKEY_052824}}
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```

1. 이전 에지 키가 더 이상 사용되지 않으면 구성에서 `edgeKey1`을(를) 제거하여 제거하십시오.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
   ```
1. Cloud Manager에서 이전 비밀 참조(`${{CDN_EDGEKEY_052824}}`)를 삭제하고 배포합니다.

1. 다음 순환에 대한 준비가 되면 동일한 절차를 따르되, 이번에는 `${{CDN_EDGEKEY_031426}}`과(와) 같은 이름의 새 Cloud Manager 환경 암호를 참조하여 구성에 `edgeKey1`을(를) 추가합니다.

   ```
   authentication:
     authenticators:
       - name: edge-auth
         type: edge
         edgeKey2: ${{CDN_EDGEKEY_041425}}
         edgeKey1: ${{CDN_EDGEKEY_031426}}
   ```
