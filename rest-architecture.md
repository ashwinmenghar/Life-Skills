# What is REST?

Learn about the REST (Representational State Transfer) paradigm and how REST architecture streamlines communication between web components.

<br>
<img src="https://raw.githubusercontent.com/Codecademy/articles/0b631b51723fbb3cc652ef5f009082aa71916e63/images/rest_api.svg" />
<br>

## REST API Model

### Representational State Transfer
REST, or Representational State Transfer, is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other. REST-compliant systems, often called RESTful systems, are characterized by their statelessness and separation of client and server concerns.

### Separation of Client and Server
In REST, the client and server implementations are independent. The client can be updated without affecting the server, and vice versa, as long as they adhere to the agreed message format. This modularity improves the flexibility, scalability, and evolution of each component independently.

RESTful interfaces allow different clients to hit the same REST endpoints, perform actions, and receive consistent responses.

### Statelessness
REST systems are stateless, meaning neither the client nor the server needs to maintain information about each other’s state. Each message is self-contained and includes all information the server needs to process. This approach enhances reliability, performance, and scalability by simplifying system components.

### Communication between Client and Server
REST communication involves clients sending requests to retrieve or modify resources, and servers responding to these requests.

#### Making Requests
A REST request generally consists of:
- **An HTTP verb**: Defines the operation to perform.
- **A header**: Provides metadata about the request.
- **A path to a resource**: Identifies the target resource.
- **An optional message body**: Contains data for the request.

#### HTTP Verbs
The four basic HTTP verbs are:
- **GET**: Retrieve a resource or collection.
- **POST**: Create a new resource.
- **PUT**: Update an existing resource.
- **DELETE**: Remove a resource.

#### Headers and Accept Parameters
The client specifies acceptable content types in the `Accept` header using MIME Types. Examples:
- `text/html`: HTML content.
- `application/json`: JSON data.

Example request:
```http
GET /articles/23
Accept: text/html, application/xhtml
```

#### Paths
Paths in REST APIs should be hierarchical and descriptive. For instance:
- `fashionboutique.com/customers/223/orders/12`

Operations on resources:
- **List all resources**: `POST /customers`
- **Access a specific resource**: `GET /customers/:id`
- **Delete a resource**: `DELETE /customers/:id`

#### Sending Responses
Responses from servers include status codes and, when applicable, content types.

#### Status Codes
- **200 (OK)**: Request successful.
- **201 (CREATED)**: Resource successfully created.
- **204 (NO CONTENT)**: Request successful, no content in response.
- **400 (BAD REQUEST)**: Malformed or invalid request.
- **403 (FORBIDDEN)**: Unauthorized access.
- **404 (NOT FOUND)**: Resource not found.
- **500 (INTERNAL SERVER ERROR)**: General error.

#### Content Types
Servers include the content type in response headers. Example:
```http
HTTP/1.1 200 (OK)
Content-Type: text/html
```

#### Examples
- **GET**: Retrieve customers
  ```http
  GET http://fashionboutique.com/customers
  Accept: application/json
  ```
  Response:
  ```http
  Status Code: 200 (OK)
  Content-Type: application/json
  ```
- **POST**: Create a customer
  ```http
  POST http://fashionboutique.com/customers
  Body:
  {
    "customer": {
      "name": "Scylla Buss",
      "email": "scylla.buss@codecademy.org"
    }
  }
  ```
  Response:
  ```http
  Status Code: 201 (CREATED)
  Content-Type: application/json
  ```

## Practice with REST
Design a REST API for a photo-collection site. Components include users, photos, and venues.

### Models
```json
{
  "user": {
    "id": <Integer>,
    "username": <String>,
    "password": <String>
  }
}
{
  "photo": {
    "id": <Integer>,
    "venue_id": <Integer>,
    "author_id": <Integer>
  }
}
{
  "venue": {
    "id": <Integer>,
    "name": <String>,
    "address": <String>
  }
}
```

### Requests/Responses

#### GET Requests

| Request                                   | Response Code | Content-Type       |
|------------------------------------------|---------------|--------------------|
| `GET /index.html`                        | 200 (OK)      | text/html          |
| `GET /style.css`                         | 200 (OK)      | text/css           |
| `GET /venues`                            | 200 (OK)      | application/json   |
| `GET /venues/:id`                        | 200 (OK)      | application/json   |
| `GET /venues/:id/photos/:id`             | 200 (OK)      | image/png          |

#### POST Requests

| Request                                   | Response Code | Content-Type       |
|------------------------------------------|---------------|--------------------|
| `POST /users`                            | 201 (CREATED) | application/json   |
| `POST /venues`                           | 201 (CREATED) | application/json   |
| `POST /venues/:id/photos`                | 201 (CREATED) | application/json   |

#### PUT Requests

| Request                                   | Response Code |
|------------------------------------------|---------------|
| `PUT /users/:id`                         | 200 (OK)      |
| `PUT /venues/:id`                        | 200 (OK)      |
| `PUT /venues/:id/photos/:id`             | 200 (OK)      |

#### DELETE Requests

| Request                                   | Response Code |
|------------------------------------------|---------------|
| `DELETE /venues/:id`                     | 204 (NO CONTENT) |
| `DELETE /venues/:id/photos/:id`          | 204 (NO CONTENT) |

---


**Reference** : <a href="https://www.codecademy.com/article/what-is-rest">https://www.codecademy.com/article/what-is-rest</a>
