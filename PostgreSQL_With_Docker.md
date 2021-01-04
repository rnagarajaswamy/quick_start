# PostgreSQL Setup

## Step 1
Below command will download and pull all the required components to start your PostgreSQL docker.
> $ docker pull postgres

Once the above command is executed and you are ready to move to next step, check the list of images in docker repo.
> $ docker images

<br>Result
| REPOSITORY | TAG    | IMAGE ID     | CREATED    | SIZE  |
| ---------- | ------ | ------------ | ---------- | ----- |
| postgres   | latest | 1f1bd4302537 | 4 days ago | 314MB |



## Step 2
Create a folder to store the data on local machine.
> $ mkdir ~/opt/postgredata

## Step 3
To start the docker
> $ docker run -d \\<br>
> --name dev-postgres \\ <br>
> -e POSTGRES_PASSWORD=admin@123 \\<br>
> -v ${HOME}/opt/postgredata/:/var/lib/postgresql/data \\<br>
> -p 5432:5432 \\<br>
> postgres

To test the running process, run below
> docker ps 
 
 <br>
 
# Install PG Admin
An interface to interact with PostgreSQL, below commend will download PGAdmin interface.

## Step 1
> $ docker pull dpage/pgadmin4        

## Step 2
Execute below script to enable/run PGAdmin.
> $ docker run \\ <br>
-p 80:80 \\ <br>
-e 'PGADMIN_DEFAULT_EMAIL=user@domain.local' \\ <br>
-e 'PGADMIN_DEFAULT_PASSWORD=admin@123' \\ <br>
--name dev-pgadmin \\ <br>
-d dpage/pgadmin4

## Step 3
Run below to see the IPAddress of dev-postgres server
> $ docker inspect dev-postgres -f "{{json .NetworkSettings.Networks }}"

## Step 4
1. Open **http://localhost:80** 
2. Under quick link click **Add New Server"
3. Enter below details
   * Give a name 
   * IP address from **Step 3**
   * User name : postgres
   * Password : << The PostgreSQL password>>  

### *References*
1. [Docket Hub - PostgreSQL](https://hub.docker.com/_/postgres)
2. [towardsdatascience.com](https://towardsdatascience.com/local-development-set-up-of-postgresql-with-docker-c022632f13ea)

