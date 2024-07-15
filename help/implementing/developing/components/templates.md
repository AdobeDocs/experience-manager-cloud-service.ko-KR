---
title: 페이지 템플릿
description: 페이지 템플릿은 새 페이지의 기반으로 사용되는 페이지를 만들 때 사용됩니다
exl-id: ea42fce9-9af2-4349-a4e4-547e6e8da05c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '3267'
ht-degree: 4%

---

# 페이지 템플릿 {#page-templates}

페이지를 만들 때 템플릿을 선택해야 합니다. 페이지 템플릿은 새 페이지의 기반으로 사용됩니다. 템플릿은 결과 페이지의 구조, 초기 콘텐츠 및 사용할 수 있는 구성 요소(디자인 속성)를 정의합니다. 여기에는 다음과 같은 몇 가지 이점이 있습니다.

* 페이지 템플릿을 사용하면 전문 작성자가 [템플릿을 만들고 편집](/help/sites-cloud/authoring/sites-console/templates.md)할 수 있습니다.
   * 이러한 전문 작성자를 **템플릿 작성자**&#x200B;라고 합니다.
   * 템플릿 작성자는 `template-authors` 그룹의 구성원이어야 합니다.
* 페이지 템플릿에서 만든 모든 페이지에 대한 동적 연결은 유지됩니다. 이렇게 하면 템플릿에 대한 모든 변경 사항이 페이지 자체에 반영됩니다.
* 페이지 템플릿 을 사용하면 페이지 구성 요소를 보다 일반적으로 사용할 수 있으므로 맞춤화 없이 핵심 페이지 구성 요소를 사용할 수 있습니다.

페이지 템플릿을 사용하면 페이지를 만드는 조각이 구성 요소 내에서 격리됩니다. UI에서 필요한 구성 요소 조합을 구성할 수 있으므로 각 페이지 변형에 대해 새로운 페이지 구성 요소를 개발할 필요가 없습니다.

이 문서는

* 페이지 템플릿 만들기에 대한 개요를 제공합니다.
* 편집 가능한 템플릿을 만드는 데 필요한 관리/개발자 작업에 대해 설명합니다.
* 편집 가능한 템플릿의 기술 정보를 설명합니다
* AEM이 템플릿의 가용성을 평가하는 방법을 설명합니다.

>[!NOTE]
>
>이 문서에서는 사용자가 이미 템플릿 만들기 및 편집에 익숙하다고 가정합니다. 템플릿 작성자에게 노출되는 편집 가능한 템플릿의 기능에 대해 자세히 설명하는 작성 문서 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md)를 참조하십시오.

>[!TIP]
>
>[WKND 튜토리얼](/help/implementing/developing/introduction/develop-wknd-tutorial.md)은(는) 예제를 구현하여 페이지 템플릿을 사용하는 방법에 대해 자세히 알아보고 새 프로젝트에서 템플릿을 설정하는 방법을 이해하는 데 유용합니다

## 새 템플릿 만들기 {#creating-a-new-template}

페이지 템플릿 만들기는 주로 템플릿 작성자가 [템플릿 콘솔 및 템플릿 편집기](/help/sites-cloud/authoring/sites-console/templates.md)를 사용하여 수행합니다. 이 섹션은 이 프로세스에 대한 개요를 제공하며 다음 기술 수준에서 발생하는 사항에 대한 설명을 제공합니다.

편집 가능한 템플릿을 만들 때 다음 작업을 수행하십시오.

