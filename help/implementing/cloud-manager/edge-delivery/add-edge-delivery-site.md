---
title: Cloud Manager에 Edge Delivery 사이트 추가
description: 프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery 사이트를 추가하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: db661281831dcb07491dca16e73e835b487814a6
workflow-type: ht
source-wordcount: '495'
ht-degree: 100%

---

# Cloud Manager에 Edge Delivery 사이트 추가 {#adding}

프로덕션 프로그램에 Edge Delivery 사이트를 추가하면 Edge Delivery Services 라이선스가 적용됩니다.

[Edge Delivery 프로젝트에 대한 지원 티켓을 등록](/help/edge/overview.md##support-ticket)하려면 Cloud Manager에 Edge Delivery 사이트를 추가해야 합니다.

[Cloud Manager에서의 Edge Delivery Services 소개](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)도 참조하십시오.

**Cloud Manager에 Edge Delivery 사이트를 추가하려면:**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. 다음 중 하나를 수행하십시오.

   * **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다. 그런 다음 페이지의 오른쪽 하단 근처에서 **Edge Delivery 사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery 탭에서 Edge Delivery 사이트 추가](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * 페이지의 왼쪽 상단에서 ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 왼쪽 사이드 메뉴를 표시합니다.
**서비스** 제목 아래 ![Web page icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**를 클릭합니다.
페이지의 오른쪽 상단 근처에서 **사이트 추가**&#x200B;를 클릭합니다.

     ![Edge Delivery Sites 버튼에서 Edge Delivery Sites 추가](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. **Edge Delivery 사이트 추가** 대화 상자에서 필수 필드에 다음 정보를 입력합니다.

   | 텍스트 필드 | 설명 |
   | - | --- |
   | 사이트 이름 | 추가하려는 Edge Delivery 사이트의 이름을 입력합니다.<br>이 이름은 Cloud Manager 내 사이트의 고유 식별자 역할을 합니다. |
   | 저장소 URL | 웹 사이트 코드가 저장된 Git 저장소를 입력합니다.<br>이 필드를 통해 Cloud Manager는 배포 프로세스 중에 해당 저장소에서 코드를 가져올 수 있습니다. |
   | 사이트 설명 (선택 사항) | 추가하려는 Edge Delivery 사이트에 대한 간략한 설명을 입력합니다.<br>설명은 사이트를 식별하고 차별화하는 데 도움이 되며, 추가한 다른 사이트 간에 관리하고 인식하는 것이 더 쉬워집니다. |

1. 대화 상자의 오른쪽 하단에 있는 **추가**&#x200B;를 클릭합니다.

1. **저장소 소유권 확인** 대화 상자에서 다음 단계를 수행하여 저장소 소유권을 확인합니다.

   | 단계 번호 | 설명 |
   | - | - |
   | **1** | 경로가 있는 파일과 이름이 `well-known/adobe/cloudmanager-challenge.txt`인 파일을 **저장소 URL** 필드에 나열된 Git 저장소의 `main` 분기에 추가합니다. 위치 경로의 시작 부분에 마침표를 추가하지 *마십시오*.<br>필요한 경우 ![복사](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)를 클릭하여 경로를 클립보드에 복사합니다. |
   | **2** | 2단계의 텍스트 필드에 표시된 코드를 1단계에서 방금 만든 파일에 추가합니다.<br>필요한 경우 ![복사](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg)를 클릭하여 코드를 클립보드에 복사합니다. |
   | **3** | 방금 만든 변경 사항의 가져오기 요청을 Git 저장소에 만든 다음 `main`에 병합하여 코드를 커밋합니다. |

1. **확인**&#x200B;을 클릭합니다.

저장소가 검증되면 Edge Delivery 사이트 테이블의 상태가 업데이트됩니다. 내부에 흰색 확인 표시가 있는 녹색 원은 상태를 나타냅니다.

같은 테이블에서 ![Information about Edge Delivery site](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg)를 클릭하여 사이트 세부 정보를 확인합니다. 이 정보에는 검증된 저장소 URL과 미리보기 및 프로덕션 웹 사이트 URL이 포함됩니다.
