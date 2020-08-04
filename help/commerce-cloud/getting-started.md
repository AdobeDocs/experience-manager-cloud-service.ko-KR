---
title: Cloud Service으로 AEM Commerce 시작하기
description: Cloud Service으로 AEM Commerce 시작하기
translation-type: tm+mt
source-git-commit: 1fcdfa60c134491c781906e4a757a3a10399bde1
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 4%

---


# Cloud Service으로 AEM Commerce 시작하기 {#start}

AEM Commerce를 Cloud Service으로 시작하려면 Experience Manager Cloud Service에 CIF(Commerce Integration Framework) 추가 기능이 제공되어야 합니다. CIF Add-on은 Cloud Service으로 [AEM Sites 위에 추가 모듈입니다](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## 온보딩 {#onboarding}

Cloud Service으로 AEM Commerce에 대한 온보딩은 두 단계로 이루어집니다.

1. AEM Commerce를 Cloud Service이 활성화되고 제공된 CIF Add-on으로 가져오기
2. Magento 환경과 Cloud Service으로 AEM Commerce 연결

첫 번째 단계는 Adobe에 의해 행해진다. IMS 조직, Magento 환경의 GraphQL 끝점 URL 등과 같은 정보를 제공해야 합니다. 를 프로비저닝 프로세스의 일부로 사용할 수 있습니다. 가격 및 프로비저닝에 대한 자세한 내용은 세일즈 담당자에게 문의하십시오.

CIF Add-On을 제공받으면 기존 Cloud Manager 프로그램에 적용됩니다. Cloud Manager 프로그램이 없는 경우 새로 만들어야 합니다. 자세한 내용은 프로그램 [설정을 참조하십시오](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

두 번째 단계는 Cloud Service 환경으로서 각 AEM에 대한 셀프 서비스입니다. CIF Add-On의 초기 프로비저닝 후에 수행해야 하는 추가 구성이 있습니다.

## Magento과 AEM Commerce 연결 {#magento}

CIF Add-on 및 [AEM CIF 핵심 구성 요소를 Magento 환경과](https://github.com/adobe/aem-core-cif-components) 연결하려면 Cloud Manager 환경 변수를 통해 Magento GraphQL 끝점 URL을 제공해야 합니다. 변수 이름은 입니다 `COMMERCE_ENDPOINT`. HTTPS를 통한 보안 연결을 구성해야 합니다.
각 AEM에 대해 서로 다른 Magento GraphQL 끝점 URL을 Cloud Service 환경으로 사용할 수 있습니다. 이렇게 하면 Magento 스테이징 시스템 및 AEM 프로덕션 환경을 갖춘 AEM 스테이징 환경을 Magento 프로덕션 시스템에 연결할 수 있습니다. Magento GraphQL 종단점은 공개적으로 사용할 수 있어야 하며 개인 VPN 또는 로컬 연결은 지원되지 않습니다.

AEM Commerce를 Magento과 연결하려면 다음 단계를 따르십시오.

1. Cloud Manager 플러그인을 사용하여 Adobe I/O CLI 가져오기

   Cloud Manager CLI 플러그인을 사용하여 [Adobe I/O CLI를](https://docs.adobe.com/content/help/ko-KR/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) 다운로드, 설정 및 사용하는 방법에 대한 [Adobe Cloud](https://github.com/adobe/aio-cli) Manager 설명서를 [확인하십시오](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. AEM에서 CLI를 Cloud Service 프로그램으로 인증

3. 클라우드 관리자에서 `COMMERCE_ENDPOINT` 변수 설정

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   자세한 내용은 [CLI 문서를](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) 참조하십시오.

   Magento GraphQL 끝점 URL은 Magento의 GraphQl 서비스를 가리키고 보안 HTTPS 연결을 사용해야 합니다. 예: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>다음 명령을 사용하여 모든 Cloud Manager 변수를 나열하여 다시 확인할 수 있습니다. `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!Note]
>
>또는 [클라우드 관리자 API를](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) 사용하여 클라우드 관리자 변수를 구성할 수도 있습니다.

이제 AEM Commerce를 Cloud Service으로 사용할 준비가 되었으며 Cloud Manager를 통해 프로젝트를 배포할 수 있습니다.

## 타사 상거래 통합 {#integrations}

타사 상거래 통합의 경우 AEM Commerce를 Cloud Service으로 연결하고 CIF 핵심 구성 요소를 상거래 시스템과 연결하려면 [API 매핑 레이어가](architecture/third-party.md) 필요합니다. 이 API 매핑 레이어는 일반적으로 Adobe I/O Runtime에 배포됩니다. 통합 및 Adobe I/O Runtime에 대한 액세스 권한은 세일즈 담당자에게 문의하십시오.
