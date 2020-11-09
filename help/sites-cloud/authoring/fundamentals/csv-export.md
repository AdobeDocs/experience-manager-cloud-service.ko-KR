---
title: CSV로 내보내기
description: 로컬 시스템에서 페이지에 대한 정보를 CSV 파일로 내보내기
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 100%

---


# CSV로 내보내기 {#export-to-csv}

**CSV 보고서 만들기**&#x200B;를 사용하여 페이지에 대한 정보를 로컬 시스템의 CSV 파일로 내보낼 수 있습니다.

* 다운로드한 파일은 `export.csv`라고 합니다.
* 컨텐츠는 사용자가 선택한 속성에 따라 다릅니다.
* 내보내기에 대한 깊이와 함께 경로를 정의할 수 있습니다.

>[!NOTE]
>
>브라우저의 다운로드 기능 및 기본 대상이 사용됩니다.

**CSV 내보내기 만들기** 마법사를 사용하여 다음을 선택할 수 있습니다.

* 내보낼 속성
   * 메타데이터
      * 이름
      * 수정됨
      * 게시됨
      * 템플릿
      * 워크플로우
   * 번역
      * 번역됨
   * 분석
      * 페이지 보기 수
      * 고유 방문자 수
      * 페이지 시간
* 깊이
   * 상위 경로
   * 직접 하위만
   * 하위의 추가 수준
   * 수준

결과 `export.csv` 파일은 Excel 또는 기타 호환되는 애플리케이션에서 열 수 있습니다. 예를 들면 다음과 같습니다.

CSV 내보내기를 만들려면:

1. **사이트** 콘솔을 열고 필요한 경우 필요한 위치로 이동합니다.
   * **CSV 보고서** 만들기 옵션은 **Sites** 콘솔을 탐색(목록 보기)할 때 사용할 수 있습니다.
   * 이 옵션은 **만들기** 드롭다운 메뉴의 옵션입니다.

      ![CSV 만들기 옵션](/help/sites-cloud/authoring/assets/csv-create.png)

1. 도구 모음에서 **만들기**&#x200B;를 선택한 다음 **CSV 보고서**&#x200B;를 선택하여 마법사를 엽니다.

   ![CSV 내보내기 옵션](/help/sites-cloud/authoring/assets/csv-options.png)

1. 내보낼 필수 속성을 선택합니다.
1. **만들기**를 선택합니다.
   ![Excel에서 결과 CSV 내보내기](/help/sites-cloud/authoring/assets/csv-example.png)
