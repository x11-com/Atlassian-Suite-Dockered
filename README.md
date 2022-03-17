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

######### READY #########

QUICK START:

sudo apt-get install zenity		# <-- GUI

PASSWORD = "changeme"			# <-- globals
NETWORK = "jira_fastlane"		# <-- globals
RESTART = "always"				# <-- globals

#	░░█ █ █▀█ ▄▀█ ▀
#	█▄█ █ █▀▄ █▀█ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database jira_db -host jira_db -user jira_db_user -password changeme -port 5432

########## READY ##########

	host = "jira"						# <-- varible
	port = "8080"						# <-- varible
	image = "atlassian/jira-software"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8080"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▀ █▀▀ █▀█ █░█ █ █▀▀ █▀▀ ▀
#	▄█ ██▄ █▀▄ ▀▄▀ █ █▄▄ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database service_db -host service_db -user service_db_user -password changeme -port 5432

########## READY ##########

	host = "service"						# <-- varible
	port = "8080"						# <-- varible
	image = "atlassian/service-software"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8080"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/jira --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▀▀ █▀█ █▄░█ █▀▀ █░░ █░█ █▀▀ █▄░█ █▀▀ █▀▀ ▀
#	█▄▄ █▄█ █░▀█ █▀░ █▄▄ █▄█ ██▄ █░▀█ █▄▄ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database confluence_db -host confluence_db -user confluence_db_user -password changeme -port 5432

########## READY ##########

	host = "confluence"						# <-- varible
	port = "8080"						# <-- varible
	image = "atlassian/confluence-server"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8080"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/confluence --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▀▀ █ █▀ █░█ █▀▀ █▄█ █▀▀ ▀
#	█▀░ █ ▄█ █▀█ ██▄ ░█░ ██▄ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database fisheye_db -host fisheye_db -user fisheye_db_user -password changeme -port 5432

########## READY ##########

	host = "fisheye"						# <-- varible
	port = "8080"						# <-- varible
	image = "atlassian/fisheye"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8080"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/atlassian/data/fisheye --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▀▀ █▀█ █▀█ █░█░█ █▀▄ ▀
#	█▄▄ █▀▄ █▄█ ▀▄▀▄▀ █▄▀ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database crowd_db -host crowd_db -user crowd_db_user -password changeme -port 5432

########## READY ##########

	host = "crowd"						# <-- varible
	port = "8080"						# <-- varible
	image = "atlassian/crowd"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8080"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/crowd --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▄▄ █ ▀█▀ █▄▄ █░█ █▀▀ █▄▀ █▀▀ ▀█▀ ▀
#	█▄█ █ ░█░ █▄█ █▄█ █▄▄ █░█ ██▄ ░█░ ▄
#	LOCALHOST: http://localhost:8080/
#	DATABASE: -database bitbucket_db -host bitbucket_db -user bitbucket_db_user -password changeme -port 5432

########## READY ##########

	host = "bitbucket"						# <-- varible
	port = "7990"						# <-- varible
	image = "atlassian/bitbucket-server"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:7990"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/bitbucket --name=$host --network = $network --restart = $restart -d -p $port image

####### FINISHED #######

#	█▄▄ ▄▀█ █▀▄▀█ █▄▄ █▀█ █▀█ ▀
#	█▄█ █▀█ █░▀░█ █▄█ █▄█ █▄█ ▄
#	LOCALHOST: http://localhost:8085/
#	DATABASE: -database bamboo_db -host bamboo_db -user bamboo_db_user -password changeme -port 5432

########## READY ##########

	host = "bamboo"						# <-- varible
	port = "8085"						# <-- varible
	image = "atlassian/bamboo-server"	# <-- varible
	password=$PASSWORD					# <-- override
	network=$NETWORK					# <-- override
	restart=$RESTART					# <-- override

########## SET ##########

	volume = "${host}_volume"			# <-- varible
	dbvolume = "${host}_db_volume"		# <-- varible
	dbhost = "${host}_db"				# <-- varible
	database = "{host}_db"				# <-- varible
	dbuser = "{host}_db_user"			# <-- varible
	dbimage = "postgres"				# <-- varible
	port = "${port}:8085"				# <-- override

########## GO ##########

	docker volume create --name $dbvolume
	docker run -v $dbvolume:/var/lib/postgresql/data --name $dbhost -d -e 'POSTGRES_DB=$database' -e 'POSTGRES_USER=$dbuser' -e 'POSTGRES_PASSWORD=$password' --network=$network --restart=$restart dbimage
	docker run -v $volume:/var/atlassian/application-data/bamboo  --name=$host --network = $network --restart = $restart -d -p $port image

```

![image](https://user-images.githubusercontent.com/6468571/158800560-a2275687-6e5e-451c-a160-0c5debbd8388.png)


![image](https://user-images.githubusercontent.com/6468571/158800519-39280a0c-a555-4c2e-8d67-0632148204c0.png)

