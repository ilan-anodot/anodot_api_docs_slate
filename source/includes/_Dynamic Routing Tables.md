# Dynamic Routing Tables

> End Point **/api/v2/dynamic-routing

Dynamic routing tables can be used in alerts to send alert triggers to specific email addresses according to a dimension value.

Use the dynamic routing end point to:

* Get the list of currently used tables in the account
* Get the content of a routing table
* Create a new routing table from a CSV file
* Update an existing table from a CSV file

Authentication type: [Access Token Authentication] (#access-tokens).

## GET Routing Tables

> Request Example: 

```shell
curl -X GET 'https://app.anodot.com/api/v2/dynamic-routing' \
-H 'Authorization: Bearer ${TOKEN}' \
-H 'Content-Type: application/json'
```

Get the list of routing tables in the account.
This request has no body

> Response Example:

```json
[
    {
        "id": "5faa7af2085f2bxxx1f41b99",
        "title": "dynamic routing demo 1.csv",
        "owner": "5f7033946b6a7exxxe3cf861",
        "creationTime": 1605008114,
        "editTime": null,
        "csv": "",
        "version": "1.0"
    },
    {
        "id": "5fa7ac804ef60dxxx10cac80",
        "title": "dynamic routing demo 1.csv",
        "owner": "5f917739c47f32b8cxxx44a9",
        "creationTime": 1604824192,
        "editTime": 1604902670,
        "csv": "",
        "version": "1.0"
    }
]
```

### Response Fields

The response is a list of the available routing tables used in the account</br>

Field | Type | Description / Example
-|-|-
id | String ($uuid) | The routing table uuid. Use this value to get information regarding a specific table.
title | String | The table name, this is the full name of the csv file that was used to create the table
owner | String ($uuid) | The id of The table owner in Anodot.
creationTime | epoch | Time the table was created in Anodot
editTime | epoch | Time the last update was done on the table in Anodot
csv | String | TBD
version | String | TBD

## GET routing table

> Request Example: 

```shell
curl -X GET 'https://app.anodot.com/api/v2/dynamic-routing/{id}/csv' \
-H 'Authorization: Bearer ${TOKEN}' \
-H 'Content-Type: application/x-www-form-urlencoded'
```

Get a single table based on its id.

### Request Arguments

Replace {id} with the requested table id you received from the [GET routing tables] (## GET Routing Tables) request.

> Response Example:

```json
[
    [ "US", "us_ae@myorg.com"],
    [ "UK", "uk_ae@myorg.com"]
]
```

### Response Fields

The routing table content.

Column 1 | Column 2
-|-
Dimension Value | Email destination
