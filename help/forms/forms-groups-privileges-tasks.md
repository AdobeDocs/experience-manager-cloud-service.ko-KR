---
title: AEM Forms as a Cloud Service으로 제공되는 사용자 그룹은 무엇입니까?
description: 즉시 사용 가능한 사용자 그룹 및 각 그룹에 할당된 권한 목록
exl-id: bd66ce92-14d9-47fe-b5d3-022e3e468d25
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 24%

---

# 그룹 및 권한 {#aem-forms-on-osgi-groups-and-privileges}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html) |
| AEM as a Cloud Service | 이 문서 |

다음을 수행할 수 있습니다. [그룹 만들기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) 및 정책 할당 [사용자](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) 그룹에게 보냅니다. 이러한 정책은 그룹에 속한 사용자의 권한을 제어합니다.

설정한 후 [!DNL AEM Forms] as a Cloud Service으로 제공되며, 아래 표에 나열된 그룹은 [!DNL forms-users] 및 forms-power-user는 지정에 자동으로 사용할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td>그룹</td> 
   <td>권한</td> 
  </tr>
  <tr>
   <td>[!DNL forms-users] <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>적응형 Forms 만들기, 미리보기, 게시 및 제출</li> 
    <!-- <li>Create, preview, and publish interactive communications and document fragments</li> -->
     <li>AEM 인스턴스에 자산 업로드</li> 
     <li>테마 만들기</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>[!DNL forms-power-user]</td> 
   <td>
    <ul> 
     <li>Create, preview, publish, and submit Adaptive Forms</li> 
     <li>Create, preview, and publish interactive communications and document fragments</li> 
     <li>Create scripts for Adaptive Forms using code editor</li> 
     <li>Upload assets including scripts</li> 
     <li>Create themes</li> 
     <li>Import packages containing XDP</li> 
    </ul> </td> 
  </tr>
 <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Review submissions</li> 
     <li>Approve or reject submissions</li> 
    </ul> </td> 
  </tr> -->
  <tr>
   <td>[!DNL template-authors] <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>적응형 Forms 만들기 및 미리 보기 <!-- or interactive communications --> 템플릿</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>[!DNL fdm-authors]</p> </td> 
   <td>
    <ul> 
     <li>양식 데이터 모델 만들기 및 수정</li> 
    </ul> </td> 
  </tr>
  <!-- <tr>
   <td>cm-agent-users</td> 
   <td>
    <ul> 
     <li>Access Correspondence Management letters or interactive communications using Agent UI</li> 
    </ul> </td> 
  </tr> --> 
  <!-- <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> -->
    <!-- <li>Create an inbox application</li>  -->
    <!-- <li>Create a workflow model</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL workflow-users]</td> 
   <td>
    <ul> 
     <li>Use AEM inbox applications<br /> -->
     <!-- 
     <strong>Note: </strong>You must have cm-agent-users and [!DNL workflow-users] group assignments to access Interactive Communications Agent UI in AEM inbox.</li>  -->
    </ul> </td> 
  </tr>
  <tr>
   <td>[!DNL fd-administrators]</td> 
   <td>
    <ul> 
     <!-- <li>Configure PDF Generator</li> --> 
     <!-- <li>Configure Watched folder</li> -->
     <li>워크플로우 애플리케이션 관리</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 참고 항목

* [Cloud Service 환경에 온보드](/help/forms/setup-forms-cloud-service.md)
* [로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md)
* [AEM 6.5 Forms에서 Cloud Service로 마이그레이션](/help/forms/migrate-to-forms-as-a-cloud-service.md)
* [독립 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)



