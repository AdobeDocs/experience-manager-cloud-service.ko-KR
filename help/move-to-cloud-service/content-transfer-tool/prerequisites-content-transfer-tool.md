---
title: 컨텐츠 전송 도구 사전 요구 사항
description: 컨텐츠 전송 도구 사전 요구 사항
source-git-commit: f70959efd9d0382c083ac05b9ccd63cf79947bc2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---

# 컨텐츠 전송 도구 사전 요구 사항 {#prerequisites}

다음 표에는 컨텐츠 전송 도구 사용을 위한 사전 요구 사항이 요약되어 있습니다.

아래 나열된 모든 고려 사항을 검토하십시오.

| 고려 사항 | 현재 지원되는 항목 |
|--- |--- |
| AEM 버전 | 컨텐츠 전송 도구는 AEM 6.3 이상 버전에서만 실행할 수 있습니다. AEM 6.2 이전 버전과 함께 컨텐츠 전송 도구를 사용하려면 컨텐츠 저장소를 AEM 6.5로 즉석 업그레이드해야 합니다. 이 경우 코드를 AEM 6.5로 업그레이드할 필요가 없습니다. |
| 세그먼트 저장소 크기 | 컨텐츠 전송 도구는 현재 *Author*&#x200B;에서 최대 83GB를, *Publish*&#x200B;에서는 31GB를 지원합니다. |
| 컨텐츠 저장소의 총 크기 <br>*(컨텐츠 저장소 + 데이터 저장소)* | 컨텐츠 전송 도구는 최대 10TB의 컨텐츠를 전송하도록 설계되었습니다. 현재 10TB를 초과하는 항목은 지원되지 않습니다. 10TB 이상의 컨텐츠에 대한 옵션을 논의하려면 Adobe 고객 지원 팀과 지원 티켓을 작성합니다. |
| 변경할 수 없는 경로의 콘텐츠 | 컨텐츠 전송 도구는 `“/etc”` 과 같이 변경할 수 없는 경로에서 컨텐츠를 마이그레이션하는 데 작동하지 않습니다. <br>저장소 구조  [및 ](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/all-repository-restructuring-in-aem-6-4.html?lang=en#restructuring) 워크플로우 모델에 대한 자세한 내용은 공통 저장소 구조 조정을 참조하십시오. |

## 다음 기능 {#whats-next}

사전 요구 사항을 검토한 후에는 컨텐츠 전송 도구를 실행하는 방법을 배울 수 있습니다. 자세한 내용은 [컨텐츠 전송 도구 사용](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)을 참조하십시오.
