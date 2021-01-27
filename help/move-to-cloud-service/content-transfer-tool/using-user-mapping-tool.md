---
title: 사용자 매핑 도구 사용
description: 사용자 매핑 도구 사용
translation-type: tm+mt
source-git-commit: dcba197624b6a7ae668b11f43f60b13a9da0080e
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 1%

---


# 사용자 매핑 도구 사용 {#user-mapping-tool}

## 개요 {#overview}

Cloud Service에서 AEM으로 전환 여정의 일부로, 사용자와 그룹을 기존 AEM 시스템에서 AEM으로 Cloud Service으로 이동시켜야 합니다. 이는 컨텐츠 전송 도구에 의해 수행됩니다.

Cloud Service로서 AEM의 주요 변경 사항은 작성 계층에 액세스하기 위해 Adobe ID를 완벽하게 통합하는 것입니다.  이렇게 하려면 사용자 및 사용자 그룹을 관리하기 위해 Adobe Admin Console을 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 Single Sign-On을 제공하는 Adobe Identity Management System(IMS)에 중앙 집중화되어 있습니다. 자세한 내용은 Identity Management을 참조하십시오. 이러한 변경 사항으로 인해 Cloud Service 작성자 인스턴스에서 사용자와 그룹이 중복되지 않도록 기존 사용자 및 그룹을 IMS ID에 매핑해야 합니다.

## 중요 고려 사항 {#important-considerations}

고려해야 할 몇 가지 예외적인 사례가 있다. 다음 특정 사례가 기록되고 해당 사용자나 그룹이 매핑되지 않습니다.

1. 사용자에게 jcr 노드의 `profile/email` 필드에 이메일 주소가 없는 경우.

1. 사용된 조직 ID에 대한 IMS 시스템에서 지정된 이메일을 찾을 수 없는 경우(또는 다른 이유로 IMS ID를 검색할 수 없는 경우)

1. 사용자가 현재 비활성화되어 있으면 비활성화되어 있지 않은 것처럼 처리됩니다.  매핑되고 정상적으로 마이그레이션되며 클라우드 인스턴스에서 비활성화된 상태로 유지됩니다.

## 사용자 매핑 도구 {#using-user-mapping-tool} 사용

사용자 매핑 도구는 IMS 사용자를 이메일로 조회하고 IMS ID를 반환할 수 있도록 해주는 API를 사용합니다. 이 API를 사용하려면 사용자가 조직의 클라이언트 ID, 클라이언트 암호 및 액세스 토큰/전달자 토큰을 만들어야 합니다.

다음 단계에 따라 설정합니다.

1. Adobe ID을 사용하여 [Adobe 개발자 콘솔](https://console.adobe.io)로 이동합니다.
1. 새 프로젝트를 만들거나 기존 프로젝트를 엽니다.
1. API를 추가합니다.
1. 사용자 관리 API를 선택합니다.
1. JWT 자격 증명을 만듭니다.
1. 키 쌍을 생성하거나 공개 키를 업로드합니다(rsa는 좋지 않음).
1. 액세스 토큰(또는 JWT 토큰 또는 무기명 토큰)을 생성합니다.
1. **클라이언트 ID**, **클라이언트 암호**, **기술 계정 ID**, **기술 계정 이메일**, **조직 ID** 및 **액세스 등의 모든 정보를 저장합니다. 토큰**&#x200B;은(는) 안전하게 유효합니다.

## 사용자 인터페이스 {#user-interface}

사용자 매핑 도구는 내용 전송 도구에 통합됩니다. 소프트웨어 배포 포털에서 컨텐츠 전송 툴을 다운로드할 수 있습니다. 최신 버전에 대한 자세한 내용은 [현재 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

1. Adobe Experience Manager 선택을 선택하고 도구 -> **작업** -> **컨텐트 전송**&#x200B;으로 이동합니다.
1. **사용자 매핑 구성 만들기**&#x200B;를 클릭합니다.

   >[!NOTE]
   >이 단계를 건너뛰면 추출 단계 동안 사용자 및 그룹 매핑을 건너뜁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-1.png)

   아래 설명에 따라 사용자 관리 API 구성의 필드를 채웁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-2.png)

   * **조직 ID**:사용자가 마이그레이션되는 조직의 IMS 조직 ID를 입력합니다.

      >[!NOTE]
      >조직 ID를 가져오려면 [Admin Console](https://adminconsole.adobe.com/)에 로그인하고 둘 이상의 조직에 속해 있는 경우 조직을 선택합니다. 조직 ID는 해당 페이지의 URL(예: `xx@AdobeOrg` 형식)에 있으며 여기서 xx는 IMS 조직 ID입니다.  또는 액세스 토큰을 생성하는 [Adobe 개발자 콘솔](https://console.adobe.io) 페이지에서 조직 ID를 찾을 수 있습니다.

   * **클라이언트 ID**:설정 단계에서 저장한 클라이언트 ID 입력

   * **액세스 토큰**:설정 단계에서 저장한 액세스 토큰을 입력합니다

      >[!NOTE]
      >액세스 토큰은 24시간마다 만료되며 새로 만들어야 합니다. 새 토큰을 만들려면 [Adobe 개발자 콘솔](https://console.adobe.io)로 돌아가 프로젝트를 선택하고 사용자 관리 API를 클릭한 다음 동일한 개인 키를 상자에 붙여 넣습니다.

1. 위 정보를 입력한 후 **저장**&#x200B;을 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-3.png)


1. **마이그레이션 세트 만들기**&#x200B;를 클릭하고 필드를 채운 다음 **저장**&#x200B;을 클릭하여 마이그레이션 세트를 만듭니다. 자세한 내용은 컨텐츠 전송 도구 실행을 참조하십시오.

   >[!NOTE]
   >IMS에서 사용자 매핑(Mapping Users from IMS) 포함 전환 스위치는 기본적으로 켜져 있습니다. 이 설정을 사용하면 이 마이그레이션 세트에서 추출을 수행하면 사용자 매핑 도구가 추출 단계의 일부로 실행됩니다. 컨텐츠 전송 도구의 추출 단계를 실행하는 것이 좋습니다. 이 토글이 꺼져 있고/또는 사용자 매핑 구성이 생성되지 않으면 추출 단계 동안 사용자 및 그룹 매핑을 건너뜁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-4.png)

1. 추출 단계를 실행하려면 [내용 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool)을 참조하십시오.



