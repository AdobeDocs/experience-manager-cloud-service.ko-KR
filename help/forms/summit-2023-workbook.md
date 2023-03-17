---
title: 핵심 구성 요소 및 헤드리스를 사용하여 매력적인 Forms 구축
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 헤드리스를 사용하여 매력적인 Forms 구축
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: 26a4450c8b722fd4ca074abb3c260983c1ae0c64
workflow-type: tm+mt
source-wordcount: '3411'
ht-degree: 3%

---


# 핵심 구성 요소 및 헤드리스를 사용하여 매력적인 Forms 구축

## 랩 개요

이 실습 실습에서는 다음을 배울 수 있습니다.

AEM Forms을 사용하여 AEM Sites과 일치하는 최신 핵심 구성 요소를 사용하여 적응형 양식을 쉽게 만들고, 적응형 양식을 웹, 모바일 및 채팅으로 헤드리스 양식으로 전달하여 옴니채널 데이터 캡처 경험을 가능하게 하는 방법입니다. 또한 스타일, 사용자 지정 및 프런트 엔드 개발에 대한 모범 사례를 살펴볼 수 있습니다.

## 주요 이점

* **비즈니스 민첩성**: 비즈니스 사용자는 여러 채널용 양식 경험을 쉽게 작성할 수 있습니다.

* **프론트엔드 개발자를 지원하는 기능**: 프런트 엔드 개발자로서, 헤드리스 양식을 사용하여 최종 사용자 경험을 제어할 수 있습니다.

* **개발자 속도**: 개발자로서 사이트 및 Forms 구성 요소를 쉽고 일관되게 사용자 지정할 수 있습니다.

## 사전 요구 사항


+++AEM Forms as a Cloud Service 샌드박스



