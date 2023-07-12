# tokenbased-authentication
Implement Token-based Authentication with Golang and MySQL Server


## Install this app

### Create the database in local
```
user: "root"
password: ""
database name: "goblog"
```

### Clone this repository
```
$ git clone https://github.com/hashi7412/tokenbased-authentication.git <dir_name>
```

### Download Golang packages that are used for this app
```
$ cd <dir_name>

$ go get github.com/go-sql-driver/mysql

$ go get golang.org/x/crypto/bcrypt
```

### Run this app
```
$ go run ./
```

### Test this app
SSH to your server on another terminal

Add an user to database
```
$ curl -X POST http://localhost:8081/registrations -H "Content-Type: application/x-www-form-urlencoded" -d "username=john_doe&password=EXAMPLE_PASSWORD"
```

Get a time-based token using user's credential in request of `/authentications`
```
$ curl -u john_doe:EXAMPLE_PASSWORD http://localhost:8081/authentications
```

Query any resource that allows authentication using the time-based token: Copy the value of `auth_token` and execute the `curl` command below and include your token in an `Authorization` header proceded by the term `Bearer`
```
$ curl -H "Authorization: Bearer <auth_token>=" http://localhost:8081/test
```

Attempt authenticating to the application using an invalid token (ex: `fakerandomtoken`)
```
$ curl -H "Authorization: Bearer fakerandomtoken" http://localhost:8081/test
```

Attempt requesting a token without a valid user account
```
$ curl -u john_doe:WRONG_PASSWORD http://localhost:8081/authentications
```


## Guide this repository

This repository is for authentication implementation based token with Golang using MySQL as a database

