---
title: 범용 편집기를 사용하여 양식 만들기
description: API 통합을 사용하여 계단식 드롭다운 목록을 테스트하기 위한 적응형 양식 만들기
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: ht
source-wordcount: '202'
ht-degree: 100%

---

# 범용 편집기를 사용하여 양식 만들기

범용 편집기를 사용하여 다음 양식을 만듭니다. 양식에는 API 통합을 사용하여 값을 채우는 3개의 드롭다운 목록이 있습니다.
![적응형 양식](assets/address-form.png)

## 거주 국가

초기화되면 거주 국가 드롭다운 목록이 API 호출 결과로 채워집니다.
![initialize-event](assets/initialize-event.png)

## 성공 핸들러

성공 핸들러는 geonames 배열의 적절한 값으로 국가 드롭다운 목록의 enum 및 enumNames를 설정하도록 정의되었습니다. geonames 배열은 이벤트 페이로드 옵션 아래에서 사용할 수 있습니다.
![event-payload](assets/event-payload.png)
![success-handler](assets/success-handler.png)

## 하위 값 가져오기

주 또는 시/도 드롭다운 목록은 사용자가 거주 국가 드롭다운 목록에서 선택할 때 채워집니다. 선택한 국가와 연결된 geonameId가 입력 매개변수로서 GetChildren API 통합에 전달됩니다.

![get-children](assets/invoke-service-get-children.png)

성공 핸들러는 StateOrProvince 드롭다운 필드의 enum/enumNames를 설정하도록 정의되었습니다.
![get-children-success-handler](assets/child-success-handler.png)

주 또는 시/도를 선택하면 위에서 언급한 주 또는 시/도 드롭다운 목록을 채우는 데 사용된 패턴을 따라 도시 드롭다운 목록을 채울 수 있습니다.