## Kubernetes Two-Tier WordPress Deployment
This repository provides configurations and instructions for deploying a two-tier WordPress application on Kubernetes using Services, Secrets, and a MySQL database. This setup ensures secure storage of sensitive data and reliable communication between the WordPress frontend and MySQL backend.

## Prerequisites
Kubernetes cluster configured and accessible via kubectl
Basic understanding of Kubernetes concepts such as Deployments, Services, and Secrets

## Components
WordPress Deployment: Configurations for deploying the WordPress frontend.
MySQL Deployment: Configurations for deploying the MySQL database backend.
Secrets: Kubernetes Secrets to securely store MySQL credentials.
services: Kubernetes services such as cluster-IP NodePort LoadBalancer

## Deployment Steps
Deploy MySQL Database:

Use the provided MySQL Deployment YAML file to deploy MySQL on Kubernetes.
Mount the created Secret into the MySQL container for access to credentials.

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/mysql-deployment.yaml

then use the command 
kubectl apply -f mysql-deployment.yaml

Create Secrets for MySQL Credentials:
Use kubectl create secret command to create a Secret to store MySQL credentials securely. or use the yaml file mention below

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/mysql-secret.yaml

create MYSQL service using the yaml file mention below the services used for the msql deployment should be cluster IP

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/mysql-service.yaml

now,

Use the provided Wordpress Deployment YAML file to deploy Wordpress on Kubernetes.
Mount the created Secret into the Wordpress container for access to credentials.

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/wordpress-deployment.yaml

Create Secrets for Wordpress Credentials:
Use kubectl create secret command to create a Secret to store MySQL credentials securely. or use the yaml file mention below

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/wordpress-secret.yaml

create Wordpress service using the yaml file mention below the services used for the msql deployment should be NodePort for the organization or it can be LoadBalancer type to expose it to the world

https://github.com/NimishRathi/wordpress-deployment/blob/main/wordpress/wordpress-service.yaml

Be carefull while entering the env variabels  values , the MYSQL_DB_HOST will contain the name of the service used for mysql pod

now open the webserver and use the service ip with the appropriate port
congratulation you did it!








