---
title: 디자이너에서 페이지 제로 콘텐츠 변경
seo-title: Changing Page Zero content in Designer
description: Adobe PDF이 아닌 뷰어에서 XFA PDF의 페이지 0에 표시되는 메시지를 볼 때 어떻게 변경할 수 있는지 알고 있습니까?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: ac23fb21-3f15-48ea-aeeb-4ecc12b771ac
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 56b6a573-8aba-43e7-acb7-c2da45869d95
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---


# 디자이너에서 페이지 제로 콘텐츠 변경 {#changing-page-zero-content-in-designer}

Adobe PDF이 아닌 뷰어가 있는 경우(예: 의 기본 PDF 뷰어) 기본적으로 페이지 제로 컨텐츠가 표시됩니다 [!DNL Chrome] 또는 [!DNL Firefox]에서는 PDF/XFA 양식의 컨텐츠를 읽을 수 없습니다. 기본 페이지 제로 메시지는 아래에 표시되어 있습니다.

![defaultpage0message](assets/defaultpage0message.png)

[!DNL AEM Forms] 디자이너 버전을 사용하면 페이지 0에 표시되는 메시지를 변경할 수 있습니다. 페이지 제로 메시지를 변경하려면 다음 단계를 수행하십시오.

1. 다음 권한이 있는지 확인합니다. [!DNL AEM Forms] 설치된 Designer 버전입니다. 디자이너의 정보 화면에서 버전을 확인할 수 있습니다.

1. 페이지 제로 컨텐츠를 변경할 양식을 엽니다.

1. 클릭 **[!UICONTROL 파일]** > **[!UICONTROL 양식 속성]**.

1. 에서 [!UICONTROL 양식 속성] 대화 상자 ![plus](assets/plus.png) (더하기 아이콘)을 클릭하여 사용자 지정 속성을 추가합니다.

1. 지정 **_pagezerocontent** 를 속성의 이름으로 지정합니다.
1. 새 페이지 제로 메시지를 리치 텍스트 형식으로 값으로 추가합니다. 예:


   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. 양식을 PDF으로 저장합니다.

1. 브라우저에서 PDF 양식을 보고 메시지가 업데이트되었는지 확인합니다. 위의 예제 값은 다음과 같이 나타납니다.

   ![changedmessage](assets/changedmessage.png)

>[!NOTE]
>
>양식을 다시 열면 방금 만든 사용자 지정 속성이 양식 속성 대화 상자에 제대로 표시되지 않을 수 있습니다. 하지만 제대로 작동하며 업데이트된 페이지 제로 메시지가 양식에 표시됩니다.
