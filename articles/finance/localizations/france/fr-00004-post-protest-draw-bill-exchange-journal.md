--- 
title: FR-00004 Post protest draw bill of exchange journal
description: Learn about the steps of protesting bill of exchange for legal entities whose primary address is in France with a process using the FRSI demo data company.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User
ms.search.region: France
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransCustBillOfExchange, CustOpenTrans
ms.dyn365.ops.version: Version 7.0.0 
---

# FR-00004 Post protest draw bill of exchange journal

[!include [banner](../../includes/banner.md)]

This procedure walks you through the steps of protesting bill of exchange.

This procedure was created using the demo data company FRSI. 

This functionality is available for legal entities whose primary address is in France.

You should have a role of Accounts receivables clerk to complete this procedure.



1. Go to Accounts receivable > Payments > Bill of exchange > Protest bill of exchange journal.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, enter or select a value.
5. In the list, click the link in the selected row.
    * Select "LitigeEAR"  
6. Click Lines.
7. In the list, mark the selected row.
8. In the Account field, specify the values 'FR_SI_0001'.
9. Click Settle transactions.
10. In the list, mark the selected row.
    * Mark the most recently posted draw bill of exchange journal  
11. Select the Mark check box.
12. Click OK.
13. Click Post.
14. Go to Accounts receivable > Inquiries and reports > Payments > Bill of exchange journal.
    * Verify that Status for the newly posted journal should be Protested. If yes, the process is complete  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]