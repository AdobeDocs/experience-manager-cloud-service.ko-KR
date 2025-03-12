---
title: 그룹 마이그레이션
description: AEM as a Cloud Service의 그룹 마이그레이션 개요.
exl-id: 4a35fc46-f641-46a4-b3ff-080d090c593b
source-git-commit: c3a13f75757a478996918c6868a172d75158aafe
workflow-type: tm+mt
source-wordcount: '1914'
ht-degree: 3%

---


# 그룹 마이그레이션 {#group-migration}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_groupmigration"
>title="그룹 마이그레이션"
>abstract="콘텐츠 전송 도구는 그룹을 기존 AEM(Adobe Experience Manager) 시스템에서 AEM as a Cloud Service로 복사하는 데 유용합니다."

>[!NOTE]
>이전 버전의 사용자 매핑 도구에 대해서는 [레거시 설명서](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md)를 참조하십시오.

## 소개 {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermigration"
>title="사용자는 마이그레이션되지 않습니다."
>abstract="콘텐츠 전송 도구는 더 이상 사용자를 마이그레이션하지 않습니다. 사용자는 Admin Console에서 관리해야 합니다."
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="AEM Admin Console 설명서"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

Adobe Experience Manager(AEM) as a Cloud Service으로 전환 여정의 일부로 기존 AEM 시스템에서 AEM as a Cloud Service으로 그룹을 마이그레이션해야 합니다. 이 작업은 콘텐츠 전송 도구에서 수행합니다.

