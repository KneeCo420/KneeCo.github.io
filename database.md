```mermaid
erDiagram
    BOOKS {
        int book_id PK
        int book_isbn
        int book_sku
        int stock_new
        int stock_used
        char format
        char supplier
        int price
        int retail_value
    }
    BOOKS ||--|{ BOOK_TITLES : book_id
    BOOK_TITLES {
        varchar title PPK
         int book_id FK , PPK
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
    ACCOUNTS ||--o{ RECEIPT : username
    ACCOUNTS ||--o{ STORE_ORDERS : username
    ACCOUNTS {
        varchar username PK
        varchar password_hash
        int permissions_level  
    }

       