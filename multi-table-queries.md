#![img_1.png](img_1.png)

#SQL Multi-table Queries    ❓❓❓

##Objectives
    - explain the role of a foreign key
    - query data from multiple tables
    - write database access methods

###In a table the primary key, typically the id will have other keys that point to it. 
So when you find by id, all other key ids (foreign keys) will point to another table and return with it. for example

    id: 1,  //primary key represents the entity
    customerID: 02, //all others describe a property or attribute of primary
    employeeID: 049494 //ids within an id are foreign keys and are primary keys of other tables
    email: 'tmill@mail.com'

when grabbing by id the other foreign keys of name and email point towards primary key of id

such as Primary key of tony miller could contain, height, weight, hair color, finger length, 
favorite foods. THose are all attributes of primary key tony miller. but employeeID, driver's license, 
social security number as all primary keys to other data tables


each table combines refers to each other

    - Customers
    - Categories
    - Employees
    - Order Details
    - Orders
    - Products
    - Shippers
    - Suppliers

will each have their own id that is the primary key and any other referential key is a foreign key

- under customers however 

    CustomerID is primary and name, contactName, Address, etc are all attributes and the data is not 
    a key to another table. it's just simple data
  

So if i wanted to take the shipper id that shows up in Orders I would join them if the id's equal

    Select * 
    FROM orders

gives me:
OrderID	CustomerID	EmployeeID	OrderDate	ShipperID
   - 10248	90	5	1996-07-04	3
   - 10249	81	6	1996-07-05	1
   - 10250	34	4	1996-07-08	2

but when i join the shipperID from shippers with this join 

    Select * 
    FROM Orders
    JOIN Shippers
        on orders.shipperid = shippers.shipperid

this gives me shipper data appended to the list:
OrderID	CustomerID	EmployeeID	OrderDate |	ShipperID	ShipperName	Phone
    
    10248	90	5	1996-07-04	3	      | Federal Shipping	    (503) 555-9931
    10249	81	6	1996-07-05	1	      | Speedy Express	    (503) 555-9831
    10250	34	4	1996-07-08	2	      | United Package	    (503) 555-3199

left of the vertical line is from orders right is shippers


To simplify this logic we employ aliases

    Select * 
    FROM Orders O
    JOIN Shippers S
        on O.shipperid = S.shipperid

    Select 
        O.*, S.* 
    FROM Orders O
    JOIN Shippers S
    on o.shipperid = s.shipperid;
    
###this will give same query results

    Select
        o.*, s.shippername
    FROM Orders O
    Join Shippers S
    on o.shipperid = s.shipperid;

###makes only the shipper name append to the table 

    SELECT 
        O.orderid, customerid, s.shippername
    FROM Orders O
    Join Shippers S
    ON o.shipperid = s.shipperid;

###returns only three columns. orderID, customerID, shipperName

     SELECT 
        O.orderid, customerid, s.shippername
    FROM Orders O
    Join Shippers S
    ON O.shipperid = S.shipperid
    WHERE s.shippername = "Federal Shipping";

##returns the same info but only where the shippername is Federal Shipping

     SELECT 
        O.orderid, o.customerid, employeeid, orderdate, s.shippername, c.*
    FROM Orders O
    Join Shippers S
    ON O.shipperid = S.shipperid
    JOIN customers c
    ON o.customerid = c.customerid

returns 

    - Result:
Number of Records: 149
OrderID	CustomerID	EmployeeID	OrderDate	ShipperName	CustomerName	ContactName	Address	City	PostalCode	Country
10248	90	5	1996-07-04	Federal Shipping	Wilman Kala	Matti Karttunen	Keskuskatu 45	Helsinki	21240	Finland
10249	81	6	1996-07-05	Speedy Express	Tradição Hipermercados	Anabela Domingues	Av. Inês de Castro, 414	São Paulo	05634-030	Brazil
10250	34	4	1996-07-08	United Package	Hanari Carnes	Mario Pontes	Rua do Paço, 67	Rio de Janeiro	05454-876	Brazil
10251	84	3	1996-07-08	Speedy Express	Victuailles en stock	Mary Saveley	2, rue du Commerce	Lyon	69004	France
10252	76	4	1996-07-09	United Package	Suprêmes délices	Pascale Cartrain	Boulevard Tirou, 255	Charleroi	B-6000	Belgium
10253	34	3	1996-07-10	United Package	Hanari Carnes	Mario Pontes	Rua do Paço, 67	Rio de Janeiro	05454-876	Brazil
10254	14	5	1996-07-11	United Package	Chop-suey Chinese	Yang Wang	Hauptstr. 29	Bern	3012	Switzerland
10255	68	9	1996-07-12	Federal Shipping	Richter Supermarkt	Michael Holz	Grenzacherweg 237	Genève	1203	Switzerland

     SELECT 
        O.orderid, customername, e.employeeid, s.shippername, e.firstname, e.lastname
    FROM Orders O
    Join Shippers S
    ON O.shipperid = S.shipperid
    Join Customers c
    on o.customerid = c.customerid
    Join employees e
    ON o.employeeid = e.employeeid;


###but i end up with two name columns.... how do we concat? with || notation () and alias

     SELECT 
        O.orderid, customername, (e.firstname || " " || e.lastname) as name, s.shippername
    FROM Orders O
    Join Shippers S
    ON O.shipperid = S.shipperid
    Join Customers c
    on o.customerid = c.customerid
    Join employees e
    ON o.employeeid = e.employeeid;

##Group by with count (aggregating)

    SELECT 
	o.orderid, s.shippername, count(o.orderid) as ordersPlaced
    FROM Orders o
    Join Shippers s
    ON o.shipperid = s.shipperid
    GROUP BY s.shipperid;


##We have been using a standard join to accomplish out joins up until now. But if we want to find a value that exists outside the vision of the vesica piscis how would we accomplish this? 

###By using left or right join. this is based on the order of which the tables are put together.

    left being from right being the join

so how do you find an employee who maybe doesn't have an id using this method

       SELECT 
        O.orderid, (e.firstname || " " || e.lastname) as "Employee Name"
    FROM employees e
    Left Join orders o
    ON o.employeeid = e.employeeid;

returns full list in order but produces adam west with a null value in employee id

SELECT
o.orderid, (e.firstname || " " || e.lastname) as Employee_Name, count(e.employeeid) as orders
FROM employees e
left join orders o
ON o.employeeid = e.employeeid
Group by e.employeeid;


Right join describes table two

#DO NOT EVER set your knex without running SQL queries first. EVER 🥺

![img_5.png](img_5.png)






  




