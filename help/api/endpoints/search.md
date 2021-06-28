---
title: Search endpoint
description: Learn how to make calls to the /search endpoint in the Reactor API.
---
# Search endpoint

The `/search` endpoint in the Reactor API provides a way to find resources matching desired criteria, expressed as a query.

The following API resource types are searchable, utilizing the same data structure as the resource-based documents returned across the API:

* `audit_events`
* `builds`
* `callbacks`
* `data_elements`
* `environments`
* `extension_packages`
* `extensions`
* `hosts`
* `libraries`
* `properties`
* `rule_components`
* `rules`

All queries are scoped to the your current company and accessible properties.

>[!IMPORTANT]
>
>The search functionality has the following caveats and exceptions:
>* meta is not searchable and not returned in search results.
>* Schema fields for extension package delegates (actions, conditions, etc.) are searchable as text, not as a nested data structure.
>* Range queries presently only support integers.

For more in-depth information on how to use this functionality, refer to the [searching guide](../guides/search.md).

## Getting started

The endpoint used in this guide is part of the [Reactor API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/reactor.yaml). Before continuing, please review the [getting started guide](../getting-started.md) for important information regarding required headers and links to related documentation.

## Retrieve a list of rules {#list}

You can retrieve a list of rules belonging to a property by including by making a GET request.

**API format**

```http
GET /properties/{PROPERTY_ID}/rules
```

| Parameter | Description |
| --- | --- |
| `PROPERTY_ID` | The `id` of the property whose components you want to list. |

{style="table-layout:auto"}

>[!NOTE]
>
>Using query parameters, listed rules can be filtered based on the following attributes:<ul><li>`created_at`</li><li>`dirty`</li><li>`enabled`</li><li>`name`</li><li>`origin_id`</li><li>`published`</li><li>`published_at`</li><li>`revision_number`</li><li>`updated_at`</li></ul>See the guide on [filtering responses](../guides/filtering.md) for more information.

**Request**

```shell
curl -X POST \
  https://reactor.adobe.io/search \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1' \
  -d '{
        "data" : {
          "from": 0,
          "size": 25,
          "query": {
            "attributes.name": {
              "value": "Performance"
            },
            "attributes.revision_number": {
              "range": {
                "lte": "2",
                "gt": "0"
              }
            }
          },
          "sort": [
            {
              "attributes.revision_number": "desc"
            }
          ],
          "resource_types": [
            "data_elements",
            "rule_components"
          ]
        }
      }'
```

| Property | Description |
| --- | --- |
| `from` | The number of results to offset the response by. |
| `size` | The maximum amount of results to return. Results cannot exceed 100 items. |
| `query` | An object that represents the search query. For each property in this object, the key must represent a field path to query by, and the value must be an object whose sub-properties determine what to query for.<br><br>For each field path, you can use the following sub-properties:<ul><li>`exists`: Returns true if the field exists in the resource.</li><li>`value`: Returns true if the field's value matches the value of this property.</li><li>`value_operator`: Boolean logic used to determine how a `value` query should be treated with other `value` queries under the `query` object. Allowed values are `AND` and `OR`. When excluded, `AND` logic is assumed.</li><li>`range` Returns true if the field's value falls within a specific numerical range. The range itself is determined by the following sub-properties:<ul><li>`gt`: Greater than the supplied value, non-inclusive.</li><li>`gte`: Greater than or equal to the supplied value.</li><li>`lt`: Less than the supplied value, non-inclusive.</li><li>`lte`: Less than or equal to the supplied value.</li></ul></li></ul> |
| `sort` | An array of objects, indicating the order in which to sort results. Each object must contain a single property: the key represents the field path to sort by, and the value represents the sort order (`asc` for ascending, `desc` for descending). |
| `resource_types` | An array of strings, indicating the specific resource types to search. |

**Response**

A successful response returns the results of the query.

```json
{
  "data": [
    {
      "id": "DE5d11b3ed301d4ce99b530a5121e392b2",
      "type": "data_elements",
      "attributes": {
        "created_at": "2020-12-14T17:36:09.045Z",
        "deleted_at": null,
        "dirty": true,
        "enabled": true,
        "name": "Performance Indicator",
        "published": false,
        "published_at": null,
        "revision_number": 1,
        "updated_at": "2020-12-14T17:36:09.045Z",
        "clean_text": false,
        "default_value": null,
        "delegate_descriptor_id": "kessel-test::dataElements::dom-attribute",
        "force_lower_case": false,
        "review_status": "unsubmitted",
        "storage_duration": null,
        "settings": "{\"elementProperty\":\"html\",\"elementSelector\":\".target-element\"}"
      },
      "relationships": {
        "libraries": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/libraries"
          }
        },
        "revisions": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/revisions"
          }
        },
        "notes": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/notes"
          }
        },
        "property": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/property"
          },
          "data": {
            "id": "PR97d92a379a5f48758947cdf44f607a0d",
            "type": "properties"
          }
        },
        "origin": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/origin"
          },
          "data": {
            "id": "DE5d11b3ed301d4ce99b530a5121e392b2",
            "type": "data_elements"
          }
        },
        "extension": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/extension"
          },
          "data": {
            "id": "EX0348d463358c4c89afe726245576f112",
            "type": "extensions"
          }
        },
        "updated_with_extension_package": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/updated_with_extension_package"
          },
          "data": {
            "id": "EP75db2452065b44e2b8a38ca883ce369a",
            "type": "extension_packages"
          }
        },
        "updated_with_extension": {
          "links": {
            "related": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2/updated_with_extension"
          },
          "data": {
            "id": "EX1cc78b39339242da82a0e0752fa53375",
            "type": "extensions"
          }
        }
      },
      "links": {
        "property": "https://reactor.adobe.io/properties/PR97d92a379a5f48758947cdf44f607a0d",
        "origin": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2",
        "self": "https://reactor.adobe.io/data_elements/DE5d11b3ed301d4ce99b530a5121e392b2",
        "extension": "https://reactor.adobe.io/extensions/EX0348d463358c4c89afe726245576f112"
      },
      "meta": {
        "latest_revision_number": 1
      }
    }
  ],
  "meta": {
    "total_hits": 1
  }
}
```
