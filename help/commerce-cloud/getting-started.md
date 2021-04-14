---
title: Cloud Service으로 AEM Commerce 시작하기
description: 상거래 기반의 AEM 프로젝트를 Cloud 서비스 환경으로 실행 중인 AEM에 배포하는 방법에 대해 학습합니다. Adobe Cloud Manager와 CI/CD 파이프라인의 기능을 사용하여 Venia 참조 스토어를 실행 중인 환경에 구축할 수 있습니다.
topics: Commerce
feature: Cloud Manager, Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
translation-type: tm+mt
source-git-commit: e34592d24c8f6c17e6959db1d5c513feaf6381c8
workflow-type: tm+mt
source-wordcount: '766'
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
다른 GraphQL 끝점 URL은 Cloud Service 환경으로 각 AEM에 사용할 수 있습니다. 이렇게 프로젝트를 통해 AEM 스테이징 환경과 커머스 스테이징 시스템 및 AEM 프로덕션 환경을 커머스 프로덕션 시스템에 연결할 수 있습니다. GraphQL 끝점은 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결은 지원되지 않습니다. 인증이 필요한 추가 CIF 기능을 사용하기 위해 인증 헤더를 제공할 수도 있습니다.

끝점을 구성하는 두 가지 옵션이 있습니다.

### 1) Cloud Manager UI 사용(기본값)

환경 세부 사항 페이지의 대화 상자를 사용하여 수행할 수 있습니다. 상거래 지원 프로그램에 대해 이 페이지를 볼 때 종단점이 현재 구성되지 않은 경우 단추가 표시됩니다.

![친환경 배지 최종 구현](/help/commerce-cloud/assets/commerce-cmui.png)

이 단추를 클릭하면 대화 상자가 열립니다.

![친환경 배지 최종 구현](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

끝점(및 선택적으로 토큰)이 설정되면 끝점이 세부 정보 페이지에 표시됩니다. 편집 아이콘을 클릭하면 필요한 경우 끝점을 수정할 수 있는 동일한 대화 상자가 열립니다.

![친환경 배지 최종 구현](/help/commerce-cloud/assets/commerce-cmui-done.png)

### 2) Adobe I/O CLI를 통해

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Adobe I/O CLI를 통해 전자 상거래 솔루션과 AEM을 연결하려면 다음 단계를 수행합니다.

1. Cloud Manager 플러그인을 사용하여 Adobe I/O CLI 가져오기

   [Cloud Manager CLI 플러그인](https://github.com/adobe/aio-cli-plugin-cloudmanager)과 함께 [Adobe I/O CLI](https://github.com/adobe/aio-cli)을 다운로드, 설정 및 사용하는 방법에 대한 [Adobe Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)를 확인하십시오.

2. Cloud Service 프로그램으로 AEM에서 Adobe I/O CLI 인증

3. 클라우드 관리자에서 `COMMERCE_ENDPOINT` 변수 설정

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   자세한 내용은 [CLI docs](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)을 참조하십시오.

   상거래 GraphQL 끝점 URL은 상거래의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다.`aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

이제 Cloud Service으로 AEM Commerce를 사용할 준비가 되었으며 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## 인증이 필요한 기능 활성화(옵션) {#staging}

>[!NOTE]
>
>이 기능은 Magento Enterprise Edition 또는 Magento Cloud에서만 사용할 수 있습니다.

1. Magento에 로그인하고 통합 토큰을 만듭니다. 자세한 내용은 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)을 참조하십시오. 통합 토큰에 *만 `Content -> Staging` 리소스에 대한* 액세스 권한이 있는지 확인합니다. `Access Token` 값을 복사합니다.

1. 클라우드 관리자에서 `COMMERCE_AUTH_HEADER` 비밀 변수 설정:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

   Cloud Manager용 Adobe I/O CLI를 구성하는 방법은 [Magento](#magento)에 AEM Commerce 연결을 참조하십시오.

## 타사 상거래 통합 {#integrations}

제3자 상거래 통합의 경우, AEM 상거래를 Cloud Service으로 연결하고 CIF 핵심 구성 요소를 상거래 시스템과 연결하려면 [API 매핑 레이어](architecture/third-party.md)가 필요합니다. 이 API 매핑 레이어는 일반적으로 Adobe I/O Runtime에 배포됩니다. 사용 가능한 통합 기능과 Adobe I/O Runtime에 대한 액세스 권한은 판매 담당자에게 문의하십시오.
