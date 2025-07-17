---
title: HTML5 양식에 대한 그림 절 지원
description: HTML5 forms에서는 날짜, 텍스트 및 숫자 기호에 대한 표시 값 및 서식 있는 값에 대한 XFA Picture 절을 지원합니다.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5e344be7-46cd-4e1f-ae3a-1f89c645cffe
feature: HTML5 Forms,Mobile Forms
exl-id: 7f9c77c6-447a-407f-ae58-6735176dc99c
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 1%

---

# HTML5 양식에 대한 그림 절 지원 {#picture-clause-support-for-html-forms}

<span class="preview"> HTML5 Forms 기능은 조기 액세스 프로그램의 일부로 제공됩니다. 액세스 권한을 요청하려면 공식(회사) 이메일 ID에서 aem-forms-ea@adobe.com으로 이메일을 보내십시오.
</span>

HTML5 forms에서는 날짜, 텍스트 및 숫자 기호에 대한 표시 값 및 서식 있는 값에 대한 XFA Picture 절을 지원합니다. 지원되는 Picture 절 식은 다음과 같습니다.

* category(locale){picture-clause} | category(locale){picture-clause} | category(locale){picture-clause}
* category.subcategory{}

>[!NOTE]
>
>현재 Mobiles Forms은 Edit Picture 절을 지원하지 않습니다. 또한 DateTime 및 Time Picture 절 기호는 지원되지 않습니다.

## 지원되는 날짜 필드 기호 {#supported-date-field-symbols}

Date Picture 절에 지원되는 표현식:

* date.long{}
* date.short{}
* date.medium{}
* date.full{}
* date.short{}
* 날짜{date Picture Clause symbols}

>[!NOTE]
>
>picture 절의 기본 패턴은 {MMM D, YYYY} 패턴입니다. 패턴이 적용되지 않으면 기본 패턴이 사용됩니다.

<table>
 <tbody>
  <tr>
   <th><strong>기호</strong></th>
   <th>해석</th>
  </tr>
  <tr>
   <td>D</td>
   <td>해당 월의 1-31일 또는 2자리</td>
  </tr>
  <tr>
   <td>DD</td>
   <td>01-31일(한 달 기준)의 두 숫자를 0으로 채워넣었습니다.<br /> </td>
  </tr>
  <tr>
   <td>월</td>
   <td>1-12자리(한 해의 1-12자리) 월.<br /> </td>
  </tr>
  <tr>
   <td>MM</td>
   <td>한 해의 두 자리(01-12)를 0으로 채웠습니다.<br /> </td>
  </tr>
  <tr>
   <td>MMM</td>
   <td>현재 로케일의 약식 월 이름<br /> </td>
  </tr>
  <tr>
   <td>MMMM</td>
   <td>현재 로케일의 전체 월 이름<br /> </td>
  </tr>
  <tr>
   <td>EEE</td>
   <td>현재 로케일의 약식 요일 이름<br /> </td>
  </tr>
  <tr>
   <td>EEEE</td>
   <td>현재 로케일의 전체 평일 이름<br /> </td>
  </tr>
  <tr>
   <td>YY</td>
   <td>2자리 연도. 여기서 00 = 2000, 29 = 2029, 30 = 1930, 99 = 1999<br /> </td>
  </tr>
  <tr>
   <td>YYYY</td>
   <td>4자리 연도<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
> 디자인에 따라 HTML5 Forms의 날짜 필드는 편집 형식의 `MM-YYYY` 패턴을 지원하지 않습니다. 그러나 패턴은 표시 형식으로 지원됩니다.

## 숫자 그림 절 {#numeric-picture-clause}

HTML5 forms는 숫자 그림 기호를 지원합니다. 다만 PDF forms과 HTML Forms은 지원에 차이가 있다.

**PDF forms**&#x200B;에서 Picture 절의 기호 수에 관계없이 숫자의 형식이 지정됩니다

**HTML Forms**&#x200B;에서 숫자는 그림 절의 기호 수보다 적은 숫자만 사용할 수 있습니다.

