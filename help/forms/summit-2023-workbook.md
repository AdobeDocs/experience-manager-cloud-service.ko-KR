---
title: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
exl-id: e1eb0812-c92e-4a18-aabb-5a70b9e6fc7d
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '3359'
ht-degree: 99%

---

# 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성

## 랩 개요

이 실습 랩에서는 다음과 같은 사항을 알아봅니다.

AEM Forms를 사용하여 AEM Sites와 일치하는 최신 핵심 구성 요소를 사용해 적응형 양식을 쉽게 만드는 방법, 적응형 양식을 웹, 모바일 및 채팅에 헤드리스 양식으로 제공하여 옴니채널 데이터 캡처 경험을 가능하게 하는 방법. 또한 스타일링, 사용자 정의 및 프론트엔드 개발에 대한 모범 사례를 살펴봅니다.

## 핵심 사항

* **비즈니스 민첩성**: 비즈니스 사용자로서 여러 채널의 양식 경험을 쉽게 작성할 수 있습니다.

* **프론트엔드 개발자의 능력**: 프론트엔드 개발자로서 Headless 양식을 사용하여 최종 사용자 경험을 제어할 수 있습니다.

* **개발자 속도**: 개발자로서 Sites 및 Forms 구성 요소를 쉽고 일관되게 사용자 정의할 수 있습니다.

## 사전 요구 사항


+++AEM Forms as Cloud Service 샌드박스



