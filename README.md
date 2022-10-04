# SpringBootSecurityRest

Spring Boot rest application with token (JWT) security. Application code took from this article: https://habr.com/ru/post/545610/

It is necessary to prepare a secure REST application that can only be accessed by an authorized user. 

Authorization with the transfer of login and password is performed by a separate request; 

upon successful authorization, the system must generate and return a token. Validation of other requests must be carried out by token.

Our application schema will look like this:

![1](https://user-images.githubusercontent.com/71104368/193878858-70046997-c226-40c0-b4de-63169a2d7599.jpg)

For the solution, we use the Spring Boot and Spring Web framework, it requires:

Java 8+;

Apache Maven

Authorization and validation will be done by Spring Security and JsonWebToken (JWT).

To reduce the code I use Lombok.

I use Postman to test. We start the backend and execute the request http://localhost:8080/users with the GET type.

There is no token, validation failed, we get a message with 401 status.

![2](https://user-images.githubusercontent.com/71104368/193879155-caac7f81-a6b4-42d0-b329-79d5dd6f6750.jpg)

We are trying to log in with incorrect data, we execute a request http://localhost:8080/auth/login with the POST type, 

validation was not completed, the token was not received, an error with a 401 status was returned.

![3](https://user-images.githubusercontent.com/71104368/193879292-2a636e50-2b5a-44d2-a589-fe6030ff834f.jpg)

We authorize with the correct data, authorization is completed, an authorized user and a token are received.

![4](https://user-images.githubusercontent.com/71104368/193879457-eba90cb7-caa9-40d3-b3d4-da54fc8d86f5.jpg)
![5](https://user-images.githubusercontent.com/71104368/193879468-6be046ef-732d-45b6-9391-e421555663de.jpg)

We repeat the request http://localhost:8080/users with the GET type, but with the received token in the previous step. We get a list of users and an updated token.

![6](https://user-images.githubusercontent.com/71104368/193879622-06d0a6ec-293e-4f13-8d6c-065b7c632f73.jpg)
