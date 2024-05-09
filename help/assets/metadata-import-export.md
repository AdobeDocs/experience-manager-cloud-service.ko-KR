---
title: 자산 메타데이터 일괄적으로 가져오기 및 내보내기
description: 이 문서에서는 메타데이터를 일괄적으로 가져오고 내보내는 방법에 대해 설명합니다.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: fb70a068-3ba3-4459-952d-79155d286c42
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 10%

---

# 자산 메타데이터 일괄적으로 가져오기 및 내보내기 {#import-and-export-asset-metadata-in-bulk}

Adobe Experience Manager Assets을 사용하면 CSV 파일을 사용하여 에셋 메타데이터를 일괄적으로 가져올 수 있습니다. CSV 파일을 가져와서 최근에 업로드한 에셋 또는 기존 에셋에 대한 대량 업데이트를 수행할 수 있습니다. 자산 메타데이터를 CSV 형식으로 서드파티 시스템에서 일괄로 수집할 수도 있습니다.

## 메타데이터 가져오기 {#import-metadata}

메타데이터 가져오기는 비동기적이며 시스템 성능을 방해하지 않습니다. 에셋 마이크로서비스를 사용하는 메타데이터 원본에 쓰기 활동으로 인해 여러 에셋에 대한 메타데이터를 동시에 업데이트하면 리소스가 많이 소모될 수 있습니다. Adobe은 다른 사용자의 성능에 영향을 주지 않도록 린 서버 사용 중 대량 작업을 계획할 것을 권장합니다.

>[!NOTE]
>
>사용자 지정 네임스페이스에 대한 메타데이터를 가져오려면 먼저 네임스페이스를 등록합니다.

1. 다음으로 이동 [!DNL Assets] 사용자 인터페이스, 선택 **[!UICONTROL 만들기]** 도구 모음에서 를 선택하고 **[!UICONTROL 메타데이터]** 메뉴에서 삭제할 수 있습니다.
1. 다음에서 **[!UICONTROL 메타데이터 가져오기]** 페이지, 클릭 **[!UICONTROL 파일 선택]**. Select the CSV file with the metadata.
1. 다음 매개 변수를 제공합니다.

   | 매개변수 | 설명 |
   | ---------------------- | ------- |
   | 일괄 처리 크기 | 메타데이터를 가져올 일괄 처리의 자산 수입니다. 기본값은 50입니다. 최대값은 100입니다. |
   | 필드 분리 기호 | 기본값은 입니다. `,` (쉼표). 다른 문자를 지정할 수 있습니다. |
   | 다중 값 구분 기호 | 메타데이터 값에 대한 구분 기호입니다. 기본값은 입니다. `|`. |
   | 워크플로우 실행 | 기본적으로 False입니다. 로 설정된 경우 `true` 및 기본 설정은 이진 XMP 데이터에 메타데이터를 작성하는 DAM 메타데이터 WriteBack 워크플로우에 적용됩니다. 워크플로우를 활성화하면 시스템 속도가 느려집니다. |
   | 자산 경로 열 이름 | 자산이 있는 CSV 파일의 열 이름을 정의합니다. |

1. 선택 **[!UICONTROL 가져오기]** 을 클릭합니다. 메타데이터를 가져오면 알림이 알림 받은 편지함으로 전송됩니다. 에셋 속성 페이지로 이동하여 에셋에 대한 메타데이터 값을 올바르게 가져왔는지 확인합니다.

1. 날짜 및 타임스탬프를 추가하여 메타데이터를 가져오려면 `YYYY-MM-DDThh:mm:ss.fff-00:00` 날짜 및 시간 형식 날짜 및 시간은 다음으로 구분됨 `T`, `hh` 은 24시간 형식의 시간입니다. `fff` 은(는) 나노초이며, `-00:00` 시간대 오프셋입니다. 예를 들어, `2020-03-26T11:26:00.000-07:00` 은(는) 2020년 3월 26일 11시입니다.:26:오전 0시(태평양 표준시)

   * 날짜 형식은 열 제목과 열 머리글의 형식에 따라 다릅니다. 예를 들어 날짜가 형식이 잘못된 경우 `yyyy-MM-dd'T'HH:mm:ssXXX` 그러면 각 열 헤더가 `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX`.
   * 기본 날짜 형식은 입니다. `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`.

<!-- Hidden via cqdoc-17869>

