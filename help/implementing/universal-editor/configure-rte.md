---
title: 범용 편집기에 대한 RTE 구성
description: 범용 편집기에서 리치 텍스트 편집기(RTE)를 구성하는 방법을 이해합니다.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 60699db418e5f02b8bdb0471eb2996c9caf5694b
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# 범용 편집기에 대한 RTE 구성 {#configure-rte}

범용 편집기에서 리치 텍스트 편집기(RTE)를 구성하는 방법을 이해합니다.

>[!NOTE]
>
>이 설명서는 얼리어답터 기능으로 사용할 수 있는 유니버설 편집기용 새 RTE에 적용됩니다. 이 새로운 기능을 테스트하려면 [자세한 내용은 릴리스 정보를 참조하십시오.](/help/release-notes/universal-editor/current.md#new-rte)

## 개요 {#overview}

유니버설 편집기는 작성자가 텍스트를 편집할 때 서식 변경 사항을 적용할 수 있도록 하기 위해 서식 있는 텍스트 편집기(RTE)를 현재 위치 및 속성 패널에 제공합니다.

이 RTE는 [구성 요소 필터를 사용하여 구성할 수 있습니다.](/help/implementing/universal-editor/filtering.md) 이 문서에서는 예제와 함께 사용 가능한 구성 옵션에 대해 설명합니다.

## 구성 구조 {#structure}

RTE 구성은 다음 두 부분으로 구성됩니다.

* [`toolbar`](#toolbar): 도구 모음 구성은 UI에서 사용할 수 있는 편집 옵션과 구성 방법을 제어합니다.
* [`actions`](#actions): 작업 구성을 사용하면 개별 편집 작업의 동작 및 모양을 사용자 지정할 수 있습니다.

이러한 구성은 속성이 [인 &#x200B;](/help/implementing/universal-editor/filtering.md)구성 요소 필터`rte`의 일부로 정의할 수 있습니다.

```json
[
  {
    "id": "richtext",
    "rte": {
      "toolbar": {
        // Toolbar configuration
      },
      "actions": {
        // Action-specific configurations
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## 도구 모음 구성 {#toolbar}

도구 모음 구성은 UI에서 사용할 수 있는 편집 옵션과 구성 방법을 제어합니다. 사용 가능한 섹션은 다음과 같습니다

```json
{
  "toolbar": {
    // Text formatting options
    "format": ["bold", "italic", "underline", "strike"],
    // Text alignment options
    "alignment": ["left", "center", "right", "justify"],
    // Text direction options, right-to-left or left-to-right
    "direction": ["rtl", "ltr"],
    // Indentation controls
    "indentation": ["indent", "outdent"],
    // Block-level elements
    "blocks": ["paragraph", "h1", "h2", "h3", "h4", "h5", "h6", "code_block"],
    // List options
    "list": ["bullet_list", "ordered_list"],
    // Content insertion
    "insert": ["link", "unlink"],
    // Superscript/subscript
    "sr_script": ["superscript", "subscript"],
    // Editor utilities
    "editor": ["removeformat"],
    // Section ordering (optional)
    "sections": ["format", "alignment", "list"]
  }
}
```

## 작업 구성 {#actions}

작업 구성을 사용하면 개별 편집 작업의 비헤이비어와 모양을 사용자 지정할 수 있습니다. 사용 가능한 섹션입니다.

### 액션 포맷 {#format}

형식 작업은 형식을 적용하고 의미 체계 변형 중에서 선택하는 HTML 태그 전환을 지원하는 데 사용됩니다. 다음 섹션을 사용할 수 있습니다.

```json
{
  "actions": {
    "bold": {
      "tag": "strong",      // Use <strong> instead of <b>
      "shortcut": "Mod-B",  // Custom keyboard shortcut
      "label": "Make Bold"  // Custom button label 
    },
    "italic": {
      "tag": "em",          // Use <em> instead of <i>
      "shortcut": "Mod-I",
      "label": "Italicize"
    },
    "strike": {
      "tag": "del"          // Use <del> instead of <s>
    }
  }
}
```

### 작업 나열 {#list}

목록 작업은 HTML 구조를 제어하는 컨텐츠 줄바꿈을 지원합니다. 다음 섹션을 사용할 수 있습니다.

```json
{
  "actions": {
    "bullet_list": {
      "wrapInParagraphs": true,    // <ul><li><p>content</p></li></ul>
      "shortcut": "Mod-Shift-8",   // Custom shortcut
      "label": "Bullet List"       // Custom label
    },
    "ordered_list": {
      "wrapInParagraphs": false,   // <ol><li>content</li></ol> (default)
      "shortcut": "Mod-Shift-9"
    }
  }
}
```

### 링크 작업 {#link}

링크 작업은 링크 동작을 관리하기 위해 대상 속성 제어를 지원합니다. 다음 섹션을 사용할 수 있습니다.

```json
{
  "actions": {
    "link": {
      "hideTarget": false,       // Show target attribute options (default)
      "shortcut": "Mod-K",       // Custom keyboard shortcut
      "label": "Insert Link"     // Custom button label
    },
    "unlink": {
      "shortcut": "Mod-Shift-K", // Custom keyboard shortcut
      "label": "Remove Link"     // Custom button label
    }
  }
}
```

#### 링크 구성 옵션 {#link-options}

* `hideTarget`: `false`(기본값) - 링크에 대상 특성을 포함하여 `_self`, `_blank` 등을 허용합니다.
* `hideTarget`: `true` - 링크에서 대상 특성을 완전히 제외

`unlink` 동작은 기존 링크 내에 커서가 있는 경우에만 나타납니다. 텍스트 콘텐츠를 유지하면서 링크 서식을 제거합니다.

### 기타 작업 {#other}

다른 모든 작업은 기본 사용자 지정을 지원합니다. 다음 섹션을 사용할 수 있습니다.

```json
{
  "actions": {
    "h1": {
      "shortcut": "Mod-Alt-1",
      "label": "Large Heading"
    },
    "paragraph": {
      "shortcut": "Mod-Alt-0",
      "label": "Normal Text"
    },
    "link": {
      "shortcut": "Mod-K",
      "label": "Insert Link",
      "hideTarget": false    // Show target attribute options (default: false)
    }
  }
}
```

## 전체 예 {#example}

다음은 전체 구성의 예입니다.

```json
[
  {
    "id": "richtext",
    "rte": {
      // Configure which tools appear in toolbar
      "toolbar": {
        "format": [
          "bold",
          "italic"
        ],
        "blocks": [
          "paragraph",
          "h1",
          "h2"
        ],
        "list": [
          "bullet_list",
          "ordered_list"
        ],
        "insert": [
          "link",
          "unlink"
        ],
        "sections": [
          "format",
          "blocks",
          "list",
          "insert"
        ]
      },
      // Customize individual action behavior
      "actions": {
        // Format actions with HTML tag choices
        "bold": {
          "tag": "strong",
          "shortcut": "Mod-B",
          "label": "Bold"
        },
        "italic": {
          "tag": "em",
          "shortcut": "Mod-I"
        },
        // List actions with content wrapping
        "bullet_list": {
          "wrapInParagraphs": true,
          "label": "Bullet List"
        },
        "ordered_list": {
          "wrapInParagraphs": false
        },
        // Link actions with target control
        "link": {
          "hideTarget": false,
          "shortcut": "Mod-K",
          "label": "Add Link"
        },
        "unlink": {
          "label": "Remove Link"
        },
        // Other actions with basic customization
        "h1": {
          "shortcut": "Mod-Alt-1",
          "label": "Main Heading"
        }
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## 작업 옵션 세부 정보 {#action-details}

몇 가지 옵션에는 기억해야 할 중요한 추가 세부 사항이 있습니다.

### `wrapInParagraphs` {#wrapInParagraphs}

목록에 대한 `wrapInParagraphs` 옵션은 HTML 구조를 제어합니다.

#### `wrapInParagraphs: false` (기본값) {#wrapInParagraphs-false}

```html
<ul>
  <li>Simple text content</li>
  <li>Another item</li>
</ul>
```

#### `wrapInParagraphs: true` {#wrapInParagraphs-true}

```html
<ul>
  <li><p>Text wrapped in paragraphs</p></li>
  <li><p>Supports rich formatting within items</p></li>
</ul>
```

필요한 경우 `wrapInParagraphs: true`을(를) 사용합니다.

* 목록 항목 내의 서식
* 목록 항목당 여러 단락
* 일관된 블록 수준 스타일

### 링크 대상 옵션 {#link-target}

링크에 대한 `hideTarget` 옵션은 생성된 링크에 `target` 특성이 포함되어 있는지 여부와 링크 생성을 위한 대화 상자에 대상 선택을 위한 필드가 포함되어 있는지 여부를 제어합니다.

#### `hideTarget: false` (기본값) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### 태그 옵션 {#tag}

형식 작업을 사용하면 HTML 변형 간을 전환할 수 있습니다.

| 작업 | 기본 태그 | 대체 태그 | 사용 사례 |
|---|---|---|---|
| `bold` | `<strong>` | `<b>` | 의미론적 강조와 시각적 강조 |
| `italic` | `<em>` | `<i>` | 의미 체계와 시각적 스타일 비교 |
| `strike` | `<del>` | `<s>` | 시각적 대 의미 체계 삭제 |

액세스 가능성 및 SEO 향상을 위해 의미 체계 태그(`<strong>`, `<em>`, `<del>`)를 선택하십시오.

### 키보드 단축키 {#keyboard-shortcuts}

바로 가기는 `Mod-Key` 형식을 사용합니다. 여기서

* `Mod` = `Cmd`(Mac), `Ctrl`(Windows/Linux)
* 예: `Mod-B`, `Mod-Shift-8`, `Mod-Alt-1`
