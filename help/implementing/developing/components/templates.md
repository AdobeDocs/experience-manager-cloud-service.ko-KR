---
title: 페이지 템플릿
description: 페이지 템플릿 은 새 페이지의 기반으로 사용할 페이지를 만들 때 사용됩니다
exl-id: ea42fce9-9af2-4349-a4e4-547e6e8da05c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '3296'
ht-degree: 7%

---

# 페이지 템플릿 {#page-templates}

페이지를 만들 때는 템플릿을 선택해야 합니다. 페이지 템플릿은 새 페이지의 기초로 사용됩니다. 템플릿은 결과 페이지의 구조, 초기 컨텐츠 및 사용할 수 있는 구성 요소(디자인 속성)를 정의합니다. 다음과 같은 몇 가지 이점이 있습니다.

* 페이지 템플릿을 사용하면 전문 작성자가 [템플릿을 만들고 편집할 수 있습니다](/help/sites-cloud/authoring/features/templates.md).
   * 이러한 전문 작성자는 **템플릿 작성자**&#x200B;라고 합니다.
   * 템플릿 작성자는 `template-authors` 그룹의 구성원이어야 합니다.
* 페이지 템플릿 은 페이지 템플릿에서 만든 모든 페이지에 대한 동적 연결을 유지합니다. 이렇게 하면 템플릿 변경 사항이 페이지 자체에 반영됩니다.
* 페이지 템플릿 을 사용하면 페이지 구성 요소를 보다 일반적으로 만들 수 있으므로 사용자 지정 없이 핵심 페이지 구성 요소를 사용할 수 있습니다.

페이지 템플릿을 사용하면 페이지를 만드는 조각은 구성 요소 내에서 구분됩니다. UI에서 구성 요소의 필요한 조합을 구성할 수 있으므로 각 페이지 변형에 대해 새 페이지 구성 요소를 개발할 필요가 없습니다.

이 문서는

* 페이지 템플릿 만들기에 대한 개요를 제공합니다
* 편집 가능한 템플릿을 만드는 데 필요한 관리자/개발자 작업에 대해 설명합니다
* 편집 가능한 템플릿의 기술적 기본 사항을 설명합니다
* AEM이 템플릿 가용성을 평가하는 방법에 대해 설명합니다.

>[!NOTE]
>
>이 문서에서는 사용자가 이미 템플릿 만들기 및 편집에 익숙하다고 가정합니다. 템플릿 작성자에게 노출된 대로 편집 가능한 템플릿의 기능을 자세히 설명하는 작성 문서 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md)를 참조하십시오.

