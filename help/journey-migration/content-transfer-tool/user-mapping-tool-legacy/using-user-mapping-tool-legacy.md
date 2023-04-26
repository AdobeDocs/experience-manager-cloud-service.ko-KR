---
title: 사용자 매핑 도구 사용(이전)
description: 사용자 매핑 도구 사용(이전)
exl-id: dcb750c4-0f81-4d11-ac6c-0592162b683d
hide: true
hidefromtoc: true
source-git-commit: 8a258c2c929f9af84a1cde99072291a3e7f6cfc3
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 3%

---

# 사용자 매핑 도구 사용(이전) {#using-user-mapping-tool}

>[!INFO]
>
>이 설명서는 더 이상 사용되지 않는 버전의 도구를 참조합니다. 최신 버전에 대한 자세한 내용은 [사용자 매핑 및 보안 주체 마이그레이션](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

사용자 매핑 도구는 API를 사용하여 이메일로 IMS(Adobe Identity Management System) 사용자를 조회하고 IMS ID를 반환할 수 있습니다. 이 API를 사용하려면 사용자가 조직의 클라이언트 ID, 클라이언트 암호 및 액세스 또는 베어러 토큰을 만들어야 합니다.

## 사용자 매핑 도구 설정 {#setting-up-user-mapping}

**전제 조건:** 사용자 매핑을 사용하려면 각 사용자를 해당 IMS ID에 매핑해야 합니다. AEM 및 IMS의 프로필에는 이메일 주소가 있습니다.  사용자가 이메일 주소를 로그인에 사용자 ID로 사용하더라도 이메일 주소가 프로필에도 있고 IMS에도 있지 않으면 해당 사용자에 대한 매핑이 작동하지 않습니다.

아래 절차에 따라 이 설정을 수행하십시오.

1. 다음으로 이동 [Adobe Developer 콘솔](https://console.adobe.io) Adobe ID 사용.
1. 새 프로젝트를 만들거나 기존 프로젝트를 엽니다.
1. API 추가 - 클릭 **프로젝트에 추가** 을(를) 선택합니다. **API**
1. 사용자 관리 API를 선택합니다.  이 옵션을 사용하려면 시스템 관리자 권한이 있어야 합니다.
1. JWT 자격 증명을 만듭니다.
1. 키 쌍을 생성하거나 공개 키를 업로드합니다(rsa는 좋지 않음).  버튼이 있는데 **공용/개인 키 쌍 생성**&#x200B;그러면 어떤 것이 여러분을 위해 이 작업을 수행합니다.  공개 키와 개인 키를 모두 저장해야 합니다.
1. 사용자 관리 API로 이동합니다.
1. 개인 키 컨텐츠를 텍스트 상자에 붙여넣고 을 클릭하여 액세스 토큰(또는 베어러 토큰)을 생성합니다. **토큰 생성**.
1. 다음과 같은 모든 정보를 저장합니다. **클라이언트 ID**, **클라이언트 암호**, **기술 계정 ID**, **기술 계정 이메일**, **조직 ID**, 및 **액세스 토큰** 안전하게

## 사용자 매핑 도구에 대한 사용자 인터페이스 액세스 {#user-interface}

사용자 매핑 도구는 컨텐츠 전송 도구에 통합되었습니다. 에서 컨텐츠 전송 도구를 다운로드할 수 있습니다 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). 최신 버전에 대한 자세한 내용은 [현재 릴리스 노트](/help/release-notes/release-notes-cloud/release-notes-current.md).

1. Adobe Experience Manager을 선택하고 도구 -> 로 이동합니다. **작업** -> **컨텐츠 마이그레이션**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access1.png)

1. 클릭 **사용자 매핑** 카드.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access2.png)

