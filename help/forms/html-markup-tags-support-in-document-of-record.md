---
title: 기록 문서에서 지원되는 HTML 마크업 태그
description: 렌더링 동작 및 접근성 고려 사항을 포함하여 기록 문서 생성에서 이제 HTML 마크업 태그에 대한 참조 안내서가 지원됩니다
feature: Adaptive Forms
role: Developer, User
source-git-commit: 739b2b396bf0c9042d6287bfba2e8e8792cabf70
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 7%

---



# 기록 문서에서 지원되는 HTML 마크업 태그

## 이 참조가 다루는 내용은 무엇입니까?

이제 AEM Forms은 DoR(문서 기록) PDF를 생성할 때 서식 있는 텍스트 필드의 HTML 마크업 태그를 지원합니다. 이 안내서에서는 적응형 Forms에서 안전하게 사용할 수 있는 HTML 마크업 태그와 생성된 문서에서 이들 태그를 렌더링하는 방법에 대해 설명합니다.

양식에 서식 있는 텍스트 콘텐츠(예: 굵은 서식, 목록 또는 링크)를 추가하는 경우 지원되는 태그와 제한 사항을 이해하는 것이 중요합니다. 이 참조는 콘텐츠가 올바르게 표시되고 기록 문서에서 액세스할 수 있는 상태를 유지하기 위해 적절한 태그를 선택하는 데 도움이 됩니다.

## 시작하기 전

### 사전 요구 사항

다음 사항을 숙지해야 합니다.

- 기본 HTML 마크업 구문
- [기록 문서 기본 사항](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- 접근성 원칙 및 WCAG 지침
- PDF 접근성 요구 사항
- HTML 마크업을 수락하는 적응형 양식 구성 요소

### 고려 사항

기록 문서(DoR)는 태그가 지정된 PDF일 수 있으므로 보조 기술에 대한 접근성과 적절한 구조를 유지하는 데 도움이 됩니다. 태그가 지정된 PDF 출력을 사용하려면 [XCI 속성 `config/present/pdf/tagged`을(를) `true`](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file)(으)로 설정합니다. PDF을 생성한 후에는 접근성 태그가 올바르게 적용되었는지 확인해야 합니다. [Adobe Acrobat을 사용하여 접근성 태그](https://helpx.adobe.com/in/acrobat/using/create-verify-pdf-accessibility.html)를 확인하고 문서가 접근성 표준을 충족하는지 확인할 수 있습니다.

### 새로운 기능

기록 문서의 리치 텍스트 지원은 최근 향상된 기능입니다. 이전에는 생성된 문서에서 서식 있는 텍스트 콘텐츠가 일반 텍스트로 표시되었습니다. 이 새로운 기능을 사용하면 형식이 지정된 콘텐츠를 PDF 출력에서 제대로 렌더링할 수 있습니다.

## HTML 태그 지원 참조

### 완전히 지원되는 태그

이러한 태그는 적절한 접근성 노드 생성으로 완벽하게 지원됩니다.

| HTML 태그 | 설명 | 기록 문서 지원 | 접근성 | 예 |
|----------|-------------|-------------|---------------|---------|
| `<p>` | 단락 | 예 | 완전히 지원됨 - `<P>` 노드 수정 | `<p>This is a paragraph.</p>` |
| `<br/>` | 줄 바꿈 | 예 | 완전히 지원됨 - `<P>` 노드 내 | `<p>Line 1<br/>Line 2</p>` |
| `<b>` | 굵은 텍스트 | 예 | 완전히 지원됨 - `<P>` 노드 내 | `<b>bold text</b>` |
| `<i>` | 기울임체 텍스트 | 예 | 완전히 지원됨 - `<P>` 노드 내 | `<i>italic text</i>` |
| `<span>` | 범용 인라인 컨테이너 | 예 | 블록 요소 내 | `<span>styled text</span>` |
| `<sub>` | 아래 첨자 | 예 | 전체 지원 - 블록 요소 내 | `H<sub>2</sub>O` |
| `<sup>` | 위 첨자 | 예 | 전체 지원 - 블록 요소 내 | `E=mc<sup>2</sup>` |
| `<a>` | 하이퍼링크 | 예 | 제한된 지원 - 적절한 중첩 필요 | `<a href="url">link text</a>` |


#### 목록 액세스 가능성 문제

현재 목록 렌더링이 올바른 목록 구조 대신 `<P>`개의 노드를 만듭니다.

```
Current: <P>1. First item
Current: <P>2. Second item

Expected: <L>
Expected:   <LI>
Expected:     <LBL>1.
Expected:     <LBody>First item
```

### 지원되지 않는 태그

이러한 태그는 지원되지 않으며 제대로 렌더링되지 않습니다.

| HTML 태그 | 설명 | 대체 솔루션 |
|----------|-------------|---------------------|
| `<h1>` - `<h6>` | 제목 태그 | 스타일이 지정된 `<p>` 태그 또는 디자인 수준 헤더 사용 |
| `<img>` | 이미지 | 별도의 이미지 필드 또는 디자인 템플릿 사용 |
| `<code>` | 코드 블록 | `<span>` 스타일에 고정 공간 글꼴 사용 |
| `<blockquote>` | 블록 인용 | 들여쓰기를 사용하여 스타일이 지정된 `<p>` 태그 사용 |
| `<table>` | 표 | 적응형 양식 표 구성 요소 사용 |

## 코드 예

### 기본 텍스트 서식

```html
<!--  Supported - renders correctly -->
<p>This paragraph contains <b>bold text</b> and <i>italic text</i>.</p>

<!--  Supported - combined formatting -->
<p>This text is <i><b>bold and italic</b></i>.</p>

<!--  Unsupported - headings don't work -->
<h1>This won't render as a heading</h1>
```

### 목록

```html
<!-- ⚠️ Partially supported - renders but not accessible -->
<ol>
  <li>First numbered item</li>
  <li>Second numbered item</li>
</ol>

<ul>
  <li>First bullet point</li>
  <li>Second bullet point</li>
</ul>
```

### 링크

```html
<!--  Supported - but must be within block elements -->
<p>Visit our <a href="https://example.com">website</a> for more information.</p>

<!--  Incorrect - link not properly nested -->
<a href="https://example.com">Standalone link</a>
```

### 과학적 표기법

```html
<!--  Supported - but limited accessibility -->
<p>Water formula: H<sub>2</sub>O</p>
<p>Einstein's equation: E=mc<sup>2</sup></p>
```

## 관련 정보

### AEM Forms 설명서

- [적응형 양식의 기록 문서 생성](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- [핵심 구성 요소에 대한 기록 문서 생성](/help/forms/generate-document-of-record-core-components.md)
- [기록 문서 템플릿 사용자 정의](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record)

### 기술 참조

- [XFA 사양 - XHTML 및 CSS 특성](https://www.adobe.com/devnet/acrobat/pdfs/XFA-3_3.pdf)&#x200B;(1187페이지)
- [PDF 접근성 표준](https://www.w3.org/TR/WCAG21/)
- [핵심 접근성 API 매핑](https://www.w3.org/TR/core-aam-1.2/#role-map-superscript)

### 모범 사례 안내서

- [액세스 가능한 PDF 만들기](https://www.adobe.com/accessibility/pdf.html)
- [양식의 리치 텍스트 모범 사례](/help/forms/creating-accessible-adaptive-forms.md)
- [접근성을 위한 문서 구조](/help/forms/creating-accessible-adaptive-forms.md)

