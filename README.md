# docker-compose
# create a file with the name: docker-compose.yml
# cp the following in the file and save

version: '3'
services:
  back-app:
    image: abdulkhalil/vote-back:v1
    container_name: back-container-app
    environment:
      ALLOW_EMPTY_PASSWORD: "yes"
    ports:
        - "6379:6379"

  front-app:
    build: ./azure-vote
    image: abdulkhalil/vote-front:v2
    container_name: front-container-app
    environment:
      REDIS: back-app
    ports:
        - "8080:80"
