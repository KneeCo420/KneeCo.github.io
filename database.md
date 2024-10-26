```mermaid
erDiagram
    BOOKS ||--|| INVENTORY : book_id
    BOOKS {
        int book_id PK
        int book_isbn
        int book_sku
        char title
        char genre
        char author
        char format
        char supplier
        int price
        int retail_value
    }
    RECEIPT ||--|{ RECEIPT_ITEMS : receipt_id
    RECEIPT {
        int receipt_id PK
        int username FK 
        int retail_tax
        int total
        datetime time_of_transaction
    }
    STORE_ORDERS ||--|{ ORDER_ITEMS : order_id
    STORE_ORDERS {
        int order_id PK
        int username FK 
        int total
        datetime time_of_transaction
        datetime ship_date
        char status
    }
    BOOKS ||--|{ ORDER_ITEMS : book_id
    ORDER_ITEMS {
        int order_id FK
        int book_id FK
        int quantity
    }
    BOOKS ||--|{ RECEIPT_ITEMS : book_id
    RECEIPT_ITEMS {
        int order_id FK
        int book_id FK
        int quantity
        int promotions_discount
        int quality_discount
    }
    INVENTORY {
        int book_id FK
        int stock_used
        int stock_new
    }
    CUSTOMER_ACCOUNTS ||--|{ RECEIPT : username
    CUSTOMER_ACCOUNTS {
        varchar username PK
        varchar password_hash
        varchar payment_method   
    }
    USER_ACCOUNTS ||--|{ STORE_ORDERS : username
    USER_ACCOUNTS {
        varchar username PK
        varchar password_hash
        int permissions_level 
    } 
       
       