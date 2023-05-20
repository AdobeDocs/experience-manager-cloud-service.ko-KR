---
title: 컨텐츠 전송 도구 시작하기 (기존)
description: 콘텐츠 전송 도구 시작하기
hide: true
hidefromtoc: true
exl-id: a6ee6996-510e-42d7-9a7c-f64732764f97
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 24%

---

# 컨텐츠 전송 도구 시작하기 (기존) {#getting-started-content-transfer-tool}


## 사용 가능 {#availability}

소프트웨어 배포 포털에서 콘텐츠 전송 도구를 zip 파일로 다운로드할 수 있습니다. 다음을 통해 패키지를 설치할 수 있습니다. [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 소스 Adobe Experience Manager(AEM) 인스턴스에서 다음을 수행합니다. 최신 버전을 다운로드하십시오. 최신 버전에 대한 자세한 내용은 [릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=ko-kr).

>[!NOTE]
>[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 컨텐츠 전송 도구를 다운로드합니다.

## 소스 환경 연결 {#source-environment-connectivity}

소스 AEM 인스턴스가 허용 목록에 추가된 특정 호스트에만 도달할 수 있는 방화벽을 통해 실행되고 있을 수 있습니다. 추출을 성공적으로 실행하려면 AEM을 실행 중인 인스턴스에서 다음 끝점에 액세스해야 합니다.

* 대상 AEM as a Cloud Service 환경: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Azure Blob 스토리지 서비스: `*.blob.core.windows.net`
* 사용자 매핑 IO 끝점: `usermanagement.adobe.io`

대상 AEM as a Cloud Service 환경에 대한 연결을 테스트하려면 소스 인스턴스의 셸에서 다음 cURL 명령을 실행합니다(바꾸기) `program_id`, `environment_id`, 및 `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>다음과 같은 경우 `HTTP/2 200` 이(가) 수신되었습니다. AEM에 as a Cloud Service으로 연결되었습니다.

## 컨텐츠 전송 도구 실행 {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


이 섹션을 따라 컨텐츠 전송 도구를 사용하여 컨텐츠를 AEM as a Cloud Service(작성자/게시)에 마이그레이션하는 방법을 알아보십시오.

1. Adobe Experience Manager을 선택하고 도구 -> 로 이동합니다. **작업** -> **컨텐츠 마이그레이션**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt01.png)

1. 다음 항목 선택 **컨텐츠 전송** 옵션 from **컨텐츠 마이그레이션** 마법사.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt02.png)


1. 첫 번째 마이그레이션 세트를 만들면 아래 콘솔이 표시됩니다. **마이그레이션 세트 만들기**&#x200B;를 클릭하여 새 마이그레이션 세트를 만듭니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >기존 마이그레이션 세트가 있는 경우 콘솔에는 현재 상태와 함께 기존 마이그레이션 세트 목록이 표시됩니다.


1. 필드 채우기 **마이그레이션 세트 만들기** 아래에 설명된 대로 화면을 표시합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt04.png)

   1. **이름**: 마이그레이션 세트의 이름을 입력합니다.
      >[!NOTE]
      >마이그레이션 세트 이름에는 특수 문자를 사용할 수 없습니다.

   1. **클라우드 서비스 구성**: 대상 AEM as a Cloud Service 작성자 URL로 입력합니다.

      >[!NOTE]
      >컨텐츠 전송 작업 중에 한 번에 최대 10개의 마이그레이션 세트를 만들고 유지 관리할 수 있습니다.
      >또한 특정 환경 - *단계*, *개발* 또는 *프로덕션*&#x200B;마다 개별적으로 마이그레이션을 만들어야 합니다.

   1. **액세스 토큰**: 액세스 토큰을 입력합니다.

      >[!NOTE]
      >다음을 사용하여 액세스 토큰을 검색할 수 있습니다. **액세스 토큰 열기** 단추를 클릭합니다. 대상 Cloud Service 인스턴스의 &#39;관리자&#39; 그룹에 속해 있는지 확인해야 합니다.

   1. **매개 변수**: 다음 매개 변수를 선택하여 마이그레이션 세트를 만듭니다.

      1. **버전 포함**: 필요에 따라 선택합니다. 버전이 포함된 경우 경로 `/var/audit` 감사 이벤트를 마이그레이션할 때 자동으로 포함됩니다.

         ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt05.png)

         >[!NOTE]
         >버전을 마이그레이션 세트의 일부로 포함하려는 경우 다음을 사용하여 추가 작업을 수행합니다 `wipe=false`, 콘텐츠 전송 도구의 현재 제한으로 인해 버전 지우기를 비활성화해야 합니다. 버전 삭제를 활성화하고 마이그레이션 세트에 대해 추가 작업을 수행하는 경우 수집 작업을 다음과 같이 수행해야 합니다. `wipe=true`.


      1. **포함할 경로**: 경로 브라우저를 사용하여 마이그레이션해야 하는 경로를 선택합니다. 경로 선택기는 입력하거나 선택하여 입력을 허용합니다.

         >[!IMPORTANT]
         >마이그레이션 세트를 만드는 동안 다음 경로가 제한됩니다.
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (일부 `/etc` CTT에서 경로를 선택할 수 있음)


1. 클릭 **저장** 의 모든 필드를 채운 후 **마이그레이션 세트 만들기** 세부 정보 화면입니다.

1. 마이그레이션 세트는 다음에서 볼 수 있습니다. **컨텐츠 전송** 마법사: 아래 그림과 같습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   기존의 모든 마이그레이션 세트가 **컨텐츠 전송** 현재 상태 및 상태 정보가 포함된 마법사 아래에 설명된 이들 아이콘 중 일부가 표시될 수 있습니다.

   * *빨간색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 없음을 나타냅니다.
   * A *그린 클라우드* 는 추출 프로세스를 완료할 수 있음을 나타냅니다.
   * *노란색 아이콘*&#x200B;은 기존 마이그레이션 세트를 만들지 않았으며, 특정 마이그레이션은 동일한 인스턴스에 있는 다른 사용자가 작성했음을 나타냅니다.

1. 마이그레이션 세트를 선택하고 을(를) 클릭합니다 **속성** 마이그레이션 세트 속성을 보거나 편집합니다. 속성을 편집하는 동안에는 **마이그레이션 세트 이름** 또는 **서비스 URL**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png)

### 마이그레이션 세트 크기 및 디스크 공간 확인 {#migration-set-size}

마이그레이션 세트를 만든 후 추출 프로세스를 시작하기 전에 마이그레이션 세트에 대해 크기 검사를 실행하는 것이 좋습니다.
마이그레이션 세트에서 크기 검사를 실행하면 다음 작업을 수행할 수 있습니다.
* 에 디스크 공간이 충분한지 확인 `crx-quickstart` 추출을 완료할 하위 디렉터리입니다.
* 마이그레이션 세트 크기가 지원되는 제품 제한 내에 속하는지 확인하고 실패한 콘텐츠 수집을 방지합니다.

크기 검사를 실행하려면 아래 단계를 따르십시오.

1. 마이그레이션 세트를 선택하고 을(를) 클릭합니다 **크기 확인**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image1.png)

1. 이렇게 하면 **크기 확인** 대화 상자.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image2.png)

1. 클릭 **크기 확인** 프로세스를 시작합니다. 그런 다음 마이그레이션 세트 목록 보기로 돌아오면 **크기 확인** 이(가) 실행 중입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image3.png)


1. 한 번 **크기 확인** 프로세스가 완료되었습니다. 상태가 다음 중 하나로 변경됩니다. **완료됨**. 동일한 마이그레이션 세트를 선택하고 다음을 클릭하십시오. **크기 확인** 결과를 봅니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image4.png)

   다음은 의 예입니다. **크기 확인** 경고가 없는 결과입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image5.png)

1. 다음과 같은 경우 **크기 확인** 디스크 공간이 부족하거나 마이그레이션 세트가 제품 제한을 초과한다는 결과가 나타납니다. **경고** 상태가 표시됩니다.

![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)

다음은 의 예입니다. **크기 확인** 경고가 있는 결과.

![이미지](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png)


## 다음 단계 {#whats-next}

마이그레이션 세트를 만드는 방법을 배웠다면 이제 콘텐츠 전송 도구의 추출 및 수집 프로세스에 대해 알아볼 수 있습니다. 이러한 프로세스를 학습하기 전에 다음을 검토해야 합니다 [대형 콘텐츠 저장소 처리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) 컨텐츠 전송 활동의 추출 및 수집 단계 속도를 크게 향상시켜 컨텐츠를 AEM으로 as a Cloud Service 이동합니다.