<table>
        <thead>
            <tr><th>랩 ID</th><th>작성자 인스턴스 URL</th><th>게시 인스턴스 URL</th></tr>           
        </thead>
        <tbody>
            <tr><td>L716001</td><td>https://author-p105303-e986623.adobeaemcloud.com</td><td>https://publish-p105303-e986623.adobeaemcloud.com</td></tr><tr><td>L716002</td><td>https://author-p106405-e993047.adobeaemcloud.com</td><td>https://publish-p106405-e993047.adobeaemcloud.com</td></tr><tr><td>L716003</td><td>https://author-p106406-e993049.adobeaemcloud.com</td><td>https://publish-p106406-e993049.adobeaemcloud.com</td></tr><tr><td>L716004</td><td>https://author-p106398-e993114.adobeaemcloud.com</td><td>https://publish-p106398-e993114.adobeaemcloud.com</td></tr><tr><td>L716005</td><td>https://author-p106407-e993048.adobeaemcloud.com</td><td>https://publish-p106407-e993048.adobeaemcloud.com</td></tr><tr><td>L716006</td><td>https://author-p106408-e993155.adobeaemcloud.com</td><td>https://publish-p106408-e993155.adobeaemcloud.com</td></tr><tr><td>L716007</td><td>https://author-p106343-e993067.adobeaemcloud.com</td><td>https://publish-p106343-e993067.adobeaemcloud.com</td></tr><tr><td>L716008</td><td>https://author-p106399-e993108.adobeaemcloud.com</td><td>https://publish-p106399-e993108.adobeaemcloud.com</td></tr><tr><td>L716009</td><td>https://author-p106344-e993064.adobeaemcloud.com</td><td>https://publish-p106344-e993064.adobeaemcloud.com</td></tr><tr><td>L716010</td><td>https://author-p106409-e993051.adobeaemcloud.com</td><td>https://publish-p106409-e993051.adobeaemcloud.com</td></tr><tr><td>L716011</td><td>https://author-p106345-e993060.adobeaemcloud.com</td><td>https://publish-p106345-e993060.adobeaemcloud.com</td></tr><tr><td>L716012</td><td>https://author-p106346-e993061.adobeaemcloud.com</td><td>https://publish-p106346-e993061.adobeaemcloud.com</td></tr><tr><td>L716013</td><td>https://author-p106410-e993153.adobeaemcloud.com</td><td>https://publish-p106410-e993153.adobeaemcloud.com</td></tr><tr><td>L716014</td><td>https://author-p106502-e993073.adobeaemcloud.com</td><td>https://publish-p106502-e993073.adobeaemcloud.com</td></tr><tr><td>L716015</td><td>https://author-p106401-e993112.adobeaemcloud.com</td><td>https://publish-p106401-e993112.adobeaemcloud.com</td></tr><tr><td>L716016</td><td>https://author-p106452-e993115.adobeaemcloud.com</td><td>https://publish-p106452-e993115.adobeaemcloud.com</td></tr><tr><td>L716017</td><td>https://author-p106453-e993113.adobeaemcloud.com</td><td>https://publish-p106453-e993113.adobeaemcloud.com</td></tr><tr><td>L716018</td><td>https://author-p106411-e993050.adobeaemcloud.com</td><td>https://publish-p106411-e993050.adobeaemcloud.com</td></tr><tr><td>L716019</td><td>https://author-p106454-e993116.adobeaemcloud.com</td><td>https://publish-p106454-e993116.adobeaemcloud.com</td></tr><tr><td>L716020</td><td>https://author-p106347-e993063.adobeaemcloud.com</td><td>https://publish-p106347-e993063.adobeaemcloud.com</td></tr><tr><td>L716021</td><td>https://author-p106455-e993109.adobeaemcloud.com</td><td>https://publish-p106455-e993109.adobeaemcloud.com</td></tr><tr><td>L716022</td><td>https://author-p106456-e993110.adobeaemcloud.com</td><td>https://publish-p106456-e993110.adobeaemcloud.com</td></tr><tr><td>L716023</td><td>https://author-p106466-e993291.adobeaemcloud.com</td><td>https://publish-p106466-e993291.adobeaemcloud.com</td></tr><tr><td>L716024</td><td>https://author-p106413-e993156.adobeaemcloud.com</td><td>https://publish-p106413-e993156.adobeaemcloud.com</td></tr><tr><td>L716025</td><td>https://author-p106348-e993066.adobeaemcloud.com</td><td>https://publish-p106348-e993066.adobeaemcloud.com</td></tr><tr><td>L716026</td><td>https://author-p106414-e993154.adobeaemcloud.com</td><td>https://publish-p106414-e993154.adobeaemcloud.com</td></tr><tr><td>L716027</td><td>https://author-p106349-e993065.adobeaemcloud.com</td><td>https://publish-p106349-e993065.adobeaemcloud.com</td></tr><tr><td>L716028</td><td>https://author-p106415-e993152.adobeaemcloud.com</td><td>https://publish-p106415-e993152.adobeaemcloud.com</td></tr><tr><td>L716029</td><td>https://author-p106350-e993068.adobeaemcloud.com</td><td>https://publish-p106350-e993068.adobeaemcloud.com</td></tr><tr><td>L716030</td><td>https://author-p106351-e993062.adobeaemcloud.com</td><td>https://publish-p106351-e993062.adobeaemcloud.com</td></tr><tr><td>L716031</td><td>https://author-p106417-e993158.adobeaemcloud.com</td><td>https://publish-p106417-e993158.adobeaemcloud.com</td></tr><tr><td>L716032</td><td>https://author-p106418-e993159.adobeaemcloud.com</td><td>https://publish-p106418-e993159.adobeaemcloud.com</td></tr><tr><td>L716033</td><td>https://author-p106503-e993080.adobeaemcloud.com</td><td>https://publish-p106503-e993080.adobeaemcloud.com</td></tr><tr><td>L716034</td><td>https://author-p106457-e993125.adobeaemcloud.com</td><td>https://publish-p106457-e993125.adobeaemcloud.com</td></tr><tr><td>L716035</td><td>https://author-p106504-e993081.adobeaemcloud.com</td><td>https://publish-p106504-e993081.adobeaemcloud.com</td></tr><tr><td>L716036</td><td>https://author-p106458-e993120.adobeaemcloud.com</td><td>https://publish-p106458-e993120.adobeaemcloud.com</td></tr><tr><td>L716037</td><td>https://author-p106419-e993160.adobeaemcloud.com</td><td>https://publish-p106419-e993160.adobeaemcloud.com</td></tr><tr><td>L716038</td><td>https://author-p106420-e993162.adobeaemcloud.com</td><td>https://publish-p106420-e993162.adobeaemcloud.com</td></tr><tr><td>L716039</td><td>https://author-p106517-e993235.adobeaemcloud.com</td><td>https://publish-p106517-e993235.adobeaemcloud.com</td></tr><tr><td>L716040</td><td>https://author-p106506-e993079.adobeaemcloud.com</td><td>https://publish-p106506-e993079.adobeaemcloud.com</td></tr><tr><td>L716041</td><td>https://author-p106507-e993074.adobeaemcloud.com</td><td>https://publish-p106507-e993074.adobeaemcloud.com</td></tr><tr><td>L716042</td><td>https://author-p106508-e993075.adobeaemcloud.com</td><td>https://publish-p106508-e993075.adobeaemcloud.com</td></tr><tr><td>L716043</td><td>https://author-p106421-e993163.adobeaemcloud.com</td><td>https://publish-p106421-e993163.adobeaemcloud.com</td></tr><tr><td>L716044</td><td>https://author-p106459-e993121.adobeaemcloud.com</td><td>https://publish-p106459-e993121.adobeaemcloud.com</td></tr><tr><td>L716045</td><td>https://author-p106467-e993292.adobeaemcloud.com</td><td>https://publish-p106467-e993292.adobeaemcloud.com</td></tr><tr><td>L716046</td><td>https://author-p106518-e993234.adobeaemcloud.com</td><td>https://publish-p106518-e993234.adobeaemcloud.com</td></tr><tr><td>L716047</td><td>https://author-p106511-e993076.adobeaemcloud.com</td><td>https://publish-p106511-e993076.adobeaemcloud.com</td></tr><tr><td>L716048</td><td>https://author-p106512-e993077.adobeaemcloud.com</td><td>https://publish-p106512-e993077.adobeaemcloud.com</td></tr><tr><td>L716049</td><td>https://author-p106460-e993124.adobeaemcloud.com</td><td>https://publish-p106460-e993124.adobeaemcloud.com</td></tr><tr><td>L716050</td><td>https://author-p106519-e993237.adobeaemcloud.com</td><td>https://publish-p106519-e993237.adobeaemcloud.com</td></tr><tr><td>L716051</td><td>https://author-p106513-e993084.adobeaemcloud.com</td><td>https://publish-p106513-e993084.adobeaemcloud.com</td></tr><tr><td>L716052</td><td>https://author-p106461-e993122.adobeaemcloud.com</td><td>https://publish-p106461-e993122.adobeaemcloud.com</td></tr><tr><td>L716053</td><td>https://author-p106514-e993082.adobeaemcloud.com</td><td>https://publish-p106514-e993082.adobeaemcloud.com</td></tr><tr><td>L716054</td><td>https://author-p106462-e993123.adobeaemcloud.com</td><td>https://publish-p106462-e993123.adobeaemcloud.com</td></tr><tr><td>L716055</td><td>https://author-p106463-e993127.adobeaemcloud.com</td><td>https://publish-p106463-e993127.adobeaemcloud.com</td></tr><tr><td>L716056</td><td>https://author-p106515-e993083.adobeaemcloud.com</td><td>https://publish-p106515-e993083.adobeaemcloud.com</td></tr><tr><td>L716057</td><td>https://author-p106464-e993126.adobeaemcloud.com</td><td>https://publish-p106464-e993126.adobeaemcloud.com</td></tr><tr><td>L716058</td><td>https://author-p106520-e993236.adobeaemcloud.com</td><td>https://publish-p106520-e993236.adobeaemcloud.com</td></tr><tr><td>L716059</td><td>https://author-p106423-e993161.adobeaemcloud.com</td><td>https://publish-p106423-e993161.adobeaemcloud.com</td></tr><tr><td>L716060</td><td>https://author-p106516-e993078.adobeaemcloud.com</td><td>https://publish-p106516-e993078.adobeaemcloud.com</td></tr><tr><td>L716061</td><td>https://author-p106521-e993240.adobeaemcloud.com</td><td>https://publish-p106521-e993240.adobeaemcloud.com</td></tr><tr><td>L716062</td><td>https://author-p106424-e993308.adobeaemcloud.com</td><td>https://publish-p106424-e993308.adobeaemcloud.com</td></tr><tr><td>L716063</td><td>https://author-p106468-e993295.adobeaemcloud.com</td><td>https://publish-p106468-e993295.adobeaemcloud.com</td></tr><tr><td>L716064</td><td>https://author-p106425-e993309.adobeaemcloud.com</td><td>https://publish-p106425-e993309.adobeaemcloud.com</td></tr><tr><td>L716065</td><td>https://author-p106426-e993314.adobeaemcloud.com</td><td>https://publish-p106426-e993314.adobeaemcloud.com</td></tr><tr><td>L716066</td><td>https://author-p106469-e993293.adobeaemcloud.com</td><td>https://publish-p106469-e993293.adobeaemcloud.com</td></tr><tr><td>L716067</td><td>https://author-p106522-e993238.adobeaemcloud.com</td><td>https://publish-p106522-e993238.adobeaemcloud.com</td></tr><tr><td>L716068</td><td>https://author-p106470-e993299.adobeaemcloud.com</td><td>https://publish-p106470-e993299.adobeaemcloud.com</td></tr><tr><td>L716069</td><td>https://author-p106427-e993311.adobeaemcloud.com</td><td>https://publish-p106427-e993311.adobeaemcloud.com</td></tr><tr><td>L716070</td><td>https://author-p106428-e993310.adobeaemcloud.com</td><td>https://publish-p106428-e993310.adobeaemcloud.com</td></tr><tr><td>L716071</td><td>https://author-p106471-e993298.adobeaemcloud.com</td><td>https://publish-p106471-e993298.adobeaemcloud.com</td></tr><tr><td>L716072</td><td>https://author-p106429-e993315.adobeaemcloud.com</td><td>https://publish-p106429-e993315.adobeaemcloud.com</td></tr><tr><td>L716073</td><td>https://author-p106523-e993239.adobeaemcloud.com</td><td>https://publish-p106523-e993239.adobeaemcloud.com</td></tr><tr><td>L716074</td><td>https://author-p106472-e993300.adobeaemcloud.com</td><td>https://publish-p106472-e993300.adobeaemcloud.com</td></tr><tr><td>L716075</td><td>https://author-p106430-e993312.adobeaemcloud.com</td><td>https://publish-p106430-e993312.adobeaemcloud.com</td></tr><tr><td>L716076</td><td>https://author-p106524-e993241.adobeaemcloud.com</td><td>https://publish-p106524-e993241.adobeaemcloud.com</td></tr><tr><td>L716077</td><td>https://author-p106431-e993313.adobeaemcloud.com</td><td>https://publish-p106431-e993313.adobeaemcloud.com</td></tr><tr><td>L716078</td><td>https://author-p106473-e993294.adobeaemcloud.com</td><td>https://publish-p106473-e993294.adobeaemcloud.com</td></tr><tr><td>L716079</td><td>https://author-p106474-e993297.adobeaemcloud.com</td><td>https://publish-p106474-e993297.adobeaemcloud.com</td></tr><tr><td>L716080</td><td>https://author-p106475-e993296.adobeaemcloud.com</td><td>https://publish-p106475-e993296.adobeaemcloud.com</td></tr><tr><td>L716081</td><td>https://author-p106476-e993353.adobeaemcloud.com</td><td>https://publish-p106476-e993353.adobeaemcloud.com</td></tr><tr><td>L716082</td><td>https://author-p106525-e993247.adobeaemcloud.com</td><td>https://publish-p106525-e993247.adobeaemcloud.com</td></tr><tr><td>L716083</td><td>https://author-p106526-e993244.adobeaemcloud.com</td><td>https://publish-p106526-e993244.adobeaemcloud.com</td></tr><tr><td>L716084</td><td>https://author-p106527-e993243.adobeaemcloud.com</td><td>https://publish-p106527-e993243.adobeaemcloud.com</td></tr><tr><td>L716085</td><td>https://author-p106477-e993356.adobeaemcloud.com</td><td>https://publish-p106477-e993356.adobeaemcloud.com</td></tr><tr><td>L716086</td><td>https://author-p106478-e993355.adobeaemcloud.com</td><td>https://publish-p106478-e993355.adobeaemcloud.com</td></tr><tr><td>L716087</td><td>https://author-p106528-e993245.adobeaemcloud.com</td><td>https://publish-p106528-e993245.adobeaemcloud.com</td></tr><tr><td>L716088</td><td>https://author-p106432-e993316.adobeaemcloud.com</td><td>https://publish-p106432-e993316.adobeaemcloud.com</td></tr><tr><td>L716089</td><td>https://author-p106529-e993242.adobeaemcloud.com</td><td>https://publish-p106529-e993242.adobeaemcloud.com</td></tr><tr><td>L716090</td><td>https://author-p106436-e993320.adobeaemcloud.com</td><td>https://publish-p106436-e993320.adobeaemcloud.com</td></tr><tr><td>L716091</td><td>https://author-p106480-e993301.adobeaemcloud.com</td><td>https://publish-p106480-e993301.adobeaemcloud.com</td></tr><tr><td>L716092</td><td>https://author-p106530-e993246.adobeaemcloud.com</td><td>https://publish-p106530-e993246.adobeaemcloud.com</td></tr><tr><td>L716093</td><td>https://author-p106481-e993352.adobeaemcloud.com</td><td>https://publish-p106481-e993352.adobeaemcloud.com</td></tr><tr><td>L716094</td><td>https://author-p106482-e993354.adobeaemcloud.com</td><td>https://publish-p106482-e993354.adobeaemcloud.com</td></tr><tr><td>L716095</td><td>https://author-p106531-e993248.adobeaemcloud.com</td><td>https://publish-p106531-e993248.adobeaemcloud.com</td></tr><tr><td>L716096</td><td>https://author-p106483-e993357.adobeaemcloud.com</td><td>https://publish-p106483-e993357.adobeaemcloud.com</td></tr><tr><td>L716097</td><td>https://author-p106433-e993318.adobeaemcloud.com</td><td>https://publish-p106433-e993318.adobeaemcloud.com</td></tr><tr><td>L716098</td><td>https://author-p106532-e993249.adobeaemcloud.com</td><td>https://publish-p106532-e993249.adobeaemcloud.com</td></tr><tr><td>L716099</td><td>https://author-p106434-e993317.adobeaemcloud.com</td><td>https://publish-p106434-e993317.adobeaemcloud.com</td></tr><tr><td>L716100</td><td>https://author-p106435-e993319.adobeaemcloud.com</td><td>https://publish-p106435-e993319.adobeaemcloud.com</td></tr>
        </tbody>