>[!TIP]
>
>[WKND ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 자습서에서는 예를 구현하여 페이지 템플릿을 사용하는 방법에 대해 깊이 있게 설명하며, 새 프로젝트에서 템플릿을 설정하는 방법을 이해하는 데 유용합니다

## 새 템플릿 만들기 {#creating-a-new-template}

페이지 템플릿 만들기는 주로 템플릿 작성자가 [템플릿 콘솔 및 템플릿 편집기](/help/sites-cloud/authoring/features/templates.md)로 수행합니다. 이 섹션에서는 이 프로세스에 대한 개요를 설명하고 기술 수준에서 발생하는 사항에 대한 설명을 제공합니다.

편집 가능 템플릿을 새로 만들 때 다음을 수행합니다.

1. 템플릿](#template-folders)에 대한 [폴더를 만듭니다. 이것은 필수가 아니지만, 권장하는 우수 사례입니다.
1. [템플릿 유형](#template-type)을 선택합니다. [템플릿 정의](#template-definitions)를 만들기 위해 복사됩니다.

   >[!NOTE]
   >
   >다양한 템플릿 유형이 기본적으로 제공됩니다. 필요한 경우 [고유한 사이트별 템플릿 유형](#creating-template-types)을 만들 수도 있습니다.

1. 새 템플릿의 구조, 컨텐츠 정책, 초기 컨텐츠 및 레이아웃을 구성합니다.

   **구조**

   * 구조를 사용하면 템플릿에 대한 구성 요소 및 컨텐츠를 정의할 수 있습니다.
   * 템플릿 구조에 정의된 구성 요소는 결과 페이지 안에서 이동하거나 결과 페이지에서 삭제할 수 없습니다.
   * 페이지 작성자가 구성 요소를 추가 및 제거할 수 있도록 하려면 템플릿에 단락 시스템을 추가하십시오.
   * 초기 컨텐츠를 정의할 수 있도록 하려면 구성 요소 잠금을 해제했다가 다시 잠글 수 있습니다.

   템플릿 작성자가 구조를 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author)를 참조하십시오.

   구조에 대한 자세한 내용은 이 문서에서 [구조](#structure)를 참조하십시오.

   **정책**

   * 컨텐츠 정책은 구성 요소의 디자인 속성을 정의합니다.

      * 예: 사용 가능한 구성 요소 또는 최소/최대 크기.
   * 이러한 속성은 템플릿(및 템플릿으로 만든 페이지)에 적용될 수 있습니다.

   템플릿 작성자가 정책을 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author)를 참조하십시오.

   정책에 대한 기술적인 세부 사항은 이 문서에서 [컨텐츠 정책](#content-policies)을 참조하십시오.

   **초기 컨텐츠**

   * 초기 컨텐츠 는 템플릿을 기반으로 페이지를 처음 만들 때 표시되는 컨텐츠를 정의합니다.
   * 그런 다음 초기 컨텐츠를 페이지 작성자가 편집할 수 있습니다.

   템플릿 작성자가 구조를 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md#editing-a-template-initial-content-author)를 참조하십시오.

   초기 컨텐츠에 대한 기술 세부 정보는 이 문서의 [초기 컨텐츠](#initial-content)를 참조하십시오.

   **레이아웃**

   * 장치 범위에 대한 템플릿 레이아웃을 정의할 수 있습니다.
   * 템플릿에 대한 응답형 레이아웃은 페이지 작성의 경우와 마찬가지로 작동합니다.

   템플릿 작성자가 템플릿 레이아웃을 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md#editing-a-template-layout-template-author)를 참조하십시오.

   템플릿 레이아웃에 대한 자세한 내용은 이 문서의 [레이아웃](#layout)을 참조하십시오.

1. 템플릿을 활성화한 다음 특정 컨텐츠 트리에 대해 허용합니다.

   * 템플릿을 활성화하거나 비활성화하여 페이지 작성자가 사용하거나 사용할 수 없게 만들 수 있습니다.
   * 특정 페이지 분기에서 템플릿을 사용하거나 사용할 수 없게 지정할 수 있습니다.

   템플릿 작성자가 템플릿을 활성화하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author)를 참조하십시오.

   템플릿 활성화에 대한 자세한 내용은 이 문서에서 [Us](#enabling-and-allowing-a-template-for-use)용 템플릿 활성화 및 허용 을 참조하십시오

1. 이 필드를 사용하여 컨텐츠 페이지를 만듭니다.

   * 템플릿을 사용하여 새 페이지를 만들 경우 정적 및 편집 가능 템플릿 간에 차이점은 없으며 구분하는 표시도 없습니다.
   * 페이지 작성자를 위해 프로세스는 투명하게 진행됩니다.

   페이지 작성자가 템플릿을 사용하여 페이지를 만드는 방법에 대한 자세한 내용은 [페이지 만들기 및 구성](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#templates)을 참조하십시오.

   편집 가능한 템플릿으로 페이지 만들기에 대한 기술적 세부 사항은 이 문서에서 [결과 컨텐츠 페이지](#resultant-content-pages)를 참조하십시오.

>[!TIP]
>
>국제화해야 하는 정보는 템플릿에 입력하지 마십시오. 내부화를 위해 코어 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html)의 [현지화 기능이 권장됩니다.

>[!NOTE]
>
>템플릿은 페이지 작성 워크플로우를 간소화하는 강력한 도구입니다. 그러나 너무 많은 템플릿이 작성자를 압도하고 페이지 생성을 혼동시킬 수 있습니다. 경험상 좋은 방법은 서식 파일의 수를 100개 미만으로 유지하는 것입니다.
>
>Adobe은 성능에 영향을 줄 수 있으므로 1,000개 이상의 템플릿을 사용하지 않는 것이 좋습니다.

>[!NOTE]
>
>편집기 클라이언트 라이브러리는 컨텐츠 페이지에 `cq.shared` 네임스페이스가 있다고 가정하며, 없는 경우 JavaScript 오류 `Uncaught TypeError: Cannot read property 'shared' of undefined`가 발생합니다.
>
>모든 샘플 컨텐츠 페이지에는 `cq.shared`이 포함되어 있으므로 이를 기반으로 하는 모든 컨텐츠는 자동으로 `cq.shared`을 포함합니다. 그러나 샘플 컨텐츠를 기반으로 컨텐츠 페이지를 지정하지 않고 처음부터 직접 만드는 경우에는 `cq.shared` 네임스페이스를 포함해야 합니다.
>
>자세한 내용은 [클라이언트측 라이브러리 사용](/help/implementing/developing/introduction/clientlibs.md)을 참조하십시오.



## 템플릿 폴더 {#template-folders}

템플릿을 구성하려면 다음 폴더를 사용할 수 있습니다.

* `global`
* 사이트별

>[!NOTE]
>
>폴더를 중첩할 수 있더라도 사용자가 **템플릿** 콘솔에서 볼 때 폴더가 플랫 구조로 표시됩니다.

표준 AEM 인스턴스에서는 `global` 폴더가 템플릿 콘솔에 이미 있습니다. 이 폴더는 기본 템플릿을 보유하며, 현재 폴더에 정책 및/또는 템플릿 유형을 찾을 수 없는 경우 폴백으로 작동합니다. 기본 템플릿을 이 폴더에 추가하거나 새 폴더를 만들 수 있습니다(권장).

>[!NOTE]
>
>사용자 지정된 템플릿을 포함하고 `global` 폴더를 사용하지 않도록 새 폴더를 만드는 것이 가장 좋습니다.

>[!CAUTION]
>
>폴더는 `admin` 권한이 있는 사용자가 만들어야 합니다.

템플릿 유형 및 정책은 다음 우선 순위 순서에 따라 모든 폴더에 상속됩니다.

1. 현재 폴더
1. 현재 폴더의 상위 폴더
1. `/conf/global`
1. `/apps`
1. `/libs`

허용되는 모든 항목 목록이 만들어집니다. 구성이 겹치는 경우( `path`/ `label`), 현재 폴더에 가장 가까운 인스턴스만 사용자에게 표시됩니다.

새 폴더를 만들려면 다음 중 하나를 수행할 수 있습니다.

* 프로그래밍 방식으로 또는 CRXDE Lite 사용
* [구성 브라우저 사용](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

## CRXDE Lite {#using-crxde-lite} 사용

1. 프로그래밍 방식으로 또는 CRXDE Lite을 사용하여 인스턴스에 새 폴더( /conf 아래)를 만들 수 있습니다.

   다음 구조를 사용해야 합니다.

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. 그런 다음 폴더 루트 노드에서 다음 속성을 정의할 수 있습니다.

   `<your-folder-name> [sling:Folder]`

   * 이름: `jcr:title`
   * 유형: `String`
   * 값:**템플릿** 콘솔에 표시할 제목(폴더의 경우)입니다.

1. 표준 작성 권한 및 권한 외에도(예:`content-authors`) 이제 그룹을 할당하고 작성자가 새 폴더에 템플릿을 만들 수 있도록 필요한 ACL(액세스 권한)을 정의해야 합니다.

   `template-authors` 그룹은 할당해야 하는 기본 그룹입니다. 자세한 내용은 [ACL 및 그룹](#acls-and-groups) 섹션을 참조하십시오.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### 구성 브라우저 {#using-the-configuration-browser} 사용

1. **전역 탐색** -> **도구** > [**구성 브라우저**&#x200B;로 이동합니다.](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

   기존 폴더는 `global` 폴더를 포함하여 왼쪽에 나열됩니다.

1. **만들기**&#x200B;를 클릭합니다.
1. **구성 만들기** 대화 상자에서 다음 필드를 구성해야 합니다.

   * **제목**:구성 폴더의 제목을 입력합니다
   * **편집 가능한 템플릿**:이 폴더 내에서 편집 가능한 템플릿을 허용하는 확인 표시

1. **만들기**&#x200B;를 클릭합니다

>[!NOTE]
>
>[구성 브라우저,](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)에서 이 폴더 내에 템플릿을 만들려면 전역 폴더를 편집하고 **편집 가능한 템플릿** 옵션을 활성화할 수 있지만, 권장되는 방법은 아닙니다.

### ACL 및 그룹 {#acls-and-groups}

템플릿 폴더가 생성되면(CRXDE를 통해 또는 구성 브라우저를 통해), 템플릿 폴더에 대한 적절한 그룹에 대해 ACL을 정의해야 적절한 보안이 보장됩니다.

[WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)에 대한 템플릿 폴더를 예로 사용할 수 있습니다.

#### template-authors 그룹 {#the-template-authors-group}

`template-authors` 그룹은 템플릿에 대한 액세스를 관리하는 데 사용되는 그룹이며, AEM과 표준으로 제공되지만 비어 있습니다. 프로젝트/사이트의 그룹에 사용자를 추가해야 합니다.

>[!CAUTION]
>
>`template-authors` 그룹은 새 템플릿을 만들 수 있어야 하는 사용자만을 위한 것입니다.
>
>템플릿 편집은 매우 강력하며, 제대로 수행하지 않으면 기존 템플릿을 끊을 수 있습니다. 따라서 이 역할은 초점을 맞춰야 하며 자격이 있는 사용자만 포함해야 합니다.

다음 표에서는 템플릿 편집에 필요한 권한에 대해 자세히 설명합니다.

<table>
 <tbody>
  <tr>
   <th>경로</th>
   <th>역할/그룹</th>
   <th>권한<br /> </th>
   <th>설명</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>템플릿 작성자<br /> </td>
   <td>읽기, 쓰기, 복제</td>
   <td>사이트 특정 <code>/conf</code> 공간에서 템플릿을 작성, 읽기, 업데이트, 삭제 및 복제하는 템플릿 작성자</td>
  </tr>
  <tr>
   <td>익명 웹 사용자</td>
   <td>읽기</td>
   <td>익명 웹 사용자는 페이지를 렌더링하는 동안 템플릿을 읽어야 합니다.</td>
  </tr>
  <tr>
   <td>컨텐츠 작성자</td>
   <td>복제</td>
   <td>replicateContent 작성자는 페이지를 활성화할 때 페이지 템플릿을 활성화해야 합니다</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>읽기, 쓰기, 복제</td>
   <td>사이트 특정 <code>/conf</code> 공간에서 템플릿을 작성, 읽기, 업데이트, 삭제 및 복제하는 템플릿 작성자</td>
  </tr>
  <tr>
   <td>익명 웹 사용자</td>
   <td>읽기</td>
   <td>익명 웹 사용자는 페이지를 렌더링하는 동안 정책을 읽어야 합니다.</td>
  </tr>
  <tr>
   <td>컨텐츠 작성자</td>
   <td>복제</td>
   <td>컨텐츠 작성자는 페이지를 활성화할 때 페이지 템플릿의 정책을 활성화해야 합니다</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>템플릿 작성자</td>
   <td>읽기</td>
   <td>템플릿 작성자는 사전 정의된 템플릿 유형 중 하나를 기반으로 새 템플릿을 만듭니다.</td>
  </tr>
  <tr>
   <td>익명 웹 사용자</td>
   <td>없음</td>
   <td>익명 웹 사용자는 템플릿 형식에 액세스할 수 없습니다</td>
  </tr>
 </tbody>
</table>

이 기본 `template-authors` 그룹은 모든 `template-authors` 구성원이 모든 템플릿에 액세스하고 작성할 수 있는 프로젝트 설정만 포함합니다. 템플릿에 대한 액세스를 구분하기 위해 여러 템플릿 작성자 그룹이 필요한 보다 복잡한 설정의 경우 더 많은 사용자 지정 템플릿 작성자 그룹을 만들어야 합니다. 그러나 템플릿 작성자 그룹에 대한 권한은 여전히 동일합니다.

## 템플릿 유형 {#template-type}

새 템플릿을 만들 때는 템플릿 유형을 지정해야 합니다.

* 템플릿 유형은 템플릿에 대한 템플릿을 효과적으로 제공합니다. 새 템플릿을 만들 때 선택한 템플릿 유형의 구조 및 초기 컨텐츠를 사용하여 새 템플릿에 만듭니다.

   * 템플릿 유형이 복사되어 템플릿을 만듭니다.
   * 복사가 발생하면 템플릿과 템플릿 유형 간의 유일한 연결은 정보를 위한 정적 참조입니다.

* 템플릿 유형을 사용하면 다음을 정의할 수 있습니다.

   * 페이지 구성 요소의 리소스 유형입니다.
   * 템플릿 편집기에서 허용되는 구성 요소를 정의하는 루트 노드의 정책입니다.
   * 템플릿 유형에서 응답형 그리드에 대한 중단점을 정의하고 모바일 에뮬레이터를 설정하는 것이 좋습니다.

* AEM에서는 HTML5 페이지 및 적응형 양식 페이지와 같은 기본적인 템플릿 유형 중 일부를 제공합니다.

   * 추가 예제는 [WKND 자습서의 일부로 제공됩니다.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* 템플릿 유형은 일반적으로 개발자가 정의합니다.

기본 템플릿 유형은 다음 위치에 저장됩니다.

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>`/libs` 경로에서 아무 것도 변경하면 안 됩니다. AEM에 대한 업데이트로 언제든지 `/libs` 컨텐츠를 덮어쓸 수 있기 때문입니다.

사이트별 템플릿 유형은 다음과 유사한 위치에 저장해야 합니다.

* `/apps/settings/wcm/template-types`

사용자 지정된 템플릿 유형에 대한 정의는 사용자 정의 폴더에 저장하거나(권장) `global`에 저장해야 합니다. 예:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>템플릿 유형은 올바른 폴더 구조(즉,`/settings/wcm/...`)가 없으면 템플릿 유형을 찾을 수 없습니다.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating a new editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

>[!CAUTION]
>
>The value of `cq:deviceGroups` must be set as a relative path such as `mobile/groups/responsive` and not as an absolute path such as `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>With static templates /help/sites-developing/page-templates-static.md, the value of `cq:deviceGroups` could be set at the root of the site.
>
>With editable templates, this value is now stored at the template level and is not supported at the page root level.
-->

### 템플릿 유형 만들기 {#creating-template-types}

다른 템플릿의 기반으로 사용할 수 있는 템플릿을 만든 경우 이 템플릿을 템플릿 유형으로 복사할 수 있습니다.

1. 템플릿 유형의 기반으로 사용할 페이지 템플릿 [에 설명된 대로 템플릿을 만듭니다.](/help/sites-cloud/authoring/features/templates.md#creating-a-new-template-template-author)
1. CRXDE Lite을 사용하여 새로 만든 템플릿을 `templates` 노드에서 [템플릿 폴더](#template-folders) 아래의 `template-types` 노드로 복사합니다.
1. [템플릿 폴더](#template-folders) 아래의 `templates` 노드에서 템플릿을 삭제합니다.
1. `template-types` 노드 아래에 있는 템플릿의 복사본에서 모든 `cq:template` 및 `cq:templateType` `jcr:content` 속성을 삭제합니다.

GitHub에서 사용할 수 있는 편집 가능한 템플릿 예제 를 사용하여 고유한 템플릿 유형을 개발할 수도 있습니다.

GITHUB의 코드

GitHub에서 이 페이지의 코드를 찾을 수 있습니다

* [GitHub에서 aem-sites-example-custom-template-type project 열기](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* 프로젝트를 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)로 다운로드합니다

## 템플릿 정의 {#template-definitions}

편집 가능한 템플릿에 대한 정의는 [사용자 정의 폴더](#template-folders)(권장)나 `global`에 저장됩니다. 예:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

템플릿의 루트 노드는 `cq:Template` 유형이며 뼈대 구조가 다음과 같습니다.

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

기본 요소는 다음과 같습니다.

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:content {#jcr-content}

이 노드는 템플릿에 대한 속성을 보유합니다.

* **이름**: `jcr:title`
* **이름**: `status`
   * ``**유형**: `String`
   * **값**: `draft`,  `enabled` 또는  `disabled`

### 구조 {#structure}

결과 페이지의 구조를 정의합니다.

* 새 페이지를 만들 때 초기 컨텐츠( `/initial`)와 병합됩니다.
* 구조를 변경하면 템플릿으로 만든 페이지에 반영됩니다.
* `root` ( `structure/jcr:content/root`) 노드는 결과 페이지에서 사용할 수 있는 구성 요소 목록을 정의합니다.
   * 템플릿 구조에 정의된 구성 요소는 결과 페이지에서 이동하거나 삭제할 수 없습니다.
   * 구성 요소 잠금이 해제되면 `editable` 속성이 `true` 로 설정됩니다.
   * 이미 컨텐츠가 포함된 구성 요소의 잠금이 해제되면 이 컨텐츠는 `initial` 분기로 이동합니다.

* `cq:responsive` 노드는 응답형 레이아웃에 대한 정의를 보유합니다.

### 초기 컨텐츠 {#initial-content}

작성 시 새 페이지가 가질 초기 컨텐츠를 정의합니다.

* 새 페이지에 복사된 `jcr:content` 노드를 포함합니다.
* 새 페이지를 만들 때 구조( `/structure`)와 병합됩니다.
* 작성 후 초기 컨텐츠가 변경되는 경우 기존 페이지가 업데이트되지 않습니다.
* `root` 노드에는 결과 페이지에서 사용할 수 있는 구성 요소 목록이 있습니다.
* 구조 모드에서 구성 요소에 컨텐츠를 추가하고 해당 구성 요소의 잠금이 해제되거나 그 반대의 경우 이 컨텐츠가 초기 컨텐츠로 사용됩니다.

### 레이아웃 {#layout}

[템플릿을 편집할 때 레이아웃](/help/sites-cloud/authoring/features/templates.md)을 정의할 수 있습니다. 이 레이아웃은 [표준 응답형 레이아웃](/help/sites-cloud/authoring/features/responsive-layout.md)을 사용합니다.

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### 컨텐츠 정책 {#content-policies}

컨텐츠 정책은 구성 요소의 디자인 속성을 정의합니다. 예: 사용 가능한 구성 요소 또는 최소/최대 크기. 이러한 속성은 템플릿(및 템플릿으로 만든 페이지)에 적용될 수 있습니다. 템플릿 편집기에서 컨텐츠 정책을 만들고 선택할 수 있습니다.

* `root` 노드의 `cq:policy` 속성
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
페이지의 단락 시스템에 대한 컨텐츠 정책에 대한 상대적 참조를 제공합니다.

* `root` 아래의 구성 요소 명시적 노드에서 속성 `cq:policy`이 개별 구성 요소에 대한 정책에 대한 링크를 제공합니다.

* 실제 정책 정의는 다음과 같이 저장됩니다.
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>정책 정의 경로는 구성 요소의 경로에 따라 다릅니다. `cq:policy` 구성 자체에 대한 상대 참조를 보유합니다.

### 페이지 정책 {#page-policies}

페이지 정책을 사용하면 템플릿 또는 결과 페이지에서 페이지(주 parsys)에 대한 [컨텐츠 정책](#content-policies)을 정의할 수 있습니다.

### 템플릿 활성화 및 허용 {#enabling-and-allowing-a-template-for-use}

1. **템플릿 활성화**

   템플릿을 사용하려면 다음 중 한 방법으로 템플릿을 활성화해야 합니다.

   * [템플릿 콘솔](/help/sites-cloud/authoring/features/templates.md) 에서 템플릿  **** 활성화

   * `jcr:content` 노드에서 상태 속성을 설정합니다.

      * 예를 들어,
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * 속성을 정의합니다.

         * 이름:상태
         * 유형:문자열
         * 값: `enabled`

1. **허용된 템플릿**

   * [하위 분기의 해당 페이지나  **루트**](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) 페이지의 페이지 속성에서 허용된 템플릿 경로를 정의합니다.
   * 속성을 설정합니다.
      `cq:allowedTemplates`
설정 
`jcr:content` 필요한 분기의 노드입니다.
   예를 들어 다음 값이 있는 경우:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## 결과 컨텐츠 페이지 {#resultant-content-pages}

편집 가능한 템플릿에서 만든 페이지:

* 템플릿의 `structure` 및 `initial`에서 병합된 하위 트리를 사용하여 만들어집니다

* 템플릿 및 템플릿 유형에 있는 정보에 대한 참조를 보유합니다. 이 작업은 속성이 있는 `jcr:content` 노드를 사용하여 수행됩니다.

   * `cq:template` - 실제 템플릿에 대한 동적 참조를 제공합니다.템플릿 변경 사항이 실제 페이지에 반영되도록 합니다.

   * `cq:templateType` - 템플릿 유형에 대한 참조를 제공합니다.

![템플릿, 컨텐츠 및 구성 요소가 상호 작용하는 방법](assets/templates-content-components.png)

위의 다이어그램은 템플릿, 콘텐츠 및 구성 요소가 상호 작용하는 방법을 보여줍니다.

* 컨트롤러 - `/content/<my-site>/<my-page>` - 템플릿을 참조하는 결과 페이지입니다. 컨텐츠는 전체 프로세스를 제어합니다. 정의에 따라 적절한 템플릿 및 구성 요소에 액세스합니다.
* 구성 - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - [템플릿 및 관련 컨텐츠 정책](#template-definitions)이 페이지 구성을 정의합니다.
* 모델 - OSGi 번들 - [OSGI 번들](/help/implementing/deploying/configuring-osgi.md)은 기능을 구현합니다.
* 보기 - `/apps/<my-site>/components` - 작성자와 게시 환경 모두에서 컨텐츠가 구성 요소에 의해 렌더링됩니다.

페이지를 렌더링할 때:

* **템플릿**:

   * 해당 `jcr:content` 노드의 `cq:template` 속성이 참조되어 해당 페이지에 해당하는 템플릿에 액세스합니다.

* **구성 요소**:

   * 페이지 구성 요소는 템플릿의 `structure/jcr:content` 트리를 페이지의 `jcr:content` 트리와 병합합니다.
      * 페이지 구성 요소는 작성자가 편집 가능한 것으로 플래그가 지정된 템플릿 구조(하위 항목 포함)의 노드만 편집할 수 있도록 허용합니다.
      * 페이지에서 구성 요소를 렌더링할 때 해당 구성 요소의 상대 경로는 `jcr:content` 노드에서 가져옵니다.템플릿의 `policies/jcr:content` 노드 아래에 있는 동일한 경로가 검색됩니다.
         * 이 노드의 `cq:policy` 속성은 실제 컨텐츠 정책을 가리킵니다(즉, 해당 구성 요소에 대한 디자인 구성을 보유함).
            * 이렇게 하면 동일한 컨텐츠 정책 구성을 다시 사용하는 여러 템플릿이 있을 수 있습니다.

### 템플릿 가용성 {#template-availability}

사이트 관리자 인터페이스에서 새 페이지를 만들 때 사용 가능한 템플릿 목록은 새 페이지의 위치와 각 템플릿에 지정된 배치 제한에 따라 다릅니다.

다음 속성은 새 페이지를 `P` 페이지의 자식으로 배치할 때 템플릿 `T`을 사용할 수 있는지 여부를 결정합니다. 이러한 각 속성은 경로와의 일치에 사용되는 0개 이상의 정규 표현식을 포함하는 다중 값 문자열입니다.

* `P`의 `jcr:content` 하위 노드의 `cq:allowedTemplates` 속성 또는 `P`의 상위 노드입니다.

* `T`의 `allowedPaths` 속성.

* `T`의 `allowedParents` 속성.

* `P` 템플릿의 `allowedChildren` 속성입니다.

평가는 다음과 같이 작동합니다.

* `P`로 시작하는 페이지 계층 구조를 오름차순으로 변경하는 동안 비어 있지 않은 첫 번째 `cq:allowedTemplates` 속성이 `T` 경로에 대해 일치합니다. 값이 일치하지 않으면 `T`이 거부됩니다.

* `T`에 비어 있지 않은 `allowedPaths` 속성이 있지만, 값이 `P` 경로와 일치하지 않으면 `T`이 거부됩니다.

* 위의 속성 중 둘 다 비어 있거나 존재하지 않는 경우 `T`이 `P`과 동일한 애플리케이션에 속하지 않는 한 거부됩니다. `T` 은  `P` if 와 동일한 응용 프로그램에 속하며, 경로 중 두 번째 수준의 이름이 경로 `T` 의 두 번째 수준의 이름과 동일한 경우에만  `P`속합니다. 예를 들어 템플릿 `/apps/wknd/templates/foo`은 페이지 `/content/wknd`과 동일한 애플리케이션에 속합니다.

* `T`에 비어 있지 않은 `allowedParents` 속성이 있지만, 값이 `P` 경로와 일치하지 않으면 `T`이 거부됩니다.

* `P` 의 템플릿에 비어 있지 않은 `allowedChildren` 속성이 있지만, 값이 `T` 경로와 일치하지 않으면 `T`이 거부됩니다.

* 다른 모든 경우에는 `T`이 허용됩니다.

다음 다이어그램은 템플릿 평가 프로세스를 나타냅니다.

![템플릿 평가 프로세스](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM은 **사이트**&#x200B;에서 허용되는 템플릿을 제어하는 여러 속성을 제공합니다. 그러나 이러한 규칙을 결합하면 추적 및 관리가 어려운 매우 복잡한 규칙이 만들어질 수 있습니다.
>
>따라서 다음을 정의하여 간단하게 시작할 것을 Adobe에서 권장합니다.
>
>* `cq:allowedTemplates` 속성만
   >
   >
* 사이트 루트에서만
>
>
예를 들어 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 컨텐츠를 참조하십시오.`/content/wknd/jcr:content`
>
>`allowedPaths`, `allowedParents` 및 `allowedChildren` 속성을 템플릿에 놓아 보다 복잡한 규칙을 정의할 수도 있습니다. 그러나 가능한 경우 허용되는 템플릿을 추가로 제한해야 하는 경우 사이트의 하위 섹션에서 추가 `cq:allowedTemplates` 속성을 정의하는 것이 훨씬 쉽습니다.**
>
>추가 이점은 **페이지 속성**&#x200B;의 **고급** 탭에서 작성자가 `cq:allowedTemplates` 속성을 업데이트할 수 있다는 것입니다. 다른 템플릿 속성은 (표준) UI를 사용하여 업데이트할 수 없으므로 변경 때마다 개발자가 규칙과 코드 배포를 유지해야 합니다.

#### 하위 페이지에 사용된 템플릿 제한 {#limiting-templates-used-in-child-pages}

지정된 페이지에서 하위 페이지를 만드는 데 사용할 수 있는 템플릿을 제한하려면 페이지의 `jcr:content` 노드의 `cq:allowedTemplates` 속성을 사용하여 하위 페이지로 허용할 템플릿 목록을 지정합니다. 목록의 각 값은 허용되는 하위 페이지에 대한 템플릿의 절대 경로여야 합니다(예: `/apps/wknd/templates/page-content`).

템플릿의 `jcr:content` 노드에서 `cq:allowedTemplates` 속성을 사용하여 이 템플릿을 사용하는 새로 만든 모든 페이지에 이 구성을 적용할 수 있습니다.

템플릿 계층 구조 등 추가 제약 조건을 추가하려면 템플릿에서 `allowedParents/allowedChildren` 속성을 사용할 수 있습니다. 그런 다음 템플릿에서 만든 페이지를 T 템플릿에서 만든 페이지의 상위/1차 하위 구성요소로 명시적으로 지정할 수 있습니다.
