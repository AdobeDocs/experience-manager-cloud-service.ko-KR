---
title: 업무 중지 시간 및 무료 기간 업데이트
description: 자동 체류 시간 및 업데이트 불가 기간을 사용하여 AEM as a Cloud Service 자동 업데이트의 운영상의 영향을 최소화하는 방법에 대해 알아봅니다.
feature: Deploying
role: Admin
badge: label="제한된 가용성" type="Positive"
exl-id: 54f86a58-eb56-43e6-ab51-7af7466a2d40
source-git-commit: aec58ceffbbc6c7e2921c471d608ed3c381fe2e4
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# 업무 중지 시간 및 무료 기간 업데이트 {#quiet-hours-update-free-periods}

>[!NOTE]
>이 기능은 9월 25일부터 **제한된 가용성** 기능으로 사용할 수 있습니다. 프로그램에서 기능을 활성화하려면 [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com)에 전자 메일을 보내십시오.

>[!WARNING]
>[자동 유지 관리 업데이트](/help/implementing/deploying/aem-version-updates.md)에 온보딩된 후에만 방해 금지 시간 및 자유 기간 업데이트 기능을 사용할 수 있습니다.

AEM as a Cloud Service [자동 유지 관리 업데이트](/help/implementing/deploying/aem-version-updates.md)를 통해 인스턴스가 최신 유지 관리 릴리스를 통해 최신 상태로 안전하게 유지될 수 있습니다. 즉, 일부 경우 (Go-Live 이벤트와 같은) 중요한 작업 시간을 잠재적인 중단으로부터 &quot;보호&quot;해야 할 수도 있습니다. 따라서 AEM as a Cloud Service에서는 진행 중인 프로그램에 대해 자동 업데이트가 수행되지 않는 시간대를 설정할 수 있는 옵션을 제공합니다.

다음 두 가지 예약 옵션을 사용하여 이러한 시간대를 구성할 수 있습니다.

* **방해 금지 시간** - 업데이트가 발생하지 않는 일별 시간 간격(최대 8시간)을 정의할 수 있습니다.
* **무료 기간 업데이트** - 업데이트가 발생하지 않는 7일 기간을 정의할 수 있습니다. 12개월 기간 내에 최대 3개의 무료 업데이트 기간을 가질 수 있습니다.

무료 기간 및 자동 시간 업데이트 기능은 &quot;프로그램별&quot;로 구성됩니다.

또한 예약된 AEM as a Cloud Service 자동 유지 관리 기간에 대한 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/ko/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) 페이지를 참조하십시오.

## 방해 금지 시간 {#quiet-hours}

자동 업데이트 없이 하루 동안의 시간 창을 정의할 수 있습니다. 모든 유지 보수 업데이트는 구성된 시간 범위를 벗어나서 실행되도록 전환됩니다. 예를 들어, 지정된 자동 시간 동안 업데이트가 예약되면 자동 시간 간격이 종료된 후에 자동으로 시작됩니다. 업데이트가 매일 발생할 수 있도록 구성된 시간 간격은 8시간을 초과할 수 없습니다.

로컬 시간대를 사용하여 **프로그램당**&#x200B;의 방해 금지 시간을 정의할 수 있습니다.

### 자동 시간 간격을 구성하는 방법 {#configure-quiet-hours}

AEM Cloud Manager 인터페이스를 사용하여 자동 시간 간격을 다음과 같이 구성할 수 있습니다.

**활동>자동 업데이트>업데이트 옵션**(으)로 이동합니다.

![구성](assets/main-config.png)

1. **특정 시간 동안 자동 업데이트 금지** 옵션이 전환되어 있는지 확인하십시오.
2. **편집**&#x200B;을 클릭합니다.
3. 구성 창에서 자동 시간 간격을 설정합니다.

![방해 금지 모드 구성](assets/quiet-hours.png)

설정되면, 지정한 시작 및 종료 시간이 앞으로 이동할 모든 역일에 적용됩니다. 필요에 따라 저소음 시간 값을 비활성화하거나 다시 구성할 수 있습니다.

## 자유 기간 업데이트 {#update-free-periods}

무료 기간 업데이트 기능을 사용하여 업데이트가 발생하지 않는 7일 기간을 정의할 수 있습니다. 구성되면 모든 유지 보수 업데이트는 정의된 시간대 외부에서 발생하도록 자동으로 이동됩니다. 12개월 간격 내에 최대 3개의 무료 업데이트 기간을 가질 수 있습니다. 또한 업데이트 자유 기간은 최대 1년 전에 지정할 수 있습니다.

자동 업데이트를 용이하게 하기 위해 기간 간 1주 이상의 시간 간격이 필수라는 점을 이 옵션을 구성할 때 염두에 두십시오. 따라서 이 1주 시간 간격은 자동으로 적용되며 사용자가 구성한 업데이트 사용 가능 기간 사이의 달력에 추가됩니다. 이로 인해 일부 일정은 선택할 수 없습니다.

**프로그램당** 무료 기간 업데이트를 정의할 수 있습니다.

### 업데이트 사용 가능 기간을 구성하는 방법 {#configure-update-free-periods}

자유 기간 업데이트 기능은 다음과 같이 AEM Cloud Manager 인터페이스를 사용하여 구성할 수 있습니다.

**활동>자동 업데이트>업데이트 옵션**(으)로 이동합니다.

![구성](assets/main-config.png)

1. 자유 기간 업데이트 섹션으로 이동합니다.
2. **업데이트 사용 가능 기간 추가**&#x200B;를 클릭합니다.
3. 달력에서 1주 갱신 자유 기간을 선택합니다.

![사용 가능 기간 구성 업데이트](assets/update-free-periods.png)

**활성** 아이콘은 현재 활성 업데이트 사용 가능 기간 근처에 표시되고 **완료** 아이콘은 완료된 업데이트 사용 가능 기간 근처에 표시됩니다.
