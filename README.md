# Atlassian-Suite-Dockered
![image](https://user-images.githubusercontent.com/6468571/158800664-c2152886-7203-4152-93fd-e6a78394179a.png)

⏫Atlassian Suite (Complete) Dockered (from source) Atlassian (Authentic) Jira Software, Jira Service Management, Confluence, Fisheye, Crowd, Bitbucket and Bamboo with latest Postgres DB's

![image](https://user-images.githubusercontent.com/6468571/158800426-8c7c3858-bb3c-4525-b2ce-b636a37fb24b.png)

```

#	▄▀█ ▀█▀ █░░ ▄▀█ █▀ █▀ █ ▄▀█ █▄░█   █▀ █░█ █ ▀█▀ █▀▀ ▀
#	█▀█ ░█░ █▄▄ █▀█ ▄█ ▄█ █ █▀█ █░▀█   ▄█ █▄█ █ ░█░ ██▄ ▄
#	ATLASSIAN SUITE (COMPLETE) DOCKERED (FROM SOURCE) ATLASSIAN
#	===========================================================================
#	░░░██╗░██╗░██████╗░░█████╗░░█████╗░██╗░░██╗███████╗██████╗░███████╗██████╗░
#	██████████╗██╔══██╗██╔══██╗██╔══██╗██║░██╔╝██╔════╝██╔══██╗██╔════╝██╔══██╗
#	╚═██╔═██╔═╝██║░░██║██║░░██║██║░░╚═╝█████═╝░█████╗░░██████╔╝█████╗░░██║░░██║
#	██████████╗██║░░██║██║░░██║██║░░██╗██╔═██╗░██╔══╝░░██╔══██╗██╔══╝░░██║░░██║
#	╚██╔═██╔══╝██████╔╝╚█████╔╝╚█████╔╝██║░╚██╗███████╗██║░░██║███████╗██████╔╝
#	░╚═╝░╚═╝░░░╚═════╝░░╚════╝░░╚════╝░╚═╝░░╚═╝╚══════╝╚═╝░░╚═╝╚══════╝╚═════╝░
#	JIRA, SERVICE, CONFLUENCE, FISHEYE, CROWD, BITBUCKET, BAMBOO & POSTGRES DB
#	===========================================================================

#	░░█ █ █▀█ ▄▀█ ▀
#	█▄█ █ █▀▄ █▀█ ▄
#	JIRA SOFTWARE

######### START #########

#	JIRA SOFTWARE: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432
#	- Volume: jiraDBVolume

docker volume create --name jiraDBVolume
docker run -v jiraDBVolume:/var/lib/postgresql/data --name jira_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=jira_db'    -e 'POSTGRES_USER=jira_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres

#	JIRA SOFTWARE: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume

docker volume create --name jiraVolume
docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira"  --network="jira" --restart="always"  -d -p 8080:8080 atlassian/jira-software

######### END #########

#	█▀ █▀▀ █▀█ █░█ █ █▀▀ █▀▀ ▀
#	▄█ ██▄ █▀▄ ▀▄▀ █ █▄▄ ██▄ ▄
#	JIRA SERVICE MANAGEMENT

######### START #########

#	JIRA SERVICE MANAGEMENT: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name servicemanagementDBVolume
docker run -v servicemanagementDBVolume:/var/lib/postgresql/data --name servicemanagement_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=servicemanagement_db'    -e 'POSTGRES_USER=servicemanagement_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres


#	JIRA SERVICE MANAGEMENT: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume


docker volume create --name servicemanagementVolume
docker run -v servicemanagementVolume:/var/atlassian/application-data/servicemanagement --name="servicemanagement"  --network="jira" --restart="always"  -d -p 8110:8080 atlassian/jira-servicemanagement

######### END #########

#	█▀▀ █▀█ █▄░█ █▀▀ █░░ █░█ █▀▀ █▄░█ █▀▀ █▀▀ ▀
#	█▄▄ █▄█ █░▀█ █▀░ █▄▄ █▄█ ██▄ █░▀█ █▄▄ ██▄ ▄
#	CONFLUENCE

######### START #########

#	CONFLUENCE: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name confluenceDBVolume
docker run -v confluenceDBVolume:/var/lib/postgresql/data --name confluence_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=confluence_db'    -e 'POSTGRES_USER=confluence_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres

#	CONFLUENCE: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume


docker volume create --name confluenceVolume
docker run -v confluenceVolume:/var/atlassian/application-data/confluence --name="confluence"  --network="jira" --restart="always"  -d -p 8090:8090 atlassian/confluence-server

######### END #########

#	█▀▀ █ █▀ █░█ █▀▀ █▄█ █▀▀ ▀
#	█▀░ █ ▄█ █▀█ ██▄ ░█░ ██▄ ▄
#	FISHEYE

######### START #########

#	FISHEYE: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name fisheyeDBVolume
docker run -v fisheyeDBVolume:/var/lib/postgresql/data --name fisheye_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=fisheye_db'    -e 'POSTGRES_USER=fisheye_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres


#	FISHEYE: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume


docker volume create --name fisheyeVolume
docker run -v fisheyeVolume:/var/atlassian/application-data/fisheye --name="fisheye"  --network="jira" --restart="always"  -d -p 6680:8080 atlassian/fisheye

######### END #########

#	█▀▀ █▀█ █▀█ █░█░█ █▀▄ ▀
#	█▄▄ █▀▄ █▄█ ▀▄▀▄▀ █▄▀ ▄
#	CROWD

######### START #########

#	CROWD: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name crowdDBVolume
docker run -v crowdDBVolume:/var/lib/postgresql/data --name crowd_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=crowd_db'    -e 'POSTGRES_USER=crowd_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres


#	CROWD: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume


docker volume create --name crowdVolume
docker run -v crowdVolume:/var/atlassian/application-data/crowd --name="crowd"  --network="jira" --restart="always"  -d -p 8095:8095 atlassian/crowd

######### END #########

#	█▄▄ █ ▀█▀ █▄▄ █░█ █▀▀ █▄▀ █▀▀ ▀█▀ ▀
#	█▄█ █ ░█░ █▄█ █▄█ █▄▄ █░█ ██▄ ░█░ ▄
#	BITBUCKET

######### START #########

#	BITBUCKET: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name bitbucketDBVolume
docker run -v bitbucketDBVolume:/var/lib/postgresql/data --name bitbucket_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=bitbucket_db'    -e 'POSTGRES_USER=bitbucket_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres


#	BITBUCKET: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume
#	Jira


docker volume create --name bitbucketVolume
docker run -v bitbucketVolume:/var/atlassian/application-data/bitbucket --name="bitbucket"  --network="jira" --restart="always"  -d -p 7990:7990 atlassian/bitbucket-server

######### END #########

#	█▄▄ ▄▀█ █▀▄▀█ █▄▄ █▀█ █▀█ ▀
#	█▄█ █▀█ █░▀░█ █▄█ █▄█ █▄█ ▄
#	BAMBOO

######### START #########

#	BAMBOO: DATABASE
#	- HOST: jira_db
#	- DATABASE: jira_db
#	- USER: jira_db
#	- PORT: 5432

docker volume create --name bambooDBVolume
docker run -v bambooDBVolume:/var/lib/postgresql/data --name bamboo_db -d  --network="jira" --restart="always"     -e 'POSTGRES_DB=bamboo_db'    -e 'POSTGRES_USER=bamboo_db'    -e 'POSTGRES_PASSWORD=changeme'    postgres


#	BAMBOO: APP
#	- PORT: 8080
#	- Volume: jiraDBVolume


docker volume create --name bambooVolume
docker run -v bambooVolume:/var/atlassian/application-data/bamboo --name="bamboo"  --network="jira" --restart="always"  -d -p 8085:8085 atlassian/bamboo-server


```


![image](https://user-images.githubusercontent.com/6468571/158800560-a2275687-6e5e-451c-a160-0c5debbd8388.png)


![image](https://user-images.githubusercontent.com/6468571/158800519-39280a0c-a555-4c2e-8d67-0632148204c0.png)

