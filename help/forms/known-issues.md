---
title: 알려진 문제 및 제한 사항
description: 의 알려진 문제 및 제한 사항  [!DNL AEM Forms] as a Cloud Service 환경
contentOwner: khsingh
role: User, Developer
level: Intermediate
topic: Administration
exl-id: 871f294d-f251-4966-a021-39df65b613f0
source-git-commit: 94825e3b60d970fec5bf696d932ca66bb83fd2f3
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 11%

---

# 알려진 문제 및 제한 사항 {#known-issues-and-limitations}

사용하기 전에 [!DNL AEM Forms] as a Cloud Service, 다음의 알려진 문제 및 제한 사항을 검토하십시오.

## 알려진 문제 {#known-issues}

* 추가적인 통지가 있을 때까지 게시 인스턴스에서 작성자 인스턴스에서 실행되는 AEM Workflow에 적응형 양식을 제출하는 테스트를 추가 및 실행하지 마십시오.

* 를 포함하는 템플릿을 사용하는 적응형 양식을 가져올 때 **[!UICONTROL 저장]** 버튼, **[!UICONTROL 저장]** 해당 템플릿에서 단추가 제거되더라도 적응형 양식에 계속 나타납니다. 제거 **[!UICONTROL 저장]** 게시하기 전에 적용형 Forms에서 단추를 클릭합니다. Forms Portal과 초안으로 저장 기능을 사용하여 해당 단추를 복원 및 사용할 수 있는지 릴리스 노트를 확인해 보십시오.

* 다음 **[!UICONTROL 변수 설정]** AEM Workflows의 단계는 배열 목록 유형의 변수를 지원하지 않습니다. 프로세스 단계를 사용하여 유형 배열 목록의 변수를 설정할 수 있습니다.

* Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 적응형 양식을 제출하면 파일의 컨텐츠가 전송되지 않고, 다른 끝에는 0바이트 파일이 수신됩니다. 이 문제는 간헐적으로 그리고 동기 전송 사용 시에만 발생합니다. 이것은 [알려진 문제](https://feedbackassistant.apple.com/feedback/9117687) Apple iOS.

* Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 양식을 제출하는 경우 때로 파일의 컨텐츠가 전송되지 않고 다른 끝에는 0바이트 파일이 수신됩니다. Apple iOS에서 알려진 문제입니다. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

* AEM Forms as a Cloud Service은 XDP 및 JSON 스키마 파일에 대한 축소판을 생성하지 않습니다. 축소판 대신 기본 아이콘이 표시됩니다.

   ![Forms 축소판 그림 알려진 문제](/help/forms/assets/forms-tumbnail-known-issue.png)


## 제한 사항 {#limitations}

* XFA 기반 적응형 양식에 대한 지원은 즉시 사용할 수 없습니다. XFA 기반 적응형 양식을 사용하려는 경우 Adobe 지원 팀에 문의하여 사용 사례 및 특정 요구 사항에 대해 자세히 알아보십시오.

