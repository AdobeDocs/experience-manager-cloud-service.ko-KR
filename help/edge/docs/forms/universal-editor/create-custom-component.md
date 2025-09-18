---
title: EDS 양식에 대한 사용자 정의 구성 요소 만들기
description: EDS 양식에 대한 사용자 정의 구성 요소 만들기
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9664495d17ad8a8101c886408bee1584b3d48f1e
workflow-type: tm+mt
source-wordcount: '2103'
ht-degree: 4%

---


# 적응형 양식 블록에서 사용자 정의 양식 구성 요소 생성

Edge Delivery Services 양식은 사용자 정의 기능을 제공하여 프론트엔드 개발자가 맞춤형 양식 구성 요소를 구축할 수 있도록 합니다. 이러한 사용자 정의 구성 요소는 WYSIWYG 저작 환경에 완벽하게 통합되어 양식 작성자가 양식 편집기 내에서 쉽게 추가, 구성 및 관리할 수 있습니다. 사용자 정의 구성 요소를 통해 작성자는 기능을 향상시키면서 원활하고 직관적인 작성 과정을 보장할 수 있습니다.

이 문서에서는 사용자 경험을 개선하고 양식의 시각적 매력을 높이기 위해 기본 HTML 양식 구성 요소의 스타일을 지정하여 사용자 정의 구성 요소를 만드는 절차에 대해 설명합니다.

## 아키텍처 개요

Forms 블록의 사용자 지정 구성 요소는 **MVC(Model-View-Controller)** 아키텍처 패턴을 따릅니다.

### 모델

- 각 `field/component`에 대해 JSON 스키마로 정의됩니다.

- 작성 가능한 속성은 해당 JSON 파일에 지정됩니다(블록/양식/모델/양식- 구성 요소 참조).

- 이러한 속성은 양식 빌더에서 작성자가 사용할 수 있으며 fd(필드 정의)의 일부로 구성 요소에 전달됩니다.

### 보기

- 각 필드 유형에 대한 HTML 구조는 양식 필드 유형에 설명되어 있습니다.

- 확장 또는 수정할 수 있는 구성 요소의 기본 구조입니다.

- 각 OOTB 구성 요소에 대한 기본 HTML 구조는 양식 필드 유형으로 문서화되어 있습니다.

### 컨트롤러/구성 요소 논리

- JavaScript에서 OOTB(기본 제공) 또는 사용자 지정 구성 요소로 구현되었습니다.  - 사용자 지정 구성 요소의 `blocks/form/components`에 있습니다.

## OOTB 구성 요소

**OOTB(기본 제공)** 구성 요소는 사용자 지정 개발의 기반을 제공합니다.

- OOTB 구성 요소가 `blocks/form/models/form-components`에 있습니다.

- 각 OOTB 구성 요소에는 작성 가능한 속성(예: ` _text-input.json`,`_drop-down.json`)을 정의하는 JSON 파일이 있습니다.

- 이러한 속성은 양식 빌더에서 작성자가 사용할 수 있으며 fd(필드 정의)의 일부로 구성 요소에 전달됩니다.

- 각 OOTB 구성 요소에 대한 기본 HTML 구조는 양식 필드 유형으로 문서화되어 있습니다.

기존 OOTB 구성 요소를 확장하면 기본 구조, 동작 및 속성을 재사용하는 동시에 요구 사항에 맞게 사용자 지정할 수 있습니다.

- 사용자 지정 구성 요소는 사전 정의된 OOTB 구성 요소 집합에서 확장되어야 합니다.

- 시스템은 필드의 JSON에 있는 `viewType` 속성을 기반으로 확장할 OOTB 구성 요소를 식별합니다.

- 시스템은 허용된 사용자 지정 구성 요소 변형의 레지스트리를 유지 관리합니다. 이 레지스트리에 나열된 변형만 사용할 수 있습니다(예: `customComponents[]`의 `mappings.js`).

- 양식을 렌더링할 때 시스템에서 variant 속성 또는 `:type/fd:viewType`을(를) 확인하고 등록된 사용자 지정 구성 요소와 일치하는 경우 `blocks/form/components` 폴더에서 해당 JS 및 CSS 파일을 로드합니다.

