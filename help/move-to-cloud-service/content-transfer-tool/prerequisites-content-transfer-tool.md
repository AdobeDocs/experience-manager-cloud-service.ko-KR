---
title: 컨텐츠 전송 도구 사전 요구 사항
description: 컨텐츠 전송 도구 사전 요구 사항
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: 87fa7079388e7a125ed62577123959524390486c
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 2%

---

# 컨텐츠 전송 도구 사전 요구 사항 {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="컨텐츠 전송 도구 사용에 대한 중요한 고려 사항"
>abstract="Java 및 AEM 버전, 지원되는 데이터 저장소 유형, 사용자 그룹 고려 사항 등을 포함한 컨텐츠 전송 도구를 사용하기 위한 중요한 고려 사항을 검토하십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs" text="컨텐츠 전송 도구 사용에 대한 중요한 고려 사항"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#best-practices" text="우수 사례 및 지침"

다음 표에는 컨텐츠 전송 도구 사용을 위한 사전 요구 사항이 요약되어 있습니다.

아래 나열된 모든 고려 사항을 검토하십시오.

| 고려 사항 | 현재 지원되는 항목 |
|--- |--- |
| AEM 버전 | 컨텐츠 전송 도구는 AEM 6.3 이상 버전에서만 실행할 수 있습니다. AEM 6.2 이전 버전과 함께 컨텐츠 전송 도구를 사용하려면 컨텐츠 저장소를 AEM 6.5로 즉석 업그레이드해야 합니다. 이 경우 코드를 AEM 6.5로 업그레이드할 필요가 없습니다. |
| 세그먼트 저장소 크기 | *Author*&#x200B;에서는 최대 83GB이고 *Publish*&#x200B;에서는 31GB가 현재 지원됩니다. Adobe 고객 지원 센터를 통해 지원 티켓을 만들어 이러한 제한을 초과하는 세그먼트 저장소 크기에 대한 옵션을 논의합니다. |
| 컨텐츠 저장소의 총 크기 <br>*(세그먼트 저장소 + 데이터 저장소)* | 컨텐츠 전송 도구는 파일 데이터 저장소 유형의 데이터 저장소에 대해 최대 10TB의 컨텐츠를 전송하도록 설계되었습니다. 현재 10TB를 초과하는 항목은 지원되지 않습니다. 10TB 이상의 컨텐츠에 대한 옵션을 논의하려면 Adobe 고객 지원 팀과 지원 티켓을 작성합니다. <br>Amazon S3 및 Azure Data Store 유형의 데이터 저장소의 경우 선택적 사전 복사 단계를 사용하여 컨텐츠 전송 프로세스를 획기적으로 단축하고 10TB 이상의 데이터 저장소를 지원합니다. |
| 변경할 수 없는 경로의 콘텐츠 | 컨텐츠 전송 도구를 사용하여 변경할 수 없는 경로에서 컨텐츠를 마이그레이션할 수 없습니다. `/etc`에서 컨텐츠를 전송하려면 특정 `"/etc"` 경로만 선택할 수 있지만 Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets)로서 [AEM Forms을 AEM Forms에 지원하기만 하면 됩니다. 다른 모든 사용 사례에 대해서는 [공통 저장소 구조 변경](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring)을 참조하여 저장소 구조 변경에 대해 자세히 알아보십시오. |

## 다음은 무엇입니까? {#whats-next}

사전 요구 사항을 검토하고 마이그레이션 프로젝트에서 컨텐츠 전송 도구를 사용할 수 있는지 여부를 결정했으면 컨텐츠 전송 도구를 사용하는 동안 [추가 우수 사례 및 고려 사항](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)을 참조하십시오.
