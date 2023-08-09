---
title: 컨텐츠 전송 도구 사용을 위한 지침 및 우수 사례
description: 컨텐츠 전송 도구 사용을 위한 지침 및 우수 사례
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: 83c6c3c8c069059e49b632f332e24946e1712cb7
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 19%

---

# 컨텐츠 전송 도구 사용을 위한 지침 및 우수 사례 {#guidelines}

## 지침 및 모범 사례 {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.md#important-considerations" text="Important Considerations when Mapping and Migrating Users" 

-->

콘텐츠 전송 프로세스를 Cloud Acceleration Manager와 통합하는 콘텐츠 전송 도구의 새 버전이 제공됩니다. 이 새 버전으로 전환하여 제공되는 모든 이점을 사용하는 것이 좋습니다.

* 마이그레이션 세트를 한 번 추출하여 동시에 여러 환경에서 수집하는 셀프서비스 방식
* 효율적인 로딩 상태, 가드레일 및 오류 처리를 통해 개선된 사용자 경험
* 수집 로그는 유지되고 문제 해결에 항시 사용 가능합니다.

새 버전을 사용하려면 이전 버전의 콘텐츠 전송 도구를 제거해야 합니다. 새로운 버전은 주요 아키텍처 변경과 함께 제공되기 때문에 필요합니다. 버전 2.x에서는 새 마이그레이션 세트를 만들고 새 마이그레이션 세트에서 추출 및 수집을 다시 실행해야 합니다.
2.0.0 이전 버전은 더 이상 지원되지 않으며 최신 버전을 사용하는 것이 좋습니다.

다음 지침 및 모범 사례는 새 버전의 콘텐츠 전송 도구에 적용됩니다.

