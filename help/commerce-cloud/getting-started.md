---
title: Cloud Service으로 AEM Commerce 시작하기
description: 상거래 기반의 AEM 프로젝트를 Cloud 서비스 환경으로 실행 중인 AEM에 배포하는 방법에 대해 학습합니다. Adobe Cloud Manager와 CI/CD 파이프라인의 기능을 사용하여 Venia 참조 스토어를 실행 중인 환경에 구축할 수 있습니다.
topics: Commerce
feature: Cloud Manager, Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: 05242f0ca4168e220a4b83436da4daa0013edfaf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Cloud Service {#start}으로 AEM Commerce 시작하기

Cloud Service으로 AEM Commerce를 시작하려면 Experience Manager Cloud Service에 CEF(Commerce Integration Framework) 추가 기능이 제공되어야 합니다. CIF Add-on은 Cloud Service](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/sites/home.html)으로 [AEM Sites 위에 있는 추가 모듈입니다.

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## 온보딩 {#onboarding}

Cloud Service으로 AEM Commerce에 대한 온보딩은 2단계 프로세스입니다.

1. AEM Commerce를 Cloud Service이 활성화되고 제공된 CIF Add-On으로 사용
2. Magento 환경에 Cloud Service으로 AEM Commerce 연결

첫 번째 온보딩 단계는 Adobe에 의해 행해진다. 가격 및 프로비저닝에 대한 자세한 내용은 해당 세일즈 담당자에게 문의해야 합니다.

CIF Add-On을 제공받으면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 새로 만들어야 합니다. 자세한 내용은 [프로그램 설정](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html)을 참조하십시오.

두 번째 단계는 Cloud Service 환경으로서 각 AEM에 대한 셀프 서비스입니다. CIF Add-On의 초기 프로비저닝 후 수행해야 하는 추가 구성이 있습니다.

## Magento {#magento}에 AEM Commerce 연결

CIF Add-on 및 [AEM CIF 핵심 구성 요소](https://github.com/adobe/aem-core-cif-components)를 Magento 환경에 연결하려면 Cloud Manager 환경 변수를 통해 Magento GraphQL 끝점 URL을 제공해야 합니다. 변수 이름은 `COMMERCE_ENDPOINT`입니다. HTTPS를 통한 보안 연결을 구성해야 합니다.
서로 다른 Magento GraphQL 끝점 URL은 Cloud Service 환경으로 각 AEM에 사용할 수 있습니다. 이렇게 하면 프로젝트가 Magento 스테이징 시스템 및 AEM 프로덕션 환경을 AEM 스테이징 환경에서 Magento 프로덕션 시스템에 연결할 수 있습니다. Magento GraphQL 끝점은 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결은 지원되지 않습니다.

AEM Commerce를 Magento과 연결하려면 다음 단계를 따르십시오.

1. Cloud Manager 플러그인을 사용하여 Adobe I/O CLI 가져오기

   [Cloud Manager CLI 플러그인](https://github.com/adobe/aio-cli-plugin-cloudmanager)과 함께 [Adobe I/O CLI](https://github.com/adobe/aio-cli)을 다운로드, 설정 및 사용하는 방법에 대한 [Adobe Cloud Manager 설명서](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)를 확인하십시오.

2. Cloud Service 프로그램으로 AEM을 사용하여 CLI 인증

3. 클라우드 관리자에서 `COMMERCE_ENDPOINT` 변수 설정

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   자세한 내용은 [CLI docs](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid)을 참조하십시오.

   Magento GraphQL 끝점 URL은 Magento의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다.`aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>또는 [클라우드 관리자 API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)를 사용하여 클라우드 관리자 변수를 구성할 수도 있습니다.

이제 Cloud Service으로 AEM Commerce를 사용할 준비가 되었으며 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## 단계 카탈로그 기능 사용(선택 사항) {#staging}

>[!NOTE]
>
>이 기능은 Magento Enterprise Edition 또는 Magento Cloud에서만 사용할 수 있습니다.

1. Magento에 로그인하고 통합 토큰을 만듭니다. 자세한 내용은 [토큰 기반 인증](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)을 참조하십시오. 통합 토큰에 *만 `Content -> Staging` 리소스에 대한* 액세스 권한이 있는지 확인합니다. `Access Token` 값을 복사합니다.

1. 클라우드 관리자에서 `COMMERCE_AUTH_HEADER` 비밀 변수 설정:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization Bearer: <Access Token>"
   ```

   Cloud Manager용 Adobe I/O CLI를 구성하는 방법은 [Magento](#magento)에 AEM Commerce 연결을 참조하십시오.

## 타사 상거래 통합 {#integrations}

제3자 상거래 통합의 경우, AEM 상거래를 Cloud Service으로 연결하고 CIF 핵심 구성 요소를 상거래 시스템과 연결하려면 [API 매핑 레이어](architecture/third-party.md)가 필요합니다. 이 API 매핑 레이어는 일반적으로 Adobe I/O Runtime에 배포됩니다. 사용 가능한 통합 기능과 Adobe I/O Runtime에 대한 액세스 권한은 판매 담당자에게 문의하십시오.
