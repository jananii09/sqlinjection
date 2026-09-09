# sqlinjection
Exploiting SQL Injection vulnerability
## NAME: JANANI SHREE A
## REG NO: 212224100023
# AIM:
To exploit SQL Injection vulnerability using Multidae web application in Metasploitable2

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode


### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

SQL Injection is a sort of infusion assault that makes it conceivable to execute malicious SQL statements. These statements control a database server behind a web application. Assailants can utilize SQL Injection vulnerabilities to sidestep application safety efforts. They can circumvent authentication and authorization of a page or web application and recover the content of the whole SQL database. 
Identify IP address using ifconfig in Metasploitable2
## OUTPUT
<img width="676" height="317" alt="image" src="https://github.com/user-attachments/assets/4be8bc4e-8430-4590-9a4d-e08b849eda9b" />


Use the above ip address to access the apache webserver of Metasploitable2 from kali/parrot linux. In Kali Linux use the ip address in a web browser.
##  OUTPUT
<img width="670" height="462" alt="image" src="https://github.com/user-attachments/assets/b2c20d88-e45e-460c-a1f5-92bc1c16528b" />


Select Multidae from the menu listed as shown above. The page is displayed as below:
##  OUTPUT
<img width="663" height="437" alt="image" src="https://github.com/user-attachments/assets/a14779cc-e637-47c3-b41d-d011e9edb838" />



Click on the menu Login/Register and register for an account
##  OUTPUT
<img width="671" height="422" alt="image" src="https://github.com/user-attachments/assets/c069645b-ea7a-4814-ab5d-b5ff249902fa" />



Click on the link “Please register here”
##  OUTPUT
<img width="663" height="420" alt="image" src="https://github.com/user-attachments/assets/3330281f-a365-427f-b50f-b4ce62d354a5" />



Click on “Create Account” to display the following page:
##  OUTPUT
<img width="673" height="440" alt="image" src="https://github.com/user-attachments/assets/e8ac9713-7d4e-4367-a4f3-1bb6d8425ee9" />


The login structure we will use in our examples is straightforward. It contains two input fields (username and password), which are both vulnerable. The back-end content creates a query to approve the username and secret key given by the client. Here is an outline of the page rationale:


($query = “SELECT * FROM users WHERE username=’$_POST[username]’ AND password=’$_POST[password]’“;).
 For the username put “ganesh” or “anything” and for the password put (anything’ or ‘1’=’1) or (admin’ or ‘1’=’1) then try to log in, and you’ll be presented with an admin login page.
##  OUTPUT

<img width="672" height="425" alt="image" src="https://github.com/user-attachments/assets/bb8f971e-7efa-4530-88eb-f8612dc29ac9" />


Click “Login”. The logged in page will show as below:
##  OUTPUT
<img width="682" height="312" alt="image" src="https://github.com/user-attachments/assets/e706fe99-50b9-4892-886e-b9c2b3347bba" />



If error faced in registration follow the following steps in metasploitable 2:


This issue is caused by a misconfiguration in the config.inc located in the /var/www/mutillidae folder on Metasploitable 2 VM.

Edit config.inc
Edit config.inc file located in /var/www/mutillidae folder on Metasploitable 2 by typing the following commands [one at the time]:
cd /
sudo nano /var/www/mutillidae/config.inc
Type msfadmin when prompted for the root password. 
Once nano opens config.inc file, look for the line $dbname = ‘metasploit’ as shown in Figure  below:
##  OUTPUT

<img width="670" height="428" alt="image" src="https://github.com/user-attachments/assets/76ab85cf-eb43-451d-831b-66f82601a059" />

Replace ‘metasploit’ with ‘owasp10’ and make sure the lines end with semicolon ; as shown in Figure
##  OUTPUT

<img width="675" height="382" alt="image" src="https://github.com/user-attachments/assets/068872d3-5e2e-41da-a34c-5921832236e3" />




Save and exit the config.inc
Save than exit the config.inc file by typing CTRL+X keys on your keyboard and the Y [Enter] when prompted to save the file
Restart the Apache server
To restart Apache, type the following command in the terminal. Alternatively, you can just reboot Metasploitalbe 2 VM.
sudo /etc/init.d/apache2 reload
##  OUTPUT
<img width="671" height="370" alt="image" src="https://github.com/user-attachments/assets/8521092d-4212-4ae7-acac-68e721ff0e79" />




# Reset Mutillidae database
Refresh the page then clicking on the Reset DB menu option to reset the Mutillidae database [Figure ]. Click OK when prompted.
##  OUTPUT

<img width="676" height="326" alt="image" src="https://github.com/user-attachments/assets/98dcc3e5-c0cf-421b-82d1-a1a005c04f58" />




# Test the new configuration
Alright. Now is time to test if we managed to fix the database issue. Go ahead and register a new account on the Mutillidae webpage.

 The Mutillidae database error no longer appears 
#OUTPUT

<img width="677" height="422" alt="image" src="https://github.com/user-attachments/assets/f8bc58c7-d9a8-4d83-a7f9-434341d0c61c" />


Now after logging out you will see the login page. In the login page give ganesh’ # (myusername). You can see the page now enters into the administrator page as before when giving the password.
#OUTPUT
<img width="676" height="427" alt="image" src="https://github.com/user-attachments/assets/44e88f71-43a4-4060-a512-18c8672eb58c" />


Click the login button and you will see it enter into the administrator page.
#OUTPUT

<img width="675" height="271" alt="image" src="https://github.com/user-attachments/assets/4cbe0751-85ff-40df-8c7a-c56d98c00c99" />


## Union-based SQL injection

