---
title: Cloud Manager에서 Edge Delivery Sites 관리
description: Edge Delivery 사이트에 CDN 구성을 추가하거나 Edge Delivery 사이트를 삭제하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: fc9f7f10d1797bda5f31d82005b0afbb6ea1e644
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 64%

---

# Cloud Manager에서 Edge Delivery 사이트 관리 {#manage-edge-delivery-sites}

기존 사이트에 CDN 구성을 추가하여 Cloud Manager에서 Edge Delivery 사이트를 관리하는 방법을 알아봅니다. 또는 Edge Delivery 사이트를 삭제합니다.

## 기존 Edge Delivery 사이트에 도메인 매핑 추가 {#add-cdn-to-edge-delivery-site}

[도메인 매핑 추가](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)를 참조하십시오.

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


## Edge Delivery 사이트(Beta)에 대한 게시 계층 활성화 {#activate-publish-tier-for-eds}

>[!NOTE]
>
>여기에 설명된 게시 기능은 Beta에 있습니다. Beta에 가입하려면 Adobe 조직 ID와 프로그램 ID로 [grp-beta_xwalk-publish_config@adobe.com](mailto:grp-beta_xwalk-publish_config@adobe.com)에 전자 메일을 보내십시오.

이 기능은 유연한 게시 계층 기능이 활성화된 프로그램에서 **AEM 작성** 옵션을 사용하여 만든 Edge Delivery 사이트에만 적용됩니다.

Edge Delivery 사이트에서 AEM 작성을 사용하는 경우 Edge Delivery이 컨텐츠 전달을 처리하므로 게시 계층은 기본적으로 프로비저닝되지 않습니다. 그러나 사이트에서 필요로 하는 경우 언제든지 게시 계층을 활성화할 수 있습니다. 예를 들어 Edge Delivery과 함께 기존 AEM 게시를 지원해야 하는 경우.

Edge Delivery 사이트가 만들어지고 Cloud Manager에서 해당 상태가 **확인됨**&#x200B;을(를) 표시하면 AEM 유니버설 편집기를 사용하여 콘텐츠를 작성하고 게시할 수 있습니다.

**Cloud Manager에서 유니버설 편집기에 액세스하려면:**

1. Edge Delivery 탭의 Edge Delivery 사이트 목록에서 사이트를 찾습니다.

   ![AEM 작성자의 콘텐츠를 Edge Delivery에 게시하는 중.](/help/implementing/cloud-manager/edge-delivery/assets/eds-content-source-link.png)

1. 사이트 행에서 **컨텐츠 Source** 링크를 클릭합니다. 이 링크를 클릭하면 사이트의 컨텐츠를 작성하고 편집할 수 있는 AEM 범용 편집기 페이지가 열립니다.—>

**Edge Delivery 사이트에 대한 게시 계층을 활성화하려면:**

1. **프로그램 개요** 페이지의 **게재 게시** 탭 아래의 **환경** 카드에서 정보 아이콘을 클릭합니다.

1. 정보 팝업의 **게시 URL**&#x200B;에서 **활성화하려면 클릭**&#x200B;을 선택하여 Cloud Manager 사용자 인터페이스에서 게시 계층 프로비저닝을 사용하도록 설정합니다.

   ![게시 계층 프로비저닝을 활성화하려면 클릭](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/click-to-activate-publish-tier-capabilities.png)

1. 게시 계층 활성화 대화 상자에서 **활성화**&#x200B;를 클릭합니다.

   ![게시 계층 활성화 대화 상자](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/activate-publish-tier.png)

   활성화되면 게시 계층이 자동으로 프로비저닝됩니다. 또는 작성자가 AEM 사용자 인터페이스에서 직접 콘텐츠를 게시하려고 하는 경우 게시 계층을 자동으로 프로비저닝할 수 있습니다.

   게시 계층이 정상적으로 활성화되고 프로비저닝되면 **활성화하려면 클릭** 링크가 흐리게 표시되거나 사용할 수 없게 됩니다.

* **AEM 작성자로부터** — AEM 작성 인터페이스에서 **빠른 게시**&#x200B;를 클릭하여 콘텐츠를 Edge Delivery 사이트에 직접 게시합니다. Edge Delivery이 게재를 처리할 때 이 작업에는 게시 계층이 필요하지 않습니다.

게시 후 사이트의 `.page` URL에서 콘텐츠를 미리 보거나 `.live` URL에서 실시간으로 볼 수 있습니다.

>[!NOTE]
>
>게시 계층을 활성화하면 환경에 게시 인프라가 추가됩니다. 이 기능은 프로그램의 리소스 사용량에 영향을 줄 수 있습니다. 프로그램 수준에서 게시 계층이 필요한지 여부를 구성하려면 [유연한 게시 계층(Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier)을 참조하십시오.


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

     ![Edge Delivery Sites 버튼으로 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Helix 4와 Helix 5 간 Edge Delivery 사이트 관리

`/program/{programId}/site/{siteId}` API 엔드포인트를 사용하여 Helix 4와 Helix 5 간에 Edge Delivery 사이트를 마이그레이션할 수 있습니다.

>[!IMPORTANT]
>
>Helix 4 웹 사이트의 콘텐츠 전송 네트워크 구성은 Helix 5로 자동 마이그레이션할 수 없습니다. 이 제한 사항은 고객의 프로덕션 사이트가 아직 Helix 4에서 실행 중인 반면, Helix 5 버전은 아직 개발 중일 수 있기 때문에 존재합니다.

**사전 요구 사항**

* `sitename`이 이미 존재해야 합니다.
* 적절한 `branchName`, Helix `version` 및 `repo` 값을 알고 있어야 합니다.
* 마이그레이션은 `branchName`, Helix `version` 및 `repo`만 수정합니다. 소유자 필드는 변경할 수 없습니다.

**API 형식**

```http
PUT /api/program/{programId}/site/{siteId}
```

**요청 본문 매개변수**
요청 본문에 지정된 출처를 적용하기 위해 Edge Delivery 사이트에 대한 재정의를 만듭니다.

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
다음 원본 URL을 포함하는 Edge Delivery 사이트를 반환합니다.

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
다음 원본 URL을 포함하는 Edge Delivery 사이트를 반환합니다.

`"origin": "branch--my-website--Teo48.hlx.live"`

### 예제 3: 저장소 없는 사이트를 Helix 5로 마이그레이션

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
다음 원본 URL을 포함하는 Edge Delivery 사이트를 반환합니다.

`"origin": "main--my-repoless-website--Teo48.aem.live"`

## 지원 티켓 로그 {#eds-support-ticket}

{{support-ticket}}
