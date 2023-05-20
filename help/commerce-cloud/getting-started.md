---
title: AEM Commerce 시작하기 as a Cloud Service
description: 상거래 지원 AEM 프로젝트를 실행 중인 AEM as a Cloud Service 환경에 배포하는 방법에 대해 알아봅니다. Adobe Cloud Manager 및 CI/CD 파이프라인의 기능을 사용하여 실행 환경에 대한 Venia 참조 스토어를 구축합니다.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: aa7b9daba4242965baf20a77af356952cd7bc279
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 3%

---

# AEM Commerce 시작하기 as a Cloud Service {#start}

AEM Commerce를 as a Cloud Service으로 시작하려면 Commerce Integration Framework(CIF) 추가 기능으로 Experience Manager Cloud Service을 프로비저닝해야 합니다. CIF 추가 기능은 맨 위에 있는 추가 모듈입니다. [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/home.html).

## 온보딩 {#onboarding}

AEM Commerce as a Cloud Service에 대한 온보딩은 두 단계로 구성됩니다.

1. AEM Commerce as a Cloud Service 활성화 및 CIF 추가 기능 프로비저닝
2. AEM Commerce를 상거래 솔루션과 as a Cloud Service 연결

첫 번째 온보딩 단계는 Adobe이 수행합니다. 가격 책정 및 프로비저닝에 대한 자세한 내용은 영업 담당자에게 문의해야 합니다.

CIF 추가 기능을 제공받으면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 새 프로그램을 만들어야 합니다. 자세한 내용은 다음을 참조하십시오. [프로그램 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

두 번째 단계는 각 AEM as a Cloud Service 환경에 대한 셀프서비스입니다. CIF 추가 기능을 처음 프로비저닝한 후 수행해야 하는 몇 가지 추가 구성이 있습니다.

## 상거래 솔루션과 AEM 연결 {#solution}

CIF 추가 기능 및 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components) 상거래 솔루션을 사용하려면 Cloud Manager 환경 변수를 통해 GraphQL 엔드포인트 URL을 제공해야 합니다. 변수 이름은 입니다. `COMMERCE_ENDPOINT`. HTTPS를 통한 보안 연결을 구성해야 합니다.

이 환경 변수는 다음 두 위치에서 사용됩니다.

- GraphQL은 AEM CIF 핵심 구성 요소 및 고객 프로젝트 구성 요소에서 사용하는 일부 공통 공유 가능한 GraphQl 클라이언트를 통해 AEM에서 상거래 백엔드로 호출을 수행합니다.
- 변수가 설정된 각 AEM 환경에서 GraphQL 프록시 URL을 설정합니다 `/api/graphql`. AEM commerce 작성 도구(CIF 추가 기능) 및 CIF 클라이언트측 구성 요소에서 사용됩니다.

각 AEM as a Cloud Service 환경에 대해 다른 GraphQL 엔드포인트 URL을 사용할 수 있습니다. 이 방법으로 프로젝트는 AEM 스테이징 환경을 상거래 스테이징 시스템 및 AEM 프로덕션 환경과 상거래 프로덕션 시스템을 연결할 수 있습니다. GraphQL 끝점을 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결이 지원되지 않습니다. 선택적으로, 인증이 필요한 추가 CIF 기능을 사용하기 위해 인증 헤더가 제공될 수 있다.

선택 사항으로 Adobe Commerce Enterprise/Cloud에만 CIF 추가 기능이 추가되어 AEM 작성자를 위한 준비된 카탈로그 데이터 사용을 지원합니다. 인증 헤더를 구성하는 데 필요합니다. 이 헤더는 보안상의 이유로 AEM 작성자 인스턴스에서만 사용할 수 있습니다. AEM 게시 인스턴스는 준비된 데이터를 표시할 수 없습니다.

끝점을 구성하는 두 가지 옵션이 있습니다.

### Cloud Manager UI를 통해(기본값) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

이 작업은 환경 세부 정보 페이지의 대화 상자를 사용하여 수행할 수 있습니다. 상거래 지원 프로그램에 대한 이 페이지를 볼 때 엔드포인트가 현재 구성되지 않은 경우 버튼이 표시됩니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui.png)

이 버튼을 클릭하면 대화 상자가 열립니다.

