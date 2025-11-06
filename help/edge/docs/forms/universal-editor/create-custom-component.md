---
title: EDS 양식에 대한 사용자 정의 구성 요소 만들기
description: EDS 양식에 대한 사용자 정의 구성 요소 만들기
feature: Edge Delivery Services
role: Admin, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2103'
ht-degree: 100%

---


# 적응형 양식 블록에서 사용자 정의 양식 구성 요소 만들기

Edge Delivery Services 양식은 사용자 정의 기능을 제공하여 프론트엔드 개발자가 맞춤형 양식 구성 요소를 구축할 수 있도록 합니다. 이러한 사용자 정의 구성 요소는 WYSIWYG 저작 환경에 완벽하게 통합되어 양식 작성자가 양식 편집기 내에서 쉽게 추가, 구성 및 관리할 수 있습니다. 사용자 정의 구성 요소를 통해 작성자는 기능을 향상시키면서 원활하고 직관적인 작성 과정을 보장할 수 있습니다.

이 문서에서는 사용자 경험을 개선하고 양식의 시각적 매력을 높이기 위해 기본 HTML 양식 구성 요소의 스타일을 지정하여 사용자 정의 구성 요소를 만드는 절차에 대해 설명합니다.

## 아키텍처 개요

형식 블록의 사용자 정의 구성 요소는 **MVC(Model-View-Controller)** 아키텍처 패턴을 따릅니다.

### 모델

- 각 `field/component`에 해당하는 JSON 스키마에 따라 정의됩니다.

- 작성 가능한 속성은 해당 JSON 파일에서 지정됩니다(블록/양식/모델/양식- 구성 요소 참조).

- 이러한 속성은 작성자가 양식 빌더에서 사용할 수 있고 필드 정의(fd)의 일부로 구성 요소에 전달됩니다.

### 보기

- 각 필드 유형의 HTML 구조에 대해서는 form-field-types에 설명되어 있습니다.

- 이것은 확장 또는 수정이 가능한 구성 요소의 기본 구조입니다.

- 각 OOTB 구성 요소의 기본 HTML 구조는 form-field-types에 문서화되어 있습니다.

### 컨트롤러/구성 요소 논리

- JavaScript에서 OOTB(기본 제공) 또는 사용자 정의 구성 요소로 구현되었습니다.  - 사용자 정의 구성 요소의 `blocks/form/components`에 있습니다.

## OOTB 구성 요소

**OOTB(기본 제공)** 구성 요소는 사용자 정의 개발의 토대를 제공합니다.

- OOTB 구성 요소는 `blocks/form/models/form-components`에 있습니다.

- 각 OOTB 구성 요소에는 작성 가능한 속성(예: ` _text-input.json`,`_drop-down.json`)을 정의하는 JSON 파일이 있습니다.

- 이러한 속성은 작성자가 양식 빌더에서 사용할 수 있고 필드 정의(fd)의 일부로 구성 요소에 전달됩니다.

- 각 OOTB 구성 요소의 기본 HTML 구조는 form-field-types에 문서화되어 있습니다.

기존 OOTB 구성 요소를 확장하면 기본 구조, 동작 및 속성을 재사용하는 동시에 필요에 따라 이를 사용자 정의할 수 있습니다.

- 사용자 정의 구성 요소는 사전 정의된 OOTB 구성 요소 세트에서 확장되어야 합니다.

- 시스템은 필드의 JSON에 있는 `viewType` 속성을 기반으로 확장할 OOTB 구성 요소를 식별합니다.

- 시스템은 허용된 사용자 정의 구성 요소 변형의 레지스트리를 유지 관리합니다. 이 레지스트리에 나열된 변형만 사용할 수 있습니다(예: `mappings.js`의 `customComponents[]`).

- 양식을 렌더링할 때 시스템은 변형 속성 또는 `:type/fd:viewType`을 확인하며, 이것이 등록된 사용자 정의 구성 요소와 일치하는 경우에는 `blocks/form/components` 폴더에서 해당 JS 및 CSS 파일을 로드합니다.

- 그러면 사용자 정의 구성 요소가 OOTB 구성 요소의 기본 HTML 구조에 적용되므로 사용자는 그 동작과 모양을 개선하거나 재정의할 수 있습니다.

