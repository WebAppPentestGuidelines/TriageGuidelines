---
title: "Exploitの流通状況"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 3
bookToc: false
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Exploitの流通状況
脆弱性を悪用する攻撃コードの流通状況を把握することで、対応までの時間的猶予（緊急度）をより正確に判断できます。

以下のExploit流通状況の中では、「攻撃事例がある」場合が最も緊急性が高く、即座に対応すべき脆弱性と判断できます。

- 攻撃事例がある
- 脆弱性の実証コード（PoC）が出回っている
（PoCが正しいものであるかの確認が必要）
- 理論的に脆弱なだけで実証されていない

{{% hint info %}}
**補足**  
Exploitの流通状況だけで対策の優先順位を決定することは推奨されません。即座に攻撃される可能性があるのか、攻撃手段が流通してしまっているのかを元に判断することを意図しています。
{{% /hint %}}

## どのように情報収集するのか
悪用されやすかったり、利用者が多いプロダクトの脆弱性については、ニュースサイトや第1章で紹介した脆弱性情報サイト（ [JPCERT/CC](https://www.jpcert.or.jp/)、[JVN](https://jvn.jp/)など）から情報が得られやすいです。  
しかし、注目される脆弱性は限られているため、使用しているプロダクトに関連する攻撃コードの流通状況については、常に注意して情報を収集する必要があります。

### 実証コード（PoC）の掲載サイト  

脆弱性の実証コード（PoC: Proof of Concept）の掲載サイトや脆弱性スキャンツールベンダーのサイトなどから情報が得られやすいです。

- [ExploitDB](https://www.exploit-db.com/)
- [Vulnerability & Exploit Database](https://www.rapid7.com/db/?q=&type=metasploit)
- [vulnerability-lab](https://www.vulnerability-lab.com/index.php)
- [Packet Storm Security](https://packetstormsecurity.com/files/tags/exploit/)

### 悪用された脆弱性リスト  

米国CISA（Cybersecurity＆Infrastructure Security Agency）が提供する、実際に悪用が確認された脆弱性リストである[KEVカタログ](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)（Known Exploited Vulnerabilities catalog）を参照することも有効です。ただし、脆弱性が公開された直後の場合、悪用がまだ確認されていないこともあるため、対応の優先順位を決定する際には注意が必要です。  
継続的にKEVカタログから情報収集する場合は、情報更新時にお知らせを受領するための登録フォームがあります。
    
### 検索  

Web検索や脆弱性情報管理ツールでExploitの流通状況を調べる手段もあります。  
検索クエリに「CVE番号」や「CVE番号　PoC」、「CVE番号　"in the wild"」などを設定しての検索は有効です。ただし、誤った情報や偽PoC、偽攻撃ツールも存在しているため、信頼できる情報であるのか慎重な判断が必要です。

-  [Flashpoint Vulnerability Intelligence \- VulnDB](https://flashpoint.io/ignite/vulnerability-intelligence/)（有償）

## 自社開発のアプリケーション等の場合
自社開発のアプリケーションは一般的なプロダクトではないため、実証コード掲載サイトやKEVカタログを参照しても、Exploitの流通状況が把握できないことが多々あります。  
「脆弱性の前提条件」の項目や脆弱性診断を実施したベンダーからの報告内容を基に、同様の攻撃手法が実行される可能性やその影響について調査する必要があります。