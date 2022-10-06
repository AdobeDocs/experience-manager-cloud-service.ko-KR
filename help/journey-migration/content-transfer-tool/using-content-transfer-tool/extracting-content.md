---
title: 소스에서 콘텐츠 추출
description: 소스에서 콘텐츠 추출
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 509715eb6324a370e28d681111ee0fd3fa2a7b44
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 21%

---

# 소스에서 콘텐츠 추출 {#extracting-content}

## 컨텐츠 전송 도구의 추출 프로세스 {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="컨텐츠 추출"
>abstract="추출이란 소스 AEM 인스턴스에서 마이그레이션 세트라는 임시 영역으로 컨텐츠를 추출하는 것입니다. 마이그레이션 세트는 소스 AEM 인스턴스와 클라우드 서비스 AEM 인스턴스 간에 전송된 컨텐츠를 임시 저장할 수 있도록 Adobe가 제공하는 클라우드 저장소 영역입니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="추출 추가"


컨텐츠 전송 도구에서 마이그레이션 세트를 추출하려면 아래 단계를 따르십시오.

>[!NOTE]
>Amazon S3, Azure Data Store 또는 파일 데이터 저장소를 데이터 저장소 유형으로 사용하는 경우 선택적 사전 복사 단계를 실행하여 추출 단계를 크게 단축할 수 있습니다. 사전 복사 단계는 첫 번째 전체 추출 및 통합에 가장 효과적입니다. 이렇게 하려면 다음을 구성해야 합니다 `azcopy.config` 파일 압축을 실행하기 전에 을(를) 참조하십시오. [대용량 컨텐츠 저장소 처리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 자세한 내용

>[!IMPORTANT]
>소스에서 컨텐츠를 추출하기 전에 사용자 매핑 도구를 실행해야 합니다. 자세한 내용은 [사용자 매핑 도구 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=en) 자세한 내용

1. 마이그레이션 세트 선택 **컨텐츠 전송** 마법사를 클릭하고 **Extract** 추출을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!IMPORTANT]
   >
   >추출 키가 유효하고 만료 기한이 아닌지 확인합니다. 만료 날짜가 가까워지면 마이그레이션 세트를 선택하고 속성을 클릭하여 추출 키를 갱신할 수 있습니다. 클릭 **갱신**. 클릭하면 Cloud Acceleration Manager가 표시됩니다 **추출 키 복사**. 클릭할 때마다 **추출 키 복사**를 입력하면 생성 후 14일 동안 유효한 새 추출 키가 생성됩니다.
   >![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. 그러면 추출 대화 상자가 표시됩니다. 클릭 **Extract** 추출 단계를 시작하려면 다음을 수행하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14.png)

   >[!NOTE]
   >추출 단계 중에 스테이징 컨테이너를 덮어쓰는 옵션이 제공됩니다. If **스테이징 컨테이너 덮어쓰기** 이 비활성화되면 컨텐츠 경로 또는 버전 포함 설정이 변경되지 않은 후속 마이그레이션에 대한 추출 속도를 높일 수 있습니다. 그러나 콘텐츠 경로 또는 버전 설정이 변경된 경우에는 **스테이징 컨테이너 덮어쓰기** 를 활성화해야 합니다.

   >[!IMPORTANT]
   >소스에서 컨텐츠를 추출하기 전에 이 마이그레이션 세트에 대해 사용자 매핑을 실행하지 않은 경우 위의 그림과 같이 사용자 매핑 단계가 보류 중임을 알리는 경고가 표시됩니다. 클릭 **사용자 매핑** 사용자 매핑 도구를 실행하려면

1. 다음 **추출** 이제 필드에 가 표시됩니다. **실행 중** 상태: 추출이 진행 중임을 나타냅니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   을(를) 클릭합니다. **진행률 보기** 진행 중인 추출을 자세히 보기 위해.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   컨텐츠 전송 페이지를 방문하여 Cloud Acceleration Manager에서 추출 단계 진행 상태를 모니터링할 수도 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. 추출이 완료되면 다른 열(예: **소스** 및 **경로** 를 클릭하여 채운 마이그레이션 세트의 세부 사항을 보려면 **...** 그런 다음 **세부 사항 보기**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18.png)


## 추가 추출 {#top-up-extraction-process}

컨텐츠 전송 도구에는 이전 컨텐츠 전송 활동 이후 수행된 변경 사항만 전송할 수 있는 차등 컨텐츠 추가를 지원하는 기능이 있습니다.

>[!NOTE]
>처음 컨텐츠 전송 후 클라우드 서비스에서 라이브로 전환되기 전에 최종 차등 컨텐츠 전송에 대한 컨텐츠 고정 기간을 단축하기 위해 자주 차등 컨텐츠 추가를 수행하는 것이 좋습니다. 첫 번째 전체 추출에 사전 복사 단계를 사용한 경우, 전체 프로세스에 시간을 추가할 수 있으므로 후속 추가 압출을 위해 사전 복사를 건너뛸 수 있습니다(추가 마이그레이션 세트 크기가 200GB 미만인 경우).
>또한 기존 컨텐츠의 컨텐츠 구조는 초기 추출을 수행한 때부터 추가 추출을 실행할 때까지의 변경되지 않는 것이 중요합니다. 초기 추출 후 구조가 변경된 컨텐츠에서는 추가를 실행할 수 없습니다. 마이그레이션 프로세스 중에 이를 제한해야 합니다.

추출 프로세스가 완료되면 추가 추출 방법을 사용하여 델타 컨텐츠를 전송할 수 있습니다.

아래 단계를 따르십시오.

1. 로 이동합니다 **컨텐츠 전송** 마법사를 열고 추가 추출을 수행할 마이그레이션 세트를 선택합니다. **추출**&#x200B;을 클릭하여 추가 추출을 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. 다음 **마이그레이션 세트 추출** 대화 상자가 표시됩니다. 클릭 **Extract**.

   >[!IMPORTANT]
   >**추출 중에 스테이징 컨테이너 덮어쓰기** 옵션을 비활성화해야 합니다.
   >![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## 다음 단계 {#whats-next}

이제 컨텐츠 전송 도구에서 소스에서 컨텐츠 추출을 학습하면 컨텐츠 전송 도구에서 수집 프로세스를 배울 수 있습니다. 자세한 내용은 [Target에 컨텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) 컨텐츠 전송 도구에서 마이그레이션 세트를 수집하는 방법을 알아봅니다.
