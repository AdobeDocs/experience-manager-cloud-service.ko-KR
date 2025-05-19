---
title: 컨텐츠 Source 구성
description: Helix 4의 fstab.yaml 또는 Helix 5의 Edge Delivery Services UI(또는 구성 서비스 API)를 사용하여 Edge Delivery 사이트에 대한 콘텐츠 소스를 구성하는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8696cf8a7e7cfc439450b34fa6fda10b38cd415e
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Edge Delivery Services에 대해 한 번의 클릭으로 콘텐츠 소스 구성 {#config-content-source}

Adobe Experience Manager(AEM) Edge Delivery Services을 사용하면 빠르고 전역적으로 분산된 에지 네트워크를 사용하여 Google 드라이브, SharePoint 또는 AEM 자체와 같은 여러 소스에서 콘텐츠를 전달할 수 있습니다.

콘텐츠 소스 구성은 다음과 같은 방식으로 Helix 4와 Helix 5에서 다릅니다.

| 버전 | 컨텐츠 소스 구성 방법 |
| --- | --- |
| 헬릭스 4 | YAML 파일(`fstab.yaml`) |
| 헬릭스 5 | 구성 서비스 API(*아니요`fstab.yaml`*) |

이 문서에서는 두 버전에 대한 포괄적인 구성 단계, 예 및 유효성 검사 지침을 제공합니다.

**시작하기 전에**

Cloud Manager에서 [한 번 클릭 Edge Delivery](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site)을 사용하는 경우 사이트는 단일 리포지토리가 있는 Helix 5입니다. [Helix 5 지침을 따르고](#config-helix5) 제공된 Helix 4 YAML 버전의 지침을 대체 항목으로 사용하십시오.

**Helix 버전 확인**

* Helix 4 - 프로젝트에 `fstab.yaml` 파일이 포함되어 있습니다.
* Helix 5 - 프로젝트 *이(가) `fstab.yaml`을(를) 사용하지 않고 [Edge Delivery Services UI](#config-helix5) 또는 API를 통해 설정되었습니다.*

저장소 메타데이터를 통해 확인하거나 확실하지 않은 경우 관리자에게 문의하십시오.

## Helix 4에 대한 콘텐츠 소스 구성

Helix 4에서 fstab.yaml 파일은 사이트의 콘텐츠 소스를 정의합니다. GitHub 리포지토리의 루트에 있는 이 파일은 URL 경로 접두사(마운트 지점이라고 함)를 외부 콘텐츠 소스에 매핑합니다. 일반적인 예는 다음과 같습니다.

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

이 예는 그림에만 해당됩니다. 실제 URL은 Google 드라이브 폴더, SharePoint 디렉터리 또는 AEM 경로와 같은 컨텐츠 소스를 가리켜야 합니다.

**Helix 4에 대한 콘텐츠 원본을 구성하려면:**

단계는 사용하는 소스 시스템에 따라 다릅니다.

* **Google 드라이브**

   1. Google 드라이브 폴더를 만듭니다.
   1. `helix@adobe.com`과(와) 폴더를 공유합니다.
   1. 공유 가능한 폴더 링크를 가져옵니다.
   1. 다음과 같이 `fstab.yaml`을(를) 업데이트합니다.

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

* **SharePoint**

   1. SharePoint 폴더 또는 문서 라이브러리를 만듭니다.
   1. `helix@adobe.com`과(와) 액세스 권한을 공유합니다.
   1. 폴더 URL을 가져옵니다.
   1. 다음과 같이 `fstab.yaml`을(를) 업데이트합니다.

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

* **AEM**

   1. AEM 컨텐츠 경로를 식별합니다.
   1. 다음과 같이 AEM 컨텐츠 내보내기 URL을 사용합니다.

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. GitHub에 변경 사항을 커밋하고 푸시합니다.

### 유효성 검사

* AEM Sidekick Chrome 확장을 사용하여 **미리 보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* URL 유효성 검사: `https://main--<repo>--<org>.hlx.page/`

## Helix 5에 대한 콘텐츠 소스 구성 {#config-helix5}

Helix 5는 신뢰할 수 없으며 `fstab.yaml`을(를) 사용하지 않으며 동일한 디렉터리를 공유하는 여러 사이트를 지원합니다. 구성은 구성 서비스 API 또는 Edge Delivery Services UI를 통해 관리됩니다. 구성은 저장소 수준이 아닌 사이트 수준입니다.

개념상의 차이점은 다음과 같습니다.

| Aspect | 헬릭스 4 | 헬릭스 5 |
| --- | --- | --- |
| 구성 | `fstab.yaml`을(를) 통해 완료 | YAML 대신 API 또는 UI를 통해 수행됩니다. |
| 마운트 지점 | `fstab.yaml`에 정의되었습니다. | 필요하지 않습니다. 그 뿌리는 암묵적으로 이해된다. |

**Helix 5에 대한 콘텐츠 원본을 구성하려면:**

1. 구성 서비스 API를 사용하여 API 키 또는 액세스 토큰을 통해 인증합니다.
1. 다음 `PUT` API 호출 수행:

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

1. 응답 유효성 검사(예상: HTTP 200 OK).

### 유효성 검사

* AEM Sidekick Chrome 확장을 사용하여 **미리 보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* URL 유효성 검사: `https://main--<repo>--<org>.aem.page/`
* (선택 사항) 다음 `GET` API 호출을 통해 현재 구성을 검사합니다.

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