* 잠재적인 문제를 식별하고 저장소의 크기를 줄이기 위해 [소스](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 저장소에서 [수정 정리](https://helpx.adobe.com/kr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) 및 **데이터 저장소 일관성 검사**&#x200B;를 실행하는 것이 좋습니다.

* 수집 단계에서는 다음을 사용하여 수집을 실행하는 것이 좋습니다. *지우기* 대상 AEM Cloud Service 환경의 기존 저장소(작성자 또는 게시)가 완전히 삭제된 후 마이그레이션 세트 데이터로 업데이트되는 모드가 활성화됩니다. 이 모드는 현재 컨텐츠 위에 마이그레이션 세트가 적용되는 지우지 않음 모드보다 훨씬 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 클라우드 서비스 환경에서 컨텐츠가 성공적으로 렌더링되도록 하려면 클라우드 서비스 환경에 올바른 프로젝트 구조가 필요합니다.

* 컨텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 `crx-quickstart` 하위 디렉토리에 디스크 공간이 충분한지 확인해야 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 여유 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
  `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉토리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.

* 콘텐츠 추가를 지원하려면 콘텐츠 전송 작업 전반에 걸쳐 마이그레이션 세트를 유지 관리해야 합니다. Cloud Acceleration Manager에서는 프로젝트당 최대 5개의 마이그레이션 세트를 컨텐츠 전송 작업 중에 한 번에 만들고 유지 관리할 수 있습니다. 5개 이상의 마이그레이션 세트가 필요한 경우 Cloud Acceleration Manager에서 두 번째 프로젝트를 만들어야 합니다. 그러나 이를 위해서는 여러 사용자가 타겟의 콘텐츠를 덮어쓰는 것을 방지하기 위해 추가적인 프로젝트 관리 및 제품 외 거버넌스가 필요합니다.

## 컨텐츠 전송 도구 사용 전 중요 고려 사항 {#important-considerations}

아래 섹션을 따라 수행하여 컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하십시오.

* 컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드해야 컨텐츠 전송 도구를 사용할 수 있습니다.

* AEM 환경에서 Java를 구성해야 합니다. `java` AEM을 시작하는 사용자가 명령을 실행할 수 있습니다.

* 컨텐츠 전송 도구는 파일 데이터 저장소, S3 데이터 저장소, 공유 S3 데이터 저장소 및 Azure Blob 저장소 데이터 저장소 유형과 함께 사용할 수 있습니다.

* 를 사용하는 경우 *샌드박스 환경*, 환경이 최신 상태이고 최신 릴리스로 업그레이드되었는지 확인하십시오. *프로덕션 환경*&#x200B;을 사용하는 경우 자동으로 업데이트됩니다.

* 수집을 시작하려면 로컬 AEM에 속해야 합니다 **관리자** 컨텐츠를 전송하는 Cloud Service 인스턴스의 그룹입니다. 권한이 없는 사용자는 마이그레이션 토큰을 수동으로 제공하지 않으면 수집을 시작할 수 없습니다.

* 다음과 같은 경우 **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 이 옵션을 활성화하면 기존 저장소 전체가 삭제되고 컨텐츠를 수집할 새 저장소가 만들어집니다. 즉, 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정이 재설정됩니다. 에 추가된 관리자 사용자에게도 마찬가지입니다. **관리자** 그룹입니다. 사용자를 다음에 다시 추가해야 합니다 **관리자** 그룹 을 클릭하여 콘텐츠 전송 도구에 대한 액세스 토큰을 검색합니다.

* 두 소스의 콘텐츠가 타겟의 동일한 경로로 이동되는 경우, 수집은 여러 소스의 콘텐츠를 타겟 Cloud Service 인스턴스로 병합하는 것을 지원하지 않습니다. 여러 소스의 콘텐츠를 단일 대상 Cloud Service 인스턴스로 이동하려면 소스에서 콘텐츠 경로가 겹치지 않도록 해야 합니다.

* 추출 키는 생성/갱신된 시점부터 14일 동안 유효합니다. 언제든지 갱신할 수 있습니다. 추출 키가 만료된 경우 추출을 수행할 수 없습니다.

* CTT(컨텐츠 전송 도구)는 소스 인스턴스에서 대상 인스턴스로 컨텐츠를 전송하기 전에 어떠한 종류의 컨텐츠 분석도 수행하지 않습니다. 예를 들어 CTT는 컨텐츠를 게시 환경에 수집하는 동안 게시된 컨텐츠와 게시되지 않은 컨텐츠를 구분하지 않습니다. 마이그레이션 세트에 지정된 모든 콘텐츠는 선택한 대상 인스턴스로 수집됩니다. 사용자는 마이그레이션 세트를 작성자 인스턴스나 게시 인스턴스 또는 둘 다로 수집할 수 있습니다. 프로덕션 인스턴스로 콘텐츠를 이동하는 동안 소스 작성자 인스턴스에 CTT를 설치하여 콘텐츠를 타겟 작성자 인스턴스로 이동하고, 마찬가지로 소스 게시 인스턴스에 CTT를 설치하여 콘텐츠를 타겟 게시 인스턴스로 이동하는 것이 좋습니다. 다음을 참조하십시오 [게시 인스턴스에서 컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) 을 참조하십시오.

* 컨텐츠 전송 도구에서 전송한 사용자 및 그룹은 컨텐츠에서 권한을 충족하기 위해 필요한 사용자 및 그룹입니다. 다음 _추출_ 전체 복사 처리 `/home` 마이그레이션 세트에 추가되고 각 사용자의 이메일 주소에서 만든 필드를 추가하여 사용자 매핑을 수행합니다. 자세한 내용은 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md). 다음 _수집_ 프로세스는 마이그레이션된 콘텐츠 ACL에서 참조된 모든 사용자 및 그룹을 복사합니다. 다음을 참조하십시오 [폐쇄된 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) CUG(폐쇄형 사용자 그룹) 정책에 사용된 그룹에 대한 추가 고려 사항.

* 추출 단계 중에 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 완료 후 *추출* 컨텐츠 전송 프로세스의 단계 및 시작 전 *수집 단계* 컨텐츠를 AEM as a Cloud Service으로 수집 *단계* 또는 *프로덕션* 인스턴스: 지원 티켓을 로그하여 Adobe에게 실행 의도를 알려야 합니다 *수집* 따라서 Adobe이 작업 중에 중단이 발생하지 않도록 *수집* 프로세스. 1주일 전에 지원 티켓을 기록해야 합니다. *수집* 날짜. 지원 티켓을 제출한 후 지원 팀에서 다음 단계에 대한 지침을 제공합니다. 다음 세부 정보로 지원 티켓을 기록할 수 있습니다.

   * 다음을 시작할 정확한 날짜 및 예상 시간(표준 시간대 포함) *수집* 단계.
   * 데이터를 수집할 환경 유형(스테이지 또는 프로덕션).
   * 프로그램 ID.

* 다음 *수집 단계* 작성자는 전체 작성자 배포를 축소합니다. 즉, 전체 수집 프로세스 중에는 작성자 AEM을 사용할 수 없습니다. 또한 를 실행하는 동안 Cloud Manager 파이프라인이 실행되지 않도록 하십시오. *수집* 단계.

* 사용 시 `Amazon S3` 또는 `Azure` 소스 AEM 시스템의 데이터 저장소로, 저장된 블롭을 삭제(가비지 수집)할 수 없도록 데이터 저장소를 구성해야 합니다. 이렇게 하면 인덱스 데이터의 무결성이 보장되며 이러한 방식을 구성하지 않으면 인덱스 데이터의 무결성이 부족하여 추출에 실패할 수 있습니다.

* 사용자 지정 색인을 사용하는 경우 다음을 사용하여 사용자 지정 색인을 구성해야 합니다 `tika` 컨텐츠 전송 도구를 실행하기 전의 노드입니다. 다음을 참조하십시오 [새 색인 정의 준비](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html#preparing-the-new-index-definition) 을 참조하십시오.

* 추가 추출을 하려는 경우 기존 콘텐츠의 콘텐츠 구조를 초기 추출 시점부터 추가 추출을 실행할 때까지 변경하지 않는 것이 중요합니다. 초기 추출 이후 구조가 변경된 콘텐츠에서는 추가 작업을 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

* 버전을 마이그레이션 세트의 일부로 포함하려는 경우 다음을 사용하여 추가 작업을 수행합니다 `wipe=false`, 콘텐츠 전송 도구의 현재 제한으로 인해 버전 지우기를 비활성화해야 합니다. 버전 삭제를 활성화하고 마이그레이션 세트에 대해 추가 작업을 수행하는 경우 수집 작업을 다음과 같이 수행해야 합니다. `wipe=true`.

* 오랫동안 사용하지 않으면 마이그레이션 세트가 만료되며 그 이후에는 데이터를 더 이상 사용할 수 없습니다. 리뷰 [마이그레이션 세트 만료](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html#migration-set-expiry) 을 참조하십시오.

## 다음 단계 {#whats-next}

지침, 모범 사례 및 컨텐츠 전송 도구 사용에 대한 중요한 고려 사항을 학습하면 이제 마이그레이션 세트 생성부터 시작하여 도구를 설치하고 사용할 준비가 된 것입니다. 다음을 참조하십시오 [컨텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) 자세히 알아보십시오.
