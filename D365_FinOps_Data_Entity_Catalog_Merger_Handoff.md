
# D365 Finance & Operations  
## Greenlane Database - Data Entity Catalog

---

## 1. Purpose of This Document

This document provides a business-oriented overview of the data entities included in the Greenlane Dynamics 365 Finance & Operations (FinOps) database delivered as part of the company merger.

The objective is to help the receiving organization understand:
- What type of business data is available
- What each data entity represents
- How entities relate to one another
- Which entities are native to FinOps and which are custom extensions

This document is intentionally non-technical and designed for management, finance, operations, and business intelligence users.

---

## 2. Scope & Design Notes

- The database contains a curated subset of FinOps Data Entities.
- It is intended for reporting, analytics, and operational visibility.
- Data is historical and transactional in nature.
- Custom entities exist to simplify reporting, enforce compliance, and support business-specific logic.
- Custom entities are clearly identified.

---

## 3. Customers & Parties

### CustCustomerV3Staging
Native | Customers  
Customer master data including account, status, and classification.  
Related to sales orders, invoices, and customer transactions.

### CustCustomerGroupEntityStaging
Native | Customers  
Customer group definitions used for segmentation, pricing, and reporting.

### DirPartyV2Staging
Native | Global  
Core party records shared across customers, vendors, and workers.

### DirPartyContactV3Staging
Native | Contacts  
Contact details such as phone numbers and emails linked to parties.

### CustElectronicAddressStaging
Native | Customers  
Electronic addresses (emails) associated with customers.

### smmContactPersonV2Staging
Native | CRM  
Named contact persons linked to customer and vendor parties.

---

## 4. Sales (Order to Cash)

### SalesOrderHeaderV2Staging
Native | Sales  
Sales order headers representing commercial agreements with customers.

### SalesOrderLineV2Staging
Native | Sales  
Line-level detail for items or services sold on sales orders.

### SalesOrderHeaderChargeV2Staging
Native | Sales  
Charges applied at the sales order header level.

### SalesChargeStaging
Native | Sales  
Charge definitions and values applied to sales documents.

### SalesInvoiceHeaderV2Staging
Native | Sales  
Posted customer invoice headers.

### SalesInvoiceLineV3Staging
Native | Sales  
Line-level invoice detail derived from sales orders.

### CustInvoiceJournalHeaderStaging
Native | Finance  
Posted customer invoice journals.

### CustInvoiceJournalLineStaging
Native | Finance  
Invoice journal line detail.

### CustInvoiceTransStaging
Native | Finance  
Customer invoice transactions used for subledger reporting.

### CustPackingSlipTransStaging
Native | Sales  
Packing slip transactions representing shipment activity.

### SalesPackingSlipTrackingInformationStaging
Native | Sales  
Tracking and logistics information for shipped sales orders.

### ReturnOrderHeaderStaging
Native | Sales  
Sales return order headers.

### ReturnOrderLineStaging
Native | Sales  
Line-level detail for return orders.

### FreeTextInvoiceStaging
Native | Sales  
Invoices not tied to sales orders.

### SalesQuotationHeaderV2Staging
Native | Sales  
Sales quotations prior to order confirmation.

### SalesTableStaging
Native | Sales  
General sales order table abstraction.

### SalesLineStaging
Native | Sales  
General sales line abstraction.

### SalesPriceAgreementStaging
Native | Sales  
Customer and item-specific pricing agreements.

### SalesOpenSalesPriceJournalLineV2Staging
Native | Sales  
Open sales price journal entries.

### GNLNCustomerInvoiceHeaderChargeStaging
Custom | Sales / Finance  
Custom invoice-level charges designed to simplify reporting and separate logic from native charges.

---

## 5. Procurement & Vendors

### PurchPurchaseOrderHeaderV2Staging
Native | Procurement  
Purchase order headers representing vendor commitments.

### PurchPurchaseOrderLineV2Staging
Native | Procurement  
Line-level detail for purchase orders.

### VendProductReceiptHeaderStaging
Native | Procurement  
Vendor product receipt headers.

### VendProductReceiptLineStaging
Native | Procurement  
Line-level received quantities from vendors.

### VendorInvoiceHeaderStaging
Native | Finance  
Posted vendor invoice headers.

### VendorInvoiceLineStaging
Native | Finance  
Line-level vendor invoice detail.

### VendorPaymentJournalHeaderStaging
Native | Finance  
Vendor payment journal headers.

### VendorPaymentJournalLineStaging
Native | Finance  
Vendor payment journal lines.

### VendVendorV2Staging
Native | Vendors  
Vendor master records.

### VendTransStaging
Native | Finance  
Vendor transaction records for payables and settlements.

---

## 6. Inventory, Warehousing & Transfers

### InventWarehouseStaging
Native | Inventory  
Warehouse master data.

### WMSWarehouseLocationStaging
Native | Warehouse  
Warehouse locations and bins.

### InventorySiteOnHandV2Staging
Native | Inventory  
On-hand inventory by site.

### InventWarehouseOnHandV2Staging
Native | Inventory  
On-hand inventory by warehouse.

### InventWarehouseInventoryStatusOnHandV2Staging
Native | Inventory  
Inventory quantities by warehouse and status.

### InventTransferOrderHeaderStaging
Native | Inventory  
Transfer orders between warehouses.

