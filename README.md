# Job-Recommendation
The project aims to use personalization to improve ticket search and recommendation 
* Created Java servlets with **RESTful** APIs to handle HTTP requests and responses
* Built **MySQL** database on **Amazon RDS** to store position data from Github API
* Designed algorithms (e.g., **content-based** recommendation) to improve event recommendation based on search history and favorite records) 
* Deployed server to **Amazon EC2** to handle 150 queries per second tested by Apache JMeter. 
# Project Structure
![image of project structure](https://github.com/alex0527/Job-Recommendation/blob/master/jupiter/project%20structure.png)
# What is JavaEE, Servlet, Tomcat and how do you use them?
The Java EE platform is built on top of the Java SE platform. The Java EE platform provides an API and runtime environment for developing and running large-scale, multi-tiered, reliable, and secure network applications. 

A servlet is a Java class that is used to extend the capabilities of servers that host applications accessed by means of a request-response programming model.

The Apache Tomcat software is an open-source implementation of the Java Servlet, JavaServer Pages, Java Expression Language, and Java WebSocket technologies.

I used Java to build a few servlets. The first one is a SearchItems API that provides the functionality to search around, The second servlet that allows a user to set or unset their favorite records. The last one that recommends similar items to the user. And I deploy these servlets on tomcat.
# What’s the RESTful API and what’s the benefit of REST?
Resource representational state transfer(REST) is an architectural approach to designing web services. 

RESTful API satisfies the following few requirements:
* A resource has an identifier, which is a URL that uniquely identifies that resource. For example http://localhost:8080/jupiter/history?user_id=1111
* REST APIs built on HTTP, the uniform interface includes using standard HTTP verbs to perform operations on resources. The most common operations are GET, POST, PUT, PATCH, and DELETE.
* REST APIs use a stateless request model. HTTP requests should be independent and may occur in any order, so keeping transient state information between requests is not feasible

Benefits of REST
* Operations are directly based on HTTP methods, so that server doesn’t need to parse extra thing
* URL clearly indicates which resources a client wants, easy for clients to understand.
* The server is running in stateless mode, improving scalability.

# What's the builder pattern and why/how do you use the builder pattern?
The builder pattern is a creational pattern for solving a problem of how can a class (the same construction process) create different representations of a complex object. The builder pattern has a nested static builder class to build the object step-by-step and provide a method that will actually return the object. The builder pattern is to deal with constructors that require too many parameters. Also, it can make sure the object is immutable. For example, in our project, our Item class has many different attributes and thus we use a builder pattern.
# How do you use MySQL
I used Amazon's Relational Database Service to store my data. It’s easy to set up and scale. I created 4 tables(Item, User, Category, History)
# Content-based vs. User-based vs. Item-based recommendation
What’s the difference between (Content-based, User-based, Item-based) recommendation?
Content-based is to recommend items to users with similar attributes of an item like price, category, etc. User-based calculates the similarity of users based on their behavior, not on their attributes. Users are similar because they take the same action to the same items. Item-based is similar to user-based but based on the similarity of items, and the similarity calculation is also based on user behavior.
# What is a session?
The session is a conversational state between client and server and it consists of multiple requests and responses between client and server. 
# Why do we need a session?
The HTTP protocol and Web Servers are stateless, what it means is that for a web server every request is a new request to process and they can’t identify if it’s coming from a client that has been sending requests previously. But sometimes in web applications, we should know who the client is and process the request accordingly. For example, a shopping cart application should know who is sending the request to add an item and in which cart the item has to be added or who is sending a checkout request so that it can charge the amount to the correct client.
# What are the HttpSession and Cookie?
HttpSession: An interface provided by the servlet API, we can get a session from HttpServletRequest object using getSession(). HttpSession allows us to set objects as attributes that can be retrieved in future requests. The session ends when the user logs out or inactive after a predetermined period of time.

Cookie: Cookies are text files stored on the client computer and they are kept for user tracking purposes. The server script sends a set of cookies to the browser. The browser stores this information on a local machine for future use. When the next time the browser sends any request to the web server then it sends those cookies information to the server and the server uses that information to identify the user.

