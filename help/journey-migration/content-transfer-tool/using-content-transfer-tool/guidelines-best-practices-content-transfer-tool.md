---
title: 컨텐츠 전송 도구 사용에 대한 지침 및 우수 사례
description: 콘텐츠 전송 도구 사용에 대한 지침과 모범 사례에 대해 알아봅니다.
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 15%

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
* 로드 상태, 보호 및 오류 처리를 개선하여 사용자 경험 개선
* 수집 로그는 유지되고 문제 해결에 항시 사용 가능합니다.

새 버전을 사용하려면 이전 버전의 콘텐츠 전송 도구를 제거합니다. 새로운 버전은 주요 아키텍처 변경과 함께 제공되기 때문에 필요합니다. 버전 2.x에서는 마이그레이션 세트를 만들고 세트에서 추출 및 수집을 다시 실행합니다.
2.0.0 이전 버전은 지원되지 않으며 최신 버전을 사용하는 것이 좋습니다.

다음 지침 및 모범 사례는 새 버전의 콘텐츠 전송 도구에 적용됩니다.

* 잠재적인 문제를 식별하고 저장소의 크기를 줄일 수 있도록 **원본** 저장소에서 [수정 정리](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) 및 [데이터 저장소 일관성 검사](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html)를 실행하십시오.

* Adobe 수집 단계에서는 대상 Adobe Experience Manager(AEM) Cloud Service 환경의 기존 저장소(작성자 또는 게시)가 삭제되는 *지우기* 모드를 사용하여 수집을 실행하는 것이 좋습니다. 그런 다음 마이그레이션 세트 데이터로 업데이트합니다. 이 모드는 현재 콘텐츠 위에 마이그레이션 세트가 적용되는 지우지 않음 모드보다 빠릅니다.

* 컨텐츠 전송 활동이 완료되면 클라우드 서비스 환경에서 컨텐츠가 성공적으로 렌더링되도록 하려면 클라우드 서비스 환경에 올바른 프로젝트 구조가 필요합니다.

* 컨텐츠 전송 도구를 실행하기 전에 소스 AEM 인스턴스의 `crx-quickstart` 하위 디렉토리에 디스크 공간이 충분한지 확인해야 합니다. 이는 컨텐츠 전송 도구가 나중에 마이그레이션 세트에 업로드된 저장소의 로컬 복사본을 만들기 때문입니다.
필요한 여유 디스크 공간을 계산하는 일반 공식은 다음과 같습니다.
  `data store size + node store size * 1.5`

   * *데이터 저장소 크기*: 컨텐츠 전송 도구는 실제 데이터 저장소가 더 큰 경우에도 64GB를 사용합니다.
   * *노드 저장소 크기*: 세그먼트 저장소 디렉토리 크기 또는 MongoDB 데이터베이스 크기입니다.
따라서 세그먼트 저장소 크기가 20GB인 경우 필요한 여유 디스크 공간은 94GB입니다.

* 콘텐츠 추가를 지원하려면 콘텐츠 전송 작업 전반에 걸쳐 마이그레이션 세트를 유지 관리해야 합니다. Cloud Acceleration Manager에서 프로젝트당 최대 20개의 마이그레이션 세트를 만들고 컨텐츠 전송 활동 중에 유지 관리할 수 있습니다. 마이그레이션 세트가 20개 이상 필요한 경우 Cloud Acceleration Manager에서 두 번째 프로젝트를 만듭니다. 그러나 이를 위해서는 여러 사용자가 타겟의 콘텐츠를 덮어쓰는 것을 방지하기 위해 추가적인 프로젝트 관리 및 제품 외 거버넌스가 필요합니다.

* CTT 도구의 설치 디렉토리를 변경하지 마십시오. 기본적으로 설치는 crx-quickstart/cloud-migration 경로에서 수행됩니다. 이 특정 위치는 다른 라이브러리에서 내부적으로 사용됩니다. 이 경로를 수정하면 추출 문제가 발생할 수 있습니다.

## 컨텐츠 전송 도구 사용 전 중요 고려 사항 {#important-considerations}

아래 섹션을 따라 수행하여 컨텐츠 전송 도구를 실행하는 동안 중요한 고려 사항을 이해하십시오.

* 컨텐츠 전송 도구의 최소 시스템 요구 사항은 AEM 6.3 이상 및 Java™ 8입니다. 더 낮은 AEM 버전을 사용하는 경우 컨텐츠 저장소를 AEM 6.5로 업그레이드하여 컨텐츠 전송 도구를 사용하십시오.

* AEM을 시작하는 사용자가 `java` 명령을 실행할 수 있도록 AEM 환경에서 Java™을 구성해야 합니다.

* 컨텐츠 전송 도구는 파일 데이터 저장소, S3 데이터 저장소, 공유 S3 데이터 저장소 및 Azure Blob 저장소 데이터 저장소 유형과 함께 사용할 수 있습니다.

* *샌드박스 환경*&#x200B;을(를) 사용하는 경우 환경이 최신이고 최신 릴리스로 업그레이드되었는지 확인하십시오. *프로덕션 환경*&#x200B;을 사용하는 경우 자동으로 업데이트됩니다.

* 수집을 시작하려면 콘텐츠를 전송할 Cloud Service 인스턴스의 로컬 AEM **관리자** 그룹에 속해 있어야 합니다. 권한이 없는 사용자는 수동으로 마이그레이션 토큰을 제공하지 않으면 수집을 시작할 수 없습니다.

