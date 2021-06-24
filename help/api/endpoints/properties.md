---
title: Properties endpoint
description: Learn how to make calls to the /properties endpoint in the Reactor API.
---
# Properties endpoint

A property is a container construct that holds most of the other resources available within the Reactor API. You manage properties programmatically using the `/properties` endpoint.

In the resource hierarchy, a property is the owner of the following:

* [Builds](./builds.md)
* [Callbacks](./callbacks.md)
* [Data elements](./data-elements.md)
* [Environments](./environments.md)
* [Extensions](./extensions.md)
* [Hosts](./properties.md)
* [Libraries](./libraries.md)
* [Rule components](./rule-components.md)
* [Rules](./rules.md)

A property belongs to exactly one company. A company can have many properties.

For more general information about properties and their role in tag management, see the overview on [companies and properties](../../launch-reference/administration/companies-and-properties.md).

## Getting started

The endpoint used in this guide is part of the [Reactor API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/reactor.yaml). Before continuing, please review the [getting started guide](../getting-started.md) for important information regarding required headers and links to related documentation.

## Retrieve a list of properties {#list}

You can retrieve a list of properties for a property by including the property's ID in the path of a GET request.

**API format**

```http
GET /properties/{PROPERTY_ID}/properties
```

| Parameter | Description |
| --- | --- |
| `PROPERTY_ID` | The `id` of the property that owns the properties. |

{style="table-layout:auto"}

>[!NOTE]
>
>Using query parameters, listed properties can be filtered based on the following attributes:<ul><li>`created_at`</li><li>`name`</li><li>`type_of`</li><li>`updated_at`</li></ul>See the guide on [filtering responses](../guides/filtering.md) for more information.

**Request**

```shell
curl -X GET \
  https://reactor.adobe.io/properties/PRd428c2a25caa4b32af61495f5809b737/properties \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1'
```

**Response**

A successful response returns a list of properties for the specified property.

```json
{
  "data": [
    {
      "id": "HT405b8d9306004eb38106e66c8a4afc09",
      "type": "properties",
      "attributes": {
        "created_at": "2020-12-14T17:42:35.239Z",
        "server": null,
        "name": "Example Akamai Host",
        "path": null,
        "port": null,
        "status": "succeeded",
        "type_of": "akamai",
        "updated_at": "2020-12-14T17:42:35.239Z",
        "username": null
      },
      "relationships": {
        "property": {
          "links": {
            "related": "https://reactor.adobe.io/properties/HT405b8d9306004eb38106e66c8a4afc09/property"
          },
          "data": {
            "id": "PRd428c2a25caa4b32af61495f5809b737",
            "type": "properties"
          }
        }
      },
      "links": {
        "property": "https://reactor.adobe.io/properties/PRd428c2a25caa4b32af61495f5809b737",
        "self": "https://reactor.adobe.io/properties/HT405b8d9306004eb38106e66c8a4afc09"
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

## Look up a property {#lookup}

You can look up a property by providing its ID in the path of a GET request.

**API format**

```http
GET /properties/{HOST_ID}
```

| Parameter | Description |
| --- | --- |
| `HOST_ID` | The `id` of the property that you want to look up. |

{style="table-layout:auto"}

**Request**

```shell
curl -X GET \
  https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84 \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1'
