---
title: ' [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]용 자산 선택기'
description: 에셋 선택기를 다양한 Adobe, 비Adobe 및 타사 애플리케이션과 통합합니다.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: b85363b0a284929a2308ebee24888937f7c32841
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 47%

---

# Vanilla JS를 사용하여 자산 선택기 통합 {#integration-using-vanilla-js}

[!DNL Adobe] 또는 Adobe이 아닌 응용 프로그램을 [!DNL Experience Manager Assets] 리포지토리와 통합하고 응용 프로그램 내에서 에셋을 선택할 수 있습니다. [다양한 응용 프로그램과 자산 선택기 통합](#asset-selector-integration-with-apps)을 참조하십시오.

이러한 통합은 자산 선택기 패키지를 가져온 다음 Vanilla JavaScript 라이브러리를 사용하여 Assets as a Cloud Service에 연결하여 수행할 수 있습니다. `index.html` 또는 응용 프로그램 내의 적절한 파일을 편집하여 다음 작업을 수행합니다.

* 인증 세부 정보 정의
* Assets as a Cloud Service 저장소 액세스
* 자산 선택기 표시 속성 구성

다음과 같은 경우 일부 IMS 속성을 정의하지 않고 인증을 수행할 수 있습니다.

* [통합 셸](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=ko)에서 [!DNL Adobe] 애플리케이션을 통합하는 경우
* 인증용으로 생성된 IMS 토큰을 이미 보유하고 있는 경우

## 에셋 선택기를 다양한 애플리케이션과 통합 {#asset-selector-integration-with-apps}

에셋 선택기를 다음과 같은 다양한 애플리케이션과 통합할 수 있습니다.

* [자산 선택기를  [!DNL Adobe] 응용 프로그램과 통합](/help/assets/integrate-asset-selector-adobe-app.md)
* [에셋 선택기를 Adobe이 아닌 애플리케이션과 통합](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [OpenAPI 기능과 Dynamic Media 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [자산 선택기 사용자 지정](/help/assets/asset-selector-customization.md)
>* [자산 선택기 속성](/help/assets/asset-selector-properties.md)
>* [자산 선택기 Dynamic Media Open API 통합](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
