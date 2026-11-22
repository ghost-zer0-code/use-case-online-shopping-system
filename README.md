flowchart LR
    Customer(["Customer"])
    PaymentGateway(["Payment Gateway"])
    Administrator(["Administrator"])

    subgraph OnlineShoppingSystem["Online Shopping System"]
        CreateAccount(["Create Account"])
        LogIn(["Log In"])
        BrowseProducts(["Browse Products"])
        SearchProducts(["Search Products"])
        AddToCart(["Add Products to Shopping Cart"])
        PlaceOrder(["Place Order"])
        CheckAvailability(["Check Product Availability"])
        CalculateTotal(["Calculate Total Order Price"])
        FraudVerification(["Perform Fraud Verification"])
        PayForOrder(["Pay for Order"])
        RetryPayment(["Retry Payment"])
        ManageProductInfo(["Manage Product Information"])
        UpdatePrices(["Update Prices"])
        ManageCustomerAccounts(["Manage Customer Accounts"])
    end

    Customer --- CreateAccount
    Customer --- LogIn
    Customer --- BrowseProducts
    Customer --- SearchProducts
    Customer --- AddToCart
    Customer --- PlaceOrder
    Customer --- PayForOrder

    PaymentGateway --- PayForOrder

    Administrator --- ManageProductInfo
    Administrator --- UpdatePrices
    Administrator --- ManageCustomerAccounts

    PlaceOrder -.->|"&laquo;include&raquo;"| CheckAvailability
    PlaceOrder -.->|"&laquo;include&raquo;"| CalculateTotal

    FraudVerification -.->|"&laquo;extend&raquo;: order exceeds specified value"| PlaceOrder
    RetryPayment -.->|"&laquo;extend&raquo;: payment fails"| PayForOrder
