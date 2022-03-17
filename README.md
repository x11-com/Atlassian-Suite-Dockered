# Atlassian Complete Suite Dockered

![image](https://user-images.githubusercontent.com/6468571/158800664-c2152886-7203-4152-93fd-e6a78394179a.png)

## Atlassian Complete Suite
### Latest Authentic Images From Source

⏫ Atlassian Suite (Complete) Dockered (from source) Atlassian (Authentic) Jira Software, Jira Service Management, Confluence, Fisheye, Crowd, Bitbucket and Bamboo with latest Postgres DB's

![image](https://user-images.githubusercontent.com/6468571/158800426-8c7c3858-bb3c-4525-b2ce-b636a37fb24b.png)

```

#	▄▀█ ▀█▀ █░░ ▄▀█ █▀ █▀ █ ▄▀█ █▄░█   █▀ █░█ █ ▀█▀ █▀▀ ▀
#	█▀█ ░█░ █▄▄ █▀█ ▄█ ▄█ █ █▀█ █░▀█   ▄█ █▄█ █ ░█░ ██▄ ▄
#	ATLASSIAN SUITE (COMPLETE) DOCKERED (FROM SOURCE) ATLASSIAN
#	===========================================================================
#	        ╔════╗        ╔═══════╗         ╔═════╗      ╔════════╗     ╔═══╗ 
#	░░░██╗░██╗░██████╗░░█████╗░░█████╗░██╗░░██╗███████╗██████╗░███████╗██████╗░
#	██████████╗██╔══██╗██╔══██╗██╔══██╗██║░██╔╝██╔════╝██╔══██╗██╔════╝██╔══██╗
#	╚═██╔═██╔═╝██║░░██║██║░░██║██║░░╚═╝█████═╝░█████╗░░██████╔╝█████╗░░██║░░██║
#	██████████╗██║░░██║██║░░██║██║░░██╗██╔═██╗░██╔══╝░░██╔══██╗██╔══╝░░██║░░██║
#	╚██╔═██╔══╝██████╔╝╚█████╔╝╚█████╔╝██║░╚██╗███████╗██║░░██║███████╗██████╔╝
#	░╚═╝░╚═╝░░░╚═════╝░░╚════╝░░╚════╝░╚═╝░░╚═╝╚══════╝╚═╝░░╚═╝╚══════╝╚═════╝░
#	JIRA, SERVICE, CONFLUENCE, FISHEYE, CROWD, BITBUCKET, BAMBOO & POSTGRES DB
#	===========================================================================

#	 GLOBALS:

	PASSWORD="changeme"	
	NETWORK="jira_fastlane"
	RESTART="always"
	
	docker network create -d bridge $NETWORK
	
#	  .--.      .-'
#	:::::.\::::::::
#	░░█ █ █▀█ ▄▀█ ▀
#	█▄█ █ █▀▄ █▀█ ▄
#	:::::.\::::::::
#	'      `--'    

#	READY?

	host="jira"		
	port="8080"		
	image="atlassian/jira-software"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network=$network --restart=$restart -d -p $port $image

#	🏁 FINISHED

#	  .--.      .-'.      .-
#	:::::.\::::::::.\:::::::
#	█▀ █▀▀ █▀█ █░█ █ █▀▀ █▀▀ ▀
#	▄█ ██▄ █▀▄ ▀▄▀ █ █▄▄ ██▄ ▄
#	:::::.\::::::::.\:::::::
#	'     `--'      `.-'   

#	READY?

	host="service"		
	port="8080"		
	image="atlassian/service-software"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"	
	dbimage="postgres"
	port="${port}:8080"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network=$network --restart=$restart -d -p $port $image

#	🏁 FINISHED

#	  .--.      .-'.      .-.      .-'.      .-
#	:::::.\::::::::.\:::::::.\::::::::.\::::::
#	█▀▀ █▀█ █▄░█ █▀▀ █░░ █░█ █▀▀ █▄░█ █▀▀ █▀▀ ▀
#	█▄▄ █▄█ █░▀█ █▀░ █▄▄ █▄█ ██▄ █░▀█ █▄▄ ██▄ ▄
#	:::::.\::::::::.\:::::::.\::::::::.\:::::::
#	'      `--'      `.-'     `--'      `.-'   

#	READY?

	host="confluence"		
	port="8080"		
	image="atlassian/confluence-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/confluence --name=$host --network=$network --restart=$restart -d -p $port $image

#	FINISHED

#	  .--.      .-'.      .
#	:::::.\::::::::.\::::::
#	█▀▀ █ █▀ █░█ █▀▀ █▄█ █▀▀ ▀
#	█▀░ █ ▄█ █▀█ ██▄ ░█░ ██▄ ▄
#	:::::.\::::::::.\::::::
#	'      `--'      `.-'  

#	READY?

	host="fisheye"		
	port="8080"		
	image="atlassian/fisheye"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/atlassian/data/fisheye --name=$host --network=$network --restart=$restart -d -p $port $image

#	FINISHED

#	  .--.      .-'.      .
#	:::::.\::::::::.\::::::
#	█▀▀ █▀█ █▀█ █░█░█ █▀▄ ▀
#	█▄▄ █▀▄ █▄█ ▀▄▀▄▀ █▄▀ ▄
#	:::::.\::::::::.\::::::
#	'      `--'      `.-' 
 
#	READY?

	host="crowd"		
	port="8080"		
	image="atlassian/crowd"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/crowd --name=$host --network=$network --restart=$restart -d -p $port $image

#	FINISHED

#	  .--.      .-'.      .-.      .-'.
#	:::::.\::::::::.\:::::::.\::::::::.
#	█▄▄ █ ▀█▀ █▄▄ █░█ █▀▀ █▄▀ █▀▀ ▀█▀ ▀
#	█▄█ █ ░█░ █▄█ █▄█ █▄▄ █░█ ██▄ ░█░ ▄
#	:::::.\::::::::.\:::::::.\::::::::.
#	'      `--'      `.-'     `--'     

#	READY?

	host="bitbucket"		
	port="7990"		
	image="atlassian/bitbucket-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:7990"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/bitbucket --name=$host --network=$network --restart=$restart -d -p $port $image

#	FINISHED

#	  .--.      .-'.      .-.  
#	:::::.\::::::::.\:::::::.\:
#	█▄▄ ▄▀█ █▀▄▀█ █▄▄ █▀█ █▀█ ▀
#	█▄█ █▀█ █░▀░█ █▄█ █▄█ █▄█ ▄
#	:::::.\::::::::.\:::::::.\:
#	'      `--'      `.-'     `

#	READY?

	host="bamboo"		
	port="8085"		
	image="atlassian/bamboo-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

	echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

#	SET

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8085"

	echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

#	GO

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart $dbimage
	docker run -v $volume:/var/atlassian/application-data/bamboo  --name=$host --network=$network --restart=$restart -d -p $port $image

[ whereis my head at!

```

![image](https://user-images.githubusercontent.com/6468571/158800560-a2275687-6e5e-451c-a160-0c5debbd8388.png)


![image](https://user-images.githubusercontent.com/6468571/158800519-39280a0c-a555-4c2e-8d67-0632148204c0.png)
