---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

---

# Introduction

Welcome to the <a href='https://node-rest-users.herokuapp.com/users'>node-rest-users</a> API! You can use our API to access the API endpoints, which can get information on various users and modify it in our database.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate).

[comment]: <> (<aside class="notice">You must replace <code>meowmeowmeow</code> with your personal API key.</aside>)
[comment]: <> (<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>)
[comment]: <> (<aside class="success">Remember — a happy kitten is an authenticated kitten!</aside>)

# Users

## Get All Users

```shell
curl -X GET https://node-rest-users.herokuapp.com/users | json_pp 
```

```json
```

> The above command returns JSON structured like this:

```json
{
    "message": "Handling GET requests to /users",
    "allUsers": [{
        "_id": "5e6b8dd7c7abfc0d9f760904",
        "fname": "Jane",
        "lname": "Doe",
        "age": 20,
        "isvip": false,
        "__v": 0
    }, {
        "_id": "5e6ba3cf45f0a21ad4e0b7c1",
        "fname": "John",
        "lname": "Doe",
        "age": 20,
        "isvip": true,
        "__v": 0
    }, {
        "_id": "5e7601e78b107401997099f7",
        "__v": 0,
        "age": 80,
        "fname": "Anna",
        "isvip": false,
        "lname": "Frank"
    }, {
        "_id": "5e7601fb8b107401997099f8",
        "__v": 0,
        "age": 10,
        "fname": "Jim",
        "isvip": false,
        "lname": "Morrison"
    }]
}
```

This endpoint retrieves all users.

### HTTP Request
`GET /users HTTP/1.1
Host: node-rest-users.herokuapp.com`

## Create Single User
```shell
curl --header "Content-Type: application/json" --request POST --data '{"fname":"John","lname":"Doe","age":"10","isvip":"true"}' --url 'https://node-rest-users.herokuapp.com/users/' | json_pp
```

```json
{
  "fname": "John",
  "lname": "Doe",
  "age": 5,
  "isvip": true
}
```

> The above command returns JSON structured like this:

```json
{
    "message": "Handling POST requests to /users",
    "createdUser": {
        "_id": "5e7f8fc8789e8a00178b4210",
        "fname": "John",
        "lname": "Doe",
        "age": 5,
        "isvip": true
    }
}
```

This endpoint creates a single user.

### HTTP Request
`POST /users/ HTTP/1.1
Host: node-rest-users.herokuapp.com
Content-Type: application/json
Content-Length: 74

{
  "fname": "Something",
  "lname": "Something",
  "age": 5,
  "isvip": true
}`


### Parameters

Parameter | Type | Description
--------- | ---- | -----------
fname | string | The User's first name.
lname | string | The User's last name.
age | integer | The User's age.
isvip | boolean | Indicator that shows whether the User is a VIP member or not.

## Edit Single User
```shell
curl --header "Content-Type: application/json" --request PATCH --data '[{"propName":"fname","value":"Something"}]' --url 'https://node-rest-users.herokuapp.com/users/5e7f9750789e8a00178b4213' | json_pp
```

```json
[
  {"propName":"fname", "value":"Something"},
  {"propName":"lname", "value":"Something"},
  {"propName":"age", "value":"19"},
  {"propName":"isvip", "value":"true"}
]
```

> The above command returns JSON structured like this:

```json
{
    "message": {
        "n": 1,
        "nModified": 1,
        "opTime": {
            "ts": "6809344432156966913",
            "t": 3
        },
        "electionId": "7fffffff0000000000000003",
        "ok": 1,
        "$clusterTime": {
            "clusterTime": "6809344432156966913",
            "signature": {
                "hash": "+k6TVvm1YeyIoNDypkDIXnWrj8k=",
                "keyId": "6802959550954602498"
            }
        },
        "operationTime": "6809344432156966913"
    }
}
```

This endpoint edits a single user.

### HTTP Request
`PATCH /users/5e7f9750789e8a00178b4213 HTTP/1.1
Host: node-rest-users.herokuapp.com
Content-Type: application/json
Content-Length: 163

[
  {"propName":"fname", "value":"Something"},
  {"propName":"lname", "value":"Something"},
  {"propName":"age", "value":"19"},
  {"propName":"isvip", "value":"true"}
]`

### Parameters

Parameter | Description
--------- | -----------
propname| Any of the Parameters passed when creating the User.
value | The new value that we want to assign to that parameter.

## Delete Single User
```shell
curl --request DELETE --url 'https://node-rest-users.herokuapp.com/users/<UserIdHere>' | json_pp
```

```json
```

> The above command returns JSON structured like this:

```json
{
    "n": 1,
    "opTime": {
        "ts": "6809337216611909633",
        "t": 3
    },
    "electionId": "7fffffff0000000000000003",
    "ok": 1,
    "$clusterTime": {
        "clusterTime": "6809337216611909633",
        "signature": {
            "hash": "R/CDpuf1ENSJXV/VpIcp6EqUAGM=",
            "keyId": "6802959550954602498"
        }
    },
    "operationTime": "6809337216611909633",
    "deletedCount": 1
}
```

This endpoint deletes single user's data.

### HTTP Request
`DELETE /users/<UserIdHere> HTTP/1.1
Host: node-rest-users.herokuapp.com`

<aside class="success">Remember: Change <UserIdHere> to the actual ID E. g. <i>5e7601fb8b107401997099f8</i></aside>

## Get Single User
```shell
curl -X GET https://node-rest-users.herokuapp.com/users/<UserIdHere> | json_pp
```

```json
```

> The above command returns JSON structured like this:

```json
{
   "message" : "Handling GET requests to /users/id",
   "createdUser" : {
      "__v" : 0,
      "age" : 10,
      "fname" : "Jim",
      "isvip" : false,
      "_id" : "5e7601fb8b107401997099f8",
      "lname" : "Morrison"
   }
}
```

This endpoint retrieves single user's data.

### HTTP Request
`GET /users/<UserIdHere> HTTP/1.1
Host: node-rest-users.herokuapp.com`

<aside class="success">Remember: Change <UserIdHere> to the actual ID E. g. <i>5e7601fb8b107401997099f8</i></aside>
