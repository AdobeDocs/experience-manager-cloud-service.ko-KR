---
title: 알려진 문제
description: Adobe Experience Manager as a Cloud Service 관련 알려진 문제
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 755c0072148ad73486df2ccfed69248b9d73ec2a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 100%

---

# 알려진 문제 {#known-issues}

이 문서에는 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 제품의 알려진 문제가 나열되어 있습니다. 해당 목록은 [!DNL Experience Manager]의 지속적인 릴리스와 함께 수정되고 업데이트됩니다.

알려진 문제에 대한 자세한 내용은 [지원 센터에 문의](https://experienceleague.adobe.com/?lang=ko-kr&amp;support-solution=Experience+Manager#support)하십시오.

<!-- 
## Platform {#platform}
-->

## Sites {#sites}

일부 [!DNL Sites]의 알려진 문제는 다음과 같습니다.

* GraphQL IDE에서 [지속 쿼리의 캐시를 관리](/help/headless/graphql-api/graphiql-ide.md##managing-cache)할 수 있습니다.
   * 첫 번째 저장 시 헤더에 대해 저장된 값은 사용자가 대화 상자에서 해당 값을 변경하지 않은 경우 기본값이 아닌 `0`으로 설정됩니다.
   * 이후에 저장하면 값이 올바르게 저장됩니다.
   * 따라서 사용자는 헤더를 두 번 저장해야 합니다.

## [!DNL Assets] {#assets}

<!-- Jira label: assets-cloud-known-issues -->

일부 [!DNL Assets]의 알려진 문제는 다음과 같습니다.

* **다운로드**: 빈 폴더를 다운로드하는 경우 [!DNL Experience Manager]에 ZIP 아카이브 생성에 대한 성공 메시지가 표시되지만, 아카이브는 생성되지 않습니다.

* **메타데이터 스키마**: 사용된 에셋 등급 위젯으로 인해 JSP 컴파일 오류가 발생했습니다. 메타데이터 스키마에서 제거되었습니다. <!-- CQ-4282865, CQ-4284633 -->

또한 [ [!DNL Experience Manager Assets]](/help/assets/assets-cloud-changes.md)의 주목할 만한 변경 내용을 참조하십시오.

<!-- This content was added at GA. Not sure if we should continue to have this commitment about upcoming features/enh. in the docs. Commenting it for now.

### Upcoming Assets capabilities {#upcoming-assets-capabilities}

A few capabilities of Adobe Experience Manager Assets that depend on foundation capabilities, which are not yet available in the Experience Manager as a Cloud Service deployment architecture, are expected to be enabled at a later stage:

* Capabilities not enabled at this stage due to dependency on Commerce Integration Framework APIs:
  * Photoshoot workflow models.
  * Product information tab in the asset properties user interface is not populated.

* Capabilities not enabled at this stage due to dependency on InDesign Server integration:
  * Asset Templates and Asset Catalogs.
  * Multi-page preview of Adobe InDesign files.
-->

>[!MORELIKETHIS]
>
>* [ [!DNL Experience Manager]](aem-cloud-changes.md)의 주요 변경 내용
>* [이제 사용되지 않는 기능과 제거된 기능](deprecated-removed-features.md)
>* [릴리스 정보](home.md)

