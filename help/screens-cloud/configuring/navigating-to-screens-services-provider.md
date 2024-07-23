---
title: Screens Services Provider로 이동
description: 이 페이지에서는 Screens 서비스 공급자로 이동하는 방법에 대해 설명합니다.
exl-id: 9eff6fe8-41d4-4cf3-b412-847850c4e09c
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: 5452a02ed20d70c09728b3e34f248c7d37fc4668
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 4%

---

# Screens Services Provider로 이동 {#setup-screens-services-provider}

## 소개 {#introduction}

**Screens 서비스 공급자**&#x200B;를 사용하면 콘텐츠를 채널에 추가한 후 콘텐츠 작성자, 개발자 및 관리자가 콘텐츠를 재생할 수 있는 디스플레이와 플레이어를 관리할 수 있습니다. 사용자에게 AEM Cloud Service에 대한 액세스 권한이 부여되면 Screens 서비스 공급자에 로그인할 수 있어야 합니다.

이 섹션에서는 Screens 서비스 공급자를 설정하는 방법에 대해 설명합니다.


## 목표 {#objective}

다음 섹션에서는 Screens Services Provider를 구성하고 설정하는 방법을 설명합니다.

## Screens 서비스 공급자 설정 절차 {#screens-services-provider}

Screens 서비스 공급자를 설정하려면 아래 단계를 따르십시오.

1. [여기](https://experience.adobe.com/screens)에서 Screens 서비스 공급자로 이동합니다.

   >[!CAUTION]
   >여러 조직에 대한 액세스 권한이 있는 경우 올바른 조직에 로그인했는지 확인하십시오. 조직을 변경하려면 화면 오른쪽 상단에서 조직 이름을 클릭하고 액세스가 필요한 필수 조직을 선택합니다.

1. 프로젝트 옆에 있는 톱니바퀴 아이콘(왼쪽 위 모서리)을 클릭합니다

   ![이미지](/help/screens-cloud/assets/configure/configure-screens0.png)

1. 설정 편집 대화 상자에 다음 세부 정보를 입력합니다.
   * **Publish Url** - AEM 게시 URL(예: `https://publish-p12345-e12345.adobeaemcloud.com`)
   * **작성자 URL** - AEM 작성자 URL(예: `https://author-p12345-e12345.adobeaemcloud.com`)

   >[!NOTE]
   >Screens 서비스 공급자에서 AEM을 구성하기 전에 AEM Screen 채널을 하나 이상 만들고 게시해야 합니다. 채널을 만들려면 콘텐츠 공급자에서 /screens.html으로 이동합니다.

   ![이미지](/help/screens-cloud/assets/configure/configure-screens4.png)

1. Screens 콘텐츠 공급자에 연결하려면 **저장**&#x200B;을 클릭하십시오.

1. Cloud Manager의 IP 허용 목록에 추가하다 기능을 통해 신뢰할 수 있는 IP 주소에만 액세스할 수 있도록 AEM 게시 인스턴스를 구성한 경우 아래 표시된 대로 설정 대화 상자에서 키 값으로 헤더를 구성해야 합니다.
화이트리스트에 추가해야 하는 IP도 구성 파일로 이동하고 Cloud Manager 설정에서 [적용 취소](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list)해야 합니다.

   ![이미지](/help/screens-cloud/assets/configure/configure-screens20b.png)
AEM CDN 구성에서 동일한 키를 구성해야 합니다.  헤더 값을 GITHub에 직접 입력하지 않고 [비밀 참조](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-credentials-authentication#rotating-secrets)를 사용하는 것이 좋습니다.
샘플 [CDN 구성](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf)은(는) 아래에 제공됩니다.

   ```kind: "CDN"
       version: "1"
       metadata:
         envTypes: ["dev", "stage", "prod"]
       data:
         trafficFilters:
           rules:
             - name: "block-request-from-not-allowed-ips"
               when:
                 allOf:
                   - reqProperty: clientIp
                     notIn: ["101.41.112.0/24"]
                    reqProperty: tier
                     equals: publish
               action: block
             - name: "allow-requests-with-header"
               when:
                 allOf:
                   - reqProperty: tier
                     equals: publish
                   - reqProperty: path
                     equals: /screens/channels.json
                   - reqHeader: x-screens-allowlist-key
                     equals: $\
       {CDN_HEADER_KEY}
               action:
                 type: allow
   ```

1. 왼쪽 탐색 모음에서 **채널**&#x200B;을 선택하고 **콘텐츠 공급자에서 열기**&#x200B;를 클릭합니다.

   ![이미지](/help/screens-cloud/assets/configure/configure-screens1.png)

1. Screens 콘텐츠 공급자는 콘텐츠를 만들 수 있는 다른 탭에서 열립니다.

   ![이미지](/help/screens-cloud/assets/configure/configure-screens2.png)





## 다음 단계 {#whats-next}

Screens Services Provider를 설정하는 방법에 대해 알아본 후 자세한 내용을 보려면 [Screens Content Provider 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html#screens-content-provider)(으)로 이동하십시오.
