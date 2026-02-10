
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

## 4. Data Entity Inventory

| Domain | Entity Name | Type | Record Type | Description | Related Entity | Key |
|------|-------------|------|-------------|-------------|----------------|-----|
| Customers & Parties | CustCustomerV3Staging | Native | Customers | Customer master data including account, status, and classification | SalesOrderHeaderV2Staging, SalesInvoiceHeaderV2Staging, GNLNCustTransStaging | CUSTOMERACCOUNT |
| Customers & Parties | CustCustomerGroupEntityStaging | Native | Customers | Customer group definitions for segmentation and pricing | CustCustomerV3Staging | CUSTOMERGROUPID |
| Customers & Parties | DirPartyV2Staging | Native | Global | Core party records shared across customers, vendors, and workers | CustCustomerV3Staging, VendVendorV2Staging, HcmWorkerStaging | PARTYNUMBER |
| Customers & Parties | DirPartyContactV3Staging | Native | Contacts | Contact details such as phone numbers and emails linked to parties | DirPartyV2Staging | PARTYNUMBER |
| Customers & Parties | CustElectronicAddressStaging | Native | Customers | Electronic contact information (emails) | CustCustomerV3Staging | PARTYNUMBER |
| Customers & Parties | smmContactPersonV2Staging | Native | CRM | Named contact persons for customers and vendors | DirPartyV2Staging | PARTYNUMBER |
| Sales | SalesOrderHeaderV2Staging | Native | Sales | Sales order headers representing customer agreements | SalesOrderLineV2Staging, SalesOrderHeaderChargeV2Staging | SALESORDERNUMBER |
| Sales | SalesOrderLineV2Staging | Native | Sales | Line-level detail for sales orders | SalesOrderHeaderV2Staging, EcoResReleasedProductV2Staging | SALESORDERNUMBER, ITEMNUMBER |
| Sales | SalesOrderHeaderChargeV2Staging | Native | Sales | Charges applied at sales order header level | SalesOrderHeaderV2Staging | SALESORDERNUMBER |
| Sales | SalesChargeStaging | Native | Sales | Sales charge definitions and values | SalesOrderHeaderV2Staging, SalesInvoiceHeaderV2Staging | CHARGECODE |
| Sales | SalesInvoiceHeaderV2Staging | Native | Sales | Posted customer invoice headers | SalesInvoiceLineV3Staging, CustInvoiceJournalHeaderStaging | INVOICENUMBER |
| Sales | SalesInvoiceLineV3Staging | Native | Sales | Line-level invoice detail | SalesInvoiceHeaderV2Staging, EcoResReleasedProductV2Staging | INVOICENUMBER, ITEMNUMBER |
| Sales | CustInvoiceJournalHeaderStaging | Native | Finance | Posted customer invoice journals | CustInvoiceJournalLineStaging | JOURNALNUM |
| Sales | CustInvoiceJournalLineStaging | Native | Finance | Invoice journal line detail | CustInvoiceJournalHeaderStaging | JOURNALNUM |
| Sales | CustInvoiceTransStaging | Native | Finance | Customer invoice subledger transactions | GNLNCustTransStaging, SalesInvoiceHeaderV2Staging | VOUCHER, INVOICENUMBER |
| Sales | CustPackingSlipTransStaging | Native | Sales | Packing slip (shipment) transactions | SalesOrderHeaderV2Staging | SALESORDERNUMBER |
| Sales | SalesPackingSlipTrackingInformationStaging | Native | Sales | Shipment tracking and logistics data | CustPackingSlipTransStaging | PACKINGSLIPID |
| Sales | ReturnOrderHeaderStaging | Native | Sales | Sales return order headers | ReturnOrderLineStaging | RETURNORDERNUMBER |
| Sales | ReturnOrderLineStaging | Native | Sales | Line-level return order detail | ReturnOrderHeaderStaging | RETURNORDERNUMBER |
| Sales | FreeTextInvoiceStaging | Native | Sales | Invoices not linked to sales orders | GNLNCustTransStaging | INVOICENUMBER |
| Sales | SalesQuotationHeaderV2Staging | Native | Sales | Sales quotations prior to confirmation | CustCustomerV3Staging | QUOTATIONID |
| Sales | SalesTableStaging | Native | Sales | General sales order abstraction | SalesLineStaging | SALESORDERNUMBER |
| Sales | SalesLineStaging | Native | Sales | General sales line abstraction | SalesTableStaging | SALESORDERNUMBER |
| Sales | SalesPriceAgreementStaging | Native | Sales | Customer and item-specific pricing agreements | CustCustomerV3Staging, EcoResReleasedProductV2Staging | CUSTOMERACCOUNT, ITEMNUMBER |
| Sales | SalesOpenSalesPriceJournalLineV2Staging | Native | Sales | Open sales price journal entries | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Sales | GNLNCustomerInvoiceHeaderChargeStaging | Custom | Sales / Finance | Custom invoice-level charges for reporting | SalesInvoiceHeaderV2Staging | INVOICENUMBER |
| Procurement & Vendors | PurchPurchaseOrderHeaderV2Staging | Native | Procurement | Purchase order headers | PurchPurchaseOrderLineV2Staging | PURCHASEORDERNUMBER |
| Procurement & Vendors | PurchPurchaseOrderLineV2Staging | Native | Procurement | Purchase order line detail | PurchPurchaseOrderHeaderV2Staging, EcoResReleasedProductV2Staging | PURCHASEORDERNUMBER, ITEMNUMBER |
| Procurement & Vendors | VendProductReceiptHeaderStaging | Native | Procurement | Vendor product receipt headers | VendProductReceiptLineStaging | PRODUCTRECEIPTID |
| Procurement & Vendors | VendProductReceiptLineStaging | Native | Procurement | Vendor product receipt lines | VendProductReceiptHeaderStaging | PRODUCTRECEIPTID |
| Procurement & Vendors | VendorInvoiceHeaderStaging | Native | Finance | Posted vendor invoice headers | VendorInvoiceLineStaging | INVOICENUMBER |
| Procurement & Vendors | VendorInvoiceLineStaging | Native | Finance | Vendor invoice line detail | VendorInvoiceHeaderStaging | INVOICENUMBER |
| Procurement & Vendors | VendorPaymentJournalHeaderStaging | Native | Finance | Vendor payment journals | VendorPaymentJournalLineStaging | JOURNALNUM |
| Procurement & Vendors | VendorPaymentJournalLineStaging | Native | Finance | Vendor payment journal lines | VendorPaymentJournalHeaderStaging | JOURNALNUM |
| Procurement & Vendors | VendVendorV2Staging | Native | Vendors | Vendor master records | PurchPurchaseOrderHeaderV2Staging | VENDORACCOUNT |
| Procurement & Vendors | VendTransStaging | Native | Finance | Vendor transactions and settlements | VendorInvoiceHeaderStaging | VOUCHER |
| Inventory & Warehousing | InventWarehouseStaging | Native | Inventory | Warehouse master data | InventWarehouseOnHandV2Staging | WAREHOUSEID |
| Inventory & Warehousing | WMSWarehouseLocationStaging | Native | Warehouse | Warehouse locations and bins | InventWarehouseStaging | WAREHOUSEID |
| Inventory & Warehousing | InventorySiteOnHandV2Staging | Native | Inventory | On-hand inventory by site | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventWarehouseOnHandV2Staging | Native | Inventory | On-hand inventory by warehouse | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventWarehouseInventoryStatusOnHandV2Staging | Native | Inventory | Inventory by status | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventTransferOrderHeaderStaging | Native | Inventory | Transfer order headers | InventTransferOrderLineStaging | TRANSFERORDERNUMBER |
| Inventory & Warehousing | InventTransferOrderLineStaging | Native | Inventory | Transfer order line detail | InventTransferOrderHeaderStaging | TRANSFERORDERNUMBER |
| Inventory & Warehousing | InventItemPriceStaging | Native | Inventory | Item cost and pricing | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventItemPriceV2Staging | Native | Inventory | Extended item pricing | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventProductGroupStaging | Native | Inventory | Product group classifications | EcoResReleasedProductV2Staging | ITEMGROUPID |
| Inventory & Warehousing | ItemThresholdSetupBySalesChannel_GNLNStaging | Custom | Inventory / E-commerce | Reserved quantities by sales channel | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Inventory & Warehousing | InventDimMergeITStaging | Custom | Inventory | Harmonized inventory dimensions | InventTransMergeITStaging | INVENTDIMID |
| Inventory & Warehousing | InventTransMergeITStaging | Custom | Inventory | Harmonized inventory transactions | InventTransOriginMergeITStaging | INVENTTRANSID |
| Inventory & Warehousing | InventTransOriginMergeITStaging | Custom | Inventory | Inventory transaction origins | InventTransMergeITStaging | INVENTTRANSID |
| Products | EcoResProductV2Staging | Native | Products | Core product definitions | EcoResReleasedProductV2Staging | PRODUCTNUMBER |
| Products | EcoResReleasedProductV2Staging | Native | Products | Products released to companies | SalesOrderLineV2Staging, PurchPurchaseOrderLineV2Staging | ITEMNUMBER |
| Products | EcoResProductVariantV2Staging | Native | Products | Product variants | EcoResProductV2Staging | PRODUCTNUMBER |
| Products | EcoResReleasedProductVariantV2Staging | Native | Products | Released product variants | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Products | EcoResEveryProductStaging | Native | Products | Unified product view | EcoResProductV2Staging | PRODUCTNUMBER |
| Products | EcoResProductTranslationStaging | Native | Products | Multilingual descriptions | EcoResProductV2Staging | PRODUCTNUMBER |
| Products | EcoResProductBarcodeV2Staging | Native | Products | Product barcodes | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Products | EcoResProductBarcodeV3Staging | Native | Products | Extended barcode definitions | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Products | EcoResProductGlobalTradeItemNumberAssignmentV2Staging | Native | Products | GTIN assignments | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Finance & Accounting | MainAccountStaging | Native | Finance | Chart of accounts | GeneralJournalAccountEntryStaging | MAINACCOUNTID |
| Finance & Accounting | GeneralJournalAccountEntryStaging | Native | Finance | General ledger entries | MainAccountStaging | MAINACCOUNTID |
| Finance & Accounting | GeneralJournalAccountEntryReportingStaging | Native | Finance | Reporting-friendly GL entries | MainAccountStaging | MAINACCOUNTID |
| Finance & Accounting | BusinessDocumentTaxTransactionStaging | Native | Tax | Tax transaction detail | SalesInvoiceHeaderV2Staging, VendorInvoiceHeaderStaging | INVOICENUMBER |
| Finance & Accounting | CustomerAgingDataStorageStaging | Native | Finance | Pre-aggregated AR aging | CustCustomerV3Staging | CUSTOMERACCOUNT |
| Finance & Accounting | GNLNCustTransStaging | Custom | Finance | Customer transactions for aging/open balances | CustCustomerV3Staging | CUSTOMERACCOUNT |
| Financial Dimensions | DimensionAttributeStaging | Native | Finance | Financial dimension definitions | FinancialDimensionValueEntityStaging | DIMENSIONATTRIBUTE |
| Financial Dimensions | FinancialDimensionValueEntityStaging | Native | Finance | Dimension values | DimensionAttributeStaging | DIMENSIONATTRIBUTE |
| Financial Dimensions | MIT_AccountingDistributionStaging | Custom | Finance | Custom accounting distributions | MIT_GeneralJournalEntryStaging | LEDGERVOUCHER |
| Financial Dimensions | MIT_DIMENSIONATTRIBUTEVALUESETStaging | Custom | Finance | Dimension value sets | MIT_DIMENSIONATTRIBUTEVALUESETITEMVIEWStaging | DIMENSIONATTRIBUTEVALUESETID |
| Financial Dimensions | MIT_DIMENSIONATTRIBUTEVALUESETITEMVIEWStaging | Custom | Finance | Flattened dimension sets | MIT_DIMENSIONATTRIBUTEVALUESETStaging | DIMENSIONATTRIBUTEVALUESETID |
| Financial Dimensions | MIT_DIMENSIONATTRIBUTEVALUEGROUPCOMBINATIONStaging | Custom | Finance | Grouped dimension combinations | MIT_DimensionAttributeValueGroupStaging | VALUEGROUPID |
| Financial Dimensions | MIT_DimensionAttributeValueGroupStaging | Custom | Finance | Dimension value groups | MIT_DIMENSIONHIERARCHYStaging | VALUEGROUPID |
| Financial Dimensions | MIT_DIMENSIONHIERARCHYStaging | Custom | Finance | Custom dimension hierarchies | MIT_DIMENSIONHIERARCHYLEVELStaging | HIERARCHYID |
| Financial Dimensions | MIT_DIMENSIONHIERARCHYLEVELStaging | Custom | Finance | Hierarchy levels | MIT_DIMENSIONHIERARCHYLEVELVIEWStaging | HIERARCHYLEVELID |
| Financial Dimensions | MIT_DIMENSIONHIERARCHYLEVELVIEWStaging | Custom | Finance | Hierarchy level views | MIT_DIMENSIONHIERARCHYLEVELStaging | HIERARCHYLEVELID |
| Financial Dimensions | MIT_DimensionAttributeLevelValueStaging | Custom | Finance | Dimension values by hierarchy | MIT_DIMENSIONHIERARCHYLEVELStaging | HIERARCHYLEVELID |
| Financial Dimensions | MIT_InventDimCombinationStaging | Custom | Inventory | Inventory dimension combinations | InventDimMergeITStaging | INVENTDIMID |
| Financial Dimensions | MIT_GeneralJournalEntryStaging | Custom | Finance | Custom journal entries | MIT_AccountingDistributionStaging | LEDGERVOUCHER |
| Human Resources | HcmEmployeeV2Staging | Native | HR | Employee master records | HcmWorkerStaging | PERSONNELNUMBER |
| Human Resources | HcmWorkerStaging | Native | HR | Worker records | DirPartyV2Staging | PARTYNUMBER |
| Legal, Compliance & Trade | GNLNLegalRestrictions_FDD031Staging | Custom | Compliance | Legal and regulatory restrictions | GNLNRestrictionTypes_FDD031Staging | RESTRICTIONID |
| Legal, Compliance & Trade | GNLNProductRestrictionTypes_FDD031Staging | Custom | Compliance | Restriction type catalog | GNLNLegalRestrictions_FDD031Staging | RESTRICTIONTYPEID |
| Legal, Compliance & Trade | GNLNRestrictionTypes_FDD031Staging | Custom | Compliance | Core restriction definitions | GNLNLegalRestrictions_FDD031Staging | RESTRICTIONTYPEID |
| Legal, Compliance & Trade | WHSProductHarmonizedTariffCodeStaging | Native | Trade | Harmonized tariff codes | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Legal, Compliance & Trade | NmbUSAHarmonizeStaging | Native | Trade | US harmonized trade data | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Legal, Compliance & Trade | NmbCANHarmonizeStaging | Native | Trade | Canada harmonized trade data | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Legal, Compliance & Trade | NmbINTHarmonizeStaging | Native | Trade | International harmonized trade data | EcoResReleasedProductV2Staging | ITEMNUMBER |
| Legal, Compliance & Trade | NmbWHSHarmonizedStaging | Native | Trade | Warehouse harmonized trade mappings | EcoResReleasedProductV2Staging | ITEMNUMBER |

---

## 5. Company Scope & Legal Entity Context

The data contained in this database spans **multiple legal entities (companies)** within the Dynamics 365 Finance & Operations environment.

The following companies are represented:

- **WHG**
- **VWD**
- **ARI**
- **SHVT**

Each record in transactional and master data tables is associated with a specific company through the **`DATAAREAID`** field.

### How to Interpret Company-Specific Data

- `DATAAREAID` identifies the **legal entity** to which a record belongs.
- Most analytical queries should **explicitly filter by `DATAAREAID`** to ensure results reflect the intended company.
- When no filter is applied, query results may include **data from multiple companies**, which can lead to overstated totals or mixed operational context.

### Best Practices for Reporting and Analysis

- Always include `DATAAREAID` in:
  - WHERE clauses
  - GROUP BY logic
  - Report-level filters
- Treat `DATAAREAID` as a **mandatory dimension** for financial, sales, inventory, and operational reporting.
- For cross-company analysis, intentionally aggregate across multiple `DATAAREAID` values and clearly label outputs accordingly.

### Example

```sql
SELECT *
FROM SalesInvoiceHeaderV2Staging
WHERE DATAAREAID = 'WHG';
```


End of Document.
