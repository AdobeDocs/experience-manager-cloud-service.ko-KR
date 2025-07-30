---
title: 도메인 매핑 추가
description: Edge Delivery 사이트 또는 Cloud Manager 환경에 대한 도메인 매핑을 추가하는 방법에 대해 알아봅니다.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: bf519f03b9be56c46c1ca04420169eaf221478cc
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 8%

---


# 도메인 매핑 추가 {#add-domain-mapping}

프로그램 내의 Adobe 관리 CDN에서 SSL 인증서와 도메인을 연결하려면 CDN(Content Delivery Network) 구성을 추가해야 합니다.

Adobe 관리 CDN의 경우 DV SSL 인증서를 사용할 때 ACME 인증이 있는 사이트만 허용됩니다.

>[!IMPORTANT]
>
>각각 [사용자 정의 도메인 이름을 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)하고 [SSL 인증서를 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)했습니까? 그렇지 않은 경우 CDN 구성을 추가하려면 먼저 이 두 작업을 완료해야 합니다.

[Adobe 관리 CDN](https://www.aem.live/docs/byo-cdn-adobe-managed)도 참조하세요.

**도메인 매핑을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. 사용 사례에 따라 다음 중 하나를 수행합니다.

   | 사용 사례 | 단계 |
   | --- | --- |
   | Cloud Manager의 *기존* Edge Delivery 사이트에 CDN 구성을 추가하고 싶습니다 | a. 왼쪽 메뉴의 **서비스**&#x200B;에서 ![웹 페이지 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery 사이트**&#x200B;를 클릭합니다.<br>b. Edge Delivery 테이블에서 연결된 도메인이 없는 행의 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.<br>c입니다. **CDN 구성**&#x200B;을 클릭합니다. |
   | Cloud Manager에 CDN 구성을 추가하려고 합니다. | a. 왼쪽 메뉴의 **서비스**&#x200B;에서 ![소셜 네트워크 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **도메인 매핑**&#x200B;을 클릭합니다.<br>b. 도메인 매핑 페이지의 오른쪽 상단 모서리에서 **추가**&#x200B;를 클릭합니다. |

1. **CDN 구성** 대화 상자의 **원본** 드롭다운 목록에서 다음 중 하나를 선택합니다.

   ![CDN 구성 대화 상자](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Origin | 설명 |
   | --- | --- |
   | Sites | Edge Delivery 사이트를 선택합니다. |
   | 환경 | AEM 설정 내에서 타깃팅할 특정 Cloud Service 환경을 선택합니다.<br>**계층** 드롭다운 목록에서 다음 중 하나를 선택합니다.<br>· 콘텐츠가 최종 사용자에게 제공되는 라이브 프로덕션 환경을 타깃팅하려면 **게시**&#x200B;를 선택합니다.<br>· 변경 내용을 실행하기 전에 테스트하는 스테이징 또는 비프로덕션 환경의 **미리 보기**&#x200B;를 선택합니다. |

1. 다음 중 하나를 선택하여 CDN 유형 및 관련 구성을 선택합니다.

   | CDN 유형 | 구성 세부 정보 |
   | --- | --- |
   | Adobe 관리 CDN | **구성 정보**&#x200B;에서 다음을 수행합니다.<br>a. **도메인** 드롭다운 목록에서 사용할 도메인 이름을 선택합니다.<br>드롭다운 목록에 사용 가능한 확인된 도메인이 없습니까? [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.<br>b. **SSL 인증서** 드롭다운 목록에서 사용할 인증서를 선택합니다.<br>드롭다운 목록에서 사용할 수 있는 SSL 인증서가 없습니까? [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오. |
   | 기타 CDN 공급자 | 사용 가능한 Adobe 관리 CDN이 아닌 자체 CDN 공급자를 사용하는 경우 이 옵션을 선택합니다.<br>**구성 정보**&#x200B;의 **도메인** 드롭다운 목록에서 사용할 도메인 이름을 선택합니다.<br>드롭다운 목록에 사용 가능한 확인된 도메인이 없습니까? [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. |

1. **저장**&#x200B;을 클릭합니다.

   Adobe에서는 도메인 매핑을 테스트할 것을 권장합니다.

## 도메인 매핑 테스트 {#test-domain-mapping}

공개 DNS 전파를 기다리지 않고 Adobe 관리 CDN에서 새 도메인 매핑이 활성 상태인지 확인할 수 있습니다.

DNS 확인을 재정의하고 CDN 가장자리를 바로 가리키는 **curl** 명령을 실행합니다.

```bash
curl -svo /dev/null https://www.example.com \
--resolve www.example.com:443:151.101.3.10
```

* **`www.example.com`**&#x200B;을(를) 도메인으로 바꾸십시오.
* 이 매핑을 위해 **151.101.3.10**&#x200B;을(를) Cloud Manager에 표시된 Edge IP 주소로 대체하십시오.

`--resolve` 플래그는 지정된 IP에 요청을 강제 적용하고 도메인의 인증서 및 라우팅이 올바르게 설치된 후에만 성공을 반환합니다.

