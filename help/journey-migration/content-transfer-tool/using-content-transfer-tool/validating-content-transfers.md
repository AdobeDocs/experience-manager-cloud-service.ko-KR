---
title: 콘텐츠 전송 확인
description: 컨텐츠 전송 도구를 사용하여 컨텐츠 전송의 유효성을 검사합니다
exl-id: a12059c3-c15a-4b6d-b2f4-df128ed0eea5
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 2%

---

# 콘텐츠 전송 확인 {#validating-content-transfers}

## 시작 {#getting-started}

사용자는 콘텐츠 전송 도구에서 추출한 모든 콘텐츠가 대상 인스턴스에 성공적으로 수집되었는지 확인할 수 있습니다. 이 유효성 검사 기능은 추출 중에 포함된 모든 노드의 경로 요약과 수집 중에 포함된 모든 노드의 경로 요약을 비교하여 작동합니다. 추출 다이제스트에 포함된 노드 경로 중 수집 다이제스트에서 누락된 노드가 있는 경우 유효성 검사가 실패한 것으로 간주되며 추가 수동 유효성 검사가 필요할 수 있습니다.

>[!INFO]
>
>이 기능은 CTT(Content Transfer Tool) 버전 1.8.x 릴리스에서 사용할 수 있습니다. AEM Cloud Service 대상 환경은 버전 6158 이상을 실행 중이어야 합니다. 또한 소스 환경을 설정하여 실행해야 합니다 [사전 복사](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#setting-up-pre-copy-step). 유효성 검사 기능은 소스에서 azcopy.config 파일을 찾습니다. 이 파일을 찾지 못하면 유효성 검사가 실행되지 않습니다. azcopy.config 파일을 구성하는 방법에 대한 자세한 내용은 [이 페이지](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#configure-azcopy-config-file).

컨텐츠 전송 유효성 검사는 선택적 기능입니다. 이 기능을 활성화하면 추출 및 수집을 수행하는 데 걸리는 시간이 모두 늘어납니다. 이 기능을 사용하려면 다음 단계에 따라 소스 AEM 환경의 시스템 콘솔에서 활성화하십시오.

1. 다음 위치로 이동하여 소스 인스턴스의 Adobe Experience Manager 웹 콘솔로 이동합니다. **도구 - 작업 - 웹 콘솔** 또는 을 통해 URL로 바로 이동할 수 있습니다 *https://serveraddress:serverport/system/console/configMgr*
1. 검색 대상 **컨텐츠 전송 도구 추출 서비스 구성**
1. 연필 아이콘 버튼을 사용하여 구성 값을 편집합니다
1. 활성화 **추출 중 마이그레이션 유효성 검사 활성화** 설정 후 누르기 **저장**:

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTTvalidation1.png)

이 설정이 활성화되고 대상 AEM Cloud Service 환경이 호환되는 릴리스를 실행하면 뒤따르는 모든 추출 및 수집 중에 마이그레이션 유효성 검사가 발생합니다.

컨텐츠 전송 도구 설치 방법에 대한 자세한 내용은 [컨텐츠 전송 도구 시작하기](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).

## 컨텐츠 전송의 유효성 검사 방법 {#how-to-validate-a-content-transfer}

소스 AEM 환경에서 마이그레이션 유효성 검사를 활성화한 상태에서 추출을 시작합니다.

If **추출 중 스테이징 컨테이너 덮어쓰기** 가 활성화되면 추출과 관련된 모든 노드가 추출 경로 다이제스트에 기록됩니다. 이 설정을 사용할 때는 를 활성화해야 합니다. **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 수집 중에 를 설정합니다. 그렇지 않으면 수집 다이제스트에서 누락된 노드가 있을 수 있습니다. 이는 이전 수집에서 대상에 이미 존재하는 노드입니다.

이에 대한 그래픽 설명은 다음 예를 참조하십시오.

### 예 1 {#example-1}

* **추출(덮어쓰기)**

  ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/validation-01.png)

* **수집(지우기)**

  ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/validation-02.png)

* **메모**

  이러한 &quot;덮어쓰기&quot;와 &quot;지우기&quot;의 조합은 반복되는 수집에도 일관된 유효성 검사 결과를 가져옵니다.

### 예 2 {#example-2}

* **추출**

  ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/validation-03.png)

* **수집**

  ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/validation-04.png)

* **메모**

  이렇게 &quot;덮어쓰기&quot;와 &quot;지우기&quot;를 조합하면 초기 수집에 대해 일관성 있는 유효성 검사 결과가 생성됩니다.

  수집이 반복되면 수집 다이제스트가 비어 있고 유효성 검사가 실패한 것으로 표시됩니다. 이 추출의 모든 노드가 대상에 이미 존재하므로 수집 다이제스트가 비어 있습니다.

추출이 완료되면 수집을 시작합니다.

수집 로그의 맨 위에는 과 유사한 항목이 포함됩니다. `aem-ethos/tools:1.2.438`. 이 버전 번호가 **1.2.438** 또는 그 이상이며, 그렇지 않은 경우 사용 중인 AEM as a Cloud Service 릴리스에서는 유효성 검사가 지원되지 않습니다.

수집이 완료되고 유효성 검사가 시작되면 수집 로그에 다음 로그 항목이 기록됩니다.

```
Gathering artifacts for migration validation...
```

유효성 검사에 대한 세부 정보는 이 항목 뒤에 표시됩니다. 아래에서 대규모 마이그레이션의 예를 확인하십시오.

