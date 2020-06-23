---
title: "hugo-amazon-apiからRedisを使えるようにしました"
date: 2018-01-07T18:05:24+09:00
tags: ["hugo", "golang"]
---

## tl;dr

[hugo-amazon-api](https://github.com/upamune/hugo-amazon-api)からRedisを使えるようにしました。

<!--more-->

## README

https://github.com/poppen/hugo-amazon-api

Usage:

```shell
% go get github.com/poppen/hugo-amazon-api
% cd $GOPATH/src/github.com/poppen/hugo-amazon-api
% go build
% ./hugo-amazon-api -access YOUR_ACCESS_KEY -secret YOUR_SECRET_KEY -tag YOUR_TAG -redis-url REDIS_URL(ex. redis://localhost:6379)
```

## 読まなくてOKな経緯

このブログは[Netlify](https://www.netlify.com/)にホストしてあります。[^1]

Netlifyはとても高機能な上に無料で使えるという涙が出るほど素晴しいサービスなのですが、当然ながらAmazon Product Amazon APIへの問い合わせとJSONへ変換してくれるサーバはNetlifyからアクセスできる場所に置かなければいけません。色々考えた末、こちらは[Heroku Container Registry](https://devcenter.heroku.com/articles/container-registry-and-runtime)でDockerコンテナとして動かしてみることにしました。[^2]

今までのエントリではAmazonへのリンクを張っていなかったこともあり、[amazon-product-json](https://github.com/poppen/amazon-product-json)をローカルで使っていましたが、すべてTOMLファイルを経由して設定する仕様のため、[Twelve-Factor App](https://12factor.net/ja/)的に使いにくいのが難点です。

amazon-product-jsonに環境変数に読み込めるように手を入れようかとも考えましたが、ググって見つけた[hugo-amazon-api](https://github.com/upamune/hugo-amazon-api)の方がDockerで動かすには楽そうなので、こちらに乗り換えてみることにしました。

ただ、HerokuでDockerコンテナを走らせるにあたって問題なのが、アクセスがしばらくないとスリープすることです。この時、コンテナもkillされてしまうようで、hugo-amazon-apiが使っているAPIからの問い合わせ結果をローカル・ファイルとしてキャッシュしておくという方法はあまり有効ではありません。

ということで、Herokuでもaddon経由で使えるRedisをhugo-amazon-apiから使えるようにしてみました。

## まとめ

今回はやりたいことを正味1時間ほどのコーディングで実現できて、やっぱり、Goはいい言語だなーと再認識しました。

仕事でちょろっとGoを書いたことはありますが、今年はもうちょっとGoと触れたいなと思います。

あと、他の人が書いたコードを読むのはやはり勉強になります。

今回書いたコードは、正直需要がものすごく低そうなので、fork元のupamuneさんにpullreq送るかしばらく考えたいと思います。

[^1]: ブログの環境まわりについては、記録としてまた別エントリに起こしたいと思います。
[^2]: 純粋に動かしてみたかったという理由です。ちなみに自前サーバで動かすという案は「運用をできるだけ楽する」というのがコンセプトなので脳内で即却下しました。
