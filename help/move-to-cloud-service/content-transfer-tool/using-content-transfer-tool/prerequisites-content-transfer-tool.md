---
title: 컨텐츠 전송 도구 사전 요구 사항
description: 컨텐츠 전송 도구 사전 요구 사항
exl-id: ef6d0e1a-0ed2-4485-adab-df6e0cf3ac4d
source-git-commit: bdcc5cfc229fd5b1fd1f70e37c7231ed3f727e72
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

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
| 세그먼트 저장소 크기 | *Author* 및 *Publish*&#x200B;에서 최대 83GB(온라인 압축 크기)가 있는 기존 저장소가 현재 지원됩니다. Adobe 고객 지원 센터를 통해 지원 티켓을 만들어 이러한 제한을 초과하는 세그먼트 저장소 크기에 대한 옵션을 논의합니다. |
| 컨텐츠 저장소의 총 크기 <br>*(세그먼트 저장소 + 데이터 저장소)* | 컨텐츠 전송 도구는 파일 데이터 저장소 유형의 데이터 저장소에 대해 최대 10TB의 컨텐츠를 전송하도록 설계되었습니다. 현재 10TB를 초과하는 항목은 지원되지 않습니다. 10TB 이상의 컨텐츠에 대한 옵션을 논의하려면 Adobe 고객 지원 팀과 지원 티켓을 작성합니다. <br>Amazon S3 및 Azure Data Store 유형의 데이터 저장소의 경우 선택적  [사전 ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step) 복사 단계를 사용하여 컨텐츠 전송 프로세스를 획기적으로 단축하고 10TB 이상의 데이터 저장소를 지원합니다. |
| 총 인덱스 크기 | 현재 최대 25GB의 총 인덱스 크기가 지원됩니다. 이 제한을 초과하는 색인 크기에 대한 옵션을 토론하려면 Adobe 고객 지원 센터에서 지원 티켓을 만드십시오. |
| 노드 이름 길이 | 노드 이름의 길이는 150바이트 이하여야 합니다. AEM as a Cloud Service의 문서 노드 저장소에서 지원되려면 150바이트보다 긴 노드 이름을 150바이트보다 작게 지정해야 합니다. 이러한 긴 노드 이름이 수정되지 않으면 처리가 실패합니다. |
| 변경할 수 없는 경로의 콘텐츠 | 컨텐츠 전송 도구를 사용하여 변경할 수 없는 경로에서 컨텐츠를 마이그레이션할 수 없습니다. `/etc`에서 컨텐츠를 전송하려면 특정 `/etc` 경로만 선택할 수 있지만 [AEM Forms을 AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/migrate-to-forms-as-a-cloud-service.html?lang=en#paths-of-various-aem-forms-specific-assets)로 지원하기만 하면 됩니다. 다른 모든 사용 사례에 대해서는 [공통 저장소 구조 변경](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring)을 참조하여 저장소 구조 변경에 대해 자세히 알아보십시오. |
| MongoDB의 노드 속성 값 | MongoDB에 저장된 노드 속성 값은 16MB를 초과할 수 없습니다. 이는 MongoDB에 의해 적용됩니다. 이 제한보다 큰 속성 값이 있는 경우 처리가 실패합니다. 추출을 실행하기 전에 이 [oak-run](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/1.38.0/oak-run-1.38.0.jar) 스크립트를 실행합니다. 모든 큰 속성 값을 검토하고 필요한 경우 확인합니다. 16MB를 초과하는 값은 이진 값으로 변환해야 합니다. |

## 다음은 무엇입니까? {#whats-next}

사전 요구 사항을 검토하고 마이그레이션 프로젝트에서 컨텐츠 전송 도구를 사용할 수 있는지 여부를 결정했으면 컨텐츠 전송 도구를 사용하는 동안 [추가 우수 사례 및 고려 사항](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)을 참조하십시오.
