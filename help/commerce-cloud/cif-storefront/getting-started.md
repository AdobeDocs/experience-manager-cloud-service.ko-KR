---
title: AEM Commerce as a Cloud Service 시작하기
description: Adobe Cloud Manager, CI/CD 파이프라인 및 Venia 참조 상점을 사용하여 Adobe Experience Manager(AEM) 상거래 프로젝트를 배포하는 방법에 대해 알아봅니다.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Experience Manager as a Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
role: Admin
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 1%

---


# AEM Commerce as a Cloud Service 시작하기 {#start}

Adobe Experience Manager(AEM) Commerce as a Cloud Service을 시작하려면 Experience Manager Cloud Service에 Commerce integration framework(CIF) 추가 기능을 프로비저닝해야 합니다. CIF 추가 기능은 [AEM Sites as a Cloud Service 위에 있는 추가 모듈입니다.](/help/sites-cloud/sites-cloud-changes.md)

>[!TIP]
>
>**Edge Delivery Services을 고려했습니까?**
>
>Edge Delivery Services은 상점 만들기를 위해 Adobe이 선호하는 솔루션입니다. 자세한 내용은 [소개 및 개요](/help/commerce-cloud/introduction.md) 문서를 참조하십시오.

## 온보딩 {#onboarding}

AEM Commerce as a Cloud Service에 대한 온보딩은 두 단계 프로세스입니다.

1. AEM Commerce as a Cloud Service 활성화 및 CIF 추가 기능 프로비저닝하기
1. AEM Commerce as a Cloud Service을 상거래 솔루션과 연결

첫 번째 온보딩 단계는 Adobe에서 수행합니다. 가격 책정 및 프로비저닝에 대한 자세한 내용은 영업 담당자에게 문의해야 합니다.

CIF 추가 기능을 제공받으면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 만들어야 합니다. 자세한 내용은 [프로그램 설정](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html?lang=ko)을 참조하세요.

두 번째 단계는 각 AEM as a Cloud Service 환경에 대한 셀프서비스입니다. CIF 추가 기능의 초기 프로비저닝 후에 수행해야 하는 몇 가지 추가 구성이 있습니다.

## Commerce 솔루션과 AEM 연결 {#solution}

CIF 추가 기능 및 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 상거래 솔루션과 연결하려면 Cloud Manager 환경 변수를 통해 GraphQL 끝점 URL을 제공해야 합니다. 변수 이름은 `COMMERCE_ENDPOINT`입니다. HTTPS를 통한 보안 연결을 구성해야 합니다.

이 환경 변수는 다음 두 위치에서 사용됩니다.

* GraphQL은 AEM CIF 핵심 구성 요소 및 고객 프로젝트 구성 요소에서 사용하는 몇 가지 일반적인 공유 가능한 GraphQl 클라이언트를 통해 AEM에서 상거래 백엔드로 호출을 수행합니다.
* 변수가 설정된 각 AEM 환경에서 `/api/graphql`에서 사용할 수 있도록 GraphQL 프록시 URL을 설정합니다. 이 URL은 AEM 상거래 작성 도구(CIF 추가 기능) 및 CIF 클라이언트측 구성 요소에서 사용됩니다.

각 AEM as a Cloud Service 환경에 대해 다른 GraphQL 엔드포인트 URL을 사용할 수 있습니다. 이 방법으로 프로젝트는 AEM 스테이징 환경을 상거래 스테이징 시스템 및 AEM 프로덕션 환경과 상거래 프로덕션 시스템을 연결할 수 있습니다. GraphQL 끝점을 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결이 지원되지 않습니다. 선택적으로, 인증이 필요한 추가 CIF 기능을 사용하도록 인증 헤더를 제공할 수 있습니다.

선택적으로, Adobe Commerce Enterprise/Cloud의 경우에만 CIF 추가 기능이 AEM 작성자를 위해 준비된 카탈로그 데이터의 사용을 지원합니다. 이 데이터를 사용하려면 인증 헤더를 구성해야 합니다. 이 헤더는 보안상의 이유로 AEM 작성자 인스턴스에서만 사용할 수 있습니다. AEM 게시 인스턴스는 준비된 데이터를 표시할 수 없습니다.

끝점을 구성하는 두 가지 옵션이 있습니다.

### Cloud Manager 사용자 인터페이스(기본값) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/343273?quality=12&learn=on&captions=kor)

이 구성은 환경 세부 정보 페이지의 대화 상자를 사용하여 수행할 수 있습니다. Commerce 지원 프로그램에 대해 이 페이지를 볼 때 엔드포인트가 현재 구성되지 않은 경우 버튼이 표시됩니다.

![CM 환경 정보](/help/commerce-cloud/cif-storefront/assets/commerce-cmui.png)

이 버튼을 클릭하면 대화 상자가 열립니다.

![CM Commerce 끝점](/help/commerce-cloud/cif-storefront/assets/commerce-cm-endpoint.png)

엔드포인트와 선택적으로 준비된 카탈로그 지원에 대한 인증 헤더가 설정되면 엔드포인트가 세부 정보 페이지에 표시됩니다. 필요한 경우 편집 아이콘을 클릭하여 끝점을 편집할 수 있는 동일한 대화 상자를 엽니다.

