# timeout
An experiment to play with Akka-http timeouts, in the hope that this will help fix the timeouts perceived in the report service.

The project was created using the customary giter8 helper:
```
sbt new akka/akka-http-quickstart-scala.g8
```

The commits show the experimentation path, but in a nutshell:
- Added a fake delay during the retrieval of the users.
- Increased the timeout value of the `ask-timeout` configuration property (which is read by the `UserRoutes` class and provided implicitly to the routes).
- Added properties `akka.http.server.request-timeout` and `akka.http.server.idle-timeout`, setting their values to 1 hour.

That seems to solve the timeouts issues.