<table>
        <thead>
            <tr><th>이름</th><th>작성자 인스턴스 URL</th><th>게시 인스턴스 URL</th></tr>           
        </thead>
        <tbody>
            <tr><td>L716001</td><td>https://author-p105303-e986623.adobeaemcloud.com</td><td>https://publish-p105303-e986623.adobeaemcloud.com</td></tr><tr><td>L716002</td><td>https://author-p106405-e993047.adobeaemcloud.com</td><td>https://publish-p106405-e993047.adobeaemcloud.com</td></tr><tr><td>L716003</td><td>https://author-p106406-e993049.adobeaemcloud.com</td><td>https://publish-p106406-e993049.adobeaemcloud.com</td></tr><tr><td>L716004</td><td>https://author-p106398-e993114.adobeaemcloud.com</td><td>https://publish-p106398-e993114.adobeaemcloud.com</td></tr><tr><td>L716005</td><td>https://author-p106407-e993048.adobeaemcloud.com</td><td>https://publish-p106407-e993048.adobeaemcloud.com</td></tr><tr><td>L716006</td><td>https://author-p106408-e993155.adobeaemcloud.com</td><td>https://publish-p106408-e993155.adobeaemcloud.com</td></tr><tr><td>L716007</td><td>https://author-p106343-e993067.adobeaemcloud.com</td><td>https://publish-p106343-e993067.adobeaemcloud.com</td></tr><tr><td>L716008</td><td>https://author-p106399-e993108.adobeaemcloud.com</td><td>https://publish-p106399-e993108.adobeaemcloud.com</td></tr><tr><td>L716009</td><td>https://author-p106344-e993064.adobeaemcloud.com</td><td>https://publish-p106344-e993064.adobeaemcloud.com</td></tr><tr><td>L716010</td><td>https://author-p106409-e993051.adobeaemcloud.com</td><td>https://publish-p106409-e993051.adobeaemcloud.com</td></tr><tr><td>L716011</td><td>https://author-p106345-e993060.adobeaemcloud.com</td><td>https://publish-p106345-e993060.adobeaemcloud.com</td></tr><tr><td>L716012</td><td>https://author-p106346-e993061.adobeaemcloud.com</td><td>https://publish-p106346-e993061.adobeaemcloud.com</td></tr><tr><td>L716013</td><td>https://author-p106410-e993153.adobeaemcloud.com</td><td>https://publish-p106410-e993153.adobeaemcloud.com</td></tr><tr><td>L716014</td><td>https://author-p106502-e993073.adobeaemcloud.com</td><td>https://publish-p106502-e993073.adobeaemcloud.com</td></tr><tr><td>L716015</td><td>https://author-p106401-e993112.adobeaemcloud.com</td><td>https://publish-p106401-e993112.adobeaemcloud.com</td></tr><tr><td>L716016</td><td>https://author-p106452-e993115.adobeaemcloud.com</td><td>https://publish-p106452-e993115.adobeaemcloud.com</td></tr><tr><td>L716017</td><td>https://author-p106453-e993113.adobeaemcloud.com</td><td>https://publish-p106453-e993113.adobeaemcloud.com</td></tr><tr><td>L716018</td><td>https://author-p106411-e993050.adobeaemcloud.com</td><td>https://publish-p106411-e993050.adobeaemcloud.com</td></tr><tr><td>L716019</td><td>https://author-p106454-e993116.adobeaemcloud.com</td><td>https://publish-p106454-e993116.adobeaemcloud.com</td></tr><tr><td>L716020</td><td>https://author-p106347-e993063.adobeaemcloud.com</td><td>https://publish-p106347-e993063.adobeaemcloud.com</td></tr><tr><td>L716021</td><td>https://author-p106455-e993109.adobeaemcloud.com</td><td>https://publish-p106455-e993109.adobeaemcloud.com</td></tr><tr><td>L716022</td><td>https://author-p106456-e993110.adobeaemcloud.com</td><td>https://publish-p106456-e993110.adobeaemcloud.com</td></tr><tr><td>L716023</td><td>https://author-p106466-e993291.adobeaemcloud.com</td><td>https://publish-p106466-e993291.adobeaemcloud.com</td></tr><tr><td>L716024</td><td>https://author-p106413-e993156.adobeaemcloud.com</td><td>https://publish-p106413-e993156.adobeaemcloud.com</td></tr><tr><td>L716025</td><td>https://author-p106348-e993066.adobeaemcloud.com</td><td>https://publish-p106348-e993066.adobeaemcloud.com</td></tr><tr><td>L716026</td><td>https://author-p106414-e993154.adobeaemcloud.com</td><td>https://publish-p106414-e993154.adobeaemcloud.com</td></tr><tr><td>L716027</td><td>https://author-p106349-e993065.adobeaemcloud.com</td><td>https://publish-p106349-e993065.adobeaemcloud.com</td></tr><tr><td>L716028</td><td>https://author-p106415-e993152.adobeaemcloud.com</td><td>https://publish-p106415-e993152.adobeaemcloud.com</td></tr><tr><td>L716029</td><td>https://author-p106350-e993068.adobeaemcloud.com</td><td>https://publish-p106350-e993068.adobeaemcloud.com</td></tr><tr><td>L716030</td><td>https://author-p106351-e993062.adobeaemcloud.com</td><td>https://publish-p106351-e993062.adobeaemcloud.com</td></tr><tr><td>L716031</td><td>https://author-p106417-e993158.adobeaemcloud.com</td><td>https://publish-p106417-e993158.adobeaemcloud.com</td></tr><tr><td>L716032</td><td>https://author-p106418-e993159.adobeaemcloud.com</td><td>https://publish-p106418-e993159.adobeaemcloud.com</td></tr><tr><td>L716033</td><td>https://author-p106503-e993080.adobeaemcloud.com</td><td>https://publish-p106503-e993080.adobeaemcloud.com</td></tr><tr><td>L716034</td><td>https://author-p106457-e993125.adobeaemcloud.com</td><td>https://publish-p106457-e993125.adobeaemcloud.com</td></tr><tr><td>L716035</td><td>https://author-p106504-e993081.adobeaemcloud.com</td><td>https://publish-p106504-e993081.adobeaemcloud.com</td></tr><tr><td>L716036</td><td>https://author-p106458-e993120.adobeaemcloud.com</td><td>https://publish-p106458-e993120.adobeaemcloud.com</td></tr><tr><td>L716037</td><td>https://author-p106419-e993160.adobeaemcloud.com</td><td>https://publish-p106419-e993160.adobeaemcloud.com</td></tr><tr><td>L716038</td><td>https://author-p106420-e993162.adobeaemcloud.com</td><td>https://publish-p106420-e993162.adobeaemcloud.com</td></tr><tr><td>L716039</td><td>https://author-p106517-e993235.adobeaemcloud.com</td><td>https://publish-p106517-e993235.adobeaemcloud.com</td></tr><tr><td>L716040</td><td>https://author-p106506-e993079.adobeaemcloud.com</td><td>https://publish-p106506-e993079.adobeaemcloud.com</td></tr><tr><td>L716041</td><td>https://author-p106507-e993074.adobeaemcloud.com</td><td>https://publish-p106507-e993074.adobeaemcloud.com</td></tr><tr><td>L716042</td><td>https://author-p106508-e993075.adobeaemcloud.com</td><td>https://publish-p106508-e993075.adobeaemcloud.com</td></tr><tr><td>L716043</td><td>https://author-p106421-e993163.adobeaemcloud.com</td><td>https://publish-p106421-e993163.adobeaemcloud.com</td></tr><tr><td>L716044</td><td>https://author-p106459-e993121.adobeaemcloud.com</td><td>https://publish-p106459-e993121.adobeaemcloud.com</td></tr><tr><td>L716045</td><td>https://author-p106467-e993292.adobeaemcloud.com</td><td>https://publish-p106467-e993292.adobeaemcloud.com</td></tr><tr><td>L716046</td><td>https://author-p106518-e993234.adobeaemcloud.com</td><td>https://publish-p106518-e993234.adobeaemcloud.com</td></tr><tr><td>L716047</td><td>https://author-p106511-e993076.adobeaemcloud.com</td><td>https://publish-p106511-e993076.adobeaemcloud.com</td></tr><tr><td>L716048</td><td>https://author-p106512-e993077.adobeaemcloud.com</td><td>https://publish-p106512-e993077.adobeaemcloud.com</td></tr><tr><td>L716049</td><td>https://author-p106460-e993124.adobeaemcloud.com</td><td>https://publish-p106460-e993124.adobeaemcloud.com</td></tr><tr><td>L716050</td><td>https://author-p106519-e993237.adobeaemcloud.com</td><td>https://publish-p106519-e993237.adobeaemcloud.com</td></tr><tr><td>L716051</td><td>https://author-p106513-e993084.adobeaemcloud.com</td><td>https://publish-p106513-e993084.adobeaemcloud.com</td></tr><tr><td>L716052</td><td>https://author-p106461-e993122.adobeaemcloud.com</td><td>https://publish-p106461-e993122.adobeaemcloud.com</td></tr><tr><td>L716053</td><td>https://author-p106514-e993082.adobeaemcloud.com</td><td>https://publish-p106514-e993082.adobeaemcloud.com</td></tr><tr><td>L716054</td><td>https://author-p106462-e993123.adobeaemcloud.com</td><td>https://publish-p106462-e993123.adobeaemcloud.com</td></tr><tr><td>L716055</td><td>https://author-p106463-e993127.adobeaemcloud.com</td><td>https://publish-p106463-e993127.adobeaemcloud.com</td></tr><tr><td>L716056</td><td>https://author-p106515-e993083.adobeaemcloud.com</td><td>https://publish-p106515-e993083.adobeaemcloud.com</td></tr><tr><td>L716057</td><td>https://author-p106464-e993126.adobeaemcloud.com</td><td>https://publish-p106464-e993126.adobeaemcloud.com</td></tr><tr><td>L716058</td><td>https://author-p106520-e993236.adobeaemcloud.com</td><td>https://publish-p106520-e993236.adobeaemcloud.com</td></tr><tr><td>L716059</td><td>https://author-p106423-e993161.adobeaemcloud.com</td><td>https://publish-p106423-e993161.adobeaemcloud.com</td></tr><tr><td>L716060</td><td>https://author-p106516-e993078.adobeaemcloud.com</td><td>https://publish-p106516-e993078.adobeaemcloud.com</td></tr><tr><td>L716061</td><td>https://author-p106521-e993240.adobeaemcloud.com</td><td>https://publish-p106521-e993240.adobeaemcloud.com</td></tr><tr><td>L716062</td><td>https://author-p106424-e993308.adobeaemcloud.com</td><td>https://publish-p106424-e993308.adobeaemcloud.com</td></tr><tr><td>L716063</td><td>https://author-p106468-e993295.adobeaemcloud.com</td><td>https://publish-p106468-e993295.adobeaemcloud.com</td></tr><tr><td>L716064</td><td>https://author-p106425-e993309.adobeaemcloud.com</td><td>https://publish-p106425-e993309.adobeaemcloud.com</td></tr><tr><td>L716065</td><td>https://author-p106426-e993314.adobeaemcloud.com</td><td>https://publish-p106426-e993314.adobeaemcloud.com</td></tr><tr><td>L716066</td><td>https://author-p106469-e993293.adobeaemcloud.com</td><td>https://publish-p106469-e993293.adobeaemcloud.com</td></tr><tr><td>L716067</td><td>https://author-p106522-e993238.adobeaemcloud.com</td><td>https://publish-p106522-e993238.adobeaemcloud.com</td></tr><tr><td>L716068</td><td>https://author-p106470-e993299.adobeaemcloud.com</td><td>https://publish-p106470-e993299.adobeaemcloud.com</td></tr><tr><td>L716069</td><td>https://author-p106427-e993311.adobeaemcloud.com</td><td>https://publish-p106427-e993311.adobeaemcloud.com</td></tr><tr><td>L716070</td><td>https://author-p106428-e993310.adobeaemcloud.com</td><td>https://publish-p106428-e993310.adobeaemcloud.com</td></tr><tr><td>L716071</td><td>https://author-p106471-e993298.adobeaemcloud.com</td><td>https://publish-p106471-e993298.adobeaemcloud.com</td></tr><tr><td>L716072</td><td>https://author-p106429-e993315.adobeaemcloud.com</td><td>https://publish-p106429-e993315.adobeaemcloud.com</td></tr><tr><td>L716073</td><td>https://author-p106523-e993239.adobeaemcloud.com</td><td>https://publish-p106523-e993239.adobeaemcloud.com</td></tr><tr><td>L716074</td><td>https://author-p106472-e993300.adobeaemcloud.com</td><td>https://publish-p106472-e993300.adobeaemcloud.com</td></tr><tr><td>L716075</td><td>https://author-p106430-e993312.adobeaemcloud.com</td><td>https://publish-p106430-e993312.adobeaemcloud.com</td></tr><tr><td>L716076</td><td>https://author-p106524-e993241.adobeaemcloud.com</td><td>https://publish-p106524-e993241.adobeaemcloud.com</td></tr><tr><td>L716077</td><td>https://author-p106431-e993313.adobeaemcloud.com</td><td>https://publish-p106431-e993313.adobeaemcloud.com</td></tr><tr><td>L716078</td><td>https://author-p106473-e993294.adobeaemcloud.com</td><td>https://publish-p106473-e993294.adobeaemcloud.com</td></tr><tr><td>L716079</td><td>https://author-p106474-e993297.adobeaemcloud.com</td><td>https://publish-p106474-e993297.adobeaemcloud.com</td></tr><tr><td>L716080</td><td>https://author-p106475-e993296.adobeaemcloud.com</td><td>https://publish-p106475-e993296.adobeaemcloud.com</td></tr><tr><td>L716081</td><td>https://author-p106476-e993353.adobeaemcloud.com</td><td>https://publish-p106476-e993353.adobeaemcloud.com</td></tr><tr><td>L716082</td><td>https://author-p106525-e993247.adobeaemcloud.com</td><td>https://publish-p106525-e993247.adobeaemcloud.com</td></tr><tr><td>L716083</td><td>https://author-p106526-e993244.adobeaemcloud.com</td><td>https://publish-p106526-e993244.adobeaemcloud.com</td></tr><tr><td>L716084</td><td>https://author-p106527-e993243.adobeaemcloud.com</td><td>https://publish-p106527-e993243.adobeaemcloud.com</td></tr><tr><td>L716085</td><td>https://author-p106477-e993356.adobeaemcloud.com</td><td>https://publish-p106477-e993356.adobeaemcloud.com</td></tr><tr><td>L716086</td><td>https://author-p106478-e993355.adobeaemcloud.com</td><td>https://publish-p106478-e993355.adobeaemcloud.com</td></tr><tr><td>L716087</td><td>https://author-p106528-e993245.adobeaemcloud.com</td><td>https://publish-p106528-e993245.adobeaemcloud.com</td></tr><tr><td>L716088</td><td>https://author-p106432-e993316.adobeaemcloud.com</td><td>https://publish-p106432-e993316.adobeaemcloud.com</td></tr><tr><td>L716089</td><td>https://author-p106529-e993242.adobeaemcloud.com</td><td>https://publish-p106529-e993242.adobeaemcloud.com</td></tr><tr><td>L716090</td><td>https://author-p106436-e993320.adobeaemcloud.com</td><td>https://publish-p106436-e993320.adobeaemcloud.com</td></tr><tr><td>L716091</td><td>https://author-p106480-e993301.adobeaemcloud.com</td><td>https://publish-p106480-e993301.adobeaemcloud.com</td></tr><tr><td>L716092</td><td>https://author-p106530-e993246.adobeaemcloud.com</td><td>https://publish-p106530-e993246.adobeaemcloud.com</td></tr><tr><td>L716093</td><td>https://author-p106481-e993352.adobeaemcloud.com</td><td>https://publish-p106481-e993352.adobeaemcloud.com</td></tr><tr><td>L716094</td><td>https://author-p106482-e993354.adobeaemcloud.com</td><td>https://publish-p106482-e993354.adobeaemcloud.com</td></tr><tr><td>L716095</td><td>https://author-p106531-e993248.adobeaemcloud.com</td><td>https://publish-p106531-e993248.adobeaemcloud.com</td></tr><tr><td>L716096</td><td>https://author-p106483-e993357.adobeaemcloud.com</td><td>https://publish-p106483-e993357.adobeaemcloud.com</td></tr><tr><td>L716097</td><td>https://author-p106433-e993318.adobeaemcloud.com</td><td>https://publish-p106433-e993318.adobeaemcloud.com</td></tr><tr><td>L716098</td><td>https://author-p106532-e993249.adobeaemcloud.com</td><td>https://publish-p106532-e993249.adobeaemcloud.com</td></tr><tr><td>L716099</td><td>https://author-p106434-e993317.adobeaemcloud.com</td><td>https://publish-p106434-e993317.adobeaemcloud.com</td></tr><tr><td>L716100</td><td>https://author-p106435-e993319.adobeaemcloud.com</td><td>https://publish-p106435-e993319.adobeaemcloud.com</td></tr>
        </tbody>