</table>

+++

## 수업 1

### 목표

AEM Forms as a Cloud Service 환경을 숙지합니다.

### 수업 컨텍스트

이 수업에서는 사용자 인터페이스를 탐색하며 AEM Forms as a Cloud Service 환경을 숙지합니다.

### 연습

1. 브라우저를 열고 Cloud Service 작성자 환경의 URL을 입력합니다.

1. Cloud Service 작성자 환경에 로그인합니다. 작성자 환경에 대한 로그인 자격 증명은 실습 중에 사용자와 공유됩니다.

1. 로그인한 후 AEM Forms UI로 이동합니다. **Forms**&#x200B;를 클릭합니다.

   ![](/help/forms/assets/screenshot2028113829.png)

1. **양식 및 문서**&#x200B;를 클릭합니다. 환경 설정 또는 정보와 관련된 모든 팝업을 닫습니다.

   ![](/help/forms/assets/screenshot2028113929.png)

   사용 가능한 모든 양식이 표시됩니다.

   ![](/help/forms/assets/screenshot2028114029.png)

## 수업 2

### 목표

최신 핵심 구성 요소를 사용하여 적응형 양식을 작성하고 양식을 구성 및 제출합니다.

### 수업 컨텍스트

이 수업에서는 비즈니스 사용자로서 데이터 캡처를 위한 표준화된 OOTB 핵심 구성 요소로 적응형 양식 작성을 사용하여 웹, 모바일 및 채팅과 같은 여러 채널의 적응형 양식을 작성합니다.

