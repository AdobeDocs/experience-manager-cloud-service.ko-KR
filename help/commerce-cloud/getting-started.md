---
title: Cloud Service으로 AEM Commerce 시작하기
description: 실행 중인 AEM as a Cloud Service 환경에 상거래 지원 AEM 프로젝트를 배포하는 방법을 알아봅니다. Adobe Cloud Manager 및 CI/CD 파이프라인의 기능을 사용하여 Venia 참조 저장소를 실행 환경에 구축할 수 있습니다.
topics: Commerce
feature: Cloud Manager, Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 3%

---

# Cloud Service으로 AEM Commerce 시작하기 {#start}

Cloud Service으로 AEM Commerce를 시작하려면 Experience Manager Cloud Service에 CIF(Commerce Integration Framework) 추가 기능이 제공되어야 합니다. CIF 추가 기능은 [AEM Sites의 Cloud Service](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/sites/home.html)에 있는 추가 모듈입니다.

## 온보딩 {#onboarding}

AEM Commerce as a Cloud Service에 대한 온보딩은 두 단계로 진행되는 프로세스입니다.

1. AEM Commerce를 Cloud Service으로 사용하고 CIF 추가 기능이 프로비저닝된 상태로 가져오기
2. 전자 상거래 솔루션과 Cloud Service으로 AEM Commerce 연결

첫 번째 온보딩 단계는 Adobe에 의해 수행됩니다. 가격 및 프로비저닝에 대한 자세한 내용은 영업 담당자에게 문의해야 합니다.

CIF 추가 기능이 제공되면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 새 프로그램을 만들어야 합니다. 자세한 내용은 [프로그램 설정](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html)을 참조하십시오.

두 번째 단계는 각 AEM as a Cloud Service 환경에 대한 셀프 서비스입니다. CIF 추가 기능의 초기 프로비저닝 후에 수행해야 하는 몇 가지 추가 구성이 있습니다.

## 전자 상거래 솔루션과 AEM 연결 {#magento}

CIF 추가 기능 및 [AEM CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components)를 상거래 솔루션과 연결하려면 Cloud Manager 환경 변수를 통해 GraphQL 엔드포인트 URL을 제공해야 합니다. 변수 이름은 `COMMERCE_ENDPOINT`입니다. HTTPS를 통한 보안 연결을 구성해야 합니다.

이 환경 변수는 다음 두 위치에서 사용됩니다.

- GraphQL은 AEM CIF 코어 구성 요소 및 고객 프로젝트 구성 요소에서 사용되는 몇 가지 일반적인 공유 가능한 GraphQl 클라이언트를 통해 AEM에서 상거래 백엔드로 호출합니다.
- 이 변수를 `/api/graphql`에서 사용할 수 있도록 설정된 각 AEM 환경에서 GraphQL 프록시 URL을 설정합니다. AEM 커머스 작성 도구(CIF 추가 기능) 및 CIF 클라이언트측 구성 요소에서 사용됩니다.

다른 GraphQL 엔드포인트 URL은 각 AEM에 Cloud Service 환경으로 사용할 수 있습니다. 이렇게 하면 프로젝트가 전자 상거래 스테이징 시스템 및 AEM 프로덕션 환경과 AEM 스테이징 환경을 상거래 프로덕션 시스템에 연결할 수 있습니다. GraphQL 끝점은 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결은 지원되지 않습니다. 원할 경우, 인증을 필요로 하는 추가 CIF 기능을 사용하기 위해 인증 헤더를 제공할 수 있습니다.

CIF 추가 기능은 AEM 작성자를 위해 준비된 카탈로그 데이터의 사용을 지원합니다(선택 사항 및 Adobe Commerce Enterprise/Cloud에만 해당). 인증 토큰을 구성해야 합니다. 구성된 인증 토큰은 보안상의 이유로 AEM 작성자 인스턴스에서만 사용할 수 있으며, AEM 게시 인스턴스에서는 스테이징된 데이터를 표시할 수 없습니다.

끝점을 구성하는 두 가지 옵션이 있습니다.

### Cloud Manager UI(기본값) {#cm-ui}를 통해

이 작업은 환경 세부 사항 페이지의 대화 상자를 사용하여 수행할 수 있습니다. 상거래 활성화 프로그램에 대한 이 페이지를 볼 때 종단점이 현재 구성되지 않은 경우 단추가 표시됩니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui.png)

이 단추를 클릭하면 대화 상자가 열립니다.