</table>

+++

## 1과

### 목표

AEM Forms as a Cloud Service 환경을 숙지하십시오.

### 단원 컨텍스트

이 단원에서는 사용자 인터페이스를 탐색하여 AEM Forms as a Cloud Service 환경에 대해 숙지합니다.

### 연습

1. 브라우저를 열고 Cloud Service 작성 환경의 URL을 입력합니다. 예:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Cloud Service 작성 환경에 로그인합니다. 작성자 환경의 로그인 자격 증명은 랩 중에 사용자와 공유됩니다.

1. 로그인한 후 AEM Forms UI로 이동합니다. 클릭 **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. 클릭 **Forms 및 문서**. 기본 설정 또는 정보와 관련된 팝업을 닫습니다.

   ![](/help/forms/assets/screenshot2028113929.png)

   사용 가능한 모든 양식이 표시됩니다.

   ![](/help/forms/assets/screenshot2028114029.png)

## 2과

### 목표

최신 핵심 구성 요소를 사용하여 적응형 양식을 작성하고, 양식을 구성하고, 제출합니다.

### 단원 컨텍스트

이 단원에서는 비즈니스 사용자로서, 데이터 캡처를 위한 표준화된 OOTB 핵심 구성 요소를 사용한 적응형 양식 작성을 사용하여 웹, 모바일 및 채팅과 같은 여러 채널에 대한 적응형 양식을 작성합니다.

