---
title: 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례
description: 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: 5475f9995513d09e61bd8f52242b3e74b8d4694c
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 22%

---

# 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례 {#guidelines}

## 지침 및 모범 사례 {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.md#important-considerations" text="Important Considerations when Mapping and Migrating Users" 

-->

콘텐츠 전송 프로세스를 Cloud Acceleration Manager와 통합하는 콘텐츠 전송 도구의 새 버전이 제공됩니다. 이 새로운 버전으로 전환하여 제공되는 모든 이점을 활용하는 것이 좋습니다.

* 마이그레이션 세트를 한 번 추출하여 동시에 여러 환경에서 수집하는 셀프서비스 방식
* 효율적인 로딩 상태, 가드레일 및 오류 처리를 통해 개선된 사용자 경험
* 수집 로그는 유지되고 문제 해결에 항시 사용 가능합니다.

새 버전을 사용하려면 이전 버전의 컨텐츠 전송 도구를 제거해야 합니다. 이것은 새로운 버전이 주요한 아키텍처 변화와 함께 제공되기 때문에 필요합니다. 버전 2.x를 사용하면 새 마이그레이션 세트를 만들고 새 마이그레이션 세트에서 추출 및 수집을 다시 실행해야 합니다.
2.0.0 이전 버전은 더 이상 지원되지 않으며 최신 버전을 사용하는 것이 좋습니다.

다음 지침 및 우수 사례는 새 버전의 컨텐츠 전송 도구에 적용됩니다.

