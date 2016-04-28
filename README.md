# Chinook DB SQL Exercise

## Questions
1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.
2. Provide a query only showing the Customers from Brazil.
3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.
4. Provide a query showing only the Employees who are Sales Agents.
5. Provide a query showing a unique list of billing countries from the Invoice table.
6. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.
7. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.
8. How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?(include both the answers and the queries used to find the answers)
9. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.
10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY
11. Provide a query that includes the track name with each invoice line item.
12. Provide a query that includes the purchased track name AND artist name with each invoice line item.
13. Provide a query that shows the # of invoices per country. HINT: GROUP BY
14. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resulant table.
15. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.
16. Provide a query that shows all Invoices but includes the # of invoice line items.
17. Provide a query that shows total sales made by each sales agent.
18. Which sales agent made the most in sales in 2009? HINT: MAX
19. Which sales agent made the most in sales over all?
20. Provide a query that shows the # of customers assigned to each sales agent.
21. Provide a query that shows the total sales per country. Which country's customers spent the most?
22. Provide a query that shows the most purchased track of 2013.
23. Provide a query that shows the top 5 most purchased tracks over all.
24. Provide a query that shows the top 3 best selling artists.
25. Provide a query that shows the most purchased Media Type.

## Answers
1. SELECT FirstName || " " || LastName, CustomerId, Country FROM Customer WHERE Country != "USA"
2. SELECT FirstName || " " || LastName, Country FROM Customer WHERE Country = "Brazil"
3. SELECT Customer.FirstName || " " || Customer.LastName, Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry FROM Customer INNER JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId WHERE Customer.Country = "Brazil"
4. SELECT Employee.FirstName || " " || Employee.LastName, Employee.Title FROM Employee WHERE Employee.Title = "Sales Support Agent"
5. SELECT DISTINCT BillingCountry FROM Invoice
6. SELECT
Employee.FirstName || " " || Employee.LastName AS [Sales Rep],
Customer.FirstName || " " || Customer.LastName AS [Customer],
Invoice.InvoiceId, Invoice.CustomerId, Invoice.InvoiceDate, Invoice.Total
FROM Invoice
INNER JOIN Customer ON Customer.CustomerId = Invoice.CustomerId
INNER JOIN Employee ON Employee.EmployeeId = Customer.SupportRepId
7. SELECT
Employee.FirstName || " " || Employee.LastName AS [Sales Rep],
Customer.FirstName || " " || Customer.LastName AS [Customer],
Customer.Country,
Invoice.Total AS [Invoice Total]
FROM Invoice
INNER JOIN Customer ON Customer.CustomerId = Invoice.CustomerId
INNER JOIN Employee ON Employee.EmployeeId = Customer.SupportRepId
8. SELECT COUNT(*) FROM Invoice WHERE InvoiceDate LIKE '%2009%' OR InvoiceDate LIKE '%2011%' (249 records in 2009 or 2011)
SELECT SUM(Total) AS [2009 Total Sales] FROM Invoice WHERE InvoiceDate LIKE '%2009%' (2009 Total Sales: 449.46)
SELECT SUM(Total) AS [2011 Total Sales] FROM Invoice WHERE InvoiceDate LIKE '%2011%' (2011 Total Sales: 469.58)
9. 