### 연습

1. 양식의 제출 엔드포인트를 만듭니다.

   1. 새 브라우저 탭에서 <https://requestbin.com/>을 엽니다.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. **공개 bin 만들기**를 클릭하고 엔드포인트 URL을 복사합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. 마법사 인터페이스를 사용하여 적응형 양식 작성:

   1. 수업 1에 사용된 브라우저 탭에서 AEM Forms as Cloud Service 웹 인터페이스로 이동한 후 양식 및 문서로 이동합니다.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. **만들기**를 클릭하고 적응형 양식을 선택합니다.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. 아래와 같이 템플릿 선택 화면에서 **핵심 구성 요소가 있는 빈 내용** 템플릿을 선택합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. **스타일** 탭을 클릭하고 아래와 같이 **wknd-theme** 테마를 선택합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. **제출** 탭을 클릭하고 **REST 엔드포인트에 제출** 카드를 선택한 후
      아래와 같이 **POST 요청의 URL** 필드에서 공개 bin을 지정합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. **만들기**&#x200B;를 클릭합니다. 양식에 이름 및 제목을 지정합니다. 예: **contactus**. **만들기**를 클릭합니다.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. 적응형 양식 편집기가 열립니다. 환경 설정 또는 정보와 관련된 모든 팝업이나 대화 상자를 닫습니다. 왼쪽 레일에서 구성 요소 브라우저를 클릭하고 빈 양식 하단에 **바닥글** 구성 요소를 추가합니다.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. 헤더는 적응형 양식 템플릿의 일부입니다. 모든 적응형 양식에서 일관된 헤더/바닥글을 쉽게 제공할 수 있습니다. 또는 다음 단계에서 바닥글 구성 요소에 대해 표시되는 것처럼, 양식에서 헤더/바닥글을 편집 가능한 상태로 유지할 수도 있습니다.

   1. 양식 중간에 **제목** 구성 요소를 추가합니다.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. 제목 구성 요소 뒤에 **텍스트 입력** 구성 요소를 추가합니다.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. **숫자 입력** 구성 요소를 추가합니다.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. 양식에 **제출 버튼** 구성 요소를 추가합니다.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. **제목** 구성 요소를 클릭하여 **팝업 메뉴**&#x200B;가 표시되도록 합니다. 메뉴의 **편집 아이콘**을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. 제목 텍스트로 `Contact Us`를 입력합니다.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. **텍스트 입력** 구성 요소를 클릭하여 팝업 메뉴가 표시되도록 합니다. 메뉴의 **편집 아이콘**을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. 필드 레이블로 **전체 이름**을 입력합니다.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. **숫자 입력** 구성 요소를 클릭하여 팝업 메뉴가 표시되도록 합니다. 메뉴의 **편집 아이콘**을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. 필드 레이블로 **전화번호**를 입력합니다.
      ![](/help/forms/assets/screenshot2028123829.png)


