---
title: ブログを再開します。ツールをHugoからGatsby.jsに変更しました。
date: "2020-08-15T15:05:19.18"
template: "post"
draft: false
slug: "blog-restart-from-hugo-to-gatsbyjs"
category: "Web Development"
tags:
  - "Gatsby.js"
  - "Hugo"
  - "Web Development"
description: "しばらく更新していなかったブログを再開します。以前は、Hugoを使って運営していましたが、Gatsby.jsとGitHub Pagesの構成での運営に変更しました。これまでのブログの運営方法の中で、冗長と思われるフローを改善して、記事作成に注力できる環境を構築しました。"
socialImage: "/media/blog-restart-from-hugo-to-gatsby.jpg"
---

- [以前のブログの運用方法](#以前のブログの運用方法)
- [改善したこのブログの運用方法](#改善したこのブログの運用方法)

しばらく更新していなかったブログを再開します。以前は、Hugoを使って運営していましたが、Gatsby.jsとGitHub Pagesの構成での運営に変更しました。これまでのブログの運営方法の中で、冗長と思われるフローを改善して、記事作成に注力できる環境を構築しました。

## 以前のブログの運用方法

以前のブログ　[Leisurely Web Programing](https://hugo.vivo-one.net/)　は静的サイトジェネレーターのHugoを使って運営していました。Goで構築されているHugoは、ビルドが圧倒的に速かったです。しかし、私の運用方法は、まだ改善の余地のあるものでした。その時の運用方法は、自分のパソコンで記事を書き、ビルドをして、生成されたpublicフォルダの中身をレンタルサーバの公開ディレクトリにrsyncでアップロードするというものでした。Bitbucketにて、ソースを管理していましたが、それはただ、ソースの保管をしている意味しかありませんでした。

ソースがレポジトリサービス上にあるのであれば、そこでビルドとテストをして、デプロイまで出来ることは分かっていたのですが、ブログの更新自体をしなくなって、手付かずの状態でした。

![42-line-bible.jpg](/media/blog-restart-from-hugo-to-gatsby.jpg)

## 改善したこのブログの運用方法

ブログを再開するにあたり上記の問題の解決も含めて、ツール、運用環境の検討をしました。HugoとBitbucketの環境でも、問題点を解消できる運用は出来るのですが、他のツール、運用環境を使ってみたいので調査をしました。Gatsby.jsとGitHub Actions、GitHub Pagesで運用することにしました。

- [Gatsby](https://www.gatsbyjs.com/)　静的サイトジェネレーター　Reactで作られている
- [GitHub Actions](https://github.co.jp/features/actions)　GitHubから直接コードをビルド、テスト、デプロイ
- [GitHub Pages](https://pages.github.com/)　GitHub リポジトリからGitHub Actionsを経由してホスト


Gatsby.jsのスターターキットを使ってサイトを制作しました。自分のパソコンで記事を作成します。Hugoと同じ静的サイトジェネレーターのカテゴリのツールなので、プロジェクト内のファイルを確認すれば、なんとなく、そのファイルの役割は分かりました。

記事ができたら、GitHubのレポジトリにpushします。pushをきっかけにGitHub Actionsの機能が動作して、GitHub上でコードのビルド、テスト、デプロイが走ります。エラーが発生しても、どこでエラーが発生したのかが追えるように記録されています。GitHub Pagesにデプロイされたサイトが公開されます。記事ファイルをMarkdown形式で書いて、GitHubにpushするだけで、後の工程は、すべて自動化できました。
