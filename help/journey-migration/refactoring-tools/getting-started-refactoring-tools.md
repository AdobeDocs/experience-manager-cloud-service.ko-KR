---
title: 리팩토링 도구 시작하기
description: AEM as a Cloud Service에서 리팩터링 도구를 시작하는 방법에 대해 알아봅니다.
exl-id: 84394bdd-2b92-4f5d-b08a-7dc2c681baa4
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 4%

---

# 리팩토링 도구 시작하기 {#getting-started-refactoring-tools}

## 사용 가능 {#availability}

<!-- Alexandru: duplicate contextualhelp id, drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_rs_upload"
>title="Download"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=ko" text="Release Notes"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

-->

## 리팩터링 도구 실행 {#running-refactoring-tools}

리팩터링 도구를 사용하여 AEM as a Cloud Service과의 호환성을 위해 코드를 마이그레이션합니다.

1. CAM 프로젝트를 아직 만들지 않은 경우 [CAM에서 프로젝트 만들기 및 관리](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md#create-project)를 참조하십시오.
1. 소스 코드를 업로드하려면 **코드 리팩터링** 카드를 클릭하십시오.

   ![이미지](/help/journey-migration/refactoring-tools/assets/rscam1.png)

1. **Source 코드 보기**&#x200B;에 처음 액세스하면 소스 코드를 업로드하라는 메시지가 비어 있습니다.

   ![이미지](/help/journey-migration/refactoring-tools/assets/rscam2.png)

## Source 코드 업로드 {#uploading}

고객이 **리팩터링 도구**&#x200B;에 처음 액세스하면 **Source 코드 보기**&#x200B;에서 빈 상태가 표시됩니다. 아래 단계에 따라 프로젝트를 업로드하고 검사 프로세스를 시작합니다.

1. **프로젝트 업로드 페이지에 액세스**\
   업로드 프로세스를 시작하려면 빈 상태에서 **프로젝트 업로드** 단추를 클릭하십시오.

   ![이미지](/help/journey-migration/refactoring-tools/assets/rscam3.png)

1. **Source 코드 업로드**
   - 업로드 대화 상자에서 소스 코드 ZIP 파일을 선택합니다.
   - 시작하려면 **업로드**&#x200B;를 클릭하세요.
   - 업로드 진행 상황이 대화 상자에 표시됩니다. 기간은 프로젝트의 크기에 따라 다릅니다.

   ![이미지](/help/journey-migration/refactoring-tools/assets/rscam4.png)

1. **검사 프로세스**
   - 업로드 후 **검사 프로세스**&#x200B;가 백그라운드에서 자동으로 시작됩니다.
   - 이제 **Source 코드 보기**&#x200B;에 업로드된 프로젝트와 해당 검사 상태가 표시됩니다.

1. **검사 상태** 검사 프로세스는 수동 구성의 오버헤드를 줄여 리팩터링 도구 실행을 간소화하도록 설계되었습니다.

   검사에는 다음 상태 중 하나가 표시됩니다.
   - **실행 중** - 검사가 진행 중입니다.
   - **준비** - 검사가 완료되었습니다. 이제 리팩터링 도구를 실행할 수 있습니다.
   - **실패** - 오류가 발생했습니다. 프로젝트를 클릭하여 검사 보고서를 검토하고 문제를 해결합니다.

   ![이미지](/help/journey-migration/refactoring-tools/assets/rscam5.png)

>[!NOTE]
>
>새 프로젝트를 업로드하면 기존 프로젝트가 삭제됩니다. 계속하기 전에 필요한 데이터가 저장되었는지 확인하십시오.

>[!NOTE]
>
>소스 코드 업로드가 성공적으로 수행된 경우에만 리팩터링 작업을 실행할 수 있습니다.

## 리팩터링 작업 {#refactoring-jobs}

**리팩터링 작업** 탭을 클릭하면 기존 작업 목록이 표시됩니다. 아직 생성된 작업이 없는 경우 작업 생성을 묻는 빈 상태가 표시됩니다.

![이미지](/help/journey-migration/refactoring-tools/assets/rscam6.png)

### &#x200B;1. 새 리팩터링 작업 만들기

- **새 작업 만들기** 단추를 클릭합니다.
- 원하는 리팩터링 도구를 선택합니다.
- 리팩터링 프로세스를 시작하려면 **시작**&#x200B;을 클릭하세요.

![이미지](/help/journey-migration/refactoring-tools/assets/rscam7.png)

>[!NOTE]
>
>**모든 도구를 함께 사용** 옵션을 사용하여 개별 리팩터링 작업을 트리거하거나 사용 가능한 모든 도구를 한 번에 실행할 수 있습니다.

### &#x200B;2. 작업 상태

- **실행 중** - 작업이 현재 진행 중입니다. 완료 또는 실패 시 상태가 자동으로 업데이트됩니다.
- **완료됨** - 작업이 완료되었습니다. 이제 결과를 검토하거나 리팩터링된 코드를 다운로드할 수 있습니다.
- **실패** - 작업에 오류가 발생했습니다. 자세한 로그를 보고 문제를 해결하려면 작업을 클릭합니다.

![이미지](/help/journey-migration/refactoring-tools/assets/rscam8.png)

작업이 성공적으로 완료되면 다음을 검색할 수 있는 **다운로드** 단추를 사용할 수 있습니다.

- **리팩터링된 프로젝트**: 변환이 적용된 후 업데이트된 코드입니다. 고객은 프로젝트에 대한 최신 코드를 다운로드할 수 있습니다.
- **활동 로그**: 작업을 실행하는 동안 도구에서 수행한 모든 단계와 변경 사항이 이 과정의 일부로 기록됩니다.
- **결과 보고서**: 이 보고서에는 도구에서 완전히 실행되지 않았지만 해결해야 하는 항목이 포함되어 있습니다. 이러한 모든 변경 사항이 여기에 기록됩니다.

![이미지](/help/journey-migration/refactoring-tools/assets/rscam9.png)

>[!NOTE]
>
>각 작업은 완료하는 데 최대 1시간이 걸릴 수 있습니다. 상태가 업데이트되지 않은 경우 Adobe 지원 센터에 문의하십시오.
