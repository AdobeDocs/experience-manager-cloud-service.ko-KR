---
title: 사용자 매핑 도구 사용
description: 사용자 매핑 도구 사용
source-git-commit: 77c412c1050be8843e7185b0511a9d7af41669e3
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---


# 사용자 매핑 도구 사용 {#using-user-mapping-tool}

사용자 매핑 도구는 API를 사용하여 이메일로 IMS(Adobe Identity Management System) 사용자를 조회하고 IMS ID를 반환할 수 있습니다. 이 API를 사용하려면 사용자가 조직의 클라이언트 ID, 클라이언트 암호 및 액세스 또는 베어러 토큰을 만들어야 합니다.

## 사용자 매핑 도구 설정 {#setting-up-user-mapping}

아래 절차에 따라 이 설정을 수행하십시오.

1. Adobe ID을 사용하여 [Adobe 개발자 콘솔](https://console.adobe.io)로 이동합니다.
1. 새 프로젝트를 만들거나 기존 프로젝트를 엽니다.
1. API 추가 - **Add to Project**&#x200B;를 클릭하고 **API**&#x200B;를 선택합니다.
1. 사용자 관리 API를 선택합니다.  이 옵션을 사용하려면 권한을 가져와야 할 수 있습니다.
1. JWT 자격 증명을 만듭니다.
1. 키 쌍을 생성하거나 공개 키를 업로드합니다(rsa는 좋지 않음).  **공개/개인 키 쌍 생성** 버튼이 있습니다.  공개 키와 개인 키를 모두 저장해야 합니다.
1. 사용자 관리 API로 이동합니다.
1. 개인 키 컨텐츠를 텍스트 상자에 붙여넣고 **토큰 생성**&#x200B;을 클릭하여 액세스 토큰(또는 베어러 토큰)을 생성합니다.
1. **클라이언트 ID**, **클라이언트 암호**, **기술 계정 ID**, **기술 계정 이메일**, **조직 ID** 및 **액세스 토큰**&#x200B;과 같은 모든 정보를 안전하게 저장합니다.

## 사용자 매핑 도구에 대한 사용자 인터페이스 액세스 {#user-interface}

사용자 매핑 도구는 컨텐츠 전송 도구에 통합되었습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 컨텐츠 전송 도구를 다운로드할 수 있습니다. 최신 버전에 대한 자세한 내용은 [현재 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

1. Adobe Experience Manager을 선택하고 도구 -> **작업** -> **컨텐츠 마이그레이션**&#x200B;으로 이동합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. **사용자 매핑** 카드를 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. **사용자 매핑 구성 만들기**&#x200B;를 클릭합니다.

   >[!NOTE]
   >이 단계를 건너뛰면 추출 단계 중에 사용자 및 그룹 매핑을 건너뜁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   아래 설명된 대로 **사용자 관리 API 구성**&#x200B;의 필드를 채웁니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **조직 ID**: 사용자를 마이그레이션하고 있는 조직의 IMS(Identity Management 시스템) 조직 ID를 입력합니다.

      >[!NOTE]
      >조직 ID를 가져오려면 [Admin Console](https://adminconsole.adobe.com/)에 로그인하고, 둘 이상에 속해 있는 경우 조직(오른쪽 상단 영역)을 선택하십시오. 조직 ID는 해당 페이지의 URL에 있는 `xx@AdobeOrg` 형식입니다. 여기서 xx는 IMS 조직 ID입니다.  또는 [Adobe 개발자 콘솔](https://console.adobe.io) 페이지에서 액세스 토큰을 생성하는 조직 ID를 찾을 수 있습니다.

   * **클라이언트 ID**: 설정 단계에서 저장한 클라이언트 ID를 입력합니다.

   * **액세스 토큰**: 설정 단계에서 저장한 액세스 토큰을 입력합니다.

      >[!NOTE]
      >액세스 토큰이 24시간마다 만료되며 새 토큰을 만들어야 합니다. 새 토큰을 만들려면 [Adobe 개발자 콘솔](https://console.adobe.io)로 돌아가서 프로젝트를 선택하고 **사용자 관리 API**&#x200B;를 클릭한 다음 동일한 개인 키를 상자에 붙여 넣습니다.

1. 필드를 채운 후 **테스트 구성**&#x200B;을 클릭하여 사용자 관리 API 서비스에 대한 연결을 테스트합니다. 연결이 성공하면 **저장**&#x200B;을 클릭하여 구성을 저장할 수 있습니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. 구성을 저장한 후 구성을 선택하고 **사용자 매핑 시작**&#x200B;을 클릭합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. 사용자 매핑이 완료되면 **결과**&#x200B;를 클릭하여 요약을 확인합니다.

   ![이미지](/help/move-to-cloud-service/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* 사용자 매핑이 완료되면 이동 경로를 사용하여 컨텐츠 마이그레이션 페이지로 돌아갈 수 있습니다. 사용자 매핑 카드에 상태와 타임스탬프가 표시됩니다. **컨텐츠 전송**&#x200B;을 클릭하여 추출을 실행할 마이그레이션 세트를 만듭니다. 자세한 내용은 [컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool)을 참조하십시오.


### 사용자 매핑 프로세스 재개 {#resume-user-mapping-process}

다음 이유 중 하나로 인해 사용자 매핑 프로세스가 중지되는 경우

* 사용자가 선택한 **사용자 매핑 중지**
* 액세스 토큰은 프로세스 또는
* 다른 이유

진행률이 프로세스가 중지된 위치에서 저장됩니다. 사용자 매핑 로그를 검토하여 저장된 진행 상태를 확인합니다. **사용자 매핑 시작** 단추를 다시 클릭하여 중지된 위치에서 다시 시작합니다. 다시 시작하기 전에 액세스 토큰이 여전히 유효하거나 새로 고침되었는지 확인하십시오.