### 연습

1. 양식에 대한 제출 끝점을 만듭니다.

   1. 열기 <https://requestbin.com/> 새 브라우저 탭에서 을 클릭합니다.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. 클릭 **공개 저장소 만들기** 엔드포인트 URL을 복사합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. 마법사 인터페이스를 사용하여 적응형 양식을 작성합니다.

   1. 1단원에서 사용되는 브라우저 탭에서 AEM Forms as a Cloud Service 웹 인터페이스로 이동하고 Forms 및 문서로 이동합니다.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. 클릭 **만들기** 적응형 양식을 선택합니다.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. 을(를) 선택합니다 **코어 구성 요소가 있는 빈** 템플릿 선택 화면에서 아래에 표시된 대로 템플릿을 선택합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. 을(를) 클릭합니다. **스타일** 탭을 선택하고 을(를) 선택합니다 **wknd 테마** 아래 표시된 테마
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 을(를) 클릭합니다. **제출** 탭을 선택하고 을(를) 선택합니다 **REST 종단점에 제출** 카드 및
      **POST 요청에 대한 URL** 아래와 같이 필드를 입력합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. **만들기**&#x200B;를 클릭합니다. 양식의 이름과 제목을 지정합니다. 예, **동시 실행**. **만들기**를 클릭합니다.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. 적응형 양식 편집기가 열립니다. 기본 설정 또는 정보에 대한 팝업 또는 대화 상자를 닫습니다. 왼쪽 레일의 구성 요소 브라우저를 클릭하고 을(를) 추가합니다. **바닥글** 구성 요소를 사용하여 빈 양식의 맨 아래에 항목을 넣을 수 있습니다.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. 헤더는 적응형 양식 템플릿의 일부입니다. 모든 적응형 양식에서 일관된 머리글/바닥글을 쉽게 제공할 수 있습니다. 또는 다음 단계에서 바닥글 구성 요소에 대해 볼 수 있듯이 양식에서 편집 가능하게 할 수도 있습니다.

   1. 추가 **제목** 구성 요소를 양식 중간에 추가합니다.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. 추가 **텍스트 입력** 구성 요소를 생성하지 않습니다.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. 추가 **숫자 입력** 구성 요소.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. 추가 **전송 단추** 구성 요소를 생성하지 않습니다.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. 을(를) 클릭합니다. **제목** 구성 요소를 **팝업 메뉴** 이 표시됩니다. 을(를) 클릭합니다. **편집 아이콘** 메뉴에서 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. Enter 키 `Contact Us` 제목 텍스트로 추가할 수 있습니다.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. 을(를) 클릭합니다. **텍스트 입력** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 을(를) 클릭합니다. **편집 아이콘** 메뉴에서 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. Enter 키 **전체 이름** 필드 레이블로
      ![](/help/forms/assets/screenshot2028123029.png)

   1. 을(를) 클릭합니다. **숫자 입력** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 을(를) 클릭합니다. **편집 아이콘** 메뉴에서 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. 을(를) 입력합니다. **전화 번호** 를 필드 레이블로 사용합니다.
      ![](/help/forms/assets/screenshot2028123829.png)