![CM 상거래 끝점](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

엔드포인트(선택적으로 스테이지된 카탈로그 지원을 위한 인증 토큰)가 설정되면 엔드포인트가 세부 정보 페이지에 표시됩니다. 편집 아이콘을 클릭하면 필요한 경우 엔드포인트를 수정할 수 있는 동일한 대화 상자가 열립니다.

![CM 환경 정보](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Adobe I/O CLI {#adobe-cli} 사용

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Adobe I/O CLI를 통해 AEM과 상거래 솔루션을 연결하려면 다음 단계를 따르십시오.

1. Cloud Manager 플러그인을 사용하여 Adobe I/O CLI 가져오기

   [Cloud Manager CLI 플러그인](https://github.com/adobe/aio-cli-plugin-cloudmanager)과 함께 [Adobe I/O CLI](https://github.com/adobe/aio-cli)를 다운로드, 설정 및 사용하는 방법에 대해서는 [Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)를 확인하십시오.

2. AEM as a Cloud Service 프로그램으로 Adobe I/O CLI 인증

3. Cloud Manager에서 `COMMERCE_ENDPOINT` 변수 설정

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   자세한 내용은 [CLI 문서](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)를 참조하십시오.

   상거래 GraphQL 끝점 URL은 상거래 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://demo.magentosite.cloud/graphql`.

4. 인증이 필요한 준비된 카탈로그 기능 활성화(선택 사항)

   >[!NOTE]
   >
   >이 기능은 Adobe Commerce Enterprise 또는 Cloud Edition에서만 사용할 수 있습니다. 자세한 내용은 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)을 참조하십시오.

   Cloud Manager에서 `COMMERCE_AUTH_HEADER` 암호 변수를 설정합니다.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다.`aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

이를 통해 AEM Commerce를 Cloud Service으로 사용하고 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## 저장소 및 카탈로그 구성 {#catalog}

CIF 추가 기능 및 [CIF 코어 구성 요소](https://github.com/adobe/aem-core-cif-components)는 다른 상거래 저장소(또는 스토어 보기 등)에 연결된 여러 AEM 사이트 구조에서 사용할 수 있습니다. 기본적으로 CIF 추가 기능은 Adobe Commerce의 기본 스토어와 카탈로그(Magento)에 연결하는 기본 구성과 함께 배포됩니다.

이 구성은 다음 단계에 따라 CIF Cloud Service 구성을 통해 프로젝트에 대해 조정할 수 있습니다.

1. AEM에서 도구 -> Cloud Services -> CIF 구성으로 이동합니다.

2. 변경할 상거래 구성을 선택합니다

3. 작업 표시줄을 통해 구성 속성을 엽니다

![CIF Cloud Services 구성](/help/commerce-cloud/assets/cif-cloud-service-config.png)

다음 속성을 구성할 수 있습니다.

- GraphQL 클라이언트 - 상거래 백엔드 통신을 위해 구성된 GraphQL 클라이언트를 선택합니다. 이 기능은 일반적으로 기본적으로 유지됩니다.
- 저장소 보기 - (Magento) 저장소 보기 식별자입니다. 비어 있으면 기본 저장소 보기가 사용됩니다.
- GraphQL 프록시 경로 - AEM의 URL 경로 GraphQL 프록시가 상거래 백엔드 GraphQL 끝점에 요청을 프록시할 때 사용합니다.
   >[!NOTE]
   >
   > 대부분의 설정에서 기본값 `/api/graphql`은 변경할 수 없습니다. 제공된 GraphQL 프록시를 사용하지 않는 고급 설정만 이 설정을 변경해야 합니다.
- 카탈로그 UID 지원 활성화 - 상거래 백엔드 GraphQL 호출에서 ID 대신 UID에 대한 지원을 활성화합니다.
   >[!NOTE]
   >
   > UID에 대한 지원이 Adobe Commerce(Magento) 2.4.2에서 도입되었습니다. 상거래 백엔드가 버전 2.4.2 이상의 GraphQL 스키마를 지원하는 경우에만 활성화하십시오.
- 카탈로그 루트 카테고리 식별자 - 저장소 카탈로그 루트의 식별자(UID 또는 ID)입니다

위에 표시된 구성은 참조용입니다. 프로젝트는 자체 구성을 제공해야 합니다.

다른 전자 상거래 카탈로그와 결합된 여러 AEM 사이트 구조를 사용하는 보다 복잡한 설정을 알려면 [Commerce Multi-Store Setup](configuring/multi-store-setup.md) 자습서를 참조하십시오.

## 추가 리소스 {#additional-resources}

- [AEM 프로젝트 전형](https://github.com/adobe/aem-project-archetype)
- [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
- [상거래 다중 스토어 설정](configuring/multi-store-setup.md)
