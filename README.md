# computers-databases-everywhere


Play's Computer Database, implemented with various frameworks and technologies.

## Specification

The Computer Database is a pretty straightforward web app : it manages a list of computers.
Computers can be : 

* Listed : can by filtered by name or sorted by field
* Created
* Edited
* Deleted

### Model

A computer has the following properties:

* a technical id
* a name
* the day it was introduced
* eventually, the days it was discontinued
* eventually, the manufacturer

the manufacturer has the following properties:

* a techical id
* a name

## REST API

The Computer Database communicates with clients (web or mobule) through a REST API.
Clients communicates with the server using JSON.

### `GET /companies`

Fetches the list of all companies.
Useful when editing a computer : if the manufacturer can be edited when editing a computer, this operation can provides the full list of companies to select from.

#### Response status codes

* **200 (OK)** : Companies are sent to the client in the response body.

### `GET /computers`

Fetches a paginated list of computers.
Data is paginated.

#### Query parameters

* `page` : the page to fetch (default : 1)
* `pageSize` : the number of items per page (default : 10)
* `filter` : a filter applied to the computer's name (default: none)
* `orderBy` : the field used for sorting computers (default: sorted by name)

#### Response status codes

* **200 (OK)** : Computers are sent to the client in the response body.
* **400 (Bad Request)** : if one of the query parameters is invalid


### `POST /computers` 

Creates a new computer.
Data for the new computer is sent in the request body.


#### Response status codes

* **201 (Created)** : Confirms that the computer was successfully created
* **400 (Bad Request)** : if the specified id is not a valid computer id

### `DELETE /computers`

Delete all computers.

#### Response status codes

* **200 (OK)** : Confirms that all computers have been deleted.

### `GET /computer/:id`

Fetches the computer with id `:id`.

#### Response status codes

* **200 (OK)** : Computer is sent to the client in the response body.
* **400 (Bad Request)** : if the specified id is not a valid computer id.
* **404 (Not Found)** : if a computer with the specified id could not be found.

### `PUT /computer/:id`

Updates the computer with id `:id`.

The updated data for the computer is sent in the request body.

#### Response status codes

* **200 (OK)** : Confirms that the computer was successfully updated.
* **400 (Bad Request)** : if the specified id is not a valid computer id or if the JSON payload was invalid.
* **404 (Not Found)** : if a computer with the specified id could not be found.

### `DELETE /computer/:id`

Deletes the computer with id `:id`.

#### Response status codes

* **200 (OK)** : Confirms that the computer was successfully deleted.
* **400 (Bad Request)** : if the specified id is not a valid computer id.
* **404 (Not Found)** : if a computer with the specified id could not be found.


