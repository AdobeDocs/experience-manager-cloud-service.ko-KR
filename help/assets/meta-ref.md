---
title: 메타데이터 스키마 참조
description: 'Dublin Core, IPTC 및 기타 메타데이터 스키마를 비롯한 에셋 메타데이터를 설명하는 표준 규칙에 대해 알아봅니다. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# 메타데이터 스키마 참조 {#metadata-schemata-reference}

다음 참조에는 특정 메타데이터 스키마(알파벳 순서)에 대한 정보와 속성 및 해당 정의 목록이 포함되어 있습니다.

## 더블린 코어 {#dublin-core}

Dublin Core 메타데이터는 보다 쉽게 찾을 수 있도록 자산을 설명하는 표준 규칙 세트를 제공합니다. AEM 자산에서 Dublin Core는 비디오, 사운드, 이미지 및 문서를 비롯한 디지털 자산에 대해 설명합니다.

단순 더블린 코어 메타데이터 요소 세트(DCMES)에는 다음 표에 나열된 15개의 메타데이터 요소가 포함되어 있습니다. 각 더블린 코어 요소는 선택 사항이며 반복될 수 있습니다. 미디어 유형별 메타데이터와 마찬가지로 Dublin Core 메타데이터 정보를 추가하거나 삭제할 수 있습니다.

DCMES 외에도 Dublin Core Initiative에서 만든 기타 메타데이터 요소가 있습니다. 자세한 내용은 [Dublin Core](https://dublincore.org/) Initiative를 참조하십시오.

<table>
 <tbody>
  <tr>
   <td><strong>속성</strong></td> 
   <td><strong>설명</strong></td> 
  </tr>
  <tr>
   <td>contributor</td> 
   <td>컨텐트에 대한 기여를 하는 개인 또는 회사</td> 
  </tr>
  <tr>
   <td>보장</td> 
   <td>자산이 적용되는 지리적 위치 또는 기간입니다.<br /> </td> 
  </tr>
  <tr>
   <td>creator</td> 
   <td>컨텐츠 작성을 담당하는 사람 또는 회사</td> 
  </tr>
  <tr>
   <td>날짜</td> 
   <td>자산과 관련된 날짜 또는 기간<br /> </td> 
  </tr>
  <tr>
   <td>설명</td> 
   <td>자산에 대한 자세한 정보입니다.</td> 
  </tr>
  <tr>
   <td>format</td> 
   <td>자산의 파일 형식, 실제 미디어 또는 크기입니다. AEM에서는 자산의 MIME 유형을 <code>dc:format</code> 나타내는 데 사용됩니다.<br /> </td> 
  </tr>
  <tr>
   <td>식별자</td> 
   <td>자산에 대한 고유 참조입니다.</td> 
  </tr>
  <tr>
   <td>언어</td> 
   <td>자산의 언어(예: 영어)입니다.</td> 
  </tr>
  <tr>
   <td>게시자</td> 
   <td>자산을 사용할 수 있도록 만드는 담당자 또는 회사.</td> 
  </tr>
  <tr>
   <td>관계</td> 
   <td>관련 자산.</td> 
  </tr>
  <tr>
   <td>권리</td> 
   <td>이 자산에 대한 권한이 있는 사용자에 대한 정보입니다.</td> 
  </tr>
  <tr>
   <td>source</td> 
   <td>자산이 파생되는 관련 자산.</td> 
  </tr>
  <tr>
   <td>subject</td> 
   <td>자산의 주제입니다.<br /> </td> 
  </tr>
  <tr>
   <td>제목</td> 
   <td>자산의 이름입니다.</td> 
  </tr>
  <tr>
   <td>유형</td> 
   <td>자산의 특성 또는 장르입니다.</td> 
  </tr>
 </tbody>
</table>

## IPTC {#iptc}

국제 통신 통신 위원회(IPTC)는 전 세계의 뉴스 기관들의 컨소시엄으로, 그것의 목표 중 하나는 기술 표준을 개발하고 유지하는 것입니다. IPTC는 사진 작가가 거의 보편적으로 인정하는 이미지에 대한 일련의 사진 메타데이터 표준을 정의했습니다. 이러한 메타데이터 표준은 199 파섹

IPTC 헤더 정보가 대부분 XMP로 대체되었지만 IPTC 코어 스키마와 확장 스키마를 XMP에 사용할 수 있습니다. 이미지 프로그램에서 XMP 및 IPTC 속성이 모두 동기화됩니다.
