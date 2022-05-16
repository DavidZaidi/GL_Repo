# GL_Repo

Visit:

	https://www.simplilearn.com/tutorials/docker-tutorial/how-to-install-docker-on-ubuntu

Incase Docker is not installed

# Pull Images from Docker-hub (Make sure you have Docker installed)


Write command in terminal:

	sudo docker pull dzaidi/airflow
	sudo docker pull dzaidi/postgres
	sudo docker pull dzaidi/redis

# Clone this repository on your machine:
	git clone https://github.com/DavidZaidi/GL_Repo.git

cd GL_Repo and run the command:
	
	git switch master
	git clone https://github.com/DavidZaidi/GL_Repo.git

# Running Docker Images

	sudo docker run -d -p 5844:8080 -v ~/Apache_Airflow/dags/:/usr/local/airflow/dags dzaidi/airflow webserver 
	sudo docker run dzaidi/redis (or sudo docker compose -f docker-compose-CeleryExecutor.yml up -d)

(Make sure the directory you cloned the Repo in is aligned with the first location(~/Apache_Airflow/dags)

Running Postgres Source/Destination Images:

	sudo docker run --name source-db -d -p 5432:5432 -e POSTGRES_PASSWORD=source dzaidi/postgres
	sudo docker run --name dest-db -d -p 5433:5432 -e POSTGRES_PASSWORD=dest dzaidi/postgres

# Running Airflow

Once the Images are running using docker, headout to:
	http://localhost:5884 To access Apache Airflow
	
Once you see ETL as Dag, Open and Run it.

# Accessing Source/Destination Data

When the Dag is completed successfully, use any IDE To access Postgres (Here we are using Dbeaver)

Use these credentials as source:
	
	user:password@host:port
	postgres:source@localhost:5432
	
Use these credentials as Destination:		

	user:password@host:port
	postgres:dest@localhost:5433


You will see that the data in Source (de_source.source_Table_A) is transferred to Destination (de_destination.dest_Table_A)