UNION-based SQL injection assaults enable the analyzer to extract data from the database effectively. Since the “UNION” operator must be utilized if the two inquiries have precisely the same structure, the attacker must craft a “SELECT” statement like the first inquiry. 
we will be using the “User Info” page from Mutillidae to perform a Union-Based SQL injection attack. Go to “OWASP Top 10/A1 — Injection/SQLi — Extract-Data/User Info” 

After logging out, Now choose the menu as shown below:
##  OUTPUT

<img width="667" height="510" alt="image" src="https://github.com/user-attachments/assets/019fa77e-65aa-46bc-ab36-a8035f8ae9ca" />


From this point, all our attack vectors will be performed in the URL section of the page using the Union-Based technique.There are two different ways to discover how many columns are selected by the original query. The first is to infuse an “ORDER BY” statement indicating a column number. Given the column number specified is higher than the number of columns in the “SELECT” statement, an error will be returned.
##  OUTPUT

<img width="665" height="488" alt="image" src="https://github.com/user-attachments/assets/adead838-9ebe-4e95-9c31-43d718452219" />


Since we do not know the number of columns, we start at 1. To find the exact amount of columns, the number is incremented until an error related to the “ORDER BY” clause is returned. In this example, we incremented it to 6 and received an error message, so it means that the number of columns is lower than 6.

The browser url of this info page need to be modified with the url as below:
##  OUTPUT
<img width="672" height="452" alt="image" src="https://github.com/user-attachments/assets/adfa51c8-aa83-4bfe-86a1-fa405d9d77af" />




After adding the order by 6 into the existing url , the following error statement will be obtained:
##  OUTPUT

<img width="658" height="432" alt="image" src="https://github.com/user-attachments/assets/0c39a55c-9fca-47da-88a0-0a31049dce9e" />



When we ordered by 5, it worked and displayed some information. It means there are five columns that we can work with. Following screenshot shows that the url modified to have statement added with ordered by 5 replacing 6.
#OUTPUT

<img width="668" height="472" alt="image" src="https://github.com/user-attachments/assets/8c1a8701-3218-4173-89b3-0f7968950695" />



 As it is having 5 columns the query worked fine and it provides the correct result
##  OUTPUT


<img width="667" height="480" alt="image" src="https://github.com/user-attachments/assets/9a715cf7-78a0-4692-8c91-d63f70339a93" />


Instead of using the "order by" option, let’s use the "union select" option and provide all five columns. Ex: (union select 1,2,3,4,5).
##  OUTPUT

<img width="663" height="470" alt="image" src="https://github.com/user-attachments/assets/e18adfcc-a0eb-45a9-a0d6-1bd80871880d" />


As given in the screenshot below columns 2,3,4 are usable in which we can substitute any sql commands to extract necessary information.
##  OUTPUT

<img width="685" height="498" alt="image" src="https://github.com/user-attachments/assets/7eae7164-0964-4423-9020-d7d9f4e66ae1" />





Now we will substitute some few commands like database(), user(), version() to obtain the information regarding the database name, username and version of the database.
##  OUTPUT

<img width="662" height="487" alt="image" src="https://github.com/user-attachments/assets/f9cf377d-53c9-40df-be6c-f5c74feadd71" />


The url when executed, we obtain the necessary information about the database name owasp10, username as root@localhost and version as 5.0.51a-3ubuntu5.
In MySQL, the table “information_schema.tables” contains all the metadata identified with table items. Below is listed the most useful information on this table.

Replace the query in the url with the following one:
union select 1,table_name,null,null,5 from information_schema.tables where table_schema = ‘owasp10’
##  OUTPUT

<img width="666" height="476" alt="image" src="https://github.com/user-attachments/assets/e21732ba-8888-4afa-9bad-d914000eeb57" />



The url once executed will  retrieve table names from the “owasp 10” database.
##Extracting sensitive data such as passwords 

When the attacker knows table names, he needs to discover what the column names are to extract data.

In MySQL, the table “information_schema.columns” gives data about columns in tables. One of the most useful columns to extract is called “column_name.”

Ex: (union select 1,colunm_name,null,null,5 from information_schema.columns where table_name = ‘accounts’).

Here we are trying to extract column names from the “accounts” table.
##  OUTPUT

<img width="661" height="466" alt="image" src="https://github.com/user-attachments/assets/d19b3a70-a458-4930-9eea-ca1891362f10" />


The column names of the accounts is displayed below for the following url:


Once we discovered all available column names, we can extract information from them by just adding those column names in our query sentence.

Ex: (union select 1,username,password,is_admin,5 from accounts).
##  OUTPUT

<img width="672" height="462" alt="image" src="https://github.com/user-attachments/assets/ad76f349-2890-4711-9407-a6db7c7c74fe" />


## Reading and writing files on the web-server
We can use the “LOAD_FILE()” operator to peruse the contents of any file contained within the web-server. We will typically check for the “/etc/password” file to see if we get lucky and scoop usernames and passwords to possible use in brute force attacks later.

Ex: (union select null,load_file(‘/etc/passwd’),null,null,null).


##  OUTPUT
<img width="673" height="456" alt="image" src="https://github.com/user-attachments/assets/109c2680-47c9-450e-a794-15fb03ee3a7e" />
 <img width="670" height="435" alt="image" src="https://github.com/user-attachments/assets/111419a7-7bcc-476e-b0c9-744399aca6eb" />
<img width="662" height="442" alt="image" src="https://github.com/user-attachments/assets/80888868-388f-4154-8121-da81dc3caf6a" />
<img width="668" height="428" alt="image" src="https://github.com/user-attachments/assets/e608d080-c981-432d-8a07-25d3d81f2a0a" />


## RESULT:
The SQL Injection vulnerability is successfully exploited using the Multidae web application in Metasploitable2.
