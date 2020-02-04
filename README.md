## Description

Simple study project powered by [this tutorial](https://developer.okta.com/blog/2020/01/31/java-graphql)
to use Java and Spring Boot to build a GraphQL API. And also test GraphQL API using JUnit 5.

## Documentation
> edit src/main/resources/application.properties.dist (replase xxx with your okta.oauth2 client-secret)
and remove .dist postfix

> set up Okta security plugin
```
./mvnw com.okta:okta-maven-plugin:setup
```
> to run the project use
```
 ./mvnw spring-boot:run 
```

> to see web UI to test your GraphQL API go to http://localhost:8080/gui in your beowser

> to see your token displayed on the web page go to http://localhost:8080/my-access-token

> If you want to use the web UI (http://localhost:8080/gui), click on HTTP HEADERS at the bottom left
 and add the following, replacing <your_access_token> with the actual value of your access token
 that you got in the previous step:
 
  { "Authorization": "Bearer <your_access_token>" }
    
> If you are calling the API directly through HTTP, simply add the Authorization header
> with value Bearer <your_access_token>
```bash
curl 'http://localhost:8080/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: http://localhost:8080' -H 'Authorization: Bearer <your_access_token>' --data-binary '{"query":"{\n  foods {\n    id\n    name\n  }\n}"}'

# or

http POST http://localhost:8080/graphql query='{foods{id,name}}' 'Authorization: <your_access_token>'
```
> to run tests form terminal:
```
./mvnw test
```