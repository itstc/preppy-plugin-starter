## Preppy Backend Starter
Easily create a backend plugin for preppy in spring

### Prereqs for production
A database docker container must be active in order to build with docker, as environment variables must be placed to connect to the database.

### Usage:
To work locally, run command `./gradlew bootRun`
To build the plugin run command `./gradlew build`

### Build with docker:
1. Build the image by running command `./gradlew build docker`
2. Once build finished run command `docker run (image name in build.gradle nested in "docker") -p 8080:8080 -e (ENVIRONMENT VARIABLES HERE) `

If you are using docker-compose, put this within your docker-compose.yml
```yml
(container name here):
	image: (plugin image name)
	ports:
		- "8080:8080"
	environment:
		- DB_HOST=(database host)
		- DB_PASS=(database password)
		- DB_PORT=(database port)
		- DB_DATABASE=(database name)
	links:
		- database
	networks:
		- preppynet
```
Then run `docker-compose up -d` to start your plugin
