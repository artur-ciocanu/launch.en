---
title: Data elements endpoint
description: Learn how to make calls to the /data_elements endpoint in the Reactor API.
---
# Data elements endpoint

A data element functions as a variable which points to an important piece of data within your application. Data elements are used within [rules](./rules.md) and [extension](./extensions.md) configurations. When a rule is triggered at runtime in a browser or an application, the value of the data element is resolved and used within the rule. Data elements function the same for extension configurations.

Using several data elements together results in a data dictionary or data map. This dictionary represents the data that Adobe Experience Platform knows about and can make use of.

A data element belongs to exactly one [property](./properties.md). A property can have many data elements.

For more general information on data elements and their use in tags, see the [data elements guide](../../launch-reference/managing-resources/data-elements.md) in the UI documentation.

## Getting started

The endpoint used in this guide is part of the Reactor API. Before continuing, please review the [getting started guide](../getting-started.md) for links to related documentation, a guide to reading the sample API calls in this document, and important information regarding required headers.

## Retrieve a list of data elements {#list}

**API format**

```http
GET /properties/{PROPERTY_ID}/data_elements
```

| Parameter | Description |
| --- | --- |
| `PROPERTY_ID` | The `id` of the [property](./properties.md) that owns the data elements. |

**Request**

```shell
curl -X GET \
  https://reactor.adobe.io/properties/PR97d92a379a5f48758947cdf44f607a0d/data_elements \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1'
```

**Response**

A successful response returns a list of data elements for the specified property.

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
        "name": "My Data Element 2020-12-14 17:36:08 +0000",
        "published": false,
        "published_at": null,
        "revision_number": 0,
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
        "latest_revision_number": 0
      }
    }
  ],
  "meta": {
    "pagination": {
      "current_page": 1,
      "next_page": null,
      "prev_page": null,
      "total_pages": 1,
      "total_count": 1
    }
  }
}
```

## Look up a data element {#lookup}

You can look up a data element by providing its ID in the path of a GET request.

>[!NOTE]
>
>When data elements are deleted, they are marked as deleted but are not actually removed from system. Therefore, it is possible to look up a deleted data element. Deleted data elements can be identified by the presence of a `data.meta.deleted_at` attribute.

**API format**

```http
GET /data_elements/{DATA_ELEMENT_ID}
```

| Parameter | Description |
| --- | --- |
| `DATA_ELEMENT_ID` | The `id` of the data element that you want to look up. |

**Request**

```shell
curl -X GET \
  https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833 \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1'
```

**Response**

A successful response returns the details of the data element.

```json
{
  "data": {
    "id": "DE8097636264104451ac3a18c95d5ff833",
    "type": "data_elements",
    "attributes": {
      "created_at": "2020-12-14T17:35:54.956Z",
      "deleted_at": null,
      "dirty": true,
      "enabled": true,
      "name": "My Data Element 2020-12-14 17:35:54 +0000",
      "published": false,
      "published_at": null,
      "revision_number": 0,
      "updated_at": "2020-12-14T17:35:54.956Z",
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
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/libraries"
        }
      },
      "revisions": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/revisions"
        }
      },
      "notes": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/notes"
        }
      },
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/property"
        },
        "data": {
          "id": "PRa5621686159f44c880557e12af412a95",
          "type": "properties"
        }
      },
      "origin": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/origin"
        },
        "data": {
          "id": "DE8097636264104451ac3a18c95d5ff833",
          "type": "data_elements"
        }
      },
      "extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/extension"
        },
        "data": {
          "id": "EX085a465793b54be39b5408d13b50b46e",
          "type": "extensions"
        }
      },
      "updated_with_extension_package": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/updated_with_extension_package"
        },
        "data": {
          "id": "EP75db2452065b44e2b8a38ca883ce369a",
          "type": "extension_packages"
        }
      },
      "updated_with_extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833/updated_with_extension"
        },
        "data": {
          "id": "EXf9a32699efde42e9b9410b43bd660848",
          "type": "extensions"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PRa5621686159f44c880557e12af412a95",
      "origin": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833",
      "self": "https://reactor.adobe.io/data_elements/DE8097636264104451ac3a18c95d5ff833",
      "extension": "https://reactor.adobe.io/extensions/EX085a465793b54be39b5408d13b50b46e"
    },
    "meta": {
      "latest_revision_number": 0
    }
  }
}
```

## Create a data element {#create}

You can create a new data element by making a POST request.

**API format**

```http
POST /properties/{PROPERTY_ID}/data_elements
```

| Parameter | Description |
| --- | --- |
| `PROPERTY_ID` | The `id` of the [property](./properties.md) that you are defining the data element under. |

**Request**

The following request creates a new data element for the specified property. The call also associates the data element with an existing extension through the `relationship` property. See the guide on [relationships](../guides/relationships.md) for more information.

```shell
curl -X POST \
  https://reactor.adobe.io/properties/PR97d92a379a5f48758947cdf44f607a0d/data_elements \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Content-Type: application/json' \
  -d '{
        "data": {
          "attributes": {
            "name": "My Data Element 2020-12-14 17:33:21 +0000",
            "delegate_descriptor_id": "kessel-test::dataElements::dom-attribute",
            "settings": "{\"elementSelector\":\".target-element\",\"elementProperty\":\"html\"}",
            "default_value": "general_label",
            "enabled": true,
            "force_lower_case": true,
            "clean_text": true,
          },
          "relationships": {
            "extension": {
              "data": {
                "id": "EX28788723a8e24a2f927fce1b55eb7ffc",
                "type": "extensions"
              }
            }
          },
          "type": "data_elements"
        }
      }'