AEM as a Cloud Service의 주요 변경 사항은 작성자 계층 액세스에 대한 Adobe ID의 완전히 통합된 사용입니다. 이 프로세스에서는 사용자 및 사용자 그룹을 관리하기 위해 [Adobe Admin Console](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)을(를) 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 단일 사인온을 제공하는 Adobe Identity Management System(IMS)에서 중앙 집중화됩니다. 자세한 내용은 [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html#identity-management)을 참조하세요. 이러한 변경 사항으로 인해 사용자가 IMS를 통해 처음 로그인할 때 AEM에 자동으로 생성됩니다.  따라서 CTT는 사용자를 클라우드 시스템으로 마이그레이션하지 않습니다.  IMS 사용자는 IMS 그룹에 넣어야 합니다. IMS 그룹은 마이그레이션되는 그룹 또는 마이그레이션되는 AEM 콘텐츠에 액세스할 수 있는 권한이 주어진 AEM 그룹에 있는 새 그룹으로 이동할 수 있습니다.  이 방법으로 클라우드 시스템의 사용자는 소스 AEM 시스템에서 보유했던 동일한 액세스 권한을 갖게 됩니다.

## 그룹 마이그레이션 세부 정보 {#group-migration-detail}

컨텐츠 전송 도구 및 Cloud Acceleration Manager은 마이그레이션 중인 컨텐츠와 관련된 모든 그룹을 클라우드 시스템으로 마이그레이션합니다. 컨텐츠 전송 도구는 추출 프로세스 중에 소스 AEM 시스템의 모든 그룹을 복사하여 이 작업을 수행합니다. 그런 다음 CAM 수집은 특정 그룹만 선택하고 마이그레이션합니다.

* 그룹이 마이그레이션된 컨텐츠의 ACL 또는 CUG 정책에 있는 경우 아래 나열된 몇 가지 예외를 제외하고 해당 그룹이 마이그레이션됩니다.
* 내장되어 있으며 이미 타겟 클라우드 시스템에 있는 여러 그룹이 있습니다. 이러한 그룹은 마이그레이션되지 않습니다.
   * 일부 기본 제공 그룹에는 _not_ 기본 제공 구성원 그룹이 포함될 수 있습니다. 마이그레이션된 콘텐츠의 ACL 또는 CUG 정책에서 참조되는 이러한 구성원 그룹(직접 구성원 또는 구성원 등)은 마이그레이션되어 이러한 그룹의 구성원인 사용자가 직접 또는 간접적으로 마이그레이션된 콘텐츠에 대한 액세스 권한을 유지할 수 있습니다.
* ACL 또는 CUG 정책에서 찾을 수 없는 그룹, 대상 시스템에 이미 있는 그룹 및 대상 시스템에 이미 고유성이 제한된 데이터가 있는 그룹과 같은 다른 그룹은 마이그레이션되지 않습니다.

그룹에 대해 기록/보고된 경로는 해당 그룹을 마이그레이션하도록 트리거한 첫 번째 경로일 뿐이며 해당 그룹은 다른 콘텐츠 경로에 있을 수도 있습니다.

마이그레이션된 대부분의 그룹은 IMS에서 관리하도록 구성됩니다.  즉, IMS의 동일한 이름 그룹은 AEM의 그룹에 연결되고, IMS 그룹의 모든 IMS 사용자는 AEM 사용자 및 AEM의 그룹 구성원이 됩니다.  이를 통해 해당 사용자는 그룹에 대한 ACL 또는 CUG 정책에 따라 콘텐츠에 액세스할 수 있습니다.

마이그레이션된 그룹은 더 이상 AEM &quot;로컬 그룹&quot;으로 간주되지 않습니다. IMS에 아직 존재하지 않을 수 있지만 AEM에서는 IMS에 준비된 그룹입니다.  AEM과 IMS 간에 동기화할 수 있도록 IMS에서 별도로 다시 만들어야 합니다.  그룹은 다른 방법 중에서도 Admin Console을 통해 개별적으로 또는 대량으로 IMS에서 만들 수 있습니다.  Admin Console에서 개별적으로 또는 대량으로 그룹을 만드는 방법에 대한 자세한 내용은 [사용자 그룹 관리](https://helpx.adobe.com/kr/enterprise/using/user-groups.html)를 참조하십시오.

이 IMS 구성에 대한 예외는 Assets 컬렉션에서 만든 그룹에 있습니다. AEM에서 컬렉션을 만들면 해당 컬렉션에 액세스하기 위한 그룹이 만들어집니다. 이러한 그룹은 클라우드 시스템으로 마이그레이션되지만 IMS에서 관리되도록 구성되지 않습니다.  이러한 그룹에 IMS 사용자를 추가하려면 Assets UI의 그룹 속성 페이지에서 개별적으로 또는 집합적으로 다른 IMS 그룹의 일부로 추가해야 합니다.


## 그룹 마이그레이션 옵트아웃 {#group-migration-option}

CTT 버전 3.0.20 이상에는 그룹 마이그레이션을 비활성화하는 옵션이 포함되어 있습니다.  이는 다음과 같이 OSGI 콘솔에서 구성됩니다.

* OSGI 구성 `(http://<server>/system/console/configMgr)` 열기
* **콘텐츠 전송 도구 추출 서비스 구성**&#x200B;이라는 구성을 클릭합니다.
* 그룹 마이그레이션을 비활성화하려면 **마이그레이션에 그룹 포함**&#x200B;을 선택 취소합니다.
* **저장**&#x200B;을 클릭하여 구성이 서버에 저장되고 활성 상태인지 확인하세요.

이 설정을 사용하지 않으면 그룹이 마이그레이션되지 않고 사용자 마이그레이션 보고서와 사용자 보고서가 없습니다(아래 참조).

## 사용자 마이그레이션 보고서 및 사용자 보고서 {#principal-migration-report}

마이그레이션 도중 그룹이 포함된 경우(기본값), 마이그레이션 도중 각 그룹에 발생하는 상황을 요약한 사용자 마이그레이션 보고서가 저장됩니다.  수집 성공 후 이 보고서를 다운로드하려면 다음 작업을 수행하십시오.
* CAM에서 컨텐츠 전송으로 이동한 다음 수집 작업을 선택합니다.
* 해당 수집 라인의 생략 부호(...)를 클릭하고 &quot;사용자 요약 보기&quot;를 선택합니다.
* 표시되는 대화 상자에서 &quot;파일 다운로드...&quot; 아래의 드롭다운 목록에서 &quot;사용자 마이그레이션 보고서&quot;를 선택하고 다운로드 버튼을 클릭합니다.
* 결과 CSV 파일을 저장합니다.

그룹별로 기록되는 정보의 일부는 다음과 같습니다.
* 마이그레이션된 경우 그룹을 마이그레이션한 첫 번째 ACL 또는 CUG에 대한 경로입니다.
* 그룹이 이전에 마이그레이션되었는지 여부. 현재 수집이 삭제되지 않는 수집이었다면 일부 그룹은 이전 수집 중에 마이그레이션되었을 수 있습니다.
* 그룹이 기본 제공 그룹인지 여부. 이러한 그룹은 항상 대상 AEMaaCS 환경에 있으므로 마이그레이션되지 않습니다.
* 그룹이 마이그레이션된 콘텐츠의 ACL 또는 CUG에 속하지 않았다면 마이그레이션되지 않았을 것입니다.
* 그룹이 Assets 컬렉션에서 만든 그룹과 같은 로컬 그룹이었던 경우 마이그레이션되었을 수 있으며, 이 경우 &quot;local&quot;이라는 단어가 해당 그룹의 보고서에 추가됩니다.

마이그레이션 중에는 사용자가 마이그레이션되지 않지만, 소스 시스템의 사용자 그룹 관계는 어떻게든 캡처되지 않는 한 손실됩니다. 수집 프로세스는 주요 마이그레이션 보고서의 끝에 있는 사용자 보고서에서 이 정보의 일부를 텍스트 형식으로 캡처합니다.

### 사용자 보고서 {#user-report}

사용자 보고서 섹션에서 사용자는 이메일 주소 및 이 수집 중에 마이그레이션된 IMS 사용 그룹 목록과 함께 (한 줄에 하나씩) 보고됩니다.  마이그레이션되지 않았거나, 이전 수집 중에 마이그레이션되었거나, 로컬 그룹인 그룹은 목록에 포함되지 않습니다.   사용자가 마이그레이션된 IMS 사용 그룹에 없고 특수 사례임을 나타내는 추가 메모가 없는 경우(아래 **메모** 참조) 해당 사용자는 보고서에 _표시되지 않음_&#x200B;이 표시됩니다. 각 사용자와 함께 보고된 그룹은 사용자가 직접 또는 간접적으로 소스 시스템의 멤버인 그룹입니다. 소스 시스템의 그룹은 중첩되어 있을 수 있지만 타겟 시스템에는 중첩되어 있지 않으므로 이 그룹 목록은 IMS의 새 병합된 그룹 구조를 지원합니다.

지우기를 수행한 다음 지우지 않은 수집의 경우, 지우지 않은 수집에서 사용자 목록에 있는 그룹은 지우지 않는 단계 동안 마이그레이션된 그룹만 됩니다.

#### 메모 {#user-report-notes}

각 사용자의 그룹 외에도, 사용자 보고서에는 정보용으로 사용자에 대한 메모를 제공할 수 있는 필드가 있습니다(그리고 메모의 의미에 대한 자세한 설명은 보고서에 있음).  가능한 참고 사항은 다음과 같습니다.

* ACL에서 직접 참조되는 **Note-A** 사용자는 참고 섹션에 *Note-A*&#x200B;을(를) 갖게 됩니다. 이는 권장 사용 사례 또는 모범 사례가 아닙니다.
* 기본 제공 그룹의 직접 구성원인 **Note-B** 사용자는 참고 섹션에 *Note-B*&#x200B;을(를) 갖게 됩니다. 이 역시 권장 사용 사례나 모범 사례가 아닙니다.
* **Note-C** 마이그레이션된 로컬 그룹(Assets 컬렉션에서 만든 그룹 등)의 간접 구성원으로 직접 연결되는 사용자는 IMS에서 관리하도록 로컬 그룹이 구성되지 않았으므로 메모 섹션에 *Note-C*&#x200B;이(가) 있습니다.

이러한 사례는 이전 사례와 동시에 발생할 수 있습니다.  _각 노트가 각 사용자에 대해 참조하는 그룹에 대한 추가 정보를 보려면 수집 로그를 확인하십시오. 각 사용자에 대해 이 정보를 보고합니다._

사용자 보고서는 사용자 마이그레이션 보고서(아래 [최종 요약 및 보고서](#final-summary-and-report) 참조)의 끝에 추가되므로 고객이 그룹과 사용자 및 사용자 관계를 보다 완벽하게 이해할 수 있습니다.

## 파일 일괄 업로드 {#bulk-upload-files}

그룹은 AEM as a Cloud Service으로만 마이그레이션되므로 클라우드에서 AEM과 제대로 작동할 수 있도록 IMS에도 추가해야 합니다. 또한 사용자는 마이그레이션되지 않으므로 IMS에도 추가해야 합니다. CTT/CAM 마이그레이션 도구는 이 단계를 수행하지 않지만 수집 프로세스는 그룹용 파일과 사용자용 파일, 이렇게 두 개의 일괄 업로드 파일을 만듭니다. 이러한 파일을 편집한 다음 Admin Console의 벌크 업로드 기능과 함께 사용하여 AEM 그룹 및 사용자를 기반으로 IMS 그룹 및 사용자를 만들 수 있습니다.

일괄 업로드 파일을 사용하여 Admin Console을 사용하여 사용자 및 그룹을 만드는 방법에 대한 자세한 내용은 [일괄 그룹 및 IMS에 사용자 업로드](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md)를 참조하십시오.

또한 AEM as a Cloud Service 사용자 관리에 대한 자세한 내용은 [사용자 관리](https://helpx.adobe.com/ca/enterprise/using/users.html)를 참조하십시오.

## 추가 고려 사항 {#additional-considerations}

* **수집 전에 클라우드 인스턴스에서 기존 콘텐츠 지우기** 설정이 설정되어 있으면 이전에 Cloud Service 인스턴스로 전송된 그룹이 전체 기존 리포지토리와 함께 삭제됩니다. 콘텐츠가 수집되는 새 리포지토리가 만들어집니다. 또한 이 프로세스는 대상 Cloud Service 인스턴스에 대한 권한을 포함한 모든 설정을 재설정하며 **관리자** 그룹에 추가된 모든 사용자에 대해 true입니다. CTT/CAM 수집에 대한 액세스 토큰을 검색하려면 관리자 사용자를 **관리자** 그룹에 다시 추가해야 합니다.
* 지우지 않음 수집을 수행할 때(**기존 콘텐츠 지우기**&#x200B;가 설정되지 않음) 이전 전송 이후 콘텐츠가 변경되지 않아 콘텐츠가 전송되지 않으면 해당 콘텐츠와 연결된 그룹도 전송되지 않습니다. 이 규칙은 그룹이 소스 시스템에서 변경된 경우에도 적용됩니다. 이는 그룹이 연결된 콘텐츠와 함께 마이그레이션될 뿐이기 때문입니다. 이러한 이유로, 이 경우 소스 시스템의 그룹 멤버인 모든 그룹은 마이그레이션되고 있는 다른 그룹이나 마이그레이션되고 있는 다른 컨텐츠의 ACL에 포함되지 않는 한 마이그레이션되지 않습니다. 이후에 이러한 그룹을 마이그레이션하려면 패키지를 사용하거나, 대상에서 그룹을 삭제하고, 관련 콘텐츠를 다시 마이그레이션하거나, 지우기 수집을 사용하여 다시 마이그레이션하는 것이 좋습니다.
* 지우지 않는 수집 중에 소스 AEM 인스턴스와 대상 AEM Cloud Service 인스턴스 모두에서 동일한 고유성 제약 데이터(rep:principalName, rep:authorizableId, jcr:uuid 또는 rep:externalId)가 있는 그룹이 존재하는 경우 해당 그룹이 _마이그레이션되지 않음_&#x200B;이고 클라우드 시스템의 이전 기존 그룹은 변경되지 않은 상태로 유지됩니다. 주도자 마이그레이션 보고서에 기록됩니다.
* CUG(폐쇄형 사용자 그룹) 정책에 사용된 그룹에 대한 추가 고려 사항은 [폐쇄형 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md)을 참조하십시오.

## 최종 요약 및 보고서

추출 및 수집이 완료되면 그룹 마이그레이션 세부 사항을 표시하는 보고서가 생성됩니다. 자세한 내용은 [그룹 마이그레이션의 유효성을 검사하는 방법](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/validating-content-transfers.md#how-to-validate-group-migration)을 참조하십시오.
