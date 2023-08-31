---
title: 자산 보기를 사용하여 자산 일괄 가져오기
description: 새로운 에셋 UI(에셋 보기)를 사용하여 에셋을 일괄 가져오는 방법을 알아봅니다. 관리자는 데이터 소스에서 AEM Assets으로 많은 수의 에셋을 가져올 수 있습니다.
source-git-commit: 49d1e002f22427d8ffc6c5bdecd054c10eac47b9
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 3%

---

# 자산 보기를 사용하여 자산 일괄 가져오기  {#bulk-import-assets-view}

AEM Assets 보기에서 일괄 가져오기를 사용하면 관리자는 데이터 소스에서 AEM Assets으로 많은 수의 에셋을 가져올 수 있습니다. 관리자는 더 이상 AEM Assets에 개별 에셋 또는 폴더를 업로드할 필요가 없습니다.

다음 데이터 소스에서 에셋을 가져올 수 있습니다.

* Azure
* AWS
* Google Cloud
* Dropbox

## 사전 요구 사항 {#prerequisites}

| 데이터 소스 | 사전 요구 사항 |
|-----|------|
| Azure | <ul> <li>Azure 스토리지 계정 </li> <li> Azure Blob 컨테이너 <li> 인증 모드에 따른 Azure 액세스 키 또는 SAS 토큰 </li></ul> |
| AWS | <ul> <li>AWS 주 </li> <li> AWS 버킷 <li> AWS 액세스 키 </li><li> AWS 액세스 암호 </li></ul> |
| Google Cloud | <ul> <li>GCP 버킷 </li> <li> GCP 서비스 계정 이메일 <li> GCP 서비스 계정 개인 키</li></ul> |
| Dropbox | <ul> <li>Dropbox 클라이언트 ID </li> <li> Dropbox 클라이언트 암호</li></ul> |

데이터 소스를 기반으로 하는 이러한 사전 요구 사항 외에도 AEM Assets으로 가져와야 하는 모든 에셋이 포함된 데이터 소스에서 사용할 수 있는 소스 폴더 이름을 알고 있어야 합니다.

## 대량 가져오기 구성 만들기 {#create-bulk-import-configuration}

다음 단계를 실행하여 일괄 가져오기 구성을 생성합니다.

