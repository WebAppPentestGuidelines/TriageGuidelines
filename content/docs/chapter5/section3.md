---
title: "経営者の指示による優先度変更"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 3
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# 経営者の指示による優先度変更
経営判断により脆弱性対応よりもリリースを優先しなければいけない案件が存在することもあります。

例として次のような事例を考えてみましょう。  
「会社の代表が株主総会で会社の認証システムをすべて顔認証システムに3ヶ月以内に切り替えると株主に伝えて社員がその場で初めて内容を認識した」とした場合です。  

上記の場合、3ヶ月という短納期の中で開発から脆弱性診断を実施するという流れの中で他案件との兼ね合いや他フローとの兼ね合いで十全に脆弱性診断を実施ができず現場としては無理難題であるため期限内に組織で定められた脆弱性トリアージ実施をしてリリースすることが難しい可能性が考えられます。  

しかし、ビジネスインパクトを考えた際に、IRとして会社代表が出していることから、ブランドイメージの悪化や株価への悪影響が考えられます。  

そのため、上記の場合にはトップダウンで実施しなければならない案件として例外的な対応を行う必要があります。

仮に会社の脆弱性トリアージの実施規定として以下のようなものがあるとします。

【社内規定での脆弱性トリアージ】
- リスク値は緊急、高、中、低の4段階で考えられるとする
- リスク中以上の脆弱性はリリース前に全て修正して実施する

今回のケースでは、3ヶ月という短納期の中で実施しなければならないため、十分な脆弱性診断の期間と修正期間が無く、脆弱性トリアージ規定を満たせない可能性があります。つまり、想定していたよりもリスクが高い状態のままリリースするという経営判断をすることになります。  

そのため、以下のような例外を作り、組織として最終的にリスクを減らすための方針を立てることもあります。

【組織的例外フロー】  
- 組織の代表のトップダウン案件は他案件より優先して脆弱性診断を実施する
- 組織の代表のトップダウン案件で検出された脆弱性は、リスク高以上はリリース前に対策を実施して、リリース後1ヶ月以内にリスク中の脆弱性の対策を実施する
- 残存した脆弱性に関してインシデントが起きた際には組織の代表が責任を取る

日常の運用とは異なる例外的なフローを設けたことで、ビジネスインパクトを考慮することができました。

(経営者が判断したポイントは？)  
・3か月でシステムをリリースすることを決定した
・組織的例外フローを受け入れた（リスク受容した）
・事故ったときの責任は下々ではなく経営者だぞ

今回の例の中で、経営者が判断したポイントとなるのは下記の3点となります。

- 短期間でのリリース方針  
３ヶ月という短期間でのシステムリリースを決定することで、ビジネス価値の最大化に繋がります。
しかし、今回のケースとは異なり、脆弱性が多数発見された場合には、経営者の判断で、リリース時には重要度の高い中でも特に重要なものに対して優先的に対応を行うといったトリアージが必要となります。
 
- 例外承認 (リスク受容)  
経営者が組織的例外フローを受け入れて実施することで、迅速な意思決定が可能となり、責任の所在も明確になります。しかし、例外的なフローはあくまで緊急時や特別な状況における対応であり、推奨されるものではありません。そのため、例外承認を行う場合には、経営者（責任者）が慎重に判断し、適切なリスク評価を行うことが重要です。  
さらに、例外承認後には脆弱性をトレースし、対応期限を設定することが求められます。また、監視体制の強化やリスク低減策の導入など、継続的な管理が効果的です。  

- インシデントの担当責任を明確にする  
リスクを残したままサービスをリリースすることで、インシデントが発生する可能性があります。万が一インシデントが発生した場合、その責任はセキュリティ担当者ではなく、経営者が負うことでビジネス全体に関わる問題であるとしてリスク管理を明確にできます。

経営判断として、時にはビジネスが優先されることもあります。しかし、脆弱性を放置したことによって、それ以上のダメージを負うことも考えられます。
経営者には、そういったリスクがあることも伝えた上で、経営判断を行ってもらう必要があるでしょう。