- 그런 다음 사용자 지정 구성 요소가 OOTB 구성 요소의 기본 HTML 구조에 적용되어 그 비헤이비어 및 모양을 강화하거나 무시할 수 있습니다.

## 사용자 지정 구성 요소의 구조

사용자 지정 구성 요소를 만들려면 **Scaffold CLI**&#x200B;를 사용하여 구성 요소에 필요한 파일 및 폴더를 설정한 다음 사용자 지정 구성 요소에 대한 코드를 추가할 수 있습니다.

- 사용자 지정 구성 요소가 `blocks/form/components` 폴더에 있습니다.

- 각 사용자 지정 구성 요소는 구성 요소의 이름을 딴 자체 폴더(예: 카드)에 배치해야 합니다. 폴더 내부에는 다음 파일이 있어야 합니다.

   - **_cards.json** - OOTB 구성 요소의 구성 요소 정의를 확장하고, 작성 가능한 속성(모델[])과 로드 시 콘텐츠 구조(정의[])를 정의하는 JSON 파일입니다.
   - **cards.js** - 기본 논리를 포함하는 JavaScript 파일입니다.
   - **cards.css** - 스타일에 대해 선택 사항입니다.

- 폴더 이름과 JS/CSS 파일이 일치해야 합니다.

### 사용자 지정 구성 요소에서 필드 재사용 및 확장

사용자 지정 구성 요소의 JSON에 있는 필드(모든 필드 그룹, 기본, 유효성 검사, 도움말 등)를 정의할 때 유지 관리 및 일관성을 위해 다음 모범 사례를 따르십시오.

- 기존 공유 컨테이너 또는 필드 정의(예: `../form-common/_basic-input-placeholder-fields.json#/fields`, `../form-common/_basic- validation-fields.json#/fields`)를 참조하여 표준/공유 필드를 재사용합니다. 이렇게 하면 표준 옵션을 복제하지 않고 모두 상속할 수 있습니다.

- 컨테이너에 새 필드나 사용자 정의 필드만 명시적으로 추가합니다. 이렇게 하면 스키마가 건조해지고 초점이 맞춰집니다.

- 참조를 통해 이미 포함된 필드를 제거하거나 복제하지 마십시오. 구성 요소 로직에 고유한 필드만 정의합니다.

- 일관성 및 유지 관리를 위해 필요한 대로 도움말 컨테이너 및 기타 공유 콘텐츠(예: `../form-common/_help-container.json`)를 참조합니다.

>[!TIP]
>
> - 이 패턴을 사용하면 향후 논리를 쉽게 업데이트하거나 확장할 수 있으며 사용자 지정 구성 요소가 나머지 양식 시스템과 일관성을 유지하도록 할 수 있습니다.
> - 새 공유 컨테이너를 추가하기 전에 항상 기존 공유 컨테이너 또는 필드 정의를 확인하십시오.

### 사용자 정의 구성 요소에 대한 새 속성 정의

- 작성자로부터 사용자 지정 구성 요소에 대한 새 속성을 캡처해야 하는 경우 구성 요소의 JSON에서 구성 요소의 `fields[]` 배열에 있는 필드를 정의하여 캡처할 수 있습니다.

- 사용자 지정 구성 요소는 JSON 파일에서 :type(예: `fd:viewType`)로 설정할 수 있는 `fd:viewType: cards` 속성을 사용하여 식별됩니다. 이렇게 하면 시스템에서 올바른 사용자 지정 구성 요소를 인식하고 로드할 수 있으므로 사용자 지정 구성 요소에서는 필수입니다

- JSON 정의에 추가된 모든 새 속성은 필드 정의에서 속성으로 사용할 수 있습니다. 구성 요소의 JS 논리의 `<propertyName>`

## 사용자 지정 구성 요소 JavaScript API

맞춤형 구성 요소 JavaScript API는 맞춤형 양식 구성 요소의 비헤이비어, 모양 및 반응성을 제어하는 방법을 정의합니다.

### 장식 기능

**decorate** 함수는 사용자 지정 구성 요소의 진입점입니다. 구성 요소를 초기화하고, 해당 JSON 정의와 연결하며, HTML 구조 및 동작을 조작할 수 있도록 합니다.

>[!NOTE]
>
> 사용자 지정 구성 요소의 JavaScript 파일은 기본 기능을 장식용으로 내보내야 합니다.

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

