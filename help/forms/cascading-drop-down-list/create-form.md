---
title: 범용 편집기를 사용하여 양식 만들기
description: 적응형 Forms 표현식을 사용하여 자동 유효성 검사, 계산을 추가하고 섹션의 가시성을 켜거나 끕니다.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: cc3cd74ad87f4213a200f36745ab3d335edca02d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 67%

---

# 범용 편집기를 사용하여 양식 만들기

범용 편집기를 사용하여 다음 양식을 만듭니다. 양식에는 API 통합을 사용하여 값을 채우는 3개의 드롭다운 목록이 있습니다
![적응형 양식](assets/address-form.png)

## 거주 국가

초기화되면 거주 국가 드롭다운 목록이 API 호출 결과로 채워집니다.
![initialize-event](assets/initialize-event.png)

## 성공 핸들러

성공 핸들러는 geonames 배열의 적절한 값으로 국가 드롭다운 목록의 enum 및 enumNames를 설정하도록 정의되었습니다. 지리 이름 배열은 이벤트 페이로드 옵션에서 사용할 수 있습니다.
![이벤트 페이로드](assets/event-payload.png)
![성공 처리기](assets/success-handler.png)

## 하위 값 가져오기

주 또는 시/도 드롭다운 목록은 사용자가 거주 국가 드롭다운 목록에서 선택할 때 채워집니다. 선택한 국가와 연결된 geonameId가 입력 매개변수로서 GetChildren API 통합에 전달됩니다.

![get-children](assets/invoke-service-get-children.png)

성공 처리기는 StateOrProvince 드롭다운 필드의 enum/enumNames를 설정하도록 정의되었습니다.
![get-children-success-handler](assets/child-success-handler.png)

주 또는 시/도를 선택하면 위에서 언급한 주 또는 시/도 드롭다운 목록을 채우는 데 사용된 패턴을 따라 도시 드롭다운 목록을 채울 수 있습니다.