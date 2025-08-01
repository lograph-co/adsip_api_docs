# AdSiP API Reference

## 概要

* AdSiPは複数のチャネルに点在している行動の相関を見出し、それらを一連の行動として再現します。
* AdSiP自体は Web API として実装されたヘッドレスシステムです。
* コンソールは別途（[https://console.adsip.net/](https://console.omni-databank.com/)）構築されています。

## 著作権・禁止事項

* 本ドキュメントで提供される全ての情報の著作権はフリービット株式会社に帰属しています。
* API 並びに本ドキュメントの内容は予告なく変更される場合があります。
* 本ドキュメントで提供される情報及び著作物の複製を禁止します。
* 本項の内容に同意しない場合、本ドキュメントを読むことを禁止します。

## Data structure

本 API は [Hypertext Application Language](https://tools.ietf.org/html/draft-kelly-json-hal-08) でフォーマットされた JSON をレスポンスボディとして返します。

## JSON-Schema

リソースに対して `OPTIONS` メソッドでリクエストすると、そのリソースで利用可能なメソッドとそのスキーマをレスポンスします。スキーマはレスポンスボディのデータ構造を示す [JSON Schema](http://json-schema.org/latest/json-schema-core.html) と、リクエスト時に受け付けるパラメータに対する [JSON Schema Validation](http://json-schema.org/latest/json-schema-validation.html) です。
また、リソースのレスポンスヘッダにも、[Link relation](https://tools.ietf.org/html/rfc8288) として上記 JSON-Schema を示す URI が含まれています。`rel=describedby` がレスポンスボディのデータ構造を示す JSON Schema を、`rel=validation` がリクエスト時に受け付けるパラメータに対する JSON Schema Validation をそれぞれ示しています。

## コレクション

データを取得する API が返すデータの最上位は原則としてコレクションです。コレクションは集計されたデータを内包し、集計のメタ情報を持っています。`count`, `total` という2つの属性を持ち、集計されたデータは `_embedded` 配下にその名前をキーとして内包しています。

## 認証

* `POST /authentications` に認証を要求すると [JSON Web Token](https://tools.ietf.org/html/rfc7519) に基づいて生成されたアクセストークンが返却されます。
* [OAuth 2.0 Bearer](https://tools.ietf.org/html/rfc6750) に基づきアクセストークンを含めてリクエストすると、リクエストに対する承認が行われます。
* 更に詳しい情報は `/authentications` に関するドキュメントを参照してください。

## Endpoint

`https://api.adsip.net/`

## 定義されているリソースの仕様

* [`/me` - 自分自身の情報](me.md)
* [`/authentications` - 認証](authentications.md)
* [`/serviceConsumers` - サービスコンシューマー](serviceConsumers.md)
* [`/users` - ユーザー](users.md)
* [`/accounts` - アカウント](accounts.md)
* [`/campaigns` - キャンペーン](campaigns.md)
* [`/observers` - 観測点](observers.md)
* [`/trackingNumbers` - 計測番号](trackingNumbers.md)
* [`/audiences/web` - ウェブチャネルの訪問者ログ](audiences-web.md)
* [`/behaviors/phone/calls` - 入電ログ](behaviors-phone-calls.md)
* [`/count/trackingSessions` - 計測セッション](count-trackingSessions.md)