1. [템플릿 폴더를 만듭니다](#template-folders). 이 작업은 필수는 아니지만 모범 사례에 권장됩니다.
1. [템플릿 유형](#template-type)을(를) 선택하십시오. [템플릿 정의](#template-definitions)을(를) 만들기 위해 복사됩니다.

   >[!NOTE]
   >
   >다양한 템플릿 유형이 즉시 제공됩니다. 필요한 경우 [사이트별 템플릿 형식을 직접 만들 수 있습니다](#creating-template-types).

1. 새 템플릿의 구조, 콘텐츠 정책, 초기 콘텐츠 및 레이아웃을 구성합니다.

   **구조**

   * 이 구조를 통해 템플릿의 구성 요소와 콘텐츠를 정의할 수 있습니다.
   * 템플릿 구조에 정의된 구성 요소는 결과 페이지 안에서 이동하거나 결과 페이지에서 삭제할 수 없습니다.
   * 페이지 작성자가 구성 요소를 추가 및 제거할 수 있도록 하려면 템플릿에 단락 시스템을 추가하십시오.
   * 초기 콘텐츠를 정의할 수 있도록 하려면 구성 요소 잠금을 해제했다가 다시 잠글 수 있습니다.

   템플릿 작성자가 구조를 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-structure-template-author)를 참조하십시오.

   구조에 대한 기술적인 세부 정보는 이 문서의 [구조](#structure)를 참조하십시오.

   **정책**

   * 콘텐츠 정책은 구성 요소의 디자인 속성을 정의합니다.

      * 예를 들어 사용 가능한 구성 요소 또는 최소/최대 차원이 있습니다.

   * 이러한 속성은 템플릿(및 템플릿으로 만든 페이지)에 적용될 수 있습니다.

   템플릿 작성자가 정책을 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-structure-template-author)를 참조하십시오.

   정책에 대한 기술적인 세부 정보는 이 문서에서 [콘텐츠 정책](#content-policies)을(를) 참조하십시오.

   **초기 콘텐츠**

   * 초기 콘텐츠 는 템플릿을 기반으로 페이지를 처음 만들 때 표시되는 콘텐츠를 정의합니다.
   * 그런 다음 페이지 작성자는 초기 콘텐츠를 편집할 수 있습니다.

   템플릿 작성자가 구조를 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-initial-content-author)를 참조하십시오.

   초기 콘텐츠에 대한 자세한 내용은 이 문서에서 [초기 콘텐츠](#initial-content)를 참조하십시오.

   **레이아웃**

   * 디바이스 범위에 대한 템플릿 레이아웃을 정의할 수 있습니다.
   * 템플릿에 대한 응답형 레이아웃은 페이지 작성의 경우와 마찬가지로 작동합니다.

   템플릿 작성자가 템플릿 레이아웃을 정의하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-layout-template-author)를 참조하십시오.

   템플릿 레이아웃에 대한 기술적인 세부 정보는 이 문서의 [레이아웃](#layout)을(를) 참조하십시오.

1. 템플릿을 활성화한 다음 특정 콘텐츠 트리에 대해 허용합니다.

   * 페이지 작성자가 템플릿을 사용하거나 사용할 수 없게 하기 위해 템플릿을 활성화하거나 비활성화할 수 있습니다.
   * 특정 페이지 분기에서 템플릿을 사용하거나 사용할 수 없게 지정할 수 있습니다.

   템플릿 작성자가 템플릿을 사용하는 방법에 대한 자세한 내용은 [페이지 템플릿 만들기](/help/sites-cloud/authoring/sites-console/templates.md#enabling-and-allowing-a-template-template-author)를 참조하십시오.

   템플릿 사용에 대한 자세한 내용은 이 문서에서 [템플릿 사용 및 허용](#enabling-and-allowing-a-template-for-use)을 참조하십시오

1. 콘텐츠 페이지를 만드는 데 사용합니다.

   * 템플릿을 사용하여 페이지를 만들 때 정적 템플릿과 편집 가능한 템플릿 간에 눈에 보이는 차이점이 없고 표시가 없습니다.
   * 페이지 작성자의 경우 프로세스가 투명합니다.

   페이지 작성자가 템플릿을 사용하여 페이지를 만드는 방법에 대한 자세한 내용은 [페이지 만들기 및 구성](/help/sites-cloud/authoring/sites-console/organizing-pages.md#templates)을 참조하십시오.

   편집 가능한 템플릿을 사용하여 페이지를 만드는 방법에 대한 자세한 내용은 이 문서의 [결과 콘텐츠 페이지](#resultant-content-pages)를 참조하십시오.

>[!TIP]
>
>국제화해야 하는 정보는 템플릿에 입력하지 마십시오. 내재화를 위해 [핵심 구성 요소의 현지화 기능](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html)을 사용하는 것이 좋습니다.

>[!NOTE]
>
>템플릿은 페이지 생성 워크플로를 간소화할 수 있는 강력한 도구입니다. 그러나 템플릿이 너무 많으면 작성자를 압도하고 페이지 작성에 혼란을 초래할 수 있습니다. 가장 좋은 방법은 템플릿의 수를 100 미만으로 유지하는 것입니다.
>
>성능에 영향을 미칠 수 있으므로 1,000개 이상의 템플릿을 사용하지 않는 것이 좋습니다.

>[!NOTE]
>
>편집기 클라이언트 라이브러리는 컨텐츠 페이지에 `cq.shared` 네임스페이스가 있다고 가정하며, 이 네임스페이스가 없으면 JavaScript 오류 `Uncaught TypeError: Cannot read property 'shared' of undefined`이(가) 발생합니다.
>
>모든 샘플 콘텐츠 페이지에는 `cq.shared`이(가) 포함되어 있으므로 이를 기반으로 하는 모든 콘텐츠에는 자동으로 `cq.shared`이(가) 포함됩니다. 그러나 샘플 콘텐츠를 기반으로 하지 않고 처음부터 고유한 콘텐츠 페이지를 만들려는 경우에는 `cq.shared` 네임스페이스를 포함해야 합니다.
>
>자세한 내용은 [클라이언트측 라이브러리 사용](/help/implementing/developing/introduction/clientlibs.md)을 참조하십시오.



## 템플릿 폴더 {#template-folders}

템플릿을 구성하기 위해 다음 폴더를 사용할 수 있습니다.

* `global`
* 사이트별

>[!NOTE]
>
>폴더를 중첩할 수 있지만 사용자가 **템플릿** 콘솔에서 볼 때 폴더가 플랫 구조로 표시됩니다.

표준 AEM 인스턴스에서는 `global` 폴더가 템플릿 콘솔에 이미 있습니다. 이 폴더는 기본 템플릿을 보유하며, 현재 폴더에 정책 및/또는 템플릿 유형이 없는 경우 폴백으로 작동합니다. 이 폴더에 기본 템플릿을 추가하거나 폴더를 만들 수 있습니다(권장).

>[!NOTE]
>
>사용자 지정된 서식 파일을 저장할 폴더를 만들고 `global` 폴더를 사용하지 않는 것이 좋습니다.

>[!CAUTION]
>
>`admin` 권한이 있는 사용자가 폴더를 만들어야 합니다.

템플릿 유형 및 정책은 다음 우선 순위에 따라 모든 폴더에 상속됩니다.

1. 현재 폴더
1. 현재 폴더의 상위
1. `/conf/global`
1. `/apps`
1. `/libs`

허용된 모든 항목의 목록이 만들어집니다. 구성이 겹치는 경우(`path`/ `label`) 현재 폴더와 가장 가까운 인스턴스만 사용자에게 표시됩니다.

폴더를 만들려면 다음 작업을 수행할 수 있습니다.

* 프로그래밍 방식으로 또는 CRXDE Lite 사용
* [구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) 사용

## CRXDE Lite 사용 {#using-crxde-lite}

1. 프로그래밍 방식으로 또는 CRXDE Lite을 사용하여 인스턴스에 대해 새 폴더(/conf 아래에)를 만들 수 있습니다.

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
   * 값: **템플릿** 콘솔에 표시할 폴더의 제목입니다.

1. 표준 작성 권한 및 권한(예: `content-authors`) 외에도 이제 그룹을 할당하고 작성자가 새 폴더에 템플릿을 만들 수 있도록 필요한 액세스 권한(ACL)을 정의해야 합니다.

   `template-authors` 그룹은 할당해야 하는 기본 그룹입니다. 자세한 내용은 [ACL 및 그룹](#acls-and-groups) 섹션을 참조하십시오.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### 구성 브라우저 사용 {#using-the-configuration-browser}

1. **전역 탐색** > **도구** > [**구성 브라우저**](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)&#x200B;로 이동합니다.

   기존 폴더는 `global` 폴더를 포함하여 왼쪽에 나열됩니다.

1. **만들기**&#x200B;를 클릭합니다.
1. **구성 만들기** 대화 상자에서 다음 필드를 구성해야 합니다.

   * **제목**: 구성 폴더의 제목을 입력하십시오.
   * **편집 가능한 템플릿**: 이 폴더에서 편집 가능한 템플릿을 허용하려면 확인 표시를 합니다.

1. **만들기**&#x200B;를 클릭합니다.

>[!NOTE]
>
>[구성 브라우저](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)에서 전역 폴더를 편집하고 **편집 가능한 템플릿** 옵션을 활성화하면 이 폴더 내에 템플릿을 만들 수 있지만 권장되는 방법은 아닙니다.

### ACL 및 그룹 {#acls-and-groups}

CRXDE를 통해 또는 구성 브라우저를 통해 템플릿 폴더가 만들어지면 적절한 보안을 위해 템플릿 폴더의 적절한 그룹에 대해 ACL을 정의해야 합니다.

[WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)의 템플릿 폴더를 예로 사용할 수 있습니다.

#### 템플릿-작성자 그룹 {#the-template-authors-group}

`template-authors` 그룹은 템플릿에 대한 액세스를 관리하는 데 사용되는 그룹이며, AEM과 함께 기본으로 제공되지만 비어 있습니다. 프로젝트/사이트의 그룹에 사용자를 추가해야 합니다.

>[!CAUTION]
>
>`template-authors` 그룹은 새 템플릿을 만들 수 있어야 하는 사용자용입니다.
>
>템플릿 편집은 매우 강력하며, 제대로 수행하지 않으면 기존 템플릿이 손상될 수 있습니다. 따라서 이 역할은 초점을 맞추고 자격이 있는 사용자만 포함해야 합니다.

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
   <td>사이트 특정 <code>/conf</code> 공간에서 템플릿을 만들고, 읽고, 업데이트하고, 삭제하고 복제하는 템플릿 작성자</td>
  </tr>
  <tr>
   <td>익명 웹 사용자</td>
   <td>읽기</td>
   <td>익명 웹 사용자는 페이지를 렌더링하는 동안 템플릿을 읽어야 합니다.</td>
  </tr>
  <tr>
   <td>콘텐츠 작성자</td>
   <td>복제</td>
   <td>콘텐츠 작성자는 페이지를 활성화할 때 페이지의 템플릿을 활성화해야 합니다</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>읽기, 쓰기, 복제</td>
   <td>사이트 특정 <code>/conf</code> 공간에서 템플릿을 만들고, 읽고, 업데이트하고, 삭제하고 복제하는 템플릿 작성자</td>
  </tr>
  <tr>
   <td>익명 웹 사용자</td>
   <td>읽기</td>
   <td>익명 웹 사용자는 페이지를 렌더링하는 동안 정책을 읽어야 합니다.</td>
  </tr>
  <tr>
   <td>콘텐츠 작성자</td>
   <td>복제</td>
   <td>콘텐츠 작성자는 페이지를 활성화할 때 페이지 템플릿의 정책을 활성화해야 합니다</td>
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
   <td>익명 웹 사용자는 템플릿 유형에 액세스할 수 없습니다.</td>
  </tr>
 </tbody>
</table>

이 기본 `template-authors` 그룹은 모든 `template-authors` 구성원이 모든 템플릿에 액세스하고 작성할 수 있는 프로젝트 설정만 다룹니다. 템플릿에 대한 액세스를 구분하기 위해 여러 템플릿 작성자 그룹이 필요한 보다 복잡한 설정의 경우 더 많은 사용자 지정 템플릿 작성자 그룹을 만들어야 합니다. 그러나 템플릿 작성자 그룹에 대한 권한은 여전히 동일합니다.

## 템플릿 유형 {#template-type}

템플릿을 만들 때 템플릿 유형을 지정해야 합니다.

* 템플릿 유형은 템플릿에 템플릿을 효과적으로 제공합니다. 템플릿을 만들 때 선택한 템플릿 유형의 구조 및 초기 콘텐츠를 사용하여 새 템플릿을 만듭니다.

   * 템플릿 유형이 복사되어 템플릿이 생성됩니다.
   * 복사가 발생하면 템플릿과 템플릿 유형 간의 유일한 연결은 정보 제공을 위한 정적 참조입니다.

* 템플릿 유형을 사용하면 다음을 정의할 수 있습니다.

   * 페이지 구성 요소의 리소스 유형입니다.
   * 템플릿 편집기에서 허용되는 구성 요소를 정의하는 루트 노드의 정책입니다.
   * 템플릿 유형에서 반응형 그리드에 대한 중단점과 모바일 에뮬레이터의 설정을 정의하는 것이 좋습니다.

* AEM에서는 HTML5 페이지 및 적응형 양식 페이지와 같이 바로 사용할 수 있는 다양한 템플릿 유형을 제공합니다.

   * 추가 예제는 [WKND 자습서](/help/implementing/developing/introduction/develop-wknd-tutorial.md)의 일부로 제공됩니다.

* 템플릿 유형은 일반적으로 개발자에 의해 정의됩니다.

기본 제공 템플릿 유형은 아래에 저장됩니다.

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>`/libs` 경로에서 아무 것도 변경할 수 없습니다. AEM 업데이트로 언제든지 `/libs`의 콘텐츠를 덮어쓸 수 있기 때문입니다.

사이트별 템플릿 유형은 다음과 유사한 위치에 저장해야 합니다.

* `/apps/settings/wcm/template-types`

사용자 지정된 템플릿 유형에 대한 정의는 사용자 정의 폴더(권장) 또는 `global`에 저장해야 합니다. 예:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>템플릿 형식은 올바른 폴더 구조(즉, `/settings/wcm/...`)를 준수해야 합니다. 그렇지 않으면 템플릿 형식을 찾을 수 없습니다.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating an editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

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

다른 템플릿의 기반으로 사용할 수 있는 템플릿을 생성한 경우 이 템플릿을 템플릿 유형으로 복사할 수 있습니다.

1. 여기에 설명된 대로 [페이지 템플릿](/help/sites-cloud/authoring/sites-console/templates.md#creating-a-new-template-template-author)과(와) 같은 템플릿을 만드십시오. 이 템플릿은 템플릿 유형의 기반으로 사용됩니다.
1. CRXDE Lite을 사용하여 `templates` 노드에서 [템플릿 폴더](#template-folders) 아래의 `template-types` 노드로 만든 템플릿을 복사합니다.
1. [템플릿 폴더](#template-folders) 아래의 `templates` 노드에서 템플릿을 삭제하십시오.
1. `template-types` 노드 아래에 있는 템플릿의 복사본에서 모든 `jcr:content` 노드에서 모든 `cq:template` 및 `cq:templateType` 속성을 삭제합니다.

GitHub에서 사용 가능한 편집 가능한 예제 템플릿을 기준으로 자체 템플릿 유형을 개발할 수도 있습니다.

GITHUB의 코드

GitHub에서 이 페이지의 코드를 확인할 수 있습니다

* [GitHub에서 aem-sites-example-custom-template-type 프로젝트 열기](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* 프로젝트를 [ZIP 파일](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)(으)로 다운로드

## 템플릿 정의 {#template-definitions}

편집 가능한 템플릿에 대한 정의는 [사용자 정의 폴더](#template-folders)(권장) 또는 `global`에 저장됩니다. 예:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

템플릿의 루트 노드가 `cq:Template` 유형이며 뼈대 구조가 다음과 같습니다.

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

주요 요소는 다음과 같습니다.

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:content {#jcr-content}

이 노드에는 템플릿에 대한 속성이 있습니다.

* **이름**: `jcr:title`
* **이름**: `status`
   * &quot;**유형**: `String`
   * **값**: `draft`, `enabled` 또는 `disabled`

### 구조 {#structure}

결과 페이지의 구조를 정의합니다.

* 페이지를 만들 때 초기 콘텐츠(`/initial`)와 병합됩니다.
* 구조에 대한 변경 사항은 템플릿으로 만든 모든 페이지에 반영됩니다.
* `root`( `structure/jcr:content/root`) 노드는 결과 페이지에서 사용할 수 있는 구성 요소 목록을 정의합니다.
   * 템플릿 구조에 정의된 구성 요소는 결과 페이지에서 이동하거나 삭제할 수 없습니다.
   * 구성 요소 잠금을 해제하면 `editable` 속성이 `true`(으)로 설정됩니다.
   * 이미 콘텐츠가 들어 있는 구성 요소의 잠금이 해제되면 이 콘텐츠가 `initial` 분기로 이동됩니다.

* `cq:responsive` 노드에는 응답형 레이아웃에 대한 정의가 있습니다.

### 초기 콘텐츠 {#initial-content}

새 페이지가 만들어질 때 갖게 될 초기 콘텐츠를 정의합니다.

* 새 페이지에 복사된 `jcr:content` 노드를 포함합니다.
* 페이지를 만들 때 구조체(`/structure`)와 병합됩니다.
* 생성 후 초기 콘텐츠가 변경되면 기존 페이지가 업데이트되지 않습니다.
* `root` 노드에는 최종 페이지에서 사용할 수 있는 항목을 정의하는 구성 요소 목록이 있습니다.
* 콘텐츠가 구조 모드의 구성 요소에 추가되고 해당 구성 요소의 잠금이 해제된 경우(또는 반대로) 이 콘텐츠는 초기 콘텐츠로 사용됩니다.

### 레이아웃 {#layout}

[템플릿을 편집할 때 레이아웃을 정의할 수 있습니다](/help/sites-cloud/authoring/sites-console/templates.md). 이 레이아웃은 [표준 반응형 레이아웃](/help/sites-cloud/authoring/page-editor/responsive-layout.md)을 사용합니다.

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### 컨텐츠 정책 {#content-policies}

콘텐츠 정책은 구성 요소의 디자인 속성을 정의합니다. 예: 사용 가능한 구성 요소 또는 최소/최대 크기. 템플릿과 템플릿으로 만든 페이지에 적용할 수 있습니다. 템플릿 편집기에서 컨텐츠 정책을 만들고 선택할 수 있습니다.

* `root` 노드의 속성 `cq:policy`
  `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
페이지의 단락 시스템에 대한 콘텐츠 정책에 대한 상대 참조를 제공합니다.

* `root` 아래의 구성 요소 명시적 노드의 `cq:policy` 속성은 개별 구성 요소의 정책에 대한 링크를 제공합니다.

* 실제 정책 정의는 아래에 저장됩니다.
  `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>정책 정의의 경로는 구성 요소의 경로에 따라 다릅니다. `cq:policy`은(는) 구성 자체에 대한 상대 참조를 보유합니다.

### 페이지 정책 {#page-policies}

페이지 정책을 사용하면 템플릿 또는 결과 페이지에서 페이지(main parsys)에 대한 [콘텐츠 정책](#content-policies)을 정의할 수 있습니다.

### 템플릿 사용 및 사용 허용 {#enabling-and-allowing-a-template-for-use}

1. **템플릿 사용**

   템플릿을 사용하려면 다음 방법 중 하나로 템플릿을 활성화해야 합니다.

   * **템플릿** 콘솔에서 [템플릿을 사용](/help/sites-cloud/authoring/sites-console/templates.md)합니다.

   * `jcr:content` 노드에서 상태 속성을 설정하는 중입니다.

      * 예를 들어,
        `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * 속성을 정의합니다.

         * 이름: 상태
         * 유형: 문자열
         * 값: `enabled`

1. **허용된 템플릿**

   * [하위 분기의 해당 페이지 또는 루트 페이지의 **페이지 속성**](/help/sites-cloud/authoring/sites-console/templates.md#allowing-a-template-author)&#x200B;에서 허용되는 템플릿 경로를 정의합니다.
   * 속성을 설정합니다.
     `cq:allowedTemplates`
필요한 분기의 `jcr:content` 노드에서.

   예를 들어, 값이 다음과 같은 경우:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## 결과 컨텐츠 페이지 {#resultant-content-pages}

편집 가능한 템플릿에서 만든 페이지:

* 템플릿의 `structure` 및 `initial`에서 병합된 하위 트리로 만듭니다.

* 템플릿 및 템플릿 유형에 보관된 정보에 대한 참조가 있습니다. 이 작업은 속성이 있는 `jcr:content` 노드에서 수행됩니다.

   * `cq:template` - 실제 템플릿에 대한 동적 참조를 제공합니다. 템플릿 변경 내용이 실제 페이지에 반영될 수 있도록 합니다.

   * `cq:templateType` - 템플릿 형식에 대한 참조를 제공합니다.

![템플릿, 콘텐츠 및 구성 요소의 상호 연결 방법](assets/templates-content-components.png)

위의 다이어그램은 템플릿, 콘텐츠 및 구성 요소가 상호 관련되는 방법을 보여 줍니다.

* 컨트롤러 - `/content/<my-site>/<my-page>` - 템플릿을 참조하는 결과 페이지입니다. 콘텐츠는 전체 프로세스를 제어합니다. 정의에 따라 적절한 템플릿과 구성 요소에 액세스합니다.
* 구성 - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - [템플릿 및 관련 콘텐츠 정책](#template-definitions)에서 페이지 구성을 정의합니다.
* 모델 - OSGi 번들 - [OSGI 번들](/help/implementing/deploying/configuring-osgi.md)에서 기능을 구현합니다.
* 보기 - `/apps/<my-site>/components` - 작성자 및 게시 환경 모두에서 콘텐츠는 구성 요소에 의해 렌더링됩니다.

페이지를 렌더링할 때:

* **템플릿**:

   * 해당 `jcr:content` 노드의 `cq:template` 속성이 해당 페이지에 해당하는 템플릿에 액세스하기 위해 참조됩니다.

* **구성 요소**:

   * 페이지 구성 요소는 템플릿의 `structure/jcr:content` 트리를 페이지의 `jcr:content` 트리와 병합합니다.
      * 페이지 구성 요소를 사용하면 작성자는 편집 가능 (및 모든 하위 항목)으로 플래그가 지정된 템플릿 구조의 노드만 편집할 수 있습니다.
      * 페이지에서 구성 요소를 렌더링할 때 해당 구성 요소의 상대 경로는 `jcr:content` 노드에서 가져옵니다. 그러면 템플릿의 `policies/jcr:content` 노드 아래에 있는 동일한 경로가 검색됩니다.
         * 이 노드의 `cq:policy` 속성은 실제 콘텐츠 정책을 가리킵니다(즉, 해당 구성 요소에 대한 디자인 구성을 보유함).
            * 이렇게 하면 동일한 콘텐츠 정책 구성을 다시 사용하는 여러 템플릿을 사용할 수 있습니다.

### 템플릿 가용성 {#template-availability}

사이트 관리 인터페이스에서 페이지를 만들 때 사용 가능한 템플릿 목록은 새 페이지의 위치와 각 템플릿에 지정된 배치 제한에 따라 다릅니다.

다음 속성은 템플릿 `T`을(를) 사용하여 새 페이지를 `P` 페이지의 하위 페이지로 배치할 수 있는지 여부를 결정합니다. 이러한 각 속성은 경로와의 일치에 사용되는 0개 이상의 정규 표현식을 포함하는 다중 값 문자열입니다.

* `P`의 `jcr:content` 하위 노드 또는 `P`의 상위 노드의 `cq:allowedTemplates` 속성입니다.

* `T`의 `allowedPaths` 속성입니다.

* `T`의 `allowedParents` 속성입니다.

* `P` 템플릿의 `allowedChildren` 속성입니다.

평가는 다음과 같이 작동합니다.

* `P`(으)로 시작하는 페이지 계층 구조를 오름차순으로 계산하는 동안 비어 있지 않은 첫 번째 `cq:allowedTemplates` 속성이 `T`의 경로에 대해 일치합니다. 일치하는 값이 없으면 `T`이(가) 거부됩니다.

* `T`에 비어 있지 않은 `allowedPaths` 속성이 있지만 `P`의 경로와 일치하는 값이 없으면 `T`이(가) 거부됩니다.

* 위의 두 속성이 모두 비어 있거나 존재하지 않으면 `T`은(는) `P`과(와) 같은 응용 프로그램에 속하지 않는 한 거부됩니다. `T` 경로의 두 번째 수준 이름이 `P` 경로의 두 번째 수준 이름과 동일한 경우에만 `T`이(가) `P`과(와) 동일한 응용 프로그램에 속합니다. 예를 들어 템플릿 `/apps/wknd/templates/foo`이(가) 페이지 `/content/wknd`과(와) 동일한 애플리케이션에 속합니다.

* `T`에 비어 있지 않은 `allowedParents` 속성이 있지만 `P`의 경로와 일치하는 값이 없으면 `T`이(가) 거부됩니다.

* `P`의 템플릿에 비어 있지 않은 `allowedChildren` 속성이 있지만 `T`의 경로와 일치하는 값이 없으면 `T`이(가) 거부됩니다.

* 다른 모든 경우에는 `T`이(가) 허용됩니다.

다음 다이어그램은 템플리트 평가 프로세스를 보여 줍니다.

![템플릿 평가 프로세스](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM은 **Sites**&#x200B;에서 허용되는 템플릿을 제어할 수 있는 여러 속성을 제공합니다. 하지만 이를 결합하면 추적 및 관리가 어려운 매우 복잡한 규칙이 발생할 수 있습니다.
>
>따라서 Adobe은 다음을 정의하여 단순하게 시작하는 것을 권장합니다.
>
>* `cq:allowedTemplates` 속성만
>
>* 사이트 루트에서만
>
>예를 들어 [WKND 튜토리얼](/help/implementing/developing/introduction/develop-wknd-tutorial.md) 내용: `/content/wknd/jcr:content`을(를) 참조하십시오.
>
>`allowedPaths`, `allowedParents` 및 `allowedChildren` 속성을 템플릿에 배치하여 보다 정교한 규칙을 정의할 수도 있습니다. 그러나 허용된 템플릿을 추가로 제한해야 하는 경우 가능한 경우 사이트의 하위 섹션에서 `cq:allowedTemplates` 속성을 추가로 정의하는 것이 *훨씬*&#x200B;입니다.
>
>**페이지 속성**&#x200B;의 **고급** 탭에서 작성자가 `cq:allowedTemplates` 속성을 업데이트할 수 있는 추가적인 이점이 있습니다. 다른 템플릿 속성은 (표준) UI를 사용하여 업데이트할 수 없으므로 개발자는 모든 변경 사항에 대한 규칙 및 코드 배포를 유지 관리해야 합니다.

#### 하위 페이지에 사용되는 템플릿 제한 {#limiting-templates-used-in-child-pages}

지정된 페이지에서 하위 페이지를 만드는 데 사용할 수 있는 템플릿을 제한하려면 페이지의 `jcr:content` 노드의 `cq:allowedTemplates` 속성을 사용하여 하위 페이지로 허용할 템플릿 목록을 지정하십시오. 목록의 각 값은 허용된 하위 페이지(예: `/apps/wknd/templates/page-content`)에 대한 템플릿의 절대 경로여야 합니다.

템플릿의 `jcr:content` 노드에서 `cq:allowedTemplates` 속성을 사용하여 이 템플릿을 사용하는 만들어진 모든 페이지에 이 구성을 적용할 수 있습니다.

템플릿 계층 구조와 관련하여 제한을 더 추가하려면 템플릿의 `allowedParents/allowedChildren` 속성을 사용할 수 있습니다. 그런 다음 템플릿 T에서 만든 페이지가 템플릿 T에서 만든 페이지의 상위/하위 페이지가 되도록 명시적으로 지정할 수 있습니다.
