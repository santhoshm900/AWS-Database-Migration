
---

# 📌 2. VPC & Networking Setup

### ✔ Created VPC  
CIDR: **10.0.0.0/16**

### ✔ Created Subnets  
- Public: Web-Pub-Subnet  
- Private: Db-Pri-Subnet, Repl-Pri-Subnet  

### ✔ Created Route Tables  
- Public RT → Internet Gateway  
- Private RT → No IGW  

### 📸 Images  
![VPC](images/vpc.png)  
![Subnets](images/subnetz.png)  
![Route Tables](images/route-table.png)

---

# 📌 3. Security Groups

### Web-SG
- Allow SSH (22)  
- Allow HTTP (80)

### DB-SG
- Allow 3306 from Web-SG  
- Allow 3306 from DMS-SG  

### RDS-SG
- Allow 3306 from DB-SG  

### DMS-SG
- Allow traffic from DB & RDS  

### 📸 Image  
![Security Groups](images/security-groups.png)

---

# 📌 4. MySQL Setup on EC2 (Source DB)

### Install MySQL:
```bash
sudo apt update
sudo apt install mysql-server -y
Set root password:
ALTER USER 'root'@'localhost'
IDENTIFIED WITH mysql_native_password BY 'Sqladmin2025';


📸


📌 5. Create Database & Table
CREATE DATABASE appdb;
USE appdb;

CREATE TABLE Course (
   CourseID int,
   CourseName varchar(1000),
   Rating numeric(2,1)
);

Insert Data
INSERT INTO Course VALUES
(1,'AWS Certified Solutions Architect - Associate',4.5),
(2,'AWS Certified Solutions Architect - Professional',4.6),
(3,'AWS Certified DevOps Engineer - Professional',4.7);


📸


📌 6. Allow Remote DB Access (bind-address)

Edit:

sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf


Update:

bind-address = 10.0.1.212


Restart:

sudo systemctl restart mysql


📸


📌 7. Install Apache, PHP & MySQL Module on Web Server
sudo apt update
sudo apt install apache2 php php-mysql -y
sudo systemctl restart apache2


📸


📌 8. Upload PHP App (FileZilla)

Upload files to:

/var/www/html/


📸


📌 9. Test Website (DB Connectivity)

Open browser:

http://<webserver-public-ip>/index.php


📸


📌 10. Create RDS MySQL (Target DB)

Identifier: aws-rds-db

Security Group: RDS-SG

Subnet Group: RDS-subnet-groups

📸




📌 11. Create AWS DMS Components
✔ Replication Instance

📸


✔ Endpoints

📸


📌 12. Create Migration Task (Full Load)

Status: Load Completed (100%)

📸


📌 13. Verify Data in RDS

Using MySQL Workbench:

SELECT * FROM appdb.Course;


📸


📌 14. Verify EC2 ↔ DB Communication

📸


🎯 Conclusion

✔ VPC Setup

✔ Web + DB EC2 Instances

✔ Apache + PHP Deployment

✔ MySQL Source DB Setup

✔ RDS Target DB Creation

✔ DMS Migration (EC2 → RDS)

✔ Verified data in Workbench

✔ Complete Cloud Migration Project

This project is perfect for DevOps / AWS Portfolio and Interview showcase.
