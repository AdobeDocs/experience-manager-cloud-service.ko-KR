---
title: 저장소 없는 다중 사이트 관리
description: Edge Delivery Services에서 각각 제공되는 단일 코드 베이스를 활용하는 현지화된 사이트를 통해 저장소 없이 프로젝트를 설정하는 방법에 대한 모범 사례 권장 사항을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '1260'
ht-degree: 100%

---

# 저장소 없는 다중 사이트 관리 {#repoless-msm}

Edge Delivery Services에서 각각 제공되는 단일 코드 베이스를 활용하는 현지화된 사이트를 통해 저장소 없이 프로젝트를 설정하는 방법에 대한 모범 사례 권장 사항을 알아봅니다.

## 개요 {#overview}

[Multi Site Manager(MSM)](/help/sites-cloud/administering/msm/overview.md) 및 Live Copy 기능을 사용하면 다양한 변형을 활용함과 동시에 여러 지역에서 동일한 사이트 콘텐츠를 사용할 수 있습니다. 콘텐츠를 한 번 작성하고 Live Copy를 만들 수 있습니다. MSM은 소스 콘텐츠와 Live Copy 간의 라이브 관계를 유지하므로 소스 콘텐츠를 변경하면 소스와 Live Copy를 동기화할 수 있습니다.

MSM을 사용하면 여러 로케일과 언어에 걸쳐 브랜드의 전체 콘텐츠 구조를 만들고 콘텐츠를 중앙 집중식으로 작성할 수 있습니다. 현지화된 각 사이트는 중앙 코드 베이스를 활용하여 Edge Delivery Services를 통해 제공될 수 있습니다.

## 요구 사항 {#requirements}

저장소 없는 구성 설정 사용 사례에서 MSM을 구성하려면 먼저 다음 작업을 완료해야 합니다.

* 이 문서에서는 [Edge Delivery Services를 사용한 WYSIWYG 작성을 위한 개발자 시작 안내서](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)를 기반으로 프로젝트 사이트를 이미 만들었다고 가정합니다.
* [프로젝트에 대해 저장소 없는 구성 설정 기능을 이미 활성화](/help/edge/wysiwyg-authoring/repoless.md)했어야 합니다.

## 사용 사례 {#use-case}

이 문서에서는 프로젝트에 대한 기본적인 현지화된 사이트 구조를 이미 만들었다고 가정합니다. 여기서는 스위스와 독일에 기반을 둔 wknd 브랜드의 다음과 같은 구조를 예시로 사용합니다.

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

`language-masters` 콘텐츠는 독일(`de`)과 스위스(`ch`)의 현지화된 사이트에 대한 Live Copy 소스입니다. 이 문서의 목적은 현지화된 각 사이트에 대해 동일한 코드 베이스를 사용하는 Edge Delivery Services 사이트를 만드는 것입니다.

## 구성 {#configuration}

MSM 저장소 없는 구성 설정 사용 사례를 구성하려면 여러 단계를 거쳐야 합니다.