![CM Commerce 끝점](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

엔드포인트와 선택적으로 준비된 카탈로그 지원에 대한 인증 헤더가 설정되면 엔드포인트가 세부 정보 페이지에 표시됩니다. 편집 아이콘을 클릭하면 필요한 경우 끝점을 수정할 수 있는 동일한 대화 상자가 열립니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Adobe I/O CLI를 통해  {#adobe-cli}

Adobe I/O CLI를 통해 AEM을 상거래 솔루션에 연결하려면 다음 단계를 수행하십시오.

1. Cloud Manager 플러그인으로 Adobe I/O CLI 가져오기

   다음 확인: [Adobe Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) 다운로드, 설정 및 사용 방법: [ADOBE I/O CLI](https://github.com/adobe/aio-cli) (으)로 [Cloud Manager CLI 플러그인](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. as a Cloud Service 프로그램으로 Adobe I/O AEM CLI 인증

3. 설정 `COMMERCE_ENDPOINT` Cloud Manager의 변수

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   다음을 참조하십시오 [CLI 문서](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) 을 참조하십시오.

   commerce GraphQL 끝점 URL은 commerce의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://<yourcommercesystem>/graphql`.

4. 인증이 필요한 준비된 카탈로그 기능 활성화(선택 사항)

   >[!NOTE]
   >
   >이 기능은 Adobe Commerce Enterprise 또는 Cloud Edition에서만 사용할 수 있습니다. 다음을 참조하십시오 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens) 을 참조하십시오.

   설정 `COMMERCE_AUTH_HEADER` cloud Manager의 보안 변수:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다. `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

이를 통해 AEM Commerce를 as a Cloud Service으로 사용할 준비가 되었으며 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## 저장소 및 카탈로그 구성 {#catalog}

CIF 추가 기능 및 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components) 여러 상거래 저장소(또는 저장소 보기 등)에 연결된 여러 AEM 사이트 구조에서 사용할 수 있습니다.기본적으로 CIF 추가 기능은 Adobe Commerce의 기본 저장소 및 카탈로그에 연결하는 기본 구성으로 배포됩니다.

다음 단계에 따라 CIF Cloud Service 구성을 통해 프로젝트에 대해 이 구성을 조정할 수 있습니다.

1. AEM에서 도구 -> Cloud Services -> CIF 구성으로 이동합니다.

2. 변경할 상거래 구성 선택

3. 작업 표시줄을 통해 구성 속성 열기

![CIF Cloud Services 구성](/help/commerce-cloud/assets/cif-cloud-service-config.png)

다음 속성을 구성할 수 있습니다.

- GraphQL 클라이언트 - commerce 백엔드 통신용으로 구성된 GraphQL 클라이언트를 선택합니다. 이 옵션은 일반적으로 기본값으로 유지되어야 합니다.
- 스토어 뷰 - 스토어 뷰 식별자. 비어 있는 경우 기본 스토어 보기가 사용됩니다.
- GraphQL 프록시 경로 - AEM의 GraphQL 프록시가 상거래 백엔드 GraphQL 엔드포인트에 대한 요청을 프록시하는 데 사용하는 URL 경로.
   >[!NOTE]
   >
   > 대부분의 설정에서 기본값 `/api/graphql` 은(는) 변경할 수 없습니다. 제공된 GraphQL 프록시를 사용하지 않는 고급 설정만 이 설정을 변경해야 합니다.
- 카탈로그 UID 지원 활성화 - 상거래 백엔드 GraphQL 호출에서 ID 대신 UID를 지원합니다.
   >[!NOTE]
   >
   > UID에 대한 지원은 Adobe Commerce 2.4.2에서 도입되었습니다. 상거래 백엔드가 버전 2.4.2 이상의 GraphQL 스키마를 지원하는 경우에만 활성화하십시오.
- 카탈로그 루트 범주 식별자 - 스토어 카탈로그 루트의 식별자(UID 또는 ID)
   >[!CAUTION]
   >
   > CIF 코어 구성 요소 버전 2.0.0부터 `id` 을(를) 제거하고 로 대체함 `uid`. 프로젝트에서 CIF 코어 구성 요소 버전 2.0.0을 사용하는 경우 카탈로그 UID 지원을 활성화하고 유효한 범주 UID를 &quot;카탈로그 루트 범주 식별자&quot;로 사용해야 합니다.

위에 표시된 구성은 참조용입니다. 프로젝트는 자체 구성을 제공해야 합니다.

서로 다른 상거래 카탈로그와 결합된 여러 AEM 사이트 구조를 사용하는 더 복잡한 설정에 대해서는 다음을 참조하십시오. [Commerce 다중 스토어 설정](configuring/multi-store-setup.md) 튜토리얼.

## 추가 리소스 {#additional-resources}

- [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
- [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce 다중 스토어 설정](configuring/multi-store-setup.md)
- [여러 상거래 시스템 설정](configuring/multiple-commerce-systems-setup.md)

