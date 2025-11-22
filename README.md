# Power-bi-project
# Connecting Power BI to PostgreSQL (Local & Aiven)

## 📌 Prerequisites

* Power BI Desktop installed
* PostgreSQL (local or Aiven)
* Basic understanding of database credentials (host, username, password)

---

# 🟦 1. Connect Power BI to Local PostgreSQL

## **1. Install PostgreSQL ODBC Driver**

Download and install the PostgreSQL ODBC driver (psqlODBC) from the official PostgreSQL website.

<img width="1854" height="517" alt="image" src="https://github.com/user-attachments/assets/c7b335a5-476d-4917-963c-183c87975f74" />


---

## **2. Gather Local Connection Details**

Make sure you have:

```
Host: localhost
Port: 5432
Database: your_database_name
Username: your_username
Password: your_password
```

---

## **3. Connect Power BI to Local PostgreSQL**

1. Open Power BI Desktop
2. Click **Get Data → More...**
3. Select **PostgreSQL database**

<img width="955" height="814" alt="image" src="https://github.com/user-attachments/assets/bb357749-0cac-47b0-8dc4-6b1bb2474e16" />

4. Enter your connection details:

```
Server: localhost
Database: your_database_name
```

5. Click **OK** and enter your username & password.

---

## **4. Load Tables**

Power BI will display all tables in your PostgreSQL database.

Select the tables you want → click **Load**.

`[Insert screenshot: Navigator window showing tables]`

---

# 🟦 2. Connect Power BI to Aiven PostgreSQL (Cloud)

Aiven requires SSL, but the setup is straightforward.

---

## **1. Get Aiven PostgreSQL Credentials**

From your Aiven dashboard:

* Open your PostgreSQL service
* Go to **Overview**
* Copy your connection details:

  * Host
  * Port
  * Database
  * Username
  * Password
  * SSL mode (Required)

<img width="1407" height="560" alt="image" src="https://github.com/user-attachments/assets/0064b487-8475-4cca-aff8-eafb8fbfad66" />


---

## **2. Connect Power BI to Aiven with SSL Enabled**

1. Open **Get Data → PostgreSQL database**
2. Enter:

```
Server: your-service-name.aivencloud.com
Database: defaultdb
Port: your_port
```

3. Open **Advanced options** and add:

```
SSL Mode=Require
```

4. Click **OK** → Enter your password.

---

## **3. SSL Troubleshooting**

If you get certificate errors, try:

```
SSL Mode=Verify-Full
```

or download the Aiven CA certificate and configure it.

---

# 🟦 Optional: Use Connection Strings

### **Local PostgreSQL:**

```
Server=localhost;Port=5432;Database=myDB;UID=myUser;PWD=myPassword;
```

### **Aiven PostgreSQL:**

```
Server=your-host.aivencloud.com;Port=12345;Database=defaultdb;UID=avnadmin;PWD=yourPassword;SSL Mode=Require;
```

---

# 🟦 Power Query (M Code) Example

```m
let
    Source = Postgres.Database(
        "your-host.aivencloud.com",
        "defaultdb",
        [
            Port=12345,
            SSLMode=1,
            User="avnadmin"
        ]
    )
in
    Source
```

---

# 🟦 Best Practices

### 🔐 Security

* Never publish passwords in articles or dashboards
* Use Power BI Gateway for scheduled refresh

### ⚡ Performance

* Use **DirectQuery** for real-time dashboards
* Use **Import mode** for better performance on large mode

# 🟦 Conclusion

You now know how to connect Power BI to:

* **Local PostgreSQL**
* **Aiven PostgreSQL (with SSL)**

This simple setup allows you to start building powerful dashboards quickly.

#

---
