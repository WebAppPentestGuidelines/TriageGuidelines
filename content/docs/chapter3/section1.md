---
title: "CVSS"
description: "脆弱性トリアージガイドライン作成の手引き"
weight: 1
bookToc: false
# bookFlatSection: false
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# CVSS
CVSS（Common Vulnerability Scoring System）は、脆弱性の深刻度を数値化するためのフレームワークであり、ベンダーに依存しない共通の評価方法を提供しています。脆弱性の深刻度を定量的に評価することで、リスクを理解することができより精度の高いトリアージが可能となります。  

CVSSにはバージョンがあり、ここではv3.1の一部を抜粋して紹介します。CVSSv.3.1の詳細は[「Common Vulnerability Scoring System v3.1: Specification Document」](https://www.first.org/cvss/v3.1/specification-document)をご覧ください。

## CVSSのスコアの種類
CVSSは、次の3つの基準で脆弱性を評価します。  
３つの基準すべてで評価する必要はありませんが、多くの基準で評価することでより精度の高いトリアージを行うことが可能となります。基本評価基準を基本とし、評価の目的や組織の状況に応じて適切な基準を選択し利用してください。

1. **基本評価基準 (Base Metrics):**  
脆弱性そのものの特性を評価する基準です。情報システムに求められる3つのセキュリティ特性、「機密性（Confidentiality Impact）」、「完全性(Integrity Impact）」、「可用性(Availability Impact）」に対する影響を、ネットワークから攻撃可能かどうかといった基準で評価し、CVSS基本値(Base Score)を算出します。このスコアは時間の経過や利用環境の異なりによって変化しません。  
CVSS基本値は以下の8つの観点で算出します。
    * **攻撃元区分(AV：Attack Vector)**  
脆弱性のあるコンポーネントをどこから攻撃可能であるかを「ネットワーク」、「隣接」、「ローカル」または「物理」のいずれかで評価します。
    * **攻撃条件の複雑さ(AC：Attack Complexity)**  
    脆弱性のあるコンポーネントを攻撃する際に必要な条件の複雑さを「低」または「高」のいずれかで評価します。
    * **必要な特権レベル(PR：Privileges Required)**  
    脆弱性のあるコンポーネントを攻撃する際に必要な特権のレベルを「不要」、「低」または「高」のいずれかで評価します。
    * **ユーザ関与レベル(UI：User Interaction)**  
    脆弱性のあるコンポーネントを攻撃する際に必要なユーザ関与レベルを「低」または「高」のいずれかで評価します。
    * **スコープ(S：Scope)**  
    脆弱性のあるコンポーネントへの攻撃による影響範囲を「変更なし」または「変更あり」のいずれかで評価します。
    * **機密性への影響(C：Confidentiality Impact)**  
    脆弱性を攻撃された際に、対象とする影響想定範囲の情報が漏えいする可能性を「なし」、「低」または「高」のいずれかで評価します。
    * **完全性への影響(I：Integrity Impact)**  
    脆弱性を攻撃された際に、対象とする影響想定範囲の情報が改ざんされる可能性を「なし」、「低」または「高」のいずれかで評価します。
    * **可用性への影響(A：Availability Impact)**  
    脆弱性を攻撃された際に、対象とする影響想定範囲の業務が遅延・停止する可能性を「なし」、「低」または「高」のいずれかで評価します。

2. **現状評価基準 (Temporal Metrics):**  
脆弱性の現在の深刻度を評価する基準です。攻撃コードの出現有無や対策情報が利用可能であるかといった基準で評価し、CVSS現状値(Temporal Score)を算出します。このスコアは脆弱性への対応状況に応じ、時間が経過すると変化します。
CVSS現状値はCVSS基本値の項目に以下の3つの観点を加え、算出します。
    * **攻撃される可能性(E：Exploit Code Maturity)**  
    攻撃コードや攻撃手法が実際に利用可能であるかを「未評価」、「容易に攻撃可能」、「攻撃可能」、「実証可能」または「未実証」のいずれかで評価します。
    * **利用可能な対策のレベル(RL：Remediation Level)**  
    脆弱性の対策がどの程度利用可能であるかを「未評価」、「なし」、「非公式」、「暫定」または「正式」のいずれかで評価します。
    * **脆弱性情報の信頼性(RC：Report Confidence)**  
    脆弱性に関する情報の信頼性を「未評価」、「確認済」、「未確証」、「未確認」または「正式」のいずれかで評価します。

3. **環境評価基準 (Environmental Metrics):**  
利用環境も含め、最終的な脆弱性の深刻度を評価する基準です。攻撃を受けた場合の二次的な被害の大きさや、組織での対象製品の使用状況といった基準で評価し、 CVSS環境値 (Environmental Score) を算出します。このスコアは脆弱性に対して想定される脅威に応じ、変化します。  
CVSS環境値の計算には、CVSS現状値の要素に加えて、環境特有の要素として機密性、完全性、可用性の重要度や、攻撃元区分、攻撃条件の複雑さ、必要な特権レベル、ユーザー関与レベル、スコープの修正値が含まれます。これにより、環境値は利用状況固有のセキュリティ要件やリスク許容度が反映されます。


## スコアの計算
それぞれのスコアは0.0 ~ 10.0で数値化されます。  
公開されている計算式をもとに計算することも可能ですが、公式が提供している[Common Vulnerability Scoring System Version 3.1 Calculator](https://www.first.org/cvss/calculator/3.1)を使うことで簡単に計算が可能です。

## CVSSのメリット
* **優先順位が明確になる**  
最終的に数値としてスコアが算出されるため、対応すべき脆弱性の先順位が明確になります。
* **標準的に利用されている**  
最も広く使われている脆弱性評価方法です。各種ベンダーが公開する情報にもCVSSスコアが併記されていることが多く、その値を使うことでそのままトリアージが可能です。