---
title: Dynamic Media 설정
description: Dynamic Media를 설정하려면 Dynamic Media를 구성하고 이미지 및 뷰어 사전 설정을 관리해야 합니다.
contentOwner: Rick Brough
feature: Configuration,Viewer Presets,Image Presets,Dynamic Media
role: Admin,User
exl-id: 83b70b17-7ee3-41cb-be90-c92ca161660e
source-git-commit: 8a8f3d7b17d79791a3ebf6b583ffcccfcf214470
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 14%

---

# Dynamic Media 설정 {#setting-up-dynamic-media}

{{work-with-dynamic-media}}

[Dynamic Media](https://business.adobe.com/kr/products/experience-manager/assets/dynamic-media.html)는 다양한 시각적 머천다이징 및 마케팅 자산을 웹, 모바일 및 소셜 사이트에 맞게 자동으로 크기를 조정하여 주문형으로 제공함으로써 자산을 관리하는 데 도움이 됩니다. 기본 소스 자산 세트를 사용하면 Dynamic Media는 글로벌, 확장 가능 및 성능 최적화 네트워크를 통해 실시간으로 다양한 유형의 풍부한 컨텐츠를 생성하고 전달합니다.

<!-- OBSOLETE UNTIL THE INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE

>[!NOTE]
>
>This documentation describes Dynamic Media capabilites, which are integrated directly into [!DNL Experience Manager]. If you are using Dynamic Media Classic (previously called Scene7) integrated into [!DNL Experience Manager], see [Dynamic Media Classic integration documentation](/help/sites-cloud/administering/integrating-scene7.md).
>
>See [Dual Use Scenario](/help/sites-cloud/administering/integrating-scene7.md#dual-use-scenario) for times when you may want to use [!DNL Experience Manager] integrated with Dynamic Media Classic along with Dynamic Media.

-->

Dynamic Media를 관리하는 경우 다음 항목이 중요합니다.

* [Dynamic Media 구성](config-dm.md)
* [이미지 사전 설정 관리](managing-image-presets.md)
* [뷰어 사전 설정 관리](managing-viewer-presets.md)
* [Dynamic Media 문제 해결](troubleshoot-dm.md)

다음 항목도 참조하십시오.

* [비디오 인코딩 및 비디오 프로필](video-profiles.md)
* [이미지 프로필](image-profiles.md)

>[!NOTE]
>
>**업그레이드하는 경우:**
>
>* Adobe [!DNL Experience Manager]을(를) 설치 및 실행한 후에는 업로드하는 모든 자산에 Dynamic Media가 자동으로 활성화됩니다(시스템 관리자가 명시적으로 비활성화하지 않은 경우). 업그레이드된 [!DNL Experience Manager] 인스턴스에 있고 Dynamic Media를 처음 사용하는 경우 Dynamic Media를 활성화하도록 자산을 재처리해야 할 수 있습니다. [폴더에서 에셋 재처리](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets)를 참조하십시오.


## Dynamic Media 인증서 갱신에 1회 DNS 업데이트 필요 {#dns-update-dynamic-media-certificate-renewals}

도메인에서 CAA(인증 기관 인증) DNS 레코드를 사용하는 경우, Dynamic Media 호스트 이름에 사용되는 TLS/SSL 인증서의 지속적인 갱신을 허용하도록 DigiCert를 인증해야 합니다.

도메인의 루트(apex)에 다음 CAA 레코드를 추가합니다.

```
<yourdomain> CAA 0 issue "digicert.com"
```

이는 일회성 변경입니다.

DNS 공급자 도구를 사용하여 CAA 레코드가 있는지 [CAA 조회 유틸리티](https://caatest.co.uk/)를 사용하여 CAA 레코드가 있는지 확인할 수 있습니다.

CAA 레코드가 있고 DigiCert가 승인되지 않은 경우 현재 인증서가 만료되면 인증서 갱신에 실패하여 이미지 및 비디오 제공에 중단 시간이 발생할 수 있습니다. 도메인에 대한 CAA 레코드가 없으면 작업이 필요하지 않습니다.
