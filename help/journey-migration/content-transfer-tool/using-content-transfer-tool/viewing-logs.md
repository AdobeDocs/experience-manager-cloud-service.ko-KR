---
title: 컨텐츠 전송 도구의 마이그레이션 세트에 대한 로그 보기
description: 컨텐츠 전송 도구의 마이그레이션 세트에 대한 로그 보기
exl-id: aed1ac83-a2fb-425e-aca4-39cd0bb42fd3
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 52%

---

# 마이그레이션 세트에 대한 로그 보기 {#view-logs-content-transfer-tool}


>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="로그 보기"
>abstract="수집 추출이 완료되면 로그에서 오류/경고를 확인합니다. 오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="문제 해결"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Adobe 지원에 문의"

각 단계(추출 및 수집)가 완료되면 로그를 확인하고 오류를 찾습니다.  오류는 보고된 문제를 처리하거나 Adobe 지원에 연락하여 즉시 해결해야 합니다.

## 로그 보기 단계 {#viewing-logs}

*개요* 페이지에서 기존 마이그레이션 세트에 대한 로그를 볼 수 있습니다.
아래 단계를 따르십시오.

1. *개요* 페이지로 이동하여 삭제할 마이그레이션 세트를 선택하고 작업 표시줄에서 **로그 보기**&#x200B;를 클릭합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/view-log1.png)

1. **로그** 대화 상자가 표시됩니다. **추출 로그**&#x200B;를 클릭하여 새 탭에서 로그를 확인합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/view-log2.png)
또는,

   *개요* 화면에서 마이그레이션 세트에 대한 로그를 볼 수도 있습니다. 마이그레이션 세트를 선택하고 **추출** 필드 아래에서 상태를 클릭합니다. 이 경우 **완료됨**&#x200B;을 클릭하여 새 탭에서 로그를 봅니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets/view-log3.png)

1. 사용자 인터페이스를 사용하지 않고 로그를 추적하려면 소스 AEM 환경에 SSH를 사용하여 `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file`를 추적할 수 있습니다.
