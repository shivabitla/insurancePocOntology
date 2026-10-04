# Semantic Model Notes

`InsuranceSalesStarSchema` was exported as native TMDL under `semantic-model/`.

This is a separate illustrative model, not a live connection to `InsuranceDataLH`. Its exported `FactPolicySales` partition contains five illustrative records (`POL-10001` through `POL-10005`) and its `DimDate` partition covers 2025. The Lakehouse seed tables instead contain 50 policy transactions dated in 2026. Refresh or replace the model partitions before treating it as synchronized with the Lakehouse.

## Relationships

- `FactPolicySales.AgentKey` -> `DimAgent.AgentKey`
- `FactPolicySales.CustomerKey` -> `DimCustomer.CustomerKey`
- `FactPolicySales.ProductKey` -> `DimProduct.ProductKey`
- `FactPolicySales.CarrierKey` -> `DimCarrier.CarrierKey`
- `FactPolicySales.SaleDateKey` -> `DimDate.DateKey`

## Measures

- `Total Premium`
- `Total Commission`
- `Policy Transactions`
- `Average Premium`
- `Total Coverage`
- `Commission Rate`
- `New Policies`
