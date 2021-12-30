<!-- Headings -->
# Intro to SQL  

## Data Types

`char(s)` Memory set for number of characters defined (even if not used).  

`varchar()` Max char(s) set. Memory used only for characters defined.  

## Basic Commands    

**CREATE DATABASE** `name of the database` **;** &nbsp;&nbsp;EXECUTE (F5)

**USE** `name of the database` **;** &nbsp;&nbsp;EXECUTE (F5)

## Constraints in SQL  

* Not Null 
* Default 
* Unique
* Primary Key  

### *Not Null*
```
Field (Column) cannot have a NULL value  

Use Case:  
    E-Catalogue where user does not explore all the way through.
```

### *Default*  
```
Sets a default value for a column where no value is specified.  
```   

### *Unique*
```
Ensures every value in field is unique.  
```  

### *Primary Key*  
```
Uniquely identifies every record in a table.  

(Another way to look at it is: NOT NULL + UNIQUE Constraint)

CANNOT HAVE MORE THAN ONE PRIMARY KEY  
```   
____________________
## Syntax of CREATE TABLE  
&nbsp;  
**CREATE TABLE** `table_name` (  
column1name `datatype`  
column2name  `datatype`  
column3name  `datatype`  

**PRIMARY KEY** (`column`)  
) **;**


> *Example*
>
>**CREATE TABLE** `revision`(  
`e_id` **INT NOT NULL**,   
`e_name` **VARCHAR(20)**,  
`e_salary` **INT**,  
`e_age` **INT**,  
`e_gender` **VARCHAR(20)**,  
`e_dept` **VARCHAR(20)**,  
>
>**PRIMARY KEY**(`e_id`)  
) **;**


## Syntax of INSERT QUERY  
&nbsp;    
**INSERT INTO** `table_name`  **VALUES** (    
`value1`, `value2`, `value3`  
) **;**    

You can write multiple records in a single window, To execute specific commands, select with cursor and press `F5`

## Syntax of SELECT STATEMENT 
&nbsp;  
**SELECT** column1, column2, columnN  
**FROM** table_name **;**  

The output is displayed below in the `Results` window.  

## Select Entire Table    
  
**SELECT** * from  `table_name`  

## Select Distinct Syntax  
Used to select only distinct values from the column.  
&nbsp;   
**SELECT DISTINCT** column1, column2, columnN   
**FROM** table_name **;**   

## Syntax of WHERE CLAUSE  
&nbsp;  
**SELECT** column1, column2, columnN  
**FROM** table_name **WHERE** [condition]  

Example:  
**SELECT** * **FROM** employee **WHERE** e_gender='Female' **;**        
Example:  
**SELECT** * **FROM** employee **WHERE** e_age<30 **;**   
______________________
## Filter RECORDS on MULTIPLE CONDITIONS  
* **AND** Operator  
* **OR** Operator  
* **NOT** Operator  

### **AND** Operator  
&nbsp;  
**SELECT** column1, column2, columnN   
**FROM** table_name **WHERE**  [condition]  **AND**  [condition] **;**    
&nbsp;  
### **OR** Operator    
Displays records if any of the conditions seperated by the **OR** operator is true.  

**SELECT** column1, column2, columnN   
**FROM** table_name **WHERE**  [condition1]  **OR**  [condition2] ... **OR** [conditionN] **;**    

### **NOT** Operator   
Displays a record if the condition is not true.  

**SELECT** column1, column2, columnN   
**FROM** table_name **WHERE NOT**  [condition] **;**    
________________________
## **LIKE** Operator   
Used to extract records where a particular pattern is present.  

Say if you had 3 names: Johnathan, Johnny & Marcus, the **LIKE** operator is used to extract *John*athan and *John*ny  

Used in conjuction with `%` or `_`    

`%` Represents zero, one or multiple characters.  
`_` Represents a single character.  


>The `_` can only **represent** one character, it cannot **represent** multiple characters.  
>
>Think of these *WildCard* Characters as fill in the blanks.  
>
>The `%` can represent multiple blanks, but the `_` can only represent one blank.    

Even if the `_` is expected to find a single character in the middle of a word or a number, remember to use the `%` as prefix or suffix accordingly.  

Eg. Filter values that start with a particular character    

**SELECT** * **FROM** employee **WHERE** e_name **LIKE** 'J%'**;**  

Result: Records where `e_name` are *Julia, Jeff* (Not case sensitive)

## **BETWEEN** Operator
Used to select values between a certain range.  

