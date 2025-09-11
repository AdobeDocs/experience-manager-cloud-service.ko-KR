---
title: 범용 편집기에서의 콘텐츠 상속
description: 범용 편집기가 콘텐츠 재사용 및 현지화를 지원하기 위해 다중 사이트 관리 및 론치를 위한 콘텐츠 상속을 지원하는 방법에 대해 알아봅니다.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 2a1b87c2-29b9-4689-9a15-e17942439160
source-git-commit: 2099a1aecd30eaa2ca3ca33a13729817a30b6c3f
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 3%

---

# 범용 편집기에서의 콘텐츠 상속 {#inheritance}

범용 편집기가 콘텐츠 재사용 및 현지화를 지원하기 위해 다중 사이트 관리 및 론치를 위한 콘텐츠 상속을 지원하는 방법에 대해 알아봅니다.

>[!NOTE]
>
>이 기능은 AEM 저장소에 저장된 콘텐츠에만 사용할 수 있습니다.

## 사용 사례 {#use-case}

AEM의 많은 사용자에게 페이지 생성은 시작에 불과합니다. 콘텐츠를 효율적으로 확장하려면 일반적으로 페이지를 만든 후 다음 단계를 수행해야 합니다.

1. 언어 사본과 번역 워크플로를 사용하여 **페이지를 번역**&#x200B;합니다.
1. 다중 사이트 관리를 사용하여 번역된 페이지를 다른 시장에 배포하여 **페이지를 지역화**&#x200B;합니다.
1. 론치를 사용하여 페이지의 향후 반복을 준비하고 변경 내용을 실시간으로 선택하여 **새 버전을 만듭니다**.

이러한 단계를 통해 컨텐츠 속도를 가속화하고 컨텐츠 일관성을 보장할 수 있습니다. 범용 편집기는 언어 사본, 다중 사이트 관리 및 론치가 사용하는 메커니즘 콘텐츠 상속을 지원합니다.

## 상속 {#what-is-inheritance}

상속은 콘텐츠를 연결할 수 있는 메커니즘으로, 콘텐츠를 변경하면 자동으로 다른 콘텐츠가 변경됩니다.

MSM 및 론치는 상속을 사용하여 콘텐츠를 재사용하는 데 도움이 되는 강력한 도구입니다. 중앙 소스(블루프린트)에서 페이지를 복사하면 작성자가 해당 사본의 컨텍스트에 맞게 변경할 수 있지만 나머지 콘텐츠는 블루프린트에서 상속된 상태로 유지됩니다. 이 기능은 사이트를 현지화할 때 매우 유용합니다.

사본 콘텐츠를 수정하기 위해 작성자가 영향을 받는 구성 요소에 대한 상속을 중단하여 블루프린트에서 사본이 동기화될 때 로컬 변경 사항을 덮어쓰지 않도록 합니다.

## 컨텐츠 상속 및 유니버설 편집기 {#universal-editor}

페이지가 MSM의 일부이거나 론치 이고 유니버설 편집기를 사용하여 콘텐츠를 편집하는 경우 편집기는 해당 페이지에서 작성자가 변경한 모든 사항에 대한 상속을 자동으로 비활성화하여 블루프린트에서 업데이트가 동기화될 때 수정된 콘텐츠가 유지되도록 합니다.

작성자는 로컬 편집을 수행하기 전에 버튼을 클릭하거나 다른 단계를 수행하여 상속을 비활성화할 필요가 없습니다. 변경이 이루어지면 즉시 상속이 묵시적으로 취소됩니다. 이 워크플로는 [페이지 편집기](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components)와 대조적입니다.

상속은 다음을 통해 전체 페이지에 대해 되돌릴 수 있습니다.

* [Live Copy 개요 콘솔](/help/sites-cloud/administering/msm/live-copy-overview.md)
* [시작 콘솔](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
* **페이지 속성 창**&#x200B;의 **라이브 카피** 탭에서 [재설정](/help/sites-cloud/authoring/sites-console/page-properties.md) 단추를 사용합니다.

범용 편집기는 상속의 기본 메커니즘에 영향을 주지 않습니다. 상속이 작동하는 방식에 대한 자세한 내용은 다음 설명서를 참조하십시오.

* [다중 사이트 관리(MSM)](/help/sites-cloud/administering/msm/overview.md)
* [론치](/help/sites-cloud/authoring/launches/overview.md)

### AEM MSM(다중 사이트 관리) 확장 {#msm-extension}

설치된 경우 **AEM MSM(다중 사이트 관리) 확장**&#x200B;에 선택한 구성 요소의 현재 상속 상태가 표시되고 구성 요소 수준에서 상속을 중단하거나 복원할 수 있습니다.

이 확장을 사용하는 방법에 대한 자세한 내용은 [작성 설명서를 참조하십시오.](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)

이 확장을 사용하는 방법에 대한 자세한 내용은 [Extension Manager 설명서를 참조하십시오.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## 제한 사항 {#limitations}

* 단일 구성 요소의 상속을 되돌리려면 **AEM MSM(다중 사이트 관리) 확장**&#x200B;을 사용하도록 설정해야 합니다.
* 상속이 비활성화된 구성 요소와 유지된 구성 요소를 확인하기 위한 시각적 피드백을 보려면 **AEM MSM(다중 사이트 관리) 확장**&#x200B;을(를) 활성화해야 합니다.
