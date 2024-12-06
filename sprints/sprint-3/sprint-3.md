## API DOCUMENTATION  
You can see API documentation [here](https://htmlpreview.github.io/?https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-3/dist/index.html) (Refresh if blank)  
# LOAD TESTING RESULTS (APACHE JMETER)  
### Test Scenario  
The test was designed to evaluate the system's performance when handling simultaneous file uploads by multiple users.  
#### The specific scenario involved:
- Number of Concurrent Users: 150 virtual users.
- Action Simulated: Each user uploaded a file to the system.
- Loops per User: Each user performed the file upload operation 10 times in a loop.
- Total Requests: The test resulted in a total of 1,500 file upload requests (150 users × 10 loops).
  
### Load Test Configuration  
The test.jmx file was uploaded to github and you can find it [here](https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-3/test.jmx)  
#### Thread Group Setup:
- Number of Threads (Users): 150
- Ramp-Up Period: 1 second
- Loop Count: 10
- File Size: ~40KB
- Endpoints: The file upload requests targeted the endpoint POST /track.

### Results Summary:
- Response Time: Average = 77 req/sec, median = 63 req/sec, and 95th percentile = 119 req/sec.
- Throughput: 623.4 req/sec
- Error Rate: 0%

|Label       |# Samples|Average|Min|Max |Std. Dev.|Error %|Throughput|Received KB/sec|Sent KB/sec|Avg. Bytes|
|------------|---------|-------|---|----|---------|-------|----------|---------------|-----------|----------|
|HTTP Request|1500     |77     |5  |2247|157.96   |0.000% |623.44140 |35234.18       |35226.87   |57872.0   |  

### Bottleneck:
- The requirement for POST request is to already have a Boat and a Race created for what track is getting uploaded.

### Non-functional requirement:
Since many racers can create many tracks and all connect back to the internet at the same time, the system should be able to handle the concurrent uploading of at least 7 tracks from 150 users at the same time.  
- Goals met?: yes
- Why?: because our backend can handle the requests and the requirement was not that hard to achieve.

## Backend Test Coverage Reports

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

# Thoughts

## Design Changes

Given what we know now, we will probably incorporate more security features into out application. As of now, all the data we have stored is currently accessible to the users and there is no authentication or validation set in place. This would be fine (still questionable) if we were to only apply this application for personal use. But for releasing into the public, it can cause a lot of problems, such as impersonation of race teams, passing false race data etc. In order to mitigate this, some of the chaanges that an be included are as follows:
1. **User Authentication**  
   Enforce secure login mechanisms, such as email/password combinations or third-party authentication services (e.g., OAuth or SSO), to verify user identities.

2. **Role-Based Access Control**  
   Limit access to certain features and data based on user roles .

3. **Audit Logs**  
   Maintain detailed logs of user actions to enable tracing and accountability in case of disputes or security incidents.

4. **Encryption**  
   Secure sensitive user data, both in transit (e.g., using HTTPS) and at rest (e.g., encrypted databases), to protect against unauthorized access.

## Other thoughts
One key takeaway from our current project is the importance of thorough **requirement gathering** and developing a comprehensive understanding of the **domain knowledge** prior to initiating any new project.

Throughout this project, we encountered situations where individual team members held differing interpretations of the project's objectives. This misalignment resulted in several challenges, including:

1. **Improper Scoping of Features**  
   A lack of clarity regarding the project's goals led to difficulties in prioritizing and defining the features to be implemented.

2. **Frequent Code Refactoring**  
   Misunderstandings and shifts in direction required multiple rounds of refactoring, which increased development time and effort.

3. **Delays and Confusion**  
   Uncertainty surrounding the knowledge of sailboat racing contributed to delays, miscommunication, and inefficiencies within the team.

### Changes  

To address these challenges, we will:

1. **Focus on Requirement Gathering**  
   - Allocate time to clearly define the scope and objectives of the project.  

2. **Enhance Domain Knowledge**  
   - Dedicate efforts to understanding the problem space and its specific needs.  

3. **Document and Validate Requirements**  
   - Develop detailed documentation of requirements and circulate it among the team for review.  
   - Regularly validate the requirements to ensure alignment with the overall project goals.
