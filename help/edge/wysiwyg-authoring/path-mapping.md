---
title: Edge Delivery Services에 대한 경로 매핑
description: AEM 작성 인스턴스에 사용된 페이지 경로를 웹 사이트에 사용된 공개 페이지 경로에 매핑하고 Edge Delivery Services에게 게시되는 콘텐츠를 제어하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: User
source-git-commit: 2727744f276ee5facae718a987dcc6dc54d4e917
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# Edge Delivery Services에 대한 경로 매핑 {#path-mapping}

AEM 작성 인스턴스에 사용된 페이지 경로를 웹 사이트에 사용된 공개 페이지 경로에 매핑하고 Edge Delivery Services에게 게시되는 콘텐츠를 제어하는 방법에 대해 알아봅니다.

## 개요 {#overview}

AEM을 사용하여 WYSIWYG 콘텐츠를 작성하고 Edge Delivery Services에 게시하려면 프로젝트의 경로 매핑을 설정해야 합니다. 이 매핑에는 두 가지 목적이 있습니다.

* AEM 작성 인스턴스에 사용된 페이지 경로와 웹 사이트에 사용된 공개 페이지 경로 간의 관계를 매핑하고 만듭니다.
* 페이지, 시트, 에셋 등의 콘텐츠를 제어합니다. Edge Delivery Services에 게시됩니다.

프로젝트의 콘텐츠 및 URL 구조에 따라 각 프로젝트에 대해 경로 매핑을 개별적으로 구성해야 합니다. 컨텐츠 게시 중 및 [유니버설 편집기에서 컨텐츠를 편집하는 동안 AEM에서 사용됩니다.](/help/sites-cloud/authoring/universal-editor/navigation.md)

## 구성 형식 {#configuration-format}

경로 매핑 구성의 형식은 다음 예제와 유사한 두 개의 섹션(`mappings` 및 `includes`)을 포함합니다.

```json
{
  "mappings": [
    "/content/aem-boilerplate/:/",
    "/content/aem-boilerplate/configuration:/.helix/config.json"
  ],
  "includes:" [
    "/content/aem-boilerplate/"
  ]
}
```

### 매핑 {#mappings}

`mappings` 구성에는 내부 경로(AEM 작성 인스턴스에 있음)와 외부 URL 경로(공개 웹 사이트에 있음)가 포함되어 있습니다.

형식은 `<internal paths>:<external path>`입니다. 일반적으로 최소 두 개의 항목으로 구성됩니다.

1. 예제의 첫 번째 항목은 웹 사이트 페이지의 경로 매핑입니다.
1. 두 번째 항목은 AEM 작성 저장소의 해당 스프레드시트 페이지에 대한 `.helix/config.json`의 매핑을 제어합니다.

이 예제에서는 `/content/aem-boilerplate/...`에 저장된 모든 페이지를 `https://main--my-site--org.aem.live/....` 바로 아래 Edge Delivery Services 사이트에서 공개적으로 액세스할 수 있습니다.

>[!TIP]
>
>스프레드시트로 관리되는 모든 테이블 형식 데이터(예: 메타데이터, 리디렉션 및 분류법)는 일반적으로 Edge Delivery Services에서 `.json` API URL로 게시됩니다. 이렇게 하려면 매핑 구성에 개별적으로 나열되어 있어야 합니다.
>
>자세한 내용은 [스프레드시트를 사용하여 테이블 형식 데이터 관리](/help/edge/wysiwyg-authoring/tabular-data.md) 문서를 참조하십시오.

### 포함 {#includes}

`includes` 구성은 Edge Delivery Services에 실제로 복제되는 콘텐츠 경로를 제어합니다. 또한 모든 경로 배열을 보유할 수 있으며 일반적으로 사이트 최상위 루트 페이지를 포함합니다.

Edge Delivery Services 페이지에 사용된 Assets은 일반적으로 웹 페이지와 함께 게시됩니다. AEM 작성 인스턴스에서 Edge Delivery Services으로 자동으로 내보내집니다.

>[!TIP]
>
>Edge Delivery Services에 자산을 직접 게시하려는 경우(예: 페이지 컨텍스트 외부의 URL에서 이미지 또는 PDF에 직접 액세스할 수 있게 하려는 경우) 구성의 `includes` 섹션에도 DAM 경로를 추가해야 합니다.
>
>예를 들어, PDF 집합을 포함하는 `/content/dam/my-site/documents`과(와) 같은 자산 루트 폴더에 `/assets/...`을(를) 통해 공개적으로 액세스할 수 있어야 하는 경우, 항목의 `includes` 섹션을 구성의  섹션에 추가해야 합니다.

## 구성 방법 {#how-to-configure}

프로젝트의 설정에 따라 경로 매핑을 두 가지 방법 중 하나로 구성할 수 있습니다.

1. 프로젝트가 `aem.live`에 대해 구성되어 있고 중앙 집중식 구성에 대해 [구성 서비스](https://www.aem.live/docs/config-service-setup)를 사용하는 경우 이 구성 서비스를 통해 각 사이트의 경로 매핑이 구성됩니다.

   * 다음은 경로 매핑을 구성하기 위한 cURL 요청의 예입니다.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/{org}/sites/{site}/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: ......' \
     --data '{
       "paths": {
       "mappings": [
         "/content/aem-boilerplate/:/",
         "/content/aem-boilerplate/configuration:/.helix/config.json"
       ],
       "includes": [
         "/content/aem-boilerplate/"
       ]
   }
   }'
   ```

1. 프로젝트가 구성 서비스를 사용하지 않는 경우 GitHub 프로젝트의 `paths.json` 파일을 통해 경로 매핑이 구성됩니다.

   * 예를 보려면 [`https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json`](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/paths.json)을(를) 참조하십시오.

두 경우 모두 경로 매핑을 구성하면 공개적으로 액세스할 수 있는 구성 URL `https://<branch>--<site>--<org>.aem.page/config.json`을(를) 통해 구성을 확인할 수 있습니다.
