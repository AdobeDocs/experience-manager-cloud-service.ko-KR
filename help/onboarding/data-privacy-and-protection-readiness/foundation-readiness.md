---
title: 데이터 보호 및 데이터 개인 정보 보호 규정 - Adobe Experience Manager을 Cloud Service 기반 준비
description: '다양한 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 기반 지원으로서 Adobe Experience Manager에 대해 알아보십시오.여기에는 EU 개인 정보 보호 규정(GDPR), 캘리포니아 소비자 개인 정보 보호 법(California Consumer Privacy Act) 및 새로운 AEM을 Cloud Service 프로젝트로 구현할 때의 준수 방법이 포함되어 있습니다. '
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Adobe Experience Manager은 데이터 보호 및 데이터 개인 정보 보호 규정에 대한 Cloud Service 기반 준비 사항 {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>이 문서의 내용이 법률적 조언을 의미하지 않으며 법적 조언을 대체하기 위한 것이 아니다.
>
>데이터 보호 및 데이터 개인 정보 보호 규정에 대한 정보는 회사의 법무팀에 문의하십시오.

>[!NOTE]
>
>개인정보 보호 문제에 대한 Adobe의 응답과 Adobe 고객으로서 사용자에게 의미하는 바를 자세히 알아보려면 [Adobe의 개인 정보 보호 센터](https://www.adobe.com/privacy.html)를 참조하십시오.

## AEM Foundation 데이터 개인 정보 보호 및 보호 지원 {#aem-foundation-data-privacy-and-protection-support}

AEM Foundation 수준에서 저장된 개인 데이터는 사용자 프로필에 보관됩니다. 따라서 이 문서의 정보에서는 액세스 및 삭제 요청에 각각 대처하기 위해 사용자 프로필에 액세스하거나 삭제하는 방법에 대해 다룹니다.

## 사용자 프로필 {#accessing-a-user-profile} 액세스

### 수동 단계 {#manual-steps}

1. **[!UICONTROL 도구 - 보안 - 사용자]**&#x200B;로 이동하거나 `https://<serveraddress>:<serverport>/security/users.html`로 직접 이동하여 사용자 관리 콘솔을 엽니다.

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. 그런 다음 페이지 상단의 검색 표시줄에 다음 이름을 입력하여 해당 사용자를 검색합니다.

   ![계정 검색](assets/dpp-foundation-01.png)

1. 마지막으로 사용자 프로필을 클릭하여 연 다음 **[!UICONTROL 세부 사항]** 탭에서 선택합니다.

   ![사용자 프로필](assets/dpp-foundation-02.png)

### HTTP API {#http-api}

앞에서 언급했듯이 Adobe은 자동화를 용이하게 하기 위해 사용자 데이터에 액세스하기 위한 API를 제공합니다. 사용할 수 있는 API 유형에는 다음과 같은 것이 있습니다.

**사용자 속성 API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling API**

**사용자 홈 찾기:**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**사용자 데이터 검색 중:**

위의 명령에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 사용:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## 사용자 비활성화 및 연결된 프로필 {#disabling-a-user-and-deleting-the-associated-profiles} 삭제

### 사용자 {#disable-user} 비활성화

1. 위에 설명된 대로 사용자 관리 콘솔을 열고 해당 사용자를 검색합니다.
2. 사용자를 마우스로 가리키고 선택 아이콘을 클릭합니다. 프로파일이 선택되어 있음을 나타내는 회색으로 바뀝니다.

3. 위쪽 메뉴에서 **비활성화** 단추를 눌러 사용자를 비활성화합니다.

   ![계정 비활성화](assets/dpp-foundation-03.png)

4. 마지막으로 작업을 확인합니다.

   그러면 사용자 인터페이스에 사용자 계정이 로그아웃 후 프로필 카드에 잠금이 추가되어 비활성화되었음을 표시합니다.

   ![계정이 비활성화됨](assets/dpp-foundation-04.png)

### 사용자 프로필 정보 삭제 {#delete-user-profile-information}

>[!NOTE]
>
>Cloud Service의 경우 CRXDE에 액세스할 수 없으므로 UI에서 사용자 프로필을 삭제하기 위한 수동 절차를 사용할 수 없습니다.

### HTTP API {#http-api-1}

다음 절차에서는 `curl` 명령줄 도구를 사용하여 **[!UICONTROL cavery]** `userId`로 사용자를 비활성화하고 기본 위치에서 사용할 수 있는 프로필을 삭제하는 방법을 보여 줍니다.

**사용자 홈 찾기:**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**사용자 비활성화:**

위의 명령에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 사용:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**사용자 프로필 삭제**

계정 검색 명령 및 알려진 기본 프로필 노드 위치에서 반환된 JSON 페이로드의 홈 속성에서 노드 경로 사용:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