* **수집하기 전에 클라우드 인스턴스에서 기존 콘텐츠 지우기** 옵션을 사용하도록 설정한 경우 전체 기존 저장소를 삭제하고 콘텐츠를 수집할 새 저장소를 만듭니다. 즉, 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정이 재설정됩니다. **관리자** 그룹에 추가된 관리자 사용자도 마찬가지입니다. 콘텐츠 전송 도구에 대한 액세스 토큰을 검색하려면 **관리자** 그룹에 대한 사용자 권한이 있어야 합니다.

* 두 소스의 콘텐츠가 타겟의 동일한 경로로 이동되는 경우, 수집은 여러 소스의 콘텐츠를 타겟 Cloud Service 인스턴스로 병합하는 것을 지원하지 않습니다. 여러 소스의 콘텐츠를 단일 타겟 Cloud Service 인스턴스로 이동하려면 소스의 콘텐츠 경로가 겹치지 않도록 하십시오.

* 추출 키를 만들거나 갱신한 시점부터 14일 동안 유효합니다. 언제든지 갱신할 수 있습니다. 추출 키가 만료된 경우 추출을 수행할 수 없습니다.

* CTT(컨텐츠 전송 도구)는 소스 인스턴스에서 대상 인스턴스로 컨텐츠를 전송하기 전에 어떠한 종류의 컨텐츠 분석도 수행하지 않습니다. 예를 들어 CTT는 컨텐츠를 Publish 환경으로 수집하는 동안 게시된 컨텐츠와 게시되지 않은 컨텐츠를 구분하지 않습니다. 마이그레이션 세트에 지정된 모든 콘텐츠는 선택한 대상 인스턴스로 수집됩니다. 사용자는 마이그레이션 세트를 작성자 인스턴스 또는 Publish 인스턴스 또는 둘 다로 수집할 수 있습니다. Adobe은 컨텐츠를 프로덕션 인스턴스로 이동하는 동안 소스 작성자 인스턴스에 CTT를 설치하여 컨텐츠를 타겟 작성자 인스턴스로 이동하는 것을 권장합니다. 마찬가지로 소스 Publish 인스턴스에 CTT를 설치하여 컨텐츠를 대상 Publish 인스턴스로 이동합니다. 자세한 내용은 [Publish 인스턴스에서 컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool)을 참조하십시오.

* 컨텐츠 전송 도구에서 전송한 사용자 및 그룹은 컨텐츠에서 권한을 충족하기 위해 필요한 사용자 및 그룹입니다. _추출_ 프로세스는 전체 `/home`을(를) 마이그레이션 세트에 복사하고 각 사용자의 전자 메일 주소에서 만든 필드를 추가하여 사용자 매핑을 수행합니다. 자세한 내용은 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md)을 참조하십시오. _수집_ 프로세스는 마이그레이션된 콘텐츠 ACL에서 참조된 모든 사용자 및 그룹을 복사합니다. CUG(폐쇄형 사용자 그룹) 정책에 사용된 그룹에 대한 추가 고려 사항은 [폐쇄형 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md)을 참조하십시오.

* 추출 단계 중에 컨텐츠 전송 도구는 활성 AEM 소스 인스턴스에서 실행됩니다.

* 작성자의 *수집 단계*&#x200B;는 전체 작성자 배포를 축소합니다. 즉, 전체 수집 프로세스 중에는 작성자 AEM을 사용할 수 없습니다. 또한 *수집* 단계를 실행하는 동안에는 Cloud Manager 파이프라인이 실행되지 않아야 합니다.

* 소스 AEM 시스템에서 `Amazon S3` 또는 `Azure`을(를) 데이터 저장소로 사용하는 경우 저장된 Blob을 삭제(가비지 수집)할 수 없도록 데이터 저장소를 구성해야 합니다. 이렇게 하면 인덱스 데이터의 무결성이 보장되며 이러한 방식을 구성하지 않으면 인덱스 데이터의 무결성이 부족하여 추출에 실패할 수 있습니다.

* 사용자 지정 색인을 사용하는 경우 콘텐츠 전송 도구를 실행하기 전에 `tika` 노드를 사용하여 사용자 지정 색인을 구성해야 합니다. 자세한 내용은 [새 색인 정의 준비](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#preparing-the-new-index-definition)를 참조하십시오.

* 추가 추출을 하려는 경우 기존 콘텐츠의 콘텐츠 구조는 초기 추출을 하는 시점부터 추가 추출을 실행할 때까지 변경되지 않아야 합니다. 초기 추출 이후 구조가 변경된 콘텐츠에서는 추가 작업을 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

* 버전을 마이그레이션 세트의 일부로 포함하고 `wipe=false`을(를) 사용하여 추가 작업을 수행하는 경우 콘텐츠 전송 도구의 현재 제한으로 인해 버전 삭제를 비활성화해야 합니다. 버전 삭제를 활성화하고 마이그레이션 세트에 대한 추가를 수행하는 경우 `wipe=true`(으)로 수집을 수행해야 합니다.

* 마이그레이션 세트는 장기간 사용하지 않으면 만료되며 그 이후에는 데이터를 더 이상 사용할 수 없습니다. 자세한 내용은 [마이그레이션 세트 만료](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html#migration-set-expiry)를 검토하십시오.

## 다음 단계 {#whats-next}

지침, 모범 사례 및 컨텐츠 전송 도구 사용에 대한 중요한 고려 사항을 학습하면 이제 마이그레이션 세트 생성부터 시작하여 도구를 설치하고 사용할 준비가 된 것입니다. [콘텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md)를 참조하세요.