**예**: Picture 절을 고려하십시오. num{zzz,zzz,zz9}.

HTML과 PDF forms 모두에서 숫자 **10000**&#x200B;의 형식이 **10,000**(으)로 지정되었습니다.

PDF forms1000000 숫자 형식은 1,000,000입니다. 그러나 HTML Forms에서는 숫자의 서식이 지정되지 않은 상태로 1000000.

**HTML Forms**&#x200B;에서 Numeric Picture 절에 지원되는 식은 다음과 같습니다.

* num.integer{}
* num.decimal{}
* num.currency{}
* num.percent{}
* num{Numeric Picture Clause Symbols}

<table>
 <tbody>
  <tr>
   <th><strong>기호</strong></th>
   <th><strong>해석</strong></th>
   <th>입력 구문 분석</th>
  </tr>
  <tr>
   <td>9</td>
   <td><strong>출력 서식</strong>: 한 자리 숫자입니다. 또는 입력 데이터가 비어 있거나 해당 위치에 공백이 있으면 0자리입니다.<br /> </td>
   <td>한 자리</td>
  </tr>
  <tr>
   <td>Z</td>
   <td><strong>출력 서식</strong>: 한 자리 숫자입니다. 또는 입력 데이터가 비어 있는 경우 공백, 해당 위치에 있는 0자리 또는 공백입니다.<br /> </td>
   <td>한 자리 또는 공백</td>
  </tr>
  <tr>
   <td>z</td>
   <td><strong>출력 서식</strong>: 한 자리 숫자입니다. 입력 데이터가 비어 있거나, 공백 또는 해당 위치에 있는 0자리이면 아무 것도 안 됩니다.<br /> </td>
   <td>한 자리 또는 아무 것도 아님</td>
  </tr>
  <tr>
   <td>오류</td>
   <td><strong>출력 서식</strong>: 지수 기호(E)로 구성된 부동 소수점 숫자의 지수 부분입니다. 뒤에 더하기 또는 빼기 기호(선택 사항)가 옵니다. 뒤에 지수 값이 옵니다.<br /> </td>
   <td>출력 서식과 동일</td>
  </tr>
  <tr>
   <td>CR 또는 cr<br /> </td>
   <td>숫자가 음수인 경우 신용 기호(CR). 다른 건 없어</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>S 또는 s<br /> </td>
   <td>출력 형식: 숫자가 음수이면 빼기 기호입니다. Else 스페이스입니다.<br /> </td>
   <td>숫자가 음수이면 빼기 기호가 표시됩니다. 숫자가 양수이면 더하기 기호</td>
  </tr>
  <tr>
   <td>V</td>
   <td>널리 사용되는 로케일의 십진수 반경. 입력 구문 분석 시 십진수 반지름을 암시하도록 허용합니다.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>v</td>
   <td>널리 사용되는 로케일의 십진수 반경. 입력 구문 분석 및 출력 형식 지정 시 십진수 반지름을 암시할 수 있도록 합니다.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>.</td>
   <td>널리 사용되는 로케일의 십진수 반경.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>, (U+FF0C)</td>
   <td>기본 로케일의 그룹화 구분 기호</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>$(U+FF04)</td>
   <td>일반 로케일의 통화 기호.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>%(U+FF05)</td>
   <td>일반 로케일의 백분율 기호.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>(U+FF08)</td>
   <td>숫자가 음수인 경우 왼쪽 괄호. Else space공간 .</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>) (U+FF09)</td>
   <td>숫자가 음수인 경우 오른쪽 괄호. Else space공간 .</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>t</td>
   <td>탭 문자</td>
   <td><br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## 텍스트 그림 절 {#text-picture-clause}

HTML5 forms는 다음 Text Picture 절 표현식을 지원합니다.

* text{text Picture clause symbols}

| **기호** | **해석** |
|---|---|
| A | 단일 알파벳 문자 |
| X | 단일 문자 |
| O | 단일 영숫자 문자 |
| 0(영) | 단일 영숫자 문자 |
| 9 | 한 자리 숫자. |
