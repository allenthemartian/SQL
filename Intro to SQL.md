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

Used to fetch the **TOP N** Records.  

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
**ORDER BY** colname(s)  

If you mix up this sequence, then you might not get the right result.  

**WHERE** Clause precedes the **ORDER BY** Clause  













 

