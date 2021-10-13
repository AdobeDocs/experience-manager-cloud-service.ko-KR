---
title: 컨텐츠 전송 도구 사용
description: 컨텐츠 전송 도구 사용
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: dbca0404c310bc0fa9372347bb7b37649adf8b94
workflow-type: tm+mt
source-wordcount: '3193'
ht-degree: 36%

---

# 컨텐츠 전송 도구 사용 {#using-content-transfer-tool}

## 컨텐츠 전송 도구 사용에 대한 중요한 고려 사항 {#pre-reqs}

아래 섹션을 따라 수행하여 컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하십시오.

* 컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드해야 컨텐츠 전송 도구를 사용할 수 있습니다.

* AEM을 시작하는 사용자가 `java` 명령을 실행할 수 있도록 AEM 환경에서 Java를 구성해야 합니다.

* 도구에 주요 아키텍처 변경 사항이 있으므로 버전 1.3.0을 설치할 때 이전 버전의 컨텐츠 전송 도구를 제거하는 것이 좋습니다. 1.3.0을 사용하면 새 마이그레이션 세트를 만들고 새 마이그레이션 세트에서 추출 및 수집을 다시 실행해야 합니다.

* 컨텐츠 전송 도구는 다음 유형의 데이터 저장소와 함께 사용할 수 있습니다. 파일 데이터 저장소, S3 데이터 저장소, 공유 S3 데이터 저장소 및 Azure Blob 저장소 데이터 저장소.

* *샌드박스 환경*&#x200B;을(를) 사용 중인 경우 환경이 최신 상태이고 최신 릴리스로 업그레이드되었는지 확인하십시오. *프로덕션 환경*&#x200B;을 사용하는 경우 자동으로 업데이트됩니다.

* 컨텐츠 전송 도구를 사용하려면 소스 인스턴스의 관리 사용자여야 하며, 컨텐츠를 전송하는 Cloud Service 인스턴스의 로컬 AEM **administrators** 그룹에 속해 있어야 합니다. 권한이 없는 사용자는 액세스 토큰을 검색하여 컨텐츠 전송 도구를 사용할 수 없습니다.

* 수집&#x200B;**옵션이 활성화되기 전에**&#x200B;클라우드 인스턴스에서 기존 컨텐츠를 지우는 옵션이 활성화되면 기존 저장소 전체를 삭제하고 컨텐츠를 수집 (으)로 수집할 새 저장소를 만듭니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. **administrators** 그룹에 추가된 관리자 사용자에게도 적용됩니다. CTT에 대한 액세스 토큰을 검색하려면 **administrators** 그룹에 사용자를 다시 추가해야 합니다.

* 액세스 토큰은 특정 기간 후 또는 Cloud Service 환경이 업그레이드된 후 주기적으로 만료될 수 있습니다. 액세스 토큰이 만료되면 Cloud Service 인스턴스에 연결할 수 없으며 새 액세스 토큰을 검색해야 합니다. 기존 마이그레이션 세트와 연결된 상태 아이콘은 빨간색 클라우드로 변경되며, 마우스로 가리키면 메시지가 표시됩니다.

