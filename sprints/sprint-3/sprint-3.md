### API DOCUMENTATION  
You can see API documentation [here](https://htmlpreview.github.io/?https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-3/dist/index.html) (Refresh if blank)  
### LOAD TESTING RESULTS (APACHE JMETER)  
|Label       |# Samples|Average|Median|90% Line|95% Line|99% Line|Min|Max|Error %|Throughput|Received KB/sec|Sent KB/sec|
|------------|---------|-------|------|--------|--------|--------|---|---|-------|----------|---------------|-----------|
|HTTP Request|100      |10     |8     |12      |21      |57      |6  |107|0.000% |107.87487 |6096.18        |6095.35    |  

This load test simulated 10 concurrent users uploading their tracks the size of 40KB to a website, each performing 10 iterations. In total, the test generated 100 HTTP POST requests, with the server responding in an average time of 10 milliseconds.

### Coverage Reports

You can see backend coverage report [here](https://htmlpreview.github.io/?https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-3/coverage-report/index.html)  


# Security analysis

Our biggest security vulnerability is commiting things to github that should not be publicly available. We have put or database password and google maps api key in our public github repo. The maps key has been cycled and the "production" database password has been changed. 

### Backend security:
There is not many security vulnerabilities because we are not trying to obscure or protect any functions. You don't have to be concerned that someone can gain access to your system when you give them access in the first place. There is no authentication or privileged actions and thus escalation of abilities is not possible. All data is available to all users so no unauthorized data access is possible. logins and user data is not present so security concerns around those are not present. sql injection and database exploits are the greatest concerns for our system. We are using ef entity core for database management and it automatically sanitizes inputs.

We have been coding with the sonarQube extension for visual studio and it does not find any issues with our code. sonarQube is a static analysis tool.  
### Automated client side testing:
Analyzed using zap

The main use case for our app is ephemeral and disconnected from the wider internet. Any security issues that do arise are then mitigated by just not having a permanent hosted server that could be attacked.  

![Pasted image 20241203191945](https://github.com/user-attachments/assets/0e42415c-a5ac-4344-b10f-5d820c581a86)

#### 1: Cloud meta data potentially exposed
Risk -> High
Confidence -> Low

The response from this endpoint is below and given that it is not cloud metadata I believe this is a false positive. 
![Pasted image 20241205091020](https://github.com/user-attachments/assets/5cf34669-5de7-40f1-9108-d20d9b95b162)
#### 2: Content security policy header not set 

Risk -> Medium
Confidence -> High

Fixed in commit https://github.com/COMP-4350-Group-8/comp4350-project/commit/5b9118eb8a1075d9b441d00449c53a310eea3e8b
#### 3: Cross-Domain misconfiguration
Risk -> Medium 
Confidence -> Medium

Cors allow all! Since the current design of the app is to assume all data is public, and no authenticated endpoints exists this is not a major concern. The main use of the app will be ephemeral and disconnected from the wider internet removes the possibility of having someone make requests from outside the network. 

#### 4: Missing Anti-clickjacking Header
Risk -> Medium
Confidence -> Medium

#### 5: X-Content-Type-Options Header Missing
Risk -> Low
Confidence -> Medium


# CI/CD

We have our CI/CD pipeline in github actions [here](https://github.com/COMP-4350-Group-8/comp4350-project/actions)  

Snap shot of CI: ![image](https://github.com/user-attachments/assets/e3675398-abd2-4610-99e7-e06214179c2b)

Snap shot of CD: ![image](https://github.com/user-attachments/assets/ba8ebda3-8e22-40b3-b28e-356c1b20fd37)

The CD uploads the docker images to docker hub, currently linked: [react](https://hub.docker.com/repository/docker/owenhny/sailmapper_react/general) , [backend](https://hub.docker.com/repository/docker/owenhny/sailmapper_backend/general) 



