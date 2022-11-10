# Task 3

```ps
az group create --name task3 --location koreacentral
```
```ps
az container create --resource-group task3 --name container --image docker/getting-started --dns-name-label task3victoryo --ports 80
```

```ps
az storage account create --name stracctask3 --resource-group task3 --location koreacentral --sku Standard_RAGRS --kind StorageV2
```


# Task 2
1. create az rg 
2. PostrgeSQL Managed DB //dbtask2
3. create vm staging with a public ip //vm-admin Verysecret-123
4. create web app // using py 3.9 //wa-task2 Verysecret-123

5. it will create App Serivce

### vm-staging

```sh
sudo apt-get update && sudo apt-get upgrade -y
```
```sh
sudo apt-get install postgresql-client
```

6. Allow Azure connections to SQL Server
   - connection security - YES
7. Get the connection string (psql)
   - psql "host=db-lab2.postgres.database.azure.com port=5432 dbname=postgres user=dbadmin@db-lab2 password=Verysecret-123 sslmode=require"

8. VM_STAGING COMMAND
```sh
CREATE DATABASE friends;
\q
mkdir django-app
cd django-app
git clone https://github.com/VictoryoM/cloud-friends.git
cd msdocs-django-postgresql-sample-app
sudo apt-get install python3.8-venv
python3 -m venv .venv
source .venv/bin/activate
editor requirements.txt
```

`pip install -r requirements.txt` // change django to d lowercase
```sh
editor .env
DBNAME=friends
DBHOST=<database-hostname>
DBUSER=<db-user-name>
DBPASS=<db-password>


python manage.py migrate
python manage.py runserver
```

9. Create the environmental variables in the app service
    - //Configuration > New App Setting
    - Name:
     DBNAME
    - Value:
     friends
    - Name:
     DBHOST
    - Value:
     (DB Server Name) //Remove '.postgres.database.azure.com'

    - Name:
DBUSER
    - Value:
{DB Admin Username}

    - Name:
DBPASS
    - Value:
{DB Password}

10. set local git
11. set password for credential
12. //Web App > Deployment Center > Source = local git
13. get url (git clone url)


`git remote add azuretask` URL 

```sh
git push azuretask main:master
```

# TASK 1

1. create rg TASK1
2. PostrgeSQL Managed DB

```sh

sudo apt install python3 python3-pip python3.8-venv docker-compose -y
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
nano .env
```

*Modify the environment variables*


```sh
python3 manage.py migrate
```