## 사용자 정의 구성 요소의 구조

사용자 정의 구성 요소를 만들려면 **Scaffold CLI**&#x200B;를 사용하여 구성 요소에 필요한 파일과 폴더를 설정한 다음 사용자 정의 구성 요소에 해당하는 코드를 추가할 수 있습니다.

- 사용자 정의 구성 요소는 `blocks/form/components` 폴더에 있습니다.

- 각 사용자 정의 구성 요소는 구성 요소의 이름을 딴 자체 폴더(예: cards)에 있어야 합니다. 폴더 내부에는 다음 파일이 있어야 합니다.

   - **_cards.json** - OOTB 구성 요소의 구성 요소 정의를 확장하고 로드 시 작성 가능한 속성(모델[])과 콘텐츠 구조(정의[])를 정의하는 JSON 파일입니다.
   - **cards.js** - 기본 논리를 포함하는 JavaScript 파일입니다.
   - **cards.css** - 스타일에 대한 옵션입니다.

- 폴더 이름과 JS/CSS 파일명이 일치해야 합니다.

### 사용자 정의 구성 요소에서 필드 재사용 및 확장

사용자 정의 구성 요소의 JSON에서 필드(모든 필드 그룹, 기본 항목, 유효성 검사, 도움말 등)를 정의할 때 유지 관리 가능성 및 일관성을 위해 다음 모범 사례를 따르십시오.

- 기존의 공유 컨테이너 또는 필드 정의(예: `../form-common/_basic-input-placeholder-fields.json#/fields`, `../form-common/_basic- validation-fields.json#/fields`)를 참조하여 표준/공유 필드를 재사용합니다. 이렇게 하면 표준 옵션을 복제하지 않고도 모두 상속할 수 있습니다.

- 컨테이너에 새 필드 또는 사용자 정의 필드만 명시적으로 추가합니다. 이렇게 하면 스키마가 깔끔하게 초점이 맞춰집니다.

- 참조를 통해 이미 포함된 복제 필드를 제거하거나 회피합니다. 구성 요소 로직에 고유한 필드만 정의합니다.

- 일관성 및 유지 관리 가능성을 위해 필요한 경우 도움말 컨테이너 및 기타 공유 콘텐츠(예: `../form-common/_help-container.json`)를 참조합니다.

>[!TIP]
>
> - 이 패턴을 사용하면 향후에 논리를 쉽게 업데이트하거나 확장할 수 있으며, 사용자 정의 구성 요소가 나머지 양식 시스템과 일관성을 유지하도록 할 수 있습니다.
> - 새 공유 컨테이너를 추가하기 전에 반드시 기존 공유 컨테이너 또는 필드 정의를 확인합니다.

### 사용자 정의 구성 요소의 새 속성 정의

- 작성자로부터 사용자 정의 구성 요소의 새 속성을 캡처해야 하는 경우, 구성 요소의 JSON에 있는 구성 요소의 `fields[]` 배열에서 필드를 정의하여 캡처할 수 있습니다.

- 사용자 정의 구성 요소는 JSON 파일에서 `fd:viewType`(예: `fd:viewType: cards`)로 설정할 수 있는 :type 속성을 사용하여 식별됩니다. 그러면 시스템은 올바른 사용자 정의 구성 요소를 인식하고 로드할 수 있으므로 이는 사용자 정의 구성 요소에서 필수입니다

- JSON 정의에 새로 추가된 속성은 모두 필드 정의에서 속성으로 사용할 수 있습니다. 구성 요소의 JS 논리의 `<propertyName>`

## 사용자 정의 구성 요소 JavaScript API

사용자 정의 구성 요소 JavaScript API는 사용자 정의 양식 구성 요소의 동작, 모양 및 반응성을 제어하는 방법을 정의합니다.

### 장식 함수

**장식** 함수는 사용자 정의 구성 요소의 진입점입니다. 이 함수는 구성 요소를 초기화하고, 이를 해당 JSON 정의와 연결하며, HTML 구조 및 동작을 조작할 수 있도록 합니다.

