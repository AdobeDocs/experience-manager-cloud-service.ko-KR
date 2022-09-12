---
title: 양식 미리 보기
seo-title: Previewing a form
description: 양식을 게시하거나 활성화하기 전에 미리 보고 예상대로 양식을 충족할 수 있습니다. 미리 보기 옵션은 지원되는 양식 유형에 따라 달라질 수 있습니다.
seo-description: You can preview your forms before publishing or activating to ensure it meets the expectations. Preview options may vary across the supported form types.
uuid: 9ec359ea-f518-441c-9c3d-e3c1ea07a532
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 3%

---


# 양식 미리 보기 {#previewing-a-form}

## 개요 {#overview}

in [!DNL AEM Forms]저장소에 있는 양식 및 문서를 미리 볼 수 있습니다. 미리 보기는 최종 사용자에게 양식을 릴리스할 때 양식이 어떻게 표시되고 동작하는지 정확히 확인하는 데 도움이 됩니다.

양식을 미리 볼 때 대화형 인터페이스로 렌더링되고 사용자는 데이터로 양식을 채울 수 있습니다. 문서를 미리 볼 때 비대화형 모드로 렌더링되고 사용자는 문서를 볼 수만 있습니다. 양식의 경우 사용자 지정 미리 보기 의 추가 옵션을 사용할 수 있습니다. 이 옵션을 사용하면 XML 파일의 데이터를 사용하여 양식을 미리 볼 수 있습니다. 데이터는 미리 보고 있는 양식의 일부 또는 모든 필드를 채웁니다.

다음 표에는 지원되는 양식의 여러 유형에 사용할 수 있는 미리 보기 옵션이 나와 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>에셋 유형</strong><br /> </td>
   <td><strong>사용 가능한 미리 보기 옵션</strong><br /> </td>
  </tr>
  <tr>
   <td>문서</td>
   <td>PDF 미리 보기</td>
  </tr>
  <tr>
   <td>PDF 양식</td>
   <td>데이터를 사용하여 PDF 미리 보기 및 미리 보기<br /> </td>
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

1. 미리 볼 자산을 선택하고 미리 보기를 클릭합니다 ![aem6forms_preview](assets/aem6forms_preview.png) 를 클릭합니다.

   >[!NOTE]
   >
   >자산을 선택하려면 기본 카드 보기에서 목록 보기로 전환합니다. 클릭 ![aem6forms_viewlist](assets/aem6forms_viewlist.png) 또는 ![aem6forms_viewcard](assets/aem6forms_viewcard.png) 보기를 전환하려면 다음을 수행하십시오.

1. 미리 보기 를 클릭하면 선택한 자산 유형에 적용할 수 있는 가능한 미리 보기 옵션이 나열됩니다. 원하는 옵션을 클릭하여 선택한 자산을 새 탭에서 렌더링합니다.

   옵션은 다음과 같습니다.

   * HTML으로 미리 보기
   * 데이터를 포함한 미리 보기
   * PDF으로 미리 보기(양식 템플릿에 사용 가능)

## 데이터를 포함한 미리 보기 {#preview-with-data}

선택 시 **데이터를 사용하여 미리 보기**&#x200B;에 입력된 실제 데이터로 양식이 어떻게 보이는지 확인할 수 있습니다. 데이터를 사용하여 미리 보기 옵션을 사용하면 샘플 사용자 데이터가 포함된 XML을 업로드할 수 있습니다. 샘플 사용자 데이터는 선택한 형식으로 미리 보기 양식을 채우는 데 사용됩니다.

1. 자산을 선택하고 미리 보기 를 클릭합니다 ![aem6forms_preview](assets/aem6forms_preview.png), 을(를) 선택하고 을(를) 선택합니다. **데이터를 사용하여 미리 보기**.
1. [양식 미리 보기] 대화 상자에서 FormData를 XML 파일로 제공합니다. XML의 병합된 데이터를 사용하여 양식을 렌더링하려면 미리 보기 를 클릭합니다.

