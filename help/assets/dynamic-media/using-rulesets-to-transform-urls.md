---
title: 규칙 세트를 사용하여 URL 변환
description: 'Dynamic Media에서 규칙 세트를 배포하여 URL을 변환할 수 있습니다. 규칙 세트는 XML 데이터를 평가하고 특정 조건을 충족하는 경우 특정 작업을 수행하는 스크립팅 언어(예: JavaScript)로 작성된 지침 세트입니다.'
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# 규칙 세트를 사용하여 URL 변환 {#using-rulesets-to-transform-urls}

Dynamic Media에서 규칙 세트를 배포하여 URL을 변환할 수 있습니다. 규칙 세트는 XML 데이터를 평가하고 특정 조건을 충족하는 경우 특정 작업을 수행하는 스크립팅 언어(예: JavaScript)로 작성된 지침 세트입니다. 각 규칙은 하나 이상의 조건과 하나 이상의 작업으로 구성됩니다. 규칙은 조건에 대해 XML 데이터를 평가하고 조건이 충족되면 적절한 작업을 수행합니다. 규칙 세트의 예는 다음과 같습니다.

* MIME 유형 접미사를 추가합니다. 많은 서비스 및 웹 사이트에서 URL에 추가하는 것과 같은 이미지 접미어를 필요로 `.jpg` 합니다.
* SEO용 URL의 폴더 경로 만들기(검색 엔진 최적화) 목적

   Adobe [Scene7 Publishing System에서 SEO를 지원하는 방법을 참조하십시오](/help/assets/dynamic-media/assets/s7_seo.pdf).

* SEO를 위한 URL에 메타데이터 추가(검색 엔진 최적화) 목적

   Adobe [Scene7 Publishing System에서 SEO를 지원하는 방법을 참조하십시오](/help/assets/dynamic-media/assets/s7_seo.pdf).

* 다운로드를 트리거하는 컨텐츠 처리 설정
* 개인화를 위한 이미지 제공 템플릿 URL을 간소화할 수 있습니다. 예를 들어, RTF `rgb{XX,YY,ZZ}` 로 변환 `\redXX\greenYY\blueZZ`

* ImageServer에 디코딩할 특정 문자, `$``{`, `}`특정 문자 등과 같이 인코딩할 특정 문자를 요청합니다. 예를 들어, Facebook은 특수 문자가 포함된 URL과 잘 작동하지 않습니다.

   URL [에서 특수 문자 제거를 참조하십시오](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/remove-special-characters-urls.html).

다이내믹 미디어 컨텍스트에서 XML 기반 시스템을 사용하여 자산 정보를 관리하는 웹 사이트는 XML 파일을 다이내믹 미디어에 업로드할 수 있습니다. 이러한 파일 중 하나를 Dynamic Media 자산을 제공하기 위한 사전 처리 규칙 세트 파일로 지정할 수 있습니다. 이 파일은 Dynamic Media와 통합된 시스템의 비즈니스 로직을 충족하기 위해 표준 URL 프로토콜 형식을 재구성합니다. 규칙 세트 정의 파일 경로로 사용할 XML 파일을 지정합니다.

>[!CAUTION]
>
>규칙 세트를 사용할 때는 주의하십시오.다이내믹 미디어 컨텐츠가 웹 사이트에 표시되지 않도록 할 수 있습니다.

고유한 규칙 세트를 만드는 데 도움이 되는 샘플 규칙 세트가 있습니다.
규칙 [세트 참조를](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/image_catalog/c_rule_set_reference.html)참조하십시오.

모든 규칙 세트 생성과 마찬가지로 XML 파일을 업로드하기 전에 xmlvalid와 같은 XML 유효성 검사기 프로그램을 사용하여 XML 파일이 유효한지 확인합니다.
규칙 [세트](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/scene7-ruleset-troubleshooting.html)문제 해결을 참조하십시오.

