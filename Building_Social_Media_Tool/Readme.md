The Challenge - Building a Social Media Tool

In this challenge we’re going to focus in the infrastructure to create, edit and post on a schedule a post to a single social media platform. That takes you through using a message queue, scheduling and event and calling RESTful APIs.
You can (and should) consider extending it to include authentication of users. If you wanted to take it even further you could extend this challenge to be a full blown business. As you can see from Buffer’s transparency dashboard it’s potentially a profitable business.

Step Zero

As always we’re zero-indexed like every good programming language! In this step please set up your IDE, grab a good cup of coffee (or other beverage of your choice) and create a new project.
After that you will want to sign up either the LinkedIn or X APIs (or even both). You can sign up for the APIs and red their documentation via the following.
LinkedIn’s API is documented here: https://learn.microsoft.com/en-us/linkedin/consumer/integrations/self-serve/share-on-linkedin
X’s API is documented here: https://developer.twitter.com/en/products/twitter-api

Step 1

In this step your goal is to build a backend service to make a post. I’d suggest you build this as a simple service that will listen to a message queue and when it receives a message on the queue will then call the relevant API to post on the related social network.
For example a message might be in JSON and contain fields for: author, post body, and visibility.
This service could then be deployed to a Cloud platform fed via one of their queues or hosted locally and fed via a local message queue such as ZeroMQ or RabbtMQ.

Step 2

In this step your goal is to store a post in a database. You should create a service that can receive a post and store it’s details in a database. Initially the database will need the same fields as we used in Step 1, but expect to add more soon.

Step 3

In this step your goal is to schedule a post. For this you’ll need a post date and time field in the database and the ability to set it when creating the post in the database.
You’ll also what to build or leverage some form of scheduling service. That will either be triggered by a field in the database (i.e. a TTL in something like DynamoDB) or that will periodically check the database for posts that are ready to be posted.
Consider the tradeoffs between the different approaches and how they will scale.

Step 4

In this step your goal is to create a user interface that will allow a user to create a post and either post it immediately or schedule it to be posted at a later date and time.

Step 5

In this step your goal is to create a user interface that allows a user to edit one of their scheduled posts, updating the content and/or changing the time and date that it is scheduled to be posted on the social network.
