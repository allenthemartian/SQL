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

## Filter RECORDS on MULTIPLE CONDITIONS  
* **AND** Operator  
* **OR** Operator  
* **NOT** Operator  

### **AND** Operator  
&nbsp;  
**SELECT** column1, column2, columnN   
**FROM** table_name **WHERE**  [condition]  **AND**  [condition] **;**    