다음과 같은 작업을 수행할 수 있습니다.

- **요소를 수정합니다**: 이벤트 리스너를 추가하거나 특성을 업데이트하거나 추가 태그를 삽입합니다.

- **JSON 속성에 액세스**: `fd.properties.<propertyName>`을(를) 사용하여 JSON 스키마에 정의된 값을 읽고 구성 요소 논리 내에 적용합니다.

## 기능 구독

**subscribe** 함수를 사용하면 구성 요소가 필드 값 또는 사용자 지정 이벤트의 변경 내용에 반응할 수 있습니다. 이렇게 하면 구성 요소가 양식의 데이터 모델과 동기화 상태를 유지하고 해당 UI를 동적으로 업데이트할 수 있습니다.

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

다음과 같은 작업을 수행할 수 있습니다.

- **콜백 등록**: **subscribe(element, formId, callback)를 호출합니다** 필드 데이터가 변경될 때마다 실행할 콜백을 등록합니다.콜백 매개 변수 두 개를 사용하십시오.
   - **element**: 필드를 나타내는 HTML 요소입니다.
   - **fieldModel**: 필드의 상태 및 이벤트 API를 나타내는 개체입니다.

- **변경 내용 또는 이벤트를 수신**: 값이 변경되거나 사용자 지정 이벤트가 트리거될 때마다 논리를 실행하려면 `fieldModel.subscribe((event) => { ... }, 'eventName')`을(를) 사용합니다. 이벤트 개체에는 변경된 내용에 대한 세부 사항이 포함되어 있습니다.

## 사용자 지정 구성 요소 만들기

이 섹션에서는 OOTB 라디오 버튼 구성 요소를 확장하여 **카드 사용자 지정 구성 요소**&#x200B;를 만드는 과정을 알아봅니다.