1. 양식에 유효성 검사 추가:

   1. **전화번호** 구성 요소를 클릭하여 팝업 메뉴가 표시되도록 합니다. 메뉴의 **공구 모양 아이콘**을 클릭하여 필드를 구성합니다.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. **유효성 검사 탭**&#x200B;을 열고 **필수** 필드에 표시한 후 **완료**를 클릭합니다. 성공 메시지가 표시됩니다.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. 최종 사용자 관점에서 양식을 미리 보려면 **미리보기**를 클릭합니다.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. 더미 데이터로 양식 채우기
      ![](/help/forms/assets/screenshot2028125629.png)

   1. 양식 제출
      ![](/help/forms/assets/screenshot2028125729.png)

   1. bin 요청 탭에서 제출된 데이터를 확인합니다.
      ![](/help/forms/assets/screenshot2028125829.png)

이제 남은 연습에서는 사전에 만들어진 등록 양식을 사용합니다.

1. AEM Forms 관리 인터페이스(예: `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`)를 열고 등록 양식을 선택합니다.

   ![](/help/forms/assets/screenshot2028115529.png)

1. **게시**&#x200B;를 클릭합니다.

   ![](/help/forms/assets/screenshot2028115629.png)

   성공 메시지가 표시됩니다.

   ![](/help/forms/assets/screenshot2028115729.png)

   양식의 게시 URL은 `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`과 유사합니다.

