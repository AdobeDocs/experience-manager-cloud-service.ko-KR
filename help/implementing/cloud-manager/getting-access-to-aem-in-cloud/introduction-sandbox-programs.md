---
title: '샌드박스 프로그램 소개 '
description: 샌드박스 프로그램 소개
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: 1892900ea3f365e1b5f7d31ffae64d45256d2a3a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 샌드박스 프로그램 소개 {#sandbox-programs}

## 소개 {#introduction}

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 프로그램 중 하나이며 다른 프로그램은 프로덕션 프로그램입니다.

샌드박스는 일반적으로 교육, 실행 데모, 지원 또는 개념 증명(POC)의 목적을 위해 만들어집니다. 그들은 실생활에 대한 여행을 하기 위한 것이 아니다. 이 콘텐츠는 [AEM as a Cloud Service 약정](https://www.adobe.com/legal/service-commitments.html).

샌드박스에서 생성된 환경은 자동 크기 조절을 위해 구성되지 않습니다. 따라서 이러한 환경은 성능 또는 로드 테스트에 적합하지 않습니다.

샌드박스 프로그램에는 다음이 포함됩니다 [!DNL Sites] 및 [!DNL Assets] 및 는 Git 리포지토리, 개발 환경 및 비프로덕션 파이프라인으로 자동 채워집니다.  Git 리포지토리는 AEM Project 원형 기반의 샘플 프로젝트로 채워집니다.

>[!IMPORTANT]
>샌드박스 프로그램에는 개발 환경이 하나만 있습니다.

>[!NOTE]
>사용자 지정 허용 목록 및 IP 도메인은 샌드박스 프로그램에서 사용할 수 없습니다.

을(를) 참조하십시오. [프로그램 및 프로그램 유형 이해](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/understand-program-types.html?lang=en) 프로그램 유형에 대해 자세히 알아보십시오 .

### 샌드박스 프로그램 속성 {#attributes-sandbox}

샌드박스 프로그램에는 다음 속성이 있습니다.

1. **프로그램 만들기:** 샌드박스 프로그램 만들기에 자동 기능이 포함되어 있습니다.
   * 샘플 코드 및 컨텐츠로 프로젝트 설정
   * 개발 환경 생성
   * 개발 환경에 비프로덕션 파이프라인 생성(개발 환경에 마스터 분기 배포)

1. **솔루션:** 샌드박스 프로그램에는 AEM이 포함됩니다 [!DNL Sites] 및 [!DNL Assets].

1. **AEM 업데이트:** AEM 업데이트는 샌드박스 프로그램의 환경에 수동으로 적용할 수 있으며 자동으로 푸시되지 않습니다.
을(를) 참조하십시오. [샌드박스 환경에 대한 AEM 업데이트](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox) 자세한 내용

1. **최대 절전 모드:** 샌드박스 프로그램의 환경은 특정 기간 동안 활동이 감지되지 않으면 자동으로 최대 절전 모드로 전환됩니다. 샌드박스는 8시간 동안 활동하지 않으면 최대 절전 모드로 전환되고 그 이후에는 최대 절전 모드 해제 상태로 전환될 수 있습니다. 최대 절전 모드 환경을 수동으로 해제할 수 있습니다.
을(를) 참조하십시오. [최대 절전 모드 및 최대 절전 모드 해제 샌드박스 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md) 자세한 내용

1. **삭제**: 샌드박스는 연속적인 최대 절전 모드 상태에서 6개월 후 삭제되며 그 후 다시 생성할 수 있습니다.