1. 양식에 유효성 검사 추가:

   1. 을(를) 클릭합니다. **전화 번호** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 을(를) 클릭합니다. **렌치 아이콘** 메뉴에서 필드를 구성합니다.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. 를 엽니다. **검증 탭**, 필드를 표시합니다 **필수 여부**&#x200B;를 클릭하고 **완료**. 성공 메시지가 표시됩니다.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. 클릭 **미리 보기** 최종 사용자 관점에서 양식을 미리 보려면
      ![](/help/forms/assets/screenshot2028125529.png)

   1. 더미 데이터로 양식 채우기
      ![](/help/forms/assets/screenshot2028125629.png)

   1. 양식 제출
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Request bin 탭에서 제출된 데이터를 확인합니다.
      ![](/help/forms/assets/screenshot2028125829.png)

이제 나머지 연습을 위해 미리 만든 등록 양식을 사용하십시오.

1. 예를 들어 AEM Forms 관리 인터페이스를 엽니다 `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`를 클릭하고 등록 양식을 선택합니다.

   ![](/help/forms/assets/screenshot2028115529.png)

1. **게시**&#x200B;를 클릭합니다. 

   ![](/help/forms/assets/screenshot2028115629.png)

   성공 메시지가 표시됩니다.

   ![](/help/forms/assets/screenshot2028115729.png)

   양식의 게시 URL은 다음과 비슷합니다 `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. 게시된 양식을 보려면 위의 URL에서 프로그램 ID(pXXXXXX) 및 환경 ID(eXXXXXX)를 사용자 환경의 ID로 바꿉니다.

## 3과

### 목표

프런트 엔드 개발 모범 사례를 사용하여 스타일을 업데이트합니다.

### 단원 컨텍스트

이 단원에서는 프런트 엔드 개발자로서 이전에 만든 적응형 양식의 스타일을 쉽게 업데이트하는 방법에 대해 알아봅니다.

### 연습

테마의 로컬 저장소 설정:

1. 관리자 권한이 있는 명령 프롬프트 또는 셸을 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 테마 프런트 엔드 코드를 복제합니다.

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 다음 명령을 나열된 순서로 사용하여 **aem-forms-theme-canvas** Visual Studio 코드를 열고 디렉터리를 엽니다.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. 선택 **상위 폴더에 있는 모든 파일의 작성자를 신뢰합니다** 을(를) 클릭합니다. **네, 저자들이**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. 클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 이름을 `env_template` 파일.  파일의 이름을 변경하려면 **env_template** 파일을 선택하고 **이름 변경** 선택 사항입니다.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. .env 파일의 변수에 대해 다음 값을 설정하고 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: 양식의 경로를 지정합니다. 예를 들어 양식 경로가 `/content/forms/af/registration`를 채울 경우 이 변수의 값은 `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 를 통해 npm을 업데이트하라는 메시지가 표시되는 경우 `npm notice Run npm nstall -g npm@9.6.0`명령을 실행하면 메시지를 무시합니다.
   > * 통합 문서에 지시되지 않는 한 다른 npm 명령을 실행하지 마십시오.


