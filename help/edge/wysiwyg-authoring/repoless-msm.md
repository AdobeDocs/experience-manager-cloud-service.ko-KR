---
title: 저장소 없는 다중 사이트 관리
description: Edge Delivery Services에서 각각 제공하는 단일 코드 베이스를 활용하는 현지화된 사이트를 사용하여 재사용 가능한 방식으로 프로젝트를 설정하는 방법에 대한 모범 사례 권장 사항을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: tm+mt
source-wordcount: '1260'
ht-degree: 2%

---

# 저장소 없는 다중 사이트 관리 {#repoless-msm}

Edge Delivery Services에서 각각 제공하는 단일 코드 베이스를 활용하는 현지화된 사이트를 사용하여 재사용 가능한 방식으로 프로젝트를 설정하는 방법에 대한 모범 사례 권장 사항을 알아봅니다.

## 개요 {#overview}

[MSM(다중 사이트 관리자)](/help/sites-cloud/administering/msm/overview.md) 및 해당 Live Copy 기능을 사용하면 변형을 허용하면서 여러 위치에서 동일한 사이트 콘텐츠를 사용할 수 있습니다. 콘텐츠를 한 번 작성하고 라이브 카피를 만들 수 있습니다. MSM은 소스 콘텐츠와 해당 라이브 카피 간의 라이브 관계를 유지하여 소스 콘텐츠를 변경할 때 소스와 라이브 카피를 동기화할 수 있습니다.

MSM을 사용하여 로케일과 언어에 걸쳐 브랜드의 전체 콘텐츠 구조를 만들고 중앙에서 콘텐츠를 작성할 수 있습니다. 그런 다음 Edge Delivery Services에서 중앙 코드 베이스를 활용하여 현지화된 사이트를 각각 제공할 수 있습니다.

## 요구 사항 {#requirements}

무응답 사용 사례에서 MSM을 구성하려면 먼저 다음 작업을 완료해야 합니다.

* 이 문서에서는 사용자가 [Edge Delivery Services을 사용하여 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) 안내서를 기반으로 이미 프로젝트용 사이트를 만들었다고 가정합니다.
* [프로젝트에 대해 리디렉션 기능을 이미 사용하도록 설정](/help/edge/wysiwyg-authoring/repoless.md)한 상태여야 합니다.

## 사용 사례 {#use-case}

이 문서에서는 프로젝트에 대한 기본적인 현지화된 사이트 구조를 이미 만들었다고 가정합니다. 스위스, 독일 등에서의 입지를 가진 wknd 브랜드에 대해 다음과 같은 구조를 예로 사용한다.

```text
/content/wknd
/content/wknd/language-masters
/content/wknd/language-masters/en
/content/wknd/language-masters/de
/content/wknd/language-masters/fr
/content/wknd/language-masters/it
/content/wknd/ch
/content/wknd/ch/de
/content/wknd/ch/fr
/content/wknd/ch/it
/content/wknd/ch/en
/content/wknd/de
/content/wknd/de/de
/content/wknd/de/en
```

`language-masters`의 콘텐츠는 현지화된 사이트의 라이브 카피 소스입니다. 독일(`de`) 및 스위스(`ch`). 이 문서의 목표는 현지화된 각 사이트에 대해 동일한 코드 베이스를 사용하는 Edge Delivery Services 사이트를 만드는 것입니다.

## 구성 {#configuration}

MSM 리디렉션 사용 사례를 구성하는 몇 가지 단계가 있습니다.

