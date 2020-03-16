---
title: 자산 보고서
description: 이 문서에서는 AEM 자산의 자산에 대한 다양한 보고서와 보고서 생성 방법에 대해 설명합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6998ee5f3c1c1563427e8739998effe0eba867fc

---


# 자산 보고서 {#asset-reports}

자산 보고는 AEM(Adobe Experience Manager) 자산 배포의 유틸리티를 평가하는 주요 도구입니다. AEM Assets를 사용하면 디지털 자산에 대한 다양한 보고서를 생성할 수 있습니다. 보고서는 시스템 사용, 사용자가 자산과 상호 작용하는 방법, 다운로드 및 공유되는 자산에 대한 유용한 정보를 제공합니다.

보고서의 정보를 사용하여 주요 성공 지표를 추출하여 기업 내 및 고객별 AEM 자산의 채택을 측정합니다.

AEM Assets 보고 프레임워크는 Sling 작업을 활용하여 정렬된 방식으로 보고서 요청을 비동기식으로 처리합니다. 대형 저장소에 대해 확장 가능합니다. 비동기 보고서 처리는 보고서가 생성되는 효율성과 속도를 높입니다.

보고서 관리 인터페이스는 직관적이며, 보관된 보고서에 액세스하고 보고서 실행 상태(성공, 실패 및 큐에 있음)를 볼 수 있는 세밀한 옵션과 컨트롤을 포함합니다.

보고서가 생성되면 받은 편지함 알림을 통해 알림을 받게 <!-- through an email (optional) and --> 됩니다. 이전에 생성된 모든 보고서가 표시되는 보고서 목록 페이지에서 보고서를 보거나, 다운로드하거나, 삭제할 수 있습니다.

## 보고서 생성 {#generate-reports}

AEM Assets는 다음과 같은 표준 보고서를 생성합니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* 브랜드 포털 게시
* 디스크 사용량
* 파일
* 공유 링크

AEM 관리자는 구현을 위해 이러한 보고서를 쉽게 생성하고 사용자 정의할 수 있습니다. 관리자는 다음 단계에 따라 보고서를 생성할 수 있습니다.

1. AEM 로고를 탭/클릭하고 도구 > **[!UICONTROL 자산]** > **[!UICONTROL 보고서로]** 이동합니다 ****.

   ![탐색](assets/navigation.png)

1. 자산 보고서 페이지에서 도구 모음에서 만들기를 탭/ **[!UICONTROL 클릭합니다]** .
1. 보고서 **[!UICONTROL 만들기]** 페이지에서 만들 보고서를 선택하고 다음을 탭/ **[!UICONTROL 클릭합니다]**.

   ![choose_report](assets/choose_report.png)

   >[!NOTE]
   >
   >자산 다운로드됨 **[!UICONTROL 보고서를]** 생성하려면 먼저 자산 다운로드 서비스가 활성화되어 있는지 확인하십시오. 웹 콘솔(`https://[aem_server]:[port]/system/console/configMgr`)에서 **[!UICONTROL 오늘 CQ DAM 이벤트 레코더]** 구성을 열고 이벤트 유형에서 다운로드됨( **[!UICONTROL 다운로드됨)]** 옵션을 선택합니다(아직 선택되지 않은 경우).

   >[!NOTE]
   >
   >기본적으로 컨텐츠 조각 및 링크 공유는 자산 다운로드됨 보고서에 포함됩니다. 링크 공유 보고서를 만들거나 콘텐트 조각을 다운로드 보고서에서 제외하려면 적절한 옵션을 선택합니다.

1. 보고서가 저장되는 CRX 저장소에서 제목, 설명, 축소판 및 폴더 경로와 같은 보고서 세부 정보를 구성합니다. 기본적으로 폴더 경로는 */content/dam*&#x200B;입니다. 다른 경로를 지정할 수 있습니다.

   ![report_configuration](assets/report_configuration.png)

   보고서의 날짜 범위를 선택합니다.

   지금 또는 미래 날짜와 시간에 보고서를 생성하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >나중에 보고서를 예약하도록 선택하는 경우 날짜 및 시간 필드에 날짜와 시간을 지정해야 합니다. 값을 지정하지 않으면 보고서 엔진은 이 값을 즉시 생성할 보고서로 처리합니다.

   구성 필드는 만드는 보고서 유형에 따라 다를 수 있습니다.

   예를 들어 디스크 **[!UICONTROL 사용량]** 보고서는 자산에서 사용되는 디스크 공간을 계산할 때 자산 표현물을 포함하는 옵션을 제공합니다. 디스크 사용량 계산을 위해 하위 폴더에 자산을 포함하거나 제외하도록 선택할 수 있습니다.

   >[!NOTE]
   >
   >디스크 **[!UICONTROL 사용량]** 보고서는 현재 디스크 공간 사용만을 나타내므로 날짜 범위 필드를 포함하지 않습니다.

   ![disk_usage_configuration](assets/disk_usage_configuration.png)

   파일 보고서를 만들 **[!UICONTROL 때]** 하위 폴더를 포함/제외할 수 있습니다. 그러나 이 보고서에 대한 자산 표현물은 포함할 수 없습니다.

   ![files_report](assets/files_report.png)

   링크 **[!UICONTROL 공유]** 보고서는 AEM 자산 내에서 외부 사용자와 공유된 자산에 대한 URL을 표시합니다. <!-- It includes email ids of the user who shared the assets, emails ids of users with which the assets are shared, share date, and expiration date for the link. --> 열을 사용자 정의할 수 없습니다.

   링크 **[!UICONTROL 공유]** 보고서는 하위 폴더 및 변환에 대한 옵션을 포함하지 않으며, 단지 */var/dam/share*&#x200B;아래에 나타나는 공유 URL만 게시하기 때문입니다.

   ![link_share](assets/link_share.png)

