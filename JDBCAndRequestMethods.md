## Statements.

### What is Statements?
It is an interface present in java.sql package.

What is the purpose of Statements?
It helps to send our sql query tothe data base and bring the result back to the java applation.

How many types of Statements are there?
There are 3 types of Statements
a) Simple Statements - If we want to work with multiple type of sql queries then we should go for statements.
b) Prepared Statements - If we want to execute only one sql query multiple times then we shoulld go for prepared statement
c) Callable Statements - To execute procedures and functions which is already there in the data base from java application then we should go for callable statemants.

How to use Statements?
eg if we want to delete the all the employees whose income is greater than 10 lakhs

Statement st = con.createStatement(); -> Created the object os Statement
int x = st.executeUpdate(delete from employee where income > 1000000);
System.out.println("The nubmer of employees deleted is: " + x);
st.close();

Note: 
1) In the above case we have sent the required query to the data base and data base will return the number of deleted employee.
2) After completion of the statement object if we dont want to use the object then we should close the statement object for good programming practice.
3) If we want to go for good performance we should go for prepared statement because internally in case of prepared statement query will be compiled only once.


JDBC (Java Database Connectivity)

JDBC Definition 
JDBC is a technology which can be used to communicate database from our java application.

interesting example

A_________________________________________________________B
Source                                                   Destination 

Assume
If we are at place A and we want to buy somthing from place B, but at place B there is different language used which we dont know.
So the first thing we required is Translator.
Secondly we need to check if there is connectivity available to reach B. If not we need to build the connectivity.
Thirdly to reach at place B some vehicle must be required.
Assume that we arranged one vehicle then immediately the vehicle will go to the place B and brings our requirement.

Relating the example to technical term

Source (place A) is nothing but Java Application
Detination (place B) --> Database

Note: Java terminology is different and data base terminology is different then in middle some translator must be required to convert java calls into database calls and vice versa.
This converter is nothing but Driver Software.

In the example we have built a connectivity from A to B, that connectivity is nothing but connection to reach to the database.

The vehicle is nothing but Statement Object.  


1) How we can arrange Driver Software?

class.forname("oracle.jdbc.OracleDriver"); --> we are loading and registering Driver in our Application.

Note: from JDBC 4.0 version this activity is automatically performed. So we can comment the loading and registering Driver part.

2) Establish connection between java application and database.
connection con = Drrivermanager.getConnection("jdbc:oracle:this:@localhost:1521:XE","username", "password");

3) Creating Statement object.
Statement st = con.createStatement();

4) Get the result 
ResultSet rs = st.executeQuery("Write your query here")

Process the result.

while(rs.next()) {
	System.out.println(rs.getString("Column name"))
}


5) Closing the connection object
con.close();

To develope the JDBC based application we need to follow the following steps
1) Load and register driver class 
2) Establish connection between Java Application and database
3) Prepare statement object.
4) Send and Execute SQL Query.
5) Process Result.


GET and POST methods

Based on the type of operation performed by the browser all the HTTP methods are named as follows.

In HTTP 1.0 version there was only 3 methods
1) GET
2) POST
3) HEAD

In HTTP 1.1 version 4 more methods were added
1) OPTIONS
2) PUT
3) DELETE
4) TRACE

Together all the 7 methods are called Big 7 HTTP methods.

Note: There are several other HTTP methods present but the above 7 methods are generally used.


HTTP GET method -

1) If we want to just get the information from the server then we can use GET method.
2) Usually GET request is read-only request and state of the application wont be chanced.
3) Our privided end user information will be appended to the URL as part of query string.
eg we want to donwload a movie name "xyz" then
www.site_Name.com/download?movie_name=xyz

novie_name=xyz --> query string.

Just because of these property we will have many restrictions.
1) Total n user provided data should be append as a part of URL in the form of query string and compulsary this data should be character data only.

2) We can send only limited amount of information. Most of the browsers supports upto 2KB of data as a part of URL

3) Less security: sending sensitive information is not recommended.

Advantages of GET request.

1) Bookmarking of GET request is possible.
2) Caching of GET request is possible: Because of caching the browser dont have to send the request to the server for the second time. Hence performance is improved.


Triggers to send GET Request.
1) Type URL in address bar and enter.

2) Clicking hyper link is always GET request only. for example click here

3) Submitting a form without method attribute is always a GET request because default method is always GET request


Idempotent -->

If we send the request multiple time there is no change in the response. Such type of request are known as idempotent request.

Therefore GET request is idempotent request.


Is idempotent request is safe request or not?

Idempotent request is safe request because it is only read only request and doest not perform and updation on the server side.


POST Request

1) If we want to post information or give information to the server we should go for POST Request

2) It performs update/ write operation in the server.

How our request will be send to the browser?

There are 3 parts in the request.
1) Request Line
2) Request Header
3) Reqest Body.

Whatever the end user provides the information that will be encapsulated as a part of request body and it is not visible to the URL.

Advantages of the POST Requests.
1) No restrictions on the length of the body.
2) We can send body binary and text data.
3) Security is more. So we can send the sensitive data


Disadvantages of POST Request
1) Bookmarking in this case is not applicable.
2) Caching not possible.
3) POST Request is not Idempotent request.
4) It is not safe to repeat.


There is only one possibility to send POST Request that is compulsary there should be form tag and along with that we have to use method = post in the form tag.

 























































































