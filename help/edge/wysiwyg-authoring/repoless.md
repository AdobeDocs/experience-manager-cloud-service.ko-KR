---
title: 사이트 간 코드 재사용
description: 대부분 동일하게 보이고 동작하지만 콘텐츠가 다른 유사한 사이트가 많은 경우, 무시 모델의 여러 사이트에서 코드를 공유하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: e25e21984ebadde7076d95c6051b8bfca5b2ce03
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---


# 사이트 간 코드 재사용 {#repoless}

대부분 동일하게 보이고 동작하지만 콘텐츠가 다른 유사한 사이트가 많은 경우, 무시 모델의 여러 사이트에서 코드를 공유하는 방법을 알아봅니다.

## 여러 사이트를 위한 하나의 코드베이스 {#one-codebase}

기본적으로 AEM은 코드 리포지토리에 단단히 바인딩되며, 이는 대부분의 사용 사례를 충족합니다. 그러나 대부분 콘텐츠가 다른 사이트가 여러 개 있을 수 있지만 동일한 코드 베이스를 활용할 수 있습니다.

AEM에서는 여러 GitHub 저장소를 만들고 동기화를 유지하면서 전용 GitHub 저장소에서 각 사이트를 실행하는 대신 동일한 코드 베이스에서 여러 사이트 실행을 지원합니다.

