---
title: 적응형 Forms에서 SOM 표현식 사용
seo-title: Using SOM expressions in Adaptive Forms
description: 적응형 양식 패널의 SOM 표현식을 추출하는 방법을 알아봅니다.
seo-description: Learn how to extract SOM expressions of a panel of an Adaptive Form.
uuid: c5d55aff-fb69-4a1c-96ea-fb3f9322cbb0
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 13f00bb2-561f-4d64-8829-292c663abeab
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# 적응형 Forms에서 SOM 표현식 사용{#using-som-expressions-in-adaptive-forms}

응용 Forms은 AEM 리포지토리에서 JCR 컨텐츠 구조로 표시되는 AEM 페이지로 모델링됩니다. 컨텐츠 구조의 주요 요소는 guideContainer 노드입니다. guideContainer 아래에는 중첩된 패널과 필드가 포함될 수 있는 rootPanel이 있습니다.

SOM(스크립팅 개체 모델)을 사용하여 특정 DOM(문서 개체 모델) 내의 값, 속성 및 메서드를 참조할 수 있습니다. DOM은 메모리 개체와 속성을 트리 계층 구조로 구성합니다. SOM 표현식은 필드/그리기 요소 및 패널을 참조합니다.

다음 이미지는 구성 요소를 양식에 추가할 때 적응형 양식이 변환되는 노드 구조를 나타냅니다. 예를 들어, 런타임 시 DOM으로 변형되는 패널의 패널 및 라디오 단추를 루트 패널에 추가할 수 있습니다. 적응형 양식의 라디오 단추 필드에 대한 SOM 표현식은 `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![DOM 트리](assets/hierarchy.png)

DOM 트리

적응형 양식의 요소에 대한 SOM 표현식은 `guide[0].guide1[0]`. 노드 구조 계층 구조에서 구성 요소의 위치는 해당 SOM 표현식을 도출하는 데 사용됩니다.

![라디오 단추가 두 개인 DOM 트리](assets/hierarchy_radio_button.png)

라디오 단추가 두 개인 DOM 트리

적응형 양식에서 라디오 단추의 위치를 변경하면 SOM 표현식이 변경됩니다. 작성 모드에서는 내의 필드 또는 요소의 SOM 표현식을 볼 수 있습니다 [!DNL AEM Forms] SOM 표현식 보기 옵션 사용. 옵션이 패널에 표시되고 필드나 요소를 마우스 오른쪽 단추로 클릭합니다.

![적응형 양식에서 SOM 표현식 추출](assets/som-expressions.png)

적응형 양식에서 SOM 표현식 추출

패널 내에서 패널 도구 모음에서 기능에 액세스할 수 있습니다. 이 기능을 사용하면 적응형 양식 작성자가 스크립트를 쉽게 작성할 수 있습니다.

![패널 도구 모음을 사용하여 SOM 표현식 추출](assets/som-expression.png)

패널 도구 모음을 사용하여 SOM 표현식 추출

에 나열된 일부 API [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) 요소의 SOM 표현식을 사용합니다. 예를 들어 적응형 양식의 특정 필드에 포커스를 가져오려면 해당 SOM 표현식을 `getFocus`의 API `guideBridge`.