>[!NOTE]
>
> 사용자 정의 구성 요소의 JavaScript 파일은 기본 함수를 장식으로서 내보내야 합니다.

#### 함수 서명:

```javascript
export default function decorate(element, fieldJson, container, formId) 
{
  // element: The HTML structure of the OOTB component you are extending
  // fieldJson: The JSON field definition (all authorable properties)
  // container: The parent element (fieldset or form)
  // formId: The id of the form

  // ... your logic here ...
}
```

이 기능을 사용하면 다음이 가능합니다.

- **요소 수정**: 이벤트 리스너를 추가하거나, 속성을 업데이트하거나, 추가 마크업을 삽입합니다.

- **JSON 속성에 액세스**: `fd.properties.<propertyName>`을(를) 사용하여 JSON 스키마에 정의된 값을 읽고 구성 요소 논리에서 적용합니다.

## 구독 함수

**구독** 함수를 사용하면 구성 요소가 필드 값 또는 사용자 지정 이벤트의 변경 내용에 반응하도록 할 수 있습니다. 그러면 구성 요소는 양식의 데이터 모델과 동기화 상태를 유지하고 해당 UI를 동적으로 업데이트할 수 있습니다.

### 함수 서명:

```javascript
import { subscribe } from '../../rules/index.js';
export default function decorate(fieldDiv, fieldJson, container, formId) {
  // Access custom properties defined in the JSON
  const { initialText, finalText, time } = fieldJson?.properties;

  // ... setup logic ...

  subscribe(fieldDiv, formId, (_fieldDiv, fieldModel) => {
    fieldModel.subscribe(() => {
      // React to custom event (e.g., resetCardOption)
      // ... logic ...
    }, 'resetCardOption');
  });
}
```

이 기능을 사용하면 다음이 가능합니다.

- **콜백 등록**: **구독(요소, 양식 ID, 콜백)**&#x200B;을 호출하면 필드 데이터가 변경될 때마다 실행할 콜백을 등록합니다. 다음과 같은 2개의 콜백 매개변수를 사용합니다.
   - **element**: 필드를 나타내는 HTML 요소입니다.
   - **fieldModel**: 필드의 상태 및 이벤트 API를 나타내는 개체입니다.

- **변경 내용 또는 이벤트 수신**: 값이 변경되거나 사용자 지정 이벤트가 트리거될 때마다 논리를 실행하려면 `fieldModel.subscribe((event) => { ... }, 'eventName')`를 사용합니다. 이벤트 개체에는 변경된 내용에 대한 세부 정보가 포함되어 있습니다.

## 사용자 정의 구성 요소 만들기

이 섹션에서는 OOTB 라디오 버튼 구성 요소를 확장하여 **카드 사용자 정의 구성 요소**&#x200B;를 만드는 과정을 알아봅니다.

