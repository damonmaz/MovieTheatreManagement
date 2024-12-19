# Instructions for Setting Up and Running this project:

### Step 1: Download MySQL Community Server
In order to get the database working, download **MySQL Community Server 9.1.0**.

---

### Step 2: Open MySQL Command Line Client
Launch the **MySQL Command Line Client**.

---

### Step 3: Create the Database
Run the following command to create the database:
```sql
CREATE DATABASE THEATRE_DB;
USE THEATRE_DB;
```

---

### Step 4: Create a User to Connect to the Database
Run these commands to create and grant privileges to the user:
```sql
CREATE USER 'theatre_connect'@'localhost' IDENTIFIED WITH 'caching_sha2_password' BY 'theatre';
GRANT ALL ON THEATRE_DB.* TO 'theatre_connect'@'localhost';
```

---

### Step 5: Verify the User Creation
Run this command to confirm the user was successfully created:
```sql
SELECT User, Host FROM mysql.user WHERE User = 'theatre_connect';
```

---

### Step 6: Create Database Tables and Fill Them
Use the following commands in MySQL CLI to create the tables and insert data:
```sql
source Path/To/Project/database/TheatreDB.sql;
source Path/To/Project/database/queries.sql;
```

---

### Step 7: Compile `.class` Files
With `Path/To/Project/` as the current working directory, run this command to compile the `.class` files (note: the `.jar` file does not work, so compiling `.class` files is required).  

Ensure that the `mysql-connector-j-9.1.0.jar` file is in the `/lib` folder:
```bash
javac -cp "lib/mysql-connector-j-9.1.0.jar" src/objects/boundary/*.java src/objects/control/*.java src/objects/entity/*.java
```

---

### Step 8: Run the Application
After creating the `.class` files, run this command in the same working directory:
```bash
java -cp "lib/mysql-connector-j-9.1.0.jar;src" objects.boundary.appGUI
```

---

### Step 9: Payment Information Requirements
When entering payment information, ensure the following conditions are met:
- **Credit Card Number:** Must be 16 digits.
- **CVV:** Must be 3 digits.
- **Expiration Date:** Must:
  - Be in the future.
  - Follow the format `yyyy-mm-dd`.
  - Use the last day of the month (e.g., `2025-01-31`).

---
