---
title: 컨텐츠 미리 보기
description: 라이브로 전환하기 전에 AEM 미리 보기 서비스를 사용하여 컨텐츠를 미리 보는 방법을 알아봅니다.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 53a3fb91dcf093d55e80c7dfcdef3a7855731841
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 컨텐츠 미리 보기 {#previewing-content}

>[!NOTE]
>
>미리 보기 기능은 2021.5.0 릴리스의 일부이며 다음 몇 주에 걸쳐 점진적으로 롤아웃됩니다.

AEM은 웹 사이트가 게시 환경에 도달하기 전에 개발자와 컨텐츠 작성자가 웹 사이트의 최종 경험을 미리 볼 수 있도록 설계된 사이트 미리 보기 서비스를 제공하며 공개적으로 사용할 수 있습니다.

페이지 전환 및 기타 게시 측 전용 컨텐츠와 같이 작성 환경에서 볼 수 없는 페이지 경험 미리 보기를 용이하게 합니다.

## 미리 보기에 컨텐츠 게시 {#publishing-content-to-preview}

다음과 같이 관리 게시 UI를 사용하여 미리 보기 서비스에 컨텐츠를 게시할 수 있습니다.

1. Sites 콘솔에서 미리 보기 위해 보낼 페이지를 선택하고 **게시 관리** 단추를 클릭합니다.
1. 다음 마법사에서 **미리 보기**&#x200B;를 대상으로 선택합니다

   ![게시 관리](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. **다음**&#x200B;을 클릭한 다음 **게시**&#x200B;를 클릭하여 확인합니다.

미리 보기 컨텐츠, 미리 보기 **미리 보기**&#x200B;를 프로덕션 인스턴스의 게시 URL에 추가합니다. URL은 다음과 같이 구성해야 합니다.

```
https://preview-p[programID]-e[environmentID].adobeaemcloud.com/pathtopage.html
```

환경을 위한 URL을 가져오는 방법에 대한 자세한 내용은 [환경 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en)를 참조하십시오.

## 미리 보기 계층에 대한 OSGi 설정 구성 {#configuring-osgi-settings-for-the-preview-tier}

미리 보기 계층의 OSGI 속성 값은 게시 계층에서 상속되지만 미리 보기 계층 값은 &quot;preview&quot; 값으로 서비스 매개 변수를 설정하는 환경별 값을 사용하여 게시 계층과 구별할 수 있습니다. 통합 끝점의 URL을 결정하는 OSGI 속성의 아래 예를 살펴보십시오.

```
[
{
"name":"INTEGRATION_URL",
"type":"string",
"value":"http://s2.integrationvendor.com",
"service": "preview"
}
]
```

자세한 내용은 OSGi 구성 설명서의 [이 섹션](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration)을 참조하십시오.

## 개발자 콘솔을 사용하여 디버깅 미리 보기 {#debugging-preview-using-the-developer-console}

개발자 콘솔을 사용하여 미리 보기 계층을 디버깅하려면 다음 단계를 따르십시오.

* [개발자 콘솔](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools)에서 **— 모두 미리 보기 —** 또는 이름에 **prev**&#x200B;를 포함하는 프로덕션 환경을 선택합니다
* 미리 보기 인스턴스에 대한 관련 정보 생성
환경을 위한 URL을 가져오는 방법에 대한 자세한 내용은 [환경 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/manage-your-environment.html?lang=en)를 참조하십시오.
