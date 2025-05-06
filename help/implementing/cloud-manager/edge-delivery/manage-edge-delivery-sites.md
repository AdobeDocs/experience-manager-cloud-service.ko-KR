---
title: Cloud Manager에서 Edge Delivery Sites 관리
description: Edge Delivery 사이트에 CDN 구성을 추가하거나 Edge Delivery 사이트를 삭제하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 4fa8c65d9744b9451089423de0da63b39530973e
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 76%

---

# Cloud Manager에서 Edge Delivery 사이트 관리 {#manage-edge-delivery-sites}

기존 사이트에 CDN 구성을 추가하여 Cloud Manager에서 Edge Delivery 사이트를 관리하는 방법을 알아봅니다. 또는 Edge Delivery 사이트를 삭제합니다.

## 기존 Edge Delivery 사이트에 CDN 구성 추가 {#add-cdn-to-edge-delivery-site}

[CDN 구성 추가](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)를 참조하십시오.

## Edge Delivery 사이트 이름 변경 (#rename-edge-delivery-site)

Adobe Cloud Manager에서 다음의 이유로 Edge Delivery 사이트 이름을 바꾸고자 할 수 있습니다.

* **명확성과 조직성**: 사이트의 목적이나 관련 환경(예: 프로덕션, 스테이징)을 더 잘 설명할 수 있습니다.
* **혼란 방지**: 여러 사이트를 사용 중인 경우 이름을 변경해 두 사이트를 쉽게 구분할 수 있으면 잘못된 사이트에 구성이나 업데이트를 적용할 가능성을 줄일 수 있습니다.
* **표준화**: 조직의 지침에 부합하는 일관된 명명 규칙을 따라 관리 및 감사를 더 쉽게 진행할 수 있습니다.

**Edge Delivery 사이트의 이름을 바꾸려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery Services가 포함된 프로그램을 선택하고, 여기에 Edge Delivery 사이트를 추가합니다.
1. 다음 중 하나를 수행합니다.

   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. Edge Delivery 사이트 테이블에서 이름을 바꾸려는 사이트의 행 끝의 줄임표를 클릭합니다.
**이름 변경**&#x200B;을 클릭합니다.
   * 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다. **서비스** 제목 아래 ![Web pages icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**를 클릭합니다.
Edge Delivery 사이트 테이블에서 이름을 바꾸려는 사이트의 행 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다. **이름 변경**&#x200B;을 클릭합니다.

1. **Edge Delivery 사이트 편집** 대화 상자에서 **사이트 이름** 텍스트 필드에 사이트의 새 이름을 입력합니다.

1. **편집**&#x200B;을 클릭합니다.

## Edge Delivery 사이트를 삭제 {#delete-edge-delivery-site}

Edge Delivery Services 사이트를 삭제하면 관련 CDN 구성도 모두 제거됩니다. 이 작업은 사용자 정의 도메인과 사이트 간의 연결을 끊습니다. 자세한 내용은 CDN 구성을 참조하십시오. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Edge Delivery 사이트를 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery Services가 포함된 프로그램을 선택하고, 여기에 Edge Delivery 사이트를 추가합니다.
1. 다음 중 하나를 수행합니다.

   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. Edge Delivery 사이트 테이블에서 삭제하려는 사이트의 행 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
![Edge Delivery 사이트 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **삭제**&#x200B;를 클릭한 후 **삭제**&#x200B;를 다시 클릭하여 사이트 삭제를 확인합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * 페이지의 왼쪽 상단에서 ![메뉴 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)을 클릭하여 왼쪽 사이드 메뉴를 표시합니다. **서비스** 제목 아래 ![Edge Delivery 사이트용 웹 페이지 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**를 클릭합니다.
Edge Delivery 사이트 테이블에서 삭제하려는 사이트의 행 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다. ![Edge Delivery 사이트 삭제 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **삭제**&#x200B;를 클릭한 후 **삭제**&#x200B;를 다시 클릭하여 사이트 삭제를 확인합니다.

     ![Edge Delivery Sites 버튼에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Helix 4와 Helix 5 간의 Edge Delivery 사이트 관리

`/program/{programId}/site/{siteId}` API 끝점을 사용하여 Helix 4와 Helix 5 간에 Edge Delivery 사이트를 마이그레이션합니다.

>[!IMPORTANT]
>
>Helix 4 웹 사이트에 대한 CDN 구성은 Helix 5로 자동으로 마이그레이션할 수 없습니다. 고객 프로덕션 사이트는 Helix 4에서 실행될 수 있지만 Helix 5 버전은 아직 개발 중이기 때문에 이러한 제한이 있습니다.

**전제 조건**

* `sitename`이(가) 이미 있어야 합니다.
* 적절한 `branchName`, Helix `version` 및 `repo` 값을 알고 있습니다.
* 마이그레이션은 `branchName`, `version` 및 `repo`만 수정합니다. 소유자 필드는 변경할 수 없습니다.

**API 형식**

```http
PUT /api/program/{programId}/site/{siteId}
```

**본문 매개 변수 요청**
Edge Delivery 사이트에 대한 재정의를 만들어 요청 본문에 지정된 원본을 적용합니다.

```json
{
  "sitename": "<required site name>",
  "branchName": "<git branch>",
  "version": "v4" | "v5",
  "repo": "<git repository name>"
}
```

### 예제 1: Helix 5로 마이그레이션

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix5",
  "branchName": "branch",
  "version": "v5",
  "repo": "my-website"
}
```

**원본 URL 결과**
다음 원본 URL을 사용하여 Edge Delivery 사이트를 반환합니다.

`"origin": "branch--my-website–Teo48.aem.live"`


### 예제 2: Helix 4로 마이그레이션

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix4",
  "branchName": "branch",
  "version": "v4",
  "repo": "my-website"
}
```

**원본 URL 결과**
다음 원본 URL을 사용하여 Edge Delivery 사이트를 반환합니다.

`"origin": "branch--my-website--Teo48.hlx.live"`

### 예제 3: 무시 사이트를 Helix 5로 마이그레이션

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-reposless-website",
  "branchName": "main",
  "version": "v5",
  "repo": "my-reposless-website"
}
```

**원본 URL 결과**
다음 원본 URL을 사용하여 Edge Delivery 사이트를 반환합니다.

`"origin": "main--my-repoless-website--Teo48.aem.live"`

## 지원 티켓 로그 {#eds-support-ticket}

{{support-ticket}}
