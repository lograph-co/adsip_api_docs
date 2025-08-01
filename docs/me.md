# `/me` - 自分自身の情報

### `GET`

自分自身の情報を返す

#### リクエストの JSON-Schema

```json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "jsonValidate/me/get.json",
	"title": "A schema for request body when request `GET /me`.",
	"oneOf": [
		{
			"type": "array"
		},
		{
			"type": "null"
		}
	]
}
```

#### レスポンスの JSON-Schema

```json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "jsonSchema/me/get.json",
	"type": "object",
	"title": "A schema for response body when request `GET /me`.",
	"properties": {
		"email": {
			"title": "E-mail address",
			"type": "string",
			"format": "email"
		},
		"label": {
			"title": "Display name",
			"type": "string"
		},
		"role": {
			"title": "Role",
			"type": "number",
			"enum": [
				2,
				4,
				8
			]
		},
		"createdAt": {
			"title": "Created datetime",
			"type": "string",
			"format": "date-time"
		},
		"_embedded": {
			"type": "object",
			"properties": {
				"accounts": {
					"title": "Collection of account",
					"type": "array",
					"items": {
						"type": "object",
						"properties": {
							"accountId": {
								"title": "Account ID",
								"type": "number"
							},
							"label": {
								"title": "Account name",
								"type": "string"
							},
							"ownerId": {
								"title": "Owner user ID",
								"type": "number"
							},
							"agencyId": {
								"title": "Agency account ID",
								"type": "number"
							},
							"isAgency": {
								"title": "Account is agency",
								"type": "boolean"
							},
							"createdAt": {
								"title": "Created datetime",
								"type": "string",
								"format": "date-time"
							}
						}
					}
				},
				"campaigns": {
					"type": "array",
					"title": "Collection of campaign",
					"items": {
						"type": "object",
						"properties": {
							"campaignId": {
								"title": "Campaign ID",
								"type": "number"
							},
							"accountId": {
								"title": "Account ID",
								"type": "number"
							},
							"label": {
								"title": "Campaign name",
								"type": "string"
							},
							"createdAt": {
								"title": "Created datetime",
								"type": "string",
								"format": "date-time"
							},
							"attributes": {
								"type": "array",
								"title": "Collection of attribute",
								"items": {
									"type": "object",
									"properties": {
										"name": {
											"title": "Attribute name",
											"type": "string"
										},
										"value": {
											"title": "JSON encoded value"
										}
									}
								}
							}
						}
					}
				}
			}
		}
	}
}
```