![CM 환경 정보](/help/commerce-cloud/cif-storefront/assets/commerce-cmui-done.png)

### Adobe I/O CLI를 통해  {#adobe-cli}

Adobe I/O CLI를 통해 AEM을 상거래 솔루션과 연결하려면 다음 단계를 수행하십시오.

1. Cloud Manager 플러그인으로 Adobe I/O CLI를 다운로드하십시오.

   * [Adobe CLI 플러그인과 함께 &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=ko)Adobe I/O CLI[를 다운로드, 설정 및 사용하는 방법은 &#x200B;](https://github.com/adobe/aio-cli)Cloud Manager Cloud Manager 설명서[를 참조하십시오.](https://github.com/adobe/aio-cli-plugin-cloudmanager)

1. AEM as a Cloud Service 프로그램을 사용하여 Adobe I/O CLI를 인증합니다.

1. Cloud Manager에서 `COMMERCE_ENDPOINT` 변수를 설정합니다.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   * 자세한 내용은 [CLI 문서](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)를 참조하십시오.

   * commerce GraphQL 끝점 URL은 commerce의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://<yourcommercesystem>/graphql`.

1. 인증이 필요한 스테이지 카탈로그 기능을 활성화합니다(선택 사항).

   >[!NOTE]
   >
   >이 기능은 Adobe Commerce Enterprise 또는 Cloud Edition에서만 사용할 수 있습니다. 자세한 내용은 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)을 참조하십시오.

   * Cloud Manager에서 `COMMERCE_AUTH_HEADER` 비밀 변수 설정:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다. `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

AEM Commerce as a Cloud Service을 사용할 준비가 되었으며 Cloud Manager을 통해 프로젝트를 배포할 수 있습니다.

## 저장소 및 카탈로그 구성 {#catalog}

CIF 추가 기능 및 [CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)는 서로 다른 상거래 상점(또는 스토어 보기 등)에 연결된 여러 AEM 사이트 구조에서 사용할 수 있습니다. 기본적으로 CIF 추가 기능은 Adobe Commerce의 기본 스토어 및 카탈로그에 연결하는 기본 구성으로 배포됩니다.

이 구성은 다음 단계에 따라 CIF Cloud Service 구성을 통해 프로젝트에 대해 조정할 수 있습니다.

1. AEM에서 도구 > 클라우드 서비스 > CIF 구성으로 이동합니다.

1. 변경할 상거래 구성을 선택합니다.

1. 작업 표시줄을 통해 구성 속성을 엽니다.

![CIF 클라우드 서비스 구성](/help/commerce-cloud/cif-storefront/assets/cif-cloud-service-config.png)

다음 속성을 구성할 수 있습니다.

* GraphQL 클라이언트 - commerce 백엔드 통신용으로 구성된 GraphQL 클라이언트를 선택합니다. 이 클라이언트는 일반적으로 기본 상태를 유지해야 합니다.
* 스토어 뷰 - 스토어 뷰 식별자. 비어 있는 경우 기본 스토어 보기가 사용됩니다.
* GraphQL 프록시 경로 - AEM의 GraphQL 프록시가 상거래 백엔드 GraphQL 엔드포인트에 대한 요청을 프록시하는 데 사용하는 URL 경로.
  >[!NOTE]
  >
  > 대부분의 설정에서 기본값 `/api/graphql`을(를) 변경할 수 없습니다. 제공된 GraphQL 프록시를 사용하지 않는 고급 설정만 이 설정을 변경해야 합니다.
* 카탈로그 UID 지원 활성화 - 상거래 백엔드 GraphQL 호출에서 ID 대신 UID에 대한 지원을 활성화합니다.
  >[!NOTE]
  >
  > UID에 대한 지원은 Adobe Commerce 2.4.2에서 도입되었습니다. 상거래 백엔드가 버전 2.4.2 이상의 GraphQL 스키마를 지원하는 경우에만 UID를 활성화합니다.
* 카탈로그 루트 범주 식별자 - 스토어 카탈로그 루트의 식별자(UID 또는 ID)
  >[!CAUTION]
  >
  > CIF 핵심 구성 요소 버전 2.0.0부터 `id`에 대한 지원이 제거되고 `uid`(으)로 대체되었습니다. 프로젝트에서 CIF 핵심 구성 요소 버전 2.0.0을 사용하는 경우 카탈로그 UID 지원을 활성화하고 유효한 범주 UID을 &quot;카탈로그 루트 범주 식별자&quot;로 사용해야 합니다.

위에 표시된 구성은 참조용입니다. 프로젝트는 자체 구성을 제공해야 합니다.

보다 복잡한 설정의 경우 여러 상거래 카탈로그와 결합된 여러 AEM 사이트 구조를 사용하는 방법은 [Commerce 다중 스토어 설정](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md) 자습서를 참조하십시오.

## 추가 리소스 {#additional-resources}

* [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
* [AEM Venia 참조 저장소](https://github.com/adobe/aem-cif-guides-venia)
* [Commerce 다중 스토어 설정](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md)
* [여러 Commerce 시스템 설정](/help/commerce-cloud/cif-storefront/configuring/multiple-commerce-systems-setup.md)
