---
title: Cloud Service과 동일한 Adobe Experience Manager 사이트 쿠키 지원
description: Cloud Service과 동일한 Adobe Experience Manager 사이트 쿠키 지원
translation-type: tm+mt
source-git-commit: e51d9c3e4691fb58f3c4b6a2565cc8cad2a1acb0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}과(와) 동일한 Adobe Experience Manager 사이트 쿠키 지원

버전 80, Chrome 이상 버전의 Safari에서는 쿠키 보안을 위한 새로운 모델을 도입했습니다. 이 모드는 `SameSite`이라는 설정을 통해 제3자 사이트에 쿠키의 가용성에 대한 보안 제어를 도입하도록 설계되었습니다. 자세한 내용은 이 [article](https://web.dev/samesite-cookies-explained/)을 참조하십시오.

이 설정의 기본값(`SameSite=Lax`)으로 인해 AEM 인스턴스 또는 서비스 간 인증이 작동하지 않을 수 있습니다. 이러한 서비스의 도메인 또는 URL 구조가 이 쿠키 정책의 제한 사항에 해당되지 않을 수 있기 때문입니다.

이 문제를 해결하려면 로그인 토큰에 대해 SameSite 쿠키 속성을 `None`으로 설정해야 합니다.

다음 단계에 따라 이 작업을 수행할 수 있습니다.

1. 로컬로 AEM SDK Quickstart 버전 설치
1. `http://serveraddress:serverport/system/console/configMgr`의 웹 콘솔로 이동
1. **Adobe Granite Token 인증 처리기**&#x200B;를 검색하고 클릭합니다.
1. 아래 이미지에 표시된 것처럼 로그인 토큰 쿠키&#x200B;**에 대한** SameSite 특성을 `None`로 설정합니다.
   ![사마새](/help/security/assets/samesite1.png)
1. 저장을 클릭합니다
1. AEM SDK Quickstart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)를 사용하여 OSGi 구성 생성에서 설명한 단계를 따라 이 특정 설정에 대한 JSON 형식 구성을 생성합니다.[
1. 속성 설정](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi 설명서의 [클라우드 관리자 API 형식 단계에 따라 설정을 적용합니다.
