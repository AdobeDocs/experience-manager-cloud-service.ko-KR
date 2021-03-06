---
title: 응용 Forms의 구분 기호 구성 요소
seo-title: Separator component in Adaptive Forms
description: 구분 기호 구성 요소를 사용하여 양식의 섹션을 시각적으로 분리할 수 있습니다.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: a8aa77fe-5880-4c4e-9e1b-3c5a8772c29d
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 3%

---


# 응용 Forms의 구분 기호 구성 요소{#separator-component-in-adaptive-forms}

구분 기호 구성 요소를 사용하여 양식의 패널을 시각적으로 분리할 수 있습니다. 구분 기호 구성 요소의 다음 속성을 지정하여 구분 기호 구성 요소의 전체 모양과 스타일을 정의할 수 있습니다.

* **요소 이름:** 구성 요소의 이름을 지정합니다. SOM 표현식은 요소 이름 필드에 지정된 값으로 구성 요소를 해결합니다.
* **두께:** 구분 기호 구성 요소의 두께(픽셀 단위)를 지정합니다.

* **CSS 클래스:** 구분 기호 구성 요소에 대한 사용자 지정 CSS 클래스를 지정합니다

* **인라인 스타일:** 사용 [!DNL AEM Forms]이제 개별 적응형 양식 구성 요소에 인라인 CSS 스타일을 적용하고 실시간으로 변경 사항을 미리 볼 수 있습니다.

레이아웃 모드를 사용하여 구분 기호 구성 요소가 속하는 열 수를 정의할 수 있습니다. 자세한 내용은 [레이아웃 모드를 사용하여 구성 요소의크기 조정](resize-using-layout-mode.md)을 참조하십시오.

구분 기호 구성 요소의 속성을 지정하려면

1. 구분 기호 구성 요소를 선택하고 탭합니다 ![cmppr](assets/cmppr.png). 속성은 사이드바에서 열립니다.
1. 인라인 CSS 속성 섹션에서 탭을 클릭하여 CSS 속성을 지정합니다. 예: a. 필드 탭에서 **항목 추가**. 필드가 두 개인 행이 추가됩니다.
1. 왼쪽의 첫 번째 필드에서 적용할 CSS3 속성을 지정합니다. 예, **테두리**. 아래쪽 화살표 단추를 클릭하여 속성을 선택할 수도 있습니다. 드롭다운 목록은 완전하지 않으며 이 필드에 지원되는 CSS3 속성 이름을 지정할 수 있습니다.
1. 인접 필드에서 지정된 CSS3 속성에 유효한 값을 지정합니다. 예, **3px 솔리드 블랙**.
1. 클릭 **항목 추가** 다른 속성과 해당 값을 지정합니다.
1. 클릭 **미리 보기** 양식에서 변경 사항을 미리 보려면
1. 클릭 **확인** 변경 사항을 확인하려면 **취소** 변경하지 않고 대화 상자를 종료합니다.

