---
title: 범용 편집기에 대한 RTE 구성
description: 범용 편집기에서 리치 텍스트 편집기(RTE)를 구성하는 방법을 이해합니다.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: 8fcad5e212b1c64d3939065ab277e426935cb5ec
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 1%

---


# 범용 편집기에 대한 RTE 구성 {#configure-rte}

범용 편집기에서 리치 텍스트 편집기(RTE)를 구성하는 방법을 이해합니다.

## 개요 {#overview}

유니버설 편집기는 작성자가 텍스트를 편집할 때 서식 변경 사항을 적용할 수 있도록 하기 위해 서식 있는 텍스트 편집기(RTE)를 현재 위치 및 속성 패널에 제공합니다.

이 RTE는 [구성 요소 필터를 사용하여 구성할 수 있습니다.](/help/implementing/universal-editor/filtering.md) 이 문서에서는 예제와 함께 사용 가능한 구성 옵션에 대해 설명합니다.

>[!NOTE]
>
>유니버설 편집기 프로젝트를 시작하면 백엔드가 지원하는 모든 서식 있는 텍스트 기능(Edge Delivery이 포함된 AEM 또는 Headless 구현)이 자동으로 활성화되고 [RTE의 모달 편집기 창에서 사용할 수 있습니다.](/help/sites-cloud/authoring/universal-editor/authoring.md#modal-editor)
>
>* 필요하지 않은 옵션을 비활성화할 수 있습니다.
>* 프로젝트 유형과 호환되지 않는 옵션 활성화는 지원되지 않습니다.

## 구성 구조 {#structure}

RTE 구성은 다음 두 부분으로 구성됩니다.

* [`toolbar`](#toolbar): 도구 모음 구성은 UI에서 사용할 수 있는 편집 옵션과 구성 방법을 제어합니다.
* [`actions`](#actions): 작업 구성을 사용하면 개별 편집 작업의 동작 및 모양을 사용자 지정할 수 있습니다.

이러한 구성은 속성이 [인 ](/help/implementing/universal-editor/filtering.md)구성 요소 필터`rte`의 일부로 정의할 수 있습니다.

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
    "insert": ["link", "unlink", "image", "special_characters"],
    // Superscript/subscript
    "sr_script": ["superscript", "subscript"],
    // Editor utilities
    "editor": ["removeformat"],
    // Section ordering (optional)
    "sections": ["format", "alignment", "list"]
  }
}
```

## 액션 구성 {#action}

작업 구성을 사용하면 개별 편집 작업의 비헤이비어와 모양을 사용자 지정할 수 있습니다. 사용 가능한 섹션입니다.

### 일반 작업 옵션 {#common-action-options}

대부분의 작업은 다음과 같은 공통 옵션을 지원합니다.

* `shortcut?`: 문자열 - 작업의 기본 키보드 단축키를 무시합니다(있는 경우).
* `label?`: 문자열 - UI에서 작업에 사용되는 레이블을 재정의합니다.
* `hideInline?`: 부울 - `true`일 때 은 컨텍스트 내(인라인) RTE 편집기 도구 모음에서 이 작업을 숨깁니다.

```json
{
  "actions": {
    "bold": {
      "label": "Bold",
      "shortcut": "Mod-B",
      "hideInline": true
    }
  }
}
```

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

### 테이블 작업 {#table-actions}

표 작업은 표 셀에서 HTML 구조를 제어하는 컨텐츠 줄바꿈을 지원합니다.

```json
{
  "actions": {
    "table": {
      "wrapInParagraphs": false, // <td>content</td> (default)
      "shortcut": "Mod-Alt-T",   // Custom shortcut
      "label": "Insert Table"    // Custom label
    }
  }
}
```

#### 표 구성 옵션 {#table-configuration-options}

* `wrapInParagraphs`: `false`(기본값) - 테이블 셀에 래핑되지 않은 텍스트 콘텐츠가 포함되어 있습니다.
* `wrapInParagraphs`: `true` - 테이블 셀이 단락 태그의 콘텐츠를 래핑합니다.

샘플:

`wrapInParagraphs`: `false`일 때:

```html
<!-- Single line -->
<td>Cell content</td>

<!-- Multiple paragraphs get <br> separation -->
<td>Line 1<br />Line 2</td>
```

`wrapInParagraphs`: `true`일 때:

```html
<!-- Single paragraph -->
<td><p>Cell content</p></td>

<!-- Multiple paragraphs preserved -->
<td>
  <p>Line 1</p>
  <p>Line 2</p>
</td>
```

>[!NOTE]
>
>단락(`wrapInParagraphs`: `false`)의 줄바꿈을 해제할 때 삭제기가 여러 단락 사이에 `<br>` 태그를 자동으로 삽입하여 시각적 줄 바꿈을 유지합니다. 이는 주요 리치 텍스트 편집기의 HTML 표준 및 일반적인 관행을 따릅니다.

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

### 이미지 작업 {#image}

이미지 작업은 응답형 이미지 마크업을 생성하기 위해 그림 요소 래핑을 지원합니다. 다음 섹션을 사용할 수 있습니다.

```json
{
  "actions": {
    "image": {
      "wrapInPicture": false,     // Use <img> tag (default)
      "shortcut": "Mod-Shift-I",  // Custom keyboard shortcut
      "label": "Insert Image"     // Custom button label
    }
  }
}
```

#### 이미지 구성 옵션 {#image-options}

* `wrapInPicture`: `false`(기본값) - 단순 `<img>` 요소 생성
* `wrapInPicture`: `true` - 반응형 디자인을 위해 `<picture>` 요소에서 이미지 줄바꿈

### 들여쓰기 구성 {#indentation}

들여쓰기에는 들여쓰기 동작의 범위를 제어하는 기능 수준 구성과 바로 가기 및 레이블에 대한 개별 작업 구성이 있습니다.

```json
{
  "actions": {
    // Feature-level configuration
    "indentation": {
      "scope": "all"  // Controls what content can be indented (default: "all")
    },

    // Individual action configurations
    "indent": {
      "shortcut": "Tab",           // Custom keyboard shortcut
      "label": "Increase Indent"   // Custom button label
    },
    "outdent": {
      "shortcut": "Shift-Tab",     // Custom keyboard shortcut
      "label": "Decrease Indent"   // Custom button label
    }
  }
}
```

#### 들여쓰기 범위 옵션 {#indentation-options}

* `scope`: `all`(기본값) - 들여쓰기/내어쓰기가 모든 콘텐츠에 적용됩니다.
   * 목록: 목록 항목 중첩/중첩 해제
   * 단락 및 제목: 일반 들여쓰기 수준 증가/감소
* `scope`: `lists` - 들여쓰기/내어쓰기는 목록 항목에만 적용됩니다.
   * 목록: 목록 항목 중첩/중첩 해제
   * 단락 및 머리글: 들여쓰기 없음(이들에 대해 비활성화된 단추)

>[!NOTE]
>
>Tab/Shift+Tab 키를 통한 목록 중첩은 일반 들여쓰기 설정과 독립적으로 작동합니다.

### 특수 문자 {#special-characters}

`special_characters` 삽입 작업을 수행하면 커서 위치에 특수 문자(기호, 수학 연산자, 통화 기호, 구두점, 화살표 등)를 삽입할 수 있는 문자 선택 팝오버가 열립니다.

```json
{
  "toolbar": {
    "insert": ["link", "unlink", "image", "table", "special_characters"],
    "sections": ["insert"],
  },
  "actions": {
    "special_characters": {
      "label": "Special Characters"
    }
  }
}
```

일반적으로 사용되는 44개의 기본 문자 세트가 즉시 포함됩니다. 다음 두 가지 구성 옵션을 통해 문자 목록을 사용자 지정할 수 있습니다.

* `appendCharacters` - 기본 집합에 문자 추가
* `characters` - 기본 집합을 완전히 바꿉니다.

각 문자 항목에는 `character`(유니코드 문자)과 `title`(도구 설명/액세스 가능한 이름)이 있습니다.

#### 기본값에 문자 추가 {#append-special-characters}

```json
{
  "actions": {
    "special_characters": {
      "appendCharacters": [
        { "character": "\u2605", "title": "Black star" },
        { "character": "\u2764", "title": "Heavy black heart" },
      ];
    }
  }
}
```

#### 기본 특수 문자 바꾸기 {#replace-special-characters}

```json
{
  "actions": {
    "special_characters": {
      "characters": [
        { "character": "\u00A9", "title": "Copyright sign" },
        { "character": "\u00AE", "title": "Registered sign" },
        { "character": "\u2122", "title": "Trade mark sign" },
      ];
    }
  }
}
```

#### 두 옵션을 함께 사용 {#both-special-character-options}

이 예제에서는 `characters`을(를) 기본으로 사용한 다음 `appendCharacters`을(를) 사용하여 추가 문자를 추가합니다.

```json
{
  "actions": {
    "special_characters": {
      "characters": [
        { "character": "\u00A9", "title": "Copyright sign" },
        { "character": "\u00AE", "title": "Registered sign" }
      ],
      "appendCharacters": [
        { "character": "\u2605", "title": "Black star" }
      ]
    }
  }
}
```

### 텍스트로 붙여넣기 {#paste-as-text}

`paste_text` 편집기 작업을 사용하면 표준 일반 텍스트로 붙여넣기 워크플로를 사용할 수 있습니다.

* **기본 바로 가기:** Mod-Shift-v(macOS의 경우 Cmd+Shift+V, Windows/Linux의 경우 Ctrl+Shift+V)
* **동작:** 텍스트/일반 붙여넣기(원본 서식 무시)
   * 목록에서 새 행은 새 목록 항목을 만듭니다.

```json
{
  "toolbar": {
    "editor": ["removeformat", "paste_text"]
  },
  "actions": {
    "paste_text": {
      "shortcut": "Mod-Shift-v",
      "label": "Paste as Text"
    }
  }
}
```

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
          "unlink",
          "image",
          "special_characters"
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
        // Image actions with picture wrapping
        "image": {
          "wrapInPicture": false, // Use <img> tag instead of <picture>
          "shortcut": "Mod-Shift-I",
          "label": "Insert Image",
        },
        // Special characters with custom additions
        "special_characters": {
          "label": "Special Characters",
          "appendCharacters": [{ "character": "\u2605", "title": "Black star" }],
        },
        // Other actions with basic customization
        "h1": {
          "shortcut": "Mod-Alt-1",
          "label": "Main Heading"
        }
      }
    }
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

### `wrapInPicture`{#wrapinpicture}

이미지에 대한 `wrapInPicture` 옵션은 이미지 콘텐츠에 대해 생성된 HTML 구조를 제어합니다.

#### wrapInPicture: false(기본값) {#wrapinpicture-false}

```html
<img src="image.jpg" alt="Description" />
```

#### wrapInPicture: true {#wrapinpicture-true}

```html
<picture>
  <img src="image.jpg" alt="Description" />
</picture>
```

필요한 경우 `wrapInPicture: true`을(를) 사용합니다.

* `<source>`개 요소로 반응형 이미지를 지원합니다.
* 미술 감독 기능.
* 고급 이미지 기능에 대한 향후 교정.
* 일관된 그림 요소 구조.

>[!NOTE]
>
>`wrapInPicture: true`이(가) 활성화되면 다양한 미디어 쿼리 및 형식에 대한 추가 `<source>` 요소로 이미지를 개선할 수 있으므로 반응형 디자인에 보다 유연하게 사용할 수 있습니다.

### 링크 대상 옵션 {#link-target}

링크에 대한 `hideTarget` 옵션은 생성된 링크에 `target` 특성이 포함되어 있는지 여부와 링크 생성을 위한 대화 상자에 대상 선택을 위한 필드가 포함되어 있는지 여부를 제어합니다.

#### `hideTarget: false` (기본값) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

#### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### 이미지에 링크 비활성화 {#disableforimages}

링크에 대한 `disableForImages` 옵션은 사용자가 이미지 및 그림 요소에 링크를 만들 수 있는지 여부를 제어합니다. 이는 인라인 `<img>` 요소와 블록 수준 `<picture>` 요소 모두에 적용됩니다.

#### `disableForImages: false` (기본값) {#disableforimages-false}

사용자는 이미지를 선택하여 링크로 래핑할 수 있습니다.

```html
<!-- Inline image with link -->
<a href="https://example.com">
  <img src="image.jpg" alt="Description" />
</a>

<!-- Block-level picture with link -->
<a href="https://example.com">
  <picture>
    <img src="image.jpg" alt="Description" />
  </picture>
</a>
```

#### disableForImages: true {#disableforimages-true}

이미지 또는 그림을 선택하면 링크 버튼이 비활성화됩니다. 사용자는 텍스트 콘텐츠에만 링크를 만들 수 있습니다.

```html
<!-- Images remain standalone without links -->
<img src="image.jpg" alt="Description" />

<picture>
  <img src="image.jpg" alt="Description" />
</picture>

<!-- Links work normally on text -->
<a href="https://example.com">Link text</a>
```

다음을 원할 때 `disableForImages: true`을(를) 사용합니다.

* 연결된 이미지를 방지하여 시각적 일관성을 유지합니다.
* 탐색에서 이미지를 분리하여 콘텐츠 구조를 간소화합니다.
* 이미지 연결을 제한하는 컨텐츠 정책을 적용합니다.
* 콘텐츠의 접근성 복잡성을 줄입니다.

>[!NOTE]
>
>이 설정은 이미지에 새 링크를 만드는 기능에만 영향을 줍니다. 콘텐츠의 이미지에서 기존 링크가 제거되지는 않습니다.

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

## 지원되지 않는 HTML {#unsupported-html}

기본적으로 알 수 없는 HTML 태그는 편집기에서 구문 분석하면 제거됩니다. 이를 유지하려면 `unsupportedHtml` 구성 옵션을 통해 옵트인하십시오.

```javascript
const rteConfig = {
  unsupportedHtml: true, // preserve unknown HTML tags (default: false)
};
```

| 값 | 비헤이비어 |
|---|---|
| `false` (기본값) | 구문 분석 중에 알 수 없는 HTML 태그가 삭제됩니다. |
| `true` | 알 수 없는 HTML 태그는 콘텐츠가 안전하게 왕복할 수 있도록 사용자 지정 지원되지 않는 블록 노드에 래핑됩니다. |

활성화되면 편집기는 `rte-unsupported-block` 클래스로 지원되지 않는 노드를 렌더링합니다. 소비자 앱은 이 클래스에 대한 스타일을 제공해야 합니다(예: 테두리, 패딩, 배경). 블록 내의 태그 레이블은 `rte-unsupported-label`을(를) 사용하며, 이 값은 사용자 지정할 수도 있습니다.
