---
title: "HugoでFull Text RSSを有効化する"
date: 2018-01-02T22:48:03+09:00
tags: ["hugo"]
---

Hugoが生成するRSSは要約RSSですが、全文が含まれたFull Text RSSを有効化してみました。

RSSの仕様がよく分からず、少し試行錯誤しましたが、とりあえず出来たのでメモしておきます。

## Full Text RSS有効化の方法

まるっとサイト全部のRSSをFull Text化にする場合には、[このRSS template](https://github.com/poppen/blog/blob/master/layouts/_default/rss.xml)を`layouts/_default/rss.xml`として置くだけです。

RSSテンプレートを設置できるディレクトリは他にもありますので、詳しくは[Hugoのドキュメント](https://gohugo.io/templates/rss/)を参照してください。

## 迷ったところ

参考に日本語で書かれたブログのRSSをいくつか見てみたところ、`<description>`に全文を入れている場合がほとんどでした。

しかし、どうも`<description>`は短くするということが推奨されているぽいので、代わりに`<content:encoded>`を追加してそこに全文を入れることにしました。

`<description>>`の方でもいいようならば、今後変えようかと思います。

## 参考

* [Hugo | RSS Template](https://gohugo.io/templates/rss/): Hugoが生成するRSSカスタマイズの詳細
* [RSS(RDF Site Summary)によるサイト情報の要約と公開](https://www.kanzaki.com/docs/sw/rss.html#mod-content)
* [Why RSS Content Module is Popular - Including HTML Contents - RSS | MDN](https://developer.mozilla.org/en-US/docs/Web/RSS/Article/Why_RSS_Content_Module_is_Popular_-_Including_HTML_Contents)
