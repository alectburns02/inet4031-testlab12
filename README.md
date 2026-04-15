<<<<<<< HEAD
# Docker Lab: Containerizing a Three-Tier Application
**INET 4031 - Introductions to Systems**

This lab introduces Docker and Docker Compose by having you containerize a
real, multi-service application. You will package three components: Apache,
Flask, and MariaDB. These will be packaged into separate containers and wired together so they function as a complete application.

The application code and scaffolding are provided.

# Project Overview

This project packages a three tier web app into Docker containers. The user interacts with Apache on port 80 that forwards requests to Flask. Flask processes the user request, communicates with MariaDB for the appropriate data, and returns the results to the user through apache. The lab demonstrates containerizing services, using docker compose to orchestrate multi service applications, understanding health checkups, and networking between containers using service names rather than hard coded ip adresses.

# Prerequisites

Before running the stack, the VM must have Docker and Docker Compose installed, along with a user created .env file for the database credentials.

# Getting Started
To bring the stack from a fresh clone, clone this repo, then navigate into it, create a .env file, build and start the containers using docker compose up --build, access the application through a browser with your ip address, stop the stack with docker compose down, and fully reset the database with docker compose down -v.

# Configuration

This project uses a .env file to store sensitive password information that should not be committed to Git. the .env file must define the:
DB_ROOT_PASSWORD=Fill in this part
DB_NAME=ticketdb
DB_USER=flaskuser
DB_PASSWORD= Fill in this part
and should be ignored with a .gitignore

# Verification
Manual verification:
To verify the stack is running correctly, do a health check using docker compose ps to see that db and app are healthy and that web is running.

Automatic verification:
Lastly the check-lab script can be run by making it executable and then running it to see if pass or fail is provided. curl http://localhost:80/ should return html, curl http://localhost:80/health should return {"database": "connected","status": "healthy"}, and curl http://localhost:80/api/tickets should return a JSON array with tickets. Also 
curl -X POST http://localhost:80/api/tickets \
  -H "Content-Type: application/json" \
  -d '{"title": "My first ticket", "description": "Testing the API"}'
  Can be used to add a ticket.
  Data persistence can be checked by stopping the db with docker compose stop db, then docker compose start db, wait a couple of seconds, then try curl http://localhost:80/api/tickets for another JSON array.

# Feedback (Optional)
No feedback but the lab was interesting to work on.

=======
# inet4031-testlab12
>>>>>>> 787a516b19363f30ce52b49da5c8df0c4271e7d2