첫 번째 사이트를 제외한 모든 사이트에는 자체 GitHub 저장소가 필요하지 않으므로 코드 복제를 수행할 필요가 없는 간소화된 설정을 [&quot;repoless&quot;,](https://www.aem.live/docs/repoless)라고도 합니다.

프로젝트에서 사이트 간 코드 재사용의 무한한 유연성이 필요한 경우 기능을 활성화할 수 있습니다.

궁극적으로 무해한 방식으로 만들려는 사이트 수에 관계없이, 기본 사이트 역할을 하는 첫 번째 사이트를 만들어야 합니다. 이 문서에서는 재사용 방지를 위한 첫 번째 사이트를 만드는 방법에 대해 설명합니다.

## 사전 요구 사항 {#prerequisites}

이 기능을 활용하려면 다음을 수행해야 합니다.

* 문서 [Edge Delivery Services을 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 따라 사이트가 이미 완전히 설정되었습니다.
* 최소한 AEM as a Cloud Service 2024.08을 실행하고 있습니다.

또한 Adobe에게 두 항목을 구성하도록 요청해야 합니다. 이러한 요청을 수행하려면 Slack 채널을 통해 Adobe에 연락하거나 지원 문제를 제기하십시오.

* [aem.live 구성 서비스](https://www.aem.live/docs/config-service-setup#prerequisites)이(가) 사용자 환경에 대해 활성 상태이므로 관리자로 구성되었습니다.
* 프로그램에 대해 Adobe 기능을 활성화해야 합니다.

## 재생 기능 활성화 {#activate}

프로젝트에 대해 무시 기능을 활성화하는 몇 가지 단계가 있습니다.

1. [액세스 토큰 검색](#access-token)
1. [구성 서비스 설정](#config-service)
1. [액세스 제어 설정](#access-control)
1. [AEM 구성 업데이트](#update-aem)
1. [사이트 인증](#authenticate-site)

이 절차에서는 사이트 `https://wknd.site`을(를) 예로 사용합니다. 자신의 것을 적절히 바꾸십시오.

### 액세스 토큰 검색 {#access-token}

먼저 구성 서비스를 사용하고 이를 재사용 금지 사용 사례에 맞게 구성하려면 액세스 토큰이 필요합니다.

1. `https://admin.hlx.page/login`(으)로 이동하고 `login_adobe` 주소를 사용하여 Adobe ID 공급자로 로그인합니다.
1. `https://admin.hlx.page/profile`에게 전달됩니다.
1. 브라우저의 개발자 도구를 사용하여 `admin.hlx.page` 페이지가 설정하는 JSON 웹 토큰 쿠키에서 `x-auth-token`의 값을 복사합니다.

액세스 토큰이 있으면 다음 형식으로 cURL 요청의 헤더에 전달될 수 있습니다.

```text
--header 'x-auth-token: <your-token>'
```

### 구성 서비스 구성 {#config-service}

[필수 구성 요소 ](#prerequisites)에서 설명한 대로 환경에 대해 구성 서비스를 사용하도록 설정해야 합니다. 이 cURL 명령을 사용하여 구성 서비스 설정을 확인할 수 있습니다.

```text
curl  --location 'https://admin.hlx.page/config/<your-github-org>.json' \
--header 'x-auth-token: <your-token>'
```

구성 서비스가 제대로 설정되면 다음과 유사한 JSON이 반환됩니다.

```json
{
  "title": "<your-github-org>",
  "description": "Your GitHub Org",
  "lastModified": "2024-11-14T12:14:04.230Z",
  "created": "2024-11-14T12:13:37.032Z",
  "version": 1,
  "users": [
    {
      "email": "justthisguyyouknow@adobe.com",
      "roles": [
        "admin"
      ],
      "id": "<your-id>"
    }
  ]
}
```

구성 서비스가 활성화되지 않은 경우 프로젝트 Slack 채널을 통해 Adobe에게 연락하거나 지원 문제를 제기하십시오. 토큰을 가지고 구성 서비스가 활성화되어 있는지 확인하면 구성을 계속할 수 있습니다.

1. 콘텐츠 소스가 제대로 설정되었는지 확인합니다.

   ```text
   curl --request GET \
   --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>.json \
   --header 'x-auth-token: <your-token>'
   ```

1. 공개 구성에 경로 매핑을 추가합니다.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```

공개 구성이 만들어지면 `https://main--<your-aem-project>--<your-github-org>.aem.page/config.json`과(와) 유사한 URL을 통해 액세스하여 확인할 수 있습니다.

### 액세스 제어 설정 {#access-control}

액세스 제어를 설정하려면 기술 계정을 제공해야 합니다.

1. 사이트의 루트에 새 페이지를 만들고 [**구성** 템플릿을 선택합니다.](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * 미리 정의된 `key` 및 `value` 열만 있는 구성을 비워 둘 수 있습니다. 만들기만 하면 됩니다.
1. 다음과 유사한 cURL 명령을 사용하여 공개 구성에서 사이트 구성에 대한 매핑을 만듭니다.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/",
               "/content/<your-site-content>/configuration:/.helix/config.json"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```
1. 공개 구성이 설정되었는지 확인하고 다음과 유사한 cURL 명령을 사용하여 사용할 수 있습니다.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```
1. 이제 브라우저에서 다음 링크의 응답으로 기술 계정을 검색할 수 있습니다.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

응답은 다음과 비슷합니다.

```json
{
  "total": 1,
  "offset": 0,
  "limit": 1,
  "data": [
    {
      "key": "admin.role.publish",
      "value": "<tech-account-id>@techacct.adobe.com"
    }
  ],
  ":type": "sheet"
}
```

1. 다음과 유사한 cURL 명령을 사용하여 구성에서 기술 계정을 설정합니다.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "*@adobe.com"
               ],
               "config_admin": [
                   "<tech-account-id>@techacct.adobe.com"
               ]
           },
           "requireAuth": "auto"
       }
   }'
   ```

이제 구성 서비스를 사용하므로 Git 저장소에서 `fstab.yaml` 및 `paths.json`을(를) 제거할 수 있습니다.

>[!NOTE]
>
>구성 서비스를 사용하고 `config.json`을(를) 통해 경로 매핑을 노출하면 `path.json` 파일이 무시됩니다.

AEM이 다시 사용되지 않도록 구성되면 구성 서비스를 사용하고 경로 매핑에 유효한 `config.json`을(를) 제공해야 합니다.

### AEM 구성 업데이트 {#update-aem}

이제 AEM에서 Edge Delivery Services에 필요한 사항을 변경할 준비가 되었습니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **Cloud Service** -> **Edge Delivery Services 구성**(으)로 이동한 다음 사이트에 대해 자동으로 만들어진 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서 프로젝트 형식을 **AEM.live에 무수정 구성 설정**(으)로 변경하고 **저장 및 닫기**를 탭하거나 클릭합니다.
   ![Edge Delivery Services 구성](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. 범용 편집기를 사용하여 사이트로 돌아가서 제대로 렌더링되는지 확인하십시오.
1. 일부 콘텐츠를 수정하고 다시 게시합니다.
1. `https://main--<your-aem-project>--<your-github-org>.aem.page/`에 게시된 사이트를 방문하여 변경 내용이 제대로 반영되었는지 확인하십시오.

이제 프로젝트를 무보수로 사용할 수 있도록 설정했습니다.

## 다음 단계 {#next-steps}

이제 기본 사이트가 무차별 사용을 위해 구성되었으므로 동일한 코드 베이스를 활용하는 추가 사이트를 만들 수 있습니다. 사용 사례에 따라 다음 설명서를 참조하십시오.

* [복수 사이트 관리 무시](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [스테이징 및 프로덕션 환경 무시](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## 문제 해결 {#troubleshooting}

무시 사용 사례를 구성한 후 발생하는 가장 일반적인 문제는 유니버설 편집기의 페이지가 더 이상 렌더링되지 않거나 흰색 페이지 또는 일반 AEM as a Cloud Service 오류 메시지가 표시된다는 것입니다. 이 경우

* 렌더링된 페이지의 소스를 봅니다.
   * 실제로 렌더링된 항목이 있습니까? `scripts.js`, `aem.js` 및 편집기 관련 JSON 파일이 있는 올바른 HTML 헤드
* 작성자 인스턴스의 AEM `error.log`에서 예외를 확인합니다.
   * 가장 일반적인 문제는 페이지 구성 요소가 실패하고 404 오류가 발생한다는 것입니다.
   * `config.json or paths.json`을(를) 로드할 수 없습니다.
   * `component-definition.json`개 등 로드할 수 없음
