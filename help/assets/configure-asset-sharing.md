---
title: 자산, 폴더 및 컬렉션을 링크로 공유
description: 이 문서에서는 Experience Manager 자산 내에서 자산, 폴더 및 컬렉션을 하이퍼링크로 공유하는 방법에 대해 설명합니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# 자산 링크 공유 구성 {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

사용자와 공유할 에셋의 URL을 생성하려면 링크 공유 대화 상자를 사용합니다. 관리자 권한이 있거나 읽기 권한이 있는 사용자는 `/var/dam/share` 해당 사용자와 공유된 링크를 볼 수 있습니다. 링크를 통해 자산을 공유하는 것은 AEM 자산에 먼저 로그인하지 않고도 외부 당사자가 리소스를 사용할 수 있도록 하는 편리한 방법입니다.

>[!NOTE]
>
>AEM 작성자 인스턴스의 링크를 외부 엔티티에 공유하려면 `GET` 요청에 대해 다음 URL만 표시해야 합니다. 다른 URL을 차단하여 AEM 작성자 인스턴스가 안전한지 확인합니다.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


## 일 CQ 메일 서비스 구성 {#configmailservice}

자산을 링크로 공유하려면 먼저 이메일 서비스를 구성합니다.

1. AEM 로고를 클릭하거나 탭한 다음 도구 > **[!UICONTROL 작업]** > **[!UICONTROL 웹]** 콘솔로 **[!UICONTROL 이동합니다]**.
1. 서비스 목록에서 Day CQ Mail **[!UICONTROL Service를 찾습니다]**.
1. 서비스 **[!UICONTROL 옆에 있는]** 편집 아이콘을 클릭하고 이름에 대해 **명시된 세부 사항과 함께 다음 매개 변수를 구성합니다.**

   * SMTP 서버 호스트 이름:이메일 서버 호스트 이름
   * SMTP 서버 포트:이메일 서버 포트
   * SMTP 사용자:이메일 서버 사용자 이름
   * SMTP 암호:이메일 서버 암호

1. Click/tap **Save**.

## 최대 데이터 크기 구성 {#maxdatasize}

링크 공유 기능을 사용하여 공유된 링크에서 자산을 다운로드할 때 AEM은 저장소에서 자산 계층을 압축한 다음 ZIP 파일로 자산을 반환합니다. 그러나 ZIP 파일에서 압축할 수 있는 데이터 양에 제한이 없는 경우 엄청난 양의 데이터가 압축되어 JVM에서 메모리 오류가 발생합니다. 이러한 상황에서 시스템을 잠재적 서비스 거부 공격으로부터 보호하려면 Configuration Manager의 일 CQ DAM Adhoc **Asset Share 프록시 서블릿에 대한 최대 컨텐트 크기(비압축)** 매개 변수를 사용하여 최대 크기를 구성합니다. 자산의 압축되지 않은 크기가 구성된 값을 초과하는 경우 자산 다운로드 요청이 거부됩니다. 기본값은 100MB입니다.

1. AEM 로고를 클릭/탭한 다음 도구 > **작업** > **웹** 콘솔로 **이동합니다**.
1. 웹 콘솔에서 CQ DAM Adhoc **Asset Share 프록시 서블릿 구성을 찾습니다** .
1. 편집 **모드에서 일 CQ DAM 애드혹 자산 공유 프록시** 서블릿 구성을 열고 최대 컨텐트 크기(압축되지 않은) **** 매개 변수의 값을 수정합니다.
1. 변경 사항을 저장합니다.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->
