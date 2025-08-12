---
title: 여러 사이트에서 코드 재사용
description: 모양과 동작이 대부분 동일하지만 콘텐츠가 다른 유사한 사이트가 여러 개 있는 경우 저장소 없는 모델의 여러 사이트에서 코드를 공유하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
index: false
hide: true
hidefromtoc: true
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 100%

---

# 여러 사이트에서 코드 재사용 {#repoless}

모양과 동작이 대부분 동일하지만 콘텐츠가 다른 유사한 사이트가 여러 개 있는 경우 저장소 없는 모델의 여러 사이트에서 코드를 공유하는 방법을 알아봅니다.

## 여러 사이트를 위한 단일 코드 베이스 {#one-codebase}

기본적으로 AEM은 코드 저장소에 긴밀하게 바인딩되어 있어 대부분의 사용 사례를 충족합니다. 하지만 콘텐츠가 대부분 다르지만, 동일한 코드 베이스를 활용할 수 있는 사이트가 여러 개 있을 수 있습니다.

AEM은 GitHub 저장소를 여러 개 만들고 각 사이트를 전용 GitHub 저장소에서 실행하면서 동기화를 유지하는 대신 동일한 코드베이스에서 여러 사이트를 실행하는 것을 지원합니다.

코드를 복제할 필요가 없는 이 간소화된 설정을 [&quot;저장소 없는 구성 설정&quot;](https://www.aem.live/docs/repoless)이라고도 하는데, 첫 번째 사이트를 제외한 모든 사이트는 자체 GitHub 저장소가 필요하지 않기 때문입니다.

여러 사이트에서 저장소 없이 코드를 재사용할 수 있는 유연성이 필요한 프로젝트의 경우 해당 기능을 활성화할 수 있습니다.

궁극적으로 저장소 없이 만들고 싶은 사이트 수와 관계없이 첫 번째 사이트를 만들어야 하며 이 사이트가 기본 사이트가 됩니다. 이 문서에서는 저장소 없이 사용하기 위한 첫 번째 사이트를 만드는 방법을 설명합니다.

## 사전 요구 사항 {#prerequisites}

이 기능을 활용하려면 다음 작업을 수행했는지 확인하십시오.

* [Edge Delivery Services를 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) 문서를 따라 사이트가 이미 완전히 설정되어 있습니다.
* AEM as a Cloud Service 2024.08 이상을 실행하고 있습니다.

또한 Adobe에 다음 항목을 구성해 달라고 요청해야 합니다. Slack 채널을 통해 문의하거나 지원 문제를 제기하여 Adobe에 다음 변경 사항을 적용해 달라고 요청하십시오.

* 사용자 환경에 맞게 [aem.live 구성 서비스](https://www.aem.live/docs/config-service-setup#prerequisites)를 활성화하고 사용자를 관리자로 구성해 달라고 요청합니다.
* Adobe에 프로그램의 저장소 없는 구성 설정 기능을 활성화해 달라고 요청합니다.
* Adobe에 조직을 만들어 달라고 요청합니다.

## 저장소 없는 구성 설정 기능 활성화 {#activate}

프로젝트의 저장소 없는 구성 설정 기능을 활성화하려면 여러 단계를 거쳐야 합니다.

1. [액세스 토큰 가져오기](#access-token)
1. [구성 서비스 설정](#config-service)
1. [사이트 구성 및 기술 계정 추가](#access-control)
1. [AEM 구성 업데이트](#update-aem)
1. [사이트 인증](#authenticate-site)

이 단계에서는 `https://wknd.site` 사이트를 예시로 사용합니다. 자체 사이트로 적절히 대체해 보십시오.

### 액세스 토큰 가져오기 {#access-token}

구성 서비스를 사용하고 저장소 없는 구성 설정 사용 사례에 맞게 구성하려면 먼저 액세스 토큰이 필요합니다.

1. `https://admin.hlx.page/login`으로 이동한 후 `login_adobe` 주소를 사용하여 Adobe ID 공급자로 로그인합니다.
1. `https://admin.hlx.page/profile`로 연결됩니다.
1. 브라우저 개발자 도구를 사용하여 `admin.hlx.page` 페이지에서 설정한 JSON 웹 토큰 쿠키에서 `x-auth-token` 값을 복사합니다.

액세스 토큰을 받으면 다음 형식으로 cURL 요청 헤더에 전달할 수 있습니다.

```text
--header 'x-auth-token: <your-token>'
```

### 사이트 구성을 위한 경로 매핑 추가 및 기술 계정 설정 {#access-control}

사이트 구성을 만들고 경로 매핑에 추가해야 합니다.

1. 사이트 루트에 새 페이지를 만들고 [**구성** 템플릿](/help/edge/wysiwyg-authoring/tabular-data.md#other)을 선택합니다.
   * 미리 정의된 `key` 및 `value` 열만 포함한 상태로 구성을 비워 둘 수 있습니다. 구성을 만들기만 하면 됩니다.
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

1. 다음과 유사한 cURL 명령을 사용하여 공개 구성이 설정되었고 사용 가능한지 확인합니다.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```

사이트 구성이 매핑되면 기술 계정을 정의하여 게시 권한이 부여되도록 액세스 제어를 구성할 수 있습니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**&#x200B;으로 이동한 후 사이트에 대해 자동으로 생성된 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.

1. **Edge Delivery Services 구성** 창에서 **인증** 탭을 선택하고 **기술 계정 ID** 값을 복사합니다.

   * 이 값은 `<tech-account-id>@techacct.adobe.com`과 유사합니다.
   * 기술 계정은 단일 AEM 작성자 환경의 모든 사이트에서 동일합니다.

1. 복사한 기술 계정 ID를 사용하여 다음과 유사한 cURL 명령을 통해 저장소 없는 구성에 대한 기술 계정을 설정합니다.

   * `admin` 블록을 조정하여 사이트에 대한 전체 관리자 액세스 권한을 보유해야 하는 사용자를 정의합니다.
      * 이는 이메일 주소 배열입니다.
      * 와일드카드 `*`를 사용할 수 있습니다.
      * 자세한 내용은 [작성자에 대한 인증 구성](https://www.aem.live/docs/authentication-setup-authoring#default-roles) 문서를 참조하십시오.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "<email>@<domain>.<tld>"
               ],
               "config_admin": [
                   "<tech-account-id>@techacct.adobe.com"
               ]
           },
           "requireAuth": "auto"
       }
   }'
   ```

이제 구성 서비스를 사용하므로 Git 저장소에서 `fstab.yaml` 및 `paths.json`을 제거할 수 있습니다.

>[!NOTE]
>
>구성 서비스를 사용하고 `config.json`을 통해 경로 매핑을 노출하면 `path.json` 파일이 무시됩니다.

AEM이 저장소 없이 사용할 수 있도록 구성되면 구성 서비스를 사용하여 경로 매핑이 포함된 유효한 `config.json`을 제공해야 합니다.

### AEM 구성 업데이트 {#update-aem}

이제 AEM에서 Edge Delivery Services에 필요한 변경 사항을 적용할 준비가 되었습니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**&#x200B;으로 이동한 후 사이트에 대해 자동으로 생성된 구성을 선택하고 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서 프로젝트 유형을 **저장소 없는 구성 설정이 포함된 aem.live**&#x200B;로 변경하고 **저장 및 닫기**를 탭하거나 클릭합니다.
   ![Edge Delivery Services 구성](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. 범용 편집기를 사용하여 사이트로 돌아와서 여전히 제대로 렌더링되는지 확인합니다.
1. 일부 콘텐츠를 수정하여 다시 게시합니다.
1. `https://main--<your-aem-project>--<your-github-org>.aem.page/`에서 게시된 사이트를 방문하여 변경 사항이 제대로 반영되었는지 확인합니다.

이제 프로젝트가 저장소 없이 사용할 수 있도록 설정되었습니다.

## 다음 단계 {#next-steps}

이제 기본 사이트가 저장소 없이 사용할 수 있도록 구성되었으므로 동일한 코드 베이스를 활용하는 추가 사이트를 만들 수 있습니다. 사용 사례에 따라 다음 문서를 참조하십시오.

* [저장소 없는 다중 사이트 관리](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [저장소 없는 스테이징 및 프로덕션 환경](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)
* [콘텐츠 작성을 위한 사이트 인증](/help/edge/wysiwyg-authoring/site-authentication.md)

## 문제 해결 {#troubleshooting}

저장소 없는 구성 설정 사용 사례를 구성한 후 발생하는 가장 일반적인 문제는 범용 편집기의 페이지가 더 이상 렌더링되지 않거나 흰색 페이지 또는 일반 AEM as Cloud Service 오류 메시지를 받는다는 것입니다. 이러한 경우 다음과 같은 조치를 취합니다.

* 렌더링된 페이지 소스를 봅니다.
   * 실제로 렌더링된 것이 있습니까(`scripts.js`, `aem.js` 및 편집기 관련 JSON 파일이 포함된 올바른 HTML 헤드)?
* 작성자 인스턴스의 AEM `error.log`에서 예외가 있는지 확인합니다.
   * 가장 일반적인 문제는 페이지 구성 요소가 404 오류로 인해 실패한다는 것입니다.
   * `config.json or paths.json`을 로드할 수 없음
   * `component-definition.json` 등을 로드할 수 없음
