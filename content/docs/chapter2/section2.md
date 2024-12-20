---
title: "脆弱性の前提条件"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 2
bookToc: false
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# 脆弱性の前提条件

脆弱性が報告される際、よく見られるのがソフトウェアのバージョンに基づく影響範囲です。しかし、自社のシステムの使用方法次第では、脆弱性情報に記載されているバージョンを使用していても、影響を受けない場合があります。

例えば、脆弱性が特定のモジュールや設定に依存している場合、それらの条件が満たされていなければ影響を受けないことがあります。

## ソフトウェアバージョン以外の前提条件の例
具体的には、以下のようなケースが存在します。
* 特定のモジュールをインストールしている場合にのみ影響がある
(多くのCVEで該当)
* 特定の機能を利用/有効化している場合のみ影響がある
(例：Apache HTTP Serverでmod_proxyが有効な場合 等)
* 特定の設定値をon/off、あるいは特定の値に設定している場合のみ影響がある
(例：log4jなどJavaベースのアプリにてJVMの特定の起動オプションを指定する場合 等)

## 前提条件の確認方法の例
脆弱性の前提条件を把握するためには、次のような方法が考えられます。
使用しているライブラリなどのバージョン情報以外の情報を確認したり、参考サイトやベンダー情報を参照します。その上で、自社開発システムの場合などには、該当のソフトウェアの設計書やソースコードを調べる必要があります。

## システムへの影響を見極めるために確認が必要なこと
脆弱性情報に加え、自社開発システムに関しても以下の項目を確認する必要があります。ただし、どの範囲まで確認するかは、脆弱性の特性によって異なるため、一概には言えません。
* システムの構成
* システムの内部仕様/外部仕様
* 実際の設定値

これらの情報を確認することで、最も一般的な対応策である「ソフトウェアのバージョンアップ」に加え、機能の一時的な無効化など、他の柔軟な対応策を検討できるようになります。それにより、トリアージの優先順位付けがより柔軟に行えるようになります。
　(例：⁠regreSSHion(CVE-2024-6387)において、LoginGraceTimeの設定で緩和が可能 等)

## 注意
注意すべき点として、システムを調査する際仕様書を基に判断したものの、その仕様書が古く、実際のシステム環境と一致していない場合や、誤った確認方法を用いたために脆弱性が存在しているにもかかわらず、影響がないと判断してしまうケースがあります。
運用者のスキル・調査の方法などを踏まえて、「ソフトウェアのバージョンアップ」を優先するほうが安全であるケースがあるため、注意して判断を行ってください。