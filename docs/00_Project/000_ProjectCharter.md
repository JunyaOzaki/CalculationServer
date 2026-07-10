# Project Charter（ドラフト v0.1）

## プロジェクト名
CalculationServer

## Mission（使命）
CalculationServerは、生産ラインで使用されるアプリケーションのための、リアルタイムな計算・設定基盤を提供する。  

## Vision（目指す姿）
生産ラインのあらゆるアプリケーションが、
- 設定値
- 演算式
- 判定式
- パラメータ

を共通の計算基盤で管理できるようにする。その際のベースとして、Excel形式の機能を活用とする。 
エディタとしてはExcelやLiberaOfficeが担い、アプリケーションとの連携による処理サーバーがこのツールの本質とする。

## 最優先事項
下記の優先順位で、設計構想を行う
1. 安定性
2. 拡張性
3. 保守性
4. 性能
5. Excel互換性

## Excelとの位置付け
Excel形式仕様は目的ではなく、手段の一つである。  
なので、完全互換を目的としない。  
ただし、本アプリで対応している数式関数機能は、Excelとの結果が一致することを保証するものとする。

## このソフトが提供するもの
CalculationServerは、
- データ管理
- 数式演算
- 依存関係管理
- イベント通知
- 外部通信（外部アプリケーションから制御）

を提供する。   
GUIは、現在の状態をリアルタイムに見える・編集出来るようにする

## Excel互換の範囲
今後、段階的に互換レベルを検証し進めていく

- Level1
  基本演算処理

- Level2
  Lookupなどの応用演算処理

- Level3
  Dynamic Array（スピル）


## 設計理念
### Design Principles
1. Core is Forever
- Coreは可能な限り変更しない。
- 拡張はPluginで行う。

2. Excel is an Adapter
- Excelは入出力アダプタの一つ。
- システム全体をExcelに依存させない。

3. Everything is Replaceable
- 数式エンジンも通信もUIも交換できる。

4. Test First
Excelとの互換性は自動テストで証明する。

5. Architecture over Implementation
実装より設計を優先する。

### 開発方針
CalculationServerは、生産ラインにおける計算・設定基盤を提供することを目的とする。  
Excel互換やGUIは、その目的を実現するための手段であり、目的そのものではない。  
設計・実装・機能追加を行う際は、常にこの原則に立ち返る。  

### No Goal
CalculationServerは以下を目的としない
- Excelの完全互換
- Microsoft Officeの代替
- 高機能な表計算ソフトの提供
- グラフ編集
- マクロ(VBA)実行
- 印刷機能