### Syntax of **BETWEEN** Operator 
&nbsp;   
**SELECT** * **FROM** employee **WHERE** e_name **BETWEEN** 'a' **AND** 'm' **;**  

Returns records where `e_name` contains names such as: *Bob, Anne, Julia, Jeff*  (Not case sensitive)  (Upper limit of specified range is inclusive UNLIKE Python)    

**BETWEEN** Operator for numbers works the same with the upper limit being inclusive.  
&nbsp;  

# List all tables in a DB  

**SELECT** * **FROM** `information_schema.tables` **;**  

Result:  

TABLE_CATALOG |  TABLE_SCHEMA | TABLE_NAME | TABLE_TYPE |
____________________________    
# Functions in SQL  

* **MIN()**
* **MAX()**
* **COUNT()**
* **SUM()**  
* **AVG()**  

## **MIN()** Function   

Returns the smallest value  

## Syntax of **MIN()** Function  
&nbsp;  
**SELECT MIN**(`col_name`) **FROM** table_name  

Eg. Extract the *Age* of the youngest employee of the company  

**SELECT MIN** (`e_age`) **FROM** table_name  

Eg 2. Extract the record of the youngest employee in the company.  

**SELECT** * FROM `employee` WHERE `e_age` = (**SELECT MIN** (`e_age`) **FROM** `employee`)**;**   

## **MAX()** Function   

Returns the largest value  

## Syntax of **MAX()** Function  
&nbsp;  
**SELECT MAX**(`col_name`) **FROM** table_name  

Eg. Extract the highest paid employee of the company  

**SELECT MAX** (`e_salary`) **FROM** table_name    

## **MAX()** Function   

Returns the number of rows that match a specific criteria.  

## Syntax of **COUNT()** Function  
&nbsp;  
**SELECT COUNT** (`*`) **FROM** table_name **WHERE** `condition`**;**  

Eg. How many male employees work at this company?  

**SELECT COUNT** (`*`) **FROM** `employee` **WHERE** `e_gender` = 'Male'  
&nbsp;  
## Syntax of **SUM()** Function   
&nbsp;  
**SELECT SUM** (`col_name`) **FROM** table_name  

`SUM()` function gives the total sum of a numeric column.    
&nbsp;  
## Manual AVERAGE of a Column  
&nbsp;  
**SELECT SUM** (`col_name`) / **COUNT** (`*`) **FROM** table_name **;**  
&nbsp;  
____________________________   
# String Functions SQL  

* **LTRIM()**
* **LOWER()**  
* **UPPER()** 
* **REVERSE()**  
* **SUBSTRING()**  

## Syntax of **LTRIM()** Function  
&nbsp;  
**SELECT** '&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;spartaaaa' `Execute/F5`  
**SELECT LTRIM**('spartaaaa')    
&nbsp;  
## Syntax of **LOWER()** Function  
Converts all characters to lower case.    
&nbsp;  
**SELECT LOWER**('THIS IS SPARTA')  $\leftarrow$ No **;** needed.    

## Syntax of **UPPER()** Function   
Converts all characters to upper case.   
&nbsp;  
**SELECT UPPER**('this is sparta')  

Result: THIS IS SPARTA  
&nbsp;  
## Syntax of **REVERSE** Function  
Reverses all the characters in the string.  
&nbsp;  
**SELECT REVERSE**('i love icecream')  

Result: maerceci evol i  

## Syntax of **SUBSTRING()** Function   
Gives a substring from the original string.  
&nbsp;  
**SUBSTRING()** requires 3 parameters:  

* expression
* starting_position int  (index position STARTING FROM $1$)
* length int  (Length of the substring)  

**SELECT SUBSTRING**('i love icecream', 8, 8)  

Result: icecream
&nbsp;  
____________________
&nbsp;  
* **ORDER BY** Keyword  
* **TOP** Clause  

## Syntax of **ORDER BY**  
&nbsp;  
**SELECT** column_list **FROM** table_name  
**ORDER BY** col1, col2,....**ASC** or **DESC ;**  

Example:  
**SELECT** * **FROM** employee **ORDER BY** e_salary **DESC ;**  
Result: Displays the entire table ordered by salary in descending order.  

## Syntax of **TOP** Clause  

Used to fetch the **TOP N** Records.  (Not the max but similar to *Python Pandas `df.head(x)` method), where x is the parameter passed into the `.head()` method.

**SELECT TOP** **x** column_list  
**FROM** table_name **;**

# **GROUP BY**  

Used to get aggregate result with respect to a group.  

Example: Get the average salary of Male and Female seperately.  

## Syntax of **GROUP BY** 

