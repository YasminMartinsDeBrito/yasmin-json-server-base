# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 6 endpoints , 1  para cadastro de usuario, 1 para login, 1 para cadastro de animais, 1 para acessar todos os animais,1 para cadastro de endereco,1 para ver enderecos cadastrados

O url base da API é: 
## (https://yasmin-json-server-base.herokuapp.com/)


## Cadastro
POST /register <br/>
##### Para cadastra usuarios
{
	"email": "elton@gmail.com",
	"password": "123456",
	"name": "Elton",
	"age": 24
}
****************************************

## Login
POST /login <br/>
##### Para Logar Usuarios Cadastrados
{
	"email": "elton@gmail.com",
	"password": "123456"
}

*********************************************
# Precisa de Autorização Token
## Animals
GET / animals <br/>

POST /animals <br/>

## /644/*	O usuário deve possuir o recurso para gravar o recurso.Todos podem ler o recurso.

##### Deve adicionar o nesse formato 'userId'  do usuario Logado
##### Para cadastra animal
{
	"type": "Passarinho",
	"name": "Urubu",
	"userId":2
}

*******************************************
# Precisa de Autorização Token
## Endereços
GET /endereco <br/>

POST /endereco <br/>
 
 ## /640/*	O usuário deve possuir o recurso para gravar o recurso. O usuário deve estar logado para ler o recurso.
{
	"cep": 13737395,
	"rua": "Honorio Ferreira Pinto",
	"number": 299,
	"cidade": "Mococa",
	"estado": "SP",
	"userId":2
}
**************************************

## Filtrar(Pesquisar)

#### Nos animais <br/>
###### pode ser filtrado por Tipo = type
###### pode ser filtrado por Name = name
/animals?type=Gato <br/>

### filtrandos Animais pelo type
[
  {
    "type": "Gato",
    "name": "toby",
    "userId": 3,
    "id": 1
  },
  {
    "type": "Gato",
    "name": "Mini",
    "userId": 3,
    "id": 2
  }
]

****************************************************
/animals?name=toby <br/>
### filtrando Animais pelo nome
[
  {
    "type": "Gato",
    "name": "toby",
    "userId": 3,
    "id": 1
  }
]
*******************************************

### Nos Enderecos <br/>
###### pode ser filtrado por Numero = number
###### pode ser filtrado por Cidade = cidade
###### pode ser filtrado por Cep = cep

/endereco?number=299 <br/>

### filtrando Endereco pelo Numero
{
  "cep": 13737266,
  "rua": "Angelo Abeline",
  "number": 166,
  "cidade": "Mococa",
  "estado": "SP",
  "userId": 2,
  "id": 3
}

/endereco?cidade=Mococa <br/>
### filtrando Endereco pela Cidade
[
  {
    "cep": 13737395,
    "rua": "Honorio Ferreira Pinto",
    "number": 299,
    "cidade": "Mococa",
    "estado": "SP",
    "userId": 2,
    "id": 2
  },
  {
    "cep": 13737266,
    "rua": "Angelo Abeline",
    "number": 166,
    "cidade": "Mococa",
    "estado": "SP",
    "userId": 2,
    "id": 3
  },
  {
    "cep": 13737266,
    "rua": "Angelo Abeline",
    "number": 166,
    "cidade": "Mococa",
    "estado": "SP",
    "userId": 2,
    "id": 4
  }
]
/endereco?cep=13737395 <br/>
### filtrando endereco pelo cep
[
  {
    "cep": 13737395,
    "rua": "Honorio Ferreira Pinto",
    "number": 299,
    "cidade": "Mococa",
    "estado": "SP",
    "userId": 2,
    "id": 2
  }
]
