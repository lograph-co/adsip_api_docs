# AdSiP API Documents

## what

AdSiP OEM用のAPIドキュメントをMarkdownでHostするもの。どこかにDeployしてお使いください。

## requirements

* node/npm
* [docsify](https://yamachan.github.io/docsify-docs-ja/#/)
    * `npm i docsify-cli -g`

docsifyについて詳しくは[こちら](https://yamachan.github.io/docsify-docs-ja/#/)。

## how

### serve

このリポジトリをClone後、cdして以下コマンド実行

```shell
docsify serve ./docs
```

### write

`./docs` ディレクトリにあるMarkdownファイルを修正してください。また、 `README.md` ファイルが index となります。
