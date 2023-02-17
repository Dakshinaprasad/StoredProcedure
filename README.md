# StoredProcedure
create database stored_procedure
create table Customer(
CustomerID int primary key,
Customername varchar(50),
ContactName varchar(50),
address varchar(50),
City varchar(50),
PostalCode varchar(50),
Country varchar(50)
);

insert into Customer values (1,'Alfreds Futterkiste','Maria Anders',	'Obere Str. 57'	,'Berlin',	'12209','	Germany'),(2,'Ana Trujillo Emparedados y helados','	Ana Trujillo','	Avda. de la Constitución 2222	','México D.F.','	05021','	Mexico'),(3	,'Antonio Moreno Taquería','Antonio Moreno','Mataderos 2312','México D.F.'	,'05023'	,'Mexico'),(4,

'Around the Horn',	'Thomas Hardy',	'120 Hanover Sq.','London',	'WA1 1DP',	'UK'),(5,'Berglunds snabbköp',	'Christina Berglund','	Berguvsvägen 8','	Luleå','	S-958 22','	Sweden')


select * from Customer

--creates a stored procedure named "SelectAllCustomers" that selects all records from the "Customers" table:

CREATE PROCEDURE SelectAllCustomers
AS
SELECT * FROM Customer
GO;


--Execute the stored procedure
EXEC SelectAllCustomers;

--creates a stored procedure that selects Customers from a particular City from the "Customers" table:
CREATE PROCEDURE SelectAllCustomers_  @City varchar(50)
AS
SELECT * FROM Customer WHERE City = @City


EXEC SelectAllCustomers_ @City = 'London';

--creates a stored procedure that selects Customers from a particular City with a particular PostalCode from the "Customers" table:

CREATE PROCEDURE SelectAllCustomerss @City varchar(50), @PostalCode varchar(50)
AS
SELECT * FROM Customer WHERE City = @City AND PostalCode = @PostalCode;


EXEC SelectAllCustomerss @City = 'London', @PostalCode = 'WA1 1DP';
