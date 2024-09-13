---
title: Cloud Manager에 Edge Delivery 사이트 추가
description: 프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery 사이트를 추가하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 2%

---


## Cloud Manager에 Edge Delivery 사이트 추가 {#eds-add-site}

프로덕션 프로그램에 Edge Delivery Services을 추가하면 Edge Delivery Services 라이선스가 적용됩니다.

개요 페이지에 **Edge Delivery**&#x200B;이라는 클릭 가능한 탭이 표시됩니다. 탭을 클릭하면 추가한 각 Edge Delivery 사이트를 나열하는 테이블이 표시됩니다. 왼쪽 탐색 패널의 **서비스** 그룹화 아래에 **Edge Delivery 사이트**&#x200B;라는 메뉴 옵션이 있습니다.

![왼쪽 탐색 패널 및 Edge Delivery 게재 탭 오른쪽에 있는 Edge Delivery 탭에 Publish 사이트를 표시하는 개요 페이지](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**Cloud Manager에 Edge Delivery 사이트를 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery 사이트를 추가할 Edge Delivery Services이 구성된 프로그램을 선택합니다.
1. 다음 중 하나를 수행합니다.
   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. 그런 다음 페이지의 오른쪽 아래 모서리에서 **Edge Delivery 사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     위의 이미지에 표시된 **Edge Delivery 할 일 목록**&#x200B;은(는) Edge Delivery 사용을 시작하는 데 도움이 되는 선택적 온보딩 체크리스트 안내서입니다. [Edge Delivery 할 일 목록](#ed-todo-list)을 참조하세요.

   * 페이지 왼쪽 상단 모서리에서 햄버거 아이콘을 클릭하여 왼쪽 탐색 메뉴를 표시합니다. **서비스** 제목에서 **Edge Delivery 사이트**&#x200B;를 클릭합니다. 페이지의 오른쪽 상단 근처에 있는 **사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery Sites 단추에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. **Edge Delivery 사이트 추가** 대화 상자에서 다음을 수행합니다.

   | 텍스트 필드 | 할 일 |
   | --- | --- |
   | 사이트 이름 | 추가하려는 Edge Delivery 사이트의 이름을 입력합니다. 이 이름은 Cloud Manager 내에서 사이트의 고유 식별자 역할을 합니다. |
   | 저장소 URL | 이 필드는 웹 사이트의 코드가 저장된 Git 저장소를 나타냅니다.<br>Edge Delivery 사이트에 필요한 파일 및 리소스(HTML, CSS, JavaScript 및 기타 웹 자산 등)가 포함된 Git 저장소의 URL을 입력합니다. 이렇게 구성하면 Cloud Manager이 배포 프로세스 중에 해당 저장소에서 코드를 가져올 수 있습니다. |
   | 사이트 설명 (선택 사항) | 추가하려는 Edge Delivery 사이트에 대한 간략한 설명을 입력합니다.<br>이 설명을 통해 사이트를 식별하고 구별할 수 있으므로 추가한 다른 사이트를 보다 쉽게 관리하고 인식할 수 있습니다. 사이트의 목적, 콘텐츠 또는 그 기능이나 범위를 명확하게 하는 데 도움이 되는 기타 관련 정보에 대한 세부 정보를 포함할 수 있습니다. |

1. 대화 상자의 오른쪽 아래 모서리에서 **추가**&#x200B;를 클릭합니다.

1. **저장소 소유권 확인** 대화 상자에서 다음을 수행합니다.

   | 단계 | 설명 |
   | --- | --- |
   | 1 | **저장소 URL** 필드에 나열된 Git 저장소의 `main` 분기에 위치 경로가 있는 파일을 추가하십시오. 필요한 경우 복사 아이콘을 클릭하여 경로를 클립보드에 복사합니다.<br> 위치 경로는 <br>`well-known/adobe/cloudmanager-challenge.txt`입니다.<br><br>위치 경로의 시작 위치에 마침표를 *추가하지 않음*, 위치 경로 위치:<br>`.well-known/adobe/cloudmanager-challenge.txt` |
   | 2 | 생성된 코드를 1단계에서 만든 파일에 추가합니다. 필요한 경우 복사 아이콘을 클릭하여 코드를 클립보드에 복사합니다. |
   | 3 | Git 저장소에서 가져오기 요청을 만든 다음 병합하여 코드를 커밋합니다. |

1. **확인**&#x200B;을 클릭합니다. 저장소가 확인되면 Edge Deliver Sites 테이블의 상태가 내부에 흰색 확인 표시가 있는 녹색 원으로 변경됩니다.
