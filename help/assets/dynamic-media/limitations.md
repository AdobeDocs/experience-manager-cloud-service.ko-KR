---
title: Dynamic Media 제한 사항
description: 이미지 세트 또는 스핀 세트를 만들거나 PDF을 업로드할 때 모범 사례 및 강제 제한에 대해 알아봅니다. Dynamic Media Viewer용 지원되지 않는 웹 브라우저 및 운영 체제 조합에 대해서도 알아봅니다.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Viewers,Image Sets,Spin Sets,eCatalog
role: User
exl-id: fb63e2d4-2c8c-48dd-a0dc-fdfbbfb57b30
source-git-commit: 479349d2dad841a782519de3302993ea2a9f5162
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 4%

---

# Dynamic Media 제한 사항

다음 섹션에서는 Dynamic Media의 제한 사항에 대해 설명합니다.

이 주제에는 다음 섹션이 포함됩니다.

* [자산 유형에 대한 Dynamic Media의 우수 사례 및 강제 제한](#best-practice-enforced-limits)
* [Dynamic Media 뷰어용 지원되지 않는 웹 브라우저 및 운영 체제 조합](#unsupported-browser-os)

## 자산 유형에 대한 Dynamic Media의 우수 사례 및 강제 제한 {#best-practice-enforced-limits}

스핀 세트 또는 이미지 세트를 만들거나 페이지 추출을 위해 PDF을 업로드할 때 Adobe은 다음 우수 사례를 권장하고 다음 제한을 적용합니다.

| 자산 - 제한 유형 | 우수 사례 | 제한 적용 | 2022년 12월 31일에 제한하는 것으로 변경 |
| --- | --- | --- | --- |
| **이미지** - 이미지당 스마트 자르기 수 | 5 | 100 | 20 |
| **모든 세트** - 세트당 중복 자산 수 | 중복 없음 | 20년 | 해당되지 않음 |
| **모든 세트** - 세트당 최대 자산 수 | 세트당 5-10개 이미지 | 1000 | 해당되지 않음 |
| **스핀 세트** - 2D 세트당 최대 행/열 수 | 세트당 12-18개 이미지 | 1000년 | 해당되지 않음 |
| **PDF** - 추출할 PDF에 대한 최대 페이지 수 |  | 5000(새 업로드의 경우) | 100(모든 PDF에 대해) |

<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Dynamic Media 뷰어용 지원되지 않는 웹 브라우저 및 운영 체제 조합 {#unsupported-browser-os}

Dynamic Media 뷰어는 다음 웹 브라우저 및 운영 체제 조합을 지원하지 않습니다.

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1 업데이트
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9 Mavericks
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

## TLS 1.0 및 1.1 지원 종료 {#tls}

<!-- CQDOC-19433 -->

2022년 9월 30일부터 Adobe Dynamic Media Viewer는 다음 사항에 대한 지원을 종료합니다.

* TLS(전송 계층 보안) 1.0 및 1.1
* TLS 1.2에 있는 다음의 약한 암호:
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_RSA_WITH_AES_256_GCM_SHA384`
   * `TLS_RSA_WITH_AES_256_CBC_SHA256`
   * `TLS_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_AES_128_GCM_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
   * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