또한 먼저 라이브 프로덕션 환경에 영향을 주지 않는 스테이징 환경에서 규칙 세트를 테스트해야 합니다.
프로덕션 환경과 스테이징 환경에서는 일반적으로 다른 로그인이 필요합니다.

* **스테이징 환경** 로그인 페이지: [https://s7sps1-staging.scene7.com/IpsWeb/](https://s7sps1-staging.scene7.com/IpsWeb/)
* **EMEA 스테이징 환경** 로그인 페이지: [https://s7sps3-staging.scene7.com/IpsWeb/](https://s7sps3-staging.scene7.com/IpsWeb/)
* **JAPAC 스테이징 환경** 로그인 페이지: [https://s7sps5-staging.scene7.com/IpsWeb/](https://s7sps5-staging.scene7.com/IpsWeb/)

규칙 [세트에서](https://helpx.adobe.com/experience-manager/scene7/kb/base/scene7-rulesets/ruleset-asset-instead-image.html)&#39;is&#39; 이미지 대신 &#39;asset&#39; 사용을 참조하십시오.

**XML 규칙 세트를 배포하려면**

1. Dynamic Media Classic 계정에 로그온합니다.

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   자격 증명 및 로그온은 제공 당시 Adobe에서 제공했습니다. 이 정보가 없는 경우 기술 지원에 문의하십시오.

1. 다음을 수행하여 규칙 세트 파일을 업로드합니다.

   * 전역 탐색 막대에서 업로드를 **[!UICONTROL 클릭합니다]**.
   * 업로드 **[!UICONTROL 페이지의]** 왼쪽 위 모서리 근처에서 찾아보기를 **[!UICONTROL 클릭합니다]**.
   * 열기 **[!UICONTROL 대화]** 상자에서 규칙 세트 파일(XML)을 찾습니다.
   * 파일을 선택한 다음 열기를 **[!UICONTROL 클릭합니다]**.
   * 업로드 페이지 오른쪽에서 **[!UICONTROL 규칙]** 세트 파일의 대상 폴더를 선택합니다.
   * 페이지 하단에서 업로드 후 **[!UICONTROL 게시가]** 선택되어 있는지 확인합니다.
   * 페이지 오른쪽 하단에서 업로드 제출을 **[!UICONTROL 클릭합니다]**.
   * 글로벌 탐색 막대에서 **[!UICONTROL 작업을]** 클릭하여 업로드 작업의 상태를 확인합니다. 작업 **[!UICONTROL 페이지의]** 상태 **[!UICONTROL 열에]** [업로드 완료]메시지가 표시되면 다음 단계를 계속 수행합니다.

1. 페이지 상단 근처에 있는 탐색 막대에서 설정 > 응용 프로그램 **[!UICONTROL 설정 > 게시 설정 > 이미지 서버를 클릭합니다]**.
1. [이미지 **[!UICONTROL 서버 게시] 페이지의 [카탈로그 관리]** ] **[!UICONTROL 그룹에서]** **[!UICONTROL 규칙 세트 정의 파일 경로를]**&#x200B;찾은 다음 **[!UICONTROL 선택을]**&#x200B;클릭합니다.
1. 규칙 **[!UICONTROL 세트 정의 파일(XML)]** 선택 페이지에서 규칙 세트 파일을 찾은 다음 페이지의 오른쪽 아래에 있는 선택을 **[!UICONTROL 클릭합니다]**.
1. 설정 페이지의 오른쪽 아래에 있는 닫기를 **[!UICONTROL 클릭합니다]**.
1. 이미지 서버 게시 작업을 실행합니다.

   규칙 세트 조건은 라이브 다이내믹 미디어 이미지 서버에 대한 요청에 적용됩니다.

   규칙 세트 파일을 변경하면 업데이트된 규칙 세트 파일을 다시 업로드하고 다시 게시할 때 변경 내용이 즉시 적용됩니다.

