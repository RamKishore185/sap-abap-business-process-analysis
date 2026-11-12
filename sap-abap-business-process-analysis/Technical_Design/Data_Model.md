# Preliminary Data Model

## Business Data Concepts

| Business Object | Information Used |
|---|---|
| Customer / Business Partner | Sold-to, ship-to, and sales-area information |
| Material | Product identifier, description, and units of measure |
| Sales Order Header and Item | Order number, item, customer, material, quantity, and dates |
| Schedule Line | Requested and confirmed schedule quantities/dates |
| Outbound Delivery | Delivery header, item, and processing progress |
| Goods Movement | Goods-issue information relevant to delivery execution |
| Billing Document | Billing reference and billing progress |

## Classic SAP ERP Table References
The following are common classic table references and are provided only as orientation:
- `VBAK` – Sales document header
- `VBAP` – Sales document item
- `VBEP` – Sales document schedule lines
- `LIKP` – Delivery header
- `LIPS` – Delivery item
- `VBRK` – Billing document header
- `VBRP` – Billing document item

The target release may use different recommended data-access approaches. In S/4HANA, review the Business Partner model, released CDS views, APIs, and compatibility guidance.

## Proposed Report Output
- Sales document and item
- Customer and customer description
- Material and material description
- Order quantity and unit
- Confirmed quantity, where available
- Requested delivery date
- Delivery reference
- Billing reference
- Derived display status

## Status Caution
Statuses such as “Pending confirmation,” “Ready for delivery,” “Partially delivered,” and “Completed” are proposed report labels. They must be mapped to authoritative SAP status fields and approved business rules. Do not treat a custom label as an official SAP status.
