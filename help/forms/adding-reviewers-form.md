---
title: 검토를 위해 적응형 양식을 보내는 방법
description: 하나 이상의 검토자와 검토용 적응형 양식을 공유합니다.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
docset: aem65
source-git-commit: 57e421a865b664c0adb7af93b33bd4b6b32049ab
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# 제출 서류 검토자를 양식과 연결 {#associating-submission-reviewers-with-a-form}

양식을 만들 때 양식 포털을 통해 양식 제출을 검토하고 피드백을 제공하는 사용자를 지정할 수 있습니다. 조직은 피드백을 수집하고 제출된 양식에 대해 다시 작업할 수 있습니다.

[!DNL AEM Forms]을(를) 사용하면 검토자 그룹을 양식과 연결할 수 있습니다. 양식의 검토 그룹에 추가된 사용자는 이 양식의 제출 사항을 보고 피드백을 제공합니다.

양식에 할당된 검토자 그룹은 지정된 양식의 제출만 검토할 수 있습니다.

## 전제 조건 {#prerequisite}

### 메타데이터 스키마 편집기를 사용하여 적응형 Forms에 대해 제출 검토자 그룹 속성 활성화 {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

검토자 그룹을 양식에 연결하려면 적응형 Forms의 메타데이터 스키마를 편집합니다. 기본적으로 제출된 양식에 검토자 그룹을 추가할 수 없습니다.

메타데이터 스키마를 편집하려면:

1. 작성자 모드의 Experience Manager에서 **도구** > **Assets** > **메타데이터 스키마**&#x200B;를 클릭합니다.
1. 스키마 Forms 페이지에서 **Forms** > **AEM에서 작성된 Forms**&#x200B;으로 이동합니다.

   페이지의 URL은 다음과 같습니다.

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. **적응형 양식**&#x200B;을 선택하고 **편집**&#x200B;을 클릭합니다.
1. 양식 편집 페이지에서 **고급**&#x200B;을 클릭합니다.
1. 고급 탭에서 빌드 양식에서 사용할 수 있는 **한 줄 텍스트** 구성 요소를 드래그 앤 드롭합니다.
1. 추가된 텍스트 구성 요소를 선택하여 해당 설정을 확인합니다.

   [설정] 아래의 [속성에 매핑] 필드에 `./jcr:content/metadata/form-submission-reviewer-group`을(를) 입력합니다.

   적응형 양식의 고급 속성에 있는 제출 검토자 그룹 필드는 필드 레이블 아래에 지정한 이름으로 활성화됩니다.

## 제출 서류 검토자를 양식과 연결 {#associating-submission-reviewers-with-a-form-1}

제출 검토자를 적응형 양식과 연결하려면 검토자 그룹을 만들고 사용자를 추가하십시오. 양식의 고급 속성에서 양식 제출 검토자 필드 아래에 작성된 검토자 그룹을 추가합니다.
사용자 그룹을 사용하면 다양한 제출 검토자 세트를 다른 적응형 Forms과 연결할 수 있습니다. 이 기능은 권한이 없는 사용자의 제출 검토를 방지합니다.

다음 단계를 수행하기 전에 [필수 구성 요소](adding-reviewers-form.md#prerequisite)를 참조하십시오.

그룹을 만들고 구성원을 추가하려면 **도구** > **작업** > **보안** > **그룹**(으)로 이동합니다.
자세한 내용은 [사용자 관리 및 서비스](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html)를 참조하십시오.
만든 그룹을 기본 제공 사용자 그룹 **forms-submission-reviewers**&#x200B;의 구성원으로 추가했는지 확인하십시오. 이 사용자 그룹은 [!DNL AEM Forms]과(와) 함께 제공되며 사용자가 제출 검토자로 추가되었는지 확인합니다.

사용자 그룹을 적응형 양식에 연결하려면 다음 작업을 수행하십시오.

1. 작성 모드에서 **Forms** > **Forms 및 문서**(으)로 이동합니다.
1. **선택**옵션을 사용하여 적응형 양식을 선택하고 **속성 보기**&#x200B;를 클릭하세요.
1. 양식의 속성 창에서 **편집**&#x200B;을 클릭한 다음 **고급**&#x200B;을 클릭합니다.
1. 제출 검토자 그룹 필드에 그룹을 입력하고 **완료**&#x200B;를 클릭합니다.

   제출 서류 검토자 그룹 필드가 적응형 Forms의 편집된 메타데이터 스키마에 지정한 이름으로 나타납니다.

>[!NOTE]
>
>[!DNL AEM Forms]의 원격 구현에서 사용자 및 양식의 가용성을 보장하기 위해 사용자 및 양식을 복제하십시오.
>
>모든 사용자가 원격 구현에서 사용자 그룹의 구성원을 검토하는 것으로 복제되는지 확인하십시오.

>[!MORELIKETHIS]
>
>* [양식에 대한 리뷰 만들기 및 관리](/help/forms/create-reviews-forms.md)
>* [적응형 양식에 대한 리뷰 만들기 및 관리](/help/forms/review-adaptiveforms-in-sites-page.md)