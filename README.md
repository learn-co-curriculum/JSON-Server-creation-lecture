# JSON-Server-creation

## Objectives
- [ ] Understand How JSON server works.
- [ ] Create a JSON server from scratch
- [ ] Use POSTMAN to make CRUD requests to your JSON server

## Outline

```txt
5 min - Activation - What is a JSON server?
5 min - Installation - JSON server & POSTMAN
15 min - Demonstration - Create JSON file and make a `GET` request from POSTMAN
5 min - Check for understanding - `GET` request
15 min - Demonstration - `POST`, `PATCH`, `DELETE`
5 min - Demonstration - Changes in JSON file
10 min - Check for understanding - `POST`, `PATCH`, `DELETE`
---
60 min
```

## What is a JSON server?

JSON server brainstorm

* Discuss what is a need of JSON server?
    * A common task for front-end developers is to simulate a backend REST service to deliver some data in JSON format to the front-end application and make sure everything is working as expected.
* What is a JSON Server?
    * The json-server is a JavaScript library to create testing REST API.
    * JSON Server helps you to setup a REST API with CRUD operations very fast.

## Setting up Postman

* What is Postman?
    * Postman is an application that allows us to mock up frontend requests without writing any JavaScript. With Postman, we can practice sending requests to our JSON Server.

If students don't have already installed Postman: Head over to https://www.postman.com/downloads/ and click Download the App. **Make sure to mention:** There is a web version of Postman, but this will not work with our localhost server.

## Setting up JSON Server
JSON Server is available as a NPM package. The installation can be done by using the Node.js package manager:

`npm install -g json-server`

By adding the -g option we make sure that the package is installed globally on your system.

Next, we'll need to create a file that will act as our data storage.

`touch db.json`

This file contains the data which should be exposed by the REST API. For objects contained in the JSON structure CRUD entpoints are created automatically.

Add data to `db.json` file:

```json=
{
    "animals": [
      {
        "id": 1,
        "name": "Red Panda",
        "imageUrl": "https://i1.wp.com/www.redpandanetwork.org/wp-content/uploads/2018/10/Photo-1-for-Give-page.png?fit=584%2C584&ssl=1",
        "description": "not actually a panda",
        "donations": 10
      },
      {
        "id": 2,
        "name": "Pangolin",
        "imageUrl": "https://i.pinimg.com/originals/bf/ff/93/bfff9395c6ae0d24534f030580924c7e.jpg",
        "description": "The Pangolin, otherwise known as the scaly anteater, is the only mammal in the world to be covered from head to toe in keratin scales (the same as human finger nails).",
        "donations": 0
      },
      {
        "id": 3,
        "name": "Mantis Shrimp",
        "imageUrl": "https://media.wired.com/photos/5bc7d05bf867c63ebba1b104/1:1/w_1800,h_1800,c_limit/mantisshrimp-467993194.jpg",
        "description": "The mantis shrimp can punch with the speed of a .22 caliber bullet—strong enough to break the shells of its prey, as well as aquarium glass.",
        "donations": 0
      }
     ]
 }
```

### Start JSON server

`json-server --watch db.json`

As a parameter we need to pass over the file containing our JSON structure (`db.json`). Furthermore we’re using the `— watch` parameter. By using this parameter we’re making sure that the server is started in watch mode which means that it watches for file changes and updates the exposed API accordingly.

Visit URL http://localhost:3000/animals in the browser and discuss the result.

### Endpoints by JSON server:

```
GET    /animals
GET    /animals/:id
POST   /animals
PATCH  /animals/:id
DELETE /animals/:id
```

Discuss different endpoints, Spend more time on `GET`. 

`POST`, `PATCH`, and `DELETE` endpoints can discuss later in detail. 


## `GET` request from POSTMAN

1. Make a `GET` request from postman to http://localhost:3000/animals
2. Make a `GET` request from postman to http://localhost:3000/animals/1

Discuss each results.

## CFU:

Ask students to open POSTMAN and make a `GET` request for animal information with id = 3.

Give them some time to create `db.json` file and install JSON-server package.

Send data for `db.json` file as a slack message.

## `POST`, `PATCH`, `DELETE`

1. Show how to make a `POST` request using POSTMAN to add an animal
    * Discuss: headers, body, URL => http://localhost:3000/animals
    * Data to add:
        ```json
        {
        "name": "Gibbon",
        "imageUrl": "https://external-preview.redd.it/hqv76hMTwDpeM4o4jp55PIUuBCwTq5T66zy_0MJiVv8.jpg?auto=webp&s=36c0ae0727537b4a01c42cc32d37770f5b25e3e9",
        "description": "Gibbons communicate by singing! Gibbon vocalizations are often referred to as song because of the way they modulate their pitch. Gibbons sing alone and in duets and they start each day by singing at sunrise.",
        "donations": 0
      }
        ```
    * Discuss response: New added data
    * Discuss about `id` key from `db.json` file
    
2. Show how to make a `PATCH` request using POSTMAN to change donation for animal with id = 3
    * Discuss: headers, body, URL => http://localhost:3000/animals/3
    * Data to modify:
    ```json
        "donations": 10
    ```
    * Discuss response: Modified data

3. Show how to make a `DELETE` request using POSTMAN to delete an animal with id = 2
    * URL => http://localhost:3000/animals/2
    * Discuss response

## Changes in JSON file

Show changes inside JSON file after making the `POST`, `PATCH`, and `DELETE` requests.

## CFU:

Ask students to

1. Make `POST` request to add an new animal
    * Students can use their own example OR
    * Data to add:
    ```json
        {
        "name": "Wombat",
        "imageUrl": "https://live.staticflickr.com/4158/33752020123_eab52e719d_b.jpg",
        "description": "They have cube-shaped poop. Wombat poop is square. They mark their territories by defecating, and it's thought that the shape of their poop keeps it from rolling away.",
        "donations": 0
        }
    ```
2. Make `PATCH` request to change name of an animal with id = 1
    * Change name to `red cat-bear`

3. Make `DELETE` request to delete an animal with id = 3