---
title: Cloud Service으로 AEM Commerce 시작하기
description: 상거래 기반의 AEM 프로젝트를 Cloud 서비스 환경으로 실행 중인 AEM에 배포하는 방법에 대해 학습합니다. Adobe Cloud Manager와 CI/CD 파이프라인의 기능을 사용하여 Venia 참조 스토어를 실행 중인 환경에 구축할 수 있습니다.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
translation-type: tm+mt
source-git-commit: 08e258d4e9cd67de3da2aa57c058036bd104472d
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 3%

---

# Cloud Service {#start}으로 AEM Commerce 시작하기

Cloud Service으로 AEM Commerce를 시작하려면 Experience Manager Cloud Service에 CEF(Commerce Integration Framework) 추가 기능이 제공되어야 합니다. CIF Add-on은 Cloud Service](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/sites/home.html)으로 [AEM Sites 위에 있는 추가 모듈입니다.

## 온보딩 {#onboarding}

Cloud Service으로 AEM Commerce에 대한 온보딩은 2단계 프로세스입니다.

1. AEM Commerce를 Cloud Service이 활성화되고 제공된 CIF Add-On으로 사용
2. 전자 상거래 솔루션과 Cloud Service으로 AEM Commerce 연결

첫 번째 온보딩 단계는 Adobe에 의해 행해진다. 가격 및 프로비저닝에 대한 자세한 내용은 해당 세일즈 담당자에게 문의해야 합니다.

CIF Add-On을 제공받으면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 새로 만들어야 합니다. 자세한 내용은 [프로그램 설정](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html)을 참조하십시오.

두 번째 단계는 Cloud Service 환경으로서 각 AEM에 대한 셀프 서비스입니다. CIF Add-On의 초기 프로비저닝 후 수행해야 하는 추가 구성이 있습니다.

## 전자 상거래 솔루션 {#magento}에 AEM 연결

CIF 추가 기능과 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 상거래 솔루션과 연결하려면 클라우드 관리자 환경 변수를 통해 GraphQL 끝점 URL을 제공해야 합니다. 변수 이름은 `COMMERCE_ENDPOINT`입니다. HTTPS를 통한 보안 연결을 구성해야 합니다.

이 환경 변수는 다음 두 곳에서 사용됩니다.

- GraphQL은 AEM CIF 핵심 구성 요소 및 고객 프로젝트 구성 요소에서 사용되는 몇 가지 공통 공유 가능한 GraphQl 클라이언트를 통해 AEM에서 커머스 백엔드로 호출합니다.
- 변수가 `/api/graphql`에 설정되어 있는 각 AEM 환경에서 GraphQL 프록시 URL을 설정합니다. AEM 상거래 제작 도구(CEF Add-on) 및 CIF 클라이언트측 구성 요소에서 사용됩니다.

다른 GraphQL 끝점 URL은 Cloud Service 환경으로 각 AEM에 사용할 수 있습니다. 이렇게 프로젝트를 통해 AEM 스테이징 환경과 커머스 스테이징 시스템 및 AEM 프로덕션 환경을 커머스 프로덕션 시스템에 연결할 수 있습니다. GraphQL 끝점은 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결은 지원되지 않습니다. 인증이 필요한 추가 CIF 기능을 사용하기 위해 인증 헤더를 제공할 수도 있습니다.

선택 사항이며 Adobe Commerce Enterprise/Cloud에만 해당됩니다. CIF Add-on은 AEM 작성자를 위해 스테이지된 카탈로그 데이터를 사용할 수 있도록 지원합니다. 인증 토큰을 구성해야 합니다. 구성된 인증 토큰은 보안상의 이유로 AEM 작성자 인스턴스에서만 사용 및 사용할 수 있습니다. AEM 게시 인스턴스는 단계 데이터를 표시할 수 없습니다.

끝점을 구성하는 두 가지 옵션이 있습니다.

### 클라우드 관리자 UI 사용(기본값) {#cm-ui}

환경 세부 사항 페이지의 대화 상자를 사용하여 수행할 수 있습니다. 상거래 지원 프로그램에 대해 이 페이지를 볼 때 종단점이 현재 구성되지 않은 경우 단추가 표시됩니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui.png)

이 단추를 클릭하면 대화 상자가 열립니다.

