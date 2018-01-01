---
title: "Hugoでブログはじめました"
date: 2018-01-01T17:29:51+09:00
draft: true
toc: true
---

## はじめに

数年前まで積極的に読んだ本のレビューをtDiaryで構築した自分の日記サイトや[本が好き！](http://www.honzuki.jp/)を中心とした書評サイトに投稿していたのですが、忙しくなったこともあり、ずっと滞っていました。

昨年くらいから歴史の本を中心に読むようになり、自分の感想と本を選ぶ時に参考にさせていただいたエントリを記録しておきたいなと思いはじめましたので、新年ということでブログを新規蒔き直しで始めてみることにしました。

ブログツールですが、最初は「はてなあたりでいいかなー」と漠然と思っていたのですが、最近、goでコードを書く機会もありましたので、goで書かれた静的サイトジェネレータ、Hugoを使って作ってみることにしました。静的サイトになるので、独自ドメイン可でホスティングできる無料サービスも多いですし(本当であれば、またtDiaryの方で書けばいいのですが、正直、ちょっと自前でホストを管理するのが面倒になってしまったということもあります……)。

仕事で同様の静的サイトジェネレータ、middlemanを使っていることもあって、Hugoも同じようなものだろうと思っていたのですが、やはり色々と違うところがあって戸惑うことも多かったです。そこでブログ一発目のエントリとしてメモを残しておきます。

## Hugoで戸惑ったところ

### 設定がテーマ間で互換ではないところ

ブログツールなので、設定は共通でテーマを変えてば、まるっと見た目だけ変わるだけだろうと思っていたら、テーマを変更する度に設定をいじらなければならず、最初はちょっと大変でした。

たぶん、ここはgoにもう少し慣れていれば、なんとかなったのではないかとも思います。

## 参考にさせていただいた所

* [Hugo](https://gohugo.io/): 言うまでもなく、Hugoの本家。まず、`Getting Started`を読んでインストールなどをしました。
* [Robust](https://themes.gohugo.io/robust/): Hugoテーマ。色々なテーマを試してみた結果、日本語を使うことを折り込み済みのこちらのテーマに落ち着きました。
* [Hugoで静的サイトを作る(2) デザインの修正 - www.d4af.com](https://www.d4af.com/post/2017/10/hugo-static-site-2/#css%E3%82%92%E4%BF%AE%E6%AD%A3%E3%81%99%E3%82%8B): RobustのCSSカスタマイズをまるっとパクらせていただきました。Hugoテーマのカスタマイズについても参考にさせていただきました。
* [HugoでAmazonの商品を表示するShortcodeを作った - longkey1's blog](https://blog.longkey1.net/2017/10/01/hugo-amazon-shortcode/): Amazonの書影を貼りたかったので、こちらで紹介されているAmazon Product APIの問い合わせ結果をJSONで返してくれるProxy、[longkey1/amazon-product-json](https://gitlab.com/longkey1/amazon-product-json)にほんの少し手を入れて使いました(と言っても、ライブラリを入れ換えただけです)。
* [upamune/amazing](https://github.com/upamune/amazing): `amazon-product-json`で使われているAmazon Product API問い合わせgoライブラリの改良版です。ほんの少し手を入れて使いました。
* [【Hugo】Amazonアフィリエイト用のShortcodeを作った - SanRin舎](https://tmsanrinsha.net/post/2017/05/hugo-shortcode-amazon/): Amazon書影のshortcodeとcssをまるっとパクらさせていただきました。

## 成果物

* [poppen/amazon-product-json](https://github.com/poppen/amazon-product-json): 出版社なども取得できるようにしました。
* [poppen/amazing](https://github.com/poppen/amazing): 上記を実現するための改良ライブラリです。
* [poppen/blog](https://github.com/poppen/blog): このブログ一式です。

## まとめ

ということで、Hugoでブログをはじめられることができました。
参考にさせていただいたエントリ執筆者や開発者の方々に感謝いたします。
