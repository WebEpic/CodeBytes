#CodeByte API

`base_url: https://pacific-hamlet-4796.herokuapp.com/`

###Quick Find:

####Users

* [Authenticate User](#authenticate-user)
`POST '/auth/github'`
* [Get Authenticated User](#get-authenticated-user)
`GET '/me'`
* [List All Users](#list-all-users)
`GET '/users'`
* [Find User By Id](#find-user-by-id)
`GET /users/:id`
* [List a User's Posts](#list-a-users-posts)
`GET /users/:id/posts`

####Posts

* [Create a Post](#create-a-post)
`POST '/posts'`
* [Get all Posts](#get-all-posts)
`GET '/posts'`
* [Update a Post](update-a-post)
`PUT '/posts/:id'`
* [Delete a Post](#delete-a-post)
`DELETE '/posts/:id'`

####Voting

* [Add an Upvote](#add-an-upvote)
`PUT 'posts/like'`
* [Add a Downvote](#get-all-posts)
`PUT 'posts/dislike'`


All authenticated requests are made by passing 'Authorization' in the request header.  That header will contain the JWT token returned after authentication.

###Authenticate User

`POST '/auth/github'`

Returns a JWT token.

Required Params: 

* `code` => `string`, temporary code returned by callback URL

* `clientId` => `string`, known client ID of github App

* `redirectUri` => `string`, callback URL

Example Response:

Status code:

```json
{
"token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ1c2VyX2lkIjoxNn0.pGJXRN1Y32xO9ilKn-j7wdkK7CBUpCp49D7j-72Kokp1_bG09wphgTr0dimiJ8Fsqsut19SY3EYwMxkvGDqvZg"
}
```

###Get Authenticated User

`GET '/me'`

Returns the user object for the authenticated user.

No required params. 

User must be authenticated.

Example response:

Status code:`200`

```json
   {
    "id": 18,
    "email": "mdaugherty6@gmail.com",
    "password": "06becd1d7421eeff5846e0e2c3a4b27c",
    "username": "taylor-d",
    "github": "9401828",
    "created_at": "2015-07-08T17:57:24.732Z",
    "updated_at": "2015-07-10T00:30:14.142Z",
    "avatar": "https://avatars.githubusercontent.com/u/9401828?v=3",
    "company": "",
    "url": "https://api.github.com/users/taylor-d",
    "location": "Atlanta, GA",
    "follower_count": 13,
    "following_count": 17,
    "public_gists": 3,
    "hireable": true,
    "blog": "http://www.taylormath.com"
  }
```

###List all Users

`GET '/users'`

No required params.

Example Response:
```json
[
  {
    "id": 18,
    "email": "mdaugherty6@gmail.com",
    "password": "06becd1d7421eeff5846e0e2c3a4b27c",
    "username": "taylor-d",
    "github": "9401828",
    "created_at": "2015-07-08T17:57:24.732Z",
    "updated_at": "2015-07-10T00:30:14.142Z",
    "avatar": "https://avatars.githubusercontent.com/u/9401828?v=3",
    "company": "",
    "url": "https://api.github.com/users/taylor-d",
    "location": "Atlanta, GA",
    "follower_count": 13,
    "following_count": 17,
    "public_gists": 3,
    "hireable": true,
    "blog": "http://www.taylormath.com"
  }
]
```

###Find user by id

`GET '/users/:id'`

Required params:

* `id` => `string`, user id

Example Response:

```json
{
  "id": 18,
  "email": "mdaugherty6@gmail.com",
  "password": "06becd1d7421eeff5846e0e2c3a4b27c",
  "username": "taylor-d",
  "github": "9401828",
  "created_at": "2015-07-08T17:57:24.732Z",
  "updated_at": "2015-07-10T00:30:14.142Z",
  "avatar": "https://avatars.githubusercontent.com/u/9401828?v=3",
  "company": "",
  "url": "https://api.github.com/users/taylor-d",
  "location": "Atlanta, GA",
  "follower_count": 13,
  "following_count": 17,
  "public_gists": 3,
  "hireable": true,
  "blog": "http://www.taylormath.com"
}
```

###List a user's posts

`GET '/users/:id/posts'`

Required params:

* `id` => `string`, user id


Example Response:

```json
[
  {
    "id": 1,
    "title": "test",
    "content": "test",
    "user_id": 18,
    "created_at": "2015-07-10T00:50:43.473Z",
    "updated_at": "2015-07-10T00:50:43.473Z"
  }
]
```

###Create a Post

`POST '/posts'`

Creates a post.  User must be authenticated.

Required Params: 

* `title` => `string`, title of the post

* `content` => `string`, content of post

Example response:

Status code:`200`

```json
{
  "id": 1,
  "title": "test",
  "content": "test",
  "user_id": 18,
  "created_at": "2015-07-10T00:50:43.473Z",
  "updated_at": "2015-07-10T00:50:43.473Z"
}
```

###Get all Posts

`GET '/posts'`

Returns all posts from all users.

No required params.

Example response:

Status code:`200`

```json
[
	{
	  "id": 1,
	  "title": "test",
	  "content": "test",
	  "user_id": 18,
	  "created_at": "2015-07-10T00:50:43.473Z",
	  "updated_at": "2015-07-10T00:50:43.473Z"
	},
	{
	  "id": 2,
	  "title": "test",
	  "content": "test",
	  "user_id": 18,
	  "created_at": "2015-07-10T00:50:43.473Z",
	  "updated_at": "2015-07-10T00:50:43.473Z"
	},
	{
	  "id": 3,
	  "title": "test",
	  "content": "test",
	  "user_id": 18,
	  "created_at": "2015-07-10T00:50:43.473Z",
	  "updated_at": "2015-07-10T00:50:43.473Z"
	}
]
```

###Update a Post

`PUT '/posts/:id'`

Updates a post

No required params.

Options params:

* `title` => `string`, title of the post

* `content` => `string`, content of post

Example Response: 

Status code:`200`

```json
{
  "id": 1,
  "title": "test",
  "content": "test",
  "user_id": 18,
  "created_at": "2015-07-10T00:50:43.473Z",
  "updated_at": "2015-07-10T00:50:43.473Z"
}
```

###Delete a Post

`DELETE '/posts/:id'`

Deletes a post.

No required params.

Example Response:

Status code:`200`

```json
{}
```

###Add an Upvote

`PUT 'posts/:id/like'`

Adds an upvote (agreement).

No required params.

Example Response:

Status code:`200`

```json
having issues spinning up a server on my local machine. will add json response on Monday
```

###Add a Downvote

`PUT 'posts/:id/dislike'`

Adds a downvote (disagreement).

No required params.

Example Response:

Status code:`200`

```json
having issues spinning up a server on my local machine. will add json response on Monday
```








