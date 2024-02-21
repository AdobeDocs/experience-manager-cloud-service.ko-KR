---
title: EDS Forms에 대한 감사 페이지 구성
description: EDS Forms에 대한 감사 페이지 구성
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 5%

---


# 양식 블록 리디렉션 구성

기본 &quot;감사합니다&quot; 페이지 대신 웹 사이트의 다른 페이지로 리디렉션하도록 양식 블록을 구성하는 옵션이 있습니다. 다른 페이지를 리디렉션 대상으로 설정하려면

1. 편집할 `[EDS Project]/blocks/form/form.js` 페이지를 엽니다.

   ![감사 인사 노드용 코드](/help/edge/assets/change-thankyou-node.png)

1. 변경 `thankyou` 노드를 선택한 노드로 다음 줄 이동:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   예:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'home';
   ```

   >[!NOTE]
   >
   > Microsoft SharePoint 또는 Google Sheets의 Edge Delivery Service 프로젝트 폴더에 이름이 동일한 문서 페이지가 아직 만들어지지 않았는지 확인합니다.


1. 업데이트된 &#39;form.js&#39; 폴더 및 그 기본 파일을 GitHub의 Edge Delivery Service 프로젝트에 체크 인합니다. 이 업데이트를 통해 양식이 지정된 업데이트된 노드로 리디렉션됩니다.
