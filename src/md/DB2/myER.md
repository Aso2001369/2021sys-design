```startuml
@startuml


!define METAL #F2F2F2-D9D9D9
!define MASTER_MARK_COLOR AAFFAA
!define TRANSACTION_MARK_COLOR FFAA00

skinparam class {
    BackgroundColor METAL
    BorderColor Black
    ArrowColor Black
}


package "オリジナルECサイト" as target_system {

    entity "顧客マスタ" as m_customers <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        mail
        del_flag
        reg_date
    }
    
    entity "購入テーブル" as d_purchase <d_purchase> <<T,TRANSACTION_MARK_COLOR>> {
        + order_id [PK]
        --
        customer_code
        purchase_date
        total_price
    }
    
     entity "購入詳細テーブル" as d_purchase_detail <d_purchase_detail> <<T,TRANSACTION_MARK_COLOR>> {
        + order_id [PK]
        + detail_id [PK]
        --
         item_code [FK]
        price
        num
    }

    entity "商品マスタ" as m_items <m_items> <<M,MASTER_MARK_COLOR>> {
        + item_code [PK]
        --
        item_name
        price
        image
        detail
        del_flag
        reg_date
    }
    
    entity "ラッピングマスタ" as m_items <m_items> <<M,MASTER_MARK_COLOR>> {
        + item_code [PK]
        --
        item_name
        price
        image
        detail
        del_flag
        reg_date
    }
    
    m_customers |o-ri-o{ d_purchase
    d_purchase ||-ri-|{ d_purchase_detail
    d_purchase_detail }-do-|| m_items
    
@enduml
```