### InventTransferOrderLineStaging
Native | Inventory  
Line-level transfer order detail.

### InventItemPriceStaging
Native | Inventory  
Item cost and pricing data.

### InventItemPriceV2Staging
Native | Inventory  
Extended item pricing and cost records.

### InventProductGroupStaging
Native | Inventory  
Product group classifications.

### ItemThresholdSetupBySalesChannel_GNLNStaging
Custom | Inventory / E-commerce  
Stores reserved quantities by sales channel to calculate sellable inventory.

### InventDimMergeITStaging
Custom | Inventory  
Custom inventory dimension harmonization for reporting.

### InventTransMergeITStaging
Custom | Inventory  
Harmonized inventory transactions.

### InventTransOriginMergeITStaging
Custom | Inventory  
Inventory transaction origins for merge and reporting alignment.

---

## 7. Products & Product Master

### EcoResProductV2Staging
Native | Products  
Core product definitions.

### EcoResReleasedProductV2Staging
Native | Products  
Products released to specific legal entities.

### EcoResProductVariantV2Staging
Native | Products  
Product variants such as size or color.

### EcoResReleasedProductVariantV2Staging
Native | Products  
Released variants available for transactions.

### EcoResEveryProductStaging
Native | Products  
Unified product view across types.

### EcoResProductTranslationStaging
Native | Products  
Multilingual product descriptions.

### EcoResProductBarcodeV2Staging
Native | Products  
Product barcodes.

### EcoResProductBarcodeV3Staging
Native | Products  
Extended barcode definitions.

### EcoResProductGlobalTradeItemNumberAssignmentV2Staging
Native | Products  
GTIN assignments for trade compliance.

---

## 8. Finance & Accounting

### MainAccountStaging
Native | Finance  
Chart of accounts master data.

### GeneralJournalAccountEntryStaging
Native | Finance  
General ledger journal entries.

### GeneralJournalAccountEntryReportingStaging
Native | Finance  
Reporting-friendly ledger entries.

### BusinessDocumentTaxTransactionStaging
Native | Tax  
Tax transaction details.

### CustomerAgingDataStorageStaging
Native | Finance  
Pre-aggregated customer aging data.

### GNLNCustTransStaging
Custom | Finance  
Customer transactions optimized for open balances and aging reports.

---

## 9. Financial Dimensions & Accounting Framework (Custom)

### DimensionAttributeStaging
Native | Finance  
Financial dimension definitions.

### FinancialDimensionValueEntityStaging
Native | Finance  
Dimension values.

### MIT_AccountingDistributionStaging
Custom | Finance  
Custom accounting distribution framework ensuring accurate GL postings.

### MIT_DIMENSIONATTRIBUTEVALUESETStaging
Custom | Finance  
Dimension value sets used for reporting consistency.

### MIT_DIMENSIONATTRIBUTEVALUESETITEMVIEWStaging
Custom | Finance  
Flattened view of dimension value sets.

### MIT_DIMENSIONATTRIBUTEVALUEGROUPCOMBINATIONStaging
Custom | Finance  
Grouped dimension combinations.

### MIT_DimensionAttributeValueGroupStaging
Custom | Finance  
Dimension value grouping.

### MIT_DIMENSIONHIERARCHYStaging
Custom | Finance  
Custom dimension hierarchy.

### MIT_DIMENSIONHIERARCHYLEVELStaging
Custom | Finance  
Hierarchy levels.

### MIT_DIMENSIONHIERARCHYLEVELVIEWStaging
Custom | Finance  
Hierarchy level views.

### MIT_DimensionAttributeLevelValueStaging
Custom | Finance  
Dimension values by hierarchy level.

### MIT_InventDimCombinationStaging
Custom | Inventory  
Inventory dimension combinations aligned to accounting.

### MIT_GeneralJournalEntryStaging
Custom | Finance  
Custom journal entries aligned to the dimension framework.

---

## 10. Human Resources

### HcmEmployeeV2Staging
Native | HR  
Employee master records.

### HcmWorkerStaging
Native | HR  
Worker records used across HR and operations.

---

## 11. Legal, Compliance & Trade

### GNLNLegalRestrictions_FDD031Staging
Custom | Compliance  
Legal and regulatory restrictions framework.

### GNLNProductRestrictionTypes_FDD031Staging
Custom | Compliance  
Catalog of restriction types.

### GNLNRestrictionTypes_FDD031Staging
Custom | Compliance  
Core restriction definitions.

### WHSProductHarmonizedTariffCodeStaging
Native | Trade  
Harmonized tariff codes by product.

### NmbUSAHarmonizeStaging
Native | Trade  
USA harmonized trade data.

### NmbCANHarmonizeStaging
Native | Trade  
Canada harmonized trade data.

### NmbINTHarmonizeStaging
Native | Trade  
International harmonized trade data.

### NmbWHSHarmonizedStaging
Native | Trade  
Warehouse harmonized trade mappings.

---

## 12. Common Relationship Patterns

- Customer → Sales Order → Invoice → Customer Transactions
- Vendor → Purchase Order → Product Receipt → Vendor Invoice → Vendor Transactions
- Product → Inventory On-Hand → Sales / Procurement
- Dimensions → Accounting Distribution → General Ledger

---

End of Document.
