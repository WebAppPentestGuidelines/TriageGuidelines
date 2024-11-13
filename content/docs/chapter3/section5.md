---
title: "CISA KEVカタログ"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 5
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# CISA Known Exploited Vulnerabilities (KEV) カタログ

[Known Exploited Vulnerabilities (KEV) カタログ](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)（悪用された既知の脆弱性カタログ）は米国土安全保障省（DHS）のサイバーセキュリティ・インフラストラクチャセキュリティ庁（CISA: Cybersecurity and Infrastructure Security Agency）が公開している、悪用が観測された脆弱性の一覧をまとめたカタログです。もともとは連邦政府機関のシステムを対象に、脆弱性を悪用した攻撃へ対処するために作成されたものです。

2024年11月現在、このカタログには、VPN機器のRCE脆弱性やOSの特権昇格の脆弱性など、1200件近くの脆弱性が登録されています。カタログへの登録条件は下記の3つです。

1. CVE番号が割り当てられていること
2. 悪用がされている確たる証拠があること
3. ベンダーからのアップデートなどの明確な対策方法があること

このうち、「2. 悪用がされている確たる証拠があること」には、脆弱でないシステムやハニーポットに対する悪用の試行も含まれていますが、スキャン行為やエクスプロイトの研究、PoCの公開はこれに含まれません。

他組織への攻撃ですでに悪用されたことのある脆弱性は、別の攻撃でも利用されることが多いため、迅速に対処するべき脆弱性であると考えられます。