```

| Property | Description |
| --- | --- |
| `attributes.name` | **(Required)** A human-readable name for the data element. |
| `attributes.delegate_descriptor_id` | **(Required)** A formatted string that associates the data element with an extension package. All data elements must be associated with an extension package when they are first created, as each extension package defines the compatible types for its delegate data elements, as well as their intended behavior. See the guide on [delegate descriptor IDs](../guides/delegate-descriptor-ids.md) for more information. |
| `attributes.settings` | A settings JSON object represented as a string. |
| `attributes.default_value` | A default value to return if the data element evaluates to `undefined`. |
| `attributes.enabled` | A boolean value indicating whether the data element is enabled. |
| `attributes.force_lower_case` | A boolean value indicating whether the data element value should be converted to lowercase before being stored. |
| `attributes.clean_text` | A boolean value indicating whether leading and trailing whitespace should be removed from the data element value before being stored. |
| `id` | The `id` of the data element you want to update. This should match the `{DATA_ELEMENT_ID}` value provided in the request path. |
| `type` | The type of resource being updated. For this endpoint, the value must be `data_elements`. |

**Response**

A successful response return the details of the newly created data element.

```json
{
  "data": {
    "id": "DE8667bc64ceba4b599e8458ea4ab58b8f",
    "type": "data_elements",
    "attributes": {
      "created_at": "2020-12-14T17:33:21.774Z",
      "deleted_at": null,
      "dirty": true,
      "enabled": true,
      "name": "My Data Element 2020-12-14 17:33:21 +0000",
      "published": false,
      "published_at": null,
      "revision_number": 0,
      "updated_at": "2020-12-14T17:33:21.774Z",
      "clean_text": false,
      "default_value": null,
      "delegate_descriptor_id": "kessel-test::dataElements::dom-attribute",
      "force_lower_case": false,
      "review_status": "unsubmitted",
      "storage_duration": null,
      "settings": "{\"elementSelector\":\".target-element\",\"elementProperty\":\"html\"}"
    },
    "relationships": {
      "libraries": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/libraries"
        }
      },
      "revisions": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/revisions"
        }
      },
      "notes": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/notes"
        }
      },
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/property"
        },
        "data": {
          "id": "PR05ad70a8078f44c1a229ecf0da2802f2",
          "type": "properties"
        }
      },
      "origin": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/origin"
        },
        "data": {
          "id": "DE8667bc64ceba4b599e8458ea4ab58b8f",
          "type": "data_elements"
        }
      },
      "extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/extension"
        },
        "data": {
          "id": "EX28788723a8e24a2f927fce1b55eb7ffc",
          "type": "extensions"
        }
      },
      "updated_with_extension_package": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/updated_with_extension_package"
        },
        "data": {
          "id": "EP75db2452065b44e2b8a38ca883ce369a",
          "type": "extension_packages"
        }
      },
      "updated_with_extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f/updated_with_extension"
        },
        "data": {
          "id": "EXd6bf04b143e64fe0ae7efe55a6655fa9",
          "type": "extensions"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PR05ad70a8078f44c1a229ecf0da2802f2",
      "origin": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f",
      "self": "https://reactor.adobe.io/data_elements/DE8667bc64ceba4b599e8458ea4ab58b8f",
      "extension": "https://reactor.adobe.io/extensions/EX28788723a8e24a2f927fce1b55eb7ffc"
    },
    "meta": {
      "latest_revision_number": 0
    }
  }
}
```

## Update a data element {#update}

You can update a data element by including its ID in the path of a PATCH request.

**API format**

```http
PATCH /data_elements/{DATA_ELEMENT_ID}
```

| Parameter | Description |
| --- | --- |
| `DATA_ELEMENT_ID` | The `id` of the data element that you want to update. |

**Request**

The following request updates the `name` for an existing data element.

```shell
curl -X PUT \
  https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Content-Type: application/json' \
  -d '{
        "data": {
          "attributes": {
            "name": "New Data Element Name"
          },
          "id": "DE3fab176ccf8641838b3da59f716fc42b",
          "type": "data_elements"
        }
      }'
