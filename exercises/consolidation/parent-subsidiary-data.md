# Consolidation Exercise Data: Crescent Group

> This is fictional data for educational purposes only.
> Used in Exercise 11: Multi-Entity Consolidation with Intercompany Elimination.

---

## 1. Parent Entity — Crescent Textiles (Pvt) Ltd

### Income Statement (Year ended 30 June 2025)

| Line Item                                 | Amount (PKR '000) |
| ----------------------------------------- | ----------------- |
| Revenue — external                        | 489,000           |
| Revenue — intercompany (to Karachi Foods) | 15,000            |
| **Total revenue**                         | **504,000**       |
| Cost of goods sold — external             | (296,000)         |
| Cost of goods sold — intercompany         | (11,250)          |
| **Gross profit**                          | **196,750**       |
| Distribution costs                        | (24,400)          |
| Administrative expenses                   | (39,200)          |
| Finance costs                             | (9,950)           |
| **Profit before tax**                     | **123,200**       |
| Income tax expense                        | (35,728)          |
| **Profit for the year**                   | **87,472**        |

### Balance Sheet (As at 30 June 2025)

| Line Item                                          | Amount (PKR '000) |
| -------------------------------------------------- | ----------------- |
| **Non-current assets**                             |                   |
| Property, plant and equipment (net)                | 124,000           |
| Right-of-use assets (net)                          | 5,700             |
| Intangible assets (net)                            | 800               |
| Investment in subsidiary (Karachi Foods — at cost) | 40,000            |
| Intercompany loan receivable (Karachi Foods)       | 8,000             |
| **Total non-current assets**                       | **178,500**       |
| **Current assets**                                 |                   |
| Inventory                                          | 45,800            |
| Trade receivables — external                       | 36,200            |
| Trade receivables — intercompany (Karachi Foods)   | 2,200             |
| Cash and cash equivalents                          | 12,500            |
| Other current assets                               | 4,800             |
| **Total current assets**                           | **101,500**       |
| **Total assets**                                   | **280,000**       |
|                                                    |                   |
| **Equity**                                         |                   |
| Share capital                                      | 50,000            |
| Share premium                                      | 10,000            |
| Retained earnings                                  | 63,472            |
| **Total equity**                                   | **123,472**       |
| **Non-current liabilities**                        |                   |
| Long-term bank loans                               | 45,000            |
| Lease liabilities (non-current)                    | 4,200             |
| Deferred tax liability                             | 8,400             |
| Employee benefit obligations                       | 5,600             |
| **Total non-current liabilities**                  | **63,200**        |
| **Current liabilities**                            |                   |
| Trade payables                                     | 28,700            |
| Current portion of long-term loans                 | 15,000            |
| Lease liabilities (current)                        | 2,000             |
| Accrued expenses                                   | 6,400             |
| Tax payable                                        | 14,200            |
| Other current liabilities                          | 27,028            |
| **Total current liabilities**                      | **93,328**        |
| **Total equity and liabilities**                   | **280,000**       |

---

## 2. Subsidiary Entity — Karachi Foods (Pvt) Ltd

### Income Statement (Year ended 30 June 2025)

| Line Item                                                            | Amount (PKR '000) |
| -------------------------------------------------------------------- | ----------------- |
| Revenue — external                                                   | 200,000           |
| Revenue — intercompany                                               | 0                 |
| **Total revenue**                                                    | **200,000**       |
| Cost of goods sold — external                                        | (123,000)         |
| Cost of goods sold — intercompany (purchases from Crescent Textiles) | (15,000)          |
| **Gross profit**                                                     | **62,000**        |
| Distribution costs                                                   | (14,500)          |
| Administrative expenses                                              | (21,600)          |
| Management fee to parent                                             | (2,400)           |
| Finance costs — external                                             | (3,540)           |
| Finance costs — intercompany (loan from parent)                      | (1,760)           |
| **Profit before tax**                                                | **18,200**        |
| Income tax expense                                                   | (5,278)           |
| **Profit for the year**                                              | **12,922**        |

### Balance Sheet (As at 30 June 2025)

| Line Item                                         | Amount (PKR '000) |
| ------------------------------------------------- | ----------------- |
| **Non-current assets**                            |                   |
| Property, plant and equipment (net)               | 32,000            |
| **Total non-current assets**                      | **32,000**        |
| **Current assets**                                |                   |
| Inventory — external sourced                      | 14,200            |
| Inventory — from Crescent Textiles (intercompany) | 4,000             |
| Trade receivables                                 | 18,600            |
| Cash and cash equivalents                         | 5,200             |
| Other current assets                              | 2,500             |
| **Total current assets**                          | **44,500**        |
| **Total assets**                                  | **76,500**        |
|                                                   |                   |
| **Equity**                                        |                   |
| Share capital                                     | 40,000            |
| Retained earnings                                 | 10,000            |
| **Total equity**                                  | **50,000**        |
| **Non-current liabilities**                       |                   |
| Long-term bank loans                              | 8,000             |
| Deferred tax liability                            | 1,200             |
| **Total non-current liabilities**                 | **9,200**         |
| **Current liabilities**                           |                   |
| Trade payables — external                         | 6,100             |
| Trade payables — intercompany (Crescent Textiles) | 2,200             |
| Intercompany loan payable (to Crescent Textiles)  | 8,000             |
| Intercompany interest payable                     | 1,000             |
| **Total current liabilities**                     | **17,300**        |
| **Total equity and liabilities**                  | **76,500**        |

---

## 3. Intercompany Transactions to Eliminate

| #   | Transaction                             | Parent Account                       | Subsidiary Account          | Amount (PKR '000) | Elimination Entry                            |
| --- | --------------------------------------- | ------------------------------------ | --------------------------- | ----------------- | -------------------------------------------- |
| 1   | **Investment in subsidiary**            | Investment in subsidiary (Dr 40,000) | Share capital (Cr 40,000)   | 40,000            | Dr Share capital / Cr Investment             |
| 2   | **Intercompany loan**                   | Loan receivable (Dr 8,000)           | Loan payable (Cr 8,000)     | 8,000             | Dr Loan payable / Cr Loan receivable         |
| 3   | **Intercompany trading — revenue/COGS** | Revenue (Cr 15,000)                  | COGS (Dr 15,000)            | 15,000            | Dr Revenue 15,000 / Cr COGS 15,000           |
| 4   | **Intercompany receivable/payable**     | Trade receivable (Dr 2,200)          | Trade payable (Cr 2,200)    | 2,200             | Dr Trade payable / Cr Trade receivable       |
| 5   | **Management fee**                      | Admin income (implied in revenue)    | Admin expense (Dr 2,400)    | 2,400             | Dr Revenue 2,400 / Cr Admin expense 2,400    |
| 6   | **Intercompany interest**               | Finance income (implied)             | Finance cost (Dr 1,760)     | 1,760             | Dr Finance income / Cr Finance cost          |
| 7   | **Intercompany interest accrual**       | Interest receivable (implied)        | Interest payable (Cr 1,000) | 1,000             | Dr Interest payable / Cr Interest receivable |

---

## 4. Consolidation Adjustments

### Adjustment A: Unrealised Profit in Inventory (URP)

The subsidiary holds PKR 4,000,000 of inventory purchased from the parent. The parent's gross margin on intercompany sales is **25%** (sells at PKR 15,000 with cost of PKR 11,250).

**Unrealised profit** = PKR 4,000 x 25% = **PKR 1,000**

| Entry                                           | Debit (PKR '000) | Credit (PKR '000) |
| ----------------------------------------------- | ---------------- | ----------------- |
| Cost of goods sold (increase consolidated COGS) | 1,000            |                   |
| Inventory (reduce subsidiary closing inventory) |                  | 1,000             |

**Effect:** Consolidated gross profit decreases by PKR 1,000. Consolidated inventory decreases by PKR 1,000. This adjustment reverses in the following year when the goods are sold to an external customer.

### Adjustment B: Deferred Tax on URP

The unrealised profit elimination creates a temporary difference. Tax effect at 29%:

**Deferred tax asset** = PKR 1,000 x 29% = **PKR 290**

| Entry                       | Debit (PKR '000) | Credit (PKR '000) |
| --------------------------- | ---------------- | ----------------- |
| Deferred tax asset          | 290              |                   |
| Income tax expense (reduce) |                  | 290               |

---

## 5. Consolidation Workings Summary

| Line Item              | Parent (PKR '000) | Subsidiary (PKR '000) | Eliminations (PKR '000) | Consolidated (PKR '000) |
| ---------------------- | ----------------- | --------------------- | ----------------------- | ----------------------- |
| **Revenue**            | 504,000           | 200,000               | (17,400)                | 686,600                 |
| **COGS**               | (307,250)         | (138,000)             | 14,000                  | (431,250)               |
| **Gross profit**       | 196,750           | 62,000                | (3,400)                 | 255,350                 |
| **Operating expenses** | (63,600)          | (38,500)              | 2,400                   | (99,700)                |
| **Finance costs**      | (9,950)           | (5,300)               | 1,760                   | (13,490)                |
| **PBT**                | 123,200           | 18,200                | 760                     | 142,160                 |
| **Tax**                | (35,728)          | (5,278)               | 290                     | (40,716)                |
| **Profit for year**    | 87,472            | 12,922                | 1,050                   | 101,444                 |

| Balance Sheet         | Parent (PKR '000) | Subsidiary (PKR '000) | Eliminations (PKR '000) | Consolidated (PKR '000) |
| --------------------- | ----------------- | --------------------- | ----------------------- | ----------------------- |
| **PPE (net)**         | 130,500           | 32,000                | —                       | 162,500                 |
| **Investment in sub** | 40,000            | —                     | (40,000)                | —                       |
| **Interco loan rec**  | 8,000             | —                     | (8,000)                 | —                       |
| **Inventory**         | 45,800            | 18,200                | (1,000)                 | 63,000                  |
| **Trade receivables** | 38,400            | 18,600                | (2,200)                 | 54,800                  |
| **Cash**              | 12,500            | 5,200                 | —                       | 17,700                  |
| **Other current**     | 4,800             | 2,500                 | 290                     | 7,590                   |
| **Total assets**      | 280,000           | 76,500                | (50,910)                | 305,590                 |
| **Share capital**     | 50,000            | 40,000                | (40,000)                | 50,000                  |
| **Reserves**          | 73,472            | 10,000                | 1,050                   | 84,522                  |
| **Total equity**      | 123,472           | 50,000                | (38,950)                | 134,522                 |
| **Non-current liab**  | 63,200            | 9,200                 | —                       | 72,400                  |
| **Current liab**      | 93,328            | 17,300                | (11,960)                | 98,668                  |
| **Total E+L**         | 280,000           | 76,500                | (50,910)                | 305,590                 |

---

## 6. Notes for Students

1. **Start with Elimination 1** (investment vs. share capital) — this is the fundamental consolidation entry.
2. **Work through eliminations 2-7 systematically** — each removes a double-count.
3. **Adjustment A (URP) is the most complex** — understand WHY the profit is unrealised (goods not yet sold to a third party).
4. **Adjustment B (deferred tax on URP)** is frequently missed by junior accountants. The tax authorities tax the subsidiary on its profit including the intercompany purchase — but the group has eliminated that profit. This creates a temporary difference.
5. **Verify your consolidated balance sheet balances** — total assets must equal total equity plus total liabilities.
6. **The management fee and interest eliminations** are easy to miss because they may not be separately disclosed in the parent's accounts.
