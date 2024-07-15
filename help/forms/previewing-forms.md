---
title: 적응형 양식을 미리 보는 방법
description: 사용자는 게시 또는 활성화 전에 양식을 미리 보고 예상치에 부합하도록 할 수 있습니다. 미리 보기 옵션은 지원되는 양식 유형에 따라 다를 수 있습니다.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 72235277-6c34-4341-9a10-02afa753e7f5
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 4%

---

# 양식 미리보기 {#previewing-a-form}

## 개요 {#overview}

[!DNL AEM Forms]에서 저장소에 있는 양식 및 문서를 미리 볼 수 있습니다. 미리보기를 사용하면 최종 사용자에게 릴리스될 때 양식의 모양과 동작을 정확하게 파악할 수 있습니다.

양식을 미리 볼 때 대화형 인터페이스에서 렌더링되고 사용자가 양식에서 데이터를 채울 수 있습니다. 문서를 미리 볼 때 비대화형 모드로 렌더링되고 사용자만 문서를 볼 수 있습니다. 양식의 경우 사용자 지정 미리 보기 의 추가 옵션을 사용할 수 있습니다. 이 옵션을 사용하면 XML 파일의 데이터를 사용하여 양식을 미리 볼 수 있습니다. 데이터는 미리 보는 양식의 일부 필드 또는 모든 필드를 채웁니다.

다음 표에는 지원되는 여러 유형의 양식에 사용할 수 있는 미리 보기 옵션이 나열되어 있습니다.

<table>
 <tbody>
  <tr>
   <td><strong>자산 유형</strong><br /> </td>
   <td><strong>사용 가능한 미리 보기 옵션</strong><br /> </td>
  </tr>
  <!--<tr>
   <td>Document</td>
   <td>PDF preview</td>
  </tr>-->
  <tr>
   <td>PDF 양식</td>
   <td>PDF 미리 보기 및 데이터 미리 보기<br /> </td>
  </tr>
  <tr>
   <td>적응형 양식</td>
   <td>데이터를 사용하여 HTML 미리 보기 및 HTML 미리 보기</td>
  </tr>
  <!--<tr>
   <td>Form Template</td>
   <td>PDF preview, PDF preview with Data, HTML preview, HTML preview with Data<br /> </td>
  </tr>-->
 </tbody>
</table>

## 양식 미리보기 {#previewing-a-form-1}

1. 미리 보려는 자산을 선택하고 작업 도구 모음에서 ![aem6forms_preview](assets/aem6forms_preview.png) 미리 보기를 클릭합니다.

   >[!NOTE]
   >
   >에셋을 선택하려면 기본 카드 보기에서 목록 보기로 전환합니다. 보기를 전환하려면 ![aem6forms_viewlist](assets/aem6forms_viewlist.png) 또는 ![aem6forms_viewcard](assets/aem6forms_viewcard.png)을(를) 클릭하십시오.

1. 미리보기 를 클릭하면 선택한 에셋 유형에 적용할 수 있는 미리보기 옵션이 나열됩니다. 선택한 에셋을 새 탭에서 렌더링하려면 원하는 옵션을 클릭합니다.

   옵션은 다음과 같습니다.

   * HTML으로 미리 보기
   * 데이터를 포함한 미리 보기
     <!--* Preview as PDF (available for form templates)-->

## 데이터를 포함한 미리 보기 {#preview-with-data}

**데이터로 미리 보기**&#x200B;를 선택하면 양식에 입력된 실제 데이터가 어떻게 표시되는지 볼 수 있습니다. [데이터로 미리 보기] 옵션을 사용하면 샘플 사용자 데이터가 포함된 XML을 업로드할 수 있습니다. 샘플 사용자 데이터는 선택한 형식으로 미리 보기 양식을 채우는 데 사용됩니다.

1. 자산을 선택하고 미리 보기 ![aem6forms_preview](assets/aem6forms_preview.png)를 클릭한 다음 **데이터로 미리 보기**&#x200B;를 선택합니다.
1. 양식 미리 보기 대화 상자에서 FormData를 XML 파일로 제공합니다. 미리보기 를 클릭하여 XML에서 병합된 데이터로 양식을 렌더링합니다.
