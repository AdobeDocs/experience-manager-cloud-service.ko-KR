---
title: ContextHub 진단
description: ContextHub에서는 ContextHub 프레임워크의 개요를 볼 수 있는 진단 페이지를 제공합니다
exl-id: c8d4e160-ea02-49f3-9e31-119445ef5a68
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---

# ContextHub 진단 {#contexthub-diagnostics}

ContextHub에서는 ContextHub 프레임워크에 대한 개요를 볼 수 있는 진단 페이지를 제공합니다. 페이지를 열려면 `contexthub.diagnostics.html` AEM 작성자 인스턴스의 페이지(예:

`http://<host>:<port>/conf/<site>/settings/cloudsettings/default/contexthub.diagnostics.html`

ContextHub 진단 페이지에서는 생성된 저장소 및 UI 모듈, 로드되는 클라이언트 라이브러리 폴더 및 유용한 페이지에 대한 정보를 제공합니다.

>[!NOTE]
>
>진단 정보를 반환하려면 디버그 모드를 사용해야 하며, 그렇지 않으면 진단 페이지가 비어 있습니다. 자세한 내용은 [이 문서](configuring-contexthub.md#debugging-contexthub) 디버그 모드를 활성화하는 방법에 대한 자세한 내용.

## 스토어 {#stores}

저장소 섹션에는 구성된 모든 ContextHub 저장소가 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목:** 다음 [저장소 유형](sample-stores.md) 그 가게는 그 가게를 기반으로 합니다.
* **경로:** 구성을 보유하는 저장소 노드의 경로입니다.
* **resourceType:** 저장소 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** 저장소 유형을 구현하는 로드된 클라이언트 라이브러리의 카테고리입니다.

## 모듈 {#modules}

모듈 섹션에는 구성된 모든 ContextHub UI 모듈이 나열됩니다. 목록의 각 항목은 다음 정보로 구성됩니다.

* **제목:** 다음 [UI 모듈 유형](sample-modules.md) UI 모듈이 기반으로 합니다.
* **경로:** 구성을 보유하는 저장소 노드의 경로입니다.
* **resourceType:** UI 모듈 유형이 정의된 저장소 노드의 경로입니다.
* **clientlibs:** UI 모듈 유형을 구현하는 로드된 클라이언트 라이브러리의 카테고리입니다.

## Clientlibs {#clientlibs}

Clientlibs 섹션에는 [클라이언트 라이브러리 폴더](/help/implementing/developing/introduction/clientlibs.md) 해당 ContextHub가 로드되었습니다. 클라이언트 라이브러리는 다음과 같이 분류됩니다.

* **kernel.js:** ContextHub 프레임워크, 세그먼트 엔진 및 저장소 유형을 구현하는 클라이언트 라이브러리입니다.
* **ui.js:** ContextHub UI 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리.
* **style.css:** 클라이언트 라이브러리에서 로드되는 CSS 파일입니다.

## URL {#urls}

URL 섹션에는 ContextHub 기능에 대한 링크가 포함되어 있습니다.

* **구성 편집기:** 를 엽니다. [ContextHub 구성 페이지](configuring-contexthub.md) 저장소, UI 모드 및 UI 모듈을 구성할 수 있는 위치입니다.
* **ContextHub 모듈 구성:** 를 엽니다. `/etc/cloudsettings/default/contexthub.config.kernel.js` ContextHub 저장소 구성의 Javascript 개체 표현이 들어 있는 파일입니다.
* **ContextHub UI 구성:** 를 엽니다. `/etc/cloudsettings/default/contexthub.config.ui.js` ContextHub UI 모드 구성의 Javascript 개체 표현이 포함된 파일입니다.
* **kernel.js:** 를 엽니다. `/etc/cloudsettings/default/contexthub.kernel.js` ContextHub 프레임워크, 세그먼트 엔진 및 저장소 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 들어 있는 파일입니다.
* **ui.js:** 를 엽니다. `/etc/cloudsettings/default/contexthub.ui.js` ContextHub UI 및 UI 모듈 유형을 구현하는 클라이언트 라이브러리의 소스 코드가 들어 있는 파일입니다.
* **style.css:** 를 엽니다. `/etc/cloudsettings/default/contexthub.styles.css` ContextHub UI 및 UI 모듈의 CSS 스타일을 포함하는 파일입니다.
