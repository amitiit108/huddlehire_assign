## Requirements

 - [Node v10+]

#### Install dependencies:

```bash
npm i
```

#### Set environment variables:

```bash
cp .env.example .env
```

## Running Locally

```bash
npm run dev
```
## Docker

```bash
# run container locally
npm run docker


  
1a. Register user :

curl --request POST \
  --url http://localhost:3000/v1/auth/register \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjIzNzQxNDIsImlhdCI6MTYyMjM3MzI0MiwiZW50aXR5IjoiNjBiMzcyZTYyOWFjYWIxMGI4ZTgwNjU0In0.qd7yY_sfLup6mIJ1ILauRlT_mGVjeRd9JvEr8m-QJ28' \
  --header 'Content-Type: application/json' \
  --data '{
         "email": "amit@gmail.com",
         "password": "pass1234",
         "firstName": "amit",
         "lastName": "kumar"
}'



1b. Login User :

curl --request POST \
  --url http://localhost:3000/v1/auth/login \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjIzNzU3OTcsImlhdCI6MTYyMjM3NDg5NywiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.UTc4J5XQ4iFVdoRznT2YOeEMnilCUOnyvpQ9yXWPteI' \
  --header 'Content-Type: application/json' \
  --data '{
         "email": "amit@gmail.com",
         "password": "pass1234"
}'


2a. a registered user should be able to see all comments/subcomments and reactions made on
their "wall". This should return the comment text, when it was created, who created it, and
any reactions made on it.

curl --request GET \
  --url http://localhost:3000/v1/comment \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjI0MjEwMDEsImlhdCI6MTYyMjQyMDEwMSwiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.iJXjdAfcHOo3R9EE_VR533IPJkZlwgOgoXpUhkVP5Jw' \
  --header 'Content-Type: application/json' \
  --data '{
         "text": "amit comment on own comment id"
      }'

3a. A registered user can create comments for his own  wall   

curl --request POST \
  --url http://localhost:3000/v1/comment \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjI0MjM3MTUsImlhdCI6MTYyMjQyMjgxNSwiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.ALhssfTLXqCL829gRljhnDw3UqQXRYXtp8vStBYtoF0' \
  --header 'Content-Type: application/json' \
  --data '{
         "text": "comment"
      }'
	  

	  
4a. A registered user can create comments for his own  comment/subcomment   

curl --request POST \
  --url http://localhost:3000/v1/comment/60b37a9d29acab10b8e80658/reply \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjIzNzU4NjAsImlhdCI6MTYyMjM3NDk2MCwiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.isUFlpho2DU0u82vrqBngOi2r5BZJIFuWClJ-Na_nuM' \
  --header 'Content-Type: application/json' \
  --data '{
         "text": "amit comments on own comment"
      }'
	  
4b. A registered user can create comments for other  comment/subcomment   

curl --request POST \
  --url http://localhost:3000/v1/comment/60b37a9d29acab10b8e80658/reply \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjIzNzY5NzUsImlhdCI6MTYyMjM3NjA3NSwiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.SPqPbnLtVfDSaY2rFIfCEDwgP4dHO1gqJCgwUL58lF8' \
  --header 'Content-Type: application/json' \
  --data '{
         "text": "amit comment on other comment"
      }'


5. a registered user can create reaction on any comment/subcomment.

curl --request POST \
  --url http://localhost:3000/v1/comment/60b38f6329acab10b8e8065d/reaction \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjI0MjIzMTMsImlhdCI6MTYyMjQyMTQxMywiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.pa5sR-e2eALcIM_A3nXxhA7PAPvmW-lttbmOdIUx09s' \
  --header 'Content-Type: application/json' \
  --data '{
         "reaction": "like"
      }'
	  
6.  A registered user can delete their own comment/subcomment - this will also delete all
reactions made on that comment.

curl --request DELETE \
  --url http://localhost:3000/v1/comment/60b37a9d29acab10b8e80658 \
  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjI0MjEwMDEsImlhdCI6MTYyMjQyMDEwMSwiZW50aXR5IjoiNjBiMzc5YmUyOWFjYWIxMGI4ZTgwNjU3In0.iJXjdAfcHOo3R9EE_VR533IPJkZlwgOgoXpUhkVP5Jw' 


