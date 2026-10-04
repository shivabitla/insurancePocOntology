# Insurance Policy Sales Schema

```mermaid
erDiagram
    DimAgent ||--o{ FactPolicySales : soldBy
    DimCustomer ||--o{ FactPolicySales : purchasedBy
    DimProduct ||--o{ FactPolicySales : covers
    DimCarrier ||--o{ FactPolicySales : underwrittenBy
    DimDate ||--o{ FactPolicySales : soldOn

    DimAgent {
        int AgentKey PK
        string AgentID
        string AgentName
        string AgentLocation
    }

    DimCustomer {
        int CustomerKey PK
        string CustomerID
        string CustomerName
        int Phone
        string Address
        string State
        string Region
    }

    DimProduct {
        int ProductKey PK
        string ProductID
        string ProductName
        string ProductCategory
    }

    DimCarrier {
        int CarrierKey PK
        string CarrierID
        string CarrierName
        string HeadquartersState
        string AMBestRating
    }

    DimDate {
        int DateKey PK
        datetime Date
        int CalendarYear
        string Quarter
        int MonthNumber
        string MonthName
    }

    FactPolicySales {
        int PolicySaleKey PK
        string PolicyNumber
        int SaleDateKey FK
        int AgentKey FK
        int CustomerKey FK
        int ProductKey FK
        int CarrierKey FK
        decimal AnnualPremium
        decimal CoverageAmount
        decimal CommissionAmount
        string PolicyStatus
        string TransactionType
    }
```

Each fact row represents a policy issuance or renewal transaction. Dimension keys are referenced by `FactPolicySales`; each dimension can relate to many policy transactions.
