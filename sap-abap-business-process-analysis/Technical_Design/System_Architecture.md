# Preliminary System Architecture

## Architecture Principle
Use standard SAP capabilities for transactional processing. Add custom ABAP only for a confirmed reporting or visibility gap.

## Logical Layers

### 1. Presentation Layer
- SAP user interface used by sales, warehouse, and finance users.
- Selection screen for the custom report.
- ALV-style output where supported by the target environment.

### 2. Application Layer
- SAP SD: sales orders, delivery processing, billing, and document flow.
- SAP MM / Inventory Management: material and inventory-related functions.
- Custom ABAP report: `ZSD_ORDER_MONITOR`, intended to be read-only.

### 3. Data and Integration Layer
- Customer / Business Partner and material master data.
- Sales document header, item, and schedule information.
- Outbound delivery, goods movement, and billing information.
- Released CDS views, APIs, or verified data sources appropriate to the SAP release.

## High-Level Flow
1. Sales user enters a sales order.
2. Standard SAP checks master data, pricing, configured blocks, and availability.
3. Eligible order quantities proceed to delivery processing.
4. Warehouse executes picking/packing and posts goods issue.
5. Billing is created according to configured rules.
6. The custom monitor reads relevant information and displays a consolidated status.

## Design Constraints
- Do not directly update standard SAP tables.
- Prefer released CDS views or APIs when appropriate and available.
- Validate all technical objects against the target SAP release.
- Enforce authorization independently of selection-screen visibility.
- Keep report logic read-only and performance-conscious.
