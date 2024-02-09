SELECT * FROM [pizza_sales_excel_file.xlsx - pizza_sales]
------------------------------------------------------------------------------------------------------------------------
-------------------------QUARTER PIZZA ORDER AND TOTAL SALES-------------------
                                 SELECT    
                                YEAR(order_date) AS SALESYEAR,
	                            DATEPART(   QUARTER, order_date) AS QUARTERORDERS,
		                       ROUND(SUM(unit_price),2) as MNTHSALES
	                           FROM [pizza_sales_excel_file.xlsx - pizza_sales]
	                           GROUP BY YEAR(order_date), DATEPART(QUARTER,order_date)
	                          ORDER BY SALESYEAR, QUARTERORDERS
--------------------------------------------------------------------------------------------------------------------------

	 ------------------------MONTHLY ORDERS AND SALES---------------------------------------------------
	 
	                       
						                            SELECT       
                                          YEAR(order_date) AS SALESYEAR,
                                                    CASE 
                                               WHEN MONTH(order_date) = 1 THEN 'Januar'
                                               WHEN MONTH(order_date) = 2 THEN 'February'
                                               WHEN MONTH(order_date) = 3 THEN 'March'
                                               WHEN MONTH(order_date) = 4 THEN 'April'
                                               WHEN MONTH(order_date) = 5 THEN 'May'
                                               WHEN MONTH(order_date) = 6 THEN 'June'
                                               WHEN MONTH(order_date) = 7 THEN 'July'
                                               WHEN MONTH(order_date) = 8 THEN 'August'
                                               WHEN MONTH(order_date) = 9 THEN 'September'
                                               WHEN MONTH(order_date) = 10 THEN 'October'
                                               WHEN MONTH(order_date) = 11 THEN 'November'
                                               WHEN MONTH(order_date) = 12 THEN 'December'
                                               END AS MONTHSALES,
                                               ROUND(SUM(unit_price), 2) AS QUSALES
                                               FROM [pizza_sales_excel_file.xlsx - pizza_sales]
                                               GROUP BY YEAR(order_date), MONTH(order_date)
                                               ORDER BY SALESYEAR, MONTHSALES 
----------------------------------------------------------------------------------------------------------------------------
       ---------------------------pizaa category by quantity------------------------                       
							  SELECT DISTINCT pizza_category,
                                 SUM(CAST(quantity AS INT)) AS TotalQuantity
                                 FROM [pizza_sales_excel_file.xlsx - pizza_sales]
                                  GROUP BY pizza_category
                                  ORDER BY pizza_category;
---------------------------------------------------------------------------------------------------------------------------------
       ----------------------      customers with pizza category                             
										  SELECT DISTINCT pizza_category,
                                          SUM(CAST(quantity AS INT)) AS Totalcustomer
                                           FROM [pizza_sales_excel_file.xlsx - pizza_sales]
                                           GROUP BY pizza_category
                                          ORDER BY pizza_category;
------------------------------------------------------------------------------------------------------------------------------
-------------------
                                
