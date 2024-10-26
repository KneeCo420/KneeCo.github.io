```mermaid
erDiagram
    BOOKS ||--|| INVENTORY : PK_to_FK
    BOOKS {
        int isbn PK
        int SKU FK
        char title
        char genre
        char Author
        char Format
        char Supplier
        bool Availability
        int price
    }
    ORDERS ||--|{ ORDER_ITEMS : PK_to_FK
    ORDERS {
        int Order_ID PK
        int user_ID FK 
        char status
        int subtotal
        int total
    }
    ORDER_ITEMS ||--|{ BOOKS : PK_to_FK
    ORDER_ITEMS {
        int Order_ID FK
        int SKU PK
        int quantity
    }
    INVENTORY {
        int ISBN FK
        int stock_used
        int stock_new
    }
    USER_ACCOUNTS ||--|{ ORDERS : PK_to_FK
    ORDERS {
        int user_ID PK 
        varchar Username
        varchar Password
        char Permissions
    } 
    ORDERS ||--|| RECEIPTS : PK_to_FK
    RECEIPTS {
        int Order_ID FK
        datetime time_of_transaction
        varchar payment_method
        float taxes_payed
    }