![카드 사용자 정의 구성 요소](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;1. 코드 설정

#### 1.1 파일 및 폴더

첫 번째 단계는 사용자 정의 구성 요소의 필수 파일을 설정하여 이를 저장소의 코드로 연결하는 것입니다. 이 프로세스는 **AEM Forms Scaffolder CLI**&#x200B;에 의해 자동으로 수행되므로 필수 파일을 더 빨리 스캐폴드하고 연결할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3474752)

1. 터미널을 열고 양식 프로젝트의 루트로 이동합니다.
2. 다음 명령을 실행합니다.

```bash
npm install
npm run create:custom-component
```

![스캐폴더 CLI](/help/edge/docs/forms/universal-editor/assets/scaffolder-cli.png)

다음 동작이 수행됩니다.

- 새 구성 요소의 **이름을 지정**&#x200B;하라는 메시지가 표시됩니다. 이 경우에는 cards를 사용하십시오.
- 기본 구성 요소를 **선택**&#x200B;하라는 메시지가 표시됩니다(라디오 그룹 선택).

이렇게 하면 다음을 포함하여 필요한 폴더와 파일이 모두 생성됩니다.

```
blocks/form/
└── components/
  └── cards/
    ├── cards.js
    └── cards.css
    └── _cards.json
```

그런 다음 CLI 출력에 표시된 대로 저장소의 나머지 코드와 이 코드를 연결합니다.
아래 기능이 자동으로 수행됩니다.

- 적응형 양식 블록 내에 추가할 수 있도록 필터에 카드를 추가합니다.
- 새 카드 구성 요소를 포함하도록 `mappings.js`의 허용 목록을 업데이트합니다.
- 범용 편집기의 **사용자 정의 구성 요소** 목록 아래에 카드 구성 요소의 정의를 등록합니다.

>[!NOTE]
>
> 기존의 수동 방법을 사용하여 사용자 정의 구성 요소를 만들 수도 있습니다. 자세한 내용은 [수동 또는 기존 메서드](#manual-or-legacy-method-to-create-custom-component)를 사용하여 사용자 정의 구성 요소 만들기 섹션을 참조하십시오.

#### 1.2 범용 편집기에서 구성 요소 사용하기

1. **범용 편집기 새로 고침**: 저장소에서 최신 코드를 로드할 수 있도록 범용 편집기에서 양식을 열고 페이지를 새로 고칩니다.

2. **사용자 정의 구성 요소 추가**

   1. 양식 캔버스에서 **추가(+)** 버튼을 클릭합니다.
   2. 사용자 정의 구성 요소 섹션으로 스크롤합니다.
   3. 새로 만든 **카드 구성 요소**&#x200B;를 선택하여 양식에 삽입합니다.

      ![사용자 정의 구성 요소 선택](/help/edge/docs/forms/universal-editor/assets/select-custom-component.png)

`cards.js` 내에 코드가 없으므로 사용자 정의 구성 요소가 라디오 그룹으로 렌더링됩니다.

#### 1.3 미리 보기 및 로컬 테스트

이제 양식에 사용자 정의 구성 요소가 포함되어 있으므로 양식을 프록시 설정하고 로컬에서 변경하여 변경 사항을 볼 수 있습니다.

1. 터미널로 이동하여 `aem up`을 실행합니다.

2. `http://localhost:3000/{path-to-your-form}`에서 시작된 프록시 서버를 엽니다(경로 예: `/content/forms/af/custom-component-form`).


### &#x200B;2. 사용자 정의 구성 요소에 대한 사용자 정의 동작 구현

#### 2.1 사용자 정의 구성 요소 스타일링

스타일을 지정할 구성 요소에 **카드** 클래스를 추가하고 각 라디오에 해당하는 이미지를 추가해 보겠습니다. 이를 위해 아래 코드를 사용하십시오.

**card.js를 사용하여 구성 요소 스타일 지정**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');

  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper) => {
    const image = createOptimizedPicture(
      'https://main--afb--jalagari.hlx.live/lab/images/card.png',
      'card-image'
    );
    radioWrapper.appendChild(image);
  });

  return element;
}
```

**cards.css를 사용하여 런타임 동작 추가**

```javascript
.card .radio-wrapper {
  min-width: 320px; /* or whatever width fits your design */
  max-width: 340px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  flex: 0 0 auto;
  scroll-snap-align: start;
  padding: 24px 16px;
  margin-bottom: 0;
  position: relative;
  transition: box-shadow 0.2s;
  display: flex;
  align-items: flex-start;
  gap: 12px;
}
```

이제 카드 구성 요소가 다음과 같이 표시됩니다.

![add card css and js](/help/edge/docs/forms/universal-editor/assets/add-card-css.png)

#### 2.2 구독 함수를 사용하여 동적 동작 추가

드롭다운을 변경하면 카드를 가져와서 열거형의 라디오 그룹에 설정됩니다. 그러나 현재 보기에서는 이 작업을 처리하지 않습니다. 따라서 아래와 같이 렌더링됩니다.

![subscribe function](/help/edge/docs/forms/universal-editor/assets/card-subscribe.png)

API가 호출되면 필드 모델을 설정하며 변경 내용을 수신하고 그에 따라 보기를 렌더링해야 합니다. 이 작업은 **구독 함수**&#x200B;를 사용하여 수행됩니다.

이전 단계의 보기 코드를 함수로 변환하고 `cards.js`의 구독 함수 내에서 다음과 같이 호출해 보겠습니다.

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });
  });

  return element;
}
```

**구독 함수를 사용하여 cards.js에서 이벤트 변경 내용 수신**

