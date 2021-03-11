---
title: '샌드박스 프로그램 소개 '
description: '샌드박스 프로그램 소개 '
translation-type: tm+mt
source-git-commit: d98e3ba930690627bfbe9b90ce5cb93328c30503
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# 샌드박스 프로그램 소개 {#sandbox-programs}

## 소개 {#introduction}

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 유형의 프로그램 중 하나이며 다른 프로그램은 프로덕션 프로그램입니다.

샌드박스는 일반적으로 교육, 실행 데모, 지원 또는 개념 증명(POC)의 목적을 위해 만들어집니다.그들은 라이브 교통을 이용하려고 한 것이 아니다. 이러한 지표는 Cloud Service 약정](https://www.adobe.com/legal/service-commitments.html)으로서 [AEM의 적용을 받지 않습니다.

샌드박스에서 만들어진 환경은 자동 크기 조절을 위해 구성되지 않습니다. 따라서 이러한 환경은 성능이나 로드 테스트에 적합하지 않습니다.

샌드박스 프로그램에는 사이트 및 에셋이 포함되며 Git 리포지토리, 개발 환경 및 비프로덕션 파이프라인으로 자동 채워집니다.  Git 리포지토리는 AEM 프로젝트 원형을 기반으로 샘플 프로젝트로 채워집니다.

프로그램 유형에 대한 자세한 내용은 [프로그램 및 프로그램 유형 이해](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md)를 참조하십시오.

### 샌드박스 프로그램 {#attributes-sandbox} 속성

샌드박스 프로그램에는 다음 속성이 있습니다.

1. **프로그램 생성:** 샌드박스 프로그램 생성에는 자동이 포함됩니다.
   * 샘플 코드 및 컨텐츠로 프로젝트 설정
   * 개발 환경 조성
   * 개발 환경에 배포되는 비프로덕션 파이프라인 제작(개발 환경에 배포하는 마스터 지점)

1. **솔루션:** 샌드박스 프로그램에는 AEM Sites 및 에셋이 포함됩니다.

1. **AEM 업데이트:** AEM 업데이트는 샌드박스 프로그램의 환경에 수동으로 적용할 수 있으며 자동으로 푸시되지 않습니다.
자세한 내용은 [AEM 샌드박스 환경의 업데이트](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox)를 참조하십시오.

1. **최대 절전 모드:** 일정 기간 동안 활동이 감지되지 않으면 샌드박스 프로그램의 환경이 자동으로 동면됩니다. 최대 절전 모드 환경에서는 수동으로 동면되는 상태를 해제할 수 있습니다.
자세한 내용은 [최대 절전 모드 해제 및 최대 절전 모드 해제 환경](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md)을 참조하십시오.