1. [AEM 사이트 구성을 업데이트합니다](#update-aem-configurations).
1. [현지화된 페이지에 대한 새로운 Edge Delivery Services 사이트를 만듭니다](#create-edge-sites).
1. [현지화된 사이트의 AEM에서 클라우드 구성을 업데이트합니다](#update-cloud-configurations).

### AEM 사이트 구성 업데이트 {#update-aem-configurations}

[구성](/help/implementing/developing/introduction/configurations.md)은 조직용으로 설정 그룹과 관련 콘텐츠를 수집하는 데 사용할 수 있는 작업 영역으로 생각할 수 있습니다. AEM에서 사이트를 만들면 해당 사이트에 대한 구성이 자동으로 생성됩니다.

일반적으로 다음과 같은 사이트 간에 특정 콘텐츠를 공유하려고 합니다.

* 블루프린트 콘텐츠에서 생성된 템플릿
* 콘텐츠 조각 모델, 지속형, 쿼리 등

이러한 공유를 용이하게 하기 위해 추가 구성을 만들 수 있습니다. wknd 사용 사례의 경우 다음 경로에 대한 구성이 필요합니다.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

즉, 블루프린트에서 사용하는 wknd 브랜드 콘텐츠 루트(`/content/wknd`)에 대한 구성과 현지화된 각 사이트(스위스 및 독일)에서 사용하는 구성을 갖게 됩니다.

1. AEM 작성 인스턴스에 로그인합니다.
1. **도구** -> **일반** -> **구성 브라우저**&#x200B;로 이동한 후 **구성 브라우저**&#x200B;로 이동합니다.
1. 프로젝트에 대해 자동으로 생성된 구성(이 경우 wknd)을 선택한 후 도구 모음에서 **만들기**&#x200B;를 탭하거나 클릭합니다.
1. **구성 만들기** 대화 상자에서 현지화된 사이트에 설명적인 **이름**(예: `Switzerland`)을 제공하고 **제목**&#x200B;에는 현지화된 사이트의 동일한 제목(이 경우 `ch`)을 사용합니다.
1. **클라우드 구성** 기능과 **편집 가능한 템플릿** 등 프로젝트에 필요한 추가 기능을 선택합니다.
1. **만들기**&#x200B;를 탭하거나 클릭합니다.

현지화된 각 사이트에 대해 필요한 구성을 만드십시오. wknd의 경우 `ch` 구성과 함께 `de` 구성도 만들어야 합니다.

구성을 만든 후에는 현지화된 사이트에서 해당 구성을 사용해야 합니다.

1. AEM 작성 인스턴스에 로그인합니다.
1. **탐색** -> **사이트**&#x200B;로 이동한 후 **사이트 콘솔**&#x200B;로 이동합니다.
1. `Switzerland`와 같은 현지화된 사이트를 선택합니다.
1. 도구 모음에서 **속성**&#x200B;을 탭하거나 클릭합니다.
1. 페이지 속성 창에서 **고급** 탭을 선택하고 **구성** 제목에서 **/content/wknd에서 상속됨** 옵션을 선택 취소합니다. 여기서 `wknd`는 사이트 루트입니다.
1. **클라우드 구성** 필드에서 경로 브라우저를 사용하여 `/conf/wknd/ch`에 있는 `Switzerland`와 같은 현지화된 사이트에 대해 만든 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

해당 구성을 추가적으로 현지화된 사이트에 할당하십시오. wknd의 경우 `/conf/wknd/de` 구성을 독일 사이트에도 할당해야 합니다.

### 현지화된 페이지에 대한 새로운 Edge Delivery Services 사이트 만들기 {#create-edge-sites}

다중 지역, 다중 언어 사이트 설정을 위해 Edge Delivery Services에 더 많은 사이트를 연결하려면 각 AEM MSM 사이트에 대해 새로운 aem.live 사이트를 설정해야 합니다. AEM MSM 사이트와 aem.live 사이트는 공유 Git 저장소와 코드 베이스를 통해 1:1 관계를 유지합니다.

이 예시에서는 스위스에 기반을 둔 wknd의 사이트 `wknd-ch`를 만들며, 현지화된 콘텐츠는 AEM 경로 `/content/wknd/ch`에 있습니다.

1. 프로그램의 인증 토큰과 기술 계정을 가져옵니다.
   * 프로그램의 [액세스 토큰](/help/edge/wysiwyg-authoring/repoless.md#access-token)과 [기술 계정을 얻는](/help/edge/wysiwyg-authoring/repoless.md#access-control) 방법에 대한 자세한 내용은 **여러 사이트에서 코드 재사용** 문서를 참조하십시오.
1. 구성 서비스에 다음 호출을 수행하여 새 사이트를 만듭니다. 다음 사항을 고려하십시오.
   * POST URL의 프로젝트 이름은 새로 만드는 사이트 이름이어야 합니다. 이 에시에서는 `wknd-ch`입니다.
   * `code` 구성은 처음 프로젝트를 만들 때 사용한 것과 동일해야 합니다.
   * `content` > `source` > `url`은 새로 만드는 사이트 이름에 맞게 조정해야 합니다. 이 에시에서는 `wknd-ch`입니다.
   * 즉, POST URL의 사이트 이름과 `content` > `source` > `url`이 동일해야 합니다.
   * `admin` 블록을 조정하여 사이트에 대한 전체 관리자 액세스 권한을 보유해야 하는 사용자를 정의합니다.
      * 이는 이메일 주소 배열입니다.
      * 와일드카드 `*`를 사용할 수 있습니다.
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

1. 구성 서비스에 다음 호출을 수행하여 새 사이트에 대한 경로 매핑을 추가합니다.

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

1. `https://main--wknd-ch--<your-github-org>.aem.page/config.json`을 호출하고 반환된 JSON 콘텐츠를 확인하여 새 사이트의 공개 구성이 제대로 작동하는지 확인합니다.

추가적으로 현지화된 사이트를 만들려면 이 단계를 반복하십시오. wknd의 경우 독일 기반에 대해서도 `wknd-de` 사이트를 만들어야 합니다.

### 현지화된 페이지의 AEM에서 클라우드 구성 업데이트 {#update-cloud-configurations}

이전 섹션에서 현지화된 기반에 대해 만든 새로운 Edge Delivery Sites를 사용하도록 AEM 페이지를 구성해야 합니다. 이 예시에서 `/content/wknd/ch`에 있는 콘텐츠는 사용자가 만든 `wknd-ch` 사이트를 사용해야 한다는 사실을 알아야 합니다. 마찬가지로 `/content/wknd/de`에 있는 콘텐츠는 `wknd-de` 사이트를 사용해야 합니다.

1. AEM 작성자 인스턴스에 로그인하고 **도구** -> **클라우드 서비스** -> **Edge Delivery Services 구성**&#x200B;으로 이동합니다.
1. 프로젝트에 대해 자동으로 생성된 구성을 선택한 후 현지화된 페이지에 대해 생성된 폴더를 선택합니다. 이 경우에는 스위스(`ch`)입니다.
1. 도구 모음에서 **만들기** > **구성**&#x200B;을 탭하거나 클릭합니다.
1. **Edge Delivery Services 구성** 창에서:
   * **조직** 필드에 GitHub 조직을 입력합니다.
   * 사이트 이름을 이전 섹션에서 만든 사이트 이름으로 변경합니다. 이 경우에는 `wknd-ch`입니다.
   * 프로젝트 유형을 **저장소 없는 구성 설정이 포함된 aem.live**&#x200B;로 변경합니다.
1. **저장 및 닫기**&#x200B;를 탭하거나 클릭합니다.

## 설정 확인 {#verify}

이제 필요한 구성을 모두 변경했으므로 모든 것이 예상대로 작동하는지 확인하십시오.

1. AEM 작성 인스턴스에 로그인합니다.
1. **탐색** -> **사이트**&#x200B;로 이동한 후 **사이트 콘솔**&#x200B;로 이동합니다.
1. `Switzerland`와 같은 현지화된 사이트를 선택합니다.
1. 도구 모음에서 **편집**&#x200B;을 탭하거나 클릭합니다.
1. 페이지가 범용 편집기에서 제대로 렌더링되고 사이트 루트와 동일한 코드를 사용하는지 확인합니다.
1. 페이지를 변경하고 다시 게시합니다.
1. `https://main--wknd-ch--<your-github-org>.aem.page`에서 현지화된 해당 페이지에 대한 새로운 Edge Delivery Services 사이트를 방문합니다.

변경 사항이 표시되면 MSM 설정이 제대로 작동하는 것입니다.
