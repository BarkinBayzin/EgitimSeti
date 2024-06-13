### SQL ve Veritabanı Yönetimi

#### Veritabanı Giriş

**Data ve Database Nedir?**
- **Açıklama:**
  - Veritabanı, birbiriyle ilişkili verilerin organize bir şekilde saklandığı sistemdir. Veri, bilgi anlamına gelir ve veritabanı ise bu bilgilerin toplandığı yerdir.
- **Kaynaklar:**
  - [Microsoft Learn: What is a database?](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-are-databases)

**Database Files:**
- **Açıklama:**
  - Veritabanı dosyaları, verilerin fiziksel olarak saklandığı dosyalardır. SQL Server'da ana dosya türleri MDF (Primary Data File), NDF (Secondary Data File) ve LDF (Log Data File) olarak ayrılır.
- **Kaynaklar:**
  - [Microsoft Learn: Database files and filegroups](https://learn.microsoft.com/en-us/sql/relational-databases/databases/database-files-and-filegroups)

**RDBMS Nedir?**
- **Açıklama:**
  - RDBMS (Relational Database Management System), verilerin tablolar halinde saklandığı ve yönetildiği sistemdir. Örneğin, SQL Server, Oracle, MySQL gibi.
- **Kaynaklar:**
  - [Wikipedia: Relational database management system](https://en.wikipedia.org/wiki/Relational_database_management_system)

**Database Tipleri:**
- **Açıklama:**
  - Veritabanı tipleri arasında ilişkisel (SQL Server, MySQL), NoSQL (MongoDB), zaman serisi veritabanları (InfluxDB) ve diğerleri bulunur.
- **Kaynaklar:**
  - [IBM: Types of databases](https://www.ibm.com/topics)

**Database Servers:**
- **Açıklama:**
  - Veritabanı sunucuları, veritabanı yazılımını çalıştıran ve veritabanına erişim sağlayan sunuculardır. Örneğin, Microsoft SQL Server, Oracle Database Server.
- **Kaynaklar:**
  - [Microsoft Learn: What is SQL Server?](https://learn.microsoft.com/en-us/sql/sql-server/what-is-sql-server?view=sql-server-ver16)

#### SQL Server ile Veri Tabanı İşlemlerine Giriş

**MsSQL Server Tanıtımı, Versiyonları ve Tarihçesi:**
- **Açıklama:**
  - SQL Server, Microsoft tarafından geliştirilen ve ilk olarak 1989 yılında piyasaya sürülen bir RDBMS'dir. Farklı versiyonları vardır ve her bir versiyon, yeni özellikler ve iyileştirmeler getirir.
- **Kaynaklar:**
  - [Wikipedia: Microsoft SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server)

**SQL Server Management Studio Tanıtımı:**
- **Açıklama:**
  - SQL Server Management Studio (SSMS), SQL Server'ı yönetmek ve sorgular yazmak için kullanılan bir araçtır.
- **Kaynaklar:**
  - [Microsoft Learn: SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/sql-server-management-studio-ssms)

**SQL Server Veri Tipleri:**
- **Açıklama:**
  - SQL Server'da verileri saklamak için çeşitli veri tipleri kullanılır. Örneğin, INT, VARCHAR, DATETIME gibi.
- **Kaynaklar:**
  - [Microsoft Learn: Data types (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql?view=sql-server-ver16)
- **Kod Örnekleri:**
  ```sql
  CREATE TABLE ExampleTable (
      ID INT PRIMARY KEY,
      Name VARCHAR(50),
      CreatedDate DATETIME
  );
  ```

**SQL Server Üzerinde Tablo Tasarımı:**
- **Açıklama:**
  - SQL Server'da tablolar, verilerin saklandığı yapılardır. Tabloları tasarlarken sütun adları, veri tipleri ve kısıtlamalar belirlenir.
- **Kaynaklar:**
  - [Microsoft Learn: Create Tables (Database Engine)](https://learn.microsoft.com/en-us/sql/relational-databases/tables/create-tables-database-engine?view=sql-server-ver16)
- **Kod Örnekleri:**
  ```sql
  CREATE TABLE Students (
      StudentID INT PRIMARY KEY,
      FirstName VARCHAR(50),
      LastName VARCHAR(50),
      EnrollmentDate DATE
  );
  ```

**Select-Insert-Update-Delete İşlemleri:**
- **Açıklama:**
  - SQL Server'da veriler üzerinde CRUD (Create, Read, Update, Delete) işlemleri yapılır.
  - Kaynak linkteki tutorial baştan sonra ilerlenmeli, eksik olduğunuzu hissettiğiniz konu başlıklarının notlarını almanız beklenmektedir.
- **Kaynaklar:**
  - [W3Schools: SQL CRUD Operations](https://www.w3schools.com/sql/)
- **Kod Örnekleri:**
  ```sql
  -- Insert
  INSERT INTO Students (StudentID, FirstName, LastName, EnrollmentDate)
  VALUES (1, 'John', 'Doe', '2022-01-01');

  -- Select
  SELECT * FROM Students;

  -- Update
  UPDATE Students
  SET FirstName = 'Jane'
  WHERE StudentID = 1;

  -- Delete
  DELETE FROM Students
  WHERE StudentID = 1;
  ```

**Lab: CRUD Örneği:**
- **Açıklama:**
  - CRUD işlemlerinin nasıl yapıldığını gösteren örnek bir uygulama.
- **Kod Örnekleri:**
  ```sql
  CREATE TABLE Products (
      ProductID INT PRIMARY KEY,
      ProductName VARCHAR(50),
      Price DECIMAL(10, 2)
  );

  -- Insert
  INSERT INTO Products (ProductID, ProductName, Price)
  VALUES (1, 'Laptop', 999.99);

  -- Select
  SELECT * FROM Products;

  -- Update
  UPDATE Products
  SET Price = 899.99
  WHERE ProductID = 1;

  -- Delete
  DELETE FROM Products
  WHERE ProductID = 1;
  ```

#### Normalizasyon

**Data Anormallikleri ve Data Normalizasyonu:**
- **Açıklama:**
  - Normalizasyon, veritabanı tasarımında anormallikleri ve tekrarları önlemek için kullanılan bir tekniktir.
- **Kaynaklar:**
  - [Vertabelo: Database Normalization Basics](https://vertabelo.com/blog/normalize-2nf-3nf/)
  - [Medium Türkçe Makale](https://medium.com/turuncu-internet-solutions/normalizasyon-nedir-f212541f15fb)
- **Kod Örnekleri:**
  ```sql
  -- 1NF Example
  CREATE TABLE Employees (
      EmployeeID INT PRIMARY KEY,
      FullName VARCHAR(100),
      Department VARCHAR(50)
  );

  -- 2NF Example
  CREATE TABLE Departments (
      DepartmentID INT PRIMARY KEY,
      DepartmentName VARCHAR(50)
  );

  CREATE TABLE Employees (
      EmployeeID INT PRIMARY KEY,
      FullName VARCHAR(100),
      DepartmentID INT,
      FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
  );

  -- 3NF Example
  CREATE TABLE Projects (
      ProjectID INT PRIMARY KEY,
      ProjectName VARCHAR(100),
      DepartmentID INT,
      FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
  );
  ```

**SQL Server Veri Tipleri ve SQL Server Üzerinde Tablo Tasarımı:**
- **Açıklama:**
  - Veri tipleri ve tablo tasarımının normalizasyon kuralları çerçevesinde yapılması.
- **Kaynaklar:**
  - [Microsoft Learn: Data types (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql)
- **Kod Örnekleri:**
  ```sql
  CREATE TABLE Orders (
      OrderID INT PRIMARY KEY,
      OrderDate DATE,
      CustomerID INT,
      Amount DECIMAL(10, 2)
  );
  ```

**Constraints:**
- **Açıklama:**
  - Constraints, verilerin doğruluğunu ve bütünlüğünü sağlamak için kullanılan kurallardır. Örneğin, PRIMARY KEY, FOREIGN KEY, UNIQUE gibi.
- **Kaynaklar:**
  - [Microsoft Learn: Constraints](https://learn.microsoft.com/en-us/sql/relational-databases/tables/unique-constraints-and-check-constraints?view=sql-server-ver16)
- **Kod Örnekleri:**
  ```sql
  CREATE TABLE Customers (
      CustomerID INT PRIMARY KEY,
      CustomerName VARCHAR(100) NOT NULL,
      Email VARCHAR(100) UNIQUE
  );

  CREATE TABLE Orders (
      OrderID INT PRIMARY KEY,
      OrderDate DATE,
      CustomerID INT,
      Amount DECIMAL(10, 2),
      FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
  );
  ```

#### Transact SQL

**Transact SQL Nedir?**
- **Açıklama:**
  - Transact-SQL (T-SQL), SQL Server için prosedürel genişletmedir. SQL Server'da veri yönetimi ve sorgulama için kullanılır.
- **Kaynaklar:**
  - [Microsoft Learn: Introduction to T-SQL](https://learn.microsoft.com/en-us/sql/t-sql)

**T-SQL Sorgulama Örnekleri:**
- **Açıklama:**
  - Temel T-SQL sorgulama örnekleri.
- **Kaynaklar:**
  - [W3Schools: SQL Tutorial](https://www.w3schools.com/sql/)
- **Kod Örnekleri:**
  ```sql
  -- Select all records from a table
  SELECT * FROM Customers;

  -- Select specific columns from a table
  SELECT CustomerID, CustomerName FROM Customers;

  -- Select with a WHERE clause
  SELECT * FROM Customers WHERE CustomerName = 'John Doe';

  -- Select with an ORDER BY clause
  SELECT * FROM Customers ORDER BY CustomerName ASC;

  -- Select with a GROUP BY clause
  SELECT COUNT(OrderID), CustomerID FROM Orders GROUP BY CustomerID;
  ```

**T-SQL Sıralama ve Filtreleme Sorguları:**
- **Açıklama:**
  - Verilerin sıralanması ve filtrelenmesi için kullanılan sorgular.
- **Kaynaklar:**
  - [Microsoft Learn: ORDER BY Clause (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/queries/select-order-by-clause-transact-sql)
- **Kod Örnekleri:**
  ```sql
  -- Select with ORDER BY
  SELECT * FROM Orders ORDER BY OrderDate DESC;

  -- Select with multiple ORDER BY columns
  SELECT * FROM Customers ORDER BY CustomerName ASC, CustomerID DESC;

  -- Select with WHERE clause
  SELECT * FROM Orders WHERE Amount > 100;

  -- Select with WHERE and LIKE clause
  SELECT * FROM Customers WHERE CustomerName LIKE 'J%';
  ```

#### Aggregate Functions

**Count, Sum, Avg, Min-Max:**
- **Açıklama:**
  - T-SQL'de kullanılan temel toplama fonksiyonları.
- **Kaynaklar:**
  - [Microsoft Learn: Aggregate Functions (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/functions/aggregate-functions-transact-sql)
- **Kod Örnekleri:**
  ```sql
  -- COUNT function
  SELECT COUNT(*) AS TotalOrders FROM Orders;

  -- SUM function
  SELECT SUM(Amount) AS TotalSales FROM Orders;

  -- AVG function
  SELECT AVG(Amount) AS AverageOrderAmount FROM Orders;

  -- MIN function
  SELECT MIN(Amount) AS MinimumOrderAmount FROM Orders;

  -- MAX function
  SELECT MAX(Amount) AS MaximumOrderAmount FROM Orders;
  ```

**Lab: T-SQL ve Aggregate Func. Sorgu Örnekleri:**
- **Açıklama:**
  - Aggregate fonksiyonlarının nasıl kullanıldığını gösteren örnek uygulama.
- **Kod Örnekleri:**
  ```sql
  -- Count total customers
  SELECT COUNT(CustomerID) AS TotalCustomers FROM Customers;

  -- Sum of all orders
  SELECT SUM(Amount) AS TotalRevenue FROM Orders;

  -- Average order amount by customer
  SELECT CustomerID, AVG(Amount) AS AverageOrderAmount
  FROM Orders
  GROUP BY CustomerID;

  -- Minimum and maximum order amounts
  SELECT MIN(Amount) AS MinOrderAmount, MAX(Amount) AS MaxOrderAmount FROM Orders;
  ```

#### T-SQL Sorgularında Group By ve Having Kullanımı

**T-SQL Sorgularında Case-When, Group By ve Having Kullanımı:**
- **Açıklama:**
  - Verilerin gruplandırılması ve filtrelenmesi için kullanılan sorgular.
- **Kaynaklar:**
  - [Microsoft Learn: GROUP BY Clause (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/queries/select-group-by-transact-sql?view=sql-server-ver16)
  - [Microsoft Learn: HAVING Clause (Transact-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/queries/select-having-transact-sql?view=sql-server-ver16)
- **Kod Örnekleri:**
  ```sql
  -- Group By with Aggregate Function
  SELECT CustomerID, COUNT(OrderID) AS OrderCount
  FROM Orders
  GROUP BY CustomerID;

  -- Group By with Having Clause
  SELECT CustomerID, COUNT(OrderID) AS OrderCount
  FROM Orders
  GROUP BY CustomerID
  HAVING COUNT(OrderID) > 1;

  -- Case-When Statement
  SELECT OrderID, 
         Amount, 
         CASE 
           WHEN Amount > 1000 THEN 'High Value' 
           ELSE 'Low Value' 
         END AS OrderValue
  FROM Orders;

  -- Group By with Multiple Columns
  SELECT CustomerID, ProductID, SUM(Amount) AS TotalAmount
  FROM Orders
  GROUP BY CustomerID, ProductID;
  ```

#### T-SQL Join

**T-SQL Join Nedir?**
- **Açıklama:**
  - JOIN, iki veya daha fazla tablonun verilerini birleştirmek için kullanılır. INNER JOIN, LEFT JOIN, RIGHT JOIN ve FULL JOIN gibi türleri vardır.
- **Kaynaklar:**
  - [W3Schools: SQL JOIN](https://www.w3schools.com/sql/sql_join.asp)
- **Kod Örnekleri:**
  ```sql
  -- Inner Join
  SELECT Orders.OrderID, Customers.CustomerName, Orders.Amount
  FROM Orders
  INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

  -- Left Join
  SELECT Orders.OrderID, Customers.CustomerName, Orders.Amount
  FROM Orders
  LEFT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

  -- Right Join
  SELECT Orders.OrderID, Customers.CustomerName, Orders.Amount
  FROM Orders
  RIGHT JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

  -- Full Join
  SELECT Orders.OrderID, Customers.CustomerName, Orders.Amount
  FROM Orders
  FULL JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
  ```

#### İleri Seviye Konular: Views, Functions, Stored Procedures

**Views:**
- **Açıklama:**
  - View, SQL sorgularının saklanmış hali olup, tablo gibi kullanılabilir.
- **Kaynaklar:**
  - [Microsoft Learn: SQL Server Views](https://learn.microsoft.com/en-us/sql/relational-databases/views/views)
- **Kod Örnekleri:**
  ```sql
  -- Create a View
  CREATE VIEW CustomerOrders AS
  SELECT Customers.CustomerName, Orders.OrderID, Orders.Amount
  FROM Orders
  INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;

  -- Select from a View
  SELECT * FROM CustomerOrders;
  ```

**Functions:**
- **Açıklama:**
  - Fonksiyonlar, tekrar kullanılabilir SQL kodlarını kapsüller. Scalar-valued ve Table-valued olmak üzere iki türü vardır.
- **Kaynaklar:**
  - [Microsoft Learn: SQL Server Functions](https://learn.microsoft.com/en-us/sql/relational-databases/user-defined-functions)
- **Kod Örnekleri:**
  ```sql
  -- Scalar-valued Function
  CREATE FUNCTION GetCustomerName (@CustomerID INT)
  RETURNS VARCHAR(50)
  AS
  BEGIN
      DECLARE @CustomerName VARCHAR(50);
      SELECT @CustomerName = CustomerName FROM Customers WHERE CustomerID = @CustomerID;
      RETURN @CustomerName;
  END;

  -- Use the Function
  SELECT dbo.GetCustomerName(1);

  -- Table-valued Function
  CREATE FUNCTION GetOrdersByCustomer (@CustomerID INT)
  RETURNS TABLE
  AS
  RETURN
  (
      SELECT OrderID, Amount
      FROM Orders
      WHERE CustomerID = @CustomerID
  );

  -- Use the Function
  SELECT * FROM dbo.GetOrdersByCustomer(1);
  ```

**Stored Procedures:**
- **Açıklama:**
  - Stored Procedures, belirli bir görevi yerine getiren saklanmış SQL kod bloklarıdır.
- **Kaynaklar:**
  - [Microsoft Learn: SQL Server Stored Procedures](https://learn.microsoft.com/en-us/sql/relational-databases/stored-procedures)
- **Kod Örnekleri:**
```sql
  -- Create a Stored Procedure
  CREATE PROCEDURE GetCustomerOrders
      @CustomerID INT
  AS
  BEGIN
      SELECT Orders.OrderID, Orders.Amount
      FROM Orders
      WHERE Orders.CustomerID = @CustomerID;
  END;

  -- Execute the Stored Procedure
  EXEC GetCustomerOrders @CustomerID = 1;
  ```

### Eğitim Planı: SQL ve Veritabanı Yönetimi Tamamlandı

Bu README dosyası, SQL ve Veritabanı Yönetimi konusunda kapsamlı bir eğitim planı sunmaktadır. Bu plan, veritabanı kavramlarının temellerinden başlayarak ileri seviye konulara kadar geniş bir yelpazede bilgi ve kod örnekleri içermektedir.

### İçerik Listesi:
- Veritabanı Giriş
  - Data ve Database Nedir?
  - Database Files
  - RDBMS Nedir?
  - Database Tipleri
  - Database Servers
- SQL Server ile Veri Tabanı İşlemlerine Giriş
  - MsSQL Server Tanıtımı, Versiyonları ve Tarihçesi
  - SQL Server Management Studio Tanıtımı
  - SQL Server Veri Tipleri
  - SQL Server Üzerinde Tablo Tasarımı
  - Select-Insert-Update-Delete İşlemleri
- Normalizasyon
  - Data Anormallikleri ve Data Normalizasyonu
  - SQL Server Veri Tipleri ve SQL Server Üzerinde Tablo Tasarımı
  - Constraints
- Transact SQL
  - Transact SQL Nedir?
  - T-SQL Sorgulama Örnekleri
  - T-SQL Sıralama ve Filtreleme Sorguları
- Aggregate Functions
  - Count, Sum, Avg, Min-Max
  - Lab: T-SQL ve Aggregate Func. Sorgu Örnekleri
- T-SQL Sorgularında Group By ve Having Kullanımı
  - T-SQL Sorgularında Case-When, Group By ve Having Kullanımı
- T-SQL Join
  - T-SQL Join Nedir?
- İleri Seviye Konular: Views, Functions, Stored Procedures
  - Views
  - Functions
  - Stored Procedures

### Kullanım:
Bu README dosyası, SQL ve Veritabanı Yönetimi eğitim planını takip etmek isteyen geliştiriciler için kapsamlı bir rehberdir. Her bölümde yer alan açıklamalar, kaynaklar ve kod örnekleri, konunun daha iyi anlaşılmasını sağlamak amacıyla hazırlanmıştır. Öğrenmeye başlamak için yukarıdaki içerik listesinden ilgilendiğiniz konuyu seçebilir ve adım adım ilerleyebilirsiniz.

**Not:** Kaynak linklerinin çalıştığını ve içeriğin güncel olduğunu kontrol etmek her zaman iyi bir uygulamadır.

Bu yapıda hazırlanan README dosyası, doğrudan kullanılabilir ve eğitimi kolaylaştırmak için kapsamlı bilgi sağlar. Başka bir şey sormak ya da eklemek istediğiniz bir şey varsa, lütfen bana bildirin.