```

| Property | Description |
| --- | --- |
| `attributes` | An object whose properties represent the attributes to be updated for the data element. All data element attributes can be updated. See the example call for [creating a data element](#create) for a list of attributes and their use case. |
| `id` | The `id` of the data element you want to update. This should match the `{DATA_ELEMENT_ID}` value provided in the request path. |
| `type` | The type of resource being updated. For this endpoint, the value must be `data_elements`. |

**Response**

A successful response returns the details of the updated data element.

```json
{
  "data": {
    "id": "DE3fab176ccf8641838b3da59f716fc42b",
    "type": "data_elements",
    "attributes": {
      "created_at": "2020-12-14T17:36:24.552Z",
      "deleted_at": null,
      "dirty": true,
      "enabled": true,
      "name": "New Data Element Name",
      "published": false,
      "published_at": null,
      "revision_number": 0,
      "updated_at": "2020-12-14T17:36:25.578Z",
      "clean_text": false,
      "default_value": null,
      "delegate_descriptor_id": "kessel-test::dataElements::dom-attribute",
      "force_lower_case": false,
      "review_status": "unsubmitted",
      "storage_duration": null,
      "settings": "{\"elementSelector\":\".target-element-b\",\"elementProperty\":\"html\"}"
    },
    "relationships": {
      "libraries": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/libraries"
        }
      },
      "revisions": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/revisions"
        }
      },
      "notes": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/notes"
        }
      },
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/property"
        },
        "data": {
          "id": "PR85e261fb61ce44c9b2498807a6e6410b",
          "type": "properties"
        }
      },
      "origin": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/origin"
        },
        "data": {
          "id": "DE3fab176ccf8641838b3da59f716fc42b",
          "type": "data_elements"
        }
      },
      "extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/extension"
        },
        "data": {
          "id": "EX71f31a3eeec249dfb77fedd6c5ce6387",
          "type": "extensions"
        }
      },
      "updated_with_extension_package": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/updated_with_extension_package"
        },
        "data": {
          "id": "EP75db2452065b44e2b8a38ca883ce369a",
          "type": "extension_packages"
        }
      },
      "updated_with_extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/updated_with_extension"
        },
        "data": {
          "id": "EX1f4df32a850c48a4930fb3e1dfa83536",
          "type": "extensions"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PR85e261fb61ce44c9b2498807a6e6410b",
      "origin": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b",
      "self": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b",
      "extension": "https://reactor.adobe.io/extensions/EX71f31a3eeec249dfb77fedd6c5ce6387"
    },
    "meta": {
      "latest_revision_number": 0
    }
  }
}
```

## Revise data element {#revise}

When you revise a data element, a new revision of the data element is created with the current (head) revision. Each revision of a data element will have its own ID. The original data element may be discovered through an origin link.

You can revising a data element by supplying a `meta.action` property with a value of `revise` in the body of a PATCH request.

**API format**

```http
PATCH /data_elements/{DATA_ELEMENT_ID}
```

| Parameter | Description |
| --- | --- |
| `DATA_ELEMENT_ID` | The `id` of the data element that you want to revise. |

**Request**

```shell
curl -X PUT \
  https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Content-Type: application/json' \
  -d '{
        "data": {
          "attributes": {
            "name": "New Data Element Name"
          },
          "meta": {
            "action": "revise"
          },
          "id": "DE7d7284657ee540ee8f402277860e9f8a",
          "type": "data_elements"
        }
      }'
