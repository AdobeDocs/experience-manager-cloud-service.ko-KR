---
title: CDN 구성 추가
description: Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 CDN 구성을 추가하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 6%

---


# CDN 구성 추가 {#add-cdn}

프로그램 내의 Adobe 관리 CDN에서 도메인을 SSL 인증서와 연결하려면 CDN(Content Delivery Network) 구성을 추가해야 합니다.

Adobe 관리 CDN의 경우 DV 인증서를 사용할 때 ACME 인증이 있는 사이트만 허용됩니다.

>[!IMPORTANT]
>
>각각 [사용자 정의 도메인 이름을 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)하고 [SSL 인증서를 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)했습니까? 그렇지 않은 경우 CDN 구성을 추가하려면 먼저 이 두 작업을 완료해야 합니다.

**CDN 구성을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 사용 사례에 따라 다음 중 하나를 수행합니다.

   | 사용 사례 | 단계 |
   | --- | --- |
   | Cloud Manager의 *기존* Edge Delivery 사이트에 CDN 구성을 추가하고 싶습니다 | a. 왼쪽 탐색 패널의 **서비스**&#x200B;에서 **Edge Delivery 사이트**&#x200B;를 클릭합니다.<br>b. Edge Delivery 테이블에서 연관된 도메인이 없는 행의 끝에 있는 줄임표를 클릭합니다.<br>c입니다. **CDN 구성**&#x200B;을 클릭합니다.  ![Edge Delivery 사이트에 대한 CDN 구성을 클릭합니다](/help/implementing/cloud-manager/assets/cm-eds-config-cdn.png) |
   | Cloud Manager에 CDN 구성을 추가하려고 합니다. | a. 왼쪽 탐색 패널의 **서비스**&#x200B;에서 **CDN 구성**&#x200B;을 클릭합니다.<br>b. CDN 구성 페이지의 오른쪽 상단 모서리에서 **추가**&#x200B;를 클릭합니다. |

1. **CDN 구성** 대화 상자의 **원본** 드롭다운 목록에서 다음 중 하나를 선택합니다.

   ![CDN 구성 대화 상자](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | 원본 | 설명 |
   | --- | --- |
   | Sites | Edge Delivery 사이트를 선택합니다. |
   | 환경 | AEM 설정 내에서 타깃팅할 특정 Cloud Service 환경을 선택합니다.<br>**계층** 드롭다운 목록에서 다음 중 하나를 선택합니다.<br>· 콘텐츠가 최종 사용자에게 제공되는 라이브 프로덕션 환경을 타깃팅하려면 **Publish**&#x200B;을(를) 선택합니다.<br>· 변경 내용을 실행하기 전에 테스트하는 스테이징 또는 비프로덕션 환경의 **미리 보기**&#x200B;를 선택합니다. |

1. 다음 중 하나를 선택하여 CDN 유형 및 관련 구성을 선택합니다.

   | CDN 유형 | 구성 세부 정보 |
   | --- | --- |
   | Adobe 관리 CDN | **구성 정보**&#x200B;에서 다음을 수행합니다.<br>a. **도메인** 드롭다운 목록에서 사용할 도메인 이름을 선택합니다.<br>드롭다운 목록에 사용 가능한 확인된 도메인이 없습니까? [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.<br>b. **SSL 인증서** 드롭다운 목록에서 사용할 인증서를 선택합니다.<br>드롭다운 목록에서 사용할 수 있는 SSL 인증서가 없습니까? [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오. |
   | 기타 CDN 공급자 | 사용 가능한 Adobe 관리 CDN이 아닌 자체 CDN 공급자를 사용하는 경우 이 옵션을 선택합니다.<br>**구성 정보**&#x200B;의 **도메인** 드롭다운 목록에서 사용할 도메인 이름을 선택합니다.<br>드롭다운 목록에 사용 가능한 확인된 도메인이 없습니까? [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. |

1. **저장**&#x200B;을 클릭합니다.