**SELECT** column_list  
**FROM** table_name  
**WHERE** condition  
**GROUP BY** colname(s)  
**ORDER BY** colname(s)**;**

If you mix up this sequence, then you might not get the right result.  

**WHERE** Clause precedes the **ORDER BY** Clause      


**SELECT** **avg(**`e_salary`**),**`e_gender` **FROM** `employee` **GROUP BY** `e_gender`;  

# **HAVING** Clause  

Used in conjunction with **GROUP BY** to impose conditions on groups.  

## Syntax of **HAVING** Clause   

**SELECT** column_list  
**FROM** table_name  
**WHERE** condition  
**GROUP BY** colname(s)
**HAVING** condition  
**ORDER BY** colname(s)**;**    


**HAVING** $\rightarrow$ Used to run a condition inside the **GROUP BY** data, whereas the **WHERE** can *ONLY* be used before the **GROUP BY** and not after.  

# **UPDATE** Statement  

Used to modify the existing records in a table.  

## Syntax of **UPDATE** Statement  
**UPDATE** `table_name` 
**SET** `col1`=`val1`**,**`col2`=`val2`...
[**WHERE** Condition]**;**  

**UPDATE** `employee` **SET** `e_dept` = 'Tech' **WHERE** `e_gender` = 'Female'**;**

**SELECT** `*` **FROM** `employee`**;** (To view the results of modification)  

# **DELETE** Statement  

Used to delete existing records in a table.  

## Syntax of **DELETE** Statement  

**DELETE FROM** `table_name` [**WHERE** condition]**;**  

# **TRUNCATE** Statement  

Deletes all the data inside the table.  

## Syntax of **TRUNCATE** Statement  

**TRUNCATE TABLE** `table_name`**;**  

# **INNER JOIN**   

Returns records that have matching values in both the tables.   

It is also known as **simple join**. 

## Syntax of **INNER JOIN**  

**SELECT** `columns`  
**FROM** `table_1`  
**INNER JOIN** `table_2`  
**ON** `table_1.column_x` = `table_2.column_y`**;**  

The **ON** keyword is used to define a condition on which the *Inner Join* will take place.  

```
SELECT employee.e_name, employee.e_dept, department.d_name, department.d_location  
FROM employee  
INNER JOIN department  
ON employee.e_dept = department.d_name;  
```

* **SELECT** $\leftarrow$ Define ALL columns involved    
* **FROM** the first table   
* **INNER JOIN** the second table    
* **ON** the common table based upon which the equal assertion condition will take place  

The *records* which do not satisfy the condition placed inside the **ON** keyword are not *inner joined*.  

# **LEFT JOIN**  

Returns all the records from the left table, and the matched records from the right table.   

## Syntax of **LEFT JOIN**  

**SELECT** `columns`  
**FROM** `table_1`  
**LEFT JOIN** `table_2`  
**ON** `table_1.column_x` = `table_2.column_y`**;**  

Makes the `table_1` as the *must_display* table, and any records that do not match to the JOIN column in LEFT JOIN, the queried values are displayed as NULL.    

# **RIGHT JOIN**   

Returns all the records from the *right* table, and the matched records from the left table.  

## Syntax of **RIGHT JOIN**  

**SELECT** `columns`  
**FROM** `table_1`  
**RIGHT JOIN** `table_2`  
**ON** `table_1.column_x` = `table_2.column_y` **;**   

Makes table_1 as the must_display table, and any records that do not match to the JOIN column in RIGHT JOIN, the queried values are displayed as NULL.      

E.g  

**SELECT** `employee.e_name`, `employee.e_dept`, `department.d_name`, `department.d_location` **FROM** `employee`
**LEFT JOIN** `department`  
**ON** `employee.e_dept` = `department.d_name`;   

# **FULL JOIN** 

Returns all the records from the *left* table **and** the *right* table, with NULL values in place where the join condition is not met.  

## Syntax of **FULL JOIN** 

**SELECT** `columns`  
**FROM** `table_1`  
**FULL JOIN** `table_2`  
**ON** `table_1.column_x` = `table_2.column_y` **;** 

# **UPDATE USING JOIN**  

Used to modify values in *table_1* based on how values of a column may relate to a column in *table_2*.    

E.g

**UPDATE** `employee`  
**SET** `e_age` = `e_age` + 10   
**FROM** `employee`  
**JOIN** `department` **ON** `employee.e_dept` = `department.d_name`;

# **DELETE USING JOIN**  

**DELETE** `employee`
**FROM** `employee`
**JOIN** `department`
**ON** `employee.e_dept` = `department.d_name`
**WHERE** `d_location` = `'New York'` **;**    

