```mermaid
erDiagram
    BOOKS ||--|| INVENTORY : PK_to_FK
    BOOKS {
        int SKU FK
        string title
        string genre
        int isbn PK
        int price
    }
    ORDERS ||--|{ ORDER_ITEMS : PK_to_FK
    ORDERS {
        int Order_ID PK 
        string status
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