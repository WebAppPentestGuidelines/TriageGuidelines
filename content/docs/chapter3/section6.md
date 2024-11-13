---
title: "Risk Rating Framework: OWASP Risk Rating Methodology"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 5
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Risk Rating Framework: OWASP Risk Rating Methodology
OWASP Risk Rating Methodologyは、OWASPが提供する、アプリケーションセキュリティに特化したリスク評価手法です。
- https://owasp.org/www-community/OWASP_Risk_Rating_Methodology

本評価手法では、以下のような評価基準で判定しています。

- リスク = 可能性 × 影響（Risk = Likelihood x Impact）
    - 可能性
        - （脅威エージェントの要因 ＋ 脆弱性の要因） / 2
    - 影響
        - （技術的要因 ＋ ビジネスへの影響要因） / 2

「リスク（Risk）」は、「可能性」と「影響」を複数の要因に分けて評価され、各要因に基づきスコアを算出し、その平均値で評価を行います。

以下に概要を示します。

「可能性（Likelihood）」は、特定の脆弱性が攻撃者に発見され、悪用される可能性の大きさを指します。

以下の2つの要因についてスコアリングし、合計平均値を可能性の値として利用します。

1. **脅威エージェントの要因（Threat Agent Factors）**  
想定する攻撃者（Threat Agent）による攻撃が成功する可能性を推定します。
- スキルレベル（Skill Level）
- 動機（Motive）
- 機会（Opportunity）
- サイズ（Size）

2. **脆弱性の要因（Vulnerability Factors）**  
対象とする脆弱性について、発見や悪用される可能性を推定します。
- 発見の容易さ（Ease of Discovery）
- 悪用の容易さ（Ease of Exploit）
- 認識（Awareness）
- 侵入検出（Intrusion Detection）

「影響（Impact）」は、攻撃が成功した際に影響がある以下の2種類の影響について想定します。
1. **技術的要因（Technical Impact Factors）**  
アプリケーションや使用するデータ、提供する機能に対する技術的影響を推定します。
- 機密性の喪失（Loss of Confidentiality）
- 整合性の損失（Loss of Integrity）
- 可用性の損失（Loss of Availability）
- 説明責任の喪失（Loss of Accountability）

2. **ビジネスへの影響要因（Business Imapct Factors）**  

- 経済的損失（Financial damage）
- 風評被害（Reputation damage）
- コンプライアンス違反（Non-compliance）
- プライバシー侵害（Privacy violation）

これらの値を元に、リスクの重大度をマトリックスから導き出します。

リスク判定の際に注意すべきは、「可能性 x 技術的要因」と「可能性 x ビジネスへの影響」の2軸で検討する必要がある点です。

- 「技術的な影響度は高いが、全体的なビジネスへの影響度は低い」といった場合、ビジネスへの影響度を優先して判断するのが妥当と考えられます。
- 評価している脆弱性のビジネス上の背景を理解することが、リスクを適切に判断する上では非常に重要です。