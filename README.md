
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
