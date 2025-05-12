---
title: Cloud Manager 2025.5.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.5.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 6b18623cc940856383009cd6b4ba011515c12ab5
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 21%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.5.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.5.0 릴리스에 대해 알아봅니다.

또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.5.0 릴리스 일자는 2025년 5월 8일 금요일입니다.

다음 릴리스는 2025년 6월 5일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

### Edge Delivery Services에서 한 번의 클릭으로 컨텐츠 소스를 변경하는 방법

Adobe Experience Manager(AEM) Edge Delivery Services을 사용하면 빠르고 전역적으로 분산된 에지 네트워크를 사용하여 Google 드라이브, SharePoint 또는 AEM 자체와 같은 여러 소스에서 콘텐츠를 전달할 수 있습니다.

콘텐츠 소스 구성은 다음과 같은 방식으로 Helix 4와 Helix 5에서 다릅니다.

| 버전 | 구성 방법 |
| --- | --- |
| 헬릭스 4 | YAML 파일(`fstab.yaml`) |
| 헬릭스 5 | 구성 서비스 API(*아니요`fstab.yaml`*) |

이 문서에서는 두 버전에 대한 포괄적인 구성 단계, 예 및 유효성 검사 지침을 제공합니다.

**시작하기 전에**

Cloud Manager에서 [한 번 클릭 Edge Delivery](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site)을 사용하는 경우 사이트는 단일 리포지토리가 있는 Helix 5입니다. Helix 5 지침에 따라 제공된 Helix 4 YAML 버전을 대체 항목으로 사용합니다.

**Helix 버전 확인**

* Helix 4 - 프로젝트에 `fstab.yaml` 파일이 포함되어 있습니다.
* Helix 5 - 프로젝트 *이(가) `fstab.yaml`을(를) 사용하지*&#x200B;하며 Edge Delivery Services UI 또는 API를 통해 설정되었습니다.

저장소 메타데이터를 통해 확인하거나 확실하지 않은 경우 관리자에게 문의하십시오.

#### 콘텐츠 소스 구성(Helix 4)

Helix 4에서 콘텐츠 원본은 GitHub 저장소의 루트에 있는 `fstab.yaml`(이)라는 YAML 구성 파일에 정의되어 있습니다.

##### YAML 파일 형식

`fstab.yaml` 파일은 다음 예제와 유사한 탑재 지점(콘텐츠 원본 URL에 매핑된 URL 경로 접두사)을 정의합니다(그림 용도로만 사용).

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

##### 콘텐츠 소스 변경

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

##### 유효성 검사

* AEM Sidekick Chrome 확장을 사용하여 **미리 보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* URL 유효성 검사: `https://main--<repo>--<org>.hlx.page/`

#### 콘텐츠 소스 구성(Helix 5)

Helix 5는 오류가 없으며 `fstab.yaml`을(를) 사용하지 않으며 동일한 디렉터리를 공유하는 여러 사이트를 지원합니다. 구성은 구성 서비스 API 또는 Edge Delivery Services UI를 통해 관리됩니다. 구성은 저장소 수준이 아닌 사이트 수준입니다.

##### 개념적 차이점

| Aspect | 헬릭스 4 | 헬릭스 5 |
| --- | --- | --- |
| 구성 파일 | `fstab.yaml` | API 또는 UI 구성 |
| 마운트 지점 | YAML 정의 | 필요하지 않음(암시적 루트) |

##### 콘텐츠 소스 변경

구성 서비스 API를 사용합니다.

1. API 키 또는 액세스 토큰을 통해 인증합니다.
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

##### 유효성 검사

* AEM Sidekick Chrome 확장을 사용하여 **미리 보기** > **게시** > **라이브 사이트 테스트**&#x200B;를 클릭합니다.
* URL 유효성 검사: `https://main--<repo>--<org>.aem.page/`
* (선택 사항) 다음 `GET` API 호출을 통해 현재 구성을 검사합니다.

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```

<!--
* **AI-powered build summaries now available for internal use**

    Internal users can now use AI-powered build summaries to simplify build log analysis. The feature provides actionable recommendations and helps identify the root causes of build failures.

    ![Build Summary dialog box](/help/implementing/cloud-manager/release-notes/assets/build-summary.png)
-->


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램(Early Adopter Program)에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 다음 얼리어답터 기회를 사용할 수 있습니다.

### Edge Delivery 파이프라인 추가 {#add-eds-pipeline}

이제 Edge Delivery Services으로 빌드된 사이트에 대해 **파이프라인**&#x200B;이 지원되므로 이 기능은 Cloud Service 환경뿐만 아니라 확장됩니다. 해당되는 경우 **파이프라인**&#x200B;을 사용하여 트래픽 필터링 규칙 및 웹 응용 프로그램 방화벽(WAF) 구성과 같은 설정을 관리할 수 있습니다. [지원되는 구성](/help/operations/config-pipeline.md#configurations)을 참조하십시오.

<!-- ![Add Edge Delivery pipeline in Add Pipeline drop-down list](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png) -->

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com)(으)로 전자 메일을 보내세요.

### Azure DevOps에 대한 지원을 통해 나만의 Git 가져오기 {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

이제 고객은 최신 Azure DevOps 및 레거시 VSTS(Visual Studio Team Services) 저장소를 모두 지원하여 Azure DevOps Git 저장소를 Cloud Manager에 온보딩할 수 있습니다.

* Edge Delivery Services 사용자의 경우 온보딩된 리포지토리를 사용하여 사이트 코드를 동기화하고 배포할 수 있습니다.
* AEM as a Cloud Service 및 Adobe Managed Services(AMS) 사용자의 경우 저장소를 전체 스택 및 프론트엔드 파이프라인 모두에 연결할 수 있습니다.

추가 파이프라인 유형에 대한 지원과 코드 품질 파이프라인을 통한 가져오기 요청 유효성 검사가 곧 제공될 예정입니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

