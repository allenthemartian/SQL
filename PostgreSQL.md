# SELECT column under an alias

**SELECT** `id` **AS** `my_id` **FROM** `products`;  

# SELECT multiple rows with multiple conditions  

**SELECT** * **FROM** `products` **WHERE** `id` **IN** `(1, 2, 3)`;  

# LIMIT to Top 5 rows

**SELECT** * **FROM** `products` **LIMIT** `5`;  

# LIMIT to Top 5 rows but skip the first 2  

**SELECT** * **FROM** `products` **LIMIT** `5` **OFFSET** `2`;  

# INSERT VALUES  

**INSERT INTO** `products` (`name`, `price`, `inventory`)
**VALUES** ('tortilla', 4, 1000);  

Result: INSERT 0 1 <--Inserted $1$ row, worked perfectly.  

# RETURN all rows after INSERT  

**INSERT INTO** `products` (`name`, `price`, `inventory`)
**VALUES** ('car', 10000, 1000)
**RETURNING** *;  

Result: Inserted row displayed.  

# INSERT multiple rows  

**INSERT INTO** `products` (`name`, `price`, `inventory`)
**VALUES** 
('laptop', 50, 25),
('monitor', 60, 4)
**RETURNING** *;     

# DELETE rows  

**DELETE FROM** `products` **WHERE** `id` = 7;    

# UPDATE rows  

**UPDATE** `products`
**SET**
`is_sale` = true
**WHERE** `id` > 15
**RETURNING** *;  