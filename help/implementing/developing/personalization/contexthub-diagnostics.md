---
title: ContextHub 진단
description: ContextHub은 ContextHub 프레임워크의 개요를 볼 수 있는 진단 페이지를 제공합니다
translation-type: tm+mt
source-git-commit: 1c518830f0bc9d9c7e6b11bebd6c0abd668ce040
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---


# ContextHub 진단 {#contexthub-diagnostics}

ContextHub은 ContextHub 프레임워크의 개요를 볼 수 있는 진단 페이지를 제공합니다. 페이지를 열려면 AEM 작성자 인스턴스의 `contexthub.diagnostics.html` 페이지로 이동하십시오. 예를 들면 다음과 같습니다.

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

ContextHub 진단 페이지에서는 생성된 스토어 및 UI 모듈, 로드된 클라이언트 라이브러리 폴더 및 유용한 페이지에 대한 링크를 제공합니다.

>[!NOTE]
>
>진단 정보를 반환하려면 디버그 모드를 활성화해야 하며, 그렇지 않으면 진단 페이지가 비어 있게 됩니다. 디버그 모드를 활성화하는 방법에 대한 자세한 내용은 [이 문서](configuring-contexthub.md#debugging-contexthub)을 참조하십시오.

## {#stores} 저장

스토어 섹션에는 구성된 모든 ContextHub 스토어가 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목: 스토어** 가  [기반으로 ](sample-stores.md) 하는 스토어 유형입니다.
* **경로:** 구성을 보유하는 저장소 노드의 경로입니다.
* **resourceType:** 저장소 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** 저장소 유형을 구현하는 클라이언트 라이브러리의 범주입니다.

## 모듈 {#modules}

모듈 섹션에는 구성된 모든 ContextHub UI 모듈이 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목:** UI  [모듈](sample-modules.md) 이 기반으로 하는 UI 모듈 유형입니다.
* **경로:** 구성을 보유하는 저장소 노드의 경로입니다.
* **resourceType:** UI 모듈 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** UI 모듈 유형을 구현하는 클라이언트 라이브러리의 범주입니다.

## Clientlibs {#clientlibs}

Clientlibs 섹션에는 ContextHub가 로드한 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md)의 모든 항목이 나열됩니다. 클라이언트 라이브러리는 다음과 같이 분류됩니다.

* **kernel.js:** ContextHub 프레임워크, 세그먼트 엔진 및 스토어 유형을 구현하는 클라이언트 라이브러리.
* **ui.js:** ContextHub UI 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리.
* **style.css:** 클라이언트 라이브러리에서 로드되는 CSS 파일

## URL {#urls}

URL 섹션에는 ContextHub 기능에 대한 링크가 포함되어 있습니다.

* **구성 편집기:** 스토어,  [UI 모드 및 UI 모듈을 ](configuring-contexthub.md) 구성할 수 있는 ContextHub 구성 페이지를 엽니다.
* **ContextHub 모듈 구성:** ContextHub  `/etc/cloudsettings/default/contexthub.config.kernel.js` 저장소 구성의 Javascript 개체 표현을 포함하는 파일을 엽니다.
* **ContextHub UI 구성:** ContextHub UI  `/etc/cloudsettings/default/contexthub.config.ui.js` 모드 구성의 Javascript 개체 표현을 포함하는 파일을 엽니다.
* **kernel.js:** ContextHub 프레임워크, 세그먼트 엔진 및 저장소 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 들어 있는  `/etc/cloudsettings/default/contexthub.kernel.js` 파일을 엽니다.
* **ui.js:** ContextHub UI  `/etc/cloudsettings/default/contexthub.ui.js` 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 포함된 파일을 엽니다.
* **style.css:** ContextHub UI  `/etc/cloudsettings/default/contexthub.styles.css` 및 UI 모듈에 대한 CSS 스타일이 포함된 파일을 엽니다.
