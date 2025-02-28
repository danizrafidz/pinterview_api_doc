# Pinterview API Documentation

## Deployed server

- url : [http://localhost:3001/](http://localhost:3001/)

- registered user :

```js
admin = { email: "admin.alpha@mail.com", password: "adminalpha" };
user = { email: "red.romeo@mail.com", password: "redromeo" };
```

&nbsp;

## Models :

_User_

```

- _id: ObjectId;
- fullName: string (validation: required)
- email: string (validation: required, unique, email format)
- password: string (validation: required, length min 5)
- birthDate: string
- quota: number (default: 3)
- createdAt: date
- updatedAt: date

```

_Job_

```

- _id: ObjectId,
- userId: ObjectId,
- company: string (validation: required)
- position: string (validation: required)
- description: string (validation: required)
- skills: []string (validation: required)
- requirements: []string (validation: required)
- status: string (default: "ongoing")
- readiness: number (default: "-")
- createdAt: date,
- updatedAt: date,

```

_Test_

```

- _id: ObjectId
- jobId: ObjectId
- category: string (validation: required)
- summary: string
- score: number
- createdAt: date
- updatedAt: date

```

_Question_

```
- _id: ObjectId
- testId: ObjectId
- type: string
- question: string
- expectedAnswer: string
- answer: string
- feedback: string
- correctness: number
- createdAt: date
- updatedAt: date

```

_Todo_

```

- _id: ObjectId
- jobId: ObjectId
- activity: string
- notes: string
- status: string
- createdAt: date
- updatedAt: date

```

_Transaction_

```

- _id: ObjectId
- userId: ObjectId
- amount: number (default: 0)
- status: string
- createdAt: date
- updatedAt: date

```

&nbsp;

## Endpoints :

List of available endpoints :

- `POST /register`
- `POST /login`

And routes below need authentication :

- `GET /jobs`
- `POST /jobs`
- `GET /jobs/:id`
- `POST /jobs/:id/tests`
- `GET /jobs/:id/tests/:id`

&nbsp;

## 1. POST /register

Request:

- body:

```json
{
  "fullName": "string",
  "email": "string",
  "password": "string",
  "birthDate": "string",
}
```

_Response (201 - Created)_

```json
{
  "_id": "67a9c7e23fa25c2b0cecd576",
  "fullName": "Dummy Delta",
  "email": "dummy@mail.com",
  "password": "dummy",
  "birthDate": "2001/10/03",
  "quota": 3,
  "createdAt": "2025-02-11T12:30:22.851+00:00",
  "updatedAt": "2025-02-11T12:30:22.851+00:00"
}
```

_Response (400 - Bad Request)_

```json
{
  "message": "Full Name is required"
}
OR
{
  "message": "Email is required"
}
OR
{
  "message": "Invalid email format"
}
OR
{
  "message": "Email must be unique"
}
OR
{
  "message": "Password is required"
}
OR
{
  "message": "Team is required"
}
```

&nbsp;

## 2. POST /login

Request:

- body:

```json
{
  "email": "string",
  "password": "string"
}
```

_Response (200 - OK)_

```json
{
  "access_token": "string"
}
```

_Response (400 - Bad Request)_

```json
{
  "message": "Email is required"
}
OR
{
  "message": "Password is required"
}
```

_Response (401 - Unauthorized)_

```json
{
  "message": "Invalid email/password"
}
```

&nbsp;

## 2. POST /login

Request:

- body:

```json
{
  "email": "string",
  "password": "string"
}
```

_Response (200 - OK)_

```json
{
  "access_token": "string"
}
```

_Response (400 - Bad Request)_

```json
{
  "message": "Email is required"
}
OR
{
  "message": "Password is required"
}
```

_Response (401 - Unauthorized)_

```json
{
  "message": "Invalid email/password"
}
```

&nbsp;

## Global Errror

_Response (401 - Unauthorized)_

```json
{
  "message": "Invalid token"
}
```

_Response (500 - Internal Server Error)_

```json
{
  "message": "Internal server error"
}
```
