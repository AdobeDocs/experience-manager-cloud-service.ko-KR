---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - Adobe Experience Manager as a Cloud Service 기초 준비 완료
description: 다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 기반 지원으로서 Adobe Experience Manager에 대해 알아보십시오. 에는 유럽 연합 개인 정보 보호 규정(GDPR), 캘리포니아 소비자 개인 정보 보호법 및 새 AEM을 Cloud Service 프로젝트로 구현할 때 준수하는 방법이 포함되어 있습니다.
exl-id: 3a4b9d00-297d-4b1d-ae57-e75fbd5c490c
source-git-commit: e4527b155179c50e1e423e7e835b3fcde3a4f2af
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Adobe Experience Manager은 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 기초 준비 완료 {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 컨텐츠는 법률적인 조언을 구성하지 않으며 법률적인 조언을 대체하지 않습니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 자세한 내용은 회사의 법무 부서에 문의하십시오.

>[!NOTE]
>
>개인 정보 보호 문제에 대한 Adobe의 응답 및 Adobe 고객으로서 사용자에게 의미하는 바에 대한 자세한 내용은 [Adobe의 개인 정보 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

## AEM Foundation 데이터 개인 정보 보호 및 보호 지원 {#aem-foundation-data-privacy-and-protection-support}

AEM Foundation 수준에서 저장된 개인 데이터는 사용자 프로필에 저장됩니다. 따라서 이 문서의 정보에서는 주로 사용자 프로필을 액세스 및 삭제하고 액세스 및 삭제 요청을 각각 처리하는 방법을 다룹니다.

## 사용자 프로필 액세스 {#accessing-a-user-profile}

### 수동 단계 {#manual-steps}

1. **[!UICONTROL 도구 - 보안 - 사용자]**&#x200B;로 이동하거나 `https://<serveraddress>:<serverport>/security/users.html`로 직접 이동하여 사용자 관리 콘솔을 엽니다

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. 그런 다음 페이지 상단의 검색 표시줄에 이름을 입력하여 해당 사용자를 검색합니다.

   ![계정 검색](assets/dpp-foundation-01.png)

1. 마지막으로 사용자 프로필을 클릭하여 연 다음 **[!UICONTROL 세부 정보]** 탭 아래에서 을 선택합니다.

   ![사용자 프로필](assets/dpp-foundation-02.png)

### HTTP API {#http-api}

앞에서 설명한 바와 같이, Adobe은 자동화를 용이하게 하기 위해 사용자 데이터에 액세스하기 위한 API를 제공합니다. 사용할 수 있는 API 유형에는 몇 가지가 있습니다.

**UserProperties API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling API**

**사용자 홈 살펴보기:**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**사용자 데이터 검색:**

위의 명령에서 반환된 JSON 페이로드의 홈 속성의 노드 경로 사용:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## 사용자 비활성화 및 관련 프로필 삭제 {#disabling-a-user-and-deleting-the-associated-profiles}

### 사용자 비활성화 {#disable-user}

1. 위에 설명된 대로 사용자 관리 콘솔을 열고 해당 사용자를 검색합니다.
2. 사용자를 마우스로 가리킨 다음 선택 아이콘을 클릭합니다. 프로필이 선택되었음을 나타내는 회색으로 바뀝니다.

3. 위쪽 메뉴에서 **Disable** 단추를 눌러 사용자를 비활성화합니다.

   ![계정 비활성화](assets/dpp-foundation-03.png)

4. 마지막으로 작업을 확인합니다.

   그러면 사용자 인터페이스에 프로필 카드에 잠금을 로그아웃하고 추가하여 사용자 계정이 비활성화되었음을 나타냅니다.

   ![계정 사용 안 함](assets/dpp-foundation-04.png)

### 사용자 프로필 정보 삭제 {#delete-user-profile-information}

>[!NOTE]
>
>AEM as a Cloud Service의 경우 CRXDE에 액세스할 수 없으므로 UI에서 사용자 프로필을 삭제하기 위한 수동 절차를 사용할 수 없습니다.

### HTTP API {#http-api-1}

다음 절차에서는 `curl` 명령줄 도구를 사용하여 **[!UICONTROL cavery]** `userId`로 사용자를 비활성화하고 기본 위치에서 사용할 수 있는 프로필을 삭제하는 방법을 보여 줍니다.

**사용자 홈 살펴보기:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**사용자 비활성화:**

위의 명령에서 반환된 JSON 페이로드의 홈 속성의 노드 경로 사용:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**사용자 프로필 삭제**

계정 검색 명령에서 반환된 JSON 페이로드의 홈 속성의 노드 경로 및 알려진 기본 프로필 노드 위치 사용:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
