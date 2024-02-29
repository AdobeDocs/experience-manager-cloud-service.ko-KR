---
title: AEM Forms Edge 게재 서비스 양식 구성 요소
description: 최고 성능을 위해 구축된 AEM Forms Edge Delivery Service를 통해 향후 간소화된 데이터 수집 및 사용자 참여를 구상할 수 있습니다. 이 문서에서는 EDD 양식에 즉시 사용할 수 있는 모든 양식 구성 요소를 나열합니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 5%

---




# 양식 블록 에지 게재에서 지원되는 HTML 구성 요소

AEM Forms Edge 게재에는 양식 블록이 포함되어 있습니다. 양식 블록을 사용하면 캡처한 데이터를 캡처하고 저장할 양식을 쉽게 만들 수 있습니다.

양식 블록은 텍스트, 이메일, 번호, 날짜 등과 같은 OOTB HTML-5 구성 요소를 지원합니다. 또한 텍스트 영역, 선택 및 필드 세트 요소를 지원하며 HTML-5의 기본인 입력 유효성 검사 기능을 포함합니다. 양식 블록은 일관성을 보장하기 위해 모든 필드 유형 및 컨테이너에 대해 균일한 HTML 구조를 생성합니다. 귀하도 [필드 유형 스타일 지정](https://adobe-rnd.github.io/form-block/customization/styling_form) 사용 `form.css` 파일.

## 양식 블록에서 지원되는 HTML 5 입력 유형

양식 블록은 다양한 HTML 5 입력 유형을 지원하며 AEM 핵심 구성 요소로 만든 양식을 원활하게 렌더링합니다.

다음은 Edge Delivery에서 핵심 구성 요소가 HTML 5 입력 유형에 대응하는 방법을 간략하게 설명하는 표입니다.

<table>
 <tbody>
  <tr>
   <td><b>핵심 구성 요소</b> </td>
   <td><b>HTML 5 입력 유형</b> </td>
   <td><b>세부 사항</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">양식 컨테이너</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">양식 </td>
   <td> 사용자 입력을 캡처할 양식을 만듭니다.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">텍스트 입력</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> 한 줄 텍스트 입력 필드를 정의합니다. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">숫자 입력</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">숫자</a></td>
   <td>사용자가 숫자 입력을 입력할 수 있습니다. 내장된 유효성 검사를 추가하여 숫자가 아닌 입력을 거부할 수도 있습니다. 사용자가 숫자 입력을 입력할 수 있습니다. 내장된 유효성 검사를 추가하여 숫자가 아닌 입력을 거부할 수도 있습니다. 처음에는 입력 필드가 숫자 입력으로 표시됩니다. HTML 5에서는 표시 패턴을 지원하지 않으므로 사용자가 표시 패턴을 적용하면 작성자가 숫자 서식을 적용할 수 있도록 텍스트가 변경됩니다. 그러나 사용자가 클릭하면 숫자를 다시 입력하게 됩니다.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">날짜 선택기</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">날짜 </a></td>
   <td> 날짜 입력을 위한 입력 필드를 만듭니다. 입력을 검증하는 텍스트 상자를 통해 또는 전용 날짜 선택기 인터페이스를 통해 날짜를 입력할 수 있습니다. 처음에는 기본 날짜 입력 필드가 표시됩니다. 사용자가 표시 패턴을 적용하면 HTML 5가 표시 패턴을 지원하지 않으므로 사용자가 서식을 적용할 수 있도록 텍스트로 변경됩니다. 그러나 사용자가 클릭하면 날짜를 다시 입력하게 됩니다.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">첨부 파일</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">파일</a></td>
   <td> 사용자가 장치 저장소에서 하나 이상의 파일을 선택할 수 있습니다. 허용되는 파일 형식, 파일 크기 제한, 최소/최대 파일 선택 제한 등 향상된 파일 입력 유효성 검사를 지원합니다. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> 드롭다운 목록</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">선택</a></td>
   <td> 사용자가 사전 정의된 옵션 목록에서 하나 이상의 옵션을 선택할 수 있습니다. 옵션은 문자열, 숫자 또는 부울 유형일 수 있습니다.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">확인란 그룹</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">다중 확인란</a></td>
   <td> 사용자가 목록에서 옵션을 하나 이상 선택할 수 있도록 허용합니다. 열거형의 항목에 각각 해당하는 동일한 이름의 확인란이 여러 개 생성됩니다. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">라디오 단추 그룹</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">여러대의 라디오</a></td>
   <td> 사용자가 관련 옵션 그룹에서 하나의 옵션을 선택할 수 있습니다. 열거형의 항목에 각각 해당하는 동일한 이름으로 여러 라디오 단추가 생성됩니다.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">버튼</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">단추</a></td>
   <td>사용자가 클릭할 때 작업을 트리거할 수 있는 UI 요소입니다. </td>
  </tr>
  <tr>
   <td><a href="" https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">패널</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">범례가 있는 필드 세트</a></td>
   <td> 중첩된 *범례* 요소가 양식에 대한 캡션을 추가하는 양식 내의 섹션을 그룹화합니다.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">마법사</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">필드 세트</a></td>
   <td>양식 내에서 관련 섹션을 그룹화합니다. 또한 배열을 제어하여 맨 위나 왼쪽에 배치하기 위한 디스플레이 옵션을 지원합니다. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">텍스트</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>p 태그는 단락을 표시합니다. 시각적 콘텐츠에서 단락은 빈 줄이나 들여쓴 첫 줄로 구분된 텍스트 청크입니다</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">제출 버튼</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">제출</a></td>
   <td> 사용자가 클릭 시 서버에 양식을 제출할 수 있도록 해 주는 UI 요소입니다. 사용자가 버튼에 제출 규칙을 추가하면 제출 버튼의 기능을 합니다. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">재설정 버튼</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">재설정</a></td>
   <td>클릭 시 양식을 재설정하는 UI 요소입니다. 사용자가 버튼에 재설정 규칙을 추가하면 이는 재설정 버튼으로서 기능한다. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">이메일 입력</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">이메일</a></td>
   <td> 사용자가 이메일 주소를 입력하고 편집할 수 있습니다. 사용자가 여러 속성을 추가하는 경우 이메일 주소 목록을 추가하거나 편집할 수 있습니다.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">전화 입력</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">전화</a></td>
   <td>사용자가 전화 번호를 입력하고 편집할 수 있습니다.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">헤더</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> 머리글</a></td>
   <td>여기에는 입문 내용, 일반적으로 입문 또는 항해 보조제의 그룹이 포함됩니다. 양식 컨테이너 외부에서 지원됩니다. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">바닥글</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">꼬리말</a></td>
   <td> 저작권 데이터 또는 관련 문서에 대한 링크와 같은 정보를 포함합니다. 양식 컨테이너 외부에서 지원됩니다.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">아코디언<a></td>
   <td><i>아직 양식 블록에서 지원되지 않음</i></td>
   <td> 사용자가 양식에서 확장 및 축소 가능한 섹션을 만들 수 있습니다. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">가로 탭</a></td>
   <td><i>아직 양식 블록에서 지원되지 않음</i></td>
   <td>양식의 여러 섹션을 가로로 표시되는 별도의 탭으로 구성합니다.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">이미지</a></td>
   <td><i>아직 양식 블록에서 지원되지 않음</i></td>
   <td> 사용자가 양식에 이미지를 포함할 수 있습니다.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">제목</a></td>
   <td><i>아직 양식 블록에서 지원되지 않음</i></td>
   <td> 폼의 맨 위에 나타나는 텍스트를 나타냅니다. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">전환</td>
   <td><i>아직 양식 블록에서 지원되지 않음</i></td>
   <td> 기능, 설정 또는 기능 활성화/비활성화와 같은 두 상태 중에서 선택할 수 있는 두 상태 토글.</td>
  </tr>
 </tbody>
</table>


