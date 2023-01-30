# Yape-Code-Challenge
### Tech Stack:
- NestJS
- Typescript
- GraphQL
- Kafka
- Postgres
- Docker
* [![NestJS][NestJS]][NestJS-url]
* [![Prisma][Prisma]][Prisma-url]


## Main Setup

1. Root directory contains a `docker-compose.yml` file. Run `docker-compose up -d` to create docker containers in detached mode.

## TRANSACTION MANAGER Microservice Setup

1. Go to directory `transaction-manager-ms`
2. Run `npm i` to install dependencies.
3. Create the .env file and insert your values the following variables (for DB credentials use the same defined in the docker-compose file).
	```
	API_PORT=5001
	DATABASE_URL=postgresql://<USER_DB>:<PASS_DB>@localhost:5432/reto_yape_dev?connect_timeout=300
	KAFKA_BROKER=localhost:9092
	```
4. Run `npm run start:prisma` to generate prisma dependencies.
5. Run `npm run start:dev` to start the microservice.

## ANTI-FRAUD Microservice Setup

1. Go to directory `transaction-manager-ms`
2. Run `npm i` to install dependencies.
3. Create the .env file and insert your values the following variables.
	```
	KAFKA_BROKER=localhost:9092
	```
4. Run `npm run start:dev` to start the microservice.


# GraphQL API Documentation

Open your browser and go to http://localhost:5001/graphql

### Create transaction
```graphql
mutation  {
  createTransaction(createTransactionInput:{
    accountExternalIdDebit: "c3281685-b097-4d9a-a284-ef232af5eb32" ,
    accountExternalIdCredit: "ca7a6efa-e39f-4650-af63-2e40455850ce",
    transferTypeId: 1,
    value: 999.9
  }){
    transactionExternalId,
    transactionType{name},
    transactionStatus{name},
    value,
    createdAt
  }
}
```


### Retrieve transaction
```graphql
query{
  retrieveTransactionById(id:"ca7a6efa-e39f-4650-af63-2e40455850ce"){
    transactionExternalId,
    transactionType{name},
    transactionStatus{name},
    value,
    createdAt
  }
}
```

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[NestJS ]: https://d33wubrfki0l68.cloudfront.net/e937e774cbbe23635999615ad5d7732decad182a/26072/logo-small.ede75a6b.svg
[NestJS-url]: https://nestjs.com/
[Prisma]: https://prismalens.vercel.app/header/logo-dark.svg
[Prisma-url]: https://www.prisma.io/