1. [AEM 사이트 구성 업데이트](#update-aem-configurations).
1. [지역화된 페이지에 대한 새 Edge Delivery Services 사이트를 만듭니다](#create-edge-sites).
1. [현지화된 사이트에 대한 AEM의 클라우드 구성 업데이트](#update-cloud-configurations).

### AEM 사이트 구성 업데이트 {#update-aem-configurations}

[구성](/help/implementing/developing/introduction/configurations.md)은(는) 조직 목적으로 설정 그룹 및 관련 콘텐츠를 수집하는 데 사용할 수 있는 작업 공간으로 간주할 수 있습니다. AEM에서 사이트를 만들면 그에 대한 구성이 자동으로 만들어집니다.

일반적으로 다음과 같은 특정 콘텐츠를 사이트 간에 공유하려고 합니다.

* 블루프린트의 콘텐츠에서 생성된 템플릿
* 콘텐츠 조각 모델, 지속 쿼리 등

이러한 공유를 용이하게 하기 위해 추가 구성을 만들 수 있습니다. wknd 사용 사례의 경우 다음 경로에 대한 구성이 필요합니다.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

즉, 블루프린트에서 사용하는 wknd 브랜드 콘텐츠의 루트(`/content/wknd`)에 대한 구성과 각 현지화된 사이트(스위스 및 독일)에서 사용하는 구성이 있습니다.

1. AEM 제작 인스턴스에 로그인합니다.
1. **도구** -> **일반** -> **구성 브라우저**&#x200B;로 이동하여 **구성 브라우저**&#x200B;로 이동합니다.
1. 프로젝트에 대해 자동으로 만들어진 구성을 선택한 다음(이 경우 wknd) 도구 모음에서 **만들기**&#x200B;를 탭하거나 클릭합니다.
1. **구성 만들기** 대화 상자에서 현지화된 사이트(예: `Switzerland`)에 대한 설명 **이름**&#x200B;을 제공하고 **제목**&#x200B;에 대해 현지화된 크기의 동일한 제목을 사용합니다(이 경우 `ch`).
1. **클라우드 구성** 기능과 **편집 가능한 템플릿**&#x200B;과 같은 프로젝트에 필요한 추가 기능을 선택하십시오.
1. **만들기**&#x200B;를 탭하거나 클릭합니다.

필요한 현지화된 각 사이트에 대한 구성을 만듭니다. wknd의 경우 `ch` 구성과 함께 `de`에 대한 구성을 만들어야 합니다.

구성이 만들어지면 현지화된 사이트에서 해당 구성을 사용하도록 해야 합니다.

1. AEM 제작 인스턴스에 로그인합니다.
1. **탐색** -> **사이트**(으)로 이동하여 **사이트 콘솔**&#x200B;로 이동합니다.
1. 지역화된 사이트(예: `Switzerland`)를 선택하십시오.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 페이지 속성 창에서 **고급** 탭을 선택하고 **구성** 제목 아래에서 **/content/wknd에서 상속** 옵션을 선택 취소합니다. 여기서 `wknd`은(는) 사이트 루트입니다.
1. **클라우드 구성** 필드에서 경로 브라우저를 사용하여 현지화된 사이트(예: `/conf/wknd/ch` 아래의 `Switzerland`)에 대해 만든 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

현지화된 추가 사이트에 해당 구성을 할당합니다. wknd의 경우 독일 사이트에도 `/conf/wknd/de` 구성을 할당해야 합니다.

### 현지화된 페이지를 위한 새로운 Edge Delivery Services 사이트 생성 {#create-edge-sites}

다중 지역, 다국어 사이트 설정을 위해 더 많은 사이트를 Edge Delivery Services에 연결하려면 각 AEM MSM 사이트에 대해 새 aem.live 사이트를 설정해야 합니다. 공유 Git 저장소와 코드 베이스를 사용하는 AEM MSM 사이트와 aem.live 사이트 간에는 1:1 관계가 있습니다.

이 예제에서는 현지화된 콘텐츠가 AEM 경로 `/content/wknd/ch` 아래에 있는 스위스의 wknd에 대한 사이트 `wknd-ch`을(를) 만듭니다.

1. 프로그램에 대한 인증 토큰 및 기술 계정을 검색합니다.
   * [액세스 토큰을 얻는 방법](/help/edge/wysiwyg-authoring/repoless.md#access-token) 및 프로그램의 [기술 계정](/help/edge/wysiwyg-authoring/repoless.md#access-control)에 대한 자세한 내용은 **사이트 간 코드 재사용** 문서를 참조하십시오.
1. 구성 서비스를 다음과 같이 호출하여 새 사이트를 만듭니다. 다음을 고려하십시오.
   * POST URL의 프로젝트 이름은 생성 중인 새 사이트 이름이어야 합니다. 이 예제에서는 `wknd-ch`입니다.
   * `code` 구성은 초기 프로젝트 만들기에 사용한 구성과 같아야 합니다.
   * `content` > `source` > `url`은(는) 만들고 있는 새 사이트의 이름에 맞게 조정해야 합니다. 이 예제에서는 `wknd-ch`입니다.
   * 즉, POST URL의 사이트 이름과 `content` > `source` > `url`이(가) 같아야 합니다.
   * `admin` 블록을 조정하여 사이트에 대한 전체 관리 액세스 권한을 가져야 하는 사용자를 정의합니다.
      * 이메일 주소 배열입니다.
      * 와일드카드 `*`을(를) 사용할 수 있습니다.
      * 자세한 내용은 [작성자에 대한 인증 구성](https://www.aem.live/docs/authentication-setup-authoring#default-roles) 문서를 참조하십시오.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
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
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-ch/main",
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
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/ch/:/"
           ],
           "includes": [
               "/content/wknd/ch/"
           ]
       }
   }'
   ```

1. `https://main--wknd-ch--<your-github-org>.aem.page/config.json`을(를) 호출하고 반환된 JSON의 콘텐츠를 확인하여 새 사이트의 공용 구성이 작동하는지 확인하십시오.

현지화된 사이트를 추가로 생성하려면 단계를 반복합니다. wknd의 경우 독일어 사용자의 경우 `wknd-de` 사이트도 만들어야 합니다.

### 현지화된 페이지에 대한 AEM의 클라우드 구성 업데이트 {#update-cloud-configurations}

현지화된 현재 상태를 위해 이전 섹션에서 만든 새 Edge Delivery Sites를 사용하도록 AEM의 페이지를 구성해야 합니다. 이 예제에서 `/content/wknd/ch` 아래의 콘텐츠는 사용자가 만든 `wknd-ch` 사이트를 사용해야 합니다. 마찬가지로 `/content/wknd/de`의 콘텐츠도 `wknd-de` 사이트를 사용해야 합니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**(으)로 이동합니다.
1. 프로젝트에 대해 자동으로 생성된 구성을 선택한 다음 현지화된 페이지에 대해 생성된 폴더를 선택합니다. 이 경우 스위스(`ch`)가 됩니다.
1. 도구 모음에서 **만들기** > **구성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서:
   * **조직** 필드에 GitHub 조직을 제공합니다.
   * 사이트 이름을 이전 섹션에서 만든 사이트의 이름으로 변경합니다. 이 경우 `wknd-ch`이(가) 됩니다.
   * 프로젝트 형식을 **AEM.live로 변경하고 구성 구성을 다시 설정합니다**.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

## 설정 확인 {#verify}

필요한 구성을 모두 변경했으므로 모든 것이 예상대로 작동하는지 확인하십시오.

1. AEM 제작 인스턴스에 로그인합니다.
1. **탐색** -> **사이트**(으)로 이동하여 **사이트 콘솔**&#x200B;로 이동합니다.
1. 지역화된 사이트(예: `Switzerland`)를 선택하십시오.
1. 도구 모음에서 **편집**&#x200B;을 탭하거나 클릭합니다.
1. 페이지가 유니버설 편집기에서 제대로 렌더링되고 사이트 루트와 동일한 코드를 사용하는지 확인합니다.
1. 페이지를 변경하고 다시 게시합니다.
1. 새 Edge Delivery Services 사이트를 방문하여 `https://main--wknd-ch--<your-github-org>.aem.page`에서 해당 지역화된 페이지를 확인하십시오.

변경한 사항이 표시되면 MSM 설정이 제대로 작동하는 것입니다.