이제는 드롭다운을 변경하면 아래와 같이 카드가 채워집니다.

![subscribe function](/help/edge/docs/forms/universal-editor/assets/card-subscribe-final.png)

#### 2.3 보기 업데이트와 필드 모델 동기화

보기 변경 사항을 필드 모델에 동기화하려면 선택한 카드의 값을 설정해야 합니다. 따라서 아래와 같이 cards.js에서 다음 변경 이벤트 리스너를 추가합니다.

**cards.js에서 필드 모델 API 사용**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    // Attach index to input element for later reference
    radioWrapper.querySelector('input').dataset.index = index;

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });

    element.addEventListener('change', (e) => {
      e.stopPropagation();
      const value = fieldModel.enum?.[parseInt(e.target.dataset.index, 10)];
      fieldModel.value = value.name;
    });
  });

  return element;
}
```

이제 아래와 같이 사용자 정의 카드 구성 요소가 표시됩니다.

![카드 사용자 정의 구성 요소](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;3. 변경 사항 커밋 및 푸시

사용자 정의 구성 요소에 대한 JavaScript 및 CSS를 구현하고 로컬에서 확인했으면 변경 사항을 커밋하고 Git 저장소에 푸시합니다.

```bash
git add . && git commit -m "Add card custom component" && git push
```

간단한 몇 단계로 복잡한 사용자 정의 카드 선택 구성 요소를 만들었습니다.

+++ **사용자 정의 구성 요소를 만들기 위한 수동 또는 기존 메서드**

기존의 방법은 아래에 설명된 단계를 수동으로 수행하는 것입니다.

1. 확장할 **OOTB 구성 요소를 선택**&#x200B;합니다(예: 버튼, 드롭다운, 텍스트 입력 등). 이 경우 라디오 구성 요소를 확장합니다.

2. 구성 요소 이름(이 경우 cards)을 사용하여 `blocks/form/components`에 **폴더를 만듭니다**.

3. 같은 이름의 **JS 파일 추가**:
   - `blocks/form/components/cards/cards.js`

4. (선택 사항) 사용자 정의 스타일에 해당하는 **CSS 파일 추가**:
   - `blocks/form/components/cards/cards.css.`

5. **구성 요소 JS 파일**&#x200B;과 동일한 폴더(`blocks/form/components/cards/_cards.json`)에 **새 JSON 파일**(예: ` _cards.json`)을 정의합니다. 이 JSON은 기존 구성 요소와 해당 정의를 확장하고 `fd:viewType`를 구성 요소의 이름(이 경우 cards)으로 설정하게 됩니다.

   - 모든 필드 그룹(기본, 유효성 검사, 도움말 등)에 대해 사용자 정의 필드를 명시적으로 추가합니다.

6. **JS 및 CSS 논리 구현:**
   - 위에서 설명한 대로 기본 함수를 내보냅니다.
   - **요소** 매개 변수를 사용하여 기본 HTML 구조를 수정합니다.
   - 표준 필드 데이터에 필요한 경우 **fieldJson** 매개변수를 사용합니다.
   - 필요한 경우 **구독** 함수를 사용하여 필드 변경 내용 또는 사용자 지정 이벤트를 수신합니다.

     >[!NOTE]
     >
     >위에 설명된 대로 사용자 정의 구성 요소에 대해 JS 및 CSS 논리를 구현합니다.

7. 양식 빌더에서 구성 요소를 변형으로 등록하고 변형 속성을 설정하거나
   JSON의 `fd:viewType/:type`를 구성 요소 이름에 추가합니다. 예를 들어 `id="form`을 사용하여 `definitions[]`의 `fd:viewType` 값을 개체의 구성 요소 배열에 카드로 추가합니다.

   ```
       {
     "definitions": [
       {
         "title": "Cards",
         "id": "cards",
         "plugins": {
           "xwalk": {
             "page": {
               "resourceType": "core/fd/components/form/radiobutton/v1/radiobutton",
               "template": {
                 "jcr:title": "Cards",
                 "fieldType": "radio-button",
                 "fd:viewType": "cards",
                 "enabled": true,
                 "visible": true
               }
             }
           }
         }
       }
     ]
   }
   ```

