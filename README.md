# Booking-System
Book Tickets/Rooms/Events
create database Booking system;
Use Booking system;

Create Table Customers(customer_id INT AUTO_INCREMENT PRIMARY KEY ,first_name VARCHAR(100),last_name VARCHAR(100),email VARCHAR(150) UNIQUE NOT NULL,ph_no NUMBER(15), address VARCHAR(200));
CREATE TABLE Rooms(room_id INT AUTO_INCREMENT PRIMARY KEY ,room_type VARCHAR(60) ,description TEXT,price DECIMAL(10,2),available BOOLEAN DEFAULR TRUE);
CREATE TABLE Bookings(Booking_id AUTO INCREMENT PRIMARY KEY , customer_id INT , room_id INT, check_in_date DATE, check_out_data DATE, booking_date TIMESTAMP DEFAULT CURRENT TIMESTAMP,
  status VARCHAR(20) DEFAULT 'Pending' --Pending, Coniformed ,Cancelled
  FOREIGN KEY(customer_id) REFERENCES Customers(customer_id), FOREIGN KEY(room_id) REFERENCES Rooms(room_id));
  CREATE TABLE PAYMENTS(Payment_id INT AUTO INCREMENT PRIMARY KEY, booking_id INT, amount DECIMAL(10,2), payment_date TIMESTAMP DEFAULT CURRENT TIMESTAMP,payment_status VARCHAR(15) default 'Pending',--Pending , Paid , Failed  
  FOREIGN KEY(booking_id) REFERENCES Bookings(booking_id));
  INSERT INTO Customers(first_name,last_name,email,ph_no,address) VALUES 
  ("Dimple","Ahuja",Ahuja@gmail.com,9089098761,"Banglore , India"),
  ("Rishi","Shekhawat",rishi@gmail.com,8569742586,"Mumbai , India");

  INSERT INTO Rooms( room_type,description,price) Values 
  ("Single",'A single room with Bed, perfect for one person',150.00),('Double':'A double room with two beds , ideal for two people.',300),('Suite':'A luxurious suite with a king size bed,living areaand ocean view.',500.00);

  Insert into Bookings(customer_id,room_id,check_in_date,check_out_date,status) VALUES 
  (1,2,'12-01-25','17-01-25','Confirmed'),(2,3,'02-02-25',07-02-25',Pending');

  INSERT INTO Payments(booking_id,amount,payment_status) VALUES
  (1, 600.00,'Paid');

  SELECT b.booking_id,c.first_name ,c.last_name, r.room_type,b.check_in_date,b.check_out_date,b.status
  FROM payments p
  JOIN Bookingd b ON p.booking_id = b.booking_id;

  UPDATE Bookings SET status = 'cancelled' WHERE booking_id = 2;

  SELECT room_id , room_type,price, available FROM Rooms WHERE available = 'TRUE';

  UPDATE Payments SET payment_status = 'Paid' WHERE booking_id = 1;
