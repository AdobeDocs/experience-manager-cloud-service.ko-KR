---
title: 통합 우수 사례 [!DNL Adobe Creative Cloud]
description: 우수 사례 는 Adobe Creative Cloud과 Experience Manager 배포를 통합하여 자산 전송 워크플로우를 간소화하고 최대 효율성을 달성합니다.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration,Adobe Asset Link,Desktop App
role: Architect,User,Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '3473'
ht-degree: 15%

---

# Adobe Experience Manager 및 Creative Cloud 통합 우수 사례 {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager Assets는 DAM 사용자가 크리에이티브 팀과 함께 작업할 수 있도록 Adobe Creative Cloud과 통합하여 컨텐츠 작성 프로세스에서 간소화된 공동 작업을 수행할 수 있도록 해주는 DAM(디지털 자산 관리) 솔루션입니다.

Adobe Creative Cloud은 크리에이티브 팀이 디지털 자산을 만드는 데 도움이 되는 솔루션 및 서비스 에코시스템을 제공합니다. 여기에는 데스크톱 및 모바일 애플리케이션, 데스크탑 동기화 또는 웹 경험이 포함된 스토리지와 같은 클라우드 서비스, Adobe Stock과 같은 마켓플레이스 등이 포함됩니다.

사용 사례를 기반으로 데스크탑과 엔터프라이즈급 DAM 간에 어떤 통합을 선택하고 연결 워크플로우에 대한 관련 모범 사례는 무엇입니까? 를 참조하십시오.

>[!NOTE]
>
>Creative Cloud 폴더 공유에 대한 Experience Manager은 이제 사용되지 않으며 더 이상 아래에서 다루지 않습니다. Adobe은 크리에이티브 사용자에게 Experience Manager에서 관리되는 자산에 대한 액세스를 제공할 수 있도록 Adobe 자산 링크 또는 Experience Manager 데스크탑 앱과 같은 최신 기능을 권장합니다.

## 크리에이티브, 마케터 및 DAM 사용자의 공동 작업 필요 {#collaboration-need-of-creatives-marketers-and-dam-users}

| 요구 사항 | 사용 사례 | 관련 서피스 |
|---|---|---|
| 데스크탑에서 크리에이티브 환경 간소화 | DAM에서 자산에 대한 액세스 간소화([!DNL Assets])를 사용하도록 선택할 수 있습니다. 이 구성 요소는 새로운 파일을 업로드하고, Experience Manager을 검색, 사용(열기)하고, 변경 사항을 편집 및 저장하며, 쉽고 간단한 방법이 필요합니다. | Win 또는 Mac 데스크탑 앱 Creative Cloud |
| Adobe Livefyre에서 고품질의 즉시 사용할 수 있는 자산 제공 [!DNL Adobe Stock] | 마케터는 자산 소싱 및 검색을 지원하여 컨텐츠 작성 프로세스를 가속화할 수 있습니다. 크리에이티브 전문가가 크리에이티브 도구 내에서 바로 승인된 자산을 사용합니다. | [!DNL Assets]; [!DNL Adobe Stock] marketplace; 메타데이터 필드 |
| 조직별 자산 분배 및 공유 | 내부 부서/지역 분기 및 외부 파트너, 배포자 및 에이전시는 상위 조직에서 공유한 승인된 자산을 사용합니다. 조직은 더 광범위한 재사용을 위해 생성된 자산을 안전하고 원활하게 공유하려고 합니다. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| 업로드된 자산의 사전 정의된 변형을 자동으로 생성합니다 | 사전 정의된 작업에 Adobe의 고유한 미디어 처리 및 변환 기술을 활용하여 자산을 자동으로 처리합니다. API 및 자산 마이크로서비스를 사용하여 고유한 작업을 정의하는 사용자 지정 로직을 만듭니다. | [!DNL Assets] 사용자 인터페이스 |

## 협업 요구 사항을 지원하기 위한 Adobe 제공 {#adobe-offerings-to-support-the-collaboration-need}

