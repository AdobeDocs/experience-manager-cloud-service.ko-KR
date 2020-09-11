---
title: AEM에서 Angular를 사용하여 SPA 시작
description: 이 문서에서는 샘플 SPA 애플리케이션과 함께 설치되는 방법을 설명하며 Angular 프레임워크를 사용하여 신속하게 자체 SPA를 익힐 수 있도록 해 줍니다.
translation-type: tm+mt
source-git-commit: 8bdb7bbe80a4e22bb2b750c0719c6db745133392
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---


# Getting Started with SPAs in AEM Using Angular {#getting-started-with-spas-in-aem-using-angular}

단일 페이지 애플리케이션(SPA)을 통해 웹 사이트 사용자에게 매력적인 경험을 제공할 수 있습니다. 개발자는 SPA 프레임워크를 사용하여 사이트를 구축하고, 작성자는 SPA 프레임워크를 사용하여 구축된 사이트에서 AEM 내에서 컨텐츠를 완벽하게 편집하고자 합니다.

SPA 저작 기능은 AEM 내의 SPA를 지원하는 포괄적인 솔루션을 제공합니다. 이 문서는 Angular 프레임워크에 간소화된 SPA 애플리케이션을 제시하며, 이를 어떻게 구성하는지에 대해 설명하며, SPA를 신속하게 설치하여 바로 사용할 수 있습니다.

>[!NOTE]
>
>이 문서는 Angular 프레임워크를 기반으로 합니다. Responsive 프레임워크에 해당하는 문서는 AEM에서 SPA [시작하기 - 반응을 참조하십시오](getting-started-react.md).

## 소개 {#introduction}

이 문서는 간단한 SPA의 기본적인 기능과 필요한 최소 기능을 요약해 놓은 것입니다.

AEM에서 SPA가 작동하는 방법에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [SPA 소개 및 연습](introduction.md)
* [SPA 편집기 개요](editor-overview.md)
* [SPA 블루프린트](blueprint.md)

>[!NOTE]
>
>SPA 내에서 컨텐츠를 저작할 수 있으려면 컨텐츠가 AEM에 저장되어 컨텐츠 모델에 노출되어 있어야 합니다.
>
>AEM 외부에서 개발된 SPA는 컨텐츠 모델 계약을 준수하지 않으면 저작권을 얻을 수 없습니다.

본 문서는 간소화된 SPA의 구조를 자세히 설명하여 SPA에 이러한 이해를 적용할 수 있는 방법을 설명합니다.

## 종속성, 구성 및 작성 {#dependencies-configuration-and-building}

예상 각도 종속성 외에도 샘플 SPA는 추가 라이브러리를 활용하여 SPA를 보다 효율적으로 만들 수 있습니다.

### 종속성 {#dependencies}

이 `package.json` 파일은 전체 SPA 패키지의 요구 사항을 정의합니다. 필요한 최소 AEM 종속성은 여기에 나와 있습니다.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

빌드 프로세스 `aem-clientlib-generator` 의 일부로 클라이언트 라이브러리를 자동으로 만드는 데 사용됩니다.

`"aem-clientlib-generator": "^1.4.1",`

