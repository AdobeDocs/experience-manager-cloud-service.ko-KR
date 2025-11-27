---
title: HTML5 양식 시작하기
description: 시작하려면 AEM Forms 추가 기능 패키지를 배포하고 기존 HTML5 양식을 AEM으로 가져오십시오.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: f276d150-8936-4bfb-8475-7ca36815b233
feature: HTML5 Forms,Mobile Forms
exl-id: a3245f05-6ea3-4f90-8981-bfa89d2e7335
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 4%

---

# HTML5 양식 시작하기 {#getting-started-with-html-forms}

<span class="preview"> HTML5 Forms 기능은 조기 액세스 프로그램의 일부로 제공됩니다. 액세스 권한을 요청하려면 공식(회사) 이메일 ID에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오.
</span>

HTML5 forms는 모바일에서 사용할 수 있는 다양한 기능을 제공합니다. HTML5 브라우저를 사용하여 현재 솔루션 및 워크플로를 태블릿 또는 스마트폰 장치로 확장하는 데 도움이 됩니다. 일부 기능은 다음과 같습니다.

* **HTML5 기반 XFA 양식 서식 파일 렌더링:** 이제 일반 PDF forms 외에도 기존 XFA 기반 양식을 HTML5 형식으로 렌더링할 수 있습니다. 이는 HTML5를 지원하고 XFA Forms이 있는 Adobe Reader를 지원하지 않는 모바일 장치(Apple iPad, Android 태블릿, 스마트폰 등)로 클라이언트 플랫폼을 확장하는 데 도움이 됩니다. HTML5 기반 렌더링 기능에 대한 자세한 내용은 [HTML5 양식 소개](/help/forms/introductionhtml5.md)를 참조하십시오.

* **Forms 관리:** 또한 AEM에는 양식 구성 및 관리 프로세스를 간소화하는 새로운 기능이 포함되어 있습니다. 양식을 활성화, 비활성화, 게시 및 미리 볼 수 있습니다.<!--For more information, see [Introduction to managing forms](/help/forms/using/introduction-managing-forms.md).-->

## HTML5 forms에 대한 환경 구성 {#installing-html-forms}

HTML5 Forms의 양식 제출 및 적절한 렌더링을 활성화하려면 다음 단계를 수행하십시오.

* **Dispatcher 필터 추가:** HTML5 Forms에 필요한 요청을 허용하도록 `src/conf.dispatcher.d/filters/filters.any` 파일을 업데이트합니다. 다음 필터 규칙을 추가합니다.

  ```
  /0103 { /type "allow" /method '(HEAD|POST)' /url "/content/xfaforms/profiles/default.submit.html" }  # allow POSTs to form selectors under content
  /0104 { /type "allow" /method '(GET|HEAD|POST)' /url "/*.xdp.html" }
  ```

* **제출용 패키지 추가:** 프로젝트에서 `src/main/content/jcr_root/content` 폴더에 패키지를 추가하여 양식 제출 기능을 지원합니다.

* **HTML 가져오기5 Forms:** 로컬 파일 시스템에서 AEM Forms으로 양식을 가져옵니다.
