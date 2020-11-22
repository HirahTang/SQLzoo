


183. Customers Who Never Order
https://leetcode.com/problems/customers-who-never-order/

 

  

    # Write your MySQL query statement below
    
    # select name from the table 'customers' join 'orders', but those who never order
    # would not show up in the 'after-joined' table
    SELECT Name AS 'Customers' 
    FROM Customers 
    WHERE Id NOT IN 
    (
        SELECT CustomerId 
        FROM Customers 
        JOIN Orders 
        ON (Customers.Id = Orders.CustomerId)
    )