```

**Response**

A successful response returns the details of the property.

```json
{
  "data": {
    "id": "HT5d90148e72224224aac9bc0b01498b84",
    "type": "properties",
    "attributes": {
      "created_at": "2020-12-14T17:42:25.353Z",
      "server": "https://server.example.com",
      "name": "Example Akamai Host",
      "path": "/akamai",
      "port": 8000,
      "status": "succeeded",
      "type_of": "akamai",
      "updated_at": "2020-12-14T17:42:25.353Z",
      "username": null
    },
    "relationships": {
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84/property"
        },
        "data": {
          "id": "PRd7cf174259f34057b5c435ef873a79bf",
          "type": "properties"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PRd7cf174259f34057b5c435ef873a79bf",
      "self": "https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84"
    }
  }
}
```

## Create a property {#create}

You can create a new property by making a POST request.

**API format**

```http
POST /properties/{PROPERTY_ID}/properties
```

| Parameter | Description |
| --- | --- |
| `PROPERTY_ID` | The `id` of the [property](./properties.md) that you are defining the property under. |

{style="table-layout:auto"}

**Request**

The following request creates a new property for the specified property. The call also associates the property with an existing extension through the `relationships` property. See the guide on [relationships](../guides/relationships.md) for more information.

```shell
curl -X POST \
  https://reactor.adobe.io/properties/PRb25a704c0b7c4562835ccdf96d3afd31/properties \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Content-Type: application/json' \
  -d '{
        "data": {
          "attributes": {
            "name": "Example SFTP Host",
            "type_of": "sftp",
            "username": "John Doe",
            "encrypted_private_key": "{PRIVATE_KEY}",
            "server": "https://example.com",
            "path": "assets",
            "port": 22
          },
          "type": "properties"
        }
      }'
```

| Property | Description |
| --- | --- |
| `attributes.name` | **(Required)** A human-readable name for the property. |
| `attributes.type_of` | **(Required)** The type of property. Can be one of two options: <ul><li>`akamai` for [Adobe-managed properties](../../launch-reference/publishing/properties/managed-by-adobe-property.md)</li><li>`sftp` for [SFTP properties](../../launch-reference/publishing/properties/sftp-property.md)</li></ul> |
| `attributes.encrypted_private_key` | An optional private key to be used for property authentication. |
| `attributes.path` | The path to append to the `server` URL. |
| `attributes.port` | An integer indicating the specific server port to be used. |
| `attributes.server` | The property URL for the server. |
| `attributes.username` | An optional user name for authentication. |
| `type` | The type of resource being updated. For this endpoint, the value must be `properties`. |

{style="table-layout:auto"}

**Response**

A successful response return the details of the newly created property.

```json
{
  "data": {
    "id": "HT69bfe634dead4a9a8c659f5d4d94cecd",
    "type": "properties",
    "attributes": {
      "created_at": "2020-12-14T17:42:07.033Z",
      "server": "//example.com",
      "name": "Example SFTP Host",
      "path": "assets",
      "port": 22,
      "status": "pending",
      "type_of": "sftp",
      "updated_at": "2020-12-14T17:42:07.033Z",
      "username": "John Doe"
    },
    "relationships": {
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/properties/HT69bfe634dead4a9a8c659f5d4d94cecd/property"
        },
        "data": {
          "id": "PRb25a704c0b7c4562835ccdf96d3afd31",
          "type": "properties"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PRb25a704c0b7c4562835ccdf96d3afd31",
      "self": "https://reactor.adobe.io/properties/HT69bfe634dead4a9a8c659f5d4d94cecd"
    }
  }
}
```

## Update a property {#update}

>[!NOTE]
>
>Only SFTP properties can be updated.

You can update a property by including its ID in the path of a PATCH request.

**API format**

```http
PATCH /properties/{HOST_ID}
```

| Parameter | Description |
| --- | --- |
| `HOST_ID` | The `id` of the property that you want to update. |

{style="table-layout:auto"}

**Request**

The following request updates the `name` for an existing property.

```shell
curl -X PUT \
  https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84 \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Content-Type: application/json' \
  -d '{
        "data": {
          "attributes": {
            "name": "New property Name"
          },
          "id": "HT5d90148e72224224aac9bc0b01498b84",
          "type": "properties"
        }
      }'