```

| Property | Description |
| --- | --- |
| `attributes` | An object whose properties represent the attributes to be updated for the data element. All data element attributes can be updated. See the example call for [creating a data element](#create) for a list of attributes and their use case. |
| `meta.action` | When included with a value of `revise`, this property indicates that a new revision should be created for the data element. |
| `id` | The `id` of the data element you want to revise. This should match the `{DATA_ELEMENT_ID}` value provided in the request path. |
| `type` | The type of resource being revised. For this endpoint, the value must be `data_elements`. |

**Response**

A successful response returns the details of the new revision data element, as indicated by the incremented `meta.latest_revision_number` attribute.

```json
{
  "data": {
    "id": "DE3fab176ccf8641838b3da59f716fc42b",
    "type": "data_elements",
    "attributes": {
      "created_at": "2020-12-14T17:36:24.552Z",
      "deleted_at": null,
      "dirty": true,
      "enabled": true,
      "name": "New Data Element Name",
      "published": false,
      "published_at": null,
      "revision_number": 0,
      "updated_at": "2020-12-14T17:36:25.578Z",
      "clean_text": false,
      "default_value": null,
      "delegate_descriptor_id": "kessel-test::dataElements::dom-attribute",
      "force_lower_case": false,
      "review_status": "unsubmitted",
      "storage_duration": null,
      "settings": "{\"elementSelector\":\".target-element-b\",\"elementProperty\":\"html\"}"
    },
    "relationships": {
      "libraries": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/libraries"
        }
      },
      "revisions": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/revisions"
        }
      },
      "notes": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/notes"
        }
      },
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/property"
        },
        "data": {
          "id": "PR85e261fb61ce44c9b2498807a6e6410b",
          "type": "properties"
        }
      },
      "origin": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/origin"
        },
        "data": {
          "id": "DE3fab176ccf8641838b3da59f716fc42b",
          "type": "data_elements"
        }
      },
      "extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/extension"
        },
        "data": {
          "id": "EX71f31a3eeec249dfb77fedd6c5ce6387",
          "type": "extensions"
        }
      },
      "updated_with_extension_package": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/updated_with_extension_package"
        },
        "data": {
          "id": "EP75db2452065b44e2b8a38ca883ce369a",
          "type": "extension_packages"
        }
      },
      "updated_with_extension": {
        "links": {
          "related": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b/updated_with_extension"
        },
        "data": {
          "id": "EX1f4df32a850c48a4930fb3e1dfa83536",
          "type": "extensions"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PR85e261fb61ce44c9b2498807a6e6410b",
      "origin": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b",
      "self": "https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b",
      "extension": "https://reactor.adobe.io/extensions/EX71f31a3eeec249dfb77fedd6c5ce6387"
    },
    "meta": {
      "latest_revision_number": 1
    }
  }
}
```

## Delete a data element

You can delete a data element by including its ID in the path of a DELETE request.

**API format**

```http
DELETE /data_elements/{DATA_ELEMENT_ID}
```

| Parameter | Description |
| --- | --- |
| `DATA_ELEMENT_ID` | The `id` of the data element that you want to delete. |

**Request**

```shell
curl -X DELETE \
  https://reactor.adobe.io/data_elements/DE3fab176ccf8641838b3da59f716fc42b \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}'
```

**Response**

A successful response returns HTTP status 204 (No Content) with no response body, indicating that the data element has been deleted.