1. 이제 다음 명령을 실행하여 양식을 미리 봅니다.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   위의 명령이 실행되면 `webpack compiled` 메시지를 표시합니다. 양식이 브라우저 탭에 표시됩니다.

   >[!NOTE]
   >
   >를 실행한 후 브라우저에서 빈 화면이 발생하는 경우 `npm run live` 3-4분 이상 명령, 변경 `localhost` 127.0.0.1로 브라우저 URL에서 을 누르고 히트 **Enter 키**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Visual Studio 코드에서 `PROJECT\src\site\_variables.scss` 파일. 다음 사항에 주의하십시오. `$error` 색상은 빨간색 색조입니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저에서 양식을 제출하여 의 빨간색 색상을 확인합니다. **이름** 필드.

   ![](/help/forms/assets/screenshot2028120829.png)

1. 설정 **$error** 색상 대상 **#5736eb** 파일을 저장합니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저를 새로 고치고 양식을 제출합니다. 이름 필드의 알림 오류 색상이 그에 따라 변경되었습니다.

   ![](/help/forms/assets/screenshot2028121129.png)

1. 명령 프롬프트에서 **CTRL+C**, 입력 **Y**, 및 누르기 **Enter 키** 키를 사용하여 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 중지하는 것이 중요합니다.
1. Visual Studio 코드 및 명령 프롬프트 창을 닫습니다.

## 4과

### 목표

양식을 헤드리스 양식으로 웹/모바일 및 기타 인터페이스에 렌더링합니다.

### 단원 컨텍스트

이 단원에서는 프론트엔드 개발자로서 React Spectrum 디자인 프레임워크를 사용하여 헤드리스 양식으로 이전에 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

React 시작 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용하여 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 적응형 양식 React 시작 프로젝트를 복제합니다.

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. 다음 명령을 나열된 순서로 사용하여 **react-starter-kit-aem-headless-forms** Visual Studio 코드를 열고 디렉터리를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Visual Studio 코드 창이 열립니다.

   ![](/help/forms/assets/screenshot2028117429.png)

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음을 수행하십시오.

