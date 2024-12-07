# Voting App
A simple distributed application running across multiple Docker containers.

## Prerequisties
1. *Docker* : Make sure Docker is installed on your system. Docker Installation Guide
2. *Optional: Docker Compose* : Use Docker Compose for easier management of the MinIO container. Docker Compose Installation Guide

### Dependencies
Ensure the following dependencies are installed automatically during the build:
Redis: For collecting votes.
PostgreSQL: For storing votes persistently.

### Network Configuration
Ensure the following ports are available on your machine:  </br>
8080: Voting app frontend.  </br>
8081: Results app frontend.  </br>
31000: Voting app (Kubernetes deployment).  </br>
31001: Results app (Kubernetes deployment).  </br>
9229: Debugging port for the results service.  </br>

## Architecture
![image](https://github.com/user-attachments/assets/871db515-bd85-4b2a-8412-cfad4a5131ad)
A front-end web app in Python which lets you vote between two options </br>
A Redis which collects new votes  </br>
A .NET worker which consumes votes and stores them in  </br>
A Postgres database backed by a Docker volume  </br>
A Node.js web app which shows the results of the voting in real time  </br>

## Steps to Setup Voting App with Docker
1. Clone the github repository </br>
   ```git clone https://github.com/dockersamples/example-voting-app```  </br>
2. Run Voting App container  </br>
   ```cd example-voting-app```  </br>
   docker compose up -d  </br>
3. Verify Running Containers  </br>
   ```docker ps```  </br>
4. Access the Voting App Console
Voting Process:  </br>
![Docker 1](https://github.com/user-attachments/assets/8558e17a-5b52-4551-8a27-106607f1ddea)
Access the Voting Interface:  </br>
Open your browser and navigate to  </br>
```http://localhost:8080``` </br>
Select an Option: You will see options displayed (e.g., "Cats" and "Dogs"). Click on your preferred option to cast your vote.  </br>
Submit Your Vote: After selecting your choice, your vote is automatically registered.  </br>

Viewing Results:
![image](https://github.com/user-attachments/assets/9b2e99d8-c979-4a3a-b5d1-fa5e718ff202)
Access the Results Interface:  </br>
Open your browser and navigate to  </br>
```http://localhost:8081``` </br>
Real-Time Updates: The results page displays the voting tally in real time, showing the count for each option.  </br>
Refresh/Debugging: If results don't update as expected, ensure the app's services (vote, result, worker, redis, and db) are running properly.  </br>

## Future Improvements
1. Enhanced Features: Support for Multiple Votes - Allow users to vote more than once, with options to configure limits (e.g., per day or session).  </br>
2. Security Improvements: User Authentication - Implement a login system to prevent duplicate or fraudulent voting.  </br>
3. Analytics and Reporting - Detailed Metrics: Provide data analytics on voting trends.  </br>