1. 다음으로 이동 **[!UICONTROL 설정]** > **[!UICONTROL 일괄 가져오기]** 및 클릭 **[!UICONTROL 가져오기 만들기]**.
1. 데이터 소스를 선택합니다. 사용 가능한 옵션에는 Azure, AWS, Google Cloud 및 Dropbox이 포함됩니다.
1. 에서 대량 가져오기 구성의 이름을 지정합니다 **[!UICONTROL 이름]** 필드.
1. 에 언급된 대로 데이터 소스별 자격 증명을 지정합니다. [전제 조건](#prerequisites).
1. 의 데이터 소스에 있는 자산이 포함된 루트 폴더의 이름을 입력합니다. **[!UICONTROL 소스 폴더]** 필드.
1. (선택 사항) **[!UICONTROL 가져오기 후 소스 파일 삭제]** 파일을 Experience Manager Assets으로 가져온 후 소스 데이터 저장소에서 원본 파일을 삭제하는 옵션입니다.
1. 다음 항목 선택 **[!UICONTROL 가져오기 모드]**. 선택 **[!UICONTROL 건너뛰기]**, **[!UICONTROL 바꾸기]**, 또는 **[!UICONTROL 버전 만들기]**. 건너뛰기 모드가 기본값이며 이 모드에서는 에셋이 이미 있는 경우 수집기가 건너뜁니다.
   ![소스 세부 정보 가져오기](assets/bulk-import-source-details.png)

1. (선택 사항) CSV 형식으로 제공된 가져올 메타데이터 파일을 메타데이터 파일 필드에 지정하고 을 클릭합니다 **[!UICONTROL 다음]** 다음으로 이동 **[!UICONTROL 위치 및 필터]**.
1. DAM에서 자산을 가져올 위치를 정의하려면 다음을 수행하십시오. **[!UICONTROL 에셋 대상 폴더]** 필드, 경로를 지정합니다. (예: `/content/dam/imported_assets`)
1. (선택 사항) **[!UICONTROL 필터 선택]** 섹션에서 수집 프로세스에 포함할 에셋의 최소 파일 크기(MB)를 제공합니다. **[!UICONTROL 최소 크기로 필터링]** 필드.
1. (선택 사항) 에셋의 수집 프로세스에 포함할 에셋의 최대 파일 크기(MB)를 제공합니다. **[!UICONTROL 최대 크기로 필터링]** 필드.
1. (선택 사항) 다음을 사용하여 수집 프로세스에 포함할 MIME 유형을 선택합니다. **[!UICONTROL MIME 유형 포함]** 필드. 이 필드에서 여러 MIME 유형을 선택할 수 있습니다. 값을 정의하지 않으면 모든 MIME 유형이 수집 프로세스에 포함됩니다.

1. (선택 사항) 을 사용하여 수집 프로세스에서 제외할 MIME 유형을 선택합니다 **[!UICONTROL MIME 유형 제외]** 필드. 이 필드에서 여러 MIME 유형을 선택할 수 있습니다. 값을 정의하지 않으면 모든 MIME 유형이 수집 프로세스에 포함됩니다.

   ![일괄 가져오기 필터](assets/bulk-import-location.png)

1. **[!UICONTROL 다음]**&#x200B;을 클릭합니다. 선택 **[!UICONTROL 가져오기 저장 및 실행]** 구성을 저장하고 일괄 가져오기를 실행합니다. 선택 **[!UICONTROL 가져오기 저장]** 나중에 실행할 수 있도록 구성을 지금 저장하십시오.

   ![일괄 가져오기 실행](assets/bulk-import-run.png)

1. 클릭 **[!UICONTROL 저장]** 을 눌러 선택한 옵션을 실행합니다.

## 기존 대량 가져오기 구성 보기 {#view-import-configuration}

구성을 작성한 후 저장하도록 선택하면 구성에 가 표시됩니다. **[!UICONTROL 저장된 가져오기]** 탭.

![대량 가져오기 구성 저장](assets/bulk-import-save.png)

가져오기를 저장하고 실행하도록 선택하면 가져오기 구성에 **[!UICONTROL 실행된 가져오기]** 탭.

![대량 가져오기 구성 저장](assets/bulk-import-executed.png)

가져오기를 예약하면 **[!UICONTROL 예약된 가져오기]** 탭.

## 일괄 가져오기 구성 편집 {#edit-import-configuration}

구성 세부 정보를 편집하려면 구성 이름에 해당하는 ...을 클릭하고 을 클릭합니다. **[!UICONTROL 편집]**. 편집 작업을 수행하는 동안에는 구성 및 가져오기 데이터 소스의 제목을 편집할 수 없습니다. 실행, 예약 또는 저장된 가져오기 탭을 사용하여 구성을 편집할 수 있습니다.

![일괄 가져오기 구성 편집](assets/bulk-import-edit.png)

## 일회성 또는 반복 가져오기 예약 {#schedule-imports}

1회 또는 반복 대량 가져오기를 예약하려면 다음 단계를 실행합니다.

1. 에서 사용할 수 있는 구성 이름에 해당하는 을 클릭합니다. **[!UICONTROL 실행된 가져오기]** 또는 **[!UICONTROL 저장된 가져오기]** tab 키를 누른 다음 클릭 **[!UICONTROL 예약]**. 로 이동하여 기존 예약된 가져오기의 일정을 조정할 수도 있습니다. **[!UICONTROL 예약된 가져오기]** 탭 및 클릭 **[!UICONTROL 예약]**.

1. 일회성 수집을 설정하거나 시간별, 일별 또는 주별 일정을 예약합니다. 클릭 **[!UICONTROL 제출]**.

   ![일괄 가져오기 구성 예약](assets/bulk-import-schedule.png)

## 가져오기 상태 검사 수행 {#import-health-check}

데이터 소스에 대한 연결의 유효성을 검사하려면 구성 이름에 해당하는 ...을 클릭한 다음 를 클릭합니다 **[!UICONTROL 확인]**. 연결에 성공하면 Experience Manager Assets에 다음 메시지가 표시됩니다.

![일괄 가져오기 상태 확인](assets/bulk-import-health-check.png)

## 가져오기를 실행하기 전에 시험 실행 수행 {#dry-run-bulk-import}

구성 이름에 해당하는 을(를) 클릭하고 을(를) 클릭합니다 **[!UICONTROL 시험 실행]** 대량 가져오기 작업에 대한 테스트 실행을 호출합니다. Experience Manager Assets에 일괄 가져오기 작업에 대한 다음 세부 정보가 표시됩니다.

![일괄 가져오기 상태 확인](assets/bulk-import-dry-run.png)

## 일괄 가져오기 실행 {#run-bulk-import}

구성을 생성하는 동안 가져오기를 저장한 경우 저장된 가져오기 탭으로 이동하여 구성에 해당하는 ...을 클릭하고 를 클릭합니다 **[!UICONTROL 실행]**.

마찬가지로 이미 실행된 가져오기를 실행해야 하는 경우 실행된 가져오기 탭으로 이동하여 구성 이름에 해당하는 ...을 클릭하고 을 클릭합니다. **[!UICONTROL 실행]**.

## 진행 중인 가져오기 중지 또는 예약 {#schedule-stop-ongoing-report}

가져오는 동안 일괄 가져오기 홈 페이지에 표시되는 일괄 가져오기 상태 대화 상자를 사용하여 진행 중인 일괄 가져오기를 예약하거나 중지할 수 있습니다.

![가져오기 진행 중](assets/bulk-import-progress.png)

을 클릭하여 대상 폴더로 가져온 자산을 볼 수도 있습니다. **[!UICONTROL 에셋 보기]**.


## 대량 가져오기 구성 삭제 {#delete-bulk-import-configuration}

에 존재하는 구성 이름에 해당하는 ...을 클릭합니다. **[!UICONTROL 실행된 가져오기]**, **[!UICONTROL 예약된 가져오기]**, 또는 **[!UICONTROL 저장된 가져오기]** 탭 및 클릭 **[!UICONTROL 삭제]** 대량 가져오기 구성을 삭제합니다.

## 일괄 가져오기 수행 후 에셋으로 이동 {#view-assets-after-bulk-import}

일괄 가져오기 작업을 실행한 후 에셋을 가져오는 에셋 대상 위치를 보려면 구성 이름에 해당하는 ...을 클릭한 다음 를 클릭합니다 **[!UICONTROL 에셋 보기]**.

