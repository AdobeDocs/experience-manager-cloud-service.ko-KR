---
title: 커뮤니케이션 제작 스킬
description: Experience Production Agent의 커뮤니케이션 생성 기술과 자연어를 사용하여 대화형 커뮤니케이션을 만드는 방법에 대해 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 701c35341ead684cdf306cadcacd8c638004facd
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


# 커뮤니케이션 제작 스킬 {#ic-creation-skill}

대화형 커뮤니케이션은 계정 명세서, 정책 문서, 청구서, 환영 키트 및 혜택 알림과 같은 비즈니스 서신에 맞게 설계된 개인화된 데이터 기반 문서입니다. 사용자의 입력을 수집하는 양식과 달리 대화형 커뮤니케이션은 동적이고 수신자별 컨텐츠가 포함된 출력 문서를 생성합니다.

커뮤니케이션 제작 기술은 자연어 프롬프트를 사용하여 대화형 커뮤니케이션을 개발하도록 설계된 Experience Production Agent의 기능입니다. 이 스킬은 인쇄에 대한 개인화된 데이터 기반 서신을 자동으로 생성합니다(PDF 형식). 이 기술은 AI 비서를 통해 제공됩니다.

커뮤니케이션 작성 기술의 주요 이점은 다음과 같습니다.

* **통신 개발 가속화**: 간단한 자연어 명령을 사용하여 통신을 신속하게 만들 수 있으므로 기존 제품 인터페이스를 학습할 필요가 없습니다.
* **일관된 브랜드 내 서신**: 승인된 템플릿과 스타일을 사용하여 조직의 브랜딩, 템플릿 및 스타일 지침을 따르는 커뮤니케이션을 만듭니다.
* **낮은 기술 장벽**: 고급 기술 전문가 또는 심층적인 제품 전문 지식 없이도 비즈니스 사용자가 손쉽게 커뮤니케이션을 만들 수 있습니다.

## 기능 {#capabilities}

<!-- * **Create personalized communications with plain text prompt**: You can create communication documents for print (in PDF format) by submitting your requirements in plain language. The agent automatically generates appropriate document structures, layouts, and data bindings based on your natural language description. -->

* **템플릿에서 만들기**: 승인된 조직 템플릿을 사용하여 브랜드 일관성 및 준수 표준을 보장할 수 있습니다. 에이전트는 기존 템플릿과 스타일 지침을 활용하여 규제 요구 사항을 충족하는 온브랜드 서신을 생성합니다.

* **기존 이미지 및 문서를 대화형 통신으로 가져오기 및 변환**: 기존 문서를 대화형 통신으로 가져오고 변환할 수 있습니다. 에이전트는 업로드된 콘텐츠를 분석하여 필드를 감지하고 레이아웃을 보존하며 동적 콘텐츠 기능을 통해 데이터 기반 서신을 생성합니다. 지원되는 형식에는 PDF, 이미지(JPG, PNG) 및 손으로 그린 템플릿이 포함됩니다.


## 샘플 프롬프트 {#sample-prompts}

* *https://[aem-author-url]/path/to/pdf/file*&#x200B;에서 템플릿을 사용하여 대출 내역에 대한 통신 만들기
* *https://에서 PDF 통신 만들기[aem-author-url]/path/to/pdf/file*
* *https://의 이미지 파일에서 통신 만들기[aem-author-url]/path/to/image/file*
* https://[aem-author-url]/path/to/pdf/file에서 PDF 파일을 사용하여 편지 만들기

## 커뮤니케이션 세분화 {#refine-with-ic-editor}

AI Assistant를 사용하여 초기 통신 구조를 작성한 후 대화형 통신 편집기를 사용하여 문서를 구체화하고 향상시킬 수 있습니다. 대화형 통신 편집기에서 다음 작업을 수행하는 데 자연어로 프롬프트를 제공할 수 있습니다.

* **필드 및 콘텐츠 추가**: 자연어 프롬프트를 사용하여 통신 문서에 새 필드, 텍스트 블록, 이미지, 차트, 표 및 기타 구성 요소를 추가합니다. 에이전트는 지침을 해석하고 적절한 구조와 형식으로 적절한 요소를 삽입합니다.

* **필드 및 콘텐츠 편집**: 대화 명령을 통해 통신 문서 내의 기존 필드 및 콘텐츠를 수정합니다. 필드 속성을 업데이트하고, 텍스트 콘텐츠를 변경하고, 데이터 바인딩을 조정하고, 구성 요소 구성을 세분화합니다.

* **필드 및 콘텐츠 제거**: 자연어 지침을 사용하여 통신 문서에서 원치 않는 필드, 구성 요소 또는 섹션을 삭제합니다. 에이전트는 문서 구조 및 레이아웃 무결성을 유지하면서 지정된 요소를 제거합니다.

* **필드 및 콘텐츠 스타일 지정**: 자연어 프롬프트를 통해 필드 및 콘텐츠에 서식 및 스타일을 적용합니다. 브랜드 가이드라인과 디자인 요구 사항에 맞게 글꼴, 색상, 정렬, 간격 및 기타 시각적 속성을 조정합니다.

### 통신 세분화를 위한 샘플 프롬프트 {#sample-prompts-refining}

* *차량 보험 청구 결제 편지 생성*
* *면책조항 텍스트를 기울임꼴로 만들기*
* *면책조항 텍스트의 글꼴 크기를 12로 변경*
* *면책조항 텍스트의 글꼴 색상을 빨간색으로 업데이트*
* *머리글 및 바닥글 텍스트 상자의 배경색을 밝은 회색으로 업데이트*
* *서명 및 확인 필드가 있는 새 면책조항 패널 추가*
* *확인 텍스트 필드 제거*
* *3개의 열이 있는 결제 세부 정보 테이블 추가*
* *정책 번호 필드를 가운데로 정렬합니다*
* *약관 섹션의 줄 간격을 1.5로 변경합니다*

대화형 통신 편집기의 기능에 대한 자세한 내용은 [대화형 통신 문서](/help/forms/introduction-to-interactive-communication.md)를 참조하십시오.

