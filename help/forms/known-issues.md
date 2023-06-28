---
title: 알려진 문제 및 제한 사항
description: 의 알려진 문제 및 제한 사항  [!DNL AEM Forms] as a Cloud Service 환경
contentOwner: khsingh
role: User, Developer
level: Intermediate
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 63f6e7c6df7404062aa0d209496506bdabcf564c
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 10%

---

# 알려진 문제 및 제한 사항 {#known-issues-and-limitations}

사용을 시작하기 전에 [!DNL AEM Forms] as a Cloud Service으로 다음 알려진 문제 및 제한 사항을 검토하십시오.

## 알려진 문제 {#known-issues}

* 게시 인스턴스에서 작성자 인스턴스에서 실행 중인 AEM Workflow로 적응형 양식을 제출하는 테스트를 추가 및 실행하지 마십시오.

* 다음을 포함하는 템플릿을 사용하는 적응형 양식을 가져올 때 **[!UICONTROL 저장]** 단추, **[!UICONTROL 저장]** 해당 템플릿에서 제거된 후에도 버튼이 적응형 양식에 계속 표시됩니다. 제거 **[!UICONTROL 저장]** 게시하기 전에 적응형 Forms에서 버튼을 클릭합니다. Forms 포털의 가용성에 대한 릴리스 정보를 주시하고, 초안으로 저장 기능을 사용하여 복원하고 버튼을 사용합니다.

* 다음 **[!UICONTROL 변수 설정]** AEM 워크플로의 단계는 배열 유형 목록의 변수를 지원하지 않습니다. 프로세스 단계를 사용하여 배열 유형 목록의 변수를 설정할 수 있습니다.

* Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 적응형 양식을 제출하면 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. 이 문제는 동기식 제출을 사용하는 경우에만 간헐적으로 발생합니다. (이)는 [알려진 문제](https://feedbackassistant.apple.com/feedback/9117687) Apple iOS에서.

* Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 양식을 제출할 때 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신되는 경우가 있습니다. 이 문제는 Apple iOS에서 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

* AEM Forms as a Cloud Service은 XDP 및 JSON 스키마 파일에 대한 썸네일을 생성하지 않습니다. 서비스는 썸네일 대신 기본 아이콘을 표시합니다.

  ![Forms 썸네일 알려진 문제](/help/forms/assets/forms-tumbnail-known-issue.png)

* 반복 가능한 요소가 포함된 스키마를 사용하여 적응형 양식 기반의 핵심 구성 요소를 만드는 경우 적응형 Forms 편집기의 데이터 모델 트리에서 반복 가능한 요소를 드래그 앤 드롭하는 옵션이 작동하지 않습니다.

## 제한 사항 {#limitations}

* XFA 기반 적응형 양식에 대한 지원은 즉시 사용할 수 없습니다. XFA 기반 적응형 양식을 사용하려는 경우 Adobe 지원 팀에 문의하여 사용 사례 및 특정 요구 사항에 대해 자세히 알아보십시오.

