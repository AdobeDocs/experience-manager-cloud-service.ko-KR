---
title: 적응형 양식에 대한 JSON 스키마를 디자인하는 방법
description: 적응형 양식에 대한 JSON 스키마를 만들고 스키마를 기반으로 적응형 양식을 만들어 스키마 컴플레인 데이터를 생성하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8eeb9c5e-6866-4bfe-b922-1f028728ef0d
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1388'
ht-degree: 6%

---

# 적응형 양식에 대한 JSON 스키마 디자인 {#creating-adaptive-forms-using-json-schema}


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| 핵심 구성 요소 | [여기 클릭](/help/forms/adaptive-form-core-components-json-schema-form-model.md) |
| 기초 | 이 문서 |

>[!NOTE]
>
> Adobe은 [새로운 적응형 Forms 만들기](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=ko) 또는 [AEM Sites 페이지에 적응형 Forms 추가](/help/forms/creating-adaptive-form-core-components.md)를 위해 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)를 사용할 것을 권장합니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 Forms을 작성하는 이전 방법에 대해 설명합니다.

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-json-schema-form-model.html?lang=ko) |
| AEM as a Cloud Service | 이 문서 |


## 사전 요구 사항 {#prerequisites}

JSON 스키마를 양식 모델로 사용하여 적응형 양식을 작성하려면 JSON 스키마에 대한 기본적인 이해가 필요합니다. 이 문서 전에 다음 내용을 읽어 보는 것이 좋습니다.

