
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

##### GLOBALS:

	PASSWORD="changeme"	
	NETWORK="jira_fastlane"
	RESTART="always"

# ================

#	░░█ █ █▀█ ▄▀█ ▀
#	█▄█ █ █▀▄ █▀█ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database jira_db -host jira_db -user jira_db_user -password changeme -port 5432

### READY? ###

	host="jira"		
	port="8080"		
	image="atlassian/jira-software"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}" \n\n#\n# #\n# # #\n# # # # GO!!! \n# # #\n# #\n#\n\n"

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

#	================

#	█▀ █▀▀ █▀█ █░█ █ █▀▀ █▀▀ ▀
#	▄█ ██▄ █▀▄ ▀▄▀ █ █▄▄ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database service_db -host service_db -user service_db_user -password changeme -port 5432

### READY? ###

	host="service"		
	port="8080"		
	image="atlassian/service-software"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

# ================

#	█▀▀ █▀█ █▄░█ █▀▀ █░░ █░█ █▀▀ █▄░█ █▀▀ █▀▀ ▀
#	█▄▄ █▄█ █░▀█ █▀░ █▄▄ █▄█ ██▄ █░▀█ █▄▄ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database confluence_db -host confluence_db -user confluence_db_user -password changeme -port 5432

### READY? ###

	host="confluence"		
	port="8080"		
	image="atlassian/confluence-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/confluence --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

# ================

#	█▀▀ █ █▀ █░█ █▀▀ █▄█ █▀▀ ▀
#	█▀░ █ ▄█ █▀█ ██▄ ░█░ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database fisheye_db -host fisheye_db -user fisheye_db_user -password changeme -port 5432

### READY? ###

	host="fisheye"		
	port="8080"		
	image="atlassian/fisheye"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/atlassian/data/fisheye --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

# ================

#	█▀▀ █▀█ █▀█ █░█░█ █▀▄ ▀
#	█▄▄ █▀▄ █▄█ ▀▄▀▄▀ █▄▀ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database crowd_db -host crowd_db -user crowd_db_user -password changeme -port 5432

### READY? ###

	host="crowd"		
	port="8080"		
	image="atlassian/crowd"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8080"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/crowd --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

# ================

#	█▄▄ █ ▀█▀ █▄▄ █░█ █▀▀ █▄▀ █▀▀ ▀█▀ ▀
#	█▄█ █ ░█░ █▄█ █▄█ █▄▄ █░█ ██▄ ░█░ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database bitbucket_db -host bitbucket_db -user bitbucket_db_user -password changeme -port 5432

### READY? ###

	host="bitbucket"		
	port="7990"		
	image="atlassian/bitbucket-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:7990"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/bitbucket --name=$host --network=$network --restart=$restart -d -p $port image

### FINISHED!!! ###

# ================

#	█▄▄ ▄▀█ █▀▄▀█ █▄▄ █▀█ █▀█ ▀
#	█▄█ █▀█ █░▀░█ █▄█ █▄█ █▄█ ▄
#	LOCALHOST: http://localhost:8085/
#	DATABASE: -database bamboo_db -host bamboo_db -user bamboo_db_user -password changeme -port 5432

### READY? ###

	host="bamboo"		
	port="8085"		
	image="atlassian/bamboo-server"
	password=$PASSWORD
	network=$NETWORK
	restart=$RESTART

echo "host: ${host} | port: ${host} | image: ${image} | password: ${password} | network: ${network} | restart: ${restart}"

### SET ###

	volume="${host}_volume"		
	dbvolume="${host}_db_volume"	
	dbhost="${host}_db"
	database="{host}_db"
	dbuser="{host}_db_user"		
	dbimage="postgres"
	port="${port}:8085"

echo "volume: ${volume} | dbvolume: ${dbvolume} | dbhost: ${dbhost} | database: ${database} | dbuser: ${dbuser} | dbimage: ${dbimage} | port: ${port}"

### GO GO GO ###

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/bamboo  --name=$host --network=$network --restart=$restart -d -p $port image

[ whereis my brain?

```
