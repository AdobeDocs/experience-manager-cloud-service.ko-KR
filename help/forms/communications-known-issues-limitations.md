---
title: '알려진 문제 '
description: 통신 우수 사례, 알려진 문제 및 제한 사항
source-git-commit: 06da7d2a5063e163aa1534bedbc79ae50ef27515
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# FAQ, 우수 사례, 알려진 문제 및 제한 사항 {#best-practices-known-issues-and-limitations}

Communication API를 사용하기 전에 FAQ는 다음과 같은 알려진 문제 및 제한 사항을 검토하십시오.

## 알려진 문제

- 특정 렌더링 유형(PDF, PRINT)은 인쇄 옵션 목록에서 한 번만 사용할 수 있습니다. 예를 들어 PCL 렌더링 유형을 지정하는 PRINT 옵션은 각각 두 개 가질 수 없습니다.

- 일괄 처리 구성의 경우 OutputType(PDF, PRINT) 및 RenderType(PostScript, PCL, IPL, ZPL 등)의 값 조합 인스턴스 하나만 가 허용됩니다.

## 우수 사례

- Adobe은 AEM Cloud Service에서 사용하는 클라우드 영역에서 데이터 파일 blob 컨테이너 저장소를 호스팅하도록 권장합니다.

## 자주 묻는 질문 {#faq}

**감시 폴더나 다른 스토리지 메커니즘을 사용하여 입출력 작업을 저장할 수 있습니까?**

현재 Microsoft Azure 저장 공간을 사용하여 입력 데이터와 생성된 문서를 저장할 수 있습니다. Microsoft Azure 저장소는 [데이터 이동 작업 자동화](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10).

**Microsoft Azure 저장 공간 계정이 Experience Manager Forms Cloud Service 라이선스에 포함되어 있습니까?**

Microsoft Azure 저장 공간 계정은 Experience Manager Forms Cloud Service 라이선스와 독립적입니다.

**Communication API는 Experience Manager Forms Cloud Service 서버에 데이터를 저장합니까?**

입력 및 출력 데이터는 Microsoft Azure 저장소에만 저장됩니다.

**Communication API는 Experience Manager Forms Cloud Service에만 사용할 수 있습니까? 온-프레미스 환경에서 유사한 기능을 사용할 수 있습니까?**

AEM Forms 출력 서비스를 사용하여 템플릿(XFA 또는 PDF)을 고객 데이터와 결합하여 PDF, PS, PCL 및 ZPL 형식으로 문서를 생성할 수 있습니다.

온-프레미스 환경과 비교하여 Cloud Service은 자동 확장 및 비용 효율성의 추가적인 이점을 제공합니다.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**여러 배치 작업을 동시에 실행할 수 있습니까?**
예, 여러 배치 작업을 함께 실행할 수 있습니다. 충돌을 방지하려면 모든 작업에 항상 서로 다른 소스 및 대상 폴더를 사용하십시오.
