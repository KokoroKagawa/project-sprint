---
layout: post
title: "リリースマネジメント"
---

### バージョン管理

バージョン番号は、セマンティックバージョニングを使用して、「vX.Y.Z」のように定められます。ここで、Xはメジャーバージョン番号です。Yは、ゼロから始まるマイナーリリース番号です。Zはパッチ・リビジョン番号で、これもゼロから始まります。

定義は以下の通りです。

- メジャーアップデート
プロジェクトスプリントの記述内容に大幅な修正や方向性の変更があった場合

- マイナーアップデート
ディレクトリ構造の変更
ディレクトリ名の変更
新規URLの追加
既存URLの削除
各ドキュメント内の第二・第三・第四見出しレベルの見出し名の変更や構成変更を伴うような修正

- パッチ
マイナーアップデート以下リビジョン以上の修正

- リビジョン
誤字脱字の修正。文字校正レベルの修正

### リリース用のブランチ管理

各回のリリース後、次回リリースに向けて事務局（[@motoi](https://github.com/motoi) 、[@Satoshi-Matsumoto](https://github.com/Satoshi-Matsumoto) 、[@KokoroKagawa](https://github.com/KokoroKagawa)）が以下2点を実施します。

- Masterブランチから次回リリースの管理用ブランチを作成
命名ルール：vX.Y.Z

- 管理用ブランチをMasterブランチにマージするためのPull Requestを作成
命名ルール：vX.Y.Z
※最終的なリリース作業に入るまでは、冒頭に[WIP]を記載する(例：[WIP] v2.1.0）

個別のIssueに関しても、原則として一つずつブランチが作成され、Issueへの対応が終わると管理用ブランチにマージされ、元のブランチは削除されます。

パッチやリビジョンのみでのリリースは基本的に避け、マイナーアップデート以上の内容変更があった場合にリリースを実施します。パッチやリビジョンに当たる修正作業を行った場合には、次回リリースの管理用ブランチに作業ブランチをマージし、マイナーアップデート以上の内容変更が発生するのを待ちます。

### リリースまでのIssue処理フロー

#### (1)Issueの起票
Project Sprintのウェブサイトに課題や改善点を見つけたり意見を持ったりしたコントリビューターが、Issueの作成を行います。誰もが自由にコントリビューターとして参加することができます。参加の方法は[こちら](https://projectsprint.org/contributing.html)をご覧ください。

#### (2)Issueの確認・課題の明確化
事務局は作成されたIssueが対応を必要とするものかどうかを週次で検討し、対応するのであれば進め方や担当者、期日を決定します。課題や論点が不明確な場合は、起票者と会話したり起票者にIssueをアサインして明確化を依頼したりすることもあります。対応不要と判断されたIssueは、事務局がクローズします。

#### (3) Issueの優先順位付け
事務局は対応すべきIssueの優先順位付けを週次で行い、Project Boardに反映させます。

#### (4) Issueへの対応
Project Boardの"Prioritized"の上位にあるIssueから順に対応が進められます。
基本的に、プロジェクトスプリントの内容に関するIssueは[@KokoroKagawa](https://github.com/KokoroKagawa)が一次対応を行い、[@motoi](https://github.com/motoi)のレビューを経て対応完了となります。プロジェクトスプリントのサイト仕様に関するIssueは[@kikuchiharuma](https://github.com/kikuchiharuma)が対応します。
Issueへの対応が完了し、作業ブランチが次回リリースの管理用ブランチにマージされたら、対応担当者がIssueをクローズします。

### リリース手順

リリース作業は事務局が実施します。事務局は、マイナーアップデート以上に該当するIssueへの対応が完了したタイミングで、前回のリリース以降に対応完了されたIssueを確認します。その後、それらに関連が深い未対応のIssueのうち、今回のリリースに含めるべきものを洗い出して対応し、リリース内容の範囲とリリースの日程を確定します。

今回のリリースの管理用ブランチをMasterブランチにマージするためのPull Requestは、前回リリース直後にあらかじめ作成されています。管理用ブランチに今回のリリース内容を反映させ、Pull Requestを実施することで、リリースが行われます。

変更箇所は事務局によりリリースノートに記載されるほか、[Slackコミュニティ](https://projectsprint.slack.com/)の #04_SGMs/PJS_リリース情報 チャンネル内でもアナウンスされます。

### 英語版のリリースマネジメント
英語版は、日本語版がリリースされたタイミングで当該リリースに対応する修正・更新を開始します。 その際、「英語バージョンの更新」というIssue及びこれに紐づくブランチを立て、その中で作業します。差分は、前回のリリース管理用ブランチがmasterブランチにマージされた際のdiffで把握します。
英語版の修正・更新作業が完了したら、作業ブランチは日本語版の次回リリースの管理用ブランチにマージされ、日本語版のリリースと併せてリリースされます。
