---
title: ' [!DNL Adobe Creative Cloud]과(와) 통합하기 위한 우수 사례'
description: Experience Manager 배포를 Adobe Creative Cloud과 통합하여 에셋 전송 워크플로우를 간소화하고 효율성을 극대화할 수 있는 모범 사례
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b1586cd9d6b3e9da115bff802d840a72d1207e4a
workflow-type: tm+mt
source-wordcount: '3296'
ht-degree: 1%

---


# AEM 및 Creative Cloud 통합 우수 사례 {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager(AEM) 자산은 Adobe Creative Cloud과 통합하여 DAM 사용자가 크리에이티브 팀과 공동 작업을 할 수 있도록 하는 디지털 자산 관리(DAM) 솔루션으로 컨텐츠 제작 프로세스의 공동 작업을 간소화합니다.

Adobe Creative Cloud은 크리에이티브 팀에게 디지털 에셋 제작을 지원하는 솔루션과 서비스 에코시스템을 제공합니다. 여기에는 데스크탑 및 모바일 애플리케이션, 데스크탑 동기화 또는 웹 경험이 포함된 스토리지와 같은 클라우드 서비스, Adobe Stock과 같은 마켓플레이스가 포함됩니다.

사용 사례를 기반으로 데스크탑과 엔터프라이즈급 DAM 간의 통합을 선택하는 방법과 연계된 워크플로우에 대한 모범 사례를 살펴보십시오.

>[!NOTE]
>
>AEM에서 Creative Cloud으로 폴더 공유가 이제 더 이상 필요하지 않습니다. Adobe은 크리에이티브 사용자가 AEM에서 관리되는 에셋에 액세스할 수 있도록 Adobe 에셋 링크 또는 AEM 데스크탑 앱과 같은 새로운 기능을 권장합니다.

## 크리에이티브 전문가, 마케터 및 DAM 사용자의 공동 작업 필요 {#collaboration-need-of-creatives-marketers-and-dam-users}

| 요구 사항 | 사용 사례 | 포함된 서피스 |
|---|---|---|
| 데스크탑에서 크리에이티브 작업을 위한 경험 간소화 | 크리에이티브 전문가를 위한 DAM(AEM Assets)을 통해 에셋에 대한 액세스를 간소화할 수 있고 기본 에셋 제작 애플리케이션을 사용하는 데스크탑 사용자도 광범위하게 이용할 수 있습니다. 새로운 파일을 업로드하고 AEM에 변경 사항을 검색, 사용(열기), 편집 및 저장할 수 있는 간편하고 간단한 방법이 필요합니다. | Win 또는 Mac 데스크탑Creative Cloud 앱 |
| Adobe Stock에서 바로 사용할 수 있는 고품질의 에셋 제공 | 마케터는 자산 확보 및 검색을 지원함으로써 컨텐츠 제작 프로세스를 가속화할 수 있습니다. 크리에이티브 전문가는 승인된 자산을 크리에이티브 툴에서 바로 사용합니다. | AEM Assets;Adobe Stock 마켓플레이스메타데이터 필드 |
| 조직별 에셋 배포 및 공유 | 내부 부서/지역 지사와 외부 파트너, 배포업체 및 대리점은 상위 조직에서 공유한 승인된 자산을 사용합니다. 조직은 제작한 에셋을 보다 광범위하게 재사용할 수 있도록 안전하고 완벽하게 공유하려고 합니다. | 브랜드 포털, 자산 공유 공유물 |

## 공동 작업을 지원하기 위한 Adobe 제공{#adobe-offerings-to-support-the-collaboration-need}