| 관련 성향에 대한 가치 제안 | Adobe 제공 | 관련 서피스 |
|---|---|---|
| 크리에이티브 사용자가 [!DNL Experience Manager], 열기 및 사용 변경 내용 편집 및 업로드 [!DNL Experience Manager]및에 새 파일을 업로드합니다. [!DNL Experience Manager]에 대해 [!DNL Creative Cloud] 앱. | [Adobe Asset Link](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator 및 InDesign. |
| 비즈니스 사용자는 자산 열기 및 사용, 변경 내용 편집 및 업로드 작업을 단순화합니다. [!DNL Experience Manager], 및에 새 파일 업로드 [!DNL Experience Manager] 데스크탑 환경에서 실행할 수 있습니다. 일반 통합을 사용하여 비Adobe을 포함하여 기본 데스크탑 애플리케이션에서 자산 유형을 엽니다. | [[!DNL Experience Manager] 데스크탑 앱](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Win 및 Mac 데스크탑의 데스크탑 앱 Experience Manager |
| 마케터와 비즈니스 사용자는 Experience Manager 내에서 Adobe Stock 자산을 검색, 미리 보기, 라이선스 및 저장 및 관리합니다. 라이선스와 저장된 자산은 더 나은 거버넌스를 위해 선별된 Adobe Stock 메타데이터를 제공합니다. | [Experience Manager 및 Adobe Stock 통합](aem-assets-adobe-stock.md) | [!DNL Experience Manager] 웹 인터페이스 |
| 디지털 제품 디자이너와 마케터 간의 공동 작업을 개선합니다. 디자이너는 디자인에서 디지털 자산을 사용하고 Adobe XD 캔버스에서 와이어프레임 모델을 사용할 수 있습니다. | [[!DNL Adobe Asset Link] 대상 [!DNL Adobe XD]](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| 마케터는 사용자 지정을 사용하여 만든 업로드된 자산 및 사전 정의된 작업을 기반으로 변형 및 파생물을 자동으로 만들 수 있습니다. 이 자동화를 사용하여 컨텐츠 속도를 향상시키고 수작업 부담을 줄일 수 있습니다. | [컨텐츠 자동화](/help/assets/cc-api-integration.md) | [!DNL Experience Manager Assets] 웹 인터페이스 |

This article focuses primarily on the first two aspects of the collaboration needs. Distribution and sourcing of assets at scale is briefly mentioned as a use case. For such needs solutions, consider Adobe Brand Portal or Asset Share Commons. 과 같은 대체 솔루션 [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), 다음을 기반으로 구축 가능한 솔루션 [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/) 구성 요소, [링크 공유](share-assets.md), 사용 [Experience Manager Assets 웹 UI](/help/assets/manage-digital-assets.md) 구체적인 요구 사항에 따라 검토해야 합니다.

![Experience Manager Creative Cloud 연결: 사용할 기능 결정](assets/creative-connections-aem.png)

사용할 기능 결정

### 사용 사례 및 Adobe 솔루션 매핑 {#mapping-of-use-cases-and-adobe-solutions}

| 사용 사례 | Adobe Asset Link | Experience Manager 데스크탑 앱 | 설명 또는 대체 방법 |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| 검색 - 폴더 찾아보기 | 예 | 웹 UI Experience Manager + 데스크탑 작업 | 네트워크 공유를 검색할 때 자산의 이진 파일을 다운로드하지 않도록 미리 보기를 끕니다. |
| 검색 - 컬렉션 액세스 | 예 | 웹 UI Experience Manager + 데스크탑 작업 |  |
| 검색 - 자산 검색 | 예 | 웹 UI Experience Manager + 데스크탑 작업 |  |
| 사용 - 자산 열기 | 예 | 예 - 모든 앱의 경우 | [웹 인터페이스에서 열기](/help/assets/manage-digital-assets.md#previewing-assets) 또는 파인더에서 |
| 사용 - Experience Manager의 자산을 문서에 배치 | 예 - 포함 | 예 - 연결 또는 포함 | Experience Manager 데스크탑 앱에서는 로컬 파일 시스템에서 자산으로 자산에 대한 액세스를 제공합니다. 기본 앱의 이러한 링크는 로컬 경로로 표시됩니다. |
| 편집 - 열어서 편집합니다. | 예 - 체크아웃 작업 | 예 - 열린 작업(네트워크 공유에서) | [AAL에서 체크아웃](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 기본적으로 자산을 사용자의 creative cloud 저장소 계정(Creative Cloud 앱별로 동기화)에 저장합니다. |
| 편집 - Experience Manager 외부에서 진행 중 | 예 - 데스크탑에 동기화된 사용자의 Creative Cloud 저장소 계정에서 사용할 수 있는 자산입니다. | 예 |  |
| 편집 - 변경 내용 업로드 | 예 - [체크인 작업](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 선택적 주석 | 예 |  |
| 업로드 - 단일 파일 | 예 - 현재 활성 문서 업로드 | 예 | [웹 인터페이스를 통해 업로드](/help/assets/manage-digital-assets.md#uploading-assets) |
| 업로드 - 여러 파일/계층 폴더 구조 | 아니요 | 예 | [웹 인터페이스를 통해 업로드](/help/assets/manage-digital-assets.md#uploading-assets); 사용자 정의 스크립팅 또는 도구 |
| 기타 - 사용자 및 로그인 | Creative Cloud 사용자가 Creative Cloud 데스크탑 앱에 로그인되어 인식됨(SSO) | Experience Manager 사용자 / 로그인 | 두 솔루션의 사용자는 Experience Manager 사용자 할당량에 따라 계산됩니다. |
| 기타 - 네트워크 및 액세스 | 네트워크를 통한 Experience Manager 배포를 위해 사용자의 데스크탑에서 액세스 필요 | 네트워크를 통한 Experience Manager 배포를 위해 사용자의 데스크탑에서 액세스 필요 | Adobe 자산 링크가 네트워크 프록시 환경을 공유하지 않습니다. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

자산 분배 사용 사례를 지원하려면 다음 옵션을 고려하십시오.

* [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) 자산을 게시하기 위해 자산에 구성 가능한 추가 기능을 사용할 수 있습니다.

* 사용자 지정 솔루션은 [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/) 코드 베이스입니다.
* Experience Manager [링크 공유](/help/assets/share-assets.md) 링크를 사용하여 자산을 ad hoc으로 공유하려면 다음을 수행하십시오.
* [Assets 웹 인터페이스](/help/assets/manage-digital-assets.md) Experience Manager 액세스 제어 설정에 의해 보안 상태가 되고 필요한 IT/네트워크 구성 조정을 통해 외부 당사자를 위한 영역을 사용하여 이러한 외부 사용자에게 Experience Manager 액세스 권한을 제공합니다.

## 주요 개념 및 사용 사례 {#key-concepts-and-use-cases}

### 일반 용어 목록 {#glossary-of-common-terms}

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.

* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.

* **Minor asset  update/change :** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change :** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.

### Experience Manager 및 Creative Cloud 통합을 사용할 때의 고려 사항 {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Experience Manager 및 Creative Cloud 통합에 대한 모범 사례에 대한 간략한 요약입니다. 이 문서의 나머지 부분을 읽어 자세한 내용을 파악합니다.

* **Photoshop, InDesign 또는 Illustrator에서 작업하는 크리에이티브 사용자의 경우:** Adobe 자산 링크는 Experience Manager에서 체크 아웃된 자산에 대해 진행 중인 작업을 깨끗한 처리하는 등 최상의 사용자 경험을 제공합니다
* **모든 일반 파일 형식 또는 애플리케이션에 대해 데스크탑에서 자산에 대한 액세스를 간소화하기 위해:** Experience Manager 데스크탑 앱 사용
* **Understand why and when to store assets in DAM:** Updates to be made available to the broader team in your organization
* **Mind the volume of assets shared:** If your use case is asset distribution, governance and security might be the most important aspects. Consider using tools built for doing that at scale, like Brand Portal.
* **Understand asset lifecycle:** Know how assets are handled in your organization by different teams
* **Handle frequent saves to assets with care:** Adobe Asset Link takes care of that for you with PS, AI, ID. For other applications, don&#39;t carry out work in progress tasks in mapped/shared folder unless you need all the changes in DAM

### Experience Manager Assets에서 Adobe Stock 자산에 대한 액세스 {#access-to-adobe-stock-assets-from-aem-assets}

[Experience Manager 및 Adobe Stock 통합](/help/assets/aem-assets-adobe-stock.md) Adobe Stock에서 Experience Manager으로 자산을 검색, 미리 보기, 라이선스 및 저장할 수 있는 기능을 Experience Manager 사용자에게 제공합니다. 라이선스가 있고 저장된 Adobe Stock 자산이 Stock 메타데이터를 선택했으며, 이 메타데이터를 추가 필터로 검색하는 데 사용할 수 있습니다.

이 통합에 대한 몇 가지 중요한 사항:

* Adobe 스톡 자산의 Experience Manager이 저장되면 Experience Manager Assets 저장소는 바이너리가 Experience Manager 저장소에 저장된 일반가 됩니다. Adobe Stock과 관련된 일부 메타데이터는 Experience Manager의 자산에 대해 저장되지만, 그렇지 않으면 수집 프로세스가 다른 파일과 동일하게 표시됩니다. 예를 들어, 스마트 태그가 활성화되어 있으면 저장 시 태그가 이러한 자산에 추가됩니다.
* Experience Manager에 저장된 자산은 복사이며, Adobe Stock에 다시 연결되는 링크가 아닙니다.

**Adobe Stock에서 Creative Cloud의 Experience Manager으로 저장된 자산 작업**. 이 통합은 Adobe 자산 링크와는 다르지만, Adobe 자산 링크는 Stock에서 저장된 이러한 자산을 그러한 방식으로 인식하고, Photoshop, Illustrator 또는 InDesign의 Asset Link 확장 UI에 이러한 자산에 대한 추가 메타데이터 및 Stock 아이콘을 표시합니다. 파일은 Experience Manager에 저장할 때 일반 Experience Manager 자산이므로 찾아보기, 열기 등에 사용할 수 있습니다.
Adobe Stock에서 Experience Manager으로 이미 라이선스가 부여된 자산에 액세스할 수 있을 뿐만 아니라 Adobe Asset Link 확장이 있는 Creative Cloud 앱에서 작업하는 크리에이티브 사용자도 Creative Cloud 라이브러리 패널을 사용하여 Adobe Stock 자산을 검색, 미리 보기 및 라이선스를 제공할 수 있습니다.
사용이 허가되고 Experience Manager에 저장된 Adobe Stock의 자산은 Experience Manager Assets 배포에 액세스하는 더 광범위한 팀에서 사용할 수 있게 되지만, Creative Cloud 라이브러리 패널을 통해 Adobe Stock의 광고 라이선스 자산을 사용하면 Creative Cloud 계정에서만 기본적으로 사용할 수 있습니다.

## DAM에 자산 저장 정보 {#about-storing-assets-in-a-dam}

크리에이티브 및 마케팅/LOB(Line of Business) 팀 간의 효율적인 워크플로우를 설계하고 최상의 지원 기능을 선택하려면 DAM에 자산이 저장되는 시기와 이유를 이해하는 것이 중요합니다.

### 자산이 DAM에 저장되는 이유 {#why-assets-are-stored-in-dam}

DAM에 자산을 저장하면 쉽게 액세스하고 이를 완료할 수 있습니다. Launch를 사용하면 파트너, 고객 등을 포함하는 조직 또는 에코시스템에서 다양한 사용자가 자산을 활용할 수 있습니다.

대부분의 조직은 다운스트림 마케팅/LOB 프로세스와 관련된 자산만 저장하도록 선택합니다(Experience Manager Sites을 통해 웹 채널 또는 Adobe Experience Cloud에서 제공하는 기타 채널 - Marketing Cloud, Advertising Cloud 및 Analytics Cloud에서 측정된 측정, 사용자/파트너에게 제공 등). 또한 조직은 DAM에서 검토/승인 프로세스를 수행할 수 있는 자산을 저장합니다. 이 방법으로 DAM은 주로 자산을 활용할 가능성이 높고 유휴 자산을 저장하지 않는 자산을 저장합니다.

자산을 저장하는 것은 기술 및 리소스 활용률 고려도 받습니다. DAM은 메타데이터 추출, 버전 관리, 미리 보기/코드 변환 생성, 참조 관리, 액세스 제어 정보 추가 등 저장된 자산에 대한 추가 서비스를 제공합니다. 이러한 서비스는 추가 시간과 인프라 자원을 사용합니다.

모든 자산과 업데이트를 저장하는 것은 권장되지 않는 경우가 많습니다. 예를 들어 특정 자산에 대한 업데이트가 품질이 좋지 않고 과도한 리소스를 소비하는 경우 자산이 DAM에 저장되지 않을 수 있습니다.

#### 자산이 DAM에 저장되는 경우 {#when-assets-are-stored-in-dam}

광고 팀(및 조직)은 일반적으로 자산 라이프사이클의 각 단계에서 자산을 저장하는 것에 관심이 없습니다. 예를 들어 다음과 같은 경우 자산이 저장되지 않습니다.

* 아직 확정되지 않았거나 실험 대상이 되는 자산
* 크리에이티브/내부 팀 검토 주기를 통과하지 못하는 자산
* 해당 자산과 비교하여 외부 팀에 자신들의 일을 대표할 더 나은 후보가 있습니다

일반적으로 다음 클래스 자산은 DAM에 저장됩니다.

* 특정 성숙기에 도달했고 공유할 준비가 된 자산입니다
* 크리에이티브 팀이 미리 선택한 자산
* 특정 계약이나 계약에 따라 마케팅에서 사용 또는 요청한 특정 자산 형식(예: RAW 파일에서 변환된 JPG 파일, PSD 원본에서 TIFF/이미지)

#### 자산 업데이트가 DAM에 저장되면 {#when-updates-to-assets-are-stored-in-dam}

일반적으로, DAM 사용자 광범위한 세트와 관련된 자산만 DAM에 저장해야 합니다. 이렇게 하면 사용자(마케팅 및 유사한 기능)가 DAM 자산 타임라인에서 관련 버전만 볼 수 있습니다.

일반적으로 자산 라이프사이클의 주요 이정표에 관련된 변경 사항입니다. 예를 들어, 크리에이티브 팀이 제공하는 요청/검토를 기반으로 한 초기 마케팅 준비가 완료된 자산이나 공식 업데이트는 DAM에서 저장하고 버전을 지정해야 합니다.

DAM에서 기존 자산의 변경 요청 이후 마케팅 팀이 검토하도록 업데이트되는 크리에이티브 팀의 업데이트는 관련 업데이트의 예입니다. 추가 참조나 이전 버전으로 되돌리려면 DAM에서 저장 및 버전을 지정해야 합니다.

다음은 일반적으로 관련이 없는 업데이트의 예입니다.

* 마케팅 리뷰를 준비하기 전에 업로드된 자산의 이전 버전
* 크리에이티브 및 마케팅 팀이 자산이 준비되었다고 결정하기 전에 진행 중인 작업 단계에서 자산을 자주 크리에이티브 방식으로 변경합니다

### DAM에 대한 사용자 액세스 {#user-access-to-dam}

Experience Manager Assets은 Experience Manager Assets 배포에 대한 액세스 권한에 따라 두 가지 유형의 사용자를 지원합니다. 일반적으로 엔터프라이즈 네트워크(방화벽) 내의 사용자는 DAM에 직접 액세스할 수 있습니다. 엔터프라이즈 네트워크 외부의 다른 사용자는 직접 액세스할 수 없습니다. 사용자 유형은 기술 관점에서 사용할 수 있는 통합을 결정합니다.

#### DAM에 직접 액세스할 수 있는 크리에이티브 사용자 {#creative-users-with-direct-access-to-dam}

일반적으로 내부 크리에이티브 팀이나 내부 네트워크에 온보딩된 에이전시/크리에이티브 전문가가 Experience Manager 로그인을 포함하여 DAM 인스턴스에 액세스할 수 있습니다. Experience Manager 및 네트워크 인프라를 설정하여 외부 대상(일반적으로 클라이언트를 위해 일하는 에이전시와 같이 신뢰할 수 있는 조직)에 직접 액세스하여 VPN 또는 IP 허용 목록을 통해 네트워크를 통한 Experience Manager에 액세스할 수 있습니다.

이러한 경우 Adobe 자산 링크 또는 Experience Manager 데스크탑 앱을 사용하면 최종/승인된 자산에 쉽게 액세스할 수 있고, DAM에 크리에이티브 자산을 저장할 수 있습니다.

#### DAM에 액세스할 수 없는 크리에이티브 사용자 {#creative-users-without-access-to-dam}

DAM 인스턴스에 직접 액세스할 수 없는 외부 에이전시 및 프리랜서는 승인된 자산에 액세스해야 하거나 DAM에 새 디자인을 추가해야 할 수 있습니다.

다음 전략을 사용하여 최종/승인된 자산에 대한 액세스 권한을 제공합니다.

* Asset Link가 작동하지 않는 경우 데스크탑 앱을 사용합니다.
* 사용 [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) 자산을 외부 파트너에게 안전하게 분배하기
* 을 기반으로 하는 배포 및 소싱 포털의 사용자 지정 구현 사용 [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Experience Manager에 설정된 액세스 제어 및 필요한 네트워크 인프라(예: VPN 및 IP 허용 목록)를 사용하여 외부 당사자에게 DAM의 콘텐츠 전용 영역에 대한 액세스 권한을 제공합니다. Experience Manager 웹 UI를 사용하여 자산을 가져오고 새 컨텐츠를 DAM에 업로드할 수 있습니다.

#### Experience Manager에서 자산에 대한 작업 진행 중 {#work-in-progress-on-assets-from-aem}

이 문서에서 설명한 바와 같이, 로컬 파일에 모든 편집 내용을 저장하고 변경 내용으로 Experience Manager에 업로드하지 않고도 진행 중인 작업이라고도 하는 자산에 대한 주요 업데이트를 수행하는 것이 좋습니다. 따라서 데스크탑 사용자의 작업 속도를 높이고, 사용되는 네트워크 대역폭을 제한하며, 자산 타임라인을 깔끔하고 제어된 주요 업데이트에 주력합니다.

Adobe 자산 링크는 이 사용 사례를 지원합니다.

* Photoshop, InDesign 또는 Illustrator의 사용자가 파일을 편집하려고 하면 해당 자산에서 체크아웃 작업을 실행합니다
* 자산이 백그라운드에서 다운로드되고, Creative Cloud 데스크탑 앱별로 디스크에 동기화된 사용자 Creative Cloud 계정에 배치되며,의 Experience Manager에서 체크아웃 플래그가 전환되어 편집 충돌을 최소화합니다
* 여기서 사용자는 동기화된 위치에 로컬로 저장된 파일에서 작업하며 필요한 빈도대로 필요한 변경 사항을 계속 작업하고 저장할 수 있습니다
* 또한, 자산이 Creative Cloud 계정에 있으므로 사용자가 보유하고 있는 다른 장치(예: 전용 Creative Cloud 모바일 앱에서 열거나 편집할 수 있음)에서도 사용할 수 있으며, 공동 작업을 위해 다른 Creative Cloud 사용자와 공유할 수 있습니다.
* 크리에이티브 사용자가 변경 작업을 완료하면 Creative Cloud 애플리케이션에서 해당 파일에 대한 체크 인 작업을 실행할 수 있으며 주석도 선택 가능합니다. Experience Manager의 해당 자산에 버전이 지정되고 새 바이너리로 업데이트됩니다. 마케터나 LOB 사용자와 같은 Experience Manager 사용자는 Experience Manager 자산 타임라인 UI를 통해 주요 자산 변경 사항 또는 이정표에 액세스할 수 있습니다.

Experience Manager 데스크탑 앱에서는 기본 앱에서 열린 자산에 대한 네트워크 공유를 제공합니다. 기본적으로 로컬에서 수행한 모든 변경 사항은 잠시 후 자동으로 Experience Manager에 업로드됩니다. 이러한 구성을 사용하면 진행 중인 작업 단계 동안 자주 저장된 내용을 모두 Experience Manager에 업로드하고 버전이 지정되므로, Experience Manager에서 불필요한 버전은 물론, 많은 네트워크 트래픽과 잠재적인 확장성 문제가 발생할 수 있습니다.

여기에서 권장되는 접근 방법은 Experience Manager 데스크탑 앱의 옵션을 사용하여 자동화된 업데이트를 비활성화하고, 자산에 대한 변경 사항을 수동으로 업로드하여 앱의 Experience Manager 상태 UI에서 변경 사항 업로드 작업을 활용하는 것입니다.

#### DAM에 벌크 업로드 {#bulk-upload-to-dam}

다음과 같은 일부 시나리오에서 많은 수의 파일을 동시에 DAM에 업로드해야 할 필요가 있을 수 있습니다.

* 사진 촬영 또는 더 큰 프로젝트의 결과 업로드
* 크리에이티브 에이전시에서 제공한 자산 업로드
* DAM 외부에서 선택 작업이 수행된 경우 더 큰 세트에서 선택한 자산 업로드

이 설명은 데스크탑 사용자 워크플로우의 일반적인 일부로서 파일을 작동(예: 매주 또는 모든 사진 촬영)하여 업로드하는 것을 의미합니다. 대규모 자산 마이그레이션은 여기에서 다루지 않습니다.

다음 업로드 기능을 활용할 수 있습니다.

* 대용량/계층적 폴더를 벌크로 업로드하려면 다음을 제공하는 Experience Manager 데스크탑 앱을 사용하십시오 [폴더 업로드](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#bulk-upload-assets) 기능을 사용할 수 있습니다. 계층 폴더 구조를 업로드할 수도 있습니다. 자산은 백그라운드로 업로드되므로 웹 브라우저 세션에 연결되어 있지 않습니다
* 단일 폴더에서 몇 개의 파일을 업로드하려면 파일을 웹 인터페이스로 직접 드래그하거나 Experience Manager Assets 웹 인터페이스에서 만들기 옵션을 사용합니다.
* 비즈니스 요구 사항에 따라 사용자 정의 업로더를 사용할 수도 있습니다.

#### 데스크탑에서 직접 디지털 자산 관리 {#managing-digital-assets-directly-from-desktop}

네트워크 파일 공유를 사용하여 디지털 자산을 관리하는 경우, Experience Manager 데스크탑 앱에서 매핑되는 네트워크 공유를 사용하는 것만으로 편리하게 대체할 수 있습니다. 네트워크 파일 공유에서 전환할 때 Experience Manager 웹 인터페이스는 네트워크 공유(검색, 컬렉션, 메타데이터, 공동 작업, 미리 보기 등)에서 가능한 것 이상으로 풍부한 디지털 자산 관리 기능 세트를 제공하고 Experience Manager 데스크탑 앱에서는 서버측 DAM 저장소를 데스크탑의 작업과 연결하는 편리한 링크를 제공합니다.

Experience Manager 데스크탑 앱을 사용하여 Experience Manager Assets의 네트워크 공유에서 직접 자산을 관리하지 마십시오. 예를 들어 Experience Manager 데스크탑 앱을 사용하여 여러 파일을 이동/복사하지 마십시오. 대신 Experience Manager Assets 웹 UI를 사용하여 폴더를 Finder/Explorer에서 네트워크 공유로 드래그하거나 Experience Manager Assets 폴더 업로드 기능을 사용하십시오.

**추가 참조**

* [에셋 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산 지원 파일 형식](file-format-support.md)
* [에셋 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [에셋 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [에셋 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [벌크 메타데이터 가져오기](metadata-import-export.md)