8. **mappings.js 업데이트**: **OOTBComponentDecorators**(OOTB 스타일 구성 요소의 경우) 또는 **customComponents** 목록에 구성 요소 이름을 추가하여 시스템에서 인식하고 로드할 수 있도록 합니다.

   ```javascript
   let customComponents = ["cards"];
   const OOTBComponentDecorators = [];
   ```

9. **_form.json 업데이트**: 작성 UI에서 삭제할 수 있도록 구성 요소의 이름을 `filters.components` 배열에 추가합니다.

   ```javascript
   "filters": [
   {
       "id": "form",
       "components": [ "cards"]}
       ]
   ```

10. **_component-definition.json 업데이트**: `models/_component-definition.json`에서 개체가 있는 `id custom-components`를 포함한 그룹 내의 배열을 다음 방식으로 업데이트합니다.

   ```javascript
   {
   "...":"../blocks/form/components/cards/_cards.json#/definitions"
   }
   ```

   이는 나머지 구성 요소와 함께 빌드될 새 카드 구성 요소에 대한 참조를 제공하는 단계입니다

11. **빌드 실행:json 스크립트**: `npm run build:json`을 실행하여 모든 구성 요소 JSON 정의를 컴파일하고 서버에서 제공할 단일 파일로 병합합니다. 이렇게 하면 새 구성 요소의 스키마가 병합된 출력에 포함됩니다.

12. 변경 사항을 커밋하고 Git 저장소에 푸시합니다.

이제 사용자 정의 구성 요소를 양식에 추가할 수 있습니다.

+++

## 복합 구성 요소 만들기

복합 구성 요소는 여러 구성 요소를 결합하여 만들어집니다.
예를 들어 약관 복합 구성 요소는 다음을 포함하는 상위 패널로 구성됩니다.

- 용어를 표시하기 위한 일반 텍스트 필드

- 사용자의 계약을 캡처하기 위한 확인란

이 컴포지션 구조는 각 구성 요소의 JSON 파일 내에 템플릿으로 정의됩니다. 다음 예에서는 약관 구성 요소에 대한 템플릿을 정의하는 방법을 보여줍니다.

```javascript
{
  "definitions": [
    {
      "title": "Terms and conditions",
      "id": "tnc",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/termsandconditions/v1/termsandconditions",
            "template": {
              "jcr:title": "Terms and conditions",
              "fieldType": "panel",
              "fd:viewType": "tnc",
              "text": {
                "value": "Text related to the terms and conditions come here.",
                "sling:resourceType": "core/fd/components/form/text/v1/text",
                "fieldType": "plain-text",
                "textIsRich": true
              },
              "approvalcheckbox": {
                "name": "approvalcheckbox",
                "jcr:title": "I agree to the terms & conditions.",
                "sling:resourceType": "core/fd/components/form/checkbox/v1/checkbox",
                "fieldType": "checkbox",
                "required": true,
                "type": "string",
                "enum": [
                  "true"
                ]
              }
            }
          }
        }
      }
    }
  ],
  ...
}
```

## 모범 사례

사용자 정의 구성 요소를 만들기 전에 다음 사항을 염두에 두십시오.

- **구성 요소 논리에 집중**: 사용자 정의 동작에 필요한 항목만 추가/재정의합니다.

- **기본 구조 활용**: OOTB HTML을 시작점으로 사용합니다.

- **작성 가능한 속성 사용:** JSON 스키마를 통해 구성 가능한 옵션을 노출시킵니다.

- **CSS 네임스페이스 지정**: 고유한 클래스 이름을 사용하여 스타일 충돌을 피합니다.

## 참조

- [form-field-types](/help/edge/docs/forms/eds-form-field-properties.md): 모든 필드 유형에 대한 기본 HTML 구조 및 속성입니다.

- **blocks/form/models/form-components**: OOTB 및 사용자 정의 구성 요소 속성 정의입니다.

- **blocks/form/components**: 사용자 정의 구성 요소를 배치합니다. 예: `blocks/form/components/countdown-timer/_countdown-timer.json`은 기본 구성 요소를 확장하고 새로운 속성을 추가하는 방법을 보여줍니다.
