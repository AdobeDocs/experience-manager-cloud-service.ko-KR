---
title: 사용자 매핑 도구 사용(기존)
description: 사용자 매핑 도구 사용(기존)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 1%

---

# 사용자 매핑 도구 사용(기존) {#using-user-mapping-tool}

>[!INFO]
>
>이 설명서는 더 이상 사용되지 않는 버전의 도구를 참조합니다. 최신 버전에 대한 자세한 내용은 [사용자 매핑 및 사용자 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

사용자 매핑 도구는 이메일로 Adobe Identity Management System(IMS) 사용자를 조회하고 IMS ID를 반환할 수 있는 API를 사용합니다. 이 API를 사용하려면 사용자가 조직에 대한 클라이언트 ID, 클라이언트 암호 및 액세스 또는 전달자 토큰을 만들어야 합니다.

## 사용자 매핑 도구 설정 {#setting-up-user-mapping}

**전제 조건:** 사용자 매핑을 사용하려면 IMS ID에 매핑되는 각 사용자가 AEM 및 IMS의 프로필에 이메일 주소가 있어야 합니다. 사용자가 로그인을 위해 이메일 주소를 사용자 ID로 사용하더라도 이메일 주소가 프로필과 IMS에도 있지 않으면 해당 사용자에 대한 매핑이 작동하지 않습니다.

아래 단계에 따라 설정하십시오.

1. 다음으로 이동 [Adobe Developer 콘솔](https://developer.adobe.com/console/) Adobe ID 사용.
1. 프로젝트를 만들거나 기존 프로젝트를 엽니다.
1. API 추가 - 클릭 **프로젝트에 추가** 및 선택 **API**
1. 사용자 관리 API를 선택합니다. 이 옵션을 사용하려면 시스템 관리자 권한이 있어야 합니다.
1. JWT 자격 증명을 만듭니다.
1. 키 쌍을 생성하거나 공개 키 업로드 를 참조하십시오(rsa는 좋지 않음). 단추가 있는데, **공개/비공개 키 쌍 생성** 그러면 이 키 쌍이 만들어집니다. 공개 키와 개인 키를 모두 저장해야 합니다.
1. 사용자 관리 API로 이동합니다.
1. 개인 키 콘텐츠를 텍스트 상자에 붙여 넣고 을 클릭하여 액세스 토큰(또는 전달자 토큰)을 생성합니다. **토큰 생성**.
1. 다음과 같은 정보를 모두 저장합니다. **클라이언트 ID**, **클라이언트 암호**, **기술 계정 ID**, **기술 계정 이메일**, **조직 ID**, 및 **액세스 토큰** 안전하게.

## 사용자 매핑 도구의 사용자 인터페이스에 액세스 {#user-interface}

사용자 매핑 도구는 컨텐츠 전송 도구에 통합되어 있습니다. 다음에서 컨텐츠 전송 도구를 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). 최신 버전에 대한 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Adobe Experience Manager을 선택하고 도구 > 로 이동합니다. **작업** > **컨텐츠 마이그레이션**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. 다음을 클릭합니다. **사용자 매핑** 카드.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. 클릭 **사용자 매핑 구성 만들기**.

   >[!NOTE]
   >이 단계를 건너뛸 경우 추출 단계 동안 사용자 및 그룹 매핑을 건너뜁니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   필드 채우기 **사용자 관리 API 구성**&#x200B;에 설명되어 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **조직 ID**: 사용자가 마이그레이션되는 조직의 IMS(Identity Management 시스템) Adobe 조직 ID를 입력합니다.

     >[!NOTE]
     >조직 ID를 가져오려면에 로그온합니다. [Admin Console](https://adminconsole.adobe.com/) 둘 이상에 속해 있는 경우 오른쪽 상단에서 조직을 선택합니다. 조직 ID는 과 같은 형식으로 해당 페이지의 URL에 있습니다. `xx@AdobeOrg`여기서 xx는 IMS 조직 ID입니다. 또는 조직 ID를에서 찾을 수 있습니다. [Adobe Developer 콘솔](https://developer.adobe.com/console/) 액세스 토큰을 생성하는 페이지입니다.

   * **클라이언트 ID**: 설정 단계에서 저장한 클라이언트 ID를 입력합니다.

   * **액세스 토큰**: 설정 단계에서 저장한 액세스 토큰을 입력합니다.

     >[!NOTE]
     >액세스 토큰은 24시간마다 만료되며 새 액세스 토큰을 만들어야 합니다. 토큰을 만들려면 로 돌아갑니다. [Adobe Developer 콘솔](https://developer.adobe.com/console/)프로젝트를 선택하고 **사용자 관리 API**&#x200B;을 클릭하고 상자에 동일한 개인 키를 붙여 넣습니다.

1. 필드를 채운 후 **구성 테스트** 를 클릭하여 User Management API 서비스에 대한 연결을 테스트합니다. 연결에 성공하면 **저장** 구성을 저장합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. 구성을 저장한 후 구성을 선택하고 **사용자 매핑 시작**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. 클릭 **시작** 을 클릭하여 사용자 매핑 프로세스를 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   다음을 표시합니다. **상태** 다음으로: **실행 중**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. 사용자 매핑이 완료되면 다음을 클릭하십시오. **결과** 요약 보기.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >
   >* 사용자 매핑이 완료되면 이동 경로를 사용하여 콘텐츠 마이그레이션 페이지로 다시 이동할 수 있습니다. 사용자 매핑 카드에 상태와 타임스탬프가 표시됩니다. 클릭 **컨텐츠 전송** 마이그레이션 세트를 만들어 추출을 실행할 수 있습니다. 다음을 참조하십시오 [컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html#running-tool) 을 참조하십시오.

### 사용자 매핑 프로세스 다시 시작 {#resume-user-mapping-process}

사용자 매핑 프로세스가 다음 이유로 중지된 경우:

* 옵션 **사용자 매핑 중지** 이(가) 사용자에 의해 선택되었습니다.
* 액세스 토큰이 프로세스 중에 만료되었습니다.
* 아니면 다른 이유도 있어

  >[!NOTE]
  >진행률은 프로세스가 중지된 위치에서 저장됩니다.

사용자 매핑 프로세스를 재개하려면 아래 단계를 따르십시오.

1. 클릭 **로그 보기** 저장된 진행률을 확인할 수 있도록 사용자 매핑 로그를 검토합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. 클릭 **사용자 매핑 시작** 단추를 다시 클릭하여 꺼진 위치에서 다시 시작합니다.

   >[!NOTE]
   >다시 시작하기 전에 액세스 토큰이 여전히 유효한지 또는 새로 고쳐졌는지 확인하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. 클릭 **시작** 을 클릭하여 사용자 매핑 프로세스를 다시 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   사용자 매핑 프로세스가 완료되면 다음을 볼 수 있습니다. **상태** 다음으로: **완료됨** 특정 구성을 위한 것입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
