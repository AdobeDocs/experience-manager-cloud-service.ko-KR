---
title: 컨텐츠 조각 AJO 외부 참조 확장 사용
description: 콘텐츠 조각 AJO 외부 참조 확장에 대해 알아보기
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
source-git-commit: f755a5c621b68b3110642e6cfe150798555b6707
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---


# 컨텐츠 조각 AJO 외부 참조 확장 {#content-fragment-external-references-extension}

다른 Adobe 제품에서 AEM의 경험을 미리 보려면 UI 확장을 활성화할 수 있습니다.

* **AJO 외부 참조**

AJO 외부 참조 확장은 사전 정의된 태그와 연결된 모든 조직 및 샌드박스에서 콘텐츠 조각에 대한 참조를 가져와 작동합니다. 그러면 확장에 세부 정보가 표시됩니다.

예를 들어 Adobe Journey Optimizer(AJO 여정)과 통합하기 위해 세부 사항은 참조가 캠페인인지, 템플릿인지 여부에 따라 달라집니다.

>[!NOTE]
>
>확장 기능을 사용하는 방법에 대한 자세한 내용은 AEM Experience Manager의 [Extension Manager을 참조하십시오.](https://developer.adobe.com/uix/docs/extension-manager/)

예를 들어 AJO에서 확장을 사용하려면 다음을 수행하십시오.

>[!NOTE]
>
>[AJO 통합](https://experienceleague.adobe.com/ko/docs/journey-optimizer/using/integrations/aem-fragments)도 참조하세요.

1. [콘텐츠 조각 콘솔](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)을 엽니다.

1. 콘텐츠 조각 - 다양한 AJO 채널에서 만들고 사용한 조각으로 이동합니다.

1. [편집기](/help/sites-cloud/administering/content-fragments/managing.md#editing-the-content-of-your-fragment)에서 콘텐츠 조각을 엽니다.

1. AJO 외부 참조 확장은 오른쪽 패널에서 탭으로 사용할 수 있습니다. 탭을 선택하여 확장을 엽니다.

   ![AJO 외부 참조 확장](/help/sites-cloud/administering/content-fragments/assets/cf-ajo-fragment-external-references-extension.png)

   참조 유형을 선택하면 확장에 해당 외부 참조가 열이 있는 테이블로 표시됩니다.

   * **이름**: 콘텐츠 조각이 사용되는 참조의 이름
   * **미리 보기** 미리 보기를 시작하려면 이 링크를 선택하십시오.
   * **상태**: 참조의 상태

1. 드롭다운에서 **참조 형식**&#x200B;을(를) 선택하여 다음 세 가지 참조 형식 간에 전환할 수 있습니다.

   * **캠페인**
      * 현재 콘텐츠 조각에 대한 링크가 있는 모든 캠페인 목록을 표시합니다.
      * 그런 다음 선택한 캠페인을 미리 볼 수 있습니다.
      * 기본값
   * **여정**
      * 최신 여정을 표시합니다.
      * 그런 다음 선택한 여정을 선택하고 미리 볼 수 있습니다.
   * **템플릿**
      * 콘텐츠 조각과 관련된 템플릿을 표시합니다.
      * 그런 다음 선택한 템플릿을 선택하고 미리 볼 수 있습니다.