1. 게시된 양식을 보려면 위 URL의 프로그램 ID(pXXXXXX) 및 환경 ID(eXXXXXX)를 환경의 ID로 바꿉니다.

## 수업 3

### 목표

프론트엔드 개발 모범 사례를 사용하여 스타일을 업데이트합니다.

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 이전에 만든 적응형 양식의 스타일을 쉽게 업데이트하는 방법을 알아봅니다.

### 연습

테마의 로컬 저장소 설정:

1. 관리자 권한으로 명령 프롬프트 또는 셸 열기.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 테마 프론트엔드 코드를 복제합니다.

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 나열된 순서대로 다음 명령을 사용하여 **aem-forms-theme-canvas** 디렉터리로 이동하고 Visual Studio Code를 엽니다.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. **상위 폴더에 있는 모든 파일의 작성자 신뢰**&#x200B;를 선택하고 **예, 작성자를 신뢰함**&#x200B;을 클릭합니다.

   ![](/help/forms/assets/screenshot2028116229.png)

1. 클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 `env_template` 파일의 이름을 바꿉니다.  파일 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. .env 파일의 변수에 대해 다음 값을 설정하고 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: 양식의 경로를 지정합니다. 예를 들어 양식 경로가 `/content/forms/af/registration`인 경우 이 변수의 값은 `registration`이 됩니다.

   ![](/help/forms/assets/screenshot2028116429.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * `npm notice Run npm nstall -g npm@9.6.0` 명령을 통해 npm을 업데이트하라는 메시지가 표시되면 메시지를 무시합니다.
   > * 통합 문서에서 지시하지 않는 한 다른 npm 명령은 실행하지 않습니다.

1. 이제 다음 명령을 실행하여 양식을 미리 봅니다.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   위 명령이 실행되면 `webpack compiled` 메시지를 기다립니다. 양식이 브라우저 탭에 표시됩니다.

   >[!NOTE]
   >
   >`npm run live` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Visual Studio Code에서 `PROJECT\src\site\_variables.scss` 파일을 엽니다. `$error` 색상은 빨간색입니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저에서 양식을 제출하면 **이름** 필드에 빨간색이 표시됩니다.

   ![](/help/forms/assets/screenshot2028120829.png)

1. **$error** 색상을 **#5736eb**&#x200B;로 설정하고 파일을 저장합니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저를 새로 고치고 양식을 제출합니다. 이에 따라 이름 필드의 오류 색상이 변경됩니다.

   ![](/help/forms/assets/screenshot2028121129.png)

1. 명령 프롬프트에서 **CTRL+C**&#x200B;를 누르고 **Y**&#x200B;를 입력한 다음 **Enter** 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.
1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 수업 4

### 목표

양식을 웹/모바일 및 기타 인터페이스에 Headless 양식으로 렌더링합니다.

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 React 스펙트럼 디자인 프레임워크를 사용하여 이전에 Headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

React 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. 나열된 순서대로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** 디렉터리로 이동하고 Visual Studio Code를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Visual Studio Code 창이 열립니다.

   ![](/help/forms/assets/screenshot2028117429.png)

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음과 같이 합니다.

1. env_template 파일의 이름을 .env 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: 이전 수업에서 만든 적응형 양식의 경로를 지정합니다. 예, `/content/forms/af/registration/`

     ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 명령 창을 열고 현재 위치가 react-starter-kit-aem-headless-forms 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   위 명령은 React 스펙트럼 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링하는 로컬 개발 서버를 시작합니다.

   >[!NOTE]
   >
   > 
   > `npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/forms/assets/screenshot2028118229.png)

이 Headless 형식의 규칙 실행을 확인해 보겠습니다.

1. **5% 할인을 받으려면 확인란 선택** 옵션을 선택합니다. 신용 카드 신청을 위한 후속 옵션이 비활성화됩니다.

   ![](/help/forms/assets/screenshot2028126229.png)

1. 신용 카드 옵션을 활성화하려면 **5% 할인을 받으려면 확인란 선택**&#x200B;을 선택 취소합니다.

   ![](/help/forms/assets/screenshot2028126329.png)

비즈니스 사용자로서 서버의 양식을 변경하고 자동으로 Headless 양식에 반영된 변경 사항을 확인해 보겠습니다.

1. 브라우저에서 AEM Forms 관리 인터페이스를 엽니다.
\
1. **등록** 양식을 선택하고 **편집을 클릭합니다.** 적응형 양식 편집기에서 양식이 열립니다.

   ![](/help/forms/assets/screenshot2028118529.png)

1. **전화번호** 필드를 선택하고 도구 모음에서 **편집 아이콘(연필 아이콘)**&#x200B;을 클릭합니다. 팝업 도구 모음이 보이지 않으면 오른쪽 상단에서 **미리보기** 버튼 왼쪽에 있는 **편집** 버튼을 클릭하여 편집 모드로 전환합니다.

   ![](/help/forms/assets/screenshot2028119629.png)

1. 레이블을 휴대폰 번호로 변경합니다. 양식의 빈 공간을 클릭하면 양식의 변경 사항이 저장됩니다.

   ![](/help/forms/assets/screenshot2028119729.png)

변경 사항을 게시 환경에 전파하기 위해 업데이트된 양식을 게시해 보겠습니다.

1. AEM Forms 관리 인터페이스 탭에서 등록 양식을 선택하고 **게시 취소**&#x200B;를 클릭합니다. **게시 취소** 버튼이 표시되지 않으면 3단계로 건너뛰어 변경 사항을 직접 게시합니다.

   ![](/help/forms/assets/screenshot2028119829.png)

1. **게시 취소**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. 브라우저를 새로 고친 후 등록 양식을 선택하고 **게시**&#x200B;를 클릭합니다.

   ![](/help/forms/assets/screenshot2028120129.png)


1. **게시**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Headless 양식이 표시된 브라우저 탭을 새로 고칩니다. 전화번호 레이블이 휴대폰 번호로 변경됩니다.

   ![](/help/forms/assets/screenshot2028120529.png)

1. **react-starter-kit-aem-headless-forms** 프로젝트를 시작하는 데 사용된 명령 프롬프트 창을 열고 **CTRL+C**&#x200B;를 누른 후 **Y**&#x200B;를 입력하고 Enter 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.

1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.


## 수업 5

### 목표

Google Material UI를 사용하여 양식을 Headless 양식으로 렌더링

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 Google Material UI를 사용하여 이전에 Headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

Material UI 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)


1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다.

   ```Shell
   cd c:\git
   ```

1. 나열된 순서대로 다음 명령을 실행하여 mui라는 폴더를 만들고 다음 명령을 사용하여 mui 폴더로 이동합니다.

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. 나열된 순서대로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** 폴더로 이동하고 Visual Studio Code에서 코드를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음과 같이 합니다.

1. **env_template** 파일의 이름을 **.env** 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기**&#x200B;를 선택합니다.

   ![](/help/forms/assets/screenshot2028126629.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다.

   * **AEM_FORM_PATH**: 이전 수업에서 만든 적응형 양식의 경로를 지정합니다. 예: /content/forms/af/registration/

     ![](/help/forms/assets/screenshot2028126929.png)

1. 명령 창을 열고 현재 위치가 **react-starter-kit-aem-headless-forms** 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   위 명령은 로컬 개발 서버를 시작하고 Google Material UI 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링합니다.

   >[!NOTE]
   >
   >`npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/forms/assets/screenshot2028127229.png)