자세한 내용은 GitHub [에서 확인할 수 있습니다](https://github.com/wcm-io-frontend/aem-clientlib-generator).

파일 `aem-clientlib-generator` 에 다음과 같이 `clientlib.config.js` 구성됩니다.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Building {#building}

실제로 앱을 빌드하면 자동 클라이언트 라이브러리 [를](https://webpack.js.org/) 만들기 위한 aem-clientlib-generator 외에도 전달을 위한 Webpack이 활용됩니다. 따라서 빌드 명령은 다음과 같습니다.

`"build": "ng build --build-optimizer=false && clientlib",`

패키지를 빌드하면 AEM 인스턴스에 업로드할 수 있습니다.

### AEM 프로젝트 전형 {#aem-project-archetype}

모든 AEM 프로젝트는 [AEM 프로젝트 원형](https://docs.adobe.com/content/help/ko-KR/experience-manager-core-components/using/developing/archetype/overview.html)(React or Angular)을 사용하여 SPA 프로젝트를 지원하고 SPA SDK를 활용하는 프로젝트 전형(Pretype)을 활용해야 합니다.

## 애플리케이션 구조 {#application-structure}

이전에 설명한 바와 같이 종속성 및 앱 빌드를 포함하면 AEM 인스턴스에 업로드할 수 있는 작업 중인 SPA 패키지가 남아 있습니다.

이 문서의 다음 섹션에서는 AEM의 SPA 구성 방법, 애플리케이션을 구동하는 중요한 파일 및 이러한 SPA의 작동 방식을 살펴볼 수 있습니다.

간소화된 이미지 구성 요소를 예로 사용하지만 애플리케이션의 모든 구성 요소는 동일한 개념을 기반으로 합니다.

### app.module.ts {#app-module-ts}

SPA의 엔트리 포인트는 중요한 컨텐츠에 초점을 맞추기 위해 여기에 간단히 표시된 `app.module.ts` 파일입니다.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

이 `app.module.ts` `AppComponent` 파일은 앱의 시작점이며 초기 프로젝트 구성을 포함하며 앱을 부트스트래핑하는 데 사용됩니다.

#### 정적 인스턴스화 {#static-instantiation}

구성 요소 템플릿을 사용하여 구성 요소가 정적으로 인스턴스화될 경우 이 값은 모델에서 구성 요소의 속성으로 전달되어야 합니다. 모델의 값은 나중에 구성 요소 속성으로 사용할 수 있도록 속성으로 전달됩니다.

### app.component.ts {#app-component-ts}

부트스트래핑 `app.module.ts` `AppComponent`을 수행하면, 여기에서 간단한 버전으로 표시되는 앱을 초기화하여 중요한 콘텐츠에 주력할 수 있습니다.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

페이지를 처리하면 `app.component.ts` 여기에 `main-content.component.ts` 나열된 간소화된 버전으로 호출됩니다.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

페이지 모델의 JSON 표현을 `MainComponent` 인제스트하고 페이지의 각 요소를 둘러싸거나 장식하기 위해 컨텐츠를 처리합니다. 자세한 내용은 `Page` SPA Blueprint [](blueprint.md)문서를 참조하십시오.

### image.component.ts {#image-component-ts}

그 `Page` 는 구성 요소로 구성되어 있다. 인제스트된 JSON을 사용하면 여기에 표시된 것처럼 이러한 구성 요소 `Page` `image.component.ts` 를 처리할 수 있습니다.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

AEM의 SPA는 SPA 구성 요소를 AEM 구성 요소에 매핑하고 컨텐츠가 수정될 때(또는 그 반대로) 구성 요소를 업데이트하는 것을 목표로 합니다. 이 통신 모델에 대한 요약 내용은 [SPA Editor](editor-overview.md) Overview 문서를 참조하십시오.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

이 `MapTo` 방법은 SPA 구성 요소를 AEM 구성 요소에 매핑합니다. 단일 문자열 또는 문자열 배열을 사용할 수 있습니다.

`ImageEditConfig` 는 편집기가 자리 표시자를 생성하는 데 필요한 메타데이터를 제공하여 구성 요소의 작성 기능을 활성화하는 데 도움이 되는 구성 개체입니다.

콘텐트가 없으면 빈 콘텐트를 나타내는 자리 표시자로 레이블이 제공됩니다.

#### 동적으로 전달된 속성 {#dynamically-passed-properties}

모델에서 나오는 데이터는 구성 요소의 속성으로 동적으로 전달됩니다.

### image.component.html {#image-component-html}

마지막으로 이미지를 렌더링할 수 있습니다 `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## SPA 구성 요소 간 정보 공유 {#sharing-information-between-spa-components}

단일 페이지 애플리케이션 내의 구성 요소가 정보를 공유하려면 정기적으로 필요합니다. 다음과 같은 몇 가지 권장 방법으로 복잡도가 높아집니다.

* **옵션 1:** util 클래스를 순수한 객체 지향 솔루션으로 사용하면 논리 및 브로드캐스트를 필요한 구성 요소로 중앙에서 제어할 수 있습니다.
* **옵션 2:** NgRx와 같은 상태 라이브러리를 사용하여 구성 요소 상태를 공유합니다.
* **옵션 3:** 컨테이너 구성 요소를 사용자 지정하고 확장하여 객체 계층 구조를 활용할 수 있습니다.

## 다음 단계 {#next-steps}

* [React를 사용하여 AEM에서 SPA를 시작한다는 것은 React를 사용하여 AEM에서 SPA Editor와 연동되도록 기본 SPA가 어떻게 구축되었는지를 보여줍니다.](getting-started-react.md)
* [SPA Editor 개요](editor-overview.md) 는 AEM과 SPA 간의 커뮤니케이션 모델에 대해 더 자세히 설명합니다.
* [WKND SPA Project](wknd-tutorial.md) 는 AEM에서 간단한 SPA 프로젝트를 구현하는 단계별 자습서입니다.
* [SPA에 대한 동적 모델-구성 요소 매핑](model-to-component-mapping.md) 기능은 구성 요소 간 동적 모델과 AEM의 SPA 내에서 작동하는 방식을 설명합니다.
* [SPA Blueprint](blueprint.md) 는 AEM에서 Reresponsive 또는 Angular 이외의 프레임워크를 위해 SPA를 구현하려는 경우 AEM용 SPA SDK의 작동 방식을 자세히 살펴볼 수 있습니다.
