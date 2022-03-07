# Project Background
One of my modules for Year 2 is **Enterprise Systems Development (aka ESDE)** where I had to **implement secure coding practices and cloud computing skillsets such as refactoring of APIs and deployment via AWS console to an existing website within 6 months** based on the given web vulnerabilities...

## Flaws Identified in the Website
In terms of the secuity vulnerabilities, this website has 7 types:
- SQL Injection (SQL-I)
- Broken Authentication (BA)
- Sensitive Data Exposure (SDE)
- Broken Access Control (BAC)
- Cross Site Scripting (XSS)
- Insufficient Logging and Monitoring (ILM)
- Using Components with Known Vulnerabilities (CKV)

In terms of the above mentioned flaws, 
- SQL-I is fixed by replacing the existing SQL queries with **prepared statements that contain placeholders as parameterized queries**
- BA is fixed by improving the session management by **creating a blacklisted JWT token table in MYSQL database** and **password enumeration**
- SDE is fixed by **using HTTPS protocol and SSL certificate**
- BAC is fixed by **using middleware functions for authorization**
- XSS is fixed by **creating middlware for input validation and output sanitization**
- ILM is fixed by **installing Winston** which is a simple and universal logging library avaialble on open-source Github
- CKV is fixed by **installing OWASP Dependency Check** which is a software composition analysis tool to detect publicly disclosed vulnerabilities contained within a project
 
In terms of code review, the website has an overall **inconsident JSON response structure** and **poor scenario handling**. To fix this, I decided to implement a common data structure that includes the **HTTP status code** and the **JSON data body**, regardless of the API type (ie. GET, POST, PUT, DELETE). In terms of scenerios, it can be differentiated into 2 types:
- Success: A **HTTP status code of 200**, message and **only the relevant rows from the database** should be returned to prevent users with malicious intentions from getting more than the necessary information. For successful updates (ie. PUT API requests), an **array of data ccalled jsonResult should preferably be printed out**, instead of just results[0] which does not provide a meaningful insight into the data representation. 

- Error:  Changing the **API response to return the relevant error message**. For example, when logging in, the user could view a pop up message stating "invalid email and/or password" instead of "null". 

Furthermore, the use of **nested callbacks** are seen within the previous code, which may allow attackers to use automated tools to "hang" the project for several days. Thus, these nested callbacks can be replaced with **async and await technique** that **enables promise based behavior** through `try` and `catch` blocks. In this way, **promise chains need not be explicitly configured** and the **code can be executed without waiting for the fulfillment of callbacks**. 

## Configurations
- Frontend: Localhost 3000
- Backend: Localhost 8080
- Database: MySQL Localhost 3306 

### Other Notes
1. For an in-depth documentation of flaws identified in the website, you may refer to the ESDE CA1 report under my LinkedIn profile `projects` section.

2. For an in-depth documentation of my progress from the deployment of the web application to refactoring of APIs and troubleshooting of bugs, you may refer to the ESDE CA2 report under my LinkedIn profile `projects` section.

3. This project has no association with **any of the designs featured on the webpage**. Images were given for use as testing placeholders upon uploading to Cloudinary platform, so any similar seen in real life is purely coincidental.
