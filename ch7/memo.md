# Chapter 7 Webシステムの構築と運用

## 01

## 02

## 03

## 04

## 05

## 06

## 07

## 08

## 09

## 10 バックアップ運用
サーバを冗長化しても，災害などで全て故障することがある
-> データをバックアップして，万が一に備えましょう

バックアップ運用: バックアップデータの取得，不要データの削除などの作業

バックアップ方法
- 対象 アプリケーション，コンテンツ, DB
- 保存場所 災害に備えるため，別のデータセンターにあるサーバ保存

バックアップ頻度・世代
- 頻繁に保存して，出来るだけ最新状態に復旧できるようにする
- 適切な状態に戻せるように，何世代分は保管しておく

## 11 ログ運用

サーバやネットワーク機器の動作状態が記録　ログファイル
種類：
- システムログ OSが発生したイベントやエラー
- アプリケーションログ ミドルウェアなどアプリケーションの動作履歴
- アクセスログ Webサーバなどが受けたリクエスト

機器故障の原因，バグ，サイバー攻撃の形など読み取れる有益な情報 -> ログもバックアップ対象hに

可読性，容量低下に対応するため，定期的にログ運用，メンテナンスが必要

ログローテーション
- ログファイルを切り分け，別ファイルとして保存して可読性を上げる
- ハウスキープ 古いログファイルを削除してストレージ容量を圧迫しないようにする

アクセスログ解析
- アクセスログを解析して，売り上げなどの増加につなげる
- 例 ApachLogViewer Visitors

## 12 Webサイトのパフォーマンス

リクエスト -> 一連の処理 -> 画面表示　までの時間など

指標
- 応答時間 リクエスト送信からHTTP応答が帰ってくるまで
- 表示完了時間 リクエスト送信からWebページ読み込みが完了するまで
- ページ読み込み時間 ページの読み込み開始から読み込み完了まで
- 可用性 エラーなくWebサイトにアクセスできた確率

パフォーマンス監視
- 定期的にパフォーマンスを監視して，低下を検知した場合は原因を調査し適切に対処する
- パフォーマンスの監視とともに，サーバの負荷状態を同時に監視する
- 常時監視することで可用性を算出できる
- 監視ツール Zabbix, Pandra FMS, Nagiosなど

## 13 脆弱性診断

構築時脆弱性対策をやっても運用時に新たな脆弱性が発見される可能性

対策
- 脆弱性情報データベースを定期的にチェックし，利用製品の脆弱性情報を確認
- ペネトレーションテスト 擬似的にWebシステムに攻撃を仕掛けてチェックする
    - ツールを用いて実施することもできるが，より詳細な診断を求める場合はセキュリティ企業に依頼 (例 このまえ頼んだゲヒルンとか)
    - WebアプリケーションだけでなくOSやミドルウェアの脆弱性も同時に調査してもらえる

脆弱性が発見された場合の対策
- Webアプリケーション 該当箇所の修正
- OS，ミドルウェア 修正プログラムを適用，脆弱性のないバージョンへアップグレード
(OS，ミドルウェアのバージョンアップをすると，アプリケーションの構築環境がかわるので，十分な検討が必要)