1. 이 양식 렌디션에서 동일한 비즈니스 로직의 실행을 평가하려면 다음 작업을 수행하십시오.

   **5% 할인을 받으려면 확인란 선택**&#x200B;을 선택합니다. 후속 옵션인 **We Finance 기업 신용 카드 양식을 신청하시겠습니까?**&#x200B;가 비활성화됩니다.

   ![](/help/forms/assets/screenshot2028127329.png)

## 수업 6

### 목표

Material UI 구성 요소 변형을 사용하여 Headless 형태의 대체 디자인 만들기

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 이전에 비즈니스 사용자가 만든 적응형 양식에 대해 Material UI를 사용하여 다양한 구성 요소의 대체 표시를 만드는 방법을 알아봅니다.

### 연습

Headless 프로젝트의 구성 요소 변형을 업데이트합니다. Material UI 텍스트 입력 구성 요소의 변형을 `OutlinedInput`으로 변경하려면 다음과 같이 합니다.

1. Visual Code에서 `src/components/textinput/index.tsx`에 있는 `index.tsx` 파일을 열어 텍스트 입력 구성 요소로 이동합니다.

1. 코드 103행의 시작 부분에 `//`를 추가합니다. 이렇게 하면 줄이 주석으로 변환됩니다.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 구성 요소의 다른 변형을 사용하고 파일을 저장하려면 104행에 다음을 추가합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   &#39;OutlinedInput&#39; 변형에 올바른 대소문자를 사용하는 것이 필수적입니다. 그렇게 하지 않으면 컴파일이 실패합니다. 로컬 개발 환경 컴파일은 명령 프롬프트에서 자동으로 시작됩니다. 다음 메시지가 나타날 때까지 기다립니다

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 브라우저가 자동으로 새로 고쳐지지 않으면 브라우저를 새로 고쳐 텍스트 입력 구성 요소가 다른 변형을 사용하는지 확인합니다.

   ![](/help/forms/assets/screenshot2028127729.png)


   이 변경 사항은 AEM Forms Server의 양식 정의를 변경하지 않고 최종 사용자에게 발생하며, 고려 중인 Headless 채널에만 적용됩니다. 예: 이 랩의 웹 채널.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 자주 묻는 질문 (FAQ)

