---
title: 컨텐츠 전송 도구 시작하기
description: 컨텐츠 전송 도구 시작하기
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: bdcc5cfc229fd5b1fd1f70e37c7231ed3f727e72
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 32%

---

# 컨텐츠 전송 도구 시작하기 {#getting-started-content-transfer-tool}

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

1. 아래 그림과 같이 **컨텐츠 전송** 마법사에서 마이그레이션 세트를 봅니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   모든 기존 마이그레이션 세트가 현재 상태 및 상태 정보와 함께 **컨텐츠 전송** 마법사에 표시됩니다. 아래에 설명된 이러한 아이콘 중 일부가 표시될 수 있습니다.

   * *빨간색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 없음을 나타냅니다.
   * *녹색 클라우드*&#x200B;는 추출 프로세스를 완료할 수 있음을 나타냅니다.
   * *노란색 아이콘*&#x200B;은 기존 마이그레이션 세트를 만들지 않았으며, 특정 마이그레이션은 동일한 인스턴스에 있는 다른 사용자가 작성했음을 나타냅니다.

1. 마이그레이션 세트를 선택하고 **속성**&#x200B;을 클릭하여 마이그레이션 세트 속성을 보거나 편집합니다. 속성을 편집하는 동안 **마이그레이션 세트 이름** 또는 **서비스 URL**&#x200B;을 변경할 수 없습니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## 다음은 무엇입니까? {#whats-next}

마이그레이션 세트를 만드는 방법을 알게 되면 이제 컨텐츠 전송 도구에서 추출 및 수집 프로세스에 대해 학습할 준비가 되었습니다. 이러한 프로세스를 배우려면 먼저 [대용량 컨텐츠 저장소 처리](help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)를 검토하여 컨텐츠 전송 활동의 추출 및 수집 단계를 크게 단축하여 컨텐츠를 AEM으로 as a Cloud Service으로 이동해야 합니다.
