# `/audiences/web` - ウェブチャネルの訪問者ログ

### `GET`

訪問者ログ

* 指定した `beginTimestamp` と `endTimestamp` の間に `campaignId` 上で観測された訪問者を返します。
* HTTPリクエストのヘッダに `Accept: text/csv` がある場合、レスポンスボディは CSV 形式になります。
* またその場合 `page` パラメータは無視されます。

#### リクエストの JSON-Schema

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "$id": "jsonValidate/audiences/get.json",
    "type": "object",
    "title": "A schema for request body when `GET /audiences`.",
    "required": [
        "campaignId",
        "beginTimestamp",
        "endTimestamp"
    ],
    "properties": {
        "campaignId": {
            "title": "Campaign ID",
            "oneOf": [
                {
                    "type": "string",
                    "pattern": "^[0-9]+"
                },
                {
                    "type": "integer"
                }
            ]
        },
        "beginTimestamp": {
            "title": "Timestamp of an extraction target scope begin date.",
            "oneOf": [
                {
                    "type": "string",
                    "pattern": "^[0-9]+"
                },
                {
                    "type": "integer"
                }
            ]
        },
        "endTimestamp": {
            "title": "Timestamp of an extraction target scope end date.",
            "oneOf": [
                {
                    "type": "string",
                    "pattern": "^[0-9]+"
                },
                {
                    "type": "integer"
                }
            ]
        },
        "page": {
            "title": "Number of page",
            "oneOf": [
                {
                    "type": "string",
                    "default": "1",
                    "pattern": "^[0-9]+"
                },
                {
                    "type": "null"
                },
                {
                    "type": "integer"
                }
            ]
        },
        "limit": {
            "title": "Number of contain in 1 page",
            "oneOf": [
                {
                    "type": "string",
                    "default": "100",
                    "pattern": "^[0-9]+"
                },
                {
                    "type": "null"
                },
                {
                    "type": "integer"
                }
            ]
        },
        "sort": {
            "title": "Sort order",
            "default": "desc",
            "oneOf": [
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
    "$id": "jsonSchema/audiences/web/get.json",
    "type": "object",
    "title": "A schema for response body when request `GET /audiences/web`.",
    "required": [
        "count",
        "total",
        "_embedded"
    ],
    "properties": {
        "count": {
            "title": "Number of audience in a response.",
            "type": "number"
        },
        "total": {
            "title": "Number of audience in a query.",
            "type": "number"
        },
        "_embedded": {
            "type": "object",
            "required": [
                "audiences"
            ],
            "properties": {
                "audiences": {
                    "title": "Audience collection",
                    "type": "array",
                    "items": {
                        "title": "Audience",
                        "type": "object",
                        "properties": {
                            "visitedAt": {
                                "title": "Visited datetime",
                                "type": "string",
                                "format": "date-time"
                            },
                            "audienceId": {
                                "title": "Audience ID",
                                "type": "string",
                                "pattern": "^[a-z0-9]{24}$"
                            },
                            "callId": {
                                "title": "Call ID",
                                "type": "string"
                            },
                            "history": {
                                "title": "Behavior history",
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "behaviorId": {
                                            "title": "Behavior ID",
                                            "type": "string",
                                            "pattern": "^[a-z0-9]{24}$"
                                        },
                                        "createdAt": {
                                            "title": "Created datetime",
                                            "type": "string",
                                            "format": "date-time"
                                        },
                                        "url": {
                                            "title": "URL",
                                            "type": "string"
                                        },
                                        "referrer": {
                                            "title": "Referrer",
                                            "anyOf": [
                                                {
                                                    "type": "string"
                                                },
                                                {
                                                    "type": "null"
                                                }
                                            ]
                                        }
                                    }
                                }
                            },
                            "media": {
                                "title": "Media type",
                                "description": "`utm_medium` in URL of a landing page.",
                                "anyOf": [
                                    {
                                        "type": "string",
                                        "examples": [
                                            "PPC"
                                        ]
                                    },
                                    {
                                        "type": "null"
                                    }
                                ]
                            },
                            "source": {
                                "title": "Source type",
                                "description": "`utm_source` in URL of a landing page.",
                                "anyOf": [
                                    {
                                        "type": "string",
                                        "examples": [
                                            "Google"
                                        ]
                                    },
                                    {
                                        "type": "null"
                                    }
                                ]
                            },
                            "keyword": {
                                "title": "Keyword",
                                "anyOf": [
                                    {
                                        "type": "string"
                                    },
                                    {
                                        "type": "null"
                                    }
                                ]
                            },
                            "webCv": {
                                "title": "Web conversion",
                                "type": "number"
                            },
                            "callCv": {
                                "title": "Call conversion",
                                "type": "number"
                            },
                            "stayDuration": {
                                "title": "Stay duration (second)",
                                "type": "number"
                            },
                            "callDuration": {
                                "title": "Call duration (second)",
                                "anyOf": [
                                    {
                                        "type": "number"
                                    },
                                    {
                                        "type": "null"
                                    }
                                ]
                            },
                            "callerPhoneNumber": {
                                "title": "Caller phone number",
                                "anyOf": [
                                    {
                                        "type": "string"
                                    },
                                    {
                                        "type": "null"
                                    }
                                ]
                            },
                            "matchType": {
                                "title": "Match type",
                                "type": [
                                    "null",
                                    "string"
                                ]
                            },
                            "referrerDomain": {
                                "title": "Domain of referrer",
                                "type": [
                                    "null",
                                    "string"
                                ]
                            }
                        }
                    }
                }
            }
        }
    }
}
```