1. env_template 파일의 이름을 .env 파일로 변경합니다. 이름을 변경하려면 마우스 오른쪽 단추를 클릭하여 **env_template** 파일을 선택하고 **이름 변경** 선택 사항입니다.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예, `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 명령 창을 열고 react-starter-kit-aem-headless-forms 디렉토리에 있는지 확인하고 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   위의 명령은 React-spectrum 프런트 엔드 라이브러리를 사용하여 헤드리스 방식으로 AEM에서 가져온 양식 정의를 렌더링하는 로컬 개발 서버를 시작합니다.

   >[!NOTE]
   >
   > 
   > 를 실행한 후 브라우저에서 빈 화면이 발생하는 경우 `npm start` 3-4분 이상 명령, 변경 `localhost` 127.0.0.1로 브라우저 URL에서 을 누르고 히트 **Enter 키**.

   ![](/help/forms/assets/screenshot2028118229.png)

이 헤드리스 양식에서 규칙 실행을 확인하겠습니다.

1. 을(를) 선택합니다 **5% 할인을 받으려면 상자를 선택합니다** 선택 사항입니다. 신용 카드 적용 후 옵션이 비활성화됩니다.

   ![](/help/forms/assets/screenshot2028126229.png)

1. 선택을 취소합니다 **5% 할인을 받으려면 상자를 선택합니다** 신용 카드 옵션을 활성화하려면

   ![](/help/forms/assets/screenshot2028126329.png)

비즈니스 사용자로 서버의 양식을 변경하고 헤드리스 양식에 반영된 변경 사항을 자동으로 확인하겠습니다.

1. 브라우저에서 AEM Forms 관리 인터페이스를 엽니다. 예, [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. 을(를) 선택합니다 **등록** 을 클릭하고 **편집.** 적응형 양식 편집기에서 양식이 열립니다.

   ![](/help/forms/assets/screenshot2028118529.png)

1. 을(를) 선택합니다 **전화 번호** 필드를 클릭하고 **편집 아이콘(연필 아이콘)** 클릭합니다. 팝업 도구 모음을 볼 수 없는 경우 을 클릭하여 편집 모드로 전환합니다. **편집** 오른쪽 상단의 단추, 왼쪽에서 **미리 보기** 버튼을 클릭합니다.

   ![](/help/forms/assets/screenshot2028119629.png)

1. 레이블을 모바일 번호로 변경합니다. 양식의 빈 공간을 클릭하면 양식에 적용된 변경 내용이 저장됩니다.

   ![](/help/forms/assets/screenshot2028119729.png)

업데이트된 양식을 게시하여 변경 사항을 게시 환경에 전파하겠습니다.

1. AEM Forms 관리 인터페이스 탭에서 등록 양식을 선택하고 **게시 취소**. 이 표시되지 않으면 **게시 취소** 버튼을 클릭하고 3단계로 건너뛰고 변경 사항을 직접 게시합니다.

   ![](/help/forms/assets/screenshot2028119829.png)

1. 클릭 **게시 취소**. 클릭 **닫기** 를 클릭합니다.

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. 브라우저를 새로 고친 후 등록 양식을 선택하고 을(를) 클릭합니다 **게시**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. **게시**&#x200B;를 클릭합니다. 클릭 **닫기** 를 클릭합니다.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. 헤드리스 양식이 표시된 브라우저 탭을 새로 고칩니다. 알림. 전화 번호 레이블이 모바일 번호로 변경되었습니다.

   ![](/help/forms/assets/screenshot2028120529.png)

1. 를 시작하는 데 사용되는 명령 프롬프트 창을 엽니다 **react-starter-kit-aem-headless-forms** 프로젝트, 누르기 **CTRL+C**&#x200B;를 입력한 다음 를 입력합니다. **Y** 그리고 Enter 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 중지하는 것이 중요합니다.

1. Visual Studio 코드 및 명령 프롬프트 창을 닫습니다.


## 5과

### 목표

Google 재료 UI를 사용하여 양식을 헤드리스 양식으로 렌더링합니다

### 단원 컨텍스트

이 단원에서는 프런트 엔드 개발자로서 Google 자료 UI를 사용하여 이전에 헤드리스 양식으로 작성된 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

재료 UI 시작 프로젝트를 사용하여 로컬 저장소를 설정합니다.

1. 관리자 권한을 사용하여 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)


1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더:

   ```Shell
   cd c:\git
   ```

1. 나열된 명령을 실행하여 mui라는 폴더를 만들고 다음 명령을 사용하여 mui 폴더로 이동합니다.

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 다음 명령을 사용하여 적응형 양식 React 시작 프로젝트를 복제합니다.

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. 다음 명령을 나열된 순서로 사용하여 **react-starter-kit-aem-headless-forms** 폴더를 열고 Visual Studio 코드에서 코드를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음을 수행하십시오.

1. 이름 바꾸기 **env_template** 파일 위치 **.env** 파일. 이름을 변경하려면 마우스 오른쪽 단추를 클릭하여 **env_template** 파일을 선택하고 **이름 변경**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다. 를 사용하십시오 **CTRL + S** 조합을 전환하여 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다. 예, [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. 명령 창을 열고 **react-starter-kit-aem-headless-forms** 디렉토리 및 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   명령은 로컬 개발 서버를 시작하고 Google Material UI 프런트 엔드 라이브러리를 사용하여 헤드리스 방식으로 AEM에서 가져온 양식 정의를 렌더링합니다.

   >[!NOTE]
   >
   >를 실행한 후 브라우저에서 빈 화면이 발생하는 경우 `npm start` 3-4분 이상 명령, 변경 `localhost` 127.0.0.1로 브라우저 URL에서 을 누르고 히트 **Enter 키**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. 이 양식 변환에서 동일한 비즈니스 로직의 실행을 평가하려면

   선택 **5% 할인을 받으려면 상자를 선택합니다**. 후속 옵션 **We.Finance 법인 카드 양식에 신청하시겠습니까?** 이 비활성화되어 있습니다.

   ![](/help/forms/assets/screenshot2028127329.png)

## 6과

### 목표

재료 UI 구성 요소 변형을 사용하여 헤드리스 양식의 대체 모양과 느낌을 만듭니다

### 단원 컨텍스트

이 단원에서는 프런트 엔드 개발자로서 비즈니스 사용자가 이전에 만든 적응형 양식에 대해 재료 UI를 사용하여 서로 다른 구성 요소를 대체 표현하여 만드는 방법을 알아봅니다.

### 연습

헤드리스 프로젝트에서 구성 요소의 변형을 업데이트합니다. 재료 UI 텍스트 입력 컴포넌트의 변형을 로 변경하려면 `OutlinedInput`:

1. 시각적 코드에서 `index.tsx` 파일 위치 `src/components/textinput/index.tsx`.

1. 추가 `//` 코드 줄 103의 시작 부분. 선을 주석으로 변환합니다.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 104행에 다음 내용을 추가하여 다른 구성 요소 변형을 사용하고 파일을 저장합니다. 를 사용하십시오 **CTRL + S** 조합을 전환하여 파일을 저장합니다.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   &#39;OutgulimedInput&#39; 변형 컴파일에 올바른 대문자를 사용해야 합니다. 그렇지 않으면 컴파일할 수 없습니다. 로컬 개발 환경 컴파일이 명령 프롬프트에서 자동으로 시작됩니다. 다음 메시지가 표시될 때까지 기다립니다.

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 브라우저를 자동으로 새로 고치지 않으면 새로 고쳐 텍스트 입력 구성 요소에서 다른 변형을 사용하는 것을 확인합니다.

   ![](/help/forms/assets/screenshot2028127729.png)


   이러한 변경은 AEM Forms Server에서 양식 정의를 변경하지 않고 최종 사용자에게 적용되며 고려 중인 헤드리스 채널에 대해 적용됩니다. 예를 들어 이 실습의 웹 채널입니다.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Visual Studio 코드 및 명령 프롬프트 Windows를 닫습니다.

