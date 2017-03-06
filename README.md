# Wordy Ninja Blog
Wordy Ninja Blog is an application for demonstrating security concepts.

# WARNING: this application intentionally contains security vulnerabilities.

# Build & Run

To run the application locally, you need to have mysql installed and create a database of wordyninjadb and a user and password of wordyninja/wordyninja+1

```
mysql -e "create database wordyninjadb"
mysql -e "CREATE USER 'wordyninja'@'%' IDENTIFIED BY 'wordyninja+1';"
mysql -e "GRANT ALL PRIVILEGES ON *.* TO 'wordyninja'@'%'"
```

You can build and run the project on the command-line using:

```
./gradlew build
java -jar build/libs/wordyninjablog.war
```

Or you can build and run a docker image using:

```
./gradlew build buildDocker
docker run --name wordyninjadb \
    -e MYSQL_ROOT_PASSWORD=root+1 \
    -e MYSQL_DATABASE=wordyninjadb \
    -e MYSQL_USER=wordyninja \
    -e MYSQL_PASSWORD=wordyninja+1 \
    -d mysql:latest
docker run -p 8080:8080 --link wordyninjadb:mysql  -it --rm javajudd/wordyninjablog:latest
```