| 고객의 가치 제안 | Adobe 제공 | 포함된 서피스 |
|---|---|---|
| 크리에이티브 사용자는 Creative Cloud 앱을 종료하지 않고도 AEM에서 에셋을 검색하고, 열어 사용하고, AEM에 변경 사항을 편집 및 업로드하고, AEM에 새 파일을 업로드합니다. | [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator 및 InDesign |
| 비즈니스 사용자는 간단하게 에셋 열기 및 사용, AEM에 대한 변경 사항 편집 및 업로드, 데스크탑 환경에서 AEM에 새 파일 업로드 등을 할 수 있습니다. 일반 통합을 사용하여 Adobe이 아닌 에셋 유형을 비롯한 모든 에셋 유형을 기본 데스크탑 애플리케이션에서 엽니다. | [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en) | Win 및 Mac 데스크탑 기반의 AEM 데스크탑 앱 |
| 마케터와 비즈니스 사용자는 AEM에서 Adobe Stock 에셋을 검색, 미리 보기, 라이선스 부여 및 저장하고 관리할 수 있습니다. 라이선스가 부여된 에셋과 저장된 에셋은 보다 효과적인 관리를 위해 특정 Adobe Stock 메타데이터를 제공합니다. | [Experience Manager 및 Adobe Stock 통합](aem-assets-adobe-stock.md) | AEM 웹 인터페이스 |

이 문서에서는 주로 협업의 첫 두 가지 측면을 집중적으로 다룹니다. 자산의 규모에 대한 분배 및 소싱은 사용 사례로서 간단히 언급됩니다. 이러한 요구 사항에 대한 솔루션에 대해서는 Adobe 브랜드 포털 또는 자산 공유 공유의 사용을 고려하십시오. [AEM Assets 브랜드 포털](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html)과 같은 대체 솔루션, [자산 공유 commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) 구성 요소, [링크 공유](share-assets.md)를 기반으로 구축할 수 있는 솔루션, [AEM Assets 웹 UI](/help/assets/manage-digital-assets.md)은 특정 요구 사항에 따라 검토해야 합니다.

![AEM용 Creative Cloud 연결:사용할 기능 결정](assets/creative-connections-aem.png)

사용할 기능 결정

### 사용 사례 및 Adobe 솔루션 매핑 {#mapping-of-use-cases-and-adobe-solutions}

| 사용 사례 | Adobe Asset Link | AEM Desktop App | 언급 또는 대체 방법 |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Discover - AEM 폴더 찾아보기 | 예 | AEM 웹 UI + 데스크탑 작업 | 네트워크 공유를 검색할 때 자산의 바이너리 파일을 다운로드하지 않도록 축소판을 끕니다. |
| Discover - AEM 컬렉션 액세스 | 예 | AEM 웹 UI + 데스크탑 작업 |  |
| Discover - AEM에서 자산 검색 | 예 | AEM 웹 UI + 데스크탑 작업 |  |
| 사용 - 자산 열기 | 예 | 예 - 모든 앱에 사용 | [Finder에서 웹 ](/help/assets/manage-digital-assets.md#previewing-assets) 인터페이스에서 열기 |
| 사용 - AEM의 에셋을 문서에 배치 | 예 - 포함 | 예 - 연결 또는 포함 | AEM 데스크탑 앱은 로컬 파일 시스템의 파일로 에셋에 액세스할 수 있도록 해줍니다. 기본 앱의 이러한 링크는 로컬 경로로 표시됩니다. |
| 편집 - 편집을 위해 열기 | 예 - 체크아웃 작업 | 예 - 열기 작업(네트워크 공유) | [AAL에서 체크 ](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 아웃하면 기본적으로 사용자의 creative cloud 스토리지 계정(Creative Cloud 앱으로 동기화됨)에 에셋이 저장됩니다. |
| 편집 - AEM 외부에서 진행 중 | 예 - 데스크탑에 동기화되는 사용자의 Creative Cloud 저장소 계정에서 사용할 수 있는 자산입니다. | 예 |  |
| 편집 - 변경 내용 업로드 | 예 - [체크 인 작업](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html)(선택 사항 주석 포함) | 예 |  |
| 업로드 - 단일 파일 | 예 - 현재 활성 문서를 업로드합니다. | 예 | [웹 인터페이스를 통해 업로드](/help/assets/manage-digital-assets.md#uploading-assets) |
| 업로드 - 여러 파일/계층적 폴더 구조 | 아니오 | 예 | [웹 인터페이스를 통해](/help/assets/manage-digital-assets.md#uploading-assets) 업로드;사용자 정의 스크립팅 또는 도구 |
| 기타 - 사용자 및 로그인 | Creative Cloud 데스크톱 응용 프로그램에 로그인한 Creative Cloud 사용자가 인식됨(SSO) | AEM 사용자/로그인 | 두 솔루션의 사용자는 AEM 사용자 할당량에 따라 계산됩니다. |
| 기타 - 네트워크 및 액세스 | 네트워크를 통해 사용자 데스크탑에서 AEM 배포에 액세스 필요 | 네트워크를 통해 사용자 데스크탑에서 AEM 배포에 액세스 필요 | Adobe 자산 링크가 네트워크 프록시 환경을 공유하지 않습니다. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

자산 배포 사용 사례를 지원하려면 다른 솔루션을 고려해야 합니다.

* [AEM Assets 브랜드 ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) 프로모션을 참조하십시오.

* 사용자 지정 솔루션은 [자산 공유 공용](https://adobe-marketing-cloud.github.io/asset-share-commons/) 코드 베이스를 기반으로 만들어집니다.
* AEM [링크 공유](/help/assets/share-assets.md)를 참조하십시오.
* [AEM Assets 웹 ](/help/assets/manage-digital-assets.md) 인터페이스는 AEM 액세스 제어 설정 및 필요한 IT/네트워크 구성 조정을 통해 외부 업체를 위한 영역과 상호 작용하여 외부 사용자가 AEM에 액세스할 수 있도록 합니다.

## 주요 개념 및 사용 사례 {#key-concepts-and-use-cases}

### 일반 용어 용어집 {#glossary-of-common-terms}

* **진행 중인 작업 또는 WIP(Creative Work-in-** Progress): 자산이 여러 개의 변경을 받고 일반적으로 더 광범위한 팀과 공유할 준비가 되어 있지 않은 자산 라이프사이클의 단계입니다.
* **크리에이티브한 에셋:** 마케팅 또는 LOB 팀과 공유할 수 있도록 크리에이티브 팀에서 선택/승인한 자산을 더 광범위한 팀과 공유할 준비가 되었거나, 선택할 수 있습니다.

* **자산 승인:** DAM에 이미 업로드된 자산에 대해 실행되는 승인 프로세스는 일반적으로 브랜드 승인, 법적 승인 등을 포함합니다.
* **최종 자산:** 모든 승인/메타데이터 태그 지정을 통해 광범위한 팀에서 사용할 준비가 된 자산입니다. 이러한 자산은 DAM에 저장되며 모든(또는 모든 관심 있는) 사용자가 사용할 수 있게 됩니다. 마케팅 채널 또는 크리에이티브 팀이 디자인을 제작하는 데 사용할 수 있습니다.

* **사소한 에셋 업데이트/변경:** 디지털 에셋에 대한 빠르고 작은 변경 사항입니다. 수정 또는 경미한 편집 요청, 에셋 검토 또는 승인(예: 위치 변경, 텍스트 크기 변경, 채도/밝기, 색상 조정 등)에 대한 응답으로 주로 사용됩니다.
* **주요 에셋 업데이트/변경:** 상당한 작업이 필요하고 경우에 따라 긴 시간 동안 수행해야 하는 디지털 에셋의 변경 사항입니다. 일반적으로 여러 변경 사항이 포함됩니다. 자산을 업데이트하는 동안 여러 번 저장해야 합니다. 주요 자산 갱신으로 인해 일반적으로 자산이 WIP 단계에 들어갑니다.
* **DAM:** 디지털 에셋 관리. 이 문서에서 별도로 언급되지 않는 한 AEM Experience Manager 자산과 비슷합니다.
* **크리에이티브 사용자:** Creative Cloud 앱 및 서비스를 사용하여 디지털 자산을 만드는 크리에이티브 전문가입니다. 경우에 따라 크리에이티브 사용자는 Creative Cloud을 사용할 수 있지만 디지털 에셋(예: 크리에이티브 디렉터 또는 크리에이티브 팀 관리자)을 만들지 않는 크리에이티브 팀의 구성원일 수 있습니다.
* **DAM 사용자:** DAM 시스템의 일반 사용자입니다. 조직에 따라 DAM 사용자는 마케팅 또는 비마케팅 사용자가 될 수 있습니다(예: LOB(Line-of-Business) 사용자, 사관, 영업 사원 등).

### AEM 및 Creative Cloud 통합 사용 시 고려 사항 {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

AEM 및 Creative Cloud 통합에 대한 모범 사례에 대한 간략한 요약입니다. 이 문서의 나머지 부분을 참조하여 이러한 내용을 자세히 파악하십시오.

* **Photoshop, InDesign 또는 Illustrator에서 작업하는 크리에이티브 사용자의 경우:** Adobe Asset Link는 AEM에서 체크 아웃한 자산에 대한 진행 중인 작업을 깔끔하게 처리하는 등 최고의 사용자 환경을 제공합니다
* **모든 일반 파일 포맷 또는 응용 프로그램에 대해 데스크탑에서 에셋에 간편하게 액세스할 수 있도록 하기: AEM 데스크탑 앱** 사용
* **DAM에 에셋을 저장하는 이유와 시기 이해:** 조직의 광범위한 팀에서 사용할 수 있는 업데이트
* **공유된 자산의 양** 에 주의하십시오. 사용 사례가 자산 배포인 경우, 거버넌스 및 보안이 가장 중요한 부분이 될 수 있습니다. 브랜드 포털과 같이 규모에 맞게 구축된 툴을 사용하는 것이 좋습니다.
* **자산 라이프사이클 이해:** 조직에서 다양한 팀이 자산을 처리하는 방법 파악
* **PS, AI, ID를 통해 자주 저장되는 에셋 저장 처리:** Adobe Asset Link가 자동으로 처리합니다. 다른 응용 프로그램의 경우, DAM의 모든 변경 사항이 필요하지 않은 경우 매핑된/공유 폴더에서 진행 중인 작업을 수행하지 마십시오

### AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}에서 Adobe Stock 에셋에 액세스

[AEM 및 Adobe Stock ](/help/assets/aem-assets-adobe-stock.md) 통합은 AEM 사용자에게 Adobe Stock에서 AEM으로 에셋을 검색, 미리 보기, 라이선스 및 저장할 수 있는 기능을 제공합니다. 라이선스가 부여된 Adobe Stock 에셋에 저장된 Stock 메타데이터가 선택되었으며 추가 필터로 해당 메타데이터를 검색하는 데 사용할 수 있습니다.

이 통합에 대한 몇 가지 중요 사항:

* Adobe 스톡 에셋을 AEM에 저장하면, 이진 파일이 AEM 저장소에 저장된 일반 AEM Assets이 됩니다. Adobe Stock과 관련된 일부 메타데이터는 AEM의 자산에 대해 저장되며, 그렇지 않으면 통합 프로세스는 다른 파일과 동일하게 보입니다. 예를 들어 스마트 태그가 활성 상태인 경우 저장 시 이러한 자산에 태그가 추가됩니다.
* AEM에 저장된 에셋은 다시 Adobe Stock으로 연결되는 링크가 아니라 복사본입니다.

**Creative Cloud에서 Adobe Stock에서 AEM으로 저장된 에셋을 사용하여 작업할 수 있습니다**. 이 통합은 Adobe 에셋 링크와는 독립적이지만 Adobe 에셋 링크는 이러한 방식으로 Stock에서 저장된 에셋을 인식하며 Photoshop, Illustrator 또는 InDesign의 Adobe 에셋 링크 확장 UI에 이러한 에셋에 추가 메타데이터 및 Stock 아이콘을 표시합니다. 파일은 AEM에 저장할 때 일반 AEM 자산이므로 찾아보거나 여는 등의 작업을 수행할 수 있습니다.
Adobe 에셋 링크 확장 기능이 있는 Creative Cloud 앱에서 작업하는 크리에이티브 사용자는 Adobe Stock에서 AEM으로 이미 라이선스가 부여된 에셋에 액세스할 수 있을 뿐만 아니라 Creative Cloud 라이브러리 패널을 사용하여 Adobe Stock 에셋을 검색하고 미리 보고 라이선스를 부여할 수도 있습니다.
AEM Assets 라이선스를 구매하여 AEM에 저장된 Adobe Stock의 에셋은 배포에 액세스하는 광범위한 팀에서 사용할 수 있는 반면, Creative Cloud 라이브러리 패널을 통해 Adobe Stock의 크리에이티브 라이선스 에셋을 Creative Cloud 계정에서만 기본적으로 이용할 수 있습니다.

## DAM {#about-storing-assets-in-a-dam}에 에셋 저장 정보

크리에이티브 팀과 마케팅/LOB(Line-Of-Business) 팀 간의 효율적인 워크플로우를 설계하고 최상의 지원 기능을 선택하려면 DAM에 자산이 저장되는 시기와 이유를 이해하는 것이 중요합니다.

### 자산이 DAM {#why-assets-are-stored-in-dam}에 저장되는 이유

DAM에 에셋을 저장하면 손쉽게 액세스하여 완료할 수 있습니다. 이를 통해 조직 또는 에코시스템 전반에 걸쳐 파트너, 고객 등이 포함된 수많은 사용자가 자산을 활용할 수 있습니다.

대부분의 조직은 다운스트림 마케팅/LOB 프로세스와 관련이 있는 자산만 저장하도록 선택합니다(AEM Sites 또는 Adobe Experience Cloud에서 제공하는 기타 채널을 통해 웹 채널에 게시 - Marketing Cloud, Advertising Cloud, Analytics Cloud에서 측정, 사용자/파트너에게 제공 등). 또한 조직은 DAM에서 검토/승인 프로세스를 진행할 수 있는 자산을 저장합니다. 이렇게 하면 DAM은 대부분 자산을 활용할 가능성이 높은 에셋을 저장하고 유휴 에셋을 저장하지 않습니다.

에셋 저장은 기술 및 리소스 활용 고려 사항도 따릅니다. DAM은 메타데이터 추출, 버전 관리, 미리 보기/트랜스코딩 생성, 참조 관리, 액세스 제어 정보 추가 등 저장된 에셋에 대한 추가 서비스를 제공합니다. 이러한 서비스는 추가 시간 및 인프라 리소스를 소모합니다.

자주, 모든 자산 및 업데이트를 저장하는 것은 좋지 않습니다. 예를 들어 특정 자산에 대한 업데이트가 품질이 좋지 않고 리소스를 과도하게 사용하는 경우 DAM에 에셋이 저장되지 않을 수 있습니다.

#### 에셋이 DAM {#when-assets-are-stored-in-dam}에 저장되는 경우

일반적으로 크리에이티브 팀(및 조직)은 자산 라이프사이클의 각 단계에서 자산을 저장하는 데 관심이 없습니다. 예를 들어 다음과 같은 경우 에셋이 저장되지 않습니다.

* 아직 확정되지 않았거나 실험 대상이 되는 자산
* 크리에이티브/내부 팀 검토 주기를 통과하지 못한 에셋
* 해당 자산에 비해 외부 팀을 대표할 후보가 더 많다

일반적으로 다음 클래스 에셋은 DAM에 저장됩니다.

* 특정 성숙도에 도달했고 공유할 준비가 된 에셋
* 크리에이티브 팀이 미리 선택한 에셋
* 특정 계약이나 계약에 따라 마케팅 부서에서 사용 또는 요구하는 특정 에셋 포맷(예: RAW 파일에서 변환된 JPG 파일, TIFF/PSD 원본 이미지)

#### 자산 업데이트가 DAM {#when-updates-to-assets-are-stored-in-dam}에 저장되는 경우

일반적으로 DAM 사용자의 광범위한 집합과 관련된 에셋에 대한 업데이트만 DAM에 저장해야 합니다. 이는 사용자(마케팅 및 유사한 기능)가 DAM 자산 타임라인에서 관련 버전만 볼 수 있도록 합니다.

일반적으로 자산 라이프사이클의 주요 마일스톤과 관련된 변경 사항입니다. 예를 들어 크리에이티브 팀에서 제공하는 요청/검토 작업에 따라 마케팅 준비가 완료된 초기 자산이나 공식 업데이트를 DAM에 저장하고 버전이 관리되어야 합니다.

DAM의 기존 에셋 변경 요청 후 마케팅 팀이 검토할 크리에이티브 팀의 업데이트는 관련 업데이트의 예입니다. DAM에 저장되고 버전을 관리하여 더 참조하거나 이전 버전으로 되돌려야 합니다.

다음은 일반적으로 관련이 없는 업데이트의 예입니다.

* 마케팅 검토 준비가 되기 전에 업로드된 자산의 이전 버전
* 크리에이티브 팀과 마케팅 팀은 자산이 준비되었다고 판단하기 전에 진행 중인 작업에서 자산을 자주 크리에이티브하게 변경

### DAM {#user-access-to-dam}에 대한 사용자 액세스

AEM Assets은 AEM Assets 배포에 대한 액세스를 기반으로 두 가지 유형의 사용자를 지원합니다. 일반적으로 엔터프라이즈 네트워크(방화벽) 내의 사용자는 DAM에 직접 액세스할 수 있습니다. 엔터프라이즈 네트워크 외부의 다른 사용자는 직접 액세스할 수 없습니다. 사용자 유형은 기술적 관점에서 사용할 수 있는 통합을 결정합니다.

#### DAM {#creative-users-with-direct-access-to-dam}에 직접 액세스하는 크리에이티브 사용자

일반적으로 사내 크리에이티브 팀 또는 내부 네트워크에 연결된 에이전시/크리에이티브 전문가는 AEM 로그인을 비롯한 DAM 인스턴스에 액세스할 수 있습니다. AEM 및 네트워크 인프라를 설정하여 외부 업체(일반적으로 클라이언트를 위해 일하는 에이전시 등 신뢰할 수 있는 조직)에 직접 액세스할 수 있으므로 VPN 또는 IP 허용 목록을 통해 AEM을 이용할 수 있습니다.

이러한 경우 Adobe Asset Link 또는 AEM 데스크탑 앱을 사용하면 최종/승인된 자산에 손쉽게 액세스할 수 있고 크리에이티브한 에셋을 DAM에 저장할 수 있습니다.

#### DAM {#creative-users-without-access-to-dam}에 액세스할 수 없는 크리에이티브 사용자

DAM 인스턴스에 직접 액세스하지 않고도 외부 에이전시 및 프리랜서가 승인된 자산을 액세스하거나 DAM에 새로운 디자인을 추가해야 할 수 있습니다.

다음 전략을 사용하여 최종/승인된 자산에 액세스할 수 있습니다.

* 자산 링크가 작동하지 않는 경우 데스크탑 앱을 사용하십시오.
* 외부 파트너에게 자산을 안전하게 배포하려면 [AEM Assets 브랜드 포털](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html)을 사용하십시오.
* [자산 공유 공용](https://adobe-marketing-cloud.github.io/asset-share-commons/)을 기반으로 하는 배포 및 소싱 포털의 사용자 지정 구현 사용
* AEM에 설정된 액세스 제어 기능과 필요한 네트워크 인프라(예: VPN 및 IP 허용 목록)를 사용하여 외부 당사자가 DAM의 전용 컨텐츠 영역에 액세스할 수 있도록 합니다. AEM 웹 UI를 사용하여 에셋을 가져오고 새 컨텐츠를 DAM에 업로드할 수 있습니다.

#### AEM {#work-in-progress-on-assets-from-aem}의 자산에서 진행 중인 작업

이 문서에서 설명한 바와 같이, 로컬 파일에 저장된 모든 편집 내용을 AEM에 변경 내용으로 업로드하지 않고도 진행 중인 작업이라고도 하는 자산에 대한 주요 업데이트를 수행하는 것이 좋습니다. 이를 통해 데스크탑 사용자의 작업 시간을 단축하고, 네트워크 대역폭을 제한하며, 에셋 타임라인을 깔끔하게 유지하고 제어되고 주요 업데이트에 집중할 수 있습니다.

Adobe 자산 링크는 이 사용 사례에 대한 적절한 지원을 제공합니다.

* Photoshop, InDesign 또는 Illustrator의 사용자가 파일을 편집하려고 하면 해당 자산에 대해 체크아웃 작업을 실행합니다
* 자산이 백그라운드에서 다운로드되고 Creative Cloud 데스크탑 앱별로 디스크에 동기화된 사용자 Creative Cloud 계정에 배치되며, 자산에 있는 AEM에서 체크아웃 플래그가 전환되어 편집 충돌을 최소화할 수 있습니다
* 이 서버에서는 사용자가 동기화된 위치에 로컬로 저장된 파일에서 작업하며 필요한 빈도에 관계없이 필요한 변경 사항을 계속해서 작업하고 저장할 수 있습니다
* 또한 자산은 Creative Cloud 계정에 있으므로 사용자가 가질 수 있는 다른 장치(예: 전용 Creative Cloud 모바일 앱에서 열거나 편집할 수 있음)에서도 사용할 수 있으며 공동 작업을 위해 다른 Creative Cloud 사용자와 공유할 수 있습니다.
* 크리에이티브 사용자가 변경 사항을 수행한 경우 Creative Cloud 애플리케이션에서 해당 파일에 대한 체크 인 작업을 실행할 수 있으며 선택적인 주석을 추가할 수 있습니다. AEM의 해당 에셋에 버전이 매겨지고 새 바이너리로 업데이트됩니다. 마케터나 LOB 사용자와 같은 AEM 사용자는 AEM 에셋 타임라인 UI를 통해 주요 에셋 변경 사항 또는 마일스톤에 액세스할 수 있습니다.

AEM 데스크탑 앱은 기본 앱에서 열린 자산에 대한 네트워크 공유를 제공합니다. 기본적으로 로컬에서 수행한 모든 변경 사항은 잠시 후 AEM에 자동으로 업로드됩니다. 이러한 구성을 통해 진행 중인 작업 중 빈번한 저장 내용이 AEM에 업로드되고 버전이 관리되므로 AEM에서 불필요한 버전은 물론 네트워크 트래픽과 잠재적인 확장성 문제를 야기합니다.

여기서 권장되는 방법은 AEM 데스크탑 앱의 옵션을 사용하여 자동화된 업데이트를 끄고, 자산에 대한 변경 사항을 AEM에 수동으로 업로드하여 앱의 자산 상태 UI에서 변경 사항 업로드 작업을 이용하는 것입니다.

#### DAM {#bulk-upload-to-dam}에 일괄 업로드

다음과 같은 경우 DAM에 더 많은 파일을 동시에 업로드해야 할 수 있습니다.

* 사진 촬영 또는 대규모 프로젝트의 결과 업로드
* 크리에이티브 에이전시에서 제공하는 에셋 업로드
* DAM 외부에서 선택한 경우 더 큰 세트에서 선택한 자산 업로드

이 설명은 데스크탑 사용자의 워크플로우에서 정상적인 부분으로 파일(예: 매주 또는 모든 사진 촬영)을 정상적으로 업로드하는 것을 말합니다. 대규모 자산 마이그레이션은 여기에서 다루지 않습니다.

다음과 같은 업로드 기능을 활용할 수 있습니다.

* 대용량/계층적 폴더를 일괄 업로드하려면 [폴더 업로드](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) 기능을 제공하는 AEM 데스크탑 앱을 사용하십시오. 계층 폴더 구조를 업로드할 수도 있습니다. 자산은 백그라운드에서 업로드되므로 웹 브라우저 세션에 연결되지 않습니다
* 하나의 폴더에서 몇 개의 파일을 업로드하려면 파일을 웹 인터페이스로 직접 드래그하거나 AEM Assets 웹 인터페이스에서 만들기 옵션을 사용합니다.
* 비즈니스 요구 사항에 따라 사용자 지정 업로더를 사용할 수도 있습니다.

#### 데스크톱 {#managing-digital-assets-directly-from-desktop}에서 직접 디지털 자산 관리

네트워크 파일 공유를 사용하여 디지털 자산을 관리하는 경우, AEM 데스크탑 앱으로 매핑된 네트워크 공유를 사용하는 것만으로도 편리한 대체품으로 간주될 수 있습니다. 네트워크 파일 공유에서 전환할 때 AEM 웹 인터페이스는 네트워크 공유(검색, 컬렉션, 메타데이터, 공동 작업, 미리 보기 등)에서 가능한 것 이상으로 풍부한 디지털 자산 관리 기능을 제공하고, AEM 데스크탑 앱은 서버측 DAM 저장소를 데스크탑의 작업과 연결하는 편리한 링크를 제공합니다.

AEM 데스크탑 앱을 사용하여 AEM Assets의 네트워크 공유에서 바로 에셋을 관리하지 마십시오. 예를 들어 AEM 데스크탑 앱을 사용하여 여러 파일을 이동/복사하지 마십시오. 대신 AEM Assets 웹 UI를 사용하여 폴더를 Finder/탐색기에서 네트워크 공유로 드래그하거나 AEM Assets 폴더 업로드 기능을 사용합니다.

<!-- 
#### Asset migration {#asset-migration}

To plan and execute asset migrations from existing system to a new system or migration of large volume of assets stored on servers, see the [Migration Guide](/help/assets/assets-migration-guide.md). AEM desktop app and AEM to Creative Cloud integrations do not support such migrations. Due to the large volumes of assets to be ingested, and additional requirements around metadata mapping, transformation, and ingestion, migrations should be handled using different tools and approaches.
-->
