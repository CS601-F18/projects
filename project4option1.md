Project 4 Option 1 - Ticket Purchase Application
================================================
# *This assignment is incomplete. Proceed at your own risk.*

### Code and Deployment Due - During interactive grading appointment scheduled during (or before) finals week.

### All students will be required to demonstrate their progress on or before the last day of class - December 5, 2018. Students who fail to demonstrate reasonable progress before this checkpoint will not receive credit for the Project Checkpoint criterion.

For this project you will implement a ticket purchase web application (i.e., your own EventBrite!). You will design and implement a two-tier web application with a Java (Jetty/Servlets) front end and an SQL backend. 

### Required Features

You *must* complete all of the following required features for a total of 55 points.


| Points   | Feature         | Description |
| :-------: |:-------------:| :-----|
| 5 | User registration | Provide a *Sign Up* button that allows a user to register to use your site. Users must be able to enter appropriate account information and user data must be saved appropriately in your system. Passwords must be salted and hashed before saving to the database. | 
| 5 | Login and logout | Allow a user to login and logout of your site. Maintain the user session appropriately. |
| 5 | View user information | Display user account information including *details* for all events for which the user has purchased tickets. |
| 5 | View events | Display a list of all events. |
| 5 | View event | Display details for a specific event. |
| 5 | Create event | Allow the user to create a new event by entering all appropriate detail. |
| 5 | Purchase tickets | Allow the user to purchase tickets for an event. |
| 5 | Transfer tickets | Allow the user to transfer tickets to another user. |
| 5 | Relational database - Users | Use a relational database to store *user account* data. |
| 5 | Relational database - Events | Use a relational database to store *event* data. |
| 5 | Deployment | Your solution must be deployed on the microcloud on your [primary node](https://github.com/CS601-F18/notes/blob/master/admin/mcassignments.md) port **7070** prior to your interactive grading appointment. |

You may use additional database tables.

### Additional Features

Select up to 25 points of additional features. *No* extra credit will be awarded for implementing additional features. If you want additional credit, consider [Option 2](project4option2.md).

| Points   | Feature |  Description |
| :-------: |:-------------:|  :-----|
| 5 | Show *n* events per page | Provide pagination to allow a user to see some specific number of events per page and scroll to the next page. |
| 5 | Discount/VIP Tickets | Provide the ability to specify some tickets as discounted (e.g., students) or more expensive (e.g., VIP). |
| 5 | Modify/delete event | Allow a user to modify or delete an event *that s/he has created*.|
| 10 | Images | Integrate images into your site, allow a user to upload images when creating an event and display when the event is viewed. |
| 10 | Sign in with... |  Use a "Sign in with" feature from your favorite site like Slack, Google, or Facebook. |
| 10 | Templates |  Use [Velocity](http://velocity.apache.org/) or another template engine to generate your HTML. |
| 10 | Search | Allow a user to search events for particular phrases or other features. |
| 10 | Hosted | Run on Amazon Web Services or another hosting site. |
| 5 | Branding |  Brand your site with a logo, color scheme, etc. |


### Other Criteria

In addition, your project will be evaluated based on the following criteria for a total of 30 points.

| Points   | Criteria |
| :-------: |:-------------:| 
| 10 | Code Style |  
| 15 | Code Quality |  
| 5 | Project Checkpoint |  

### Requirements

1. You will use Servlets/Jetty as your web framework.
2. You will use a SQL database to store all data including user information, event information, and ticket transaction/purchase information. You are required to design the database tables. 
3. By the time of your demonstration you must have your application deployed on the microcloud. The web site must be deployed on your [primary node](https://github.com/CS601-F18/notes/blob/master/admin/mcassignments.md) port **7070**. See the [guide to running on the microcloud](https://github.com/srollins/software-dev-materials/blob/master/notes/usf_guides/microcloud.md) to ensure that your process is long running.

### Submission Requirements

You will schedule an interactive grading appointment during finals week. Before your schedule appointment, submit all code to your github repository for this assignment **and** ensure your complete solution is be running on the microcloud. Your web front end must be deployed on your [primary node](https://github.com/CS601-F18/notes/blob/master/admin/mcassignments.md) port **7070**. Your services (all three components!) must be running *on different hosts*.

Use the following link to create your private github repository for this assignment: [Project 4]()

For full credit, make sure to follow all [Style Guidelines](https://github.com/CS601-F18/notes/blob/master/admin/style.md). Points will be deducted for each violation.


### Academic Dishonesty

Any work you submit is expected to be your own original work. If you use any web resources in developing your code you are strongly advised to cite those resources. The only exception to this rule is code that is posted on the class website. The URL of the resource you used in a comment in your code is fine. If I google even a single line of uncited code and find it on the internet you may get a 0 on the assignment or an F in the class. You may also get a 0 on the assignment or an F in the class if your solution is at all similar to that of any other student.