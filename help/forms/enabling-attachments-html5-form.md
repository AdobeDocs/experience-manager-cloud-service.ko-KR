---
title: HTML5 양식에 대한 첨부 파일 활성화
description: 기본적으로 HTML5 양식에 대한 첨부 파일 지원이 비활성화되어 있습니다.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms,Mobile Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 4%

---

# HTML5 양식에 대한 첨부 파일 활성화 {#enabling-attachments-for-an-html-form}

<span class="preview"> HTML5 Forms 기능은 조기 액세스 프로그램의 일부로 제공됩니다. 액세스 권한을 요청하려면 공식(회사) 이메일 ID에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오.
</span>

HTML5 양식을 사용하여 첨부 파일을 업로드하고 미리 보고 제출할 수 있습니다. 첨부 파일 지원은 기본적으로 비활성화되어 있습니다. 첨부 파일 지원을 활성화하려면

1. [ 다중 선택 문자열 속성을 사용하여 ](/help/forms/custom-profile.md)사용자 지정 프로필`mfAttachmentOptions`을(를) 만듭니다. 첨부 파일 위젯의 옵션을 구성하려면 `mfAttachmentOptions` 속성의 각 문자열에 `property=value` 형식이 있어야 합니다. `property` 및 `value`은(는) 다음 값 중 하나를 가질 수 있습니다.

   | 속성 | 값 |
   |--- |---|
   | 다중 선택 | true 또는 false(기본적으로 true) |
   | fileSizeLimit | MB 단위(기본적으로 2MB). 예를 들어, 5입니다. |
   | buttonText | 팝업 창의 단추 텍스트(기본적으로 &quot;첨부&quot;) |
   | 동의 | 수락할 파일 유형을 쉼표로 구분한 목록(&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot;) |

   예:

   ![옵션 구성](assets/mfAttachmentOptions.png)

   필요에 따라 `mfAttachmentOptions` 속성에 대해 더 많은 사용자 지정 옵션을 지정할 수도 있습니다.

   >[!NOTE]
   >
   >Microsoft Internet Explorer 9에서 사용자는 지정된 제한보다 큰 파일을 첨부할 수 있습니다. 이는 알려진 문제입니다.

1. [메타데이터 편집기](/help/forms/manage-form-metadata.md)를 사용하여 HTML 5 양식에 대해 위에서 만든 사용자 지정 프로필을 선택하십시오.
1. 사용자 지정 프로필로 양식 템플릿을 렌더링하면 양식 도구 모음에 첨부 파일 아이콘이 표시됩니다.

   >[!NOTE]
   >
   >기본적으로 Forms 포털은 초안 및 첨부 파일 기능이 활성화된 사용자 지정 프로필을 제공합니다. **초안으로 저장** 프로필에 대한 자세한 내용은 [HTML5 양식을 초안으로 저장](/help/forms/saving-html5-form-draft.md)을 참조하십시오.

1. 첨부 아이콘을 클릭하면 첨부 선택 대화 상자가 나타납니다. 첨부 파일을 찾아 선택한 다음 **첨부**&#x200B;를 클릭합니다.

   >[!NOTE]
   >
   >첨부 파일을 미리 보려면 첨부 파일 이름을 클릭합니다.

   >[!NOTE]
   >
   >익명 사용자는 파일 미리 보기 옵션을 사용할 수 없습니다.

## 첨부 파일 제출 형식 {#attachment-submission-format}

첨부 파일이 활성화되면 HTML5 양식이 다중 부분 데이터를 제출합니다. 다중 부분 제출 데이터에는 두 부분 **dataXml** 및 **첨부 파일**&#x200B;이 있습니다.

>[!NOTE]
>
>이전 버전과의 호환성을 위해 `mfAllowAttachments` 옵션이 꺼져 있으면 HTML5 양식에서 다중 파트 데이터를 전송하지 않습니다. 단순 데이터 xml을 **application/xml** 형식으로 보냅니다.

mfAllowAttachments 플래그가 설정되어 있으면 [서비스 프록시 서비스 제출](/help/forms/service-proxy.md)에서 dataXml 및 첨부 파일이 포함된 다중 부분 데이터도 게시합니다.