![카드 사용자 지정 구성 요소](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;1. 코드 설정

#### 1.1 파일 및 폴더

첫 번째 단계는 사용자 지정 구성 요소에 필요한 파일을 설정하여 저장소의 코드로 연결하는 것입니다. 이 프로세스는 **AEM Forms Scaffold CLI**&#x200B;에서 자동으로 수행되므로 필요한 파일을 더 빨리 스캐폴드하고 전송하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3474752)

1. 터미널을 열고 양식 프로젝트의 루트로 이동합니다.
2. 다음 명령을 실행합니다.

```bash
npm install
npm run create:custom-component
```

![스캐폴딩 CLI](/help/edge/docs/forms/universal-editor/assets/scaffolder-cli.png)

이는 다음과 같습니다.

- **새 구성 요소의 이름을**&#x200B;하라는 메시지가 표시됩니다. 예를 들어, 이 경우 카드를 사용하십시오.
- **기본 구성 요소 선택**&#x200B;을 요청(라디오 그룹 선택)

이렇게 하면 다음을 포함하여 필요한 모든 폴더와 파일이 만들어집니다.

```
blocks/form/
└── components/
  └── cards/
    ├── cards.js
    └── cards.css
    └── _cards.json
```

그리고 CLI 출력에 표시된 대로 저장소의 나머지 코드와 함께 이 코드를 연결합니다.
다음 기능을 자동으로 수행합니다.

- 적응형 양식 블록 내에 추가할 수 있도록 필터에 카드를 추가합니다.
- 새 카드 구성 요소를 포함하도록 `mappings.js`의 허용 목록을 업데이트합니다.
- 유니버설 편집기의 **사용자 지정 구성 요소** 목록 아래에 카드 구성 요소의 정의를 등록합니다.

>[!NOTE]
>
> 수동(이전) 방법을 사용하여 사용자 지정 구성 요소를 만들 수도 있습니다. 자세한 내용은 사용자 지정 구성 요소 만들기 섹션을 보려면 [수동 또는 레거시 메서드](#manual-or-legacy-method-to-create-custom-component)를 참조하십시오.

#### 1.2 유니버설 편집기에서 구성 요소 사용

1. **유니버설 편집기 새로 고침**: 유니버설 편집기에서 양식을 열고 페이지를 새로 고쳐 저장소에서 최신 코드를 로드합니다.

2. **사용자 지정 구성 요소 추가**

   1. 양식 캔버스에서 **추가(+)** 단추를 클릭합니다.
   2. 사용자 지정 구성 요소 섹션으로 스크롤합니다.
   3. 새로 만든 **카드 구성 요소**&#x200B;를 선택하여 양식에 삽입합니다.

      ![사용자 지정 구성 요소 선택](/help/edge/docs/forms/universal-editor/assets/select-custom-component.png)

`cards.js` 내에 코드가 없으므로 사용자 지정 구성 요소가 라디오 그룹으로 렌더링됩니다.

#### 1.3 로컬에서 미리 보기 및 테스트

이제 양식에 사용자 지정 구성 요소가 포함되어 있으므로 양식을 프록시하고 로컬에서 변경하고 변경 사항을 볼 수 있습니다.

1. 터미널로 이동하여 `aem up`을(를) 실행하십시오.

2. `http://localhost:3000/{path-to-your-form}`에서 시작된 프록시 서버를 엽니다(경로 예: `/content/forms/af/custom-component-form`).


### &#x200B;2. 사용자 지정 구성 요소에 대한 사용자 지정 동작 구현

#### 2.1 사용자 지정 구성 요소 스타일링

스타일을 지정하고 각 라디오에 대한 이미지를 추가하려면 구성 요소에 클래스 **card**&#x200B;을(를) 추가해 보겠습니다. 이 경우 아래 코드를 사용하십시오.

**card.js를 사용하여 구성 요소 스타일링**

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

![카드 css 및 js 추가](/help/edge/docs/forms/universal-editor/assets/add-card-css.png)

#### 2.2 Subscribe 함수를 사용하여 동적 동작 추가

드롭다운을 변경하면 카드를 가져와서 라디오 그룹의 열거형에 설정합니다. 그러나 현재 보기에서는 이 작업을 처리하지 않습니다. 따라서 아래와 같이 렌더링됩니다.

![함수 구독](/help/edge/docs/forms/universal-editor/assets/card-subscribe.png)

API가 호출되면 필드 모델을 설정하며 변경 내용을 수신하고 그에 따라 보기를 렌더링해야 합니다. 이 작업은 **구독 함수**&#x200B;를 사용하여 수행됩니다.

이전 단계의 보기 코드를 함수로 변환하고 `cards.js`의 Subscribe 함수 내에서 다음과 같이 호출하겠습니다.

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

**Subscribe 함수를 사용하여 cards.js에서 이벤트 변경 내용을 수신**

이제 드롭다운을 변경하면 아래와 같이 카드가 채워집니다.

![함수 구독](/help/edge/docs/forms/universal-editor/assets/card-subscribe-final.png)

#### 2.3 필드 모델과 보기 업데이트 동기화

보기 변경 사항을 필드 모델에 동기화하려면 선택한 카드의 값을 설정해야 합니다. 따라서 아래와 같이 cards.js에 다음 변경 이벤트 리스너를 추가합니다.

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

이제 아래와 같이 사용자 지정 카드 구성 요소가 표시됩니다.

![카드 사용자 지정 구성 요소](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;3. 변경 사항 커밋 및 푸시

사용자 지정 구성 요소에 대한 JavaScript 및 CSS를 구현하고 로컬에서 확인했으면 변경 사항을 커밋하고 Git 저장소에 푸시합니다.

```bash
git add . && git commit -m "Add card custom component" && git push
```

몇 가지 간단한 단계로 복잡한 사용자 정의 카드 선택 구성 요소를 만들었습니다.

+++ **사용자 지정 구성 요소를 만드는 수동 또는 기존 메서드**

이렇게 하는 이전 방법은 아래에 설명된 단계를 수동으로 수행하는 것입니다.

1. **확장할 OOTB 구성 요소를 선택하십시오**(예: 단추, 드롭다운, 텍스트 입력 등). 이 경우 라디오 구성 요소를 확장합니다.

2. 구성 요소 이름(이 경우 카드)을 사용하여 **폴더를**&#x200B;에 만듭니다`blocks/form/components`.

3. 같은 이름의 **JS 파일 추가**:
   - `blocks/form/components/cards/cards.js`

4. (선택 사항) 사용자 지정 스타일에 대해 **CSS 파일 추가**:
   - `blocks/form/components/cards/cards.css.`

5. **새 JSON 파일 정의**(예: ` _cards.json`)이 **구성 요소 JS 파일**(`blocks/form/components/cards/_cards.json`)과 동일한 폴더에 있습니다. 이 JSON은 기존 구성 요소를 확장해야 하며 해당 정의에 `fd:viewType`을(를) 구성 요소의 이름(이 경우 카드)으로 설정해야 합니다.

   - 모든 필드 그룹(기본, 유효성 검사, 도움말 등)에 대해 사용자 지정 필드를 명시적으로 추가합니다.

6. **JS 및 CSS 논리 구현:**
   - 위에서 설명한 대로 기본 함수를 내보냅니다.
   - **element** 매개 변수를 사용하여 기본 HTML 구조를 수정합니다.
   - 표준 필드 데이터에 필요한 경우 **fieldJson** 매개 변수를 사용하십시오.
   - 필요한 경우 **subscribe** 함수를 사용하여 필드 변경 내용이나 사용자 지정 이벤트를 수신합니다.

     >[!NOTE]
     >
     >위에 설명된 대로 사용자 지정 구성 요소에 대한 JS 및 CSS 논리를 구현합니다.

7. 양식 빌더에서 구성 요소를 변형으로 등록하고 변형 속성을 설정하거나
   JSON의 `fd:viewType/:type`을(를) 구성 요소 이름에 추가합니다. 예를 들어 `fd:viewType`을(를) 사용하여 `definitions[]`의 `id="form` 값을 카드로 개체의 구성 요소 배열에 추가합니다.

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

8. **mappings.js 업데이트**: **OOTBComponentDecorators**(OOTB 스타일 구성 요소) 또는 **customComponents** 목록에 구성 요소 이름을 추가하여 시스템에서 인식하고 로드하십시오.

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

10. **_component-definition.json 업데이트**: `models/_component-definition.json`에서 다음 방식으로 개체가 있는 `id custom-components` 그룹 내의 배열을 업데이트합니다.

    ```javascript
    {
    "...":"../blocks/form/components/cards/_cards.json#/definitions"
    }
    ```

    나머지 구성 요소와 함께 빌드될 새 카드 구성 요소에 대한 참조를 제공합니다

11. **빌드:json 스크립트를 실행**: `npm run build:json`을(를) 실행하여 모든 구성 요소 JSON 정의를 컴파일하고 서버에서 제공할 단일 파일로 병합합니다. 이렇게 하면 새 구성 요소의 스키마가 병합된 출력에 포함됩니다.

12. 변경 사항을 커밋하고 Git 저장소에 푸시합니다.

이제 사용자 지정 구성 요소를 양식에 추가할 수 있습니다.

+++

## 복합 구성 요소 만들기

복합 구성 요소는 여러 구성 요소를 결합하여 만들어집니다.
예를 들어 약관 복합 구성 요소는 다음을 포함하는 상위 패널로 구성됩니다.

- 용어를 표시하기 위한 일반 텍스트 필드

- 사용자의 계약을 캡처하기 위한 확인란

이 구성 구조는 각 구성 요소의 JSON 파일 내에 있는 템플릿으로 정의됩니다. 다음 예에서는 약관 구성 요소에 대한 템플릿을 정의하는 방법을 보여 줍니다.

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

사용자 지정 구성 요소를 만들기 전에 다음 사항을 염두에 두십시오.

- **구성 요소 논리에 초점을 맞추십시오**: 사용자 지정 동작에 필요한 내용만 추가/재정의합니다.

- **기본 구조 활용**: OOTB HTML을 시작점으로 사용

- **작성 가능한 속성 사용:** JSON 스키마를 통해 구성 가능한 옵션을 표시합니다.

- **CSS 네임스페이스**: 고유한 클래스 이름을 사용하여 스타일 충돌을 피하십시오

## 참조

- [양식 필드 형식](/help/edge/docs/forms/eds-form-field-properties.md): 모든 필드 형식에 대한 기본 HTML 구조 및 속성입니다.

- **블록/양식/모델/양식-구성 요소**: OOTB 및 사용자 지정 구성 요소 속성 정의입니다.

- **블록/양식/구성 요소**: 사용자 지정 구성 요소를 배치합니다. 예: `blocks/form/components/countdown-timer/_countdown-timer.json`은(는) 기본 구성 요소를 확장하고 새 속성을 추가하는 방법을 보여 줍니다.
