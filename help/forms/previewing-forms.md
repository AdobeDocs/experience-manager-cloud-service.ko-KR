---
title: 적응형 양식을 미리 보는 방법
description: 사용자는 게시 또는 활성화 전에 양식을 미리 보고 예상치에 부합하도록 할 수 있습니다. 미리 보기 옵션은 지원되는 양식 유형에 따라 다를 수 있습니다.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 3%

---


# 양식 미리 보기 {#previewing-a-form}

## 개요 {#overview}

위치 [!DNL AEM Forms]저장소에 있는 양식 및 문서를 미리 볼 수 있습니다. 미리보기를 사용하면 최종 사용자에게 릴리스될 때 양식의 모양과 동작을 정확하게 파악할 수 있습니다.

양식을 미리 볼 때 대화형 인터페이스에서 렌더링되고 사용자가 양식에서 데이터를 채울 수 있습니다. 문서를 미리 볼 때 비대화형 모드로 렌더링되고 사용자만 문서를 볼 수 있습니다. 양식의 경우 사용자 지정 미리 보기 의 추가 옵션을 사용할 수 있습니다. 이 옵션을 사용하면 XML 파일의 데이터를 사용하여 양식을 미리 볼 수 있습니다. 데이터는 미리 보는 양식의 일부 필드 또는 모든 필드를 채웁니다.

다음 표에는 지원되는 여러 유형의 양식에 사용할 수 있는 미리 보기 옵션이 나열되어 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>에셋 유형</strong><br /> </td>
   <td><strong>사용 가능한 미리보기 옵션</strong><br /> </td>
  </tr>
  <tr>
   <td>문서</td>
   <td>PDF 미리보기</td>
  </tr>
  <tr>
   <td>PDF 양식</td>
   <td>PDF 미리 보기 및 데이터를 사용한 미리 보기<br /> </td>
  </tr>
  <tr>
   <td>적응형 양식</td>
   <td>데이터를 사용하여 HTML 미리 보기 및 HTML 미리 보기</td>
  </tr>
  <tr>
   <td>양식 템플릿</td>
   <td>PDF 미리 보기, 데이터를 사용한 PDF 미리 보기, HTML 미리 보기, 데이터를 사용한 HTML 미리 보기<br /> </td>
  </tr>
 </tbody>
</table>

## 양식 미리 보기 {#previewing-a-form-1}

1. 미리 보려는 에셋을 선택하고 미리 보기 를 클릭합니다 ![aem6forms_preview](assets/aem6forms_preview.png) ( 작업 도구 모음)을 참조하십시오.

   >[!NOTE]
   >
   >에셋을 선택하려면 기본 카드 보기에서 목록 보기로 전환합니다. 클릭 ![aem6forms_viewlist](assets/aem6forms_viewlist.png) 또는 ![aem6forms_viewcard](assets/aem6forms_viewcard.png) 보기를 전환합니다.

1. 미리보기 를 클릭하면 선택한 에셋 유형에 적용할 수 있는 미리보기 옵션이 나열됩니다. 선택한 에셋을 새 탭에서 렌더링하려면 원하는 옵션을 클릭합니다.

   옵션은 다음과 같습니다.

   * HTML으로 미리 보기
   * 데이터를 포함한 미리 보기
   * PDF으로 미리 보기(양식 서식 파일에 사용 가능)

## 데이터를 포함한 미리 보기 {#preview-with-data}

다음을 선택할 때 **데이터를 사용하여 미리 보기**&#x200B;을 입력하면 입력된 실제 데이터로 양식이 어떻게 보이는지 확인할 수 있습니다. [데이터로 미리 보기] 옵션을 사용하면 샘플 사용자 데이터가 포함된 XML을 업로드할 수 있습니다. 샘플 사용자 데이터는 선택한 형식으로 미리 보기 양식을 채우는 데 사용됩니다.

1. 에셋을 선택하고 미리보기 를 클릭합니다. ![aem6forms_preview](assets/aem6forms_preview.png), 및 선택 **데이터를 사용하여 미리 보기**.
1. 양식 미리 보기 대화 상자에서 FormData를 XML 파일로 제공합니다. 미리보기 를 클릭하여 XML에서 병합된 데이터로 양식을 렌더링합니다.

