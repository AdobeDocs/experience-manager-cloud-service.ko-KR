---
title: 콘텐츠 미리보기
description: 라이브로 전환하기 전에 AEM 미리 보기 서비스를 사용하여 컨텐츠를 미리 보는 방법을 알아봅니다.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 66bc262b35f69b7877e4a01df9ab26395afd604d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---


# 콘텐츠 미리보기 {#previewing-content}

AEM에서는 사이트 미리 보기 서비스를 제공하여 개발자와 컨텐츠 작성자가 웹 사이트가 게시 환경에 도달하기 전에 웹 사이트의 최종 경험을 미리 볼 수 있도록 하며 공개적으로 사용할 수 있습니다.

페이지 전환 및 기타 게시 측 전용 콘텐츠와 같이 작성 환경에서 볼 수 없는 페이지 경험을 쉽게 미리 볼 수 있습니다.

미리 보기 환경에 대한 자세한 내용은 문서를 참조하십시오 [환경 관리.](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>경험 조각 을 미리 보기에 게시하면 기본적으로 경험 조각 콘솔 또는 편집기에서 페이지에 대해 와 동일한 절차를 따릅니다.

## 미리 보기에 컨텐츠 게시 {#publishing-content-to-preview}

를 사용하여 컨텐츠를 미리 보기 서비스에 게시할 수 있습니다 **게시 관리** UI.

1. Sites 콘솔에서 미리 보기 위해 보낼 페이지를 선택하고 을(를) 클릭합니다. **게시 관리** 버튼
1. 다음 마법사에서 **미리 보기** 를 대상으로 사용

   ![게시 관리](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. 클릭 **다음**, 그런 다음 **게시** 확인합니다.

1. 미리 보기 환경에서 컨텐츠에 액세스하기 위한 URL이 대화 상자에 표시됩니다.


또는 마법사에 표시된 URL을 사용하여 미리 보기 컨텐츠를 보는 대신 다음을 수행할 수도 있습니다 `preview-` 프로덕션 인스턴스의 게시 URL에 매핑하는 플레이어 전용 확장 포함 또는 구축

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

문서를 참조하십시오 [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 를 참조하십시오.

컨텐츠를 다음 아이콘을 사용하여 미리 볼 수도 있습니다 [컨텐츠 트리 워크플로우 게시](/help/operations/replication.md#publish-content-tree-workflow) 사용 `agentId` 매개 변수가 `preview` 또는 [복제 API](/help/operations/replication.md#replication-api) 사용 `AgentFilter` 미리 보기용으로 구성되었습니다.

## 미리 보기 계층에 대한 OSGi 설정 구성 {#configuring-osgi-settings-for-the-preview-tier}

미리 보기 계층의 OSGi 속성 값은 게시 계층에서 상속됩니다. 그러나 미리 보기 계층의 값은 `service` 값에 대한 매개 변수 `preview`. 다음 OSGi 속성 예제는 통합 끝점의 URL을 결정합니다.

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

자세한 내용은 [이 섹션](/help/implementing/deploying/configuring-osgi.md#author-vs-publish-configuration) at.js 2.

## 개발자 콘솔을 사용하여 디버깅 미리 보기 {#debugging-preview-using-the-developer-console}

개발자 콘솔을 사용하여 미리 보기 계층을 디버깅하려면 다음 단계를 따르십시오.

* 에서 [개발자 콘솔](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools)다음 중 하나를 선택합니다. **— 모든 미리 보기 —** 또는 다음을 포함하는 프로덕션 환경 **prev** 이름
* 미리 보기 인스턴스에 대한 관련 정보를 생성합니다. [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 를 참조하십시오.
