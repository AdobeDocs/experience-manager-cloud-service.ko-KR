---
title: ''' [!DNL Adobe Workfront]''과(와) ''[!DNL Experience Manager Assets] 통합'
description: ' [!DNL Assets] 과(와) [!DNL Workfront] 간의 통합 소개'
role: Admin, Leader, Architect
feature: Workfront Integrations and Apps
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 3%

---

# [!DNL Adobe Experience Manager]을(를) [!DNL Cloud Service] [!DNL Assets](으)로 [!DNL Adobe Workfront]과(와) 통합 {#assets-integration-overview}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Workfront]은(는) 업무의 전체 라이프사이클을 한 곳에서 관리할 수 있도록 도와주는 작업 관리 애플리케이션입니다. [!DNL Workfront]과(와) [!DNL Adobe Experience Manager Assets] 간의 통합을 통해 조직은 작업과 디지털 에셋 관리를 본질적으로 연결하여 콘텐츠 속도와 마켓 출시 속도를 개선할 수 있습니다. Workfront에서 작업을 관리하는 맥락에서 사용자는 필요한 문서 및 이미지에 액세스할 수 있습니다.

Adobe 오퍼는 [통합 [!DNL Workfront] 및 [!DNL Adobe Experience Manager Assets] 기본적으로 Assets Essentials 및 Assets as a Cloud Service 지원](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html)입니다.

기본 Experience Manager 통합을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* Workfront 내에서 신속하게 통합을 설정합니다.

* Workfront과 Experience Manager 간에 연결된 폴더를 자동으로 만듭니다.

* 연결된 기존 에셋에 대한 메타데이터를 쉽게 동기화합니다.

* Workfront에서 프로젝트 메타데이터가 변경되면 자동으로 업데이트됩니다.

* 여러 Experience Manager Assets 저장소를 조직 ID의 한 Workfront 환경에 원활하게 연결하거나 여러 Workfront 환경을 한 Experience Manager Assets 저장소에 원활하게 연결할 수 있습니다.


## Adobe Workfront for Experience Manager 강화 커넥터 {#enhanced-connector-information}


2022년 6월 현재, Adobe은 Workfront과 Adobe Experience Manager Assets as a Cloud Service 기본 통합을 연결하기 위한 새로운 통합을 발표했습니다. 이 통합은 이 두 솔루션을 연결하는 데 필요한 방법이 되었습니다. Workfront과 새 AEM Assetsas a Cloud Service 를 연결하기 위한 향상된 커넥터(1.9.8 및 이후 버전)의 모든 향후 구현이 차단됩니다. 이 통합을 설정하는 방법에 대한 자세한 내용은 [Experience Manager Assets as a Cloud Service 통합 구성](workfront-connector-configure.md)을 참조하십시오.

>[!NOTE]
>
>Adobe은 Workfront for Experience Manager 강화 커넥터 및 Experience Manager 통합을 동시에 사용할 수 없습니다.

2022년 6월 이전 설치의 경우 [!DNL Adobe Workfront for Experience Manager enhanced connector]의 배포 및 구성에 대해 유의해야 할 사항은 다음과 같습니다.

* Adobe을 사용하려면 인증된 파트너 또는 [!DNL Adobe Professional Services]을(를) 통해서만 [!DNL Adobe Workfront for Experience Manager enhanced connector]을(를) 배포하고 구성해야 합니다. 인증 파트너 또는 [!DNL Adobe Professional Services] 없이 배포 및 구성된 경우 Adobe에서 지원하지 않습니다.
* Adobe은 이 커넥터를 중복 커넥터로 만드는 [!DNL Adobe Workfront] 및 [!DNL Adobe Experience Manager]에 대한 업데이트를 릴리스할 수 있습니다. 이러한 경우 고객은 이 커넥터를 사용하지 않도록 전환해야 할 수 있습니다.
* Adobe은 향상된 커넥터 버전 1.7.4 이상을 지원합니다. 이전 프리릴리스 및 사용자 지정 버전은 지원되지 않습니다. 향상된 커넥터 버전을 확인하려면 [향상된 커넥터 설치 지침](workfront-connector-install.md)의 5단계(a)를 참조하십시오.
* [Workfront for Experience Manager Assets 강화 커넥터에 대한 파트너 인증 시험](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html)을 참조하세요. 시험에 대한 자세한 내용은 [시험 가이드](https://express.adobe.com/page/Tc7Mq6zLbPFy8/)를 참조하세요.