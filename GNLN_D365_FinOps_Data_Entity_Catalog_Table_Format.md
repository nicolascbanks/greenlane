
# D365 Finance & Operations  
## Greenlane Database – Data Entity Catalog

---

## 1. Purpose of This Document

This document provides a business-oriented overview of the data entities included in the Greenlane Dynamics 365 Finance & Operations (FinOps) database delivered as part of the data hand-off.

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

## 3. Timeframe

- The data corresponds to records and transactions starting 2021. Data prior to this date can be found in the NetSuite Greenlane and KushCo Archive Databases.

---

## Data Entity Inventory

| Domain | Entity Name | Type | Record Type | Description | Related Entity | Key
|------|-------------|------|-------------|-------------|---------|-----|
| Customers & Parties | CustCustomerV3Staging | Native | Customers | Customer master data including account, status, and classification. Related to sales orders, invoices, and customer transactions. |
| Customers & Parties | CustCustomerGroupEntityStaging | Native | Customers | Customer group definitions used for segmentation, pricing, and reporting. |
| Customers & Parties | DirPartyV2Staging | Native | Global | Core party records shared across customers, vendors, and workers. |
| Customers & Parties | DirPartyContactV3Staging | Native | Contacts | Contact details such as phone numbers and emails linked to parties. |
| Customers & Parties | CustElectronicAddressStaging | Native | Customers | Electronic addresses (emails) associated with customers. |
| Customers & Parties | smmContactPersonV2Staging | Native | CRM | Named contact persons linked to customer and vendor parties. |
| Sales | SalesOrderHeaderV2Staging | Native | Sales | Sales order headers representing commercial agreements with customers. |
| Sales | SalesOrderLineV2Staging | Native | Sales | Line-level detail for items or services sold on sales orders. |
| Sales | SalesOrderHeaderChargeV2Staging | Native | Sales | Charges applied at the sales order header level. |
| Sales | SalesChargeStaging | Native | Sales | Charge definitions and values applied to sales documents. |
| Sales | SalesInvoiceHeaderV2Staging | Native | Sales | Posted customer invoice headers. |
| Sales | SalesInvoiceLineV3Staging | Native | Sales | Line-level invoice detail derived from sales orders. |
| Customers & Parties | CustInvoiceJournalHeaderStaging | Native | Finance | Posted customer invoice journals. |
| Customers & Parties | CustInvoiceJournalLineStaging | Native | Finance | Invoice journal line detail. |
| Customers & Parties | CustInvoiceTransStaging | Native | Finance | Customer invoice transactions used for subledger reporting. |
| Customers & Parties | CustPackingSlipTransStaging | Native | Sales | Packing slip transactions representing shipment activity. |
| Sales | SalesPackingSlipTrackingInformationStaging | Native | Sales | Tracking and logistics information for shipped sales orders. |
| Sales | ReturnOrderHeaderStaging | Native | Sales | Sales return order headers. |
| Sales | ReturnOrderLineStaging | Native | Sales | Line-level detail for return orders. |
| Other / Reference | FreeTextInvoiceStaging | Native | Sales | Invoices not tied to sales orders. |
| Sales | SalesQuotationHeaderV2Staging | Native | Sales | Sales quotations prior to order confirmation. |
| Sales | SalesTableStaging | Native | Sales | General sales order table abstraction. |
| Sales | SalesLineStaging | Native | Sales | General sales line abstraction. |
| Sales | SalesPriceAgreementStaging | Native | Sales | Customer and item-specific pricing agreements. |
| Sales | SalesOpenSalesPriceJournalLineV2Staging | Native | Sales | Open sales price journal entries. |
| Other / Reference | GNLNCustomerInvoiceHeaderChargeStaging | Custom | Sales / Finance | Custom invoice-level charges designed to simplify reporting and separate logic from native charges. |
| Procurement & Vendors | PurchPurchaseOrderHeaderV2Staging | Native | Procurement | Purchase order headers representing vendor commitments. |
| Procurement & Vendors | PurchPurchaseOrderLineV2Staging | Native | Procurement | Line-level detail for purchase orders. |
| Procurement & Vendors | VendProductReceiptHeaderStaging | Native | Procurement | Vendor product receipt headers. |
| Procurement & Vendors | VendProductReceiptLineStaging | Native | Procurement | Line-level received quantities from vendors. |
| Procurement & Vendors | VendorInvoiceHeaderStaging | Native | Finance | Posted vendor invoice headers. |
| Procurement & Vendors | VendorInvoiceLineStaging | Native | Finance | Line-level vendor invoice detail. |
| Procurement & Vendors | VendorPaymentJournalHeaderStaging | Native | Finance | Vendor payment journal headers. |
| Procurement & Vendors | VendorPaymentJournalLineStaging | Native | Finance | Vendor payment journal lines. |
| Procurement & Vendors | VendVendorV2Staging | Native | Vendors | Vendor master records. |
| Procurement & Vendors | VendTransStaging | Native | Finance | Vendor transaction records for payables and settlements. |
| Inventory & Warehousing | InventWarehouseStaging | Native | Inventory | Warehouse master data. |
| Inventory & Warehousing | WMSWarehouseLocationStaging | Native | Warehouse | Warehouse locations and bins. |
| Inventory & Warehousing | InventorySiteOnHandV2Staging | Native | Inventory | On-hand inventory by site. |
| Inventory & Warehousing | InventWarehouseOnHandV2Staging | Native | Inventory | On-hand inventory by warehouse. |
| Inventory & Warehousing | InventWarehouseInventoryStatusOnHandV2Staging | Native | Inventory | Inventory quantities by warehouse and status. |
| Inventory & Warehousing | InventTransferOrderHeaderStaging | Native | Inventory | Transfer orders between warehouses. |
| Inventory & Warehousing | InventTransferOrderLineStaging | Native | Inventory | Line-level transfer order detail. |
| Inventory & Warehousing | InventItemPriceStaging | Native | Inventory | Item cost and pricing data. |
| Inventory & Warehousing | InventItemPriceV2Staging | Native | Inventory | Extended item pricing and cost records. |
| Inventory & Warehousing | InventProductGroupStaging | Native | Inventory | Product group classifications. |
| Inventory & Warehousing | ItemThresholdSetupBySalesChannel_GNLNStaging | Custom | Inventory / E-commerce | Stores reserved quantities by sales channel to calculate sellable inventory. |
| Inventory & Warehousing | InventDimMergeITStaging | Custom | Inventory | Custom inventory dimension harmonization for reporting. |
| Inventory & Warehousing | InventTransMergeITStaging | Custom | Inventory | Harmonized inventory transactions. |
| Inventory & Warehousing | InventTransOriginMergeITStaging | Custom | Inventory | Inventory transaction origins for merge and reporting alignment. |
| Products | EcoResProductV2Staging | Native | Products | Core product definitions. |
| Products | EcoResReleasedProductV2Staging | Native | Products | Products released to specific legal entities. |
| Products | EcoResProductVariantV2Staging | Native | Products | Product variants such as size or color. |
| Products | EcoResReleasedProductVariantV2Staging | Native | Products | Released variants available for transactions. |
| Products | EcoResEveryProductStaging | Native | Products | Unified product view across types. |
| Products | EcoResProductTranslationStaging | Native | Products | Multilingual product descriptions. |
| Products | EcoResProductBarcodeV2Staging | Native | Products | Product barcodes. |
| Products | EcoResProductBarcodeV3Staging | Native | Products | Extended barcode definitions. |
| Products | EcoResProductGlobalTradeItemNumberAssignmentV2Staging | Native | Products | GTIN assignments for trade compliance. |
| Finance & Accounting | MainAccountStaging | Native | Finance | Chart of accounts master data. |
| Finance & Accounting | GeneralJournalAccountEntryStaging | Native | Finance | General ledger journal entries. |
| Finance & Accounting | GeneralJournalAccountEntryReportingStaging | Native | Finance | Reporting-friendly ledger entries. |
| Other / Reference | BusinessDocumentTaxTransactionStaging | Native | Tax | Tax transaction details. |
| Customers & Parties | CustomerAgingDataStorageStaging | Native | Finance | Pre-aggregated customer aging data. |
| Finance & Accounting | GNLNCustTransStaging | Custom | Finance | Customer transactions optimized for open balances and aging reports. |
| Financial Dimensions (Custom Framework) | DimensionAttributeStaging | Native | Finance | Financial dimension definitions. |
| Financial Dimensions (Custom Framework) | FinancialDimensionValueEntityStaging | Native | Finance | Dimension values. |
| Financial Dimensions (Custom Framework) | MIT_AccountingDistributionStaging | Custom | Finance | Custom accounting distribution framework ensuring accurate GL postings. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONATTRIBUTEVALUESETStaging | Custom | Finance | Dimension value sets used for reporting consistency. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONATTRIBUTEVALUESETITEMVIEWStaging | Custom | Finance | Flattened view of dimension value sets. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONATTRIBUTEVALUEGROUPCOMBINATIONStaging | Custom | Finance | Grouped dimension combinations. |
| Financial Dimensions (Custom Framework) | MIT_DimensionAttributeValueGroupStaging | Custom | Finance | Dimension value grouping. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONHIERARCHYStaging | Custom | Finance | Custom dimension hierarchy. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONHIERARCHYLEVELStaging | Custom | Finance | Hierarchy levels. |
| Financial Dimensions (Custom Framework) | MIT_DIMENSIONHIERARCHYLEVELVIEWStaging | Custom | Finance | Hierarchy level views. |
| Financial Dimensions (Custom Framework) | MIT_DimensionAttributeLevelValueStaging | Custom | Finance | Dimension values by hierarchy level. |
| Financial Dimensions (Custom Framework) | MIT_InventDimCombinationStaging | Custom | Inventory | Inventory dimension combinations aligned to accounting. |
| Financial Dimensions (Custom Framework) | MIT_GeneralJournalEntryStaging | Custom | Finance | Custom journal entries aligned to the dimension framework. |
| Human Resources | HcmEmployeeV2Staging | Native | HR | Employee master records. |
| Human Resources | HcmWorkerStaging | Native | HR | Worker records used across HR and operations. |
| Legal, Compliance & Trade | GNLNLegalRestrictions_FDD031Staging | Custom | Compliance | Legal and regulatory restrictions framework. |
| Legal, Compliance & Trade | GNLNProductRestrictionTypes_FDD031Staging | Custom | Compliance | Catalog of restriction types. |
| Other / Reference | GNLNRestrictionTypes_FDD031Staging | Custom | Compliance | Core restriction definitions. |
| Legal, Compliance & Trade | WHSProductHarmonizedTariffCodeStaging | Native | Trade | Harmonized tariff codes by product. |
| Legal, Compliance & Trade | NmbUSAHarmonizeStaging | Native | Trade | USA harmonized trade data. |
| Legal, Compliance & Trade | NmbCANHarmonizeStaging | Native | Trade | Canada harmonized trade data. |
| Legal, Compliance & Trade | NmbINTHarmonizeStaging | Native | Trade | International harmonized trade data. |
| Legal, Compliance & Trade | NmbWHSHarmonizedStaging | Native | Trade | Warehouse harmonized trade mappings. |

---

End of Document.