* 소스 인스턴스에서 대상 인스턴스로 컨텐츠를 전송하기 전에 CTT(컨텐츠 전송 도구)가 컨텐츠 분석을 수행하지 않습니다. 예를 들어 CTT는 컨텐츠를 게시 환경에 수집하는 동안 게시된 컨텐츠와 게시되지 않은 컨텐츠를 구분하지 않습니다. 마이그레이션 세트에 지정된 모든 콘텐츠는 선택한 대상 인스턴스로 수집됩니다. 사용자는 마이그레이션 세트를 작성자 인스턴스 또는 게시 인스턴스 또는 둘 다에 수집할 수 있습니다. 컨텐츠를 프로덕션 인스턴스로 이동하는 동안 컨텐츠를 타겟 작성자 인스턴스로 이동하도록 소스 작성자 인스턴스에 CTT를 설치하여 컨텐츠를 타겟 게시 인스턴스로 이동시키는 것이 좋습니다. 자세한 내용은 게시 인스턴스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-ctt-on-publish)에서 [컨텐츠 전송 도구 실행 을 참조하십시오.

* 컨텐츠 전송 도구에서 전송한 사용자 및 그룹은 컨텐츠에 의해 권한을 충족하기 위해 필요한 사용자 및 그룹에만 해당합니다. *추출* 프로세스는 전체 `/home`를 마이그레이션 세트에 복사하고 *수집* 프로세스는 마이그레이션된 컨텐츠 ACL에서 참조되는 모든 사용자 및 그룹을 복사합니다. 기존 사용자 및 그룹을 IMS ID에 자동으로 매핑하려면 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#cloud-migration)을 참조하십시오.

* 추출 단계 중에 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 컨텐츠 전송 프로세스의 *추출* 단계를 완료하고 *수집 단계*&#x200B;를 시작하여 AEM as a Cloud Service *Stage* 또는 *프로덕션* 인스턴스에 컨텐츠를 수집하기 전에 지원 티켓을 로그하여 *수집* 프로세스 중에 중단이 발생하지 않도록 Adobe에게 *수집*&#x200B;을 실행할 의사가 있음을 알려야 합니다. 예정된 *수집* 날짜 1주 전에 지원 티켓을 기록해야 합니다. 지원 티켓을 제출하면 지원 팀이 다음 단계에 대한 지침을 제공합니다. 다음 세부 정보로 지원 티켓을 기록할 수 있습니다.

   * *Ingestion* 단계를 시작할 때의 정확한 날짜 및 예상 시간(시간대와 함께).
   * 데이터를 수집할 환경 유형(스테이지 또는 프로덕션)입니다.
   * 프로그램 ID.

* 작성자에 대한 *수집 단계*&#x200B;는 전체 작성자 배포를 축소합니다. 즉, 전체 수집 프로세스 중에 작성자 AEM을 사용할 수 없습니다. 또한 *수집* 단계를 실행하는 동안 Cloud Manager 파이프라인이 실행되지 않는지 확인하십시오.

* 소스 AEM 시스템의 데이터 저장소로 `Amazon S3` 또는 `Azure` 를 사용하는 경우 저장된 Blob(가비지 수집)을 삭제할 수 없도록 데이터 저장소를 구성해야 합니다. 이렇게 하면 인덱스 데이터의 무결성이 보장되고 이러한 방법을 구성하지 않으면 이 인덱스 데이터의 무결성으로 인해 추출에 실패할 수 있습니다.

* 사용자 지정 인덱스를 사용하는 경우 컨텐츠 전송 도구를 실행하기 전에 `tika` 노드로 사용자 지정 인덱스를 구성해야 합니다. 자세한 내용은 [새 인덱스 정의 준비](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#preparing-the-new-index-definition)를 참조하십시오.

* 추가 작업을 하려면 초기 추출을 수행할 때부터 추가 추출을 실행할 때까지의 기존 컨텐츠의 컨텐츠 구조가 변경되지 않는 것이 중요합니다. 초기 추출 후 구조가 변경된 컨텐츠에서는 추가를 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

* 마이그레이션 세트의 일부로 버전을 포함하되 `wipe=false` 을 사용하여 추가 작업을 수행하는 경우, 컨텐츠 전송 도구의 현재 제한 사항으로 인해 버전 제거를 비활성화해야 합니다. 버전 삭제를 사용하도록 유지하고 마이그레이션 세트에 추가 작업을 수행하려는 경우 수집을 `wipe=true`(으)로 수행해야 합니다.

## 사용 가능 {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="다운로드"
>abstract="소프트웨어 배포 포털에서 컨텐츠 전송 도구를 zip 파일로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지를 설치할 수 있습니다. 최신 버전을 다운로드해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="릴리스 노트"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="소프트웨어 배포 포털"

소프트웨어 배포 포털에서 컨텐츠 전송 도구를 zip 파일로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지를 설치할 수 있습니다. 최신 버전을 다운로드해야 합니다. 최신 버전에 대한 자세한 내용은 [릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 참조하십시오.

>[!NOTE]
>[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 컨텐츠 전송 도구를 다운로드합니다.

## 컨텐츠 전송 도구 실행 {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="컨텐츠 전송 도구 실행"
>abstract="컨텐츠 전송 도구를 사용하여 컨텐츠를 AEM as a Cloud Service(작성자/게시)로 마이그레이션하는 방법을 알아봅니다."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" 데모 참조"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="자습서 - 컨텐츠 전송 도구 사용"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


이 섹션을 따라 컨텐츠 전송 도구를 사용하여 컨텐츠를 AEM as a Cloud Service(작성자/게시)에 마이그레이션하는 방법을 알아보십시오.

1. Adobe Experience Manager을 선택하고 도구 -> **작업** -> **컨텐츠 마이그레이션**&#x200B;으로 이동합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. **컨텐츠 마이그레이션** 마법사에서 **컨텐츠 전송** 옵션을 선택합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. 첫 번째 마이그레이션 세트를 만들면 아래 콘솔이 나타납니다. **마이그레이션 세트 만들기**&#x200B;를 클릭하여 새 마이그레이션 세트를 만듭니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >기존 마이그레이션 세트가 있는 경우 콘솔에 기존 마이그레이션 세트 목록이 현재 상태로 표시됩니다.


1. 아래 설명된 대로 **마이그레이션 세트 만들기** 화면의 필드를 채웁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt04.png)

   1. **이름**: 마이그레이션 세트의 이름을 입력합니다.
      >[!NOTE]
      >마이그레이션 세트 이름에는 특수 문자를 사용할 수 없습니다.

   1. **클라우드 서비스 구성**: 대상 AEM as a Cloud Service 작성자 URL로 입력합니다.

      >[!NOTE]
      >컨텐츠 전송 작업 중에 한 번에 최대 10개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
      >또한 특정 환경 - *단계*, *개발* 또는 *프로덕션*&#x200B;마다 개별적으로 마이그레이션을 만들어야 합니다.

   1. **액세스 토큰**: 액세스 토큰을 입력합니다.

      >[!NOTE]
      >**액세스 토큰 열기** 단추를 사용하여 액세스 토큰을 검색할 수 있습니다. Target Cloud Service 인스턴스의 AEM 관리자 그룹에 속해 있는지 확인해야 합니다.

   1. **매개 변수**: 다음 매개 변수를 선택하여 마이그레이션 세트를 만듭니다.

      1. **버전 포함**: 필요에 따라 선택합니다. 버전이 포함되면 감사 이벤트를 마이그레이션하기 위해 경로 `/var/audit`이 자동으로 포함됩니다.

      ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

      >[!NOTE]
      >마이그레이션 세트의 일부로 버전을 포함하되 `wipe=false` 을 사용하여 추가 작업을 수행하는 경우, 컨텐츠 전송 도구의 현재 제한 사항으로 인해 버전 제거를 비활성화해야 합니다. 버전 삭제를 사용하도록 유지하고 마이그레이션 세트에 추가 작업을 수행하려는 경우 수집을 `wipe=true`(으)로 수행해야 합니다.

      1. **IMS 사용자 및 그룹의 매핑 포함**: IMS 사용자 및 그룹의 매핑을 포함할 옵션을 선택합니다.
자세한 내용은 [사용자 매핑 도구](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html)를 참조하십시오.

      1. **포함할 경로**: 경로 브라우저를 사용하여 마이그레이션해야 하는 경로를 선택합니다. 경로 선택기는 입력 또는 선택 항목을 허용합니다.

         >[!IMPORTANT]
         >마이그레이션 세트를 만드는 동안 다음 경로가 제한됩니다.
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (일부  `/etc` 경로는 CTT에서 선택할 수 있음)




1. **마이그레이션 세트 만들기** 세부 정보 화면에서 모든 필드를 채운 후 **저장**&#x200B;을 클릭합니다.

1. 마이그레이션 세트는 *개요* 페이지에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   이 화면의 모든 기존 마이그레이션 세트가 현재 상태 및 상태 정보와 함께 *개요* 페이지에 표시됩니다. 아래에 설명된 이러한 아이콘 중 일부가 표시될 수 있습니다.

   * *빨간색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 없음을 나타냅니다.
   * *녹색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 있음을 나타냅니다.
   * *노란색 아이콘*&#x200B;은 기존 마이그레이션 세트를 만들지 않았으며, 특정 마이그레이션은 동일한 인스턴스에 있는 다른 사용자가 작성했음을 나타냅니다.

1. 개요 페이지에서 마이그레이션 세트를 선택하고 **속성**&#x200B;을 클릭하여 마이그레이션 세트 속성을 보거나 편집합니다. 속성을 편집하는 동안 컨테이너 이름 또는 서비스 URL을 변경할 수 없습니다.


### 컨텐츠 전송의 추출 프로세스 {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="컨텐츠 추출"
>abstract="추출이란 소스 AEM 인스턴스에서 마이그레이션 세트라는 임시 영역으로 컨텐츠를 추출하는 것입니다. 마이그레이션 세트는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 컨텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="추출 추가"

컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 단계를 따르십시오.
>[!NOTE]
>Amazon S3 또는 Azure 데이터 저장소가 데이터 저장소 유형으로 사용되는 경우 선택적 사전 복사 단계를 실행하여 추출 단계를 크게 단축할 수 있습니다. 이렇게 하려면 추출을 실행하기 전에 `azcopy.config` 파일을 구성해야 합니다. 자세한 내용은 [큰 컨텐츠 저장소 처리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 를 참조하십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **추출**&#x200B;을 클릭하여 추출을 시작합니다. **마이그레이션 세트 추출** 대화 상자가 표시되고 **추출**&#x200B;을 클릭하여 추출 단계를 시작합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >추출 단계 중에 스테이징 컨테이너를 덮어쓰는 옵션이 제공됩니다.


1. 이제 **EXTRACTION** 필드에 **RUNNING** 상태가 표시되어 추출이 진행 중임을 나타냅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   추출이 완료되면 마이그레이션 세트의 상태가 **완료됨**&#x200B;으로 업데이트되고 *녹색* 클라우드 아이콘이 **정보**&#x200B;필드 아래에 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >UI에는 30초마다 개요 페이지를 다시 로드하는 자동 재로드 기능이 있습니다.
   >추출 단계가 시작되면 *60초* 후 쓰기 잠금이 만들어지고 해제됩니다. 따라서 추출이 중지된 경우 다시 추출을 시작하기 전에 잠금이 해제될 때까지 잠시 기다려야 합니다.

#### 추가 추출 {#top-up-extraction-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.
>또한 기존 컨텐츠의 컨텐츠 구조는 초기 추출을 수행한 때부터 추가 추출을 실행할 때까지의 변경되지 않는 것이 중요합니다. 초기 추출 후 구조가 변경된 컨텐츠에서는 추가를 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

추출 프로세스가 완료되면 추가 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 추출을 수행할 마이그레이션 세트를 선택합니다. **추출**&#x200B;을 클릭하여 추가 추출을 시작합니다. **마이그레이션 세트 추출** 대화 상자가 표시됩니다.

   >[!IMPORTANT]
   >
   >**추출 중에 스테이징 컨테이너 덮어쓰기** 옵션을 비활성화해야 합니다.
   >
   >![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### 컨텐츠 전송의 수집 프로세스 {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="컨텐츠 수집"
>abstract="수집은 마이그레이션 세트 의 컨텐츠를 대상 Cloud Service 인스턴스로 수집하는 것입니다. 컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="추가 수집"

컨텐츠 전송 도구에서 마이그레이션 세트를 수집하려면 아래 단계를 따르십시오.
>[!NOTE]
>Amazon S3 또는 Azure Data Store가 데이터 저장소 유형으로 사용되는 경우 선택적 사전 복사 단계를 실행하여 수집 단계를 크게 단축할 수 있습니다. 자세한 내용은 [AzCopy를 사용하여 수집](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy)을 참조하십시오.

1. *개요* 페이지에서 마이그레이션 세트를 선택하고 **수집**&#x200B;을 클릭하여 수집을 시작합니다. **마이그레이션 세트 수집** 대화 상자가 표시됩니다. 컨텐츠를 한 번에 작성자 인스턴스 또는 게시 인스턴스에 수집할 수 있습니다. 컨텐츠를 수집할 인스턴스를 선택합니다. **수집**&#x200B;을 클릭하여 수집 단계를 시작합니다.

   >[!IMPORTANT]
   >사전 복사로 섭취를 사용하는 경우(S3 또는 Azure Data Store용) 먼저 작성자 수집만 실행하는 것이 좋습니다. 이 경우 나중에 실행될 때 게시 수집 속도가 빨라집니다.

   >[!IMPORTANT]
   >**수집** 옵션이 활성화되기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지우는 경우 기존 저장소 전체를 삭제하고 컨텐츠를 수집 할 새 저장소를 만듭니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. **administrators** 그룹에 추가된 관리자 사용자에게도 적용됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-03.png)

   또한 **고객 지원 센터**&#x200B;를 클릭하여 위의 그림과 같이 티켓을 기록합니다. 또한 자세한 내용은 [컨텐츠 전송 도구 사용에 대한 중요한 고려 사항](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs)을 참조하십시오.

1. 수집이 완료되면 상태가 **FINISHED**&#x200B;로 업데이트됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### 추가 수집 {#top-up-ingestion-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 *추가*&#x200B;를 지원하는 기능이 있습니다.

>[!NOTE]
>
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다.

수집 프로세스가 완료되면 추가 수집 방법을 사용하여 델타 컨텐츠를 사용할 수 있습니다. 아래 단계를 따르십시오.

1. *개요* 페이지로 이동하고 추가 수집을 수행할 마이그레이션 세트를 선택합니다. **수집**&#x200B;을 클릭하여 추가 추출을 시작합니다. **마이그레이션 세트 수집** 대화 상자가 표시됩니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >이전 수집 활동에서 기존 컨텐츠를 삭제하지 않으려면 먼저 클라우드 인스턴스에서 기존 컨텐츠를 지우는 **옵션을 비활성화해야 합니다.** 또한 **고객 지원 센터**&#x200B;를 클릭하여 이전 그림과 같이 티켓을 기록합니다.


### 마이그레이션 세트에 대한 로그 보기 {#viewing-logs-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="로그 보기"
>abstract="수집 추출이 완료되면 로그에서 오류/경고를 확인합니다. 오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="문제 해결"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Adobe 지원에 문의"

각 단계(추출 및 수집)가 완료되면 로그를 확인하고 오류를 찾습니다.  오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다.

*개요* 페이지에서 기존 마이그레이션 세트에 대한 로그를 볼 수 있습니다.
아래 단계를 따르십시오.

1. *개요* 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 **로그 보기**&#x200B;를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. **로그** 대화 상자가 표시됩니다. **추출 로그**&#x200B;를 클릭하여 새 탭에서 로그를 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
또는,

   *개요* 화면에서 마이그레이션 세트에 대한 로그를 볼 수도 있습니다. 마이그레이션 세트를 선택하고 **추출** 필드 아래에서 상태를 클릭합니다. 이 경우 **완료됨**&#x200B;을 클릭하여 새 탭에서 로그를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. 사용자 인터페이스를 사용하지 않고 로그를 추적하려면 소스 AEM 환경에 SSH를 사용하여 `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`를 추적할 수 있습니다.

### 마이그레이션 세트 삭제 {#deleting-migration-set}

*개요* 페이지에서 마이그레이션 세트를 삭제할 수 있습니다.
아래 단계를 따르십시오.

1. *개요* 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 **삭제**&#x200B;를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. **마이그레이션 세트 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭하여 삭제를 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)


## 게시 인스턴스에서 컨텐츠 전송 도구 실행 {#running-ctt-on-publish}

컨텐츠를 게시 인스턴스로 이동하는 동안 컨텐츠를 대상 게시 인스턴스로 이동하기 위해 CTT를 소스 게시 인스턴스에 설치하는 것이 좋습니다. 아래 설명된 대로 권장되는 방법을 따르십시오.

* 작성자 인스턴스에서 사용한 것과 동일한 버전의 CTT를 사용합니다.

* 단일 게시 노드만 마이그레이션해야 합니다. 추출 작업을 시작하기 전에 로드 밸런서에서 제거해야 합니다.

* 마이그레이션 세트를 만들 때 작성 AEMaaCS 환경의 URL을 사용합니다.

* 게시하기 위해 수집하는 동안 게시 계층의 크기가 조정되지 않습니다(작성자와 다름). 따라서 다음과 같은 쓰기 작업을 시작하지 마십시오.

   * AEM AaCS 작성자에서 해당 환경의 게시로 컨텐츠 배포
   * 게시 인스턴스 간 사용자 동기화


## 문제 해결 {#troubleshooting}

### Blob ID가 누락됨 {#missing-blobs}

아래에 언급했듯이 보고된 Blob ID가 누락된 경우 기존 저장소에서 일관성 검사를 실행하고 누락된 Blob를 복원해야 합니다.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

다음 명령이 실행됩니다.

>[!NOTE]
>
>`--verbose` 플래그는 BLOB을 참조하는 노드 경로를 보고하는 데 필요합니다.

**저장소 AEM 6.5(Oak 1.8 이하)의 경우**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Oak 1.10 이상이 있는 저장소의 경우**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

자세한 내용은 [Oak 실행 가능 Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)를 참조하십시오.

일관성을 위해 위에 지정된 *OUT_DIR*&#x200B;에 생성된 파일에서 경로에 바이너리가 누락되고, 백업에서 복원, 경로 삭제, 색인 재지정 등과 같은 적절한 조치를 취했는지 확인할 수 있습니다. 


### UI 동작 {#ui-behavior}

사용자는 컨텐츠 전송 도구에 대한 UI(사용자 인터페이스)에서 다음과 같은 동작 변경 사항을 볼 수 있습니다.

* 컨텐츠 전송 도구 UI의 아이콘이 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.
