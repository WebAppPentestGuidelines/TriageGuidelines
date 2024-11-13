---
title: "ビジネスインパクトを考慮した結果優先度が下がった事例"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 2
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# ビジネスインパクトを考慮した結果優先度が下がった事例
## トリアージ対象の脆弱性：CVE-2022-3080
CVE-2022-3080はBIND 9と呼ばれるDNSサーバーの実装に発見された脆弱性です。  
この脆弱性は、クライアントからフルサービスリゾルバとして動作するBIND 9のDNSサーバーに対し、細工された問い合わせを送信することにより、特定の条件下でサービス不能（DoS）にさせることができるものです。  
CVSSスコアは7.5となっています。  

## トリアージを実施するA社の状況
A社は複数のブログやWebメディアを運営する企業であり、ページ上に掲載される広告を主な収益源としています。これらのサービスは自社のオンプレミスサーバー上で提供していますが、社内業務に必要なサービスの多くはクラウドへの移行が完了しており、社内業務で自社のオンプレミスサーバーへアクセスすることはほとんどありません。  
A社では、下記の2種類の用途でそれぞれ独立したDNSサーバーを運用しており、いずれも今回の脆弱性の影響を受けるバージョンのBIND 9を利用しています。  
- 権威DNSサーバー：ブログやWebメディアのドメインの問い合わせに応答する。
- フルサービスリゾルバ：社内業務に利用するオフィス端末のインターネットアクセスに利用する。

## トリアージ例
A社では、脆弱性の危険度の分類を低・中・高で分類しており、CVSSスコアが7.5の脆弱性の危険度は「高」として分類されます。  
ただし、2種類のDNSサーバーのサービス停止によるビジネスインパクトをそれぞれ下記のように考慮してトリアージを実施しました。

- 権威DNSサーバー：利用者がブログやWebメディアの閲覧ができなくなり、A社の収益の多くを占める広告収入への影響が大きい。
- フルサービスリゾルバ：社内業務に必要な多くのサービスをクラウド化しており、かつ、代替DNSサーバーとしてISPのDNSサーバーを設定しているため、社内業務への影響は限定的である。

今回の脆弱性はフルサービスリゾルバのみに影響することから、ビジネスインパクトは限定的であると考え、優先度を下げて対応を実施することとしました。