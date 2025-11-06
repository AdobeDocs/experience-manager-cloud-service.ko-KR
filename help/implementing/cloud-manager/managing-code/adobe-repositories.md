---
title: Cloud Manager에서 Adobe 저장소 추가
description: Cloud Manager에서 Adobe 관리 저장소를 추가하는 방법을 알아봅니다.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%

---

# Cloud Manager에서 Adobe 저장소 추가 {#adobe-repositories}

Cloud Manager에서 Adobe 관리 저장소를 추가하는 방법을 알아봅니다.

**저장소** 페이지를 사용하면 선택한 프로그램에 추가 Adobe 관리 저장소를 쉽게 추가할 수 있습니다.

**Cloud Manager에서 Adobe 저장소를 추가하려면 다음 작업을 수행하십시오.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 Adobe 관리 저장소를 추가할 적절한 조직과 프로그램을 선택합니다.

1. 사이드 메뉴의 **프로그램 개요** 페이지에서 ![폴더 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **저장소** 탭을 클릭합니다.

1. 오른쪽 상단 근처의 **저장소** 페이지에서 **저장소 추가**&#x200B;를 클릭합니다.

   ![저장소 추가 버튼](assets/add-repository.png)

1. **저장소 추가** 대화 상자에서 **Adobe 저장소**&#x200B;가 저장소 유형으로 선택되어 있는지 확인합니다.

1. 각 텍스트 필드에 다음 사항을 입력합니다.

   * **저장소 이름** - 새 저장소의 표현적인 이름입니다.
   * **저장소 URL 미리보기** - 저장소 인프라가 이미 구축되고 Adobe에서 완벽히 통합, 관리되고 있으므로 URL 경로를 입력하거나 기존 경로를 편집할 필요가 없습니다.
   * **설명(옵션)** - 저장소에 대한 자세한 설명입니다.

   ![저장소 추가 대화 상자](assets/add-adobe-repository.png)

1. **저장**을 클릭합니다.
새 저장소가 **저장소** 페이지의 테이블에 표시됩니다.

이제 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 연결하거나 [**저장소** 페이지](managing-repositories.md) 내에서 관리할 수 있습니다.

>[!TIP]
>
>또한 자신이 관리하는 GitHub 저장소를 [비공개 저장소](private-repositories.md)로 추가할 수도 있습니다.
