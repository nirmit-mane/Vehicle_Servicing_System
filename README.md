# Vehicle_Servicing_System
DBMS 

mysql> CREATE DATABASE veh_servicing_system;
Query OK, 1 row affected (0.03 sec)

mysql> USE veh_servicing_system;
Database changed
mysql> CREATE TABLE Customer (
    ->     Cus_id INT PRIMARY KEY,
    ->     Name VARCHAR(50),
    ->     Contact VARCHAR(15),
    ->     Address VARCHAR(255)
    -> );
Query OK, 0 rows affected (0.07 sec)

mysql>
mysql> CREATE TABLE Vehicle (
    ->     Veh_id INT PRIMARY KEY,
    ->     Model VARCHAR(50),
    ->     Cus_id INT,
    ->     FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql>
mysql> CREATE TABLE Insurance (
    ->     Insurance_id INT PRIMARY KEY,
    ->     Company_name VARCHAR(50),
    ->     Veh_name VARCHAR(50),
    ->     Veh_id INT,
    ->     FOREIGN KEY (Veh_id) REFERENCES Vehicle(Veh_id)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql>
mysql> CREATE TABLE Appointment (
    ->     Appointment_id INT PRIMARY KEY,
    ->     Veh_id INT,
    ->     Cus_id INT,
    ->     App_date DATE,
    ->     Status VARCHAR(50),
    ->     FOREIGN KEY (Veh_id) REFERENCES Vehicle(Veh_id),
    ->     FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql>
mysql> CREATE TABLE Technician (
    ->     Technician_id INT PRIMARY KEY,
    ->     Name VARCHAR(50),
    ->     Specialization VARCHAR(100),
    ->     Experience INT
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql>
mysql> CREATE TABLE Feedback (
    ->     Feedback_id INT PRIMARY KEY,
    ->     Cus_id INT,
    ->     Ratings INT,
    ->     Comments TEXT,
    ->     FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql>
mysql> CREATE TABLE Payment (
    ->     Payment_id INT PRIMARY KEY,
    ->     Cus_id INT,
    ->     Payment_method VARCHAR(50),
    ->     Amount DECIMAL(10,2),
    ->     FOREIGN KEY (Cus_id) REFERENCES Customer(Cus_id)
    -> );
Query OK, 0 rows affected (0.07 sec)

mysql>
mysql> CREATE TABLE Services (
    ->     Service_id INT PRIMARY KEY,
    ->     Service_type VARCHAR(50),
    ->     Duration INT,
    ->     Cost DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql>
mysql> CREATE TABLE Spare_Parts (
    ->     Part_id INT PRIMARY KEY,
    ->     Name VARCHAR(50),
    ->     Cost DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.01 sec)

mysql>
mysql> CREATE TABLE Service_Center (
    ->     Center_id INT PRIMARY KEY,
    ->     Name VARCHAR(50),
    ->     Contact VARCHAR(15),
    ->     Location VARCHAR(100)
    -> );
Query OK, 0 rows affected (0.01 sec)

mysql> INSERT INTO Customer (Cus_id, Name, Contact, Address) VALUES
    -> (1, 'Ashok Patil', '9823456789', 'Pune, Maharashtra'),
    -> (2, 'Snehal Jadhav', '9856743210', 'Nashik, Maharashtra'),
    -> (3, 'Rajesh Deshmukh', '9876543211', 'Kolhapur, Maharashtra');
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Vehicle (Veh_id, Model, Cus_id) VALUES
    -> (101, 'Tata Nexon', 1),
    -> (102, 'Mahindra Thar', 2),
    -> (103, 'Maruti Swift', 3);
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Insurance (Insurance_id, Company_name, Veh_name, Veh_id) VALUES
    -> (201, 'Bajaj Allianz', 'Tata Nexon', 101),
    -> (202, 'ICICI Lombard', 'Mahindra Thar', 102),
    -> (203, 'HDFC Ergo', 'Maruti Swift', 103);
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Appointment (Appointment_id, Veh_id, Cus_id, App_date, Status) VALUES
    -> (301, 101, 1, '2025-03-01', 'Confirmed'),
    -> (302, 102, 2, '2025-03-02', 'Pending'),
    -> (303, 103, 3, '2025-03-03', 'Completed');
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Technician (Technician_id, Name, Specialization, Experience) VALUES
    -> (401, 'Shankar Pawar', 'Engine Repair', 10),
    -> (402, 'Vilas Gaikwad', 'Electrical Systems', 8),
    -> (403, 'Mangesh Joshi', 'Body Paint & Repair', 12);
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Feedback (Feedback_id, Cus_id, Ratings, Comments) VALUES
    -> (501, 1, 5, 'Excellent service! Very professional.'),
    -> (502, 2, 4, 'Good service, but a bit slow.'),
    -> (503, 3, 3, 'Average experience, can improve.');
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Payment (Payment_id, Cus_id, Payment_method, Amount) VALUES
    -> (601, 1, 'UPI', 1500.00),
    -> (602, 2, 'Credit Card', 2500.00),
    -> (603, 3, 'Cash', 1800.00);
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Services (Service_id, Service_type, Duration, Cost) VALUES
    -> (701, 'Oil Change', 1, 1000.00),
    -> (702, 'Engine Checkup', 2, 2000.00),
    -> (703, 'Body Repair', 3, 5000.00);
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Spare_Parts (Part_id, Name, Cost) VALUES
    -> (801, 'Brake Pads', 1500.00),
    -> (802, 'Spark Plug', 500.00),
    -> (803, 'Air Filter', 800.00);
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
mysql> INSERT INTO Service_Center (Center_id, Name, Contact, Location) VALUES
    -> (901, 'Shiv Auto Garage', '9823567890', 'Pune'),
    -> (902, 'Sai Car Care', '9812345678', 'Mumbai'),
    -> (903, 'Raj Auto Works', '9876543200', 'Aurangabad');
Query OK, 3 rows affected (0.00 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> SHOW TABLES;
+--------------------------------+
| Tables_in_veh_servicing_system |
+--------------------------------+
| appointment                    |
| customer                       |
| feedback                       |
| insurance                      |
| payment                        |
| service_center                 |
| services                       |
| spare_parts                    |
| technician                     |
| vehicle                        |
+--------------------------------+
10 rows in set (0.02 sec)

mysql> SELECT Cus_id, SUM(Amount) AS Total_Amount
    -> FROM Payment
    -> GROUP BY Cus_id;
+--------+--------------+
| Cus_id | Total_Amount |
+--------+--------------+
|      1 |      1500.00 |
|      2 |      2500.00 |
|      3 |      1800.00 |
+--------+--------------+
3 rows in set (0.01 sec)

mysql> SELECT * FROM Appointment
    -> WHERE App_date > '2025-03-01';
+----------------+--------+--------+------------+-----------+
| Appointment_id | Veh_id | Cus_id | App_date   | Status    |
+----------------+--------+--------+------------+-----------+
|            302 |    102 |      2 | 2025-03-02 | Pending   |
|            303 |    103 |      3 | 2025-03-03 | Completed |
+----------------+--------+--------+------------+-----------+
2 rows in set (0.01 sec)

mysql> SELECT * FROM Feedback
    -> ORDER BY Ratings DESC;
+-------------+--------+---------+---------------------------------------+
| Feedback_id | Cus_id | Ratings | Comments                              |
+-------------+--------+---------+---------------------------------------+
|         501 |      1 |       5 | Excellent service! Very professional. |
|         502 |      2 |       4 | Good service, but a bit slow.         |
|         503 |      3 |       3 | Average experience, can improve.      |
+-------------+--------+---------+---------------------------------------+
3 rows in set (0.01 sec)

mysql> SELECT DISTINCT Payment_method FROM Payment;
+----------------+
| Payment_method |
+----------------+
| UPI            |
| Credit Card    |
| Cash           |
+----------------+
3 rows in set (0.01 sec)

mysql> SELECT Cus_id, SUM(Amount) AS Total_Spent
    -> FROM Payment
    -> GROUP BY Cus_id
    -> HAVING SUM(Amount) > 2000;
+--------+-------------+
| Cus_id | Total_Spent |
+--------+-------------+
|      2 |     2500.00 |
+--------+-------------+
1 row in set (0.01 sec)

mysql> SELECT * FROM Services
    -> ORDER BY Cost DESC
    -> LIMIT 2;
+------------+----------------+----------+---------+
| Service_id | Service_type   | Duration | Cost    |
+------------+----------------+----------+---------+
|        703 | Body Repair    |        3 | 5000.00 |
|        702 | Engine Checkup |        2 | 2000.00 |
+------------+----------------+----------+---------+
2 rows in set (0.00 sec)

mysql> SELECT COUNT(*) AS Pending_Bookings
    -> FROM Appointment
    -> WHERE Status = 'Pending';
+------------------+
| Pending_Bookings |
+------------------+
|                1 |
+------------------+
1 row in set (0.00 sec)

mysql> SELECT COUNT(*) AS Vehicles_Sold
    -> FROM Vehicle
    -> WHERE Cus_id IS NOT NULL;
+---------------+
| Vehicles_Sold |
+---------------+
|             3 |
+---------------+
1 row in set (0.01 sec)