![CM 상거래 끝점](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

끝점(단계 카탈로그 지원을 위한 인증 토큰 선택)이 설정되면 끝점이 세부 정보 페이지에 표시됩니다. 편집 아이콘을 클릭하면 필요한 경우 끝점을 수정할 수 있는 동일한 대화 상자가 열립니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Adobe I/O CLI {#adobe-cli} 사용

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Adobe I/O CLI를 통해 전자 상거래 솔루션과 AEM을 연결하려면 다음 단계를 수행합니다.

1. Cloud Manager 플러그인을 사용하여 Adobe I/O CLI 가져오기

   [Cloud Manager CLI 플러그인](https://github.com/adobe/aio-cli-plugin-cloudmanager)과 함께 [Adobe I/O CLI](https://github.com/adobe/aio-cli)를 다운로드, 설정 및 사용하는 방법에 대한 [Adobe Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)를 확인하십시오.

2. Cloud Service 프로그램으로 AEM에서 Adobe I/O CLI 인증

3. 클라우드 관리자에서 `COMMERCE_ENDPOINT` 변수 설정

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   자세한 내용은 [CLI docs](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)을 참조하십시오.

   상거래 GraphQL 끝점 URL은 상거래의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://demo.magentosite.cloud/graphql`.

4. 인증이 필요한 단계 카탈로그 기능 활성화(선택 사항)

   >[!NOTE]
   >
   >이 기능은 Adobe Commerce Enterprise 또는 Cloud Edition에서만 사용할 수 있습니다. 자세한 내용은 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)을 참조하십시오.

   클라우드 관리자에서 `COMMERCE_AUTH_HEADER` 비밀 변수 설정:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다.`aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

이제 Cloud Service으로 AEM Commerce를 사용할 준비가 되었으며 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## {#catalog} 스토어 및 카탈로그 구성

CIF Add-On 및 [CIF Core Components](https://github.com/adobe/aem-core-cif-components)는 서로 다른 상거래 스토어에 연결된 여러 AEM 사이트 구조(또는 스토어 보기 등)에서 사용할 수 있습니다. 기본적으로 CIF Add-on은 Adobe Commerce의 기본 저장소 및 카탈로그(Magento)에 연결하는 기본 구성으로 배포됩니다.

이 구성은 다음 단계에 따라 CIF Cloud Service 구성을 통해 프로젝트에 맞게 조정할 수 있습니다.

1. AEM에서 도구 -> Cloud Services -> CIF 구성으로 이동합니다.

2. 변경할 상거래 구성을 선택합니다.

3. 작업 표시줄을 통해 구성 속성 열기

![CIF Cloud Services 구성](/help/commerce-cloud/assets/cif-cloud-service-config.png)

다음 속성을 구성할 수 있습니다.

- GraphQL 클라이언트 - 상거래 백엔드 통신을 위해 구성된 GraphQL 클라이언트를 선택합니다. 일반적으로 이 값은 기본적으로 유지되어야 합니다.
- 스토어 보기 - (Magento) 스토어 보기 식별자입니다. 비어 있으면 기본 스토어 보기가 사용됩니다.
- GraphQL 프록시 경로 - AEM의 URL 경로 GraphQL 프록시를 사용하여 상거래 백엔드 GraphQL 끝점에 대한 요청을 프록시합니다.
   >[!NOTE]
   >
   > 대부분의 설정에서 기본값 `/api/graphql`은(는) 변경할 수 없습니다. 제공된 GraphQL 프록시를 사용하지 않는 고급 설정만 이 설정을 변경해야 합니다.
- 카탈로그 UID 지원 활성화 - 상거래 백엔드 GraphQL 호출에서 ID 대신 UID에 대한 지원을 활성화합니다.
   >[!NOTE]
   >
   > UID에 대한 지원이 Adobe 상거래(Magento) 2.4.2에 도입되었습니다. 상거래 백엔드가 버전 2.4.2 이상의 GraphQL 스키마를 지원하는 경우에만 이 기능을 활성화합니다.
- 카탈로그 루트 카테고리 식별자 - 저장소 카탈로그 루트의 식별자(UID 또는 ID)

위에 표시된 구성은 참조용입니다. 프로젝트는 고유한 구성을 제공해야 합니다.

다른 상거래 카탈로그와 결합된 여러 AEM 사이트 구조를 사용하는 보다 복잡한 설정을 사용하려면 [상거래 다중 스토어 설정](configuring/multi-store-setup.md) 자습서를 참조하십시오.

## 추가 리소스 {#additional-resources}

- [AEM 프로젝트 전형](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [상거래 다중 스토어 설정](configuring/multi-store-setup.md)