>[!CAUTION]
>
>If the date format does not match `YYYY-MM-DDThh:mm:ss.fff-00:00`, the date values are not set. The date formats of exported metadata CSV file is in the format `YYYY-MM-DDThh:mm:ss-00:00`. If you want to import it, convert it to the acceptable format by adding the nanoseconds value denoted by `fff`.
-->

## 메타데이터 내보내기 {#export-metadata}

여러 에셋에 대한 메타데이터를 CSV 형식으로 내보낼 수 있습니다. 메타데이터는 비동기적으로 내보내지며 시스템 성능에 영향을 주지 않습니다. 메타데이터를 내보내려면 Experience Manager이 에셋 노드의 속성을 통과합니다 `jcr:content/metadata` 및 하위 노드를 포함하여 메타데이터 속성을 CSV 파일로 내보냅니다.

메타데이터를 일괄적으로 내보내는 몇 가지 사용 사례는 다음과 같습니다.

* 자산을 마이그레이션할 때 서드파티 시스템에서 메타데이터를 가져옵니다.
* 자산 메타데이터를 더 광범위한 프로젝트 팀과 공유합니다.
* 규정 준수를 위해 메타데이터를 테스트하거나 감사합니다.
* 별도의 현지화를 위해 메타데이터를 외부화합니다.

>[!NOTE]
>
>메타데이터 내보내기는 Microsoft Excel의 최대 워크시트 크기에 해당하는 1,048,575개의 자산으로 제한됩니다. 내보낸 계층에 이 수 이상의 에셋이 포함된 경우 처음 1,048,575개의 에셋의 메타데이터만 CSV 파일에 포함됩니다.

1. 메타데이터를 내보내려는 자산이 포함된 자산 폴더를 선택합니다. 도구 모음에서 를 선택합니다. **[!UICONTROL 메타데이터 내보내기]**.
1. 메타데이터 내보내기 대화 상자에서 CSV 파일의 이름을 지정합니다. 하위 폴더에 있는 에셋에 대한 메타데이터를 내보내려면 을 선택합니다. **[!UICONTROL 하위 폴더에 자산 포함]**.

   ![폴더에 있는 모든 자산의 메타데이터를 내보내는 인터페이스 및 옵션](assets/export_metadata_page.png "폴더에 있는 모든 자산의 메타데이터를 내보내는 인터페이스 및 옵션")

1. 원하는 옵션을 선택합니다. 파일 이름을 입력하고 필요한 경우 날짜를 입력합니다.

1. 다음에서 **[!UICONTROL 내보낼 속성]** 필드에서 모든 속성을 내보내는지 특정 속성을 내보내는지 여부를 지정합니다. 내보낼 선택적 속성 을 선택하는 경우 원하는 속성을 추가합니다.

1. 도구 모음에서 를 선택합니다. **[!UICONTROL 내보내기]**. 메타데이터 내보내기를 확인하는 메시지가 표시됩니다. 메시지를 닫습니다.
1. Open the inbox notification for the export job. Select the job and click **[!UICONTROL Open]** from the toolbar. 메타데이터가 포함된 CSV 파일을 다운로드하려면 다음을 선택합니다. **[!UICONTROL CSV 다운로드]** 을 클릭합니다. **[!UICONTROL 닫기]**&#x200B;를 클릭합니다.

   ![일괄로 내보낸 메타데이터가 포함된 CSV 파일을 다운로드하는 대화 상자](assets/csv_download.png)

   *그림: 일괄 내보낸 메타데이터가 포함된 CSV 파일을 다운로드하는 대화 상자*

**추가 참조**

* [자산 번역](translate-assets.md)
* [Assets HTTP API](mac-api-assets.md)
* [자산이 지원되는 파일 형식](file-format-support.md)
* [자산 검색](search-assets.md)
* [연결된 자산](use-assets-across-connected-assets-instances.md)
* [자산 보고서](asset-reports.md)
* [메타데이터 스키마](metadata-schemas.md)
* [자산 다운로드](download-assets-from-aem.md)
* [메타데이터 관리](manage-metadata.md)
* [검색 패싯](search-facets.md)
* [컬렉션 관리](manage-collections.md)
* [AEM 및 Dynamic Media에 자산 게시](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [에셋을 일괄로 가져올 때 메타데이터 가져오기](/help/assets/add-assets.md#asset-bulk-ingestor)
