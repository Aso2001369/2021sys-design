```startuml
@startuml


/'
  図の中で目立たせたいエンティティに着色するための
  色の名前（定数）を定義します。
'/
!define MAIN_ENTITY #E2EFDA-C6E0B4
!define MAIN_ENTITY_2 #FCE4D6-F8CBAD

/' 他の色も、用途が分りやすいように名前をつけます。 '/
!define METAL #F2F2F2-D9D9D9
!define MASTER_MARK_COLOR AAFFAA
!define TRANSACTION_MARK_COLOR FFAA00

/'
  デフォルトのスタイルを設定します。
  この場合の指定は class です。entity ではエラーになります。
'/
skinparam class {
    BackgroundColor METAL
    BorderColor Black
    ArrowColor Black
}


package "ECサイト" as target_system {
    /'
      マスターテーブルを M、トランザクションを T などで表記
      １文字なら "主" とか "従" まど日本語でも記載可能
     '/

    entity "顧客マスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        tel
        mail
        del_flag
        reg_date
    }
    
    entity "購入テーブル" as customer <d_purchase> <<M,MASTER_MARK_COLOR>> {
        + order_id [PK]
        --
        customer_code
        purchase_date
        total_price
        
    }
    
@enduml
```
