# OrderReportBAM

BI Report to show PO placed on a supplier, showing per item, quantity originally ordered, quantity received, and quantity ordered by customer during selected period.
Show excess/Shortfall of client order vs our projection (our orders placed on supplier less order from customer)

SELECT     fQuantity, fQtyProcessed, QtyOutstanding, StatusDescription, OrderNum, ExtOrderNum, Code, cDescription, OrderDate, cAccountName
FROM         _bvPurchaseOrdersFull
WHERE     (OrderDate BETWEEN '2018-01-01' AND '2018-02-28')

SELECT     Code, ItemGroup, OrderDate, fQuantity, fQtyProcessed, QtyOutstanding, DueDate, Account, cAccountName, ExtOrderNum, OrderNum, StatusDescription
FROM         _bvSalesOrdersFull
WHERE     (OrderDate BETWEEN CONVERT(DATETIME, '2018-02-01 00:00:00', 102) AND CONVERT(DATETIME, '2018-02-28 00:00:00', 102))
ORDER BY Code, OrderNum
