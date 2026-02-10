
# Connecting to the FinOps Azure SQL Database via SSMS

This guide walks you through connecting to the provided Azure SQL Database using **SQL Server Management Studio (SSMS)** and running a first sample query against customer invoice headers.

---

## 1. Prerequisites

Before you begin, ensure you have:

- **SQL Server Management Studio (SSMS)** installed  
  Download: https://learn.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms
- Network access to the Azure SQL server. You'll need the **HQ-Legacy-ERP-vnet** VPN installed on your machine to access the database
- Valid database credentials (provided separately)

---

## 2. Connection Details

Use the following settings in SSMS:

- **Server type:** Database Engine  
- **Server name:** `azuresqlsrv01.database.windows.net`  
- **Authentication:** SQL Server Authentication  
- **Login:** `TBD`  
- **Password:** `TBD`  

> ⚠️ Credentials should be shared securely.

---

## 3. Step-by-Step: Connecting with SSMS

1. Open **SQL Server Management Studio (SSMS)**.
2. In the **Connect to Server** window, enter:
   - Server type: **Database Engine**
   - Server name: `azuresqlsrv01.database.windows.net`
   - Authentication: **SQL Server Authentication**
   - Login: `TBD`
   - Password: `TBD`
3. Click **Connect**.
4. If prompted, allow your IP address through the Azure SQL firewall.
5. Once connected, expand the server node in **Object Explorer**.

---

## 4. Selecting the Database

Ensure you are using the correct database before querying.

```sql
USE [YourDatabaseNameHere];
GO
```

---

## 5. Sample Query: Customer Invoice Headers

```sql
SELECT TOP 50
    INVOICENUMBER,
    INVOICEDATE,
    INVOICEACCOUNT,
    CURRENCYCODE,
    TOTALINVOICEAMOUNT,
    DATAAREAID
FROM SalesInvoiceHeaderV2Staging
ORDER BY INVOICEDATE DESC;
```

### Query Purpose
- Retrieves recent customer invoices
- Useful for validating connectivity and data availability

---

## 6. Example: Join to Invoice Lines

```sql
SELECT
    h.INVOICENUMBER,
    h.INVOICEDATE,
    l.ITEMID,
    l.QTY,
    l.LINEAMOUNT
FROM SalesInvoiceHeaderV2Staging h
JOIN SalesInvoiceLineV3Staging l
    ON l.INVOICENUMBER = h.INVOICENUMBER
WHERE h.INVOICEDATE >= '2024-01-01';
```

---

## 7. Best Practices

- Filter by `DATAAREAID` in multi-company environments.
- Use `TOP` when exploring large tables.
- Treat this database as read-only.

---

End of Document.
