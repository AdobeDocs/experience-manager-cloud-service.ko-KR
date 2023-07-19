---
title: AEM을 통해 GraphQL을 사용하는 방법 알아보기 - 샘플 콘텐츠 및 쿼리
description: AEM으로 GraphQL을 사용하여 샘플 콘텐츠 및 쿼리 탐색을 통해 Headless 방식으로 콘텐츠를 제공하는 방법을 배웁니다.
feature: Content Fragments,GraphQL API
exl-id: b60fcf97-4736-4606-8b41-4051b8b0c8a7
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: ht
source-wordcount: '1752'
ht-degree: 100%

---

# AEM을 통해 GraphQL을 사용하는 방법 알아보기 - 샘플 콘텐츠 및 쿼리 {#learn-graphql-with-aem-sample-content-queries}

AEM으로 GraphQL을 사용하여 샘플 콘텐츠 및 쿼리 탐색을 통해 Headless 방식으로 콘텐츠를 제공하는 방법을 배웁니다.

>[!NOTE]
>
>다음 사항이 포함된 이 페이지를 읽으십시오.
>
>* [콘텐츠 조각](/help/sites-cloud/administering/content-fragments/content-fragments.md)
>* [콘텐츠 조각 모델](/help/sites-cloud/administering/content-fragments/content-fragments-models.md)
>* [콘텐츠 조각과 함께 사용하기 위한 AEM GraphQL API](/help/headless/graphql-api/content-fragments.md)

GraphQL 쿼리를 시작하고 이들 쿼리가 AEM 콘텐츠 조각과 함께 작동하는 방법을 알아보려면 몇 가지 실제 사례를 살펴보는 것이 도움이 됩니다.

도움이 필요하면 다음을 참조하십시오.

