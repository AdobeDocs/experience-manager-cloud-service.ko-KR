---
title: 미리보기 계층을 위한 OSGi 설정 구성
description: 콘텐츠를 시작하기 전에 미리보기 위해서 AEM 미리보기 서비스를 구성하는 방법에 대해서 알아봅니다.
exl-id: 1200bb17-8a3c-4e41-85f4-ed2334b61f69
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---

# 미리보기 계층을 위한 OSGi 설정 구성 {#configure-osgi-preview-tier}

AEM은 개발자 및 콘텐츠 작성자가 웹 사이트의 최종 결과물이 게시 환경에 도달하고 공개적으로 사용할 수 있게 되기 전에 이를 미리 볼 수 있도록 하는 Sites 미리보기 서비스를 제공합니다.

이를 사용하면 작성자 환경에는 표시되지 않는 다양한 경험을 미리 볼 수 있습니다. 예를 들어 페이지 전환, 경험 조각 및 기타 게시 측 전용 콘텐츠가 있습니다.

미리보기 계층의 OSGi 속성 값은 게시 계층에서 상속됩니다. 그러나 `service` 매개변수를 `preview` 값으로 설정하여 미리보기 계층 값을 게시 계층과 다르게 할 수 있습니다.

>[!NOTE]
>
>미리보기 환경에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)을 참조하십시오.

## 미리보기 계층을 위한 OSGi 설정 구성 {#configuring-osgi-settings-for-the-preview-tier}

다음 OSGi 속성의 예제는 통합 엔드포인트의 URL을 결정합니다.

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

## Developer Console을 사용하여 미리보기 디버깅 {#debugging-preview-using-the-developer-console}

다음 단계에 따라 Developer Console을 사용하여 미리보기 계층을 디버그하십시오.

* [Developer Console](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools)에서 **-- 모두 미리보기 --** 또는 이름에 **prev**&#x200B;가 포함된 프로덕션 환경을 선택합니다.
* 미리보기 인스턴스에 대한 관련 정보 생성
환경에 대한 URL을 가져오는 방법에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 문서를 참조하십시오.