+++ 적응형 양식 마법사를 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 사용할 수 있습니다.

+++


+++ 핵심 구성 요소를 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 적응형 양식 핵심 구성 요소를 사용할 수 있습니다.

+++

+++ Headless 양식을 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 Headless 양식을 사용할 수 있습니다.

+++

+++ Headless 양식에 별도의 라이선스가 필요합니까?

아니요, Headless 양식은 동일한 라이선스 값 지표(양식 제출 수)를 사용합니다.

+++

+++ AEM 6.5 Forms에서 핵심 구성 요소 및 Headless 양식을 사용할 수 있습니까?

예, 적응형 양식 핵심 구성 요소와 Headless 양식 모두 AEM Forms 6.5 서비스 팩 16 이상에서 사용할 수 있습니다.

+++


## 다음 단계

적응형 양식을 작성하고 Headless 양식을 사용하여 여러 채널에 전달하는 방법을 학습했으므로 이제 새로운 기술을 실무에 접목할 차례입니다. 학습한 내용을 유용하게 활용하여 최종 사용자가 있는 곳에서 대규모로 뛰어난 데이터 캡처 경험을 만들고 제공해 보십시오!

## 리소스

* [적응형 양식 핵심 구성 요소 소개](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [핵심 구성 요소를 사용하여 적응형 양식 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [핵심 구성 요소 기반 AF의 스타일링 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Headless React 스타터 키트 사용](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
