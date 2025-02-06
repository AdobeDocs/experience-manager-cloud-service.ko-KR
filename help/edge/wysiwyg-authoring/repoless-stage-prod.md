---
title: 저장소 없는 스테이징 및 프로덕션 환경
description: 리디렉션 방식으로 단일 코드 베이스를 활용하는 스테이징 및 프로덕션 환경에 대해 별도의 사이트를 설정하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 701bd9bc-30e8-4654-8248-a06d441d1504
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 2%

---

# 저장소 없는 스테이징 및 프로덕션 환경 {#repoless-stage-prod}

리디렉션 방식으로 단일 코드 베이스를 활용하는 스테이징 및 프로덕션 환경에 대해 별도의 사이트를 설정하는 방법에 대해 알아봅니다.

## 개요 {#overview}

스테이징 환경과 별도로 프로덕션 환경에 대한 사이트를 설정할 수 있습니다. 별도의 스테이징 및 프로덕션 설정에 대한 두 번째 사이트를 설정하는 것은 다중 사이트 관리에 필요한 [설정](/help/edge/wysiwyg-authoring/repoless-msm.md)과 비슷합니다. 실제로 필요한 경우 MSM 사이트 구조와 결합할 수 있습니다.

이 문서에서는 별도의 스테이징 및 프로덕션 환경의 일반적인 예를 사용합니다. 원하는 환경에 대해 별도의 환경을 만들 수 있습니다.

## 구성 {#configuration}

이 문서에서는 동일한 코드 베이스를 사용하여 프로젝트에 대해 별도의 프로덕션 사이트를 설정하는 방법에 대해 설명합니다. 다음과 같은 가정을 합니다.

* 스테이징 사이트가 이미 설정되어 있으므로 프로덕션 사이트에 대한 구성을 만들려고 합니다.
* AEM 작성의 콘텐츠 구조는 유사합니다.
* 스테이징 및 프로덕션에 동일한 경로 매핑이 사용됩니다.

이 예제에서는 GitHub 리포지토리를 wknd라고도 하는 wknd라는 프로젝트에 대해 프로덕션 사이트가 이미 생성되었다고 가정합니다.

별도의 프로덕션 사이트를 구성하는 두 가지 단계가 있습니다.

1. [프로덕션 환경에 대한 새 Edge Delivery Services 사이트를 만듭니다](#create-edge-site).
1. [프로덕션 사이트에 대한 AEM의 클라우드 구성 업데이트](#update-cloud-configuration).

### 프로덕션 환경을 위한 새 Edge Delivery Services 사이트 만들기 {#create-edge-site}

1. 프로그램에 대한 인증 토큰 및 기술 계정을 검색합니다.
   * [액세스 토큰을 얻는 방법](/help/edge/wysiwyg-authoring/repoless.md#access-token) 및 프로그램의 [기술 계정](/help/edge/wysiwyg-authoring/repoless.md#access-control)에 대한 자세한 내용은 **사이트 간 코드 재사용** 문서를 참조하십시오.
1. 구성 서비스를 다음과 같이 호출하여 새 사이트를 만듭니다. 다음을 고려하십시오.
   * POST URL의 프로젝트 이름은 생성 중인 새 사이트 이름이어야 합니다. 이 예제에서는 `wknd-prod`입니다.
   * `code` 구성은 초기 프로젝트 만들기에 사용한 구성과 같아야 합니다.
   * `content` > `source` > `url`은(는) 만들고 있는 새 사이트의 이름에 맞게 조정해야 합니다. 이 예제에서는 `wknd-prod`입니다.
   * 즉, POST URL의 사이트 이름과 `content` > `source` > `url`이(가) 같아야 합니다.
   * `admin` 블록을 조정하여 사이트에 대한 전체 관리 액세스 권한을 가져야 하는 사용자를 정의합니다.
      * 이메일 주소 배열입니다.
      * 와일드카드 `*`을(를) 사용할 수 있습니다.
      * 자세한 내용은 [작성자에 대한 인증 구성](https://www.aem.live/docs/authentication-setup-authoring#default-roles) 문서를 참조하십시오.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "code": {
           "owner": "<your-github-org>",
           "repo": "wknd",
           "source": {
               "type": "github",
               "url": "https://github.com/<your-github-org>/wknd"
           }
       },
       "content": {
           "source": {
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-prod/main",
               "type": "markup",
               "suffix": ".html"
           }
       },
       "access": {
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
       }
   }'
   ```

1. 구성 서비스를 다음과 같이 호출하여 새 사이트에 대한 경로 매핑을 추가합니다.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/:/"
           ],
           "includes": [
               "/content/wknd/"
           ]
       }
   }'
   ```

`https://main--wknd-prod--<your-github-org>.aem.page/config.json`을(를) 호출하고 반환된 JSON의 콘텐츠를 확인하여 새 사이트의 공용 구성이 작동하는지 확인하십시오.

### 프로덕션 사이트에 맞게 AEM에서 클라우드 구성 업데이트 {#update-cloud-configuration}

전용 프로덕션 사이트에 대해 이전 섹션에서 만든 새 Edge Delivery Sites를 사용하도록 프로덕션 AEM을 구성해야 합니다. 이 예제에서 프로덕션 환경의 `/content/wknd` 아래에 있는 콘텐츠는 사용자가 만든 `wknd-prod` 사이트를 사용해야 합니다.

1. AEM 프로덕션 인스턴스에 로그인하고 **도구** -> **Cloud Service** -> **Edge Delivery Services 구성**(으)로 이동합니다.
1. 프로젝트에 대해 자동으로 생성된 구성을 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서:
   * **조직** 필드에 GitHub 조직을 제공합니다.
   * 사이트 이름을 이전 섹션에서 만든 사이트의 이름으로 변경합니다. 이 경우 `wknd-prod`이(가) 됩니다.
   * 프로젝트 형식을 **AEM.live로 변경하고 구성 구성을 다시 설정합니다**.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

## 설정 확인 {#verify}

필요한 구성을 모두 변경했으므로 모든 것이 예상대로 작동하는지 확인하십시오.

1. AEM 프로덕션 작성 인스턴스에 로그인합니다.
1. **탐색** -> **사이트**(으)로 이동하여 **사이트 콘솔**&#x200B;로 이동합니다.
1. 사이트에서 페이지를 선택합니다.
1. 도구 모음에서 **편집**&#x200B;을 탭하거나 클릭합니다.
1. 페이지가 유니버설 편집기에서 제대로 렌더링되고 사이트 루트와 동일한 코드를 사용하는지 확인합니다.
1. 페이지를 변경하고 다시 게시합니다.
1. `https://main--wknd-prod--<your-github-org>.aem.page`에 있는 해당 페이지의 새 Edge Delivery Services 사이트를 방문하십시오.

변경한 사항이 표시되면 별도의 프로덕션 사이트 설정이 제대로 작동하는 것입니다.
