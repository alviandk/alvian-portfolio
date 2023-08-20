---
title: How I Securely Set Up Database Connection from DBeaver to AWS RDS with IP Whitelisting

date: 2023/7/23
description: A Step-by-Step Guide Securely Connecting DBeaver to AWS RDS with IP Whitelisting.
tag: AWS, RDS, DBeaver 
author: Alvian
---


Hey everyone! Today, I want to share with you how I successfully set up a secure connection from DBeaver to my AWS RDS instance. By implementing IP whitelisting, I made sure that only my trusted IP address could access the database, adding an extra layer of security to my infrastructure.

  

### Step 1: Configuring AWS RDS Security Group

To begin, I logged into my AWS Management Console and navigated to the "RDS" service. I located my RDS instance and clicked on its name to access the details. Under the "Security" tab, I found the "Security group rules" section and clicked "Inbound rules."

![Edit Security Group](https://storage.alviandk.com/how-i-securely-set-up-database-connection-from-dbeaver-to-aws-rds-with-ip-whitelisting/edit+security.png)  

From there, I edited the inbound rules and added a new rule. For the "Type," I chose the database engine I was using (PostgreSQL in my case). Next, I entered my public IP address in the "Source" field to whitelist it. This step ensured that only my IP address would be allowed to access the RDS instance.

  ![Edit Inbound Rule](https://storage.alviandk.com/how-i-securely-set-up-database-connection-from-dbeaver-to-aws-rds-with-ip-whitelisting/edit+inbound.png)

### Step 2: Set My IP Address to Inbound Rules

To get my public IP address, I simply click on "My IP" options from the dropdown list, and it will display my current public IP.
![enter image description here](https://storage.alviandk.com/how-i-securely-set-up-database-connection-from-dbeaver-to-aws-rds-with-ip-whitelisting/add+my+ip.png)

### Step 3: Configuring DBeaver for AWS RDS Connection

  
With my AWS RDS instance secured, it was time to set up the connection in DBeaver. I opened DBeaver on my local machine and clicked on "Database" in the top menu. From the dropdown, I selected "New Database Connection."
  
I chose the appropriate database type for my AWS RDS instance (PostgreSQL) and entered the following details in the connection settings:

  ![Setup PostgreSQL Connection](https://storage.alviandk.com/how-i-securely-set-up-database-connection-from-dbeaver-to-aws-rds-with-ip-whitelisting/setup+connection.png)

- Host/Endpoint: I used the endpoint URL of my RDS instance, provided by AWS.

- Port: I used the port number for PostgreSQL, which is 5432.

- Database/User: I entered the database name and username I had set up for my RDS instance.

- Password: Finally, I provided the password associated with the username.

  

### Step 4: Connecting to AWS RDS with IP Whitelisting

  

With the connection settings filled out, I clicked "Test Connection" to ensure everything was working smoothly. Thankfully, the test was successful, indicating that DBeaver could connect to my RDS instance.

  ![Test connection](https://storage.alviandk.com/how-i-securely-set-up-database-connection-from-dbeaver-to-aws-rds-with-ip-whitelisting/test+connection.png)

Feeling confident, I clicked "Finish" to save the connection settings. From now on, whenever I need to connect to my AWS RDS instance, I can simply select the configured connection in DBeaver's connection list.

  

### Conclusion

  

By following these steps and implementing IP whitelisting for my AWS RDS instance, I've added an essential layer of security to my database infrastructure. Now, only my trusted IP address is allowed to access the RDS instance, significantly reducing the risk of unauthorized access.

  

If you're setting up a similar database connection, I highly recommend considering IP whitelisting as part of your security measures. With DBeaver as my trusted database client, managing and querying my AWS RDS databases has become a seamless and secure experience. Stay safe and happy coding!