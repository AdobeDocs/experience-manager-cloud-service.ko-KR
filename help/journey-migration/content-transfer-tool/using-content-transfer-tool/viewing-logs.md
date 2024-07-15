---
title: 컨텐츠 전송 도구에서 마이그레이션 세트에 대한 로그 보기
description: 컨텐츠 전송 도구에서 마이그레이션 세트에 대한 로그 보기
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 36%

---

# 마이그레이션 세트에 대한 로그 보기 {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="로그 보기"
>abstract="수집 추출이 완료되면 로그에서 오류/경고를 확인하십시오. 모든 오류는 보고된 문제를 처리하거나 Adobe 지원 센터에 문의하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html#troubleshooting" text="문제 해결"
>additional-url="https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html" text="Adobe 지원 센터 문의"

각 단계(추출 및 수집)가 완료되면 로그를 확인하여 오류를 찾습니다.  모든 오류는 보고된 문제를 처리하거나 Adobe 지원 센터에 문의하여 즉시 해결해야 합니다.

## 로그 보기 단계 {#viewing-logs}

### 추출 로그

추출 로그를 보려면 소스 Adobe Experience Manager 인스턴스로 이동한 다음 원하는 마이그레이션 세트를 선택합니다.

그런 다음 아래 단계를 수행합니다.

1. 마이그레이션 세트를 선택하고 작업 표시줄에서 **로그 보기**&#x200B;를 클릭합니다. 그러면 로그 대화 상자가 표시됩니다. 새 탭에서 로그를 보려면 **추출 로그**&#x200B;를 클릭하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam25.png) \
   또는 **FINISHED** 상태를 클릭하여 새 탭에서 로그를 봅니다.

1. 사용자 인터페이스를 사용하지 않고 로그를 추적하려면 소스 AEM 환경에 SSH를 사용하여 `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`를 추적할 수 있습니다.

### 수집 로그

수집 로그를 보려면 Cloud Acceleration Manager의 수집 작업 목록으로 이동한 다음 원하는 마이그레이션 작업을 찾아 작업의 세 점(**...**)을 클릭합니다. **로그 다운로드**&#x200B;를 클릭하여 로그를 다운로드할 수 있습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam28.png)
