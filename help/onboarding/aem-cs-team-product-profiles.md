---
title: AEM as a Cloud Service 팀 및 제품 프로필
description: AEM as a Cloud Service 팀 및 제품 프로필이 사용 허가된 Adobe 솔루션에 대한 액세스 권한을 부여 및 제한할 수 있는 방법에 대해 알아봅니다.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 86bb2e020a003fd418f8b1cf7bdf55987a2eaf3d
workflow-type: tm+mt
source-wordcount: '2062'
ht-degree: 98%

---


# AEM as a Cloud Service 팀 및 제품 프로필 {#product-profiles}

AEM as a Cloud Service 팀 및 제품 프로필이 사용 허가된 Adobe 솔루션에 대한 액세스 권한을 부여 및 제한할 수 있는 방법에 대해 알아봅니다.

## 제품 프로필 {#profiles}

사용자에게 특정 Adobe 솔루션에 대한 액세스 권한을 부여할 때 반드시 전체 액세스 권한을 부여할 필요는 없습니다. 제품 프로필을 사용하면 각 솔루션이 고유한 사용자 권한 집합을 가질 수 있습니다. [Admin Console](/help/journey-onboarding/admin-console.md)을 통해 사용하고 액세스할 수 있습니다.

Adobe Admin Console은 조직의 내부 사용자에게 멤버십을 할당할 수 있는 제품, 제품 인스턴스 및 제품 프로필의 구조화된 계층 구조를 갖추고 있어 라이선스가 부여된 솔루션과 기능에 액세스할 수 있습니다.

<!-- Alexandru: Drafting for now 

Your AEM as a Cloud Service team members are added and assigned to one or more of the following product profiles via the Admin Console during onboarding.

* **AEM Administrators**: An AEM administrator is typically assigned to developers, in particular developers who need access to, for example, the development environments. The AEM administrator's product profile is used to grant administrator privileges in the associated AEM instance.

* **AEM Users**: AEM users are the users in your organization who use AEM as a Cloud Service generally to create content. These users need to access AEM to do their tasks. The AEM users product profile is typically assigned to an AEM content author who creates and reviews the content. This content can be of many types such as pages, assets, publications, and so on. The AEM users product profile shown below is assigned to these members.

![Product profiles](/help/onboarding/assets/admin-console-profiles.png) -->

## AEM as a Cloud Service 제품 프로필 {#aem-product-profiles}

AEM as a Cloud Service는 AEM as a Service를 제공하는 완전한 클라우드 네이티브 제품입니다. 항상 켜짐 상태 유지, 최신 상태 유지, 보안 유지, 규모에 맞는 확장과 같은 새로운 속성을 사용하여 클라우드 네이티브 방식으로 AEM을 제공합니다. 동시에 AEM이 고객에게 사용자 정의 플랫폼으로 제공하는 주요 가치 제안을 유지하고 기업 전문 팀이 개발 및 게재 절차에 AEM을 통합할 수 있도록 지원합니다. AEM as a Cloud Service에 대해 자세히 알아보려면 [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)를 참조하십시오.

### 조직 수준 제품 인스턴스 {#org-level-product-instances}