## FAQ

+++ 적응형 양식 마법사를 공개적으로 사용할 수 있습니까?

예, AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++


+++ 핵심 구성 요소를 공개적으로 사용할 수 있습니까?

예. 적응형 Forms 핵심 구성 요소는 AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++

+++ 헤드리스 양식을 공개적으로 사용할 수 있습니까?

예. 헤드리스 양식은 AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++

+++ 헤드리스 양식에는 별도의 라이센스가 필요합니까?

아니요. 헤드리스 양식에서는 동일한 라이선스 값 지표, 양식 제출 수를 사용합니다.

+++

+++ AEM 6.5 Forms에서 핵심 구성 요소 및 헤드리스 양식을 사용할 수 있습니까?

예. 적응형 양식 핵심 구성 요소와 헤드리스 양식은 AEM Forms 6.5 서비스 팩 16 이상에서 사용할 수 있습니다.

+++


## 다음 단계

이제 헤드리스 양식을 사용하여 적응형 양식을 작성하고 여러 채널에 전달하는 방법을 배웠으므로 새로운 기술을 구현해야 합니다. 엔드 유저가 있는 위치에 규모에 맞게 뛰어난 데이터 캡처 경험을 제작하고 전달하여 재미를 보십시오!

## 리소스

* [적응형 양식 핵심 구성 요소 소개](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [핵심 구성 요소를 사용하여 적응형 양식 만들기](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [핵심 구성 요소 기반 AF의 스타일 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [헤드리스 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [헤드리스 React 시작 키트 사용](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


