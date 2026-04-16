---
title: Adobe Experience Manager as a Cloud Service에 대한 HIPAA 준비
description: HIPAA 규정에 대한 Experience Manager as a Cloud Service 지원 및 새 AEM as a Cloud Service 프로젝트를 구현할 때 준수하는 방법에 대해 알아봅니다.
feature: Compliance
role: Admin, Architect, Developer, Leader
source-git-commit: 49721ac71bc2bde10eb5f25db58ee1b07c8a82e5
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 6%

---

# Adobe Experience Manager as a Cloud Service에 대한 HIPAA 준비 {#hipaa-readiness-for-adobe-experience-manager-as-a-cloud-service}

>[!WARNING]
>
>이 문서의 콘텐츠는 법률적인 조언을 포함하지 않으며, 법률적인 조언을 대체하지 않습니다.
>
>HIPAA 규정에 대한 자세한 내용은 귀사의 법무 부서에 문의하십시오.

>[!NOTE]
>
>개인 정보 보호 문제에 대한 Adobe의 대응 및 Adobe 고객에게 의미하는 바에 대한 자세한 내용은 다음을 참조하십시오.
>
>* Adobe Trust Center의 [HIPAA 및 Adobe 제품 및 서비스](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html)
>* [Adobe 개인 정보 보호 센터](https://www.adobe.com/kr/privacy.html)

Adobe Experience Manager(AEM) as a Cloud Service의 경우 Adobe에서 HIPAA 준비 상태를 이해하는 데 도움이 되는 설명서를 제공하고 있습니다. 이러한 규정을 준수하는 데 도움이 될 수 있습니다.

## 건강 보험 이동성 및 책임에 관한 법률(HIPAA) {#health-insurance-portability-and-accountability-act-hipaa}

### 건강 보험 이동성 및 책임에 관한 법률(HIPAA) {#the-health-insurance-portability-and-accountability-act-hipaa}

HIPAA 개인 정보, 보안 및 위반 알림 규칙은 PHI(Protected Health Information)로 알려진 개인 식별 가능한 건강 정보에 대한 중요한 보호를 설정합니다.

HIPAA에서 적용 엔티티는 의료 공급자, 의료 계획 또는 의료 정보 교환소입니다. 비즈니스 연관자는 PHI에 대한 액세스를 포함하는 적용 엔티티에 서비스를 제공하는 엔티티입니다. HIPAA 개인 정보 보호 및 보안 규칙은 적용 기업이 비즈니스 관계자에게 적용 기업의 PHI의 개인 정보 보호 및 보안을 보호하도록 요구하는 비즈니스 관련 계약(BAA) 형식으로 서면 보증을 받도록 요구합니다.

### Adobe에 PHI 제공 {#providing-phi-to-adobe}

Adobe은 AEM as a Cloud Service의 [HIPAA 서비스 준비](#hipaa-readiness-of-services-in-aem-as-a-cloud-service) 아래에 나열된 HIPAA 준비 서비스에 대해 비즈니스 담당자 역할을 합니다.

PHI **을(를) 처리하기 위해 Adobe HIPAA 지원 서비스에 라이선스를 부여하는 고객은**&#x200B;올바른 라이선스와 Adobe에 서명된 BAA가 있어야 합니다.

>[!IMPORTANT]
>
>고객은 HIPAA 준비 서비스로 지정되지 않았거나 HIPAA 준비 서비스 사용에 대한 적절한 라이선스가 없는 Adobe 제품 및 서비스를 통해 PHI를 생성, 수신, 유지 관리 또는 전송할 수 없습니다.

### HIPAA 공유 책임 {#hipaa-shared-responsibilities}

Adobe HIPAA 지원 서비스는 공유 책임 보안 모델에 의존하므로 고객과 Adobe은 PHI의 보안 유지에 대한 뚜렷한 책임을 져야 합니다. 이 공유 보안 모델에 따라 Adobe은 고객이 HIPAA와 일관되게 HIPAA 준비 서비스를 사용하고 구성하도록 의존합니다.

HIPAA 지원 서비스를 위한 Adobe BAA 실행에 대한 자세한 내용은 Adobe 영업 담당자 또는 고객 성공 관리자에게 문의하십시오.

>[!IMPORTANT]
>
>**면책조항**:
>
>고객은 Adobe HIPAA 지원 서비스를 사용하고 Adobe HIPAA 지원 서비스가 규정 준수 요구 사항을 충족하도록 할 책임이 있습니다.

자세한 내용은 Adobe Trust Center에서 [HIPAA 및 Adobe 제품 및 서비스](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html)를 참조하십시오.

## HIPAA 용어 {#hipaa-terminology}

다음 표에서는 AEM 서비스가 HIPAA 사용에 대해 분류되는 방식을 설명합니다.

| HIPAA 준비 | 설명 |
| --- | --- |
| HIPAA 지원 | 적절하게 구성하고 BAA와 함께 사용할 때 PHI를 처리하도록 설계되었습니다. |
| HIPAA 지원 안 함 | PHI를 처리하도록 설계되지 않았으며 HIPAA 관련 사용 사례에서 사용해서는 안 됩니다. |

>[!NOTE]
>
>HIPAA 준비 분류는 각 서비스의 의도된 기능을 기반으로 하며 시간이 지남에 따라 변경될 수 있습니다.
>
>고객은 HIPAA 관련 배포를 계획할 때 가장 최신 설명서 및 적용 가능한 계약 조건을 참조해야 합니다.

## AEM as a Cloud Service의 HIPAA 서비스 준비 {#hipaa-readiness-of-services-in-aem-as-a-cloud-service}

다음 표에서는 HIPAA가 준비된 AEM 서비스 및 이와 함께 사용할 수 있는 서비스에 대해 설명합니다. [추가 요구 사항](#additional-requirements)에 설명된 대로 HIPAA 지원 서비스를 사용하려면 Extended Security for Healthcare를 구입해야 합니다.

| 제품/기능 | 서비스 | HIPAA 준비 |
| --- | --- | --- |
| AEM Sites | AEM Sites, AEM Publish, Edge Delivery Services | HIPAA 지원 |
| AEM Sites | 범용 편집기 | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |
| AEM Sites Optimizer | Sites Optimizer | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |
| AEM Assets | AEM Assets | HIPAA 지원 |
| AEM Assets | Content Hub | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |
| AEM Assets | Brand Portal | HIPAA 지원 안 함 |
| AEM Assets | Dynamic Media OpenAPI | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |
| AEM Assets | Dynamic Media Scene 7 | HIPAA 지원 안 함 |
| AEM Forms | AEM Forms, Authentication Facade Service, PDF 유틸리티 서비스 | HIPAA 지원 |
| AEM CIF | Commerce integration framework | HIPAA 지원 안 함 |
| AEM Cloud Manager | AEM Cloud Manager, Release Orchestrator, 릴리스 전환, 릴리스 검사기 | HIPAA 지원 |
| AEM Cloud Manager | 소프트웨어 배포 | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |
|   |   |   |
| AEM Guides  | AEM Guides  | HIPAA 지원 안 함 |
|   |   |   |
| LLM Optimizer | LLM Optimizer | PHI가 도입되지 않은 경우 HIPAA 지원<br>[1]을 확장 보안 프로그램에 추가할 수 없습니다. |

>[!NOTE]
>
>[1]
>
>확장 보안 프로그램에 추가할 수 있는 것으로 표시되는 HIPAA 지원 서비스가 아닌 경우, 고객은 PHI가 이러한 서비스로 라우팅되거나 이러한 서비스에 저장되지 않았는지 확인해야 합니다.
>
>HIPAA 준비가 되지 않은 서비스에 PHI를 도입하면 규정 위반이 발생할 수 있습니다.

### 추가 요구 사항 {#additional-requirements}

[HIPAA 지원 서비스로 나열됨](#hipaa-readiness-of-services-in-aem-as-a-cloud-service)을 사용하려면 Extended Security for Healthcare를 구입해야 합니다.

Extended Security for Healthcare를 구입할 때 다음과 같은 요구 사항이 있습니다.

* 해당 프로그램에 대해 선택된 제품은 표에 나열된 대로 HIPAA가 준비된 제품이며,
* *각* 제품에 대해 Extended Security for Healthcare를 구입했습니다. 이를 통해 Cloud Manager 크레딧이 충분해지고
* Extended Security for Healthcare는 프로그램 생성 시 적용됩니다.

요구 사항이 충족되면 AEM 프로그램 생성 시 의료 서비스에 대한 확장 보안을 적용할 수 있습니다. 자세한 내용은 [설정](#setup)을 참조하십시오.

>[!NOTE]
>
>프로비저닝 및 가격에 대한 자세한 내용은 영업 담당자에게 문의하십시오.

## 환경 {#environments}

PHI는 이러한 환경에서 허용되지 않으므로 *HIPAA 지원*&#x200B;은(는) RDE(Rapid Development Environment), 개발 또는 스테이징 환경에는 적용되지 않습니다.

즉, 다음을 수행해야 합니다.

* 개발 및 테스트 목적으로 더미 데이터 사용
* 운영 환경의 PHI 프로세스만 가능

다음 표는 환경 유형을 HIPAA 준비로 지원할 수 있는 위치를 보여 줍니다.

| | RDE | 개발 | 단계  | Prod |
| --- | --- | --- | --- | --- |
| 환경 유형  | 아니요  | 아니요  | 아니요  | 예  |

## 설정 {#setup}

[프로덕션 프로그램을 만듭니다](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md). [보안 탭에서 HIPAA 보호를 활성화할 수 있습니다](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security).