# AdSiP API Documents

## what

AdSiP OEM用のAPIドキュメントをMarkdownでHostするもの。どこかにDeployしてお使いください。

## requirements

* node/npm
* [docsify](https://yamachan.github.io/docsify-docs-ja/#/)
    * `npm i docsify-cli -g`

## how

### where

以下のような構造になっていますので `docs` ディレクトリ配下の `.md` ファイルを修正してください。

```
├── docs
│   ├── accounts .md
│   ├── audiences-web.md
│   ├── authentications.md
│   ├── behaviors-phone-calls.md
│   ├── campaigns.md
│   ├── count-trackingSessions.md
│   ├── index.html
│   ├── me.md
│   ├── observers.md
│   ├── README.md
│   ├── serviceConsumers.md
│   ├── trackingNumbers.md
│   └── users.md
└── README.md
```

### serve

このリポジトリをClone後、cdして以下コマンド実行

```shell
docsify serve docs
```

とすると `http://localhost:3000/` でプレビューできます。

### write

`docs` ディレクトリにあるMarkdownファイルを修正してください。また、 `README.md` ファイルが index となります。
