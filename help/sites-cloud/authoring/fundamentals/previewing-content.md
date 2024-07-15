---
title: 콘텐츠 미리보기
description: AEM 미리보기 서비스를 사용하여 콘텐츠를 시작하기 전에 미리 보는 방법에 대해 알아봅니다.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: a9a2362903e8eec25393e2ceb307814e1a21f142
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 89%

---


# 콘텐츠 미리보기 {#previewing-content}

AEM은 개발자 및 콘텐츠 작성자가 웹 사이트의 최종 경험이 게시 환경에 도달하고 공개적으로 사용할 수 있게 되기 전에 이를 미리 볼 수 있도록 하는 Sites 미리보기 서비스를 제공합니다.

이를 사용하면 페이지 전환 및 게시측 전용 콘텐츠와 같은 작성자 환경에는 표시되지 않는 페이지 경험을 미리 볼 수 있습니다.

>[!NOTE]
>
>콘텐츠가 미리보기 환경에 *게시*&#x200B;되므로 URL을 통해 액세스할 수 있습니다(따라서 AEM에 액세스할 필요가 없음).

미리보기 환경에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md#access-preview-service)을 참조하십시오.

## 미리보기에 콘텐츠 게시 {#publishing-content-to-preview}

**게시 관리** UI를 사용하여 콘텐츠를 미리보기 서비스에 게시할 수 있습니다.

1. 사이트 콘솔에서 미리보기에 전송할 페이지를 선택한 다음 **게시 관리** 단추를 클릭합니다.
1. 다음 마법사에서 대상으로 **미리 보기**&#x200B;를 선택합니다.

   ![게시 관리](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. **다음**&#x200B;을 선택하고 **게시**&#x200B;를 클릭하여 확인합니다.

1. 대화 상자에 미리보기 환경의 콘텐츠에 액세스하기 위한 URL이 표시됩니다.

   >[!NOTE]
   >
   >콘텐츠가 미리보기 환경에 *게시*&#x200B;되므로 URL을 통해 액세스할 수 있습니다(따라서 AEM에 액세스할 필요가 없음).

마법사에 표시되는 URL을 사용하여 미리보기 콘텐츠를 보는 것 이외에도 프로덕션 인스턴스의 게시 URL 앞에 `preview-`를 추가할 수도 있습니다.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

환경에 대한 URL을 가져오는 방법에 대한 자세한 내용은 [환경 관리](/help/implementing/cloud-manager/manage-environments.md) 문서를 참조하십시오.

`agentId` 매개변수가 `preview`로 설정된 [콘텐츠 트리 워크플로](/help/operations/replication.md#publish-content-tree-workflow)를 사용하거나 미리보기에 대해 `AgentFilter`가 구성된 [복제 API](/help/operations/replication.md#replication-api)를 사용하여 콘텐츠를 미리보기에 게시할 수도 있습니다.

## 미리보기에서 콘텐츠 게시 취소 {#unpublishing-content-from-preview}

**미리보기** 환경에서 콘텐츠를 게시 취소하는 작업은 **게시** 환경의 [페이지 게시 취소](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages) 프로세스와 기본적으로 동일합니다.

유일한 차이점은 **대상**&#x200B;이 **미리보기**&#x200B;가 되도록 선택할 수 있다는 것입니다.