```
Beginning publish migration validation. Migration job id=[3aba1f96-84b6-4bd0-8642-c61c0d528387]
Extraction path digest is being processed...
Extraction path digest processing took 982 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 999 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 51674784
INGESTION: Number of nodes ingested: 51674784
----------------------------------------------------------
Validation succeeded! No entries were detected to be missing from the ingestion digest.
----------------------------------------------------------
Comparing the path digests took 29 seconds
Migration validation took 33 minutes
```

추출 다이제스트에 있는 수집 다이제스트에서 누락된 항목이 없으므로 성공한 유효성 검사의 예입니다.

비교하기 위해 유효성 검사가 실패한 경우(또는 추가 마이그레이션이 수행된 경우) 유효성 검사 보고서의 모양은 다음과 같습니다.

```
Beginning publish migration validation. Migration job id=[ac217e5a-a08d-4e81-cbd6-f39f88b174ce]
Extraction path digest is being processed...
Extraction path digest processing took 0 seconds
Ingestion path digest is being processed...
Ingestion path digest processing took 0 seconds
Comparing the Extraction and Ingestion path digests...
----------------------------------------------------------
EXTRACTION: Number of nodes extracted: 4635
INGESTION: Number of nodes ingested: 0
----------------------------------------------------------
Validation failed. However, the following nodes may already be present in the target environment.
See our Migration Validation FAQ (https://www.adobe.com/go/aem_cloud_ctt_validation_en) or open a ticket with Customer Care.
There are 4635 entries present in the extraction digest that are missing from the ingestion digest.
/content/dam/bruce
/content/dam/bruce-assets
... more paths listed (up to 10k) ...
----------------------------------------------------------
Comparing the path digests took 0 seconds
Migration validation took 0 minutes
```

위의 실패 예제는 수집을 실행한 다음 지우기 를 비활성화한 상태로 동일한 수집을 다시 실행하여 수집 중에 노드가 포함되지 않도록 함으로써 달성했습니다. 모든 것이 대상에 이미 존재합니다.

유효성 검사 보고서는 수집 로그에 포함될 뿐만 아니라 **수집 작업** cloud Acceleration Manager의 사용자 인터페이스. 이렇게 하려면 세 점(**...**)을 클릭한 다음 을 클릭합니다 **유효성 검사 보고서** 을 클릭하여 유효성 검사 보고서를 확인합니다.


![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/CTTvalidationreportnew.png)

## 주도자 마이그레이션의 유효성을 검사하는 방법 {#how-to-validate-principal-migration}

다음을 참조하십시오 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) 주요 마이그레이션에 대한 세부 정보 및 필요한 이유를 읽어 보십시오.

추출 및 수집이 성공적으로 완료되면 주요 마이그레이션에 대한 요약 및 보고서를 사용할 수 있습니다. 이 정보는 어떤 사용자 및 그룹이 성공적으로 마이그레이션되었는지 확인하고, 일부가 마이그레이션되지 않은 이유를 확인하는 데 사용할 수 있습니다.

이 정보를 보려면 Cloud Acceleration Manager 로 이동하십시오. 프로젝트 카드를 클릭하고 컨텐츠 전송 카드를 클릭합니다. 다음으로 이동 **수집 작업** 확인할 수집을 찾습니다. 세 점(**...**)을 클릭하여 해당 수집을 수행합니다. **사용자 요약 보기** 을 클릭합니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-action.png)

요약 정보가 포함된 대화 상자가 표시됩니다. 도움말 아이콘을 사용하여 자세한 설명을 읽을 수 있습니다. 다음을 클릭합니다. **보고서 다운로드** 단추를 클릭하여 전체 CSV(쉼표로 구분) 보고서를 다운로드합니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-principal-dialog.png)

>[!NOTE]
>
>사용자 매핑이 비활성화되면 이 대화 상자의 다른 변형이 표시됩니다. 사용자 매핑이 비활성화되었음을 나타내며 사용자 매핑 값을 제공하는 3개의 필드가 표시되지 않습니다.

## 문제 해결 {#troubleshooting}

### 유효성 검사 실패. 이제 무엇을 합니까? {#validation-fail}

첫 번째 단계는 수집이 실제로 실패했는지 또는 추출된 콘텐츠가 대상 환경에 이미 있는지 확인하는 것입니다. 이 문제는 수집이 와 반복되는 경우 발생할 수 있습니다. **수집하기 전에 클라우드 인스턴스의 기존 콘텐츠 지우기** 옵션이 비활성화되었습니다.

확인하려면 유효성 검사 보고서에서 경로를 선택하고 대상 환경에 있는지 확인합니다. 게시 환경의 경우 페이지 및 에셋을 직접 확인하는 것으로 제한될 수 있습니다. 이 단계에 대한 지원이 필요한 경우 고객 지원 센터에서 티켓을 엽니다.

### 노드 수가 예상했던 것보다 적습니다. 이유는 무엇입니까? {#node-count-lower-than-expected}

추출 및 수집 다이제스트의 일부 경로는 수집 완료 후 2시간 이내에 마이그레이션 유효성 검사 결과를 계산할 수 있도록 이러한 파일의 크기를 관리 가능하게 유지하기 위해 의도적으로 제외됩니다.

현재 다이제스트에서 제외되는 경로는 다음과 같습니다. `cqdam.text.txt` 렌디션, 노드 `/home`, 및 다음 내의 노드 `/jcr:system`.

### 폐쇄된 사용자 그룹이 작동하지 않음 {#validating-cugs}

다음을 참조하십시오 [폐쇄된 사용자 그룹 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) CUG(폐쇄형 사용자 그룹) 정책을 사용할 때의 추가 고려 사항입니다.
