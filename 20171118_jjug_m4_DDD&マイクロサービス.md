# DDD × CQRS - コマンドとクエリでORMを使い分けた話

## ビズリーチ 松岡さん
* Spring Boot,DDD,CQRS
* dddすごい好きblogで色々普及活動している

* 参考資料
http://little-hands.hatenablog.com/entry/jjug2017fall

## CQRSの誤解を解きたい
* CQRSはイベントソーシングとセットで行う必要はないよ
* 段階的CQRS
    * 読み込みと書き込みのモデルを分ける
    * データストアを分ける
    * イベントソーシングを利用する

## ORMをモデル別に分ける
* Writeはモデルに振る舞いを持たせるDDDにする
* Readはテーブルをjoinしたり集計したりする
* ORMのタイプ
    * オブジェクト中心なORM
        * Hibernate、ActiveRecord
    * SQLロジック
        * MyBatis,JOOQ
            * JOOQはRDBのスキーマからSQLに近いDSLを作ってくれる
* WriteModel:Hibernate(springDataJpa)
* ReadModel:JOOQ
* DomainModel(WriteSide)とQueryModelにしたよ

## サンプルコード
* コンストラクタで状態を設定して、初期状態を強制する
* 状態遷移メソッドを作る（setは作らないよ）

## リリース後
* 3ヶ月経ったけどよかったよ
* Hibernate
* WriteModelはSpringDataの思想と近いのでいい感じ
* TestはApplicationService層で書いているので、ドメインのリファクタやり易いよ

## まとめ
* Write/Readモデルの分けはいい感じ

## 感想
* モダンなDDDをしっかり利用している
* Aggregateもしっかり定義している
* 全体的にレベル高い