# Why Reazy

React is a library to build user interfaces. But that's not enough to build an app. An ideal app also needs to 

- Maintain the state of the app
- Fetch data from the server
- Handle user authentication
  - Token based login (like JWT)
  - Login via Facebook or Google
- Setup config variables like
  - Base API path
  - Public key for third party libs
- Run test cases
- Internationalization and localization
- Push notifications

Although we have libraries available for everything, we often struggle with making decisions about the structure of the project and configuration of libraries by following their docs.

Adding many different libraries makes your code less maintainable because the libraries required for above tasks don't reside at one place. What happens if you are much further into development and you realize you need to replace library X with library Y? Most probably you are going to have to change a lot your code to make this simple change. Reazy being a pluggable services-based framework allows you to do this with much less effort.