# **UNION** Operator  

UNION operator is used to combine the result-set of two or more SELECT statements.  

$A \cup B$ returns the elements from **both** sets **w/o** duplicates.  

## Syntax of **UNION OPERATOR**  

**SELECT** `column_list` **FROM** `table_1`  
**UNION**  
**SELECT** `column_list` **FROM** `table_2` 

*(The **number** and the **order** of the columns **must** be the same in both the select queries.)*  

# **UNION ALL** Operator  

UNION ALL operator gives all the rows from both the tables including the duplicates.  

## Syntax of **UNION ALL** Operator   

**SELECT** `column_list` **FROM** `table_1`  
**UNION ALL**  
**SELECT** `column_list` **FROM** `table_2`   

# **EXCEPT** Operator  

EXCEPT Operator combines *two SELECT statements* and returns **unique** records from the *left query* which are **not** a part of the *right query*.  

## Syntax of **EXCEPT** Operator   

**SELECT** `column_list` **FROM** `table_1`  
**EXCEPT**  
**SELECT** `column_list` **FROM** `table_2`     

*(The **number** and the **order** of the columns **must** be the same in both the select queries.)*    

# **INTERSECT** Operator  $A \cap B$ 

INTERSECT Operator helps to combine two SELECT statements and returns the records which are **common** to both the SELECT statements.    

## Syntax of **INTERSECT** Operator  

**SELECT** `column_list` **FROM** `table_1`  
**INTERSECT**  
**SELECT** `column_list` **FROM** `table_2`    

*(The **number** and the **order** of the columns **must** be the same in both the select queries.)*      

# **VIEW** 

$\hookrightarrow$ is a virtual table based on the result of an sql statement

*(used to limit the information you want to display)*  

$\hookrightarrow$ Nothing but the result of an SQL statement with a name/keyword attached to it. 

## Syntax of **VIEW** 

*('CREATE VIEW' must be the first statement in a query batch.)*    
*(CREATE VIEW must be the only statement in the batch)*  

**CREATE VIEW** `female_employee` **AS**  
**SELECT** * **FROM** `employee`  
**WHERE** `e_gender` = 'Female';  
$---------$   
**SELECT** * **FROM** `female_employee` **;**  

## Syntax of **DROP VIEW**  

**DROP VIEW** `view_name` **;** 

*Result: Commands completed successfully*  

# **ALTER TABLE** Statement  

Is used to add, delete or modify columns in a table.  

## ALTER TABLE - ADD column    

Creates a column with NULL values

### Syntax of **ALTER TABLE - ADD**  

**ALTER TABLE** `table_name`  
**ADD** `column_name` `datatype`;  

## ALTER TABLE - DROP Column  

Drop a column

### Syntax of **ALTER TABLE - DROP**  

**ALTER TABLE** `table_name`  
**DROP COLUMN** `column_name` **;**   

# **MERGE**   

**MERGE** is the combination of **INSERT**, **DELETE** and **UPDATE** statements.  

*Joins the **target table** to the **source table**.*  

**MERGE** `target_table_name` **AS** `T` *(insert the target table, and assign it an alias using the **AS** keyword)*  
**USING** `source_table_name` **AS** `S`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**ON** `join_condition`   
**WHEN MATCHED** *(if the rows match up based on the join condition)*    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**THEN** `update_statment_to_target_table`    
**WHEN NOT MATCHED BY TARGET** *(when rows are present in the source table and NOT in the target table)*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**THEN** `insert_condition` *(Insert those rows from the source table into the target table)*  
**WHEN NOT MATCHED BY SOURCE**  *(When rows are present in the target table and NOT in the source table)*  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**THEN** `delete_statement` *(then delete those rows from the target table)*  

>Example:  

**MERGE** `employee_target` **AS** `T`  
**USING** `employee_source` **AS** `S`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**ON** `T.e_id` = `S.e_id`    
**WHEN** **MATCHED**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**THEN** **UPDATE** **SET** `T.e_salary` = `S.e_salary`, `T.e_age` = `S.e_age`  
**WHEN** **NOT** **MATCHED** **BY** **TARGET**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**THEN** **INSERT** (`e_id`, `e_name`, `e_salary`, `e_age`, `e_gender`, `e_dept`)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**VALUES** (`S.e_id`, `S.e_name`, `S.e_salary`, `S.e_age`, `S.e_gender`, `S.e_dept`)      
**WHEN NOT MATCHED BY SOURCE**    

# User Defined Functions  

