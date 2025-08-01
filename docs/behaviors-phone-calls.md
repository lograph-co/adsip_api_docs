# `/behaviors/phone/calls` - 入電ログ

### `GET`

コールログ

* 指定した `beginTimestamp` と `endTimestamp` の間に `campaignId` 上で観測された入電を返します。
* HTTPリクエストのヘッダに `Accept: text/csv` がある場合、レスポンスボディは CSV 形式になります。
* またその場合 `page` パラメータは無視されます。

#### リクエストの JSON-Schema

```json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "jsonValidate/behaviors/phone/get.json",
	"type": "object",
	"title": "A schema for request parameters when `GET /behaviors/phone`.",
	"required": [
		"campaignId",
		"beginTimestamp",
		"endTimestamp"
	],
	"properties": {
		"campaignId": {
			"title": "Campaign ID",
			"type": "string",
			"pattern": "^[0-9]+"
		},
		"observersId": {
			"title": "Observer ID",
			"type": "string",
			"pattern": "^[0-9,]+"
		},
		"beginTimestamp": {
			"title": "Timestamp of an extraction target scope begin date.",
			"type": "string",
			"pattern": "^[0-9]+"
		},
		"endTimestamp": {
			"title": "Timestamp of an extraction target scope end date.",
			"type": "string",
			"pattern": "^[0-9]+"
		},
		"page": {
			"title": "Number of page",
			"anyOf": [
				{
					"type": "string",
					"default": "1",
					"pattern": "^[0-9]+"
				},
				{
					"type": "null"
				}
			]
		},
		"limit": {
			"title": "Number of contain in 1 page",
			"anyOf": [
				{
					"type": "string",
					"default": "100",
					"pattern": "^[0-9]+"
				},
				{
					"type": "null"
				}
			]
		},
		"sort": {
			"title": "Sort order",
			"default": "desc",
			"anyOf": [
				{
					"type": "string",
					"enum": [
						"desc",
						"asc"
					]
				},
				{
					"type": "null"
				}
			]
		},
		"sortBy": {
			"title": "Column name for sort",
			"default": "createdAt"
		}
	}
}
```

#### レスポンスの JSON-Schema

```json
{
	"$schema": "http://json-schema.org/draft-07/schema#",
	"$id": "jsonSchema/behaviors/phone/get.json",
	"type": "object",
	"title": "A schema for response body when request `GET /behaviors/phone/calls`.",
	"required": [
		"count",
		"total",
		"_embedded"
	],
	"properties": {
		"count": {
			"title": "Number of audiences in a response.",
			"type": "number"
		},
		"total": {
			"title": "Number of audiences in a query.",
			"type": "number"
		},
		"_embedded": {
			"type": "object",
			"properties": {
				"calls": {
					"type": "array",
					"items": {
						"type": "object"
					}
				}
			}
		}
	}
}
```