* [샘플 콘텐츠 조각 구조](#content-fragment-structure-graphql)

* 샘플 콘텐츠 조각 구조(콘텐츠 조각 모델 및 관련 콘텐츠 조각)를 기반으로 하는 몇 가지 [샘플 GraphQL 쿼리](#graphql-sample-queries)

>[!CONTEXTUALHELP]
>id="aemcloud_headless_graphql_sample"
>title="AEM을 통해 GraphQL을 사용하는 방법 알아보기 - 샘플 콘텐츠 및 쿼리"
>abstract="AEM으로 GraphQL을 사용하여 샘플 콘텐츠 및 쿼리 탐색을 통해 콘텐츠를 Headless 방식으로 제공하는 방법을 배웁니다."

## GraphQL - 샘플 콘텐츠 조각 구조를 사용하는 샘플 쿼리 {#graphql-sample-queries-sample-content-fragment-structure}

샘플 결과와 더불어 쿼리 만들기에 대한 설명은 이 샘플 쿼리를 참조하십시오.

>[!NOTE]
>
>인스턴스에 따라 쿼리를 제출하고 테스트하기 위해 [AEM GraphQL API에 포함되어 있는 GraphiQL 인터페이스](/help/headless/graphql-api/graphiql-ide.md)에 직접 액세스할 수 있습니다.
>
>다음 중 하나에서 쿼리 편집기에 액세스할 수 있습니다.
>
>* **도구** -> **일반** -> **GraphQL 쿼리 편집기**
>* 직접 (예: `http://localhost:4502/aem/graphiql.html`)

>[!NOTE]
>
>샘플 쿼리는 [GraphQL과 함께 사용하기 위한 샘플 콘텐츠 조각 구조](#content-fragment-structure-graphql)를 기반으로 합니다.

### 샘플 쿼리 - 사용 가능한 모든 스키마 및 데이터 형식 {#sample-all-schemes-datatypes}

사용 가능한 모든 스키마에 대한 모든 `types`가 반환됩니다.

**샘플 쿼리**

```graphql
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 모든 도시에 대한 모든 정보 {#sample-all-information-all-cities}

전 도시에 대한 모든 정보를 검색하려면 다음과 같은 기본적인 쿼리를 사용하면 됩니다.
**샘플 쿼리**

```graphql
{
  cityList {
    items
  }
}
```

실행되면 시스템은 모든 필드를 포함하도록 쿼리를 자동으로 확장합니다.

```graphql
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 모든 도시의 이름 {#sample-names-all-cities}

`city` 스키마에 있는 모든 항목의 `name`을 반환하는 간단한 쿼리입니다.

**샘플 쿼리**

```graphql
query {
  cityList {
    items {
      name
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 단일 특정 도시 조각 {#sample-single-specific-city-fragment}

저장소의 특정 위치에 있는 단일 조각 항목의 세부 정보를 반환하는 쿼리입니다.

**샘플 쿼리**

```graphql
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### 샘플 쿼리 - 이름이 붙은 변형이 있는 모든 도시 {#sample-cities-named-variation}

`city` Berlin에 대해 “Berlin Centre”(`berlin_centre`)라는 변형을 만드는 경우, 쿼리를 사용하여 변형의 세부 정보를 반환할 수 있습니다.

**샘플 쿼리**

```graphql
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 모든 도시의 이름 City Break로 태그됨 {#sample-names-all-cities-tagged-city-breaks}

다음 작업을 수행하는 경우:

* `Tourism`이라는 다양한 태그 생성: `Business`, `City Break`, `Holiday`
* 및 이를 다양한 `City` 인스턴스의 마스터 변형에 할당

그러면 쿼리를 사용하여 `city`스키마에서 City Break로 태그된 모든 항목에 대한 `name` 및 `tags`의 세부 정보를 반환할 수 있습니다.

**샘플 쿼리**

```xml
query {
  cityList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "tourism:city-break", _operator: CONTAINS}]}}
  ){
    items {
      name,
      _tags
    }
  }
}
```

**샘플 결과**:

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Berlin",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        },
        {
          "name": "Zurich",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 회사 CEO 및 직원의 전체 세부 정보 {#sample-full-details-company-ceos-employees}

중첩된 조각의 구조를 사용하여 이 쿼리는 회사 CEO와 모든 직원의 전체 세부 정보를 반환합니다.

**샘플 쿼리**

```graphql
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 이름이 “Jobs” 또는 “Smith”인 모든 사람 {#sample-all-persons-jobs-smith}

이름이 `Jobs` 또는 `Smith`인 모든 `persons`가 필터링되는 쿼리입니다.

**샘플 쿼리**

```graphql
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 이름이 “Jobs”가 아닌 모든 사람 {#sample-all-persons-not-jobs}

이름이 `Jobs` 또는 `Smith`인 모든 `persons`가 필터링되는 쿼리입니다.

**샘플 쿼리**

```graphql
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - `_path`가 특정 접두사로 시작하는 모든 모험 {#sample-wknd-all-adventures-cycling-path-filter}

`_path`가 특정 접두사로 시작하는 `adventures`(`/content/dam/wknd/en/adventures/cycling`).

**샘플 쿼리**

```graphql
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 독일 또는 스위스에 위치한 인구 400,000~999,999의 모든 도시 {#sample-all-cities-d-ch-population}

여기에서는 필드를 조합하여 필터링됩니다. An `AND`(묵시적)는 `population`범위를 선택하는 데 사용되며, `OR`(명시적)는 필요한 도시를 선택하는 데 사용됩니다.

**샘플 쿼리**

```graphql
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 대소문자에 관계없이 이름에 SAN이 있는 모든 도시 {#sample-all-cities-san-ignore-case}

이 쿼리는 대소문자에 관계없이 이름에 `SAN`이 있는 모든 도시에 대한 정보를 얻습니다.

**샘플 쿼리**

```graphql
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 적어도 한 번은 발생해야 하는 항목이 있는 배열 필터링 {#sample-array-item-occur-at-least-once}

이 쿼리는 적어도 한 번은 발생해야 하는 항목(`city:na`)이 있는 배열을 필터링합니다.

**샘플 쿼리**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### 샘플 쿼리 - 정확한 배열 값 필터링 {#sample-array-exact-value}

이 쿼리는 정확한 배열 값을 필터링합니다.

**샘플 쿼리**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### 중첩된 콘텐츠 조각에 대한 샘플 쿼리 - 이름이 “Smith”인 직원이 한 명 이상 있는 모든 회사 {#sample-companies-employee-smith}

이 쿼리는 `name`이 “Smith”인 모든 `person`에 대한 필터링을 보여 주고, 두 가지 중첩된 조각(`company` 및 `employee`)에서 정보를 반환합니다.

**샘플 쿼리**

```graphql
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### 중첩된 콘텐츠 조각에 대한 샘플 쿼리 - 모든 직원이 “Gamestar“ 상을 수상한 모든 회사 {#sample-all-companies-employee-gamestar-award}

이 쿼리는 세 가지 중첩된 조각(`company`, `employee`, `award`)에 대한 필터링을 보여 줍니다.

**샘플 쿼리**

```graphql
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
        awards {
          id
          title
        }
      }
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### 메타데이터에 대한 샘플 쿼리 - GB라는 제목의 상에 대한 메타데이터 나열 {#sample-metadata-awards-gb}

이 쿼리는 세 가지 중첩된 조각(`company`, `employee`, `award`)에 대한 필터링을 보여 줍니다.

**샘플 쿼리**

```graphql
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**샘플 결과**:

```json
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## WKND 프로젝트를 사용하는 샘플 쿼리 {#sample-queries-using-wknd-project}

이러한 샘플 쿼리는 WKND 프로젝트를 기반으로 합니다. 다음 항목이 있습니다.

* 콘텐츠 조각 모델은 다음에서 사용할 수 있습니다.
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* 콘텐츠 조각(및 기타 콘텐츠)은 다음에서 사용할 수 있습니다.
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
  `http://<hostname>:<port>/assets.html/content/dam/wknd-shared/en`

>[!NOTE]
>
>결과가 광범위해질 수 있으므로 여기에서 재현하지는 않습니다.

### 지정된 속성을 가진 특정 모델의 모든 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-all-model-properties}

이 샘플 쿼리는 다음에 대한 정보를 얻습니다.

* `article` 유형의 모든 콘텐츠 조각
* `_path` 및 `authorFragment`의 속성

**샘플 쿼리**

```graphql
{
  articleList {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
    }
 }
}
```

### 메타데이터에 대한 샘플 쿼리 {#sample-wknd-metadata}

이 쿼리는 다음에 대한 정보를 얻습니다.

* `adventure` 유형의 모든 콘텐츠 조각
* 메타데이터

**샘플 쿼리**

```graphql
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### 주어진 모델의 단일 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-single-content-fragment-of-given-model}

이 샘플 쿼리는 다음에 대한 정보를 얻습니다.

* 특정 경로에서 `article` 유형의 단일 콘텐츠 조각
   * 해당 조각 안에 있는 모든 형식의 콘텐츠:
      * HTML
      * Markdown
      * 일반 텍스트
      * JSON

**샘플 쿼리**

```graphql
{
  articleByPath(_path: "/content/dam/wknd-shared/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        authorFragment {
          _path
          firstName
          lastName
          birthDay
        }
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### 모델의 콘텐츠 조각 모델에 대한 샘플 쿼리 {#sample-wknd-content-fragment-model-from-model}

이 샘플 쿼리는 다음에 대한 정보를 얻습니다.

* 단일 콘텐츠 조각
   * 기본 콘텐츠 조각 모델의 세부 정보

**샘플 쿼리**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### 중첩된 콘텐츠 조각에 대한 샘플 쿼리 - 단일 모델 유형{#sample-wknd-nested-fragment-single-model}

이 쿼리는 다음에 대한 정보를 얻습니다.

* 특정 경로에서 `article` 유형의 단일 콘텐츠 조각
   * 해당 조각 안에 있는 참조된(중첩된) 조각의 경로 및 작성자

>[!NOTE]
>
>`referencearticle` 필드에는 `fragment-reference` 데이터 형식이 있습니다.

**샘플 쿼리**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### 중첩된 콘텐츠 조각에 대한 샘플 쿼리 - 복수 모델 유형{#sample-wknd-nested-fragment-multiple-model}

#### 단일 참조된 모델 유형

이 쿼리는 다음에 대한 정보를 얻습니다.

* `bookmark` 유형의 복수 콘텐츠 조각
   * 특정 모델 유형 `Article`의 다른 조각에 대한 조각 참조 포함

>[!NOTE]
>
>`fragments` 필드에는 `fragment-reference` 데이터 유형이 있고, `Article` 모델이 선택됩니다. 쿼리는 `fragments`의 배열로 `[Article]` 제공.

```graphql
{
  bookmarkList {
    items {
        fragments {
          _path
          author
        }
     }
  }
}
```

#### 다중 참조된 모델 유형

이 쿼리는 다음에 대한 정보를 얻습니다.

* `bookmark` 유형의 복수 콘텐츠 조각
   * 특정 모델 유형 `Article` 및 `Adventure`의 다른 조각에 대한 조각 참조 포함

>[!NOTE]
>
>`fragments` 필드에는 `fragment-reference` 데이터 유형이 있고, `Article`, `Adventure` 모델이 선택됩니다. 쿼리는 공용 구조체 형식으로 참조되지 않은 `[AllFragmentModels]`의 배열로 `fragments`을 제공합니다.

```graphql
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### 콘텐츠 참조가 있는 특정 모델의 콘텐츠 조각에 대한 샘플 쿼리{#sample-wknd-fragment-specific-model-content-reference}

이 쿼리에는 다음과 같은 두 가지 버전이 있습니다.

1. 모든 콘텐츠 참조 반환.
1. `attachments` 유형의 특정 콘텐츠 참조 반환.

이들 쿼리는 다음에 대한 정보를 얻습니다.

* `bookmark` 유형의 복수 콘텐츠 조각
   * 다른 조각에 대한 콘텐츠 참조 포함

#### 프리페치된 참조가 포함된 복수 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-multiple-fragments-prefetched-references}

다음 쿼리는 `_references`를 사용하여 모든 콘텐츠 참조를 반환합니다.

<!-- need replacement query -->

```graphql
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### 첨부 파일이 포함된 복수 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-multiple-fragments-attachments}

다음 쿼리는 `content-reference` 유형의 특정 필드(하위 그룹)인 모든 `attachments`를 반환합니다.

>[!NOTE]
>
>`attachments` 필드에는 `content-reference` 데이터 형식이 있고, 다양한 형태가 선택되어 있습니다.

<!-- need replacement query -->

```graphql
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### RTE 인라인 참조가 포함된 단일 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-single-fragment-rte-inline-reference}

이 쿼리는 다음에 대한 정보를 얻습니다.

* 특정 경로에서 `bookmark` 유형의 단일 콘텐츠 조각
   * 그 안에 있는 RTE 인라인 참조

>[!NOTE]
>
>RTE 인라인 참조는 `_references`에서 하이드레이션됩니다.

<!-- need replacement query -->

**샘플 쿼리**

```graphql
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### 주어진 모델의 단일 콘텐츠 조각 변형에 대한 샘플 쿼리 {#sample-wknd-single-fragment-given-model}

이 쿼리는 다음에 대한 정보를 얻습니다.

* 특정 경로에서 `author` 유형의 단일 콘텐츠 조각
   * 해당 조각 안에 있는 변형: `another`과 관련된 데이터

**샘플 쿼리**

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo", variation: "another") {
    item {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### 주어진 모델의 복수 콘텐츠 조각의 이름이 붙은 변형에 대한 샘플 쿼리 {#sample-wknd-variation-multiple-fragment-given-model}

이 쿼리는 다음에 대한 정보를 얻습니다.

* 특정 변형: `another`이 포함된 `author` 유형의 콘텐츠 조각

>[!NOTE]
>
>이 쿼리는 지정된 이름의 [변형](/help/headless/graphql-api/content-fragments.md#variations)이 없는 콘텐츠 조각에 대한 폴백을 보여 줍니다.

**샘플 쿼리**

```graphql
{
  authorList(variation: "another") {
    items {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### 주어진 모델의 복수 콘텐츠 조각과 변형에 대한 샘플 쿼리 {#sample-wknd-multiple-fragment-variations-given-model}

이 쿼리는 다음에 대한 정보를 얻습니다.

* `article` 유형과 모든 변형의 콘텐츠 조각

**샘플 쿼리**

```xml
query {
  articleList(
    includeVariations: true  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### 특정 태그가 첨부된 주어진 모델의 콘텐츠 조각 변형에 대한 샘플 쿼리{#sample-wknd-fragment-variations-given-model-specific-tag}

이 쿼리는 다음에 대한 정보를 얻습니다.

* 태그가 있는 하나 이상의 변형이 포함된 `article` 유형의 콘텐츠 조각 `WKND : Activity / Hiking`

**샘플 쿼리**

```xml
{
  articleList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "wknd:activity/hiking", _operator: CONTAINS}]}}
  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### 주어진 로케일의 복수 콘텐츠 조각에 대한 샘플 쿼리 {#sample-wknd-multiple-fragments-given-locale}

이 쿼리는 다음에 대한 정보를 얻습니다.

* `fr` 로케일 안에 있는 `article` 유형의 콘텐츠 조각

**샘플 쿼리**

```graphql
{ 
  articleList(_locale: "fr") {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### 오프셋 및 제한을 사용하는 샘플 목록 쿼리 {#sample-list-offset-limit}

이 쿼리는 다음에 대한 정보를 얻습니다.

* *전체* 결과 목록의 다섯 번째 문서부터 시작하여 최대 5개의 문서를 포함하는 결과 페이지

**샘플 쿼리**

```graphql
{
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      _path
    }
  }
}
```

### 첫 번째 및 그 다음 페이지를 사용하는 샘플 페이지 매김 쿼리  {#sample-pagination-first-after}

이 쿼리는 다음에 대한 정보를 얻습니다.

* *전체* 결과 목록의 주어진 커서 항목부터 시작하여 최대 5개의 모험을 포함하는 결과 페이지

**샘플 쿼리**

```graphql
{
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

### _태그 ID별로 필터링하고 변형을 제외하는 샘플 쿼리 {#sample-filtering-tag-not-variations}

이 쿼리는 다음에 대한 정보를 얻습니다.

* `vehicle` 유형의 콘텐츠 조각 - 태그가 있고 `big-block`
* 변형 제외

**샘플 쿼리**

```graphql
query {
  vehicleList(
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    items {
      _variation
      _path
      type
      name
      model
      fuel
      _tags
    }
  }
} 
```

### _태그 ID별로 필터링하고 변형을 포함하는 샘플 쿼리 {#sample-filtering-tag-with-variations}

이 쿼리는 다음에 대한 정보를 얻습니다.

* `vehicle` 유형의 콘텐츠 조각 - 태그가 있고 `big-block`
* 변형 포함

**샘플 쿼리**

```graphql
{
  enginePaginated(after: "SjkKNmVkODFmMGQtNTQyYy00NmQ4LTljMzktMjhlNzQwZTY1YWI2Cmo5", first: 9 ,includeVariations:true, sort: "name",
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    edges{
    node {
        _variation
        _path
        name
        type
        size
        _tags
        _metadata {
          stringArrayMetadata {
            name
            value
          }
        }
    }
      cursor
    }
  }
} 
```

## 샘플 콘텐츠 조각 구조 (GraphQL과 함께 사용) {#content-fragment-structure-graphql}

샘플 쿼리는 다음 구조를 기반으로 합니다. 사용:

* 하나 이상의 [샘플 콘텐츠 조각 구조 모델](#sample-content-fragment-models-schemas) - GraphQL 스키마의 기반 형성

* 위 모델을 기반으로 하는 [샘플 콘텐츠 모델](#sample-content-fragments)

### 샘플 콘텐츠 조각 모델 (스키마) {#sample-content-fragment-models-schemas}

샘플 쿼리의 경우, 다음 콘텐츠 모델 및 해당 상호 관계를 사용합니다(참조 ->).

* [회사](#model-company)
-> [사람](#model-person)
    -> [상](#model-award)

* [도시](#model-city)

#### 회사 {#model-company}

회사를 정의하는 기본 필드는 다음과 같습니다.

| 필드 이름 | 데이터 형식 | 참조 |
|--- |--- |--- |
| 회사 이름 | 한 줄 텍스트 | |
| CEO | 조각 참조 (단일) | [개인](#model-person) |
| 직원 | 조각 참조 (다중 필드) | [개인](#model-person) |

#### 개인 {#model-person}

직원일 수도 있는 사람을 정의하는 필드입니다.

| 필드 이름 | 데이터 형식 | 참조 |
|--- |--- |--- |
| 이름 | 한 줄 텍스트 | |
| 이름 | 한 줄 텍스트 | |
| 상 | 조각 참조 (다중 필드) | [상](#model-award) |

#### 상 {#model-award}

상을 정의하는 필드는 다음과 같습니다.

| 필드 이름 | 데이터 형식 | 참조 |
|--- |--- |--- |
| 단축키/ID | 한 줄 텍스트 | |
| 제목 | 한 줄 텍스트 | |

#### 도시 {#model-city}

도시를 정의하는 필드는 다음과 같습니다.

| 필드 이름 | 데이터 형식 | 참조 |
|--- |--- |--- |
| 이름 | 한 줄 텍스트 | |
| 국가 | 한 줄 텍스트 | |
| 인구 | 숫자 | |
| 범주 | 태그 | |

### 샘플 콘텐츠 조각 {#sample-content-fragments}

다음 조각이 적절한 모델에 사용됩니다.

#### 회사 {#fragment-company}

| 회사 이름 | CEO | 직원 |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
| Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### 개인 {#fragment-person}

| 이름 | 이름 | 상 |
|--- |--- |--- |
| Lincoln | Abe | |
| Smith | Adam | |
| Slade | Cutter | Gameblitz<br>Gamestar |
| Marsh | Duke | |
| Smith | Joe | |
| Croft | Lara | Gamestar |
| Caulfield | Max | Gameblitz |
| Jobs | Steve | |

#### 상 {#fragment-award}

| 단축키/ID | 제목 |
|--- |--- |
| GB | Gameblitz |
| GS | Gamestar |
| OSC | Oscar |

#### 도시 {#fragment-city}

| 이름 | 국가 | 인구 | 범주 |
|--- |--- |--- |--- |
| 바젤 | 스위스 | 172258 | city:emea |
| 베를린 | 독일 | 3669491 | city:capital<br>city:emea |
| 부쿠레슈티 | 루마니아 | 1821000 | city:capital<br>city:emea |
| 샌프란시스코 | 미국 | 883306 | city:beach<br>city:na |
| 새너제이 | 미국 | 102635 | city:na |
| 슈투트가르트 | 독일 | 634830 | city:emea |
| 취리히 | 스위스 | 415367 | city:capital<br>city:emea |