1. 도구 모음에서 **[!UICONTROL 다음을]** 탭/클릭합니다.

1. 열 **[!UICONTROL 구성]** 페이지에서 기본적으로 보고서에 일부 열이 표시되도록 선택됩니다. 추가 열을 선택할 수 있습니다. 보고서에서 제외하려면 선택한 열을 선택 취소합니다.

   ![configure_columns](assets/configure_columns.png)

   사용자 지정 열 이름 또는 속성 경로를 표시하려면 CRX의 jcr:content 노드 아래에 자산 바이너리의 속성을 구성합니다. 또는 속성 경로 선택기를 통해 추가합니다.

   ![custom_columns](assets/custom_columns.png)

1. 도구 모음에서 **[!UICONTROL 만들기를]** 탭/클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.
1. 자산 보고서 페이지에서 보고서 생성 상태는 성공, 실패, 큐에 있음 또는 예약됨 등의 보고서 작업의 현재 상태를 기반으로 합니다. 동일한 상태가 알림 받은 편지함에 나타납니다.

   보고서 페이지를 보려면 보고서 링크를 탭/클릭합니다. 또는 보고서를 선택하고 도구 모음에서 보기 아이콘을 탭/클릭합니다.

   ![report_page](assets/report_page.png)

   도구 모음에서 다운로드 아이콘을 탭/클릭하여 보고서를 CSV 형식으로 다운로드합니다.

## 사용자 정의 열 추가 {#add-custom-columns}

사용자 지정 열을 다음 보고서에 추가하여 사용자 지정 요구 사항에 대한 데이터를 더 많이 표시할 수 있습니다.

* 업로드
* 다운로드
* 만료
* 수정
* 게시
* 브랜드 포털 게시
* 파일

1. AEM 로고를 탭/클릭하고 도구 > **[!UICONTROL 자산]** > **[!UICONTROL 보고서로]** 이동합니다 ****.
1. 자산 보고서 페이지에서 도구 모음에서 만들기를 탭/ **[!UICONTROL 클릭합니다]** .

1. 보고서 **[!UICONTROL 만들기]** 페이지에서 만들 보고서를 선택하고 다음을 탭/ **[!UICONTROL 클릭합니다]**.
1. 제목, 설명, 축소판, 폴더 경로, 날짜 범위 등과 같은 보고서 세부 정보를 원하는 대로 구성합니다.

1. 사용자 지정 열을 표시하려면 사용자 지정 열 아래에 열 이름을 **[!UICONTROL 지정합니다]**.

   ![custom_columns-1](assets/custom_columns-1.png)

1. 속성 경로 선택기를 사용하여 CRXDE의 `jcr:content` 노드 아래에 속성 경로를 추가합니다.

   ![property_picker](assets/property_picker.png)

   또는 속성 경로 필드에 경로를 입력합니다.

   ![property_path](assets/property_path.png)

   사용자 정의 열을 더 추가하려면 추가를 탭/클릭하고 **[!UICONTROL 5,]** 6단계를 반복합니다.

1. 도구 모음에서 **[!UICONTROL 만들기를]** 탭/클릭합니다. 보고서 생성이 시작되었음을 알리는 메시지가 표시됩니다.

## 제거 서비스 구성 {#configure-purging-service}

더 이상 필요하지 않은 보고서를 제거하려면 웹 콘솔에서 DAM 보고서 삭제 서비스를 구성하여 해당 수량 및 연령을 기준으로 기존 보고서를 삭제합니다.

1. 에서 웹 콘솔(구성 관리자)에 `https://[aem_server]:[port]/system/console/configMgr`액세스합니다.
1. DAM 보고서 **[!UICONTROL 삭제 서비스 구성을]** 엽니다.
1. 필드에서 제거 서비스의 빈도(시간 간격)를 `scheduler.expression.name` 지정합니다. 보고서에 대한 연령 및 수량 임계값을 구성할 수도 있습니다.
1. 변경 사항을 저장합니다.
