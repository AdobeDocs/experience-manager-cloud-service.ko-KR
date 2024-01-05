---
title: 콘텐츠 전송 도구 사전 요구 사항
description: 컨텐츠 전송 도구 사전 요구 사항을 숙지하십시오
exl-id: 41a9cff1-4d89-480c-b9fc-5e8efc2a0705
source-git-commit: aa032af2ed7ff877b4c9f9cb6d427c84e71c3874
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 11%

---

# 콘텐츠 전송 도구 사전 요구 사항 {#prerequisites}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="콘텐츠 전송 도구 사용에 대한 중요 고려 사항"
>abstract="Java™ 및 AEM 버전, 지원되는 데이터 저장소 유형, 사용자 그룹 고려 사항 등 콘텐츠 전송 도구를 사용하기 위한 중요 고려 사항을 검토하십시오."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html" text="콘텐츠 전송 도구 사용에 대한 중요 고려 사항"
additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#best-practices" text="모범 사례 및 지침"

다음 표에는 컨텐츠 전송 도구를 사용하기 위한 사전 요구 사항이 요약되어 있습니다.

아래 나열된 고려 사항을 모두 검토하십시오.

| 고려 사항 | 현재 지원되는 항목 |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AEM 버전 | 컨텐츠 전송 도구는 AEM 6.3 이상 버전에서만 실행할 수 있습니다. |
| 세그먼트 저장소 크기 | 7억 5천만 개 미만의 JCR 노드 및 최대 500GB(온라인 압축 크기)의 기존 저장소 *작성자* 및 50GB *게시* 는 현재 지원됩니다. 이러한 제한을 초과하는 Adobe 저장소 크기 옵션에 대해 논의할 수 있도록 고객 지원 센터에서 지원 티켓을 만드십시오. |
| 콘텐츠 저장소의 총 크기 <br>*(세그먼트 저장소 + 데이터 저장소)* | 컨텐츠 전송 도구는 파일 데이터 저장소 유형의 데이터 저장소에 대해 최대 20TB의 컨텐츠를 전송하도록 설계되었습니다. 20TB 이상의 콘텐츠는 현재 지원되지 않습니다. 20TB가 넘는 컨텐츠에 대한 옵션을 논의할 수 있도록 Adobe 고객 지원 센터에서 지원 티켓을 만드십시오. <br>대형 저장소의 컨텐츠 전송 프로세스를 크게 가속화하려면 다음 옵션을 선택합니다 [사전 복사](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=ko-KR#setting-up-pre-copy-step) 단계를 사용할 수 있습니다. 이 프로세스는 파일 데이터 저장소, Amazon S3 및 Azure 데이터 저장소 유형의 데이터 저장소에 적용됩니다. Amazon S3 및 Azure Data Store의 경우 20테라바이트 이상의 저장소 크기가 지원됩니다. |
| 총 Lucene 인덱스 크기 | 최대 25GB의 총 Lucene 인덱스 크기(제외) `/oak:index/lucene` 및 `/oak:index/damAssetLucene` 은(는) 지원됩니다. 이 제한을 초과하는 인덱스 크기에 대한 옵션을 논의할 수 있도록 고객 지원 센터 Adobe으로 지원 티켓을 만드십시오. |
| 노드 이름 길이 | 노드 상위 경로가 350바이트 이상(같거나 큼)일 경우 노드 이름의 길이는 150바이트 이하여야 합니다. AEM 문서 노드 저장소에서 as a Cloud Service으로 지원하려면 이러한 노드 이름을 150바이트 이하로 줄여야 합니다. 이러한 긴 노드 이름이 수정되지 않으면 수집이 실패합니다. |
| 변경 불가능한 경로의 콘텐츠 | 변경 불가능한 경로의 콘텐츠를 마이그레이션하는 데 콘텐츠 전송 도구를 사용할 수 없습니다. 콘텐츠를 전송하려면 `/etc`, 다음을 선택할 수 있습니다. `/etc` 경로(단, 지원 전용) [AEM Forms-AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html#paths-of-various-aem-forms-specific-assets). 기타 모든 사용 사례는 [공통 저장소 재구성](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/all-repository-restructuring-in-aem-6-5.html) 저장소 재구성에 대해 자세히 알아보십시오. |
| MongoDB의 노드 속성 값 | MongoDB에 저장된 노드 속성 값은 16MB를 초과할 수 없습니다. 이 규칙은 MongoDB에 의해 시행됩니다. 이 제한보다 큰 속성 값이 있는 경우 수집이 실패합니다. 추출을 실행하기 전에 다음을 실행하십시오. [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) 스크립트. 모든 큰 속성 값을 검토하고 필요한 경우 확인합니다. 16MB를 초과하는 값은 이진 값으로 변환해야 합니다. |

## 다음 단계 {#whats-next}

사전 요구 사항을 검토하고 마이그레이션 프로젝트에서 콘텐츠 전송 도구를 사용할 수 있는지 여부를 결정했으면 다음을 참조하십시오. [컨텐츠 전송 도구 사용을 위한 지침 및 우수 사례](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html).