* [적응형 양식 만들기](creating-adaptive-form.md)
* [JSON 스키마](https://json-schema.org/)

## 양식 모델로 JSON 스키마 사용  {#using-a-json-schema-as-form-model}

Adobe Experience Manager Forms는 기존 JSON 스키마를 양식 모델로 사용하여 적응형 양식 만들기를 지원합니다. 이 JSON 스키마는 조직의 백엔드 시스템이 데이터를 생산 또는 소비하는 구조를 나타냅니다. 사용하는 JSON 스키마는 [v4 사양](https://json-schema.org/draft-04/schema)을 준수해야 합니다.

JSON 스키마 사용의 주요 기능은 다음과 같습니다.

* JSON 구조는 적응형 양식의 작성 모드에서 콘텐츠 파인더 탭에 트리로 표시됩니다. 요소를 JSON 계층에서 적응형 양식으로 드래그하여 추가할 수 있습니다.
* 연결된 스키마와 호환되는 JSON을 사용하여 양식을 미리 채울 수 있습니다.
* 제출 시 사용자가 입력한 데이터는 관련 스키마에 맞는 JSON으로 제출됩니다.
* [2012-20 버전](https://json-schema.org/draft/2020-12/release-notes)의 사양에 따라 JSON 스키마를 기반으로 양식을 만들 수도 있습니다.

JSON 스키마는 간단하고 복잡한 요소 유형으로 구성됩니다. 요소에는 요소에 규칙을 추가하는 속성이 있습니다. 이러한 요소와 속성을 적응형 양식으로 드래그하면 해당 적응형 양식 구성 요소에 자동으로 매핑됩니다.

적응형 양식 구성 요소와 JSON 요소의 이 매핑은 다음과 같습니다.

```json
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
  }
```

<table>
 <tbody>
  <tr>
   <th><strong>JSON 요소, 속성 또는 속성</strong></th>
   <th><strong>적응형 양식 구성 요소</strong></th>
  </tr>
  <tr>
   <td><p>enum 및 enumNames 제약 조건을 사용하는 문자열 속성입니다.</p> <p>구문,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td>
   <td><p>드롭다운 구성 요소:</p>
    <ul>
     <li>enumNames에 나열된 값은 드롭 상자에 표시됩니다.</li>
     <li>열거형에 나열된 값은 계산에 사용됩니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>형식 제약 조건이 있는 문자열 속성. (예: 이메일 및 날짜)</p> <p>구문,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>유형이 문자열이고 포맷이 이메일인 경우 이메일 구성 요소는 매핑됩니다.</li>
     <li>유형이 문자열이고 형식이 hostname인 경우 유효성 검사가 있는 Textbox 구성 요소가 매핑됩니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>}</code></p> </td>
   <td><br /> <br /> 텍스트 필드<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>number 속성<br /> </td>
   <td>하위 형식이 float<br />(으)로 설정된 숫자 필드 </td>
  </tr>
  <tr>
   <td>정수 속성<br /> </td>
   <td>하위 유형이 정수<br />(으)로 설정된 숫자 필드 </td>
  </tr>
  <tr>
   <td>부울 속성<br /> </td>
   <td>전환<br /> </td>
  </tr>
  <tr>
   <td>개체 속성<br /> </td>
   <td>패널<br /> </td>
  </tr>
  <tr>
   <td>배열 속성</td>
   <td>min 및 max가 각각 minItems 및 maxItems와 같은 반복 가능한 패널. Homogeneous 배열만 지원됩니다. 따라서 항목 제약 조건은 배열이 아닌 개체여야 합니다.<br /> </td>
  </tr>
 </tbody>
</table>

### 일반 스키마 속성 {#common-schema-properties}

적응형 양식은 JSON 스키마에서 사용할 수 있는 정보를 사용하여 생성된 각 필드를 매핑합니다. 특히

* `title` 속성은 적응형 양식 구성 요소에 대한 레이블 역할을 합니다.
* `description` 속성은 적응형 양식 구성 요소에 대한 긴 설명으로 설정됩니다.
* `default` 속성은 적응형 양식 필드의 초기 값 역할을 합니다.
* `maxLength` 속성이 텍스트 필드 구성 요소의 `maxlength` 특성으로 설정되어 있습니다.
* `minimum`, `maximum`, `exclusiveMinimum` 및 `exclusiveMaximum` 속성은 Numeric Box 구성 요소에 사용됩니다.
* `DatePicker component` 추가 JSON 스키마 속성 `minDate` 및 `maxDate`에 대한 범위를 지원하기 위해 제공됩니다.
* `minItems` 및 `maxItems` 속성은 패널 구성 요소에서 추가하거나 제거할 수 있는 항목/필드의 수를 제한하는 데 사용됩니다.
* `readOnly` 속성은 적응형 양식 구성 요소의 `readonly` 특성을 설정합니다.
* `required` 속성은 적응형 양식 필드를 필수 항목으로 표시하지만 패널(유형이 개체인 경우)에서 최종 제출된 JSON 데이터에는 해당 개체에 해당하는 빈 값이 있는 필드가 있습니다.
* `pattern` 속성은 적응형 양식에서 유효성 검사 패턴(정규 표현식)으로 설정되어 있습니다.
* JSON 스키마 파일의 확장은 .schema.json을 유지해야 합니다. 예: &lt;filename>.schema.json.

## 샘플 JSON 스키마 {#sample-json-schema}

>[!BEGINTABS]

>[!TAB JSON 스키마 v4]

```json
  {
  "$schema": "https://json-schema.org/draft-04/schema#",
  "definitions": {
    "employee": {
    "type": "object",
    "properties": {
      "userName": {
       "type": "string"
     },
      "dateOfBirth": {
       "type": "string",
       "format": "date"
      },
      "email": {
      "type": "string",
      "format": "email"
      },
      "language": {
       "type": "string"
     },
      "personalDetails": {
       "$ref": "#/definitions/personalDetails"
     },
      "projectDetails": {
       "$ref": "#/definitions/projectDetails"
      }
    },
    "required": [
     "userName",
     "dateOfBirth",
     "language"
    ]
    },
      "personalDetails": {
     "type": "object",
    "properties": {
       "GeneralDetails": {
      "$ref": "#/definitions/GeneralDetails"
     },
      "Family": {
       "$ref": "#/definitions/Family"
      },
      "Income": {
       "$ref": "#/definitions/Income"
     }
     }
       },
    "projectDetails": {
     "type": "array",
     "items": {
     "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```


>[!TAB JSON 스키마 2012-20]


```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://example.com/employee.schema.json",
  "$defs": {
    "employee": {
      "type": "object",
      "properties": {
        "userName": {
          "type": "string"
        },
        "dateOfBirth": {
          "type": "string",
          "format": "date"
        },
        "email": {
          "type": "string",
          "format": "email"
        },
        "language": {
          "type": "string"
        },
        "personalDetails": {
          "$ref": "#/$defs/personalDetails"
        },
        "projectDetails": {
          "$ref": "#/$defs/projectDetails"
        }
      },
      "required": [
        "userName",
        "dateOfBirth",
        "language"
      ]
    },
    "personalDetails": {
      "type": "object",
      "properties": {
        "GeneralDetails": {
          "$ref": "#/$defs/GeneralDetails"
        },
        "Family": {
          "$ref": "#/$defs/Family"
        },
        "Income": {
          "$ref": "#/$defs/Income"
        }
      }
    },
    "projectDetails": {
      "type": "array",
      "items": {
        "properties": {
          "name": {
            "type": "string"
          },
          "age": {
            "type": "number"
          },
          "projects": {
            "$ref": "#/$defs/projects"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "projects": {
      "type": "array",
      "items": {
        "properties": {
          "name": {
            "type": "string"
          },
          "age": {
            "type": "number"
          },
          "projectsAdditional": {
            "$ref": "#/$defs/projectsAdditional"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "projectsAdditional": {
      "type": "array",
      "items": {
        "properties": {
          "Additional_name": {
            "type": "string"
          },
          "Additional_areacode": {
            "type": "number"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "GeneralDetails": {
      "type": "object",
      "properties": {
        "age": {
          "type": "number"
        },
        "married": {
          "type": "boolean"
        },
        "phone": {
          "type": "number",
          "aem:afProperties": {
            "sling:resourceType": "/libs/fd/af/components/guidetelephone",
            "guideNodeClass": "guideTelephone"
          }
        },
        "address": {
          "type": "string"
        }
      }
      }
  }
  }
```

>[!ENDTABS]

JSON 스키마 V4에서 버전 2020-12 사양으로 주요 변경 사항은 다음과 같습니다.

* ID가 `$id`(으)로 선언되었습니다.
* 정의가 `$defs`(으)로 선언되었습니다.

### 재사용 가능한 스키마 정의 {#reusable-schema-definitions}

정의 키는 재사용 가능한 스키마를 식별하는 데 사용됩니다. 재사용 가능한 스키마 정의는 조각을 만드는 데 사용됩니다. <!-- It is similar to identifying complex types in XSD.--> 정의가 있는 샘플 JSON 스키마가 아래에 제공됩니다.

```json
{
  "$schema": "https://json-schema.org/draft-04/schema#",

  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },

  "type": "object",

  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

위의 예에서는 각 고객에게 배송 주소와 청구 주소가 모두 있는 고객 레코드를 정의합니다. 두 주소의 구조는 동일하며 주소에는 거리 주소, 도시 및 주가 있으므로 주소를 복제하지 않는 것이 좋습니다. 또한 향후 변경 시 필드를 쉽게 추가 및 삭제할 수 있습니다.

## JSON 스키마 정의의 사전 구성 필드 {#pre-configuring-fields-in-json-schema-definition}

**aem:afProperties** 속성을 사용하여 사용자 지정 적응형 양식 구성 요소에 매핑할 JSON 스키마 필드를 미리 구성할 수 있습니다. 예제는 아래에 나와 있습니다.

```json
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

<!--- ## Configure scripts or expressions for form objects  {#configure-scripts-or-expressions-for-form-objects}

JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. You can pre-configure form objects to [evaluate an expression](adaptive-form-expressions.md) on a form event.

Use the aem:afproperties property to preconfigure Adaptive Form expressions or scripts for Adaptive Form components. For example, when the initialize event is triggered, the below code sets value of telephone field and prints a value to the log :

```json
"telephone": {
  "type": "string",
  "pattern": "/\\d{10}/",
  "aem:affKeyword": ["phone", "telephone","mobile phone", "work phone", "home phone", "telephone number", "telephone no", "phone number"],
  "description": "Telephone Number",
  "aem:afProperties" : {
    "sling:resourceType" : "fd/af/components/guidetelephone",
    "guideNodeClass" : "guideTelephone",
    "events": {
      "Initialize" : "this.value = \"1234567890\"; console.log(\"ef:gh\") "
    }
  }
}
```

You should be a member of the [forms-power-user group](forms-groups-privileges-tasks.md) to configure scripts or expressions for form object. The below table lists all the script events supported for an Adaptive Form component.

<table>
 <tbody>
  <tr>
   <th><strong></strong>Component \ Event</th>
   <th>initialize <br /> </th>
   <td>Calculate</td>
   <td>Visibility</td>
   <td>Validate</td>
   <td>Enabled</td>
   <td>Value Commit</td>
   <td>Click </td>
   <td>Options</td>
  </tr>
  <tr>
   <td>Text Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Stepper</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Radio Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Telephone</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Switch</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
  </tr>
  <tr>
   <td>Check Box</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Drop-down</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Image Choice</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Date Input Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Date Picker</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Email</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>File Attachment</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Image</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Draw</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Panel</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Some examples of using events in a JSON are hiding a field on initialize event and configure value of another field on value commit event. For detailed information about creating expressions for the script events, see [Adaptive Form Expressions](adaptive-form-expressions.md).

Here is the sample JSON code for previously mentioned examples.

### Hiding a field on initialize event {#hiding-a-field-on-initialize-event}

```json

"name": {
    "type": "string",
    "aem:afProperties": {
        "events" : {
            "Initialize" : "this.visible = false;"
        }
    }
}
```

#### Configure value of another field on value commit event {#configure-value-of-another-field-on-value-commit-event}

```json
"Income": {
    "type": "object",
    "properties": {
        "monthly": {
            "type": "number",
            "aem:afProperties": {
                "events" : {
                    "Value Commit" : "IncomeYearly.value = this.value * 12;"
                }
            }
        },
        "yearly": {
            "type": "number",
            "aem:afProperties": {
                "name": "IncomeYearly"
            }
        }
    }
}

```
-->

## 적응형 양식 구성 요소에 허용되는 값 제한 {#limit-acceptable-values-for-an-adaptive-form-component}

JSON 스키마 요소에 다음 제한 사항을 추가하여 적응형 양식 구성 요소에 허용되는 값을 제한할 수 있습니다.

<table>
 <tbody>
  <tr>
   <td><p><strong> 스키마 속성</strong></p> </td>
   <td><p><strong>데이터 형식</strong></p> </td>
   <td><p><strong>설명</strong></p> </td>
   <td><p><strong>구성 요소</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>숫자 값 및 날짜의 상한을 지정합니다. 기본적으로 최대값이 포함됩니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼<br /> </li>
     <li>날짜 선택기</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>숫자 값 및 날짜의 하한을 지정합니다. 기본적으로 최소값이 포함됩니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택기</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>부울</p> </td>
   <td><p>true인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최대 속성에 지정된 숫자 값 또는 날짜보다 작아야 합니다.</p> <p>false인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최대 속성에 지정된 숫자 값 또는 날짜보다 작거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택기</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>부울</p> </td>
   <td><p>true인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최소 속성에 지정된 숫자 값 또는 날짜보다 커야 합니다.</p> <p>false인 경우 양식의 구성 요소에 지정된 숫자 값 또는 날짜는 최소 속성에 지정된 숫자 값 또는 날짜보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>숫자 상자</li>
     <li>숫자 스텝퍼</li>
     <li>날짜 선택기</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>구성 요소에 허용되는 최소 문자 수를 지정합니다. 최소 길이는 0보다 크거나 같아야 합니다.</p> </td>
   <td>
    <ul>
     <li>텍스트 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>문자열</td>
   <td>구성 요소에 허용되는 최대 문자 수를 지정합니다. 최대 길이는 0보다 크거나 같아야 합니다.</td>
   <td>
    <ul>
     <li>텍스트 상자</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>문자열</p> </td>
   <td><p>문자 시퀀스를 지정합니다. 문자가 지정된 패턴을 따르는 경우 구성 요소가 문자를 허용합니다.</p> <p>패턴 속성은 해당 적응형 양식 구성 요소의 유효성 검사 패턴에 매핑됩니다.</p> </td>
   <td>
    <ul>
     <li>XSD 스키마에 매핑된 모든 적응형 Forms 구성 요소 </li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxItems</code></td>
   <td>문자열</td>
   <td>배열의 최대 항목 수를 지정합니다. 최대 항목은 0보다 크거나 같아야 합니다.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>minItems</code></td>
   <td>문자열</td>
   <td>배열의 최소 항목 수를 지정합니다. 최소 항목은 0보다 크거나 같아야 합니다.</td>
   <td> </td>
  </tr>
 </tbody>
</table>


## 스키마 호환 데이터 활성화 {#enablig-schema-compliant-data}

양식 제출 시 모든 JSON 스키마 기반 적응형 Forms이 스키마 호환 데이터를 생성할 수 있도록 하려면 다음 단계를 따르십시오.

1. `https://server:host/system/console/configMgr`의 Experience Manager 웹 콘솔로 이동합니다.
1. **[!UICONTROL 적응형 양식 및 대화형 통신 웹 채널 구성]**&#x200B;을 찾습니다.
1. 을(를) 선택하여 편집 모드로 구성을 엽니다.
1. **[!UICONTROL 스키마 호환 데이터 생성]** 확인란을 선택하십시오.
1. 설정을 저장합니다.

![적응형 양식 및 대화형 통신 웹 채널 구성](/help/forms/assets/af-ic-web-channel-configuration.png)


## 지원되지 않는 구문  {#non-supported-constructs}

적응형 Forms은 다음 JSON 스키마 구성을 지원하지 않습니다.

* Null 유형
* 및 와 같은 유니온 유형
* OneOf, AnyOf, AllOf 및 NOT
* Homogeneous 배열만 지원됩니다. 따라서 항목 제약 조건은 배열이 아닌 개체여야 합니다.
* $ref의 URI 참조

## 자주 묻는 질문 {#frequently-asked-questions}

**반복 가능한 하위 양식(minOccours 또는 maxOccurs 값이 1보다 큼)에 대해 하위 양식(복합 유형에서 생성된 구조)의 개별 요소를 드래그할 수 없는 이유는 무엇입니까?**

반복 가능한 하위 양식에서는 전체 하위 양식을 사용해야 합니다. 선택 필드만 사용하려는 경우 전체 구조를 사용하고 원하지 않는 구조는 삭제하십시오.

**콘텐츠 파인더에 긴 복잡한 구조가 있습니다. 특정 요소를 찾으려면 어떻게 해야 합니까?**

다음 두 가지 옵션이 있습니다.

* 트리 구조를 스크롤합니다.
* 검색 상자를 사용하여 요소 찾기

**JSON 스키마 파일의 확장명은 무엇입니까?**

JSON 스키마 파일의 확장명은 .schema.json이어야 합니다. 예: &lt;filename>.schema.json.

## 추가 참조 {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Design XML Schema for an Adaptive Form](/help/forms/adaptive-form-xml-schema-form-model.md)

-->