* 잠재적인 문제를 식별하고 저장소의 크기를 줄이기 위해 [소스](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 저장소에서 [수정 정리](https://helpx.adobe.com/kr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) 및 **데이터 저장소 일관성 검사**&#x200B;를 실행하는 것이 좋습니다.

* 수집 단계에서는 대상 AEM 클라우드 서비스 환경의 기존 저장소(작성자 또는 게시)가 완전히 삭제된 후 마이그레이션 세트 데이터로 업데이트되는 *지우기* 모드를 사용하여 수집을 실행하는 것이 좋습니다. 이 모드는 현재 컨텐츠 위에 마이그레이션 세트가 적용되는 지우지 않음 모드보다 훨씬 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 클라우드 서비스 환경에서 컨텐츠가 성공적으로 렌더링되도록 하려면 클라우드 서비스 환경에 올바른 프로젝트 구조가 필요합니다.

* 컨텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 `crx-quickstart` 하위 디렉토리에 디스크 공간이 충분한지 확인해야 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 사용 가능한 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
   `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉토리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.

* 컨텐츠 추가를 지원하려면 컨텐츠 전송 활동 전체에서 마이그레이션 세트를 유지 관리해야 합니다. Cloud Acceleration Manager에서는 컨텐츠 전송 활동 중에 한 번에 5개의 프로젝트당 최대 마이그레이션 세트를 만들고 유지 관리할 수 있습니다. 5개 이상의 마이그레이션 세트가 필요한 경우 Cloud Acceleration Manager에서 두 번째 프로젝트를 만들어야 합니다. 그러나 여러 사용자가 타겟 콘텐츠를 덮어쓰지 않도록 하려면 추가 프로젝트 관리 및 제품 외 거버넌스가 필요합니다.

## 컨텐츠 전송 도구를 사용하기 전에 고려해야 할 사항 {#important-considerations}

아래 섹션을 따라 수행하여 컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하십시오.

* 컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 JAVA 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드해야 컨텐츠 전송 도구를 사용할 수 있습니다.

* AEM 환경에서 Java를 구성해야 `java` 명령은 AEM을 시작하는 사용자가 실행할 수 있습니다.

* 컨텐츠 전송 도구는 다음 유형의 데이터 저장소와 함께 사용할 수 있습니다. 파일 데이터 저장소, S3 데이터 저장소, 공유 S3 데이터 저장소 및 Azure Blob 저장소 데이터 저장소.

* 를 사용 중인 경우 *샌드박스 환경*&#x200B;를 입력하여 환경이 최신 상태인지 확인하고 최신 릴리스로 업그레이드되었는지 확인하십시오. *프로덕션 환경*&#x200B;을 사용하는 경우 자동으로 업데이트됩니다.

* 수집을 시작하려면 로컬 AEM에 속해야 합니다 **관리자** 그룹에 속해 있어야 합니다. 권한이 없는 사용자는 마이그레이션 토큰을 수동으로 제공하지 않으면 작업을 시작할 수 없습니다.

* 설정이 **수집하기 전에 클라우드 인스턴스에서 기존 컨텐츠를 지웁니다.** 옵션이 활성화되면 기존 저장소 전체를 삭제하고 컨텐츠를 수집할 새 저장소를 만듭니다. 즉, Target Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정합니다. 또한 **관리자** 그룹에 속해 있어야 합니다. 사용자를 다시 **관리자** 그룹화하여 컨텐츠 전송 도구의 액세스 토큰을 검색합니다.

* 두 소스의 컨텐츠를 대상에서 동일한 경로로 이동하는 경우 수집 기능은 여러 소스의 컨텐츠를 타겟 Cloud Service 인스턴스로 병합하는 것을 지원하지 않습니다. 여러 소스의 컨텐츠를 단일 타겟 Cloud Service 인스턴스로 이동하려면 소스의 컨텐츠 경로가 겹치지 않도록 해야 합니다.

* 추출 키는 생성/갱신된 후 14일 동안 유효합니다. 언제든지 갱신할 수 있습니다. 추출 키가 만료된 경우에는 추출을 수행할 수 없습니다.

* 소스 인스턴스에서 대상 인스턴스로 컨텐츠를 전송하기 전에 CTT(컨텐츠 전송 도구)가 컨텐츠 분석을 수행하지 않습니다. 예를 들어 CTT는 컨텐츠를 게시 환경에 수집하는 동안 게시된 컨텐츠와 게시되지 않은 컨텐츠를 구분하지 않습니다. 마이그레이션 세트에 지정된 모든 콘텐츠는 선택한 대상 인스턴스로 수집됩니다. 사용자는 마이그레이션 세트를 작성자 인스턴스 또는 게시 인스턴스 또는 둘 다에 수집할 수 있습니다. 컨텐츠를 프로덕션 인스턴스로 이동하는 동안 컨텐츠를 타겟 작성자 인스턴스로 이동하도록 소스 작성자 인스턴스에 CTT를 설치하여 컨텐츠를 타겟 게시 인스턴스로 이동시키는 것이 좋습니다. 자세한 내용은 [게시 인스턴스에서 컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) 자세한 내용

* 컨텐츠 전송 도구에서 전송한 사용자 및 그룹은 컨텐츠에 의해 권한을 충족하기 위해 필요한 사용자 및 그룹에만 해당합니다. 다음 _추출_ 프로세스 전체 `/home` 마이그레이션 세트에 대해, 각 사용자의 이메일 주소에서 만든 필드를 추가하여 사용자 매핑을 수행합니다. 자세한 내용은 [사용자 매핑 및 보안 주체 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md). 다음 _수집_ 마이그레이션된 컨텐츠 ACL에서 참조되는 모든 사용자와 그룹을 복사합니다.

* 추출 단계 중에 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 을 완료한 후 *추출* 컨텐츠 전송 프로세스의 단계 및 시작하기 전 *수집 단계* AEM에 컨텐츠를 수집하려면 다음을 수행하십시오. as a Cloud Service *단계* 또는 *프로덕션* 인스턴스: 지원 티켓을 로그하여 Adobe에게 실행 의사를 알려야 합니다 *수집* Adobe이 *수집* 프로세스. 지원 티켓을 계획된 1주 전에 기록해야 합니다 *수집* 날짜. 지원 티켓을 제출하면 지원 팀이 다음 단계에 대한 지침을 제공합니다. 다음 세부 정보로 지원 티켓을 기록할 수 있습니다.

   * 을(를) 시작할 예정인 정확한 날짜 및 예상 시간(시간대와 함께) *수집* 단계.
   * 데이터를 수집할 환경 유형(스테이지 또는 프로덕션)입니다.
   * 프로그램 ID.

* 다음 *수집 단계* 작성자의 경우 전체 작성자 배포를 축소합니다. 즉, 전체 수집 프로세스 중에 작성자 AEM을 사용할 수 없습니다. 또한 를 실행하는 동안 Cloud Manager 파이프라인이 실행되지 않는지 확인하십시오 *수집* 단계.

* 사용 시 `Amazon S3` 또는 `Azure` 소스 AEM 시스템의 데이터 저장소는 저장된 BLOB을 삭제할 수 없도록 구성해야 합니다(가비지 수집). 이렇게 하면 인덱스 데이터의 무결성이 보장되고 이러한 방법을 구성하지 않으면 이 인덱스 데이터의 무결성으로 인해 추출에 실패할 수 있습니다.

* 사용자 지정 인덱스를 사용하는 경우 `tika` 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 노드 아래에 있는 URL을 무시합니다. 을(를) 참조하십시오. [새 인덱스 정의 준비](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html#preparing-the-new-index-definition) 자세한 내용

* 추가 작업을 하려면 초기 추출을 수행할 때부터 추가 추출을 실행할 때까지의 기존 컨텐츠의 컨텐츠 구조가 변경되지 않는 것이 중요합니다. 초기 추출 후 구조가 변경된 컨텐츠에서는 추가를 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

* 마이그레이션 세트의 일부로 버전을 포함하려 하며 다음 방법으로 추가 작업을 수행하는 경우 `wipe=false`를 입력한 다음 컨텐츠 전송 도구의 현재 제한으로 인해 버전 제거를 비활성화해야 합니다. 버전 삭제를 활성화한 상태로 유지하고 마이그레이션 세트에 대한 추가 작업을 수행하려는 경우 수집을 다음으로 수행해야 합니다 `wipe=true`.

* 마이그레이션 세트 는 장기간 동안 활동이 없으면 만료되며, 해당 데이터는 더 이상 사용할 수 없습니다. 검토하세요 [마이그레이션 세트 만료](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html#migration-set-expiry) 자세한 내용

## 다음 단계 {#whats-next}

컨텐츠 전송 도구 사용에 대한 지침, 우수 사례 및 중요한 고려 사항을 알게 되면 이제 마이그레이션 세트 생성부터 도구를 설치하고 사용할 준비가 되었습니다. 자세한 내용은 [컨텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) 추가 정보
