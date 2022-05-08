# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

## **Endpoints**

A API tem um total de 3 endpoints, sendo 2 para dados e um para autenticação, podemos postar posts que todos conseguem visualizar mas apenas usuarios logados podem escreve-los, temos tambem os reports que são arquivos que apenas usuarios logados conseguem acessa-los.

rota: `https://fake-api-rodrigomero.herokuapp.com/`

## Rotas que não precisam de autenticação

<h2 align ='center'> Listando posts </h2>

`GET /posts - FORMATO DA RESPOSTA - STATUS 200`

```
[
	{
		"title": "Javascript",
		"data": "Javascrippppt",
		"id": 1
	},
	{
		"userId": 1,
		"title": "Javascript",
		"data": "Javascrippppt",
		"id": 2
	}
]
```

<h2 align ='center'> Login </h2>

`GET /login - FORMATO DA RESPOSTA - STATUS 200`

```
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImtlbnppbmhvQG1haWwuY29tIiwiaWF0IjoxNjUyMDUwNDYwLCJleHAiOjE2NTIwNTQwNjAsInN1YiI6IjEifQ.OpsvqhqK6ja_gLFfL7a0yFcOGSuxjNm5tyF1U8CHUlU",
	"user": {
		"email": "kenzinho@mail.com",
		"name": "Kenzinho",
		"age": 38,
		"id": 1
	}
}
```

## Rotas que precisam de autenticação

para acessar essas rotas é necessário passar como parametro o token do usuario

<h2 align ='center'> Listando reports </h2>

`GET /reports - FORMATO DA RESPOSTA - STATUS 200`

```
[
	{
		"userId": 1,
		"data": {
			"title": "title1",
			"content": "paragraph1"
		},
		"id": 1
	}
]
```

<h2 align ='center'> Postando reports </h2>

É necessario passar o `userId` no header da requisição:

`POST /reports - FORMATO DA RESPOSTA - STATUS 201`

```
{
	"userId": 1,
	"data": {
		"title": "title1",
		"content": "paragraph1"
	},
	"id": 1
}
```

<h2 align ='center'> Postando posts </h2>

É necessario passar o `userId` no header da requisição:

`POST /posts - FORMATO DA RESPOSTA - STATUS 201`

```
{
	"userId": 1,
	"title": "Javascript",
	"data": "Javascrippppt",
	"id": 2
}
```

<h2 align ='center'> Listar usuário </h2>

É necessario passar o `userId` no endpoint da requisicao.

`GET /users/{userId} - FORMATO DA RESPOSTA - STATUS 200`

```
{
	"email": "kenzinho@mail.com",
	"password": "$2a$10$YQiiz0ANVwIgpOjYXPxc0O9H2XeX3m8OoY1xk7OGgxTnOJnsZU7FO",
	"name": "Kenzinho",
	"age": 38,
	"id": 1
}
```
