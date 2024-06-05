---
title: ContextHub 진단
description: ContextHub는 ContextHub 프레임워크의 개요를 볼 수 있는 진단 페이지를 제공합니다
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---

# ContextHub 진단 {#contexthub-diagnostics}

ContextHub는 ContextHub 프레임워크의 개요를 볼 수 있는 진단 페이지를 제공합니다. 페이지를 열려면 `contexthub.diagnostics.html` AEM 작성자 인스턴스의 페이지입니다. 예:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

ContextHub 진단 페이지는 작성된 저장소 및 UI 모듈, 로드된 클라이언트 라이브러리 폴더 및 유용한 페이지에 대한 링크를 제공합니다.

>[!NOTE]
>
>진단 정보를 반환하려면 디버그 모드를 활성화해야 합니다. 그렇지 않으면 진단 페이지가 비어 있습니다. 다음을 참조하십시오 [이 문서](configuring-contexthub.md#debugging-contexthub) 디버그 모드를 활성화하는 방법에 대한 자세한 내용을 참조하십시오.

## 스토어 {#stores}

저장소 섹션에는 구성된 모든 ContextHub 저장소가 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목:** 다음 [저장소 유형](sample-stores.md) 상점이 기반으로 하는 것입니다.
* **경로:** 구성을 포함하는 저장소 노드의 경로입니다.
* **리소스 유형:** 저장소 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** 저장소 유형을 구현하는 로드된 클라이언트 라이브러리의 카테고리입니다.

## 모듈 {#modules}

모듈 섹션에는 구성된 모든 ContextHub UI 모듈이 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목:** 다음 [UI 모듈 유형](sample-modules.md) UI 모듈의 기반이 됩니다.
* **경로:** 구성을 포함하는 저장소 노드의 경로입니다.
* **리소스 유형:** UI 모듈 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** UI 모듈 유형을 구현하는 로드된 클라이언트 라이브러리의 카테고리입니다.

## Clientlibs {#clientlibs}

Clientlibs 섹션에는 모든 항목이 나열됩니다[클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md) 이 ContextHub는 로드되었습니다. 클라이언트 라이브러리는 다음과 같이 분류됩니다.

* **kernel.js:** ContextHub 프레임워크, 세그먼트 엔진 및 저장소 유형을 구현하는 클라이언트 라이브러리입니다.
* **ui.js:** ContextHub UI 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리.
* **style.css:** 클라이언트 라이브러리에서 로드되는 CSS 파일입니다.

## URL {#urls}

URL 섹션에는 ContextHub 기능에 대한 링크가 포함되어 있습니다.

* **구성 편집기:** 다음을 엽니다. [ContextHub 구성 페이지](configuring-contexthub.md) 저장소, UI 모드 및 UI 모듈을 구성할 수 있습니다.
* **ContextHub 모듈 구성:** 다음을 엽니다. `/etc/cloudsettings/default/contexthub.config.kernel.js` ContextHub 저장소 구성의 JavaScript 개체 표현을 포함하는 파일입니다.
* **ContextHub UI 구성:** 다음을 엽니다. `/etc/cloudsettings/default/contexthub.config.ui.js` ContextHub UI 모드 구성의 JavaScript 개체 표현을 포함하는 파일입니다.
* **kernel.js:** 다음을 엽니다. `/etc/cloudsettings/default/contexthub.kernel.js` ContextHub 프레임워크, 세그먼트 엔진 및 저장소 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 들어 있는 파일입니다.
* **ui.js:** 다음을 엽니다. `/etc/cloudsettings/default/contexthub.ui.js` ContextHub UI 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 포함된 파일입니다.
* **style.css:** 다음을 엽니다. `/etc/cloudsettings/default/contexthub.styles.css` ContextHub UI 및 UI 모듈의 CSS 스타일이 포함된 파일입니다.
