---
title: 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례
description: 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례
source-git-commit: fa7e5d07ed52a71999de95bbf6299ae5eb7af537
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 25%

---


# 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례 {#guidelines}

## 지침 및 우수 사례 {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="지침 및 우수 사례"
>abstract="수정 정리 작업, 디스크 공간 고려 사항 등을 비롯하여 컨텐츠 전송 도구를 사용하기 위한 지침과 모범 사례를 검토하십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="컨텐츠 전송 도구 사용에 대한 중요한 고려 사항"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="사용자 매핑 도구 사용에 대한 중요한 고려 사항"

컨텐츠 전송 도구를 사용하기 위한 지침과 우수 사례를 이해하려면 아래 섹션을 따르십시오.

* 잠재적인 문제를 식별하고 저장소의 크기를 줄이기 위해 [소스](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 저장소에서 [수정 정리](https://helpx.adobe.com/kr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) 및 **데이터 저장소 일관성 검사**&#x200B;를 실행하는 것이 좋습니다.

* AEM 클라우드 작성자 CDN(Content Delivery Network) 구성이 IP의 허용 목록을 포함하도록 구성된 경우 소스 환경과 AEM 클라우드 환경이 서로 통신할 수 있도록 소스 환경 IP가 허용 목록에도 추가되도록 해야 합니다.

* 수집 단계에서는 대상 AEM 클라우드 서비스 환경의 기존 저장소(작성자 또는 게시)가 완전히 삭제된 후 마이그레이션 세트 데이터로 업데이트되는 *지우기* 모드를 사용하여 수집을 실행하는 것이 좋습니다. 이 모드는 현재 컨텐츠 위에 마이그레이션 세트가 적용되는 지우지 않음 모드보다 훨씬 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 클라우드 서비스 환경에서 컨텐츠가 성공적으로 렌더링되도록 하려면 클라우드 서비스 환경에 올바른 프로젝트 구조가 필요합니다.

* 컨텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 `crx-quickstart` 하위 디렉토리에 디스크 공간이 충분한지 확인해야 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 여유 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
   `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉토리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.

* 컨텐츠 추가를 지원하려면 컨텐츠 전송 활동 전체에서 마이그레이션 세트를 유지 관리해야 합니다. 컨텐츠 전송 작업 중에 한 번에 최대 10개의 마이그레이션 세트를 만들고 유지 관리할 수 있으므로 마이그레이션 세트가 부족하지 않도록 컨텐츠 저장소를 그에 따라 분류하는 것이 좋습니다.

## 컨텐츠 전송 도구를 사용하기 전에 고려해야 할 사항 {#important-considerations}

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

## 다음은 무엇입니까? {#whats-next}

컨텐츠 전송 도구 사용에 대한 지침, 우수 사례 및 중요한 고려 사항을 알게 되면 이제 마이그레이션 세트 생성부터 도구를 설치하고 사용할 준비가 되었습니다. 자세한 내용은 [컨텐츠 전송 도구 시작하기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en)를 참조하십시오.
