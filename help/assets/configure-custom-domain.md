---
title: 게시 계층에 대한 사용자 정의 도메인 구성
description: Adobe Cloud Manager에서 게시 계층에 대한 사용자 정의 도메인을 구성하는 방법을 알아봅니다.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 20%

---

# 게시 계층에 대한 사용자 정의 도메인 구성{#configure-custom-domain}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>OpenAPI 기능이 포함된 Dynamic Media 안내서가 이제 PDF 포맷으로 제공됩니다. 전체 안내서를 다운로드하고 Adobe Acrobat AI 어시스턴트를 사용하여 쿼리에 답변합니다.
>
>[!BADGE OpenAPI 기능이 포함된 Dynamic Media 안내서 PDF]{type=Informative url="https://helpx.adobe.com/kr/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Adobe Cloud Manager에서 사용자 정의 도메인을 추가하여 웹 사이트를 돋보이게 할 수 있습니다. AEM as a Cloud Service에는 기본 도메인이 제공되지만 필요에 따라 사용자 정의할 수 있습니다.

## 시작하기에 앞서

* 다중 SAN(주체 대체 이름) TLS 또는 SSL 인증서가 있어야 합니다.
* SSL 인증서에는 동일한 도메인 내의 게시 계층에 대해 매핑된 인증서와 구별되는 SAN이 있어야 합니다.
* 인증서 정책은 DV(도메인 유효성 검사) 정책이 아닌 EV(확장 유효성 검사) 또는 OV(조직 유효성 검사) 정책을 준수해야 합니다.


## 게시 계층에 대한 사용자 정의 도메인 구성

1. **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL 프로그램 개요]** > **[!UICONTROL SSL 인증서]**(으)로 이동한 다음 SSL 인증서를 추가합니다.
   ![이미지](/help/assets/assets/ssl-certificate.png)
Adobe Cloud Manager에서 [SSL 인증서](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 추가하는 방법을 알아봅니다.

1. SSL 인증서를 추가한 후 사용자 정의 도메인을 추가합니다. **[!UICONTROL 도메인 설정]**&#x200B;을 클릭하고 **[!UICONTROL 서비스 게시]** 옵션에 대해 사용자 지정 도메인을 지정합니다.
[사용자 지정 도메인](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)에 대해 자세히 알아보세요.

1. DNS 레코드에 게시 도메인에 해당하는 두 개의 [CNAME 레코드](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)을(를) 추가합니다.
DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.

1. 지원 사례를 기록하여 사용자 정의 도메인을 쉽게 구성하여 게재 계층으로 전달합니다.

>[!NOTE]
>
사용자 지정 도메인을 허용된 리디렉션 URL 목록에 추가합니다. 목록은 자산 선택기의 IMS 클라이언트에 있습니다.<br>사용자 지정 도메인 문자열을 제공하여 각 Adobe 팀과 조정하여 이 작업을 실행합니다.
