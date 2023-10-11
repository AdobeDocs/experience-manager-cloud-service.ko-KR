---
title: AEM Forms as a Cloud Service 환경의 알려진 문제와 제한 사항은 무엇입니까?
description: ' [!DNL AEM Forms] as a Cloud Service 환경의 알려진 문제 및 제한 사항.'
contentOwner: khsingh
role: User, Developer
level: Intermediate
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 95%

---

# 알려진 문제 및 제한 사항 {#known-issues-and-limitations}

[!DNL AEM Forms] as a Cloud Service 사용을 시작하기 전에 다음과 같은 알려진 문제 및 제한 사항을 검토하십시오.

## 알려진 문제 {#known-issues}

* 추가 공지가 있을 때까지 게시 인스턴스에서 작성자 인스턴스에서 실행 중인 AEM 워크플로에 적응형 양식을 제출하는 테스트를 추가하고 실행하지 마십시오.

* **[!UICONTROL 저장]** 버튼이 포함된 템플릿을 사용하는 적응형 양식을 가져오면 해당 템플릿에서 제거된 후에도 **[!UICONTROL 저장]** 버튼이 적응형 양식에 계속 표시됩니다. 게시하기 전에 적응형 양식에서 **[!UICONTROL 저장]** 버튼을 제거합니다. 버튼을 복원하고 사용하려면 Forms 포털 및 초안으로 저장 기능의 가용성에 대한 릴리스 정보를 참고하십시오.

* AEM 워크플로의 **[!UICONTROL 변수 설정]** 단계는 배열 목록의 변수 유형을 지원하지 않습니다. 프로세스 단계를 사용하여 배열 목록의 변수 유형을 설정할 수 있습니다.

* Apple iOS 디바이스에서 표준 HTML 업로드 필드가 포함된 적응형 양식을 제출할 경우, 때때로 파일 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. 이 문제는 동기식 제출을 사용하는 경우에만 간헐적으로 발생합니다. 이는 Apple iOS의 [알려진 문제](https://feedbackassistant.apple.com/feedback/9117687)입니다.

* Apple iOS 디바이스에서 표준 HTML 업로드 필드가 포함된 양식을 제출할 경우, 때때로 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. 이는 Apple iOS의 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

* AEM Forms as a Cloud Service는 XDP 및 JSON 스키마 파일에 대한 썸네일을 생성하지 않습니다. 이 서비스는 썸네일 대신 기본 아이콘을 표시합니다.

  ![Forms 썸네일 알려진 문제](/help/forms/assets/forms-tumbnail-known-issue.png)

* 반복 가능한 요소가 있는 스키마를 사용하여 핵심 구성 요소 기반의 적응형 양식을 생성하는 경우, 적응형 양식 편집기의 데이터 모델 트리에서 반복 가능한 요소를 끌어다 놓는 옵션이 작동하지 않습니다.

## 제한 사항 {#limitations}

* XFA 기반 적응형 양식에 대한 지원은 즉시 사용할 수 없습니다. XFA 기반 적응형 양식을 사용하려는 경우 Adobe 지원 팀에 문의하여 사용 사례 및 특정 요구 사항에 대해 자세히 알아보십시오.