```

| Property | Description |
| --- | --- |
| `attributes` | An object whose properties represent the attributes to be updated for the property. The following attributes can be updated for a property: <ul><li>`encrypted_private_key`</li><li>`name`</li><li>`path`</li><li>`port`</li><li>`server`</li><li>`type_of`</li><li>`username`</li></ul>|
| `id` | The `id` of the property you want to update. This should match the `{HOST_ID}` value provided in the request path. |
| `type` | The type of resource being updated. For this endpoint, the value must be `properties`. |

{style="table-layout:auto"}

**Response**

A successful response returns the details of the updated property.

```json
{
  "data": {
    "id": "HTb14e136a6fe147459b298a4645d2a6f5",
    "type": "properties",
    "attributes": {
      "created_at": "2020-12-14T17:42:45.087Z",
      "server": null,
      "name": "My SFTP property",
      "path": null,
      "port": null,
      "status": "succeeded",
      "type_of": "sftp",
      "updated_at": "2020-12-14T17:42:45.696Z",
      "username": null
    },
    "relationships": {
      "property": {
        "links": {
          "related": "https://reactor.adobe.io/properties/HTb14e136a6fe147459b298a4645d2a6f5/property"
        },
        "data": {
          "id": "PR8f240526f7b54a4dbd46965e79519fde",
          "type": "properties"
        }
      }
    },
    "links": {
      "property": "https://reactor.adobe.io/properties/PR8f240526f7b54a4dbd46965e79519fde",
      "self": "https://reactor.adobe.io/properties/HTb14e136a6fe147459b298a4645d2a6f5"
    }
  }
}
```

## Delete a property

You can delete a property by including its ID in the path of a DELETE request.

**API format**

```http
DELETE /properties/{HOST_ID}
```

| Parameter | Description |
| --- | --- |
| `HOST_ID` | The `id` of the property that you want to delete. |

{style="table-layout:auto"}

**Request**

```shell
curl -X DELETE \
  https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84 \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}'
```

**Response**

A successful response returns HTTP status 204 (No Content) with no response body, indicating that the property has been deleted.

## Manage notes for a property {#notes}

Properties are "notable" resources, meaning you can create and retrieve text-based notes on each individual resource. See the [notes endpoint guide](./notes.md) for more information on how to manage notes for properties and other compatible resources.

## Retrieve related resources for a property {#related}

The following calls demonstrate how to retrieve the related resources for a property. When [looking up a property](#lookup), these relationships are listed under the `relationships` property.

See the [relationships guide](../guides/relationships.md) for more information on relationships in the Reactor API.

### Look up the related property for a property {#property}

You can look up the property that owns a property by appending `/property` to the path of a lookup request.

**API format**

```http
GET /properties/{HOST_ID}/property
```

| Parameter | Description |
| --- | --- |
| `{HOST_ID}` | The `id` of the property whose property you want to look up. |

{style="table-layout:auto"}

**Request**

```shell
curl -X GET \
  https://reactor.adobe.io/properties/HT5d90148e72224224aac9bc0b01498b84/property \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'Accept: application/vnd.api+json;revision=1'
```

**Response**

A successful response returns the details of the the specified property's property.

```json
{
  "data": {
    "id": "PRbdfaffb7bf374b87be50e672f0cf9309",
    "type": "properties",
    "attributes": {
      "created_at": "2020-12-14T17:52:05.900Z",
      "enabled": true,
      "name": "Kessel Example Property",
      "updated_at": "2020-12-14T17:52:05.900Z",
      "platform": "web",
      "development": false,
      "token": "47d65c7c98db",
      "domains": [
        "example.com"
      ],
      "undefined_vars_return_empty": false,
      "rule_component_sequencing_enabled": false
    },
    "relationships": {
      "company": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/company"
        },
        "data": {
          "id": "CO2bf094214ffd4785bb4bcf88c952a7c1",
          "type": "companies"
        }
      },
      "callbacks": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/callbacks"
        }
      },
      "properties": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/properties"
        }
      },
      "environments": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/environments"
        }
      },
      "libraries": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/libraries"
        }
      },
      "data_elements": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/data_elements"
        }
      },
      "extensions": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/extensions"
        }
      },
      "rules": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/rules"
        }
      },
      "notes": {
        "links": {
          "related": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/notes"
        }
      }
    },
    "links": {
      "company": "https://reactor.adobe.io/companies/CO2bf094214ffd4785bb4bcf88c952a7c1",
      "data_elements": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/data_elements",
      "environments": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/environments",
      "extensions": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/extensions",
      "rules": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309/rules",
      "self": "https://reactor.adobe.io/properties/PRbdfaffb7bf374b87be50e672f0cf9309"
    },
    "meta": {
      "rights": [
        "approve",
        "develop",
        "manage_environments",
        "manage_extensions",
        "publish"
      ]
    }
  }
}
```
