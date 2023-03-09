---
title: 소스에서 컨텐츠 추출(기존)
description: 소스에서 콘텐츠 추출
hide: true
hidefromtoc: true
exl-id: 9f43356c-ba51-48bc-97f5-f1f5db81e7f3
source-git-commit: 3c8035e4db5729f58bae29136a32a0b9944d6a2f
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 34%

---

# 소스에서 컨텐츠 추출(기존) {#extracting-content}

## 컨텐츠 전송 도구의 추출 프로세스 {#extraction-process}

컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 단계를 따르십시오.
>[!NOTE]
>Amazon S3 또는 Azure Data Store를 데이터 저장소 유형으로 사용하는 경우 선택적 사전 복사 단계를 실행하여 추출 단계를 크게 가속화할 수 있습니다. 이렇게 하려면 다음을 구성해야 합니다. `azcopy.config` 추출 실행 전 파일. 을(를) 참조하십시오 [대형 콘텐츠 저장소 처리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 을 참조하십시오.

>[!IMPORTANT]
>소스에서 콘텐츠를 추출하기 전에 사용자 매핑 도구를 실행해야 합니다. 다음을 참조하십시오 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=en) 을 참조하십시오.

1. 다음에서 마이그레이션 세트 선택 **컨텐츠 전송** 마법사 및 클릭 **Extract** 추출을 시작하려면

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-01.png)

1. 다음 **마이그레이션 세트 추출** 대화 상자가 표시되면 클릭 **Extract** 추출 단계를 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >추출 단계 중에 스테이징 컨테이너를 선택적으로 덮어쓸 수 있습니다.

   >[!IMPORTANT]
   >소스에서 콘텐츠를 추출하기 전에 이 마이그레이션 세트에서 사용자 매핑이 실행되지 않은 경우 아래 그림과 같이 사용자 매핑 단계가 보류 중임을 나타내는 경고가 표시됩니다. 선택 **사용자 매핑** 를 클릭하여 사용자 매핑 도구를 실행합니다.
   >![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. 다음 **추출** 이제 필드에 **실행 중** 추출이 진행 중임을 나타내는 상태.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-03.png)

   추출이 완료되면 마이그레이션 세트의 상태가 **완료됨**&#x200B;으로 업데이트되고 *녹색* 클라우드 아이콘이 **정보**&#x200B;필드 아래에 표시됩니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >UI에는 를 다시 로드하는 자동 재로드 기능이 있습니다. **컨텐츠 전송** 30초마다 마법사를 실행합니다.
   >추출 단계가 시작되면 *60초* 후 쓰기 잠금이 만들어지고 해제됩니다. 따라서 추출이 중지된 경우 다시 추출을 시작하기 전에 잠금이 해제될 때까지 잠시 기다려야 합니다.

## 추가 추출 {#top-up-extraction-process}

콘텐츠 전송 도구에는 이전 콘텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 콘텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 콘텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 콘텐츠 전송에 대한 콘텐츠 고정 기간을 단축하기 위해 자주 차등 콘텐츠 추가를 수행하는 것이 좋습니다.
>또한 기존 콘텐츠의 콘텐츠 구조는 초기 추출을 수행할 때부터 추가 추출을 실행할 때까지 변경되지 않도록 해야 합니다. 초기 추출 이후 구조가 변경된 콘텐츠에서는 최상위 실행을 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한하십시오.

추출 프로세스가 완료되면 추가 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다.

아래 단계를 따르십시오.

1. 다음 위치로 이동 **컨텐츠 전송** 추가 추출을 수행할 마이그레이션 세트를 마법사로 선택하고 선택합니다. **추출**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-05.png)

1. 다음 **마이그레이션 세트 추출** 대화 상자가 표시됩니다. 클릭 **Extract**.

   >[!IMPORTANT]
   >**추출 중에 스테이징 컨테이너 덮어쓰기** 옵션을 비활성화해야 합니다.
   >![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-06.png)


## 다음 단계 {#whats-next}

컨텐츠 전송 도구의 &quot;소스에서 컨텐츠 추출&quot;에 대해 학습한 후, 이제 컨텐츠 전송 도구의 수집 프로세스에 대해 학습할 준비가 되었습니다. 다음을 참조하십시오 [Target에 컨텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) 콘텐츠 전송 도구에서 마이그레이션 세트를 수집하는 방법을 알아봅니다.
