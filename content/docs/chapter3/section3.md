---
title: "EPSS"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 3
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# EPSS

[EPSS(Exploit Prediction Scoring System)](https://www.first.org/epss)のスコアは、各脆弱性に対して0から1の範囲で算出され、スコアが高いほど攻撃に利用される可能性が高くなります。

**スコアリング方法:**
1. CVEが割り当てられた脆弱性についての詳細を収集します。
2. ExploitDBやKEVカタログ(Known Exploited Vulnerabilities catalog)から公開されているエクスプロイトコードや攻撃に使用された実例を収集します。
3. 上記の情報をEPSSのモデルからモデリング手法を用いてスコアを算出します。

## どのように使うのか
CVEが割り当てられた脆弱性のリスク評価にはCVSSが用いられ、組織内で定められたパラメータが採用されることが多いですが、**まだ発生していないリスクの発生可能性を見積もるのは非常に難しい**といえます。

そこで、EPSSのように、脆弱性が実際に悪用される確率を表す指標を採用することも効果的です。
EPSSは実行環境を考慮していないため、リスク評価の完全な指標として用いることは推奨されませんが、**他に脆弱性の発生可能性を見積もる手段がない場合には有効**です。

トリアージのパラメータとして必ずしも採用する必要はありませんが、トリアージ担当者は「判断の指標」として知っておくべきです。


## トリアージ設定におけるEPSS確認のメリット
**脆弱性の優先順位付け**  
脆弱性が実際に悪用される可能性を考慮して、優先順位を設定できます。組織内に脆弱性の危険度設定に関するノウハウがない場合や、CERTが設立されたばかりの際には、危険度設定の参考値としてEPSSを活用できます。  
ただし、EPSSはあくまで予測値であり、全ての脆弱性に設定されているわけではない点に留意する必要があります。  
EPSSを指標として採用する場合、3章の後半で紹介されているKEVカタログなどの公開情報と組み合わせて使用することを推奨します。