* Scalar Valued Functions
* Table Valued Functions  

## Scalar Valued Functions  

Scalar Valued Function always returns a scalar value.  

### Syntax of Scalar Valued Functions  

**CREATE FUNCTION** `function_name`(`@param1` `data_type`, `@param2` `data_type`...)   
**RETURNS** `return_datatype`  
**AS**  
**BEGIN**  
&nbsp;&nbsp;&nbsp;&nbsp;*----Function Body*  
**RETURN** `value`    
**END** *(To end the function)*    

> Example:  

**CREATE FUNCTION** `add_ten`(`@num` **AS INT**)  
**RETURNS** **INT**  
**AS**  
**BEGIN**  
**RETURN** (`@num` + 10)  
**END** 

*Calling the function:*  

**SELECT** **dbo**.`add_ten`(10)  

Result: 20

## Table Valued Functions  

Table valued functions returns a table.  

### Syntax of Table Valued Functions 

There is no **BEGIN** and **END** keyword for *Table Valued Functions*  

**CREATE FUNCTION** `function_name`(`@param1` `data_type`, `@param2` `data_type`...)   
**RETURNS** `table`    
**AS**    
**RETURN** (**SELECT** `column_list` **FROM** `table_name` **WHERE** [`condition`])    

> Example:   

**CREATE FUNCTION** `select_gender`(`@gender` **AS** **VARCHAR**(`20`))    
**RETURNS** **TABLE**  
**AS**  
**RETURN** (**SELECT** * **FROM** `employee_target` **WHERE** `e_gender` = `@gender`)  

*Calling the Function:*  

**SELECT** * **FROM** `dbo`.`select_gender`(`'Male'`)  

Result: The `employee_target` with `e_gender` values which equal only `'Male'`.   

# Temporary Table  

Temporary Tables are created in tempDB and deleted as soon as the session is terminated.  

## Syntax to CREATE TEMPORARY TABLE  

*Preceded with a hash.*

**CREATE TABLE** `#table_name`();  

# CASE Statement  

CASE Statement helps in multi-way decision making.  

*Analogous to if and elif from python and the newly introduced switch-case*  

## Syntax of CASE Statement  

**CASE**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**WHEN** `condition_1` **THEN** `Result_1`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**WHEN** `condition_2` **THEN** `Result_2`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**WHEN** `condition_N` **THEN** `Result_N`   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**ELSE** `Result`  
**END;**  

>Example:  

**SELECT**  *(This happens to be required)*  
**CASE**  
**WHEN** 10>20 **THEN** '10 is greater than 20'  
**WHEN** 10<20 **THEN** '10 is lesser than 20'    
**ELSE** '10 is equal to 20'    
**END**  

Result: 10 is lesser than 20

>Working Example:  

**SELECT** *, `grade`=  
**CASE**  
**WHEN** `e_salary`<$90000$ **THEN** 'C'  
**WHEN** `e_salary`<$120000$ **THEN** 'B'   
**ELSE** 'A'  
**END**  
**FROM** `employee_target`  
**GO**  *(**batch separator** used by the SQL for when more than one SQL Statement is entered in the Query window. Go separates the SQL statements.)*  

# IIF() Function  

is an alternative for the case statement.  

## Syntax of the IIF() Function  

**IIF(**`boolean_expression`, `true_value`, `false_value`**)**  

>Example:  

**SELECT** 
**IIF**(10<20, '10 is lesser than 20', '10 is greater than 20');  

>Working Example:

**SELECT** *, `e_generation`=  
**IIF**(`e_age`<30, 'Millenial', 'Boomer')  
**FROM** `employee_target`  
**GO**  

$OR$  

**SELECT** *, **IIF**(`e_age`<30, 'Millenial', 'Boomer') **AS** `e_generation` **FROM** `employee_target` **;**  

# STORED PROCEDURE  

**STORED PROCEDURE** is a prepared **SQL** code which can be saved and reused.    

## Syntax of STORED PROCEDURE without parameter   

**CREATE PROCEDURE** `procedure_name`  
**AS**  
`sql_statement`   
**GO ;**  

After the procedure has been created, we need to EXECUTE it.  

### Syntax to EXECUTE a STORED PROCEDURE  

**EXEC** `procedure_name`  

> Example:  

**CREATE PROCEDURE** `employee_age`  
**AS**   
**SELECT** `e_age` **FROM** `employee_target`  
**GO ;**  

$THEN$    

**EXEC** `employee_age`;    

https://towardsdatascience.com/customers-who-viewed-this-item-also-viewed-40026c4eb700







































 

