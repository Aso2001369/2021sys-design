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


package "特産品販売サイト" as target_system {

    entity "商品テーブル" as m_items <m_items> <<M,MASTER_MARK_COLOR>> {
        + item_id [PK]
        --
        item_name
        item_detail
        image
        price
        gift_flag
        # region_id [FK]
    }
    
    entity "顧客テーブル" as m_customers <m_customers> <<M,MASTER_MARK_COLOR>> {
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

  
    entity "地域テーブル" as d_region <d_region> <<T,TRANSACTION_MARK_COLOR>> {
        + region_id [PK]
        --
        region_name
    }
    

    m_items }o-do-|| d_region

    
@enduml
```
