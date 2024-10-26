```mermaid
erDiagram
    BOOKS {
        int book_id PK
        int supplier_id FK
        int book_isbn
        int book_sku
        int stock_new
        int stock_used
        char format
        int price
        int retail_value
    }
    BOOKS ||--|{ SUPPLIER : book_id
    SUPPLIER {
        int book_id FK
        varchar supplier_name
        int contact_number
        varchar contact_email
    }
    BOOKS ||--|{ BOOK_TITLES : book_id
    BOOK_TITLES {
        varchar title PK
        int book_id PK, FK
    }
    BOOKS ||--|{ BOOK_GENRE : book_id
    BOOK_GENRE{
        char genre PK
        int book_id PK, FK
    }
    BOOKS ||--|{ BOOK_AUTHOR : book_id
    BOOK_AUTHOR {
        char author PK
        int book_id PK, FK
    }
    BOOKS ||--|{ ORDER_ITEMS : book_id
    ORDER_ITEMS {
        int order_id PK, FK
        int book_id PK, FK
        int quantity
    }
    BOOKS ||--|{ RECEIPT_ITEMS : book_id
    RECEIPT_ITEMS {
        int order_id PK, FK
        int book_id PK, FK
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

       