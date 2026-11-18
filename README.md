# Online Shopping System - Use Case Diagram

```mermaid
graph LR
    Customer((Customer))
    Admin((Administrator))
    PG[Payment Gateway]

    subgraph System [Online Shopping System]
        UC1[Create Account]
        UC2[Log In]
        UC3[Browse Products]
        UC4[Search Products]
        UC5[Add to Shopping Cart]
        UC6[Place Order]
        UC7[Pay for Order]
        UC8[Check Product Availability]
        UC9[Calculate Total Price]
        UC10[Retry Payment]
        UC11[Verify Fraud]
        UC12[Manage Product Info]
        UC13[Update Prices]
        UC14[Manage Customer Accounts]
    end

    Customer --> UC1
    Customer --> UC2
    Customer --> UC3
    Customer --> UC4
    Customer --> UC5
    Customer --> UC6
    Customer --> UC7

    UC7 --> PG

    Admin --> UC12
    Admin --> UC13
    Admin --> UC14

    UC6 -.->|include| UC8
    UC6 -.->|include| UC9
    UC6 -.->|include| UC2
    UC10 -.->|extend <br/> (Payment fails)| UC7
    UC11 -.->|extend <br/> (Exceeds value)| UC6
