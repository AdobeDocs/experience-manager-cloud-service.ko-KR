---
title: 콘텐츠 소스 구성
description: Edge Delivery Site에 대해 콘텐츠 소스를 구성하는 방법을 알아봅니다. Helix 4 아키텍처에서는 `fstab.yaml`을 사용하고, Helix 5 아키텍처에서는 Cloud Manager(또는 구성 서비스 API)의 가이드 마법사를 사용합니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: 71618a5603328990603db2ee7554048c9020a883
workflow-type: ht
source-wordcount: '580'
ht-degree: 100%

---

# 한 번의 클릭으로 Edge Delivery Services에 대한 콘텐츠 소스 구성 {#config-content-source}

>[!IMPORTANT]
>
>*Helix*&#x200B;는 문서 기반 작성 기능을 갖춘 AEM Sites를 구동하는 기본 아키텍처의 내부 이름입니다. 이는 기능이나 제품 이름이 아닙니다. 이 문서에서 *Helix*&#x200B;는 Edge Delivery Sites에서 사용하는 아키텍처 버전을 의미합니다. Helix 5는 기본 아키텍처의 현재 버전이고, Helix 4는 이전 버전입니다.

Adobe Experience Manager(AEM) Edge Delivery Services를 사용하면 빠르고 전역적으로 분산된 에지 네트워크를 사용하여 Google Drive, SharePoint, AEM 자체 등 여러 소스에서 콘텐츠를 게재할 수 있습니다.

콘텐츠 소스 구성은 두 아키텍처 버전 간에 다음과 같은 차이점이 있습니다.

| 버전 | 콘텐츠 소스 구성 방법 |
| --- | --- |
| Helix 4 | YAML 파일 (`fstab.yaml`) |
| Helix 5 | 구성 서비스 API (*`fstab.yaml`* 없음) |

이 문서에서는 두 버전 모두에 대한 포괄적인 구성 단계, 예시, 유효성 검사 지침을 제공합니다.

**시작하기 전**

[Cloud Manager에서 원클릭 Edge Delivery](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site)를 사용하는 경우 사이트는 단일 저장소가 있는 Helix 5를 사용합니다. [Helix 5 지침](#config-helix5)을 따르고 대안으로 제공되는 Helix 4 YAML 버전 지침을 참조하십시오.

**Helix 버전 확인**

* Helix 4 - 프로젝트에 `fstab.yaml` 파일이 포함되어 있습니다.
* Helix 5 - 프로젝트는 `fstab.yaml`을 사용하지 *않으며* 가이드 마법사 또는 API를 사용하는 [Cloud Manager](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md)를 통해 설정되었습니다.

저장소 메타데이터를 통해 확인하거나 여전히 잘 모르겠다면 관리자에게 문의하십시오.

## Helix 4의 콘텐츠 소스 구성

Helix 4에서는 `fstab.yaml` 파일이 사이트의 콘텐츠 소스를 정의합니다. GitHub 저장소 루트에 위치한 이 파일은 URL 경로 접두사(마운트 지점이라고 함)를 외부 콘텐츠 소스에 매핑합니다. 일반적인 예시는 다음과 같습니다.

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

이 예시는 단지 일러스트레이션을 위한 것입니다. 실제 URL은 Google Drive 폴더, SharePoint 디렉터리, AEM 경로와 같이 콘텐츠 소스를 가리켜야 합니다.

**Helix 4의 콘텐츠 소스를 구성하려면 다음 작업을 수행합니다.**

단계는 사용하는 소스 시스템에 따라 다릅니다.

* **Google Drive**

   1. Google Drive 폴더를 만듭니다.
   1. `helix@adobe.com`과 폴더를 공유합니다.
   1. 공유 가능한 폴더 링크를 가져옵니다.
   1. 다음과 같이 `fstab.yaml`을 업데이트합니다.

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

* **SharePoint**

   1. SharePoint 폴더나 문서 라이브러리를 만듭니다.
   1. `helix@adobe.com`과 액세스를 공유합니다.
   1. 폴더 URL을 얻습니다.
   1. 다음과 같이 `fstab.yaml`을 업데이트합니다.

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

* **AEM**

   1. AEM 콘텐츠 경로를 식별합니다.
   1. 다음과 같이 AEM 콘텐츠 내보내기 URL을 사용합니다.

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

### 유효성 검사

* AEM Sidekick Chrome 확장 프로그램을 사용하여 **미리보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* 다음 URL의 유효성을 검사합니다. `https://main--<repo>--<org>.hlx.page/`

## Helix 5의 콘텐츠 소스 구성 {#config-helix5}

Helix 5는 저장소가 없고 `fstab.yaml`을 사용하지 않으며 동일한 디렉터리를 공유하는 여러 사이트를 지원합니다. 구성은 구성 서비스 API 또는 Edge Delivery Sites 사용자 인터페이스를 통해 관리됩니다. 구성은 저장소 수준이 아닌 사이트 수준입니다.

개념적 차이점은 다음과 같습니다.

| 측면 | Helix 4 | Helix 5 |
| --- | --- | --- |
| 구성 | `fstab.yaml`을 통해 수행됩니다. | YAML 대신 API 또는 UI를 통해 수행됩니다. |
| 마운트 지점 | `fstab.yaml`에서 정의됩니다. | 필요하지 않습니다. 루트는 암묵적으로 이해됩니다. |

**Helix 5의 콘텐츠 소스를 구성하려면 다음 작업을 수행합니다.**

1. 구성 서비스 API를 사용하여 API 키 또는 액세스 토큰을 통해 인증합니다.
1. 다음 `PUT` API 호출을 수행합니다.

   ```bash {.line-numbering}
   PUT /api/{program}/{programId}/site/{siteId}
   Content-Type: application/json
   
   {
     "sitename": "my-site",
     "branchName": "main",
     "version": "v5",
     "repo": "my-content-repo-link"
   }
   ```

1. 응답의 유효성을 검사합니다(예상: HTTP 200 OK).

### 유효성 검사

* AEM Sidekick Chrome 확장 프로그램을 사용하여 **미리보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* 다음 URL의 유효성을 검사합니다. `https://main--<repo>--<org>.aem.page/`
* (선택 사항) 다음 `GET` API 호출을 통해 현재 구성을 검사합니다.

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
