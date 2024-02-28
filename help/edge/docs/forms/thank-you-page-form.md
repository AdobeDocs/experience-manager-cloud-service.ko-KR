---
title: EDS 양식의 감사 인사 페이지 구성
description: EDS 양식의 감사 인사 페이지 구성
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: ht
source-wordcount: '139'
ht-degree: 100%

---


# 양식 블록 리디렉션 구성

기본 “감사합니다” 페이지 대신 웹 사이트의 다른 페이지로 리디렉션되도록 양식 블록을 구성할 수 있습니다. 다른 페이지를 리디렉션 대상으로 설정하는 방법

1. 편집할 `[EDS Project]/blocks/form/form.js` 페이지를 엽니다.

   ![감사 인사 노드 코드](/help/edge/assets/change-thankyou-node.png)

1. 다음 줄의 `thankyou` 노드를 원하는 노드로 변경합니다.

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   예:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'home';
   ```

   >[!NOTE]
   >
   > Microsoft SharePoint 또는 Google Sheets의 Edge Delivery Service 프로젝트 폴더에 동일한 이름의 문서 페이지가 만들어졌는지 확인하십시오(아직 만들어지지 않은 경우).


1. 계속해서 업데이트된 &#39;form.js&#39; 폴더와 해당 폴더의 기본 파일을 GitHub의 Edge Delivery Service 프로젝트에 체크인하십시오. 이 업데이트를 통해 이제 양식이 지정된 대로 업데이트된 노드로 리디렉션됩니다.
