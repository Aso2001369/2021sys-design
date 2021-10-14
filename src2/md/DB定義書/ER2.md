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

    entity "商品テーブル" as d_items <d_items> <<T,TRANSACTION_MARK_COLOR>> {
        + item_id [PK]
        --
        item_name
        item_detail
        image
        price
        gift_flag
        # region_id [FK]
        # category_id [FK]
    }
    
    entity "顧客テーブル" as d_customers <d_customers> <<T,TRANSACTION_MARK_COLOR>> {
        + customer_id [PK]
        --
        name
        furigana
        postal_code
        address1
        address2
        mail
        pass
    }
    
    entity "購入テーブル" as d_purchase <d_purchase> <<T,TRANSACTION_MARK_COLOR>> {
        + purchase_id [PK]
        --
        purchase_date
        total_price
        # customer_id [FK]
    }
    
     entity "購入詳細テーブル" as d_purchase_detail <d_purchase_detail> <<T,TRANSACTION_MARK_COLOR>> {
        + purchase_id [PK]
        + detail_id [PK]
        --
         num
         price
         # item_id [FK]
    }

    
    
    entity "カテゴリーテーブル" as d_category <d_category> <<T,TRANSACTION_MARK_COLOR>> {
        + category_id [PK]
        --
        category_name
    }
    
    entity "地域テーブル" as d_region <d_region> <<T,TRANSACTION_MARK_COLOR>> {
        + region_id [PK]
        --
        region_name
    }
    
    entity "お気に入りテーブル" as d_favorite <d_favorite> <<T,TRANSACTION_MARK_COLOR>> {
        + customer_id [PK]
        + item_id [PK]
        --
    }
    
    
    d_customers |o-ri-o{ d_purchase
    d_purchase ||-ri-|{ d_purchase_detail
    d_purchase_detail }-do-|| d_items
    d_items ----|{ d_category
    d_items ----|{ d_region
    d_items ----|{ d_favorite
    d_customers ----|{ d_favorite
    
@enduml
```
