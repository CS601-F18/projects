Project 3 - HTTP Server
=======================================

### Due - Wednesday, November 7, 2018 - 11am

For this project, you will implement an HTTP server, two web applications, and a full suite of tests. You will practice using the following:

- Concurrency and threads
- Sockets
- JUnit and testing
- Remote deployment
- Good design practices

## Part 1 - HTTP Server

For Part 1 of this assignment you will implement an HTTP server. 

### Requirements

1. You must use raw sockets for this assignment. You may *not* use Tomcat, Jetty, or any other existing server. You also may *not* use any external libraries for request parsing, etc.
2. Your server must support `GET` and `POST` requests. Any other HTTP method will result in a `405 Method Not Allowed` status code. See [HTTP Status Code Definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html). 
3. Your server must be flexible enough to support different web applications. 
4. Your server will be multithreaded. Each incoming request will be handled by a different thread.

### Recommended Design

It is recommend you follow a design similar to the design supported by [Jetty](https://www.eclipse.org/jetty/documentation/9.4.12.v20180830/). Your design does not need to follow the exact API nor does it need to be as extensive, however I recommend you borrow similar ideas. Here are a few items to consider:

- Create a `Handler` interface with a `handle` method. Each web application will implement a different set of handlers, for example a search application will support a `SearchHandler` and a chat application would have a `ChatHandler`. 
- Support an `addMapping` method that will map a URI path to a specific `Handler` instance. When a new request is made to the server the server will retrieve from the mapping the `Handler` appropriate for the path in the request URI.

The examples below show how my API is used for the required applications below.


```java
public class SearchApplication {
	public static void main(String[] args) {
		int port = 1024;
		HTTPServer server = new HTTPServer(port);
		//The request GET /reviewsearch will be dispatched to the 
		//handle method of the ReviewSearchHandler.
		server.addMapping("/reviewsearch", new ReviewSearchHandler());
		//The request GET /find will be dispatched to the 
		//handle method of the FindHandler.
		server.addMapping("/find", new FindHandler());
		server.startup();
	}
}

```

```java
public class ChatApplication {
	public static void main(String[] args) {
		int port = 1024;
		HTTPServer server = new HTTPServer(port);
		server.addMapping("/slackbot", new ChatHandler());
		server.startup();
	}
}

```

## Part 2 - Search Application

For Part 2 of this assignment you will implement an application that will allow users to search the `InvertedIndex` you built for Project 1. You will deploy this application on your [primary microcloud VM](https://github.com/CS601-F18/notes/blob/master/admin/mcassignments.md) on port **8080**.

You will support the following four APIs:

#### `GET /reviewsearch`

This request will return a web page containing, at minimum, a text box and button. When the user enters a query in the text box and clicks the button the `POST` method described below will be called.

#### `POST /reviewsearch`

The body of this request will look as follows: `query=term` where the value is a URL-encoded string.

You will return a web page listing all of the review search results.

#### `GET /find`

This request will return a web page containing, at minimum, a text box and button. When the user enters a message in the text box and clicks the button the `POST` method described below will be called.

#### `POST /find`

The body of this request will look as follows: `asin=123456789` where the value is a URL-encoded string.

You will return a web page listing all of the review and qa documents with the provided ASIN.

## Part 3 - Chat Application

For Part 3 of this assignment you will implement an application that will allow a user to anonymously post a message to the Slack team. Refer to the [Accessing the Slack API](slack.md) instructions for pointers. You will deploy this application on your [primary microcloud VM](https://github.com/CS601-F18/notes/blob/master/admin/mcassignments.md) on port **9090**.

You will support the following two APIs:

#### `GET /slackbot`

This request will return a web page containing, at minimum, a text box and button. When the user enters a message in the text box and clicks the button the `POST` method described below will be called.

#### `POST /slackbot`

The body of this request will look as follows: `message=test+message` where the value is a URL-encoded string.

This request will trigger a post of the message specified by the body to the Slack channel `#project3`. Regardless of the user who types the message it will always appear to have come from your application.

You may choose what to return to the client. One options is to return a web page with a confirmation, and another option is to return the same page returned by the `GET` request so that the user may post another message.

## Part 4 - Tests

For Part 4 you will submit all test cases you have written to test your solution. You must demonstrate unit tests, integration tests, and system tests.

It is expected that all tests execute through JUnit, however if you choose to write standalone client programs for your system tests you may submit those as well, along with a README that describes how they should be executed.

Your grade for Part 4 will be based on the completeness of your tests. If you implement only the tests given as examples below you will not earn a high grade for this portion.

### Unit Tests

Unit tests will test one method. It is not required that you have unit tests for every method you implement, however methods that perform complex processing or logic should have one or more associated unit tests. As an example, you may have a method that parses an HTTP request to validate that it has a correct format, valid method, etc. You should implement several unit tests to confirm that the method works correctly when the request is valid and in all scenarios when it is invalid.

### Integration Tests

Integration tests generally test a path of execution through your program. You may, for example, have a handler that takes as input a request and then calls another method to post to to Slack. In this case, you could use a *mock request object* and test that passing that mock object to your handler results in a correct post to Slack.

### System Tests

System tests will test the end-to-end execution of your program. A system test would use a client program to make a request (valid or invalid) of your deployed server and verify that the response is correct.

## External Libraries

The only external libraries you may use for this assignment are [GSON](https://github.com/google/gson) 2.8.5 and JUnit. For this assignment, it is your responsibility to set up the `pom.xml` file correctly.

## Submission

1. Use the following link to create your private github repository for this assignment: [Project 3](https://classroom.github.com/a/canR1sdY). **Note**, the repository is completely empty so you will need to set it up as required by the assignment.
2. For full credit, make sure to follow all [Style Guidelines](https://github.com/CS601-F18/notes/blob/master/admin/style.md). Points will be deducted for each violation.
3. All code and the jar file described above must be submitted to your github repository by **Wednesday, November 7, 2018 - 11am.**.

<!--## Extra Credit
You may earn up to one (1) point of extra credit by completing interactive grading and submitting all required code during the professor's office hours on or before Friday, October 5, 2018. Note that office hours are first come, first served and students with assignment questions have priority over students wishing to complete early interactive grading. To earn the extra credit it is suggested you come for interactive grading well before the deadline!

Students who submit early and earn 100% may be eligible for an additional extra credit assignment given at the time of submission. Note that additional extra credit will only be awarded *after* a student has earned 100% on his/her solution.
-->
## Grading Rubric

| Points | Criterion |
| ------ | -------- |  
| 5 | **Functionality** - Part 2 Server: correct `GET /reviewsearch`. |  
| 5 | **Functionality** - Part 2 Server: correct `POST /reviewsearch`. |  
| 5 | **Functionality** - Part 2 Server: error conditions `GET /reviewsearch`. |  
| 5 | **Functionality** - Part 2 Server: error conditions `POST /reviewsearch`. |  
| 5 | **Functionality** - Part 2 Server: correct `GET /find`. |  
| 5 | **Functionality** - Part 2 Server: correct `POST /find`. |  
| 5 | **Functionality** - Part 2 Server: error conditions `GET /find`. |  
| 5 | **Functionality** - Part 2 Server: error conditions `POST /find`. |  
| 5 | **Functionality** - Part 3 Server: correct `GET /slackbot`. |  
| 5 | **Functionality** - Part 3 Server: correct `POST /slackbot`. |  
| 5 | **Functionality** - Part 3 Server: error conditions `GET /slackbot`. |  
| 5 | **Functionality** - Part 3 Server: error conditions `POST /slackbot`. |  
| 20 | **Design** - Part 1 Server design. |  
| 15 | **Design** - Part 4 completeness of test cases. |  
| 5 | **Design** - Meets all style guidelines. |  

Partial credit may be awarded for partial functionality and/or partially correct design or style elements.

## Academic Dishonesty

Any work you submit is expected to be your own original work. If you use any web resources in developing your code you are strongly advised to cite those resources. The only exception to this rule is code that is posted on the class website. The URL of the resource you used in a comment in your code is fine. If I google even a single line of uncited code and find it on the internet you may get a 0 on the assignment or an F in the class. You may also get a 0 on the assignment or an F in the class if your solution is at all similar to that of any other student.