>[!NOTE]
>
> 이 문서에서 설명하는 일부 제품 인스턴스와 제품 프로필은 새로 생성된 환경에서만 나타날 수 있습니다. 환경을 현대화하는 방법은 [기존 환경에 대한 제품 프로필 추가](#adding-product-profiles-for-existing-environments)를 참조하십시오.

Adobe가 처음으로 AEM 솔루션의 라이선스를 처리하면 Adobe Admin Console에서 Adobe Experience Manager as a Cloud Service 제품 아래에 두 개의 제품 인스턴스가 표시됩니다.

* **AEM 조직 수준** - 단일 AEM 환경에만 국한되지 않고 모든 AEM 환경에 적용되는 기능의 액세스를 나타내는 하나 이상의 제품 프로필을 포함합니다.
* **Cloud Manager** - Cloud Manager 기능에 대한 다양한 액세스 수준의 제품 프로필을 포함합니다.

<!--
>[!NOTE]
>
>For existing programs, the AEM Org-Level Product Instance is created upon selecting the **Update product** profiles action for a given environment.
-->

![조직 수준 제품 인스턴스](/help/onboarding/assets/orglevel.png)

AEM 조직 수준 제품 인스턴스 내부에는 현재 사용되지 않지만 향후 AEM 제품 라이선스에 대한 정보를 검색하는 데 사용할 수 있는 AEM 조직 수준 리포터라는 제품 프로필이 있습니다.

Forms Communication Solution 라이선스가 부여되면 AEM 조직 수준 제품 인스턴스 아래에도 해당 제품 프로필이 표시됩니다.

![리포터 제품 프로필](/help/onboarding/assets/org-level-reporters.png)

### 환경 및 계층 수준 제품 인스턴스 {#environment-and-tier-level-product-instances}

하나 이상의 AEM 환경으로 새 프로그램을 프로비저닝하면 환경당 두 개의 제품 인스턴스가 표시되며, 작성자와 게시자의 제품 프로필이 각각 포함됩니다.

![환경 제품 인스턴스](/help/onboarding/assets/env-productinstances.png)

아래는 AEM Sites가 포함된 프로그램에서 환경을 프로비저닝한 조직의 작성자 제품 인스턴스의 제품 프로필입니다.

![Sites 제품 인스턴스](/help/onboarding/assets/sites-product-instances.png)

다음 테이블은 환경 계층별 제품 인스턴스 아래에 있을 수 있는 제품 프로필 목록을 설명합니다.

<table style="table-layout:auto">
    <tr>
        <th>제품 인스턴스</th>
        <th>명명 규칙</th>
        <th>기본 서비스</th>
        <th>설명</th>
    </tr>
    <tr>
        <td>AEM Author</td>
        <td>AEM Sites 콘텐츠 관리자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Sites 콘텐츠 관리자</td>
        <td>
            <ul>
                <li>이 환경의 AEM Sites 작성자 기능에 대한 액세스를 제어하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM Sites 콘텐츠 작성자 AEM 그룹의 멤버가 됩니다. AEM 그룹 권한을 원하는 액세스 수준으로 AEM에서 구성해야 합니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM Sites 콘텐츠 관리자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                      <!--  <li>users in this product profile will have access to AEM Sites Content Management API.</li>
                        <li>an Adobe Developer Console API OAuth S2S project containing AEM Sites Content Management API can optionally be scoped to this environment.</li>-->
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM 관리자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM 관리자</td>
        <td>
            <ul>
                <li>AEM 작성자 및 게시 환경 기능에 제한 없이 액세스하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM 관리자 작성자 AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM 관리자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM 사용자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM 사용자</td>
        <td>
            <ul>
                <li>AEM 작성자 환경 기능에 대해 매우 제한적으로 액세스하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 “참여자” AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM 사용자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM 리포터 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM 리포터</td>
        <td>
            <ul>
                <li>현재 사용되지는 않지만 향후에는 이 환경에 대한 작성자 계층의 보고 정보에 액세스할 수 있습니다.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets 공동 작업자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Assets 공동 작업자 사용자</td>
        <td>
        <ul>
                <li>DAM에 대해 읽기 전용으로 액세스하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 “참여자” AEM 그룹의 멤버가 됩니다.
                </li>
                <li>
                또한 자산 베리에이션을 생성할 수 있는 Adobe Express 권한도 제공합니다.
                </li>
          <ul>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets 파워 유저 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Assets 파워 유저</td>
<td>
        <ul>
                <li>DAM에 대해 읽기 전용으로 액세스하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 “참여자” AEM 그룹의 멤버가 됩니다.
                </li>
                <li>
                또한 자산 베리에이션을 생성할 수 있는 Adobe Express 권한도 제공합니다.
                </li>
          <ul>
</td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms 콘텐츠 관리자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Forms 콘텐츠 관리자</td>
        <td>
            <ul>
                <li>이 환경의 AEM Forms 작성자 기능에 대한 액세스를 제어하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM Forms 양식 사용자 AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM Forms 콘텐츠 관리자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms 개발자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Forms 개발자</td>
        <td>
            <ul>
                <li>이 환경의 AEM Forms 작성자 기능에 대한 액세스를 제어하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM Forms 파워 유저 AEM 그룹의 멤버가 됩니다. 이러한 사용자는 일반 양식 작성 작업 외에도 XDP 및 작성자 양식 데이터 모델을 업로드할 수 있는 권한이 있습니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM Forms 개발자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms 커뮤니케이션 서비스 사용자 - 작성자 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Forms 커뮤니케이션 서비스 사용자</td>
        <td>
            <ul>
                <li>이 환경에서 AEM Forms 커뮤니케이션 서비스 기능에 대한 액세스를 제어하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM Forms 양식 사용자 AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM Forms 커뮤니케이션 서비스 사용자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>AEM 게시</td>
        <td>AEM 사용자 - 게시 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM 사용자</td>
        <td>
            <ul>
                <li>AEM 작성자 환경 기능에 대해 매우 제한적으로 액세스하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 “참여자” AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM 사용자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM 리포터 - 게시 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM 리포터</td>
        <td>
            <ul>
                <li>현재 사용되지는 않지만 향후에는 이 환경에 대한 게시 계층의 보고 정보에 액세스할 수 있습니다.</li>
            </ul>
        </td>
    </tr>
   <tr>
        <td></td>
        <td>AEM Forms 커뮤니케이션 서비스 사용자 - 게시 - 프로그램 <code>id</code> - 환경 <code>id</code></td>
        <td>AEM Forms 커뮤니케이션 서비스 사용자</td>
        <td>
            <ul>
                <li>이 환경에서 AEM Forms 커뮤니케이션 서비스 기능에 대한 액세스를 제어하기 위한 것입니다. 이 제품 프로필의 사용자는 AEM에서 자동으로 생성되는 AEM Forms 양식 사용자 AEM 그룹의 멤버가 됩니다.</li><br>
                <li>기본 서비스가 선택된 상태로 유지되는 경우
                    <ul>
                        <li>이 제품 프로필의 사용자는 “AEM Forms 커뮤니케이션 서비스 사용자 - 서비스” AEM 그룹의 멤버이기도 합니다.</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
</table>

각 제품 프로필에는 기본적으로 관련 제품 프로필 서비스가 활성화되어 있습니다. 복잡한 액세스 요구 사항이 없는 경우 기본 서비스만 선택된 상태로 유지하는 것이 좋습니다. 명명 규칙 `<Product Profile Prefix> - Service`(예: **AEM Sites 콘텐츠 관리자 - 서비스**)을 사용하여 해당 AEM 그룹이 AEM에 생성되며, 상위 제품 프로필의 사용자는 자동으로 해당 AEM 그룹의 멤버가 됩니다.

서비스와 관련된 AEM의 AEM 그룹에는 해당 환경 계층 조합에 대한 해당 서비스의 관련 제품 프로필 내 사용자 집계 집합이 있습니다.

![서비스](/help/onboarding/assets/services.png)

다음 이미지는 AEM Sites 콘텐츠 관리자 작성자 계층 제품 프로필 및 서비스를 반영하는 AEM 그룹을 나타냅니다.

![AEM 그룹에서 서비스로의 매핑](/help/onboarding/assets/profile-to-service-mapping.png)

>[!NOTE]
>
>AEM as a Cloud Service 제품 프로필에 할당된 모든 사용자는 **Cloud Manager 사용자** 역할을 통한 Cloud Manager에 대한 읽기 전용 액세스 권한이 있습니다.
>
>**Cloud Manager 사용자**&#x200B;역할만 있는 사용자는 **프로그램** 메뉴 옵션을 사용하여 Cloud Manager에 로그인하고 AEM 작성자 환경(존재하는 경우)으로 이동할 수 있습니다. **Cloud Manager 사용자** 역할은 프로그램 세부 정보에 액세스하기에 충분하지 않습니다. 이러한 액세스 권한이 필요한 경우 사용자는 시스템 관리자로부터 추가 역할을 부여받아야 합니다.

>[!WARNING]
>
>**AEM 관리자** 제품 프로필 이름은 변경하면 안 됩니다. **AEM 관리자** 제품 프로필의 이름을 변경하면 해당 프로필에 할당된 모든 사용자의 관리자 권한이 제거됩니다.

>[!TIP]
>
>* AEM 제품 프로필에 대한 자세한 내용은 [AEM 제품 프로필 할당](/help/journey-onboarding/assign-profiles-aem.md) 문서를 참조하십시오.
>* 온보딩 프로세스에 대한 자세한 내용은 [온보딩 여정](/help/journey-onboarding/overview.md)을 참조하십시오.

### 기존 환경의 제품 프로필 추가 {#adding-product-profiles-for-existing-environments}

2024년 4월 초 전에 생성된 환경에는 위의 섹션에 설명된 조직 수준 제품 인스턴스와 특정 제품 프로필이 누락될 수 있습니다. 기존 제품 프로필에도 서비스 토글이 없습니다. 일부 향후 API에 액세스하기 위한 필수 구성 요소인 해당 제품 프로필을 업데이트하는 것이 좋습니다.

프로그램의 환경 하나 이상에서 제품 프로필을 업데이트해야 하는 경우 Cloud Manager에 아래 알림이 표시됩니다. 제품 프로필을 업데이트하려면 먼저 환경을 최신 AEM 버전으로 업데이트해야 합니다.

![제품 프로필 현대화](/help/onboarding/assets/modernize-product-profiles.png)

**제품 프로필 추가** 버튼을 클릭하면 프로그램에서 사용 가능한 모든 환경이나 개별 환경에 새 제품 프로필을 추가할 수 있는 옵션을 표시하는 메뉴가 열립니다.

![환경 대체](/help/onboarding/assets/choose-env-r.png)

**모든 환경**&#x200B;을 클릭하여 새 제품 프로필을 프로그램의 모든 환경에 추가합니다. 또는 **개별 환경**&#x200B;을 클릭하여 선택한 환경에 새 제품 프로필을 추가합니다. **추가 선택 사항** 아이콘에서 **제품 프로필 추가** 액션을 선택할 수 있는 환경 목록 페이지로 사용자를 안내합니다.

![개별 환경](/help/onboarding/assets/individual-environments.png)

프로그램 개요 페이지의 환경 섹션으로 이동한 다음 환경에 해당되는 추가 선택 사항 아이콘을 클릭하고 제품 프로필 추가를 선택하여 선택한 환경에 제품 프로필을 추가할 수도 있습니다.

환경의 상태는 새 제품 프로필이 추가되는 동안에는 제품 프로필 추가 중으로 표시되고, 프로세스가 완료되면 실행 중으로 표시됩니다.


## Cloud Manager 제품 프로필 {#cloud-manager-product-profiles}

Cloud Manager에는 역할 기반 권한으로 생각할 수 있는 사전 구성된 제품 프로필이 있습니다. 시스템 관리자는 이러한 제품 프로필에 할당하여 Cloud Manager 팀을 설정할 책임이 있습니다.

>[!TIP]
>
>자세한 내용은 [Cloud Manager의 역할 기반 권한](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)을 참조하십시오.

각 제품 프로필에는 연결된 특정 권한이 있습니다.

* **비즈니스 소유자**
   * 이 역할에는 새 프로그램을 추가하거나 프로그램을 편집하고, 환경을 추가 또는 업데이트하거나, AEM 환경에 코드를 배포하거나, 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
   * 이 사용자는 KPI를 정의하고, 프로덕션 구축을 승인하며, 필요한 경우 중요한 3계층 오류를 재정의할 책임이 있습니다.
* **배포 관리자**
   * 이 역할에는 환경을 추가 또는 업데이트하거나, 파이프라인을 실행하거나, AEM 환경에 코드를 배포하거나, 코드 품질 검사를 실행할 수 있는 권한이 있습니다.
   * 이 사용자는 배포 작업을 관리하고 Cloud Manager를 사용하여 스테이징/프로덕션 배포를 실행하고, CI/CD 파이프라인을 편집하고, 필요한 경우 중요한 3계층 오류를 승인하며, git 저장소에 액세스할 수 있습니다.
* **개발자**
   * 이 역할에는 git에 액세스하기 위한 개인 액세스 토큰을 생성할 수 있는 권한이 있습니다.
   * 이 사용자는 사용자 정의 애플리케이션 코드를 개발 및 테스트하고 주로 Cloud Manager를 사용하여 배포 상태를 보고 코드 커밋을 위해 git 저장소에 액세스할 수 있습니다.
* **프로그램 관리자**
   * 이 역할에는 파이프라인을 예약하고, 3계층 품질 게이트를 재정의하고, 프로덕션 승인을 제공할 수 있는 권한이 있습니다.
   * 이 사용자는 Cloud Manager를 사용하여 팀 설정, 상태 검토, KPI 보기를 수행하며 필요한 경우 중요한 3계층 오류를 승인할 수 있습니다.

한 사용자에게 여러 제품 프로필을 할당할 수 있습니다. 예를 들어 사용자에게 **비즈니스 소유자** 및 **배포 관리자** 역할을 모두 할당하면 이러한 권한이 모두 더해져 제공됩니다.

Cloud Manager 팀에는 최소한 다음 역할이 포함됩니다.

* 일반적으로 시스템 관리자이며 Cloud Manager에 로그인하고 액세스하는 첫 번째 사람인 **비즈니스 소유자** 1명
* **배포 관리자** 1명
* **개발자** 1명

>[!NOTE]
>
>AEM as a Cloud Service에 대한 액세스 권한을 부여받으려면 사용자가 `AEM Users` 또는 `AEM Administrators` 제품 프로필 중 하나에 속해야 합니다. Cloud Manager를 관리할 수 있는 권한만으로는 충분하지 않습니다.

>[!TIP]
>
>* Cloud Manager 제품 프로필에 대한 자세한 내용은 [Cloud Manager 제품 프로필에 팀원 할당](/help/journey-onboarding/assign-profiles-cloud-manager.md)을 참조하십시오.
>* 온보딩 프로세스에 대한 자세한 내용은 [온보딩 여정](/help/journey-onboarding/overview.md)을 참조하십시오.
