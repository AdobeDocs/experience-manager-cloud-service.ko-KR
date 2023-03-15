---
title: 핵심 구성 요소 및 헤드리스를 사용하여 매력적인 Forms 구축
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 헤드리스를 사용하여 매력적인 Forms 구축
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: aa278ca4b2a617593512cab45100d8d4e15fd6eb
workflow-type: tm+mt
source-wordcount: '7032'
ht-degree: 10%

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

* AEM Forms as a Cloud Service 샌드박스

   <table>
        <thead>
            <tr><th>이름</th><th>프로그램 id</th><th>환경 id</th><th>username</th><th>커밋 시 파이프라인 트리거</th><th>저장소 url</th><th>프런트엔드 - 분기 및 보고</th><th>프런트 엔드 리포지토리 이름</th><th>프론트엔드 파이프라인</th><th>링크</th><th>프로그램 url</th><th>환경 목록 url</th><th>프런트 엔드 리포지토리 url</th><th>url 전환</th></tr>           
        </thead>
        <tbody>
            <tr><td>L716001</td><td>105303</td><td>986623</td><td>L716+001@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716001-p105303-uk94266/</td><td>예</td><td>wknd</td><td>예</td><td>https://author-p105303-e986623.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/105303</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/105303</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme</td><td>https://author-p105303-e986623.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716002</td><td>106405</td><td>993047</td><td>L716+002@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716002-p106405-uk30744/</td><td>예</td><td>wknd2</td><td>예</td><td>https://author-p106405-e993047.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106405</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106405</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme2/</td><td>https://author-p106405-e993047.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716003</td><td>106406</td><td>993049</td><td>L716+003@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716003-p106406-uk82969/</td><td>예</td><td>wknd3</td><td>예</td><td>https://author-p106406-e993049.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106406</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106406</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme3/</td><td>https://author-p106406-e993049.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716004</td><td>106398</td><td>993114</td><td>L716+004@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716004-p106398-uk62851/</td><td>예</td><td>wknd4</td><td>예</td><td>https://author-p106398-e993114.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106398</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106398</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme4/</td><td>https://author-p106398-e993114.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716005</td><td>106407</td><td>993048</td><td>L716+005@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716005-p106407-uk76414/</td><td>예</td><td>wknd5</td><td>예</td><td>https://author-p106407-e993048.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106407</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106407</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme5/</td><td>https://author-p106407-e993048.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716006</td><td>106408</td><td>993155</td><td>L716+006@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716006-p106408-uk98879/</td><td>예</td><td>wknd6</td><td>예</td><td>https://author-p106408-e993155.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106408</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106408</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme6/</td><td>https://author-p106408-e993155.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716007</td><td>106343</td><td>993067</td><td>L716+007@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716007-p106343-uk17215/</td><td>예</td><td>wknd7</td><td>예</td><td>https://author-p106343-e993067.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106343</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106343</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme7</td><td>https://author-p106343-e993067.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716008</td><td>106399</td><td>993108</td><td>L716+008@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716008-p106399-uk50450/</td><td>예</td><td>wknd8</td><td>예</td><td>https://author-p106399-e993108.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106399</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106399</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme8</td><td>https://author-p106399-e993108.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716009</td><td>106344</td><td>993064</td><td>L716+009@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716009-p106344-uk63538/</td><td>예</td><td>wknd9</td><td>예</td><td>https://author-p106344-e993064.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106344</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106344</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme9/</td><td>https://author-p106344-e993064.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716010</td><td>106409</td><td>993051</td><td>L716+010@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716010-p106409-uk19656/</td><td>예</td><td>wknd10</td><td>예</td><td>https://author-p106409-e993051.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106409</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106409</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd10</td><td>https://author-p106409-e993051.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716011</td><td>106345</td><td>993060</td><td>L716+011@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716011-p106345-uk54192/</td><td>예</td><td>wknd11</td><td>예</td><td>https://author-p106345-e993060.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106345</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106345</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd11</td><td>https://author-p106345-e993060.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716012</td><td>106346</td><td>993061</td><td>L716+012@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716012-p106346-uk49638/</td><td>예</td><td>wknd12</td><td>예</td><td>https://author-p106346-e993061.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106346</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106346</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd12</td><td>https://author-p106346-e993061.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716013</td><td>106410</td><td>993153</td><td>L716+013@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716013-p106410-uk94707/</td><td>예</td><td>wknd13</td><td>예</td><td>https://author-p106410-e993153.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106410</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106410</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd13</td><td>https://author-p106410-e993153.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716014</td><td>106502</td><td>993073</td><td>L716+014@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716014-p106502-uk23328/</td><td>예</td><td>wknd14</td><td>예</td><td>https://author-p106502-e993073.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106502</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106502</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd14</td><td>https://author-p106502-e993073.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716015</td><td>106401</td><td>993112</td><td>L716+015@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716015-p106401-uk94501/</td><td>예</td><td>wknd15</td><td>예</td><td>https://author-p106401-e993112.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106401</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106401</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd15</td><td>https://author-p106401-e993112.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716016</td><td>106452</td><td>993115</td><td>L716+016@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716016-p106452-uk35087/</td><td>예</td><td>wknd16</td><td>예</td><td>https://author-p106452-e993115.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106452</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106452</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd16</td><td>https://author-p106452-e993115.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716017</td><td>106453</td><td>993113</td><td>L716+017@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716017-p106453-uk55732/</td><td>예</td><td>wknd17</td><td>예</td><td>https://author-p106453-e993113.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106453</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106453</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd17</td><td>https://author-p106453-e993113.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716018</td><td>106411</td><td>993050</td><td>L716+018@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716018-p106411-uk77613/</td><td>예</td><td>wknd18</td><td>예</td><td>https://author-p106411-e993050.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106411</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106411</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd18</td><td>https://author-p106411-e993050.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716019</td><td>106454</td><td>993116</td><td>L716+019@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716019-p106454-uk19216/</td><td>예</td><td>wknd19</td><td>예</td><td>https://author-p106454-e993116.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106454</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106454</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd19</td><td>https://author-p106454-e993116.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716020</td><td>106347</td><td>993063</td><td>L716+020@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716020-p106347-uk53952/</td><td>예</td><td>wknd20</td><td>예</td><td>https://author-p106347-e993063.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106347</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106347</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd20</td><td>https://author-p106347-e993063.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716021</td><td>106455</td><td>993109</td><td>L716+021@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716021-p106455-uk24058/</td><td>예</td><td>wknd21</td><td>예</td><td>https://author-p106455-e993109.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106455</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106455</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd21</td><td>https://author-p106455-e993109.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716022</td><td>106456</td><td>993110</td><td>L716+022@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716022-p106456-uk26793/</td><td>예</td><td>wknd22</td><td>예</td><td>https://author-p106456-e993110.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106456</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106456</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd22</td><td>https://author-p106456-e993110.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716023</td><td>106466</td><td>993291</td><td>L716+023@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716023-p106466-uk93719/</td><td>예</td><td>wknd23</td><td>예</td><td>https://author-p106466-e993291.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106466</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106466</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd23</td><td>https://author-p106466-e993291.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716024</td><td>106413</td><td>993156</td><td>L716+024@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716024-p106413-uk10856/</td><td>예</td><td>wknd24</td><td>예</td><td>https://author-p106413-e993156.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106413</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106413</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd24</td><td>https://author-p106413-e993156.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716025</td><td>106348</td><td>993066</td><td>L716+025@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716025-p106348-uk76381/</td><td>예</td><td>wknd25</td><td>예</td><td>https://author-p106348-e993066.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106348</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106348</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd25</td><td>https://author-p106348-e993066.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716026</td><td>106414</td><td>993154</td><td>L716+026@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716026-p106414-uk93983/</td><td>예</td><td>wknd26</td><td>예</td><td>https://author-p106414-e993154.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106414</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106414</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd26</td><td>https://author-p106414-e993154.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716027</td><td>106349</td><td>993065</td><td>L716+027@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716027-p106349-uk75744/</td><td>예</td><td>wknd27</td><td>예</td><td>https://author-p106349-e993065.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106349</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106349</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd27</td><td>https://author-p106349-e993065.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716028</td><td>106415</td><td>993152</td><td>L716+028@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716028-p106415-uk24248/</td><td>예</td><td>wknd28</td><td>예</td><td>https://author-p106415-e993152.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106415</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106415</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd28</td><td>https://author-p106415-e993152.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716029</td><td>106350</td><td>993068</td><td>L716+029@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716029-p106350-uk06304/</td><td>예</td><td>wknd29</td><td>예</td><td>https://author-p106350-e993068.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106350</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106350</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd29</td><td>https://author-p106350-e993068.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716030</td><td>106351</td><td>993062</td><td>L716+030@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716030-p106351-uk95707/</td><td>예</td><td>wknd30</td><td>예</td><td>https://author-p106351-e993062.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106351</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106351</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd30</td><td>https://author-p106351-e993062.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716031</td><td>106417</td><td>993158</td><td>L716+031@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716031-p106417-uk50022/</td><td>예</td><td>wknd31</td><td>예</td><td>https://author-p106417-e993158.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106417</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106417</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd31</td><td>https://author-p106417-e993158.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716032</td><td>106418</td><td>993159</td><td>L716+032@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716032-p106418-uk75663/</td><td>예</td><td>wknd32</td><td>예</td><td>https://author-p106418-e993159.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106418</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106418</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd32</td><td>https://author-p106418-e993159.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716033</td><td>106503</td><td>993080</td><td>L716+033@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716033-p106503-uk29541/</td><td>예</td><td>wknd33</td><td>예</td><td>https://author-p106503-e993080.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106503</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106503</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd33</td><td>https://author-p106503-e993080.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716034</td><td>106457</td><td>993125</td><td>L716+034@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716034-p106457-uk91438/</td><td>예</td><td>wknd34</td><td>예</td><td>https://author-p106457-e993125.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106457</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106457</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd34</td><td>https://author-p106457-e993125.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716035</td><td>106504</td><td>993081</td><td>L716+035@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716035-p106504-uk46573/</td><td>예</td><td>wknd35</td><td>예</td><td>https://author-p106504-e993081.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106504</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106504</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd35</td><td>https://author-p106504-e993081.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716036</td><td>106458</td><td>993120</td><td>L716+036@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716036-p106458-uk91382/</td><td>예</td><td>wknd36</td><td>예</td><td>https://author-p106458-e993120.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106458</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106458</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd36</td><td>https://author-p106458-e993120.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716037</td><td>106419</td><td>993160</td><td>L716+037@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716037-p106419-uk99235/</td><td>예</td><td>wknd37</td><td>예</td><td>https://author-p106419-e993160.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106419</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106419</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd37</td><td>https://author-p106419-e993160.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716038</td><td>106420</td><td>993162</td><td>L716+038@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716038-p106420-uk24222/</td><td>예</td><td>wknd38</td><td>예</td><td>https://author-p106420-e993162.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106420</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106420</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd38</td><td>https://author-p106420-e993162.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716039</td><td>106517</td><td>993235</td><td>L716+039@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716039-p106517-uk88649/</td><td>예</td><td>wknd39</td><td>예</td><td>https://author-p106517-e993235.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106517</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106517</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd39</td><td>https://author-p106517-e993235.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716040</td><td>106506</td><td>993079</td><td>L716+040@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716040-p106506-uk58481/</td><td>예</td><td>wknd40</td><td>예</td><td>https://author-p106506-e993079.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106506</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106506</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd40</td><td>https://author-p106506-e993079.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716041</td><td>106507</td><td>993074</td><td>L716+041@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716041-p106507-uk39478/</td><td>예</td><td>wknd41</td><td>예</td><td>https://author-p106507-e993074.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106507</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106507</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd41</td><td>https://author-p106507-e993074.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716042</td><td>106508</td><td>993075</td><td>L716+042@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716042-p106508-uk03034/</td><td>예</td><td>wknd42</td><td>예</td><td>https://author-p106508-e993075.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106508</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106508</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd42</td><td>https://author-p106508-e993075.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716043</td><td>106421</td><td>993163</td><td>L716+043@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716043-p106421-uk19734/</td><td>예</td><td>wknd43</td><td>예</td><td>https://author-p106421-e993163.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106421</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106421</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd43</td><td>https://author-p106421-e993163.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716044</td><td>106459</td><td>993121</td><td>L716+044@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716044-p106459-uk31012/</td><td>예</td><td>wknd44</td><td>예</td><td>https://author-p106459-e993121.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106459</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106459</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd44</td><td>https://author-p106459-e993121.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716045</td><td>106467</td><td>993292</td><td>L716+045@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716045-p106467-uk08507/</td><td>예</td><td>wknd45</td><td>예</td><td>https://author-p106467-e993292.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106467</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106467</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd45</td><td>https://author-p106467-e993292.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716046</td><td>106518</td><td>993234</td><td>L716+046@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716046-p106518-uk42276/</td><td>예</td><td>wknd46</td><td>예</td><td>https://author-p106518-e993234.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106518</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106518</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd46</td><td>https://author-p106518-e993234.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716047</td><td>106511</td><td>993076</td><td>L716+047@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716047-p106511-uk14074/</td><td>예</td><td>wknd47</td><td>예</td><td>https://author-p106511-e993076.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106511</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106511</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd47</td><td>https://author-p106511-e993076.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716048</td><td>106512</td><td>993077</td><td>L716+048@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716048-p106512-uk09248/</td><td>예</td><td>wknd48</td><td>예</td><td>https://author-p106512-e993077.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106512</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106512</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd48</td><td>https://author-p106512-e993077.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716049</td><td>106460</td><td>993124</td><td>L716+049@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716049-p106460-uk30141/</td><td>예</td><td>wknd49</td><td>예</td><td>https://author-p106460-e993124.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106460</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106460</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd49</td><td>https://author-p106460-e993124.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716050</td><td>106519</td><td>993237</td><td>L716+050@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716050-p106519-uk22660/</td><td>예</td><td>wknd50</td><td>예</td><td>https://author-p106519-e993237.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106519</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106519</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd50</td><td>https://author-p106519-e993237.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716051</td><td>106513</td><td>993084</td><td>L716+051@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716051-p106513-uk50830/</td><td>예</td><td>wknd51</td><td>예</td><td>https://author-p106513-e993084.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106513</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106513</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd51</td><td>https://author-p106513-e993084.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716052</td><td>106461</td><td>993122</td><td>L716+052@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716052-p106461-uk73956/</td><td>예</td><td>wknd52</td><td>예</td><td>https://author-p106461-e993122.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106461</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106461</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd52</td><td>https://author-p106461-e993122.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716053</td><td>106514</td><td>993082</td><td>L716+053@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716053-p106514-uk25965/</td><td>예</td><td>wknd53</td><td>예</td><td>https://author-p106514-e993082.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106514</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106514</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd53</td><td>https://author-p106514-e993082.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716054</td><td>106462</td><td>993123</td><td>L716+054@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716054-p106462-uk07017/</td><td>예</td><td>wknd54</td><td>예</td><td>https://author-p106462-e993123.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106462</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106462</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd54</td><td>https://author-p106462-e993123.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716055</td><td>106463</td><td>993127</td><td>L716+055@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716055-p106463-uk94955/</td><td>예</td><td>wknd55</td><td>예</td><td>https://author-p106463-e993127.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106463</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106463</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd55</td><td>https://author-p106463-e993127.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716056</td><td>106515</td><td>993083</td><td>L716+056@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716056-p106515-uk12658/</td><td>예</td><td>wknd56</td><td>예</td><td>https://author-p106515-e993083.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106515</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106515</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd56</td><td>https://author-p106515-e993083.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716057</td><td>106464</td><td>993126</td><td>L716+057@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716057-p106464-uk13238/</td><td>예</td><td>wknd57</td><td>예</td><td>https://author-p106464-e993126.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106464</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106464</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd57</td><td>https://author-p106464-e993126.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716058</td><td>106520</td><td>993236</td><td>L716+058@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716058-p106520-uk93785/</td><td>예</td><td>wknd58</td><td>예</td><td>https://author-p106520-e993236.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106520</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106520</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd58</td><td>https://author-p106520-e993236.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716059</td><td>106423</td><td>993161</td><td>L716+059@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716059-p106423-uk31356/</td><td>예</td><td>wknd59</td><td>예</td><td>https://author-p106423-e993161.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106423</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106423</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd59</td><td>https://author-p106423-e993161.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716060</td><td>106516</td><td>993078</td><td>L716+060@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716060-p106516-uk84089/</td><td>예</td><td>wknd60</td><td>예</td><td>https://author-p106516-e993078.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106516</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106516</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd60</td><td>https://author-p106516-e993078.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716061</td><td>106521</td><td>993240</td><td>L716+061@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716061-p106521-uk14423/</td><td>예</td><td>wknd61</td><td>예</td><td>https://author-p106521-e993240.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106521</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106521</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd61</td><td>https://author-p106521-e993240.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716062</td><td>106424</td><td>993308</td><td>L716+062@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716062-p106424-uk04070/</td><td>예</td><td>wknd62</td><td>예</td><td>https://author-p106424-e993308.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106424</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106424</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd62</td><td>https://author-p106424-e993308.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716063</td><td>106468</td><td>993295</td><td>L716+063@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716063-p106468-uk65739/</td><td>예</td><td>wknd63</td><td>예</td><td>https://author-p106468-e993295.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106468</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106468</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd63</td><td>https://author-p106468-e993295.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716064</td><td>106425</td><td>993309</td><td>L716+064@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716064-p106425-uk89411/</td><td>예</td><td>wknd64</td><td>예</td><td>https://author-p106425-e993309.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106425</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106425</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd64</td><td>https://author-p106425-e993309.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716065</td><td>106426</td><td>993314</td><td>L716+065@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716065-p106426-uk38598/</td><td>예</td><td>wknd65</td><td>예</td><td>https://author-p106426-e993314.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106426</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106426</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd65</td><td>https://author-p106426-e993314.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716066</td><td>106469</td><td>993293</td><td>L716+066@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716066-p106469-uk05356/</td><td>예</td><td>wknd66</td><td>예</td><td>https://author-p106469-e993293.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106469</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106469</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd66</td><td>https://author-p106469-e993293.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716067</td><td>106522</td><td>993238</td><td>L716+067@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716067-p106522-uk44251/</td><td>예</td><td>wknd67</td><td>예</td><td>https://author-p106522-e993238.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106522</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106522</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd67</td><td>https://author-p106522-e993238.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716068</td><td>106470</td><td>993299</td><td>L716+068@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716068-p106470-uk32462/</td><td>예</td><td>wknd68</td><td>예</td><td>https://author-p106470-e993299.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106470</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106470</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd68</td><td>https://author-p106470-e993299.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716069</td><td>106427</td><td>993311</td><td>L716+069@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716069-p106427-uk83971/</td><td>예</td><td>wknd69</td><td>예</td><td>https://author-p106427-e993311.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106427</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106427</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd69</td><td>https://author-p106427-e993311.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716070</td><td>106428</td><td>993310</td><td>L716+070@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716070-p106428-uk60835/</td><td>예</td><td>wknd70</td><td>예</td><td>https://author-p106428-e993310.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106428</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106428</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd70</td><td>https://author-p106428-e993310.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716071</td><td>106471</td><td>993298</td><td>L716+071@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716071-p106471-uk86739/</td><td>예</td><td>wknd71</td><td>예</td><td>https://author-p106471-e993298.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106471</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106471</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd71</td><td>https://author-p106471-e993298.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716072</td><td>106429</td><td>993315</td><td>L716+072@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716072-p106429-uk23084/</td><td>예</td><td>wknd72</td><td>예</td><td>https://author-p106429-e993315.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106429</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106429</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd72</td><td>https://author-p106429-e993315.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716073</td><td>106523</td><td>993239</td><td>L716+073@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716073-p106523-uk23422/</td><td>예</td><td>wknd73</td><td>예</td><td>https://author-p106523-e993239.adobeaemcloud.com/</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106523</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106523</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd73</td><td>https://author-p106523-e993239.adobeaemcloud.com//etc.clientlibs/toggles.json</td></tr><tr><td>L716074</td><td>106472</td><td>993300</td><td>L716+074@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716074-p106472-uk38017/</td><td>예</td><td>wknd74</td><td>예</td><td>https://author-p106472-e993300.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106472</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106472</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd74</td><td>https://author-p106472-e993300.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716075</td><td>106430</td><td>993312</td><td>L716+075@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716075-p106430-uk55913/</td><td>예</td><td>wknd75</td><td>예</td><td>https://author-p106430-e993312.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106430</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106430</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd75</td><td>https://author-p106430-e993312.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716076</td><td>106524</td><td>993241</td><td>L716+076@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716076-p106524-uk94081/</td><td>예</td><td>wknd76</td><td>예</td><td>https://author-p106524-e993241.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106524</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106524</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd76</td><td>https://author-p106524-e993241.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716077</td><td>106431</td><td>993313</td><td>L716+077@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716077-p106431-uk09241/</td><td>예</td><td>wknd77</td><td>예</td><td>https://author-p106431-e993313.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106431</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106431</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd77</td><td>https://author-p106431-e993313.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716078</td><td>106473</td><td>993294</td><td>L716+078@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716078-p106473-uk84023/</td><td>예</td><td>wknd78</td><td>예</td><td>https://author-p106473-e993294.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106473</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106473</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd78</td><td>https://author-p106473-e993294.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716079</td><td>106474</td><td>993297</td><td>L716+079@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716079-p106474-uk83600/</td><td>예</td><td>wknd79</td><td>예</td><td>https://author-p106474-e993297.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106474</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106474</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd79</td><td>https://author-p106474-e993297.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716080</td><td>106475</td><td>993296</td><td>L716+080@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716080-p106475-uk94755/</td><td>예</td><td>wknd80</td><td>예</td><td>https://author-p106475-e993296.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106475</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106475</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd80</td><td>https://author-p106475-e993296.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716081</td><td>106476</td><td>993353</td><td>L716+081@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716081-p106476-uk50558/</td><td>예</td><td>wknd81</td><td>예</td><td>https://author-p106476-e993353.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106476</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106476</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd81</td><td>https://author-p106476-e993353.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716082</td><td>106525</td><td>993247</td><td>L716+082@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716082-p106525-uk92893/</td><td>예</td><td>wknd82</td><td>예</td><td>https://author-p106525-e993247.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106525</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106525</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd82</td><td>https://author-p106525-e993247.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716083</td><td>106526</td><td>993244</td><td>L716+083@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716083-p106526-uk35635/</td><td>예</td><td>wknd83</td><td>예</td><td>https://author-p106526-e993244.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106526</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106526</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd83</td><td>https://author-p106526-e993244.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716084</td><td>106527</td><td>993243</td><td>L716+084@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716084-p106527-uk33428/</td><td>예</td><td>wknd84</td><td>예</td><td>https://author-p106527-e993243.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106527</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106527</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd84</td><td>https://author-p106527-e993243.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716085</td><td>106477</td><td>993356</td><td>L716+085@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716085-p106477-uk07483/</td><td>예</td><td>wknd85</td><td>예</td><td>https://author-p106477-e993356.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106477</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106477</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd85</td><td>https://author-p106477-e993356.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716086</td><td>106478</td><td>993355</td><td>L716+086@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716086-p106478-uk19752/</td><td>예</td><td>wknd86</td><td>예</td><td>https://author-p106478-e993355.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106478</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106478</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd86</td><td>https://author-p106478-e993355.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716087</td><td>106528</td><td>993245</td><td>L716+087@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716087-p106528-uk65196/</td><td>예</td><td>wknd87</td><td>예</td><td>https://author-p106528-e993245.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106528</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106528</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd87</td><td>https://author-p106528-e993245.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716088</td><td>106432</td><td>993316</td><td>L716+088@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716088-p106432-uk71669/</td><td>예</td><td>wknd88</td><td>예</td><td>https://author-p106432-e993316.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106432</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106432</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd88</td><td>https://author-p106432-e993316.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716089</td><td>106529</td><td>993242</td><td>L716+089@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716089-p106529-uk72336/</td><td>예</td><td>wknd89</td><td>예</td><td>https://author-p106529-e993242.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106529</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106529</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd89</td><td>https://author-p106529-e993242.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716090</td><td>106436</td><td>993320</td><td>L716+090@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716090-p106436-uk96513/</td><td>예</td><td>wknd90</td><td>예</td><td>https://author-p106436-e993320.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106436</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106436</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd90</td><td>https://author-p106436-e993320.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716091</td><td>106480</td><td>993301</td><td>L716+091@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716091-p106480-uk26189/</td><td>예</td><td>wknd91</td><td>예</td><td>https://author-p106480-e993301.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106480</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106480</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd91</td><td>https://author-p106480-e993301.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716092</td><td>106530</td><td>993246</td><td>L716+092@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716092-p106530-uk21496/</td><td>예</td><td>wknd92</td><td>예</td><td>https://author-p106530-e993246.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106530</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106530</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd92</td><td>https://author-p106530-e993246.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716093</td><td>106481</td><td>993352</td><td>L716+093@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716093-p106481-uk08136/</td><td>예</td><td>wknd93</td><td>예</td><td>https://author-p106481-e993352.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106481</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106481</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd93</td><td>https://author-p106481-e993352.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716094</td><td>106482</td><td>993354</td><td>L716+094@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716094-p106482-uk12991/</td><td>예</td><td>wknd94</td><td>예</td><td>https://author-p106482-e993354.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106482</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106482</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd94</td><td>https://author-p106482-e993354.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716095</td><td>106531</td><td>993248</td><td>L716+095@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716095-p106531-uk35835/</td><td>예</td><td>wknd95</td><td>예</td><td>https://author-p106531-e993248.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106531</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106531</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd95</td><td>https://author-p106531-e993248.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716096</td><td>106483</td><td>993357</td><td>L716+096@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716096-p106483-uk62544/</td><td>예</td><td>wknd96</td><td>예</td><td>https://author-p106483-e993357.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106483</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106483</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd96</td><td>https://author-p106483-e993357.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716097</td><td>106433</td><td>993318</td><td>L716+097@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716097-p106433-uk01013/</td><td>예</td><td>wknd97</td><td>예</td><td>https://author-p106433-e993318.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106433</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106433</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd97</td><td>https://author-p106433-e993318.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716098</td><td>106532</td><td>993249</td><td>L716+098@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716098-p106532-uk23995/</td><td>예</td><td>wknd98</td><td>예</td><td>https://author-p106532-e993249.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106532</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106532</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd98</td><td>https://author-p106532-e993249.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716099</td><td>106434</td><td>993317</td><td>L716+099@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716099-p106434-uk60991/</td><td>예</td><td>wknd99</td><td>예</td><td>https://author-p106434-e993317.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106434</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106434</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wknd99</td><td>https://author-p106434-e993317.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr><tr><td>L716100</td><td>106435</td><td>993319</td><td>L716+100@summitlab.us</td><td>예</td><td>https://git.cloudmanager.adobe.com/summit2023l716/L716100-p106435-uk70663/</td><td>예</td><td>wknd100</td><td>예</td><td>https://author-p106435-e993319.adobeaemcloud.com</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/home.html/program/106435</td><td>https://experience.adobe.com/#/@summit2023l716/cloud-manager/environments.html/program/106435</td><td>https://git.cloudmanager.adobe.com/summit2023l716/wkndtheme100</td><td>https://author-p106435-e993319.adobeaemcloud.com/etc.clientlibs/toggles.json</td></tr>
        </tbody>
    </table>

## 1과

### 목표

AEM Forms as a Cloud Service 환경을 숙지하십시오.

### 단원 컨텍스트

이 단원에서는 사용자 인터페이스를 탐색하여 AEM Forms as a Cloud Service 환경에 대해 숙지합니다.

### 연습

1. 브라우저를 열고 Cloud Service 작성 환경의 URL을 입력합니다. 예:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. 공유된 자격 증명에 따라 Cloud Service 작성 환경에 로그인합니다. 예: 사용자 이름: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
암호: 
**Adobe123!**

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