1. 클릭 **사용자 매핑 구성 만들기**.

   >[!NOTE]
   >이 단계를 건너뛰면 추출 단계 중에 사용자 및 그룹 매핑을 건너뜁니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access5.png)

   의 필드를 채웁니다 **사용자 관리 API 구성**&#x200B;아래에 설명된 대로,

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access3.png)


   * **조직 ID**: 사용자를 마이그레이션하고 있는 조직의 IMS(Identity Management 시스템) 조직 ID를 입력합니다.

      >[!NOTE]
      >조직 ID를에 로그인합니다 [Admin Console](https://adminconsole.adobe.com/) 두 개 이상에 속해 있는 경우 조직(오른쪽 상단 영역)을 선택합니다. 조직 ID는 해당 페이지의 URL에 다음 형식으로 표시됩니다 `xx@AdobeOrg`여기서 xx 는 IMS 조직 ID입니다.  또는 에서 조직 ID를 찾을 수 있습니다 [Adobe Developer 콘솔](https://console.adobe.io) 액세스 토큰을 생성하는 페이지입니다.

   * **클라이언트 ID**: 설정 단계에서 저장한 클라이언트 ID를 입력합니다.

   * **액세스 토큰**: 설정 단계에서 저장한 액세스 토큰을 입력합니다.

      >[!NOTE]
      >액세스 토큰이 24시간마다 만료되며 새 토큰을 만들어야 합니다. 새 토큰을 만들려면 다음 위치로 돌아갑니다 [Adobe Developer 콘솔](https://console.adobe.io)를 클릭하고 프로젝트를 선택한 다음 **사용자 관리 API** 같은 개인 키를 상자에 붙여 넣습니다.

1. 필드를 채운 후 **구성 테스트** 를 클릭하여 사용자 관리 API 서비스에 대한 연결을 테스트합니다. 연결에 성공하면 를 클릭하면 됩니다 **저장** 구성을 저장합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-access4.png)

1. 구성을 저장한 후 구성을 선택하고 을(를) 클릭합니다 **사용자 매핑 시작**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing4.png)

1. 클릭 **시작** 대화 상자에서 사용자 매핑 프로세스를 시작합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   이 구성 요소는 **상태** 로서의 **실행 중**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-start1.png)


1. 사용자 매핑이 완료되면 을 클릭합니다. **결과** 요약을 보려면

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/user-mapping-landing5.png)

   >[!IMPORTANT]
   >* 사용자 매핑이 완료되면 이동 경로를 사용하여 컨텐츠 마이그레이션 페이지로 돌아갈 수 있습니다. 사용자 매핑 카드에 상태와 타임스탬프가 표시됩니다. 클릭 **컨텐츠 전송** 마이그레이션을 실행할 마이그레이션 세트를 만들려면 을(를) 참조하십시오. [컨텐츠 전송 도구 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#running-tool) 자세한 내용


### 사용자 매핑 프로세스 재개 {#resume-user-mapping-process}

다음 이유 중 하나로 인해 사용자 매핑 프로세스가 중지되는 경우

* 선택한 사용자 **사용자 매핑 중지**
* 액세스 토큰은 프로세스 또는
* 다른 이유

   >[!NOTE]
   >진행률이 프로세스가 중지된 위치에서 저장됩니다.

사용자 매핑 프로세스를 재개하려면 아래 절차를 따르십시오.

1. 클릭 **로그 보기** 사용자 매핑 로그를 검토하여 저장된 진행 상태를 확인합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping1.png)

1. 을(를) 클릭합니다. **사용자 매핑 시작** 단추를 다시 클릭하여 중단된 위치에서 다시 시작합니다.

   >[!NOTE]
   >다시 시작하기 전에 액세스 토큰이 여전히 유효하거나 새로 고침되었는지 확인하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping2.png)

1. 클릭 **시작** 대화 상자에서 사용자 매핑 프로세스를 재개합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping3.png)

   사용자 매핑 프로세스가 완료되면 **상태** 로서의 **완료됨** 해당 특정 구성에 대해 설명합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-user-mapping/resume-user-mapping4.png)
