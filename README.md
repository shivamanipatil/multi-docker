# Multi Docker container deployment workflow with travis and AWS

Multi docker container CI-CD workflow for a simple express-react webapp on AWS beanstalk, RDS and elasticache with Travis-CI. 

## Containerised services
- React
- Express
- nginx
- redis
- postgres

## Development

In development :
- Docker compose is used to manage services.
- An additional nginx container is used to route traffic between development react server and express server.  
- Dev versions of Dockerfiles are used.
- Postgres and redis services are used as docker containers.

## Deployment

In deployement :
- AWS multi docker container beanstalk instance is used to run server, worker and nginx containers.
- Postgres database is used as AWS RDS postgres instance.
- Redis is used as AWS elasticache instance.
- Production build for react files is created and a nginx image is created with these build files places inside of it.

Changes on master branch result in a travis pipeline job in turn doing:
- Code testing.
- Building docker images using our modified code and deployment dockefiles.
- Pushing the newly built docker images to dockerhub.
- Prompts AWS beanstalk to use the newly built docker images for latest code deployment. 
