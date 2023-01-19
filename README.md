<a name="readme-top"></a>

<!-- PROJECT LOGO -->
<br />
<div align="center">
    <img src="images/logo.png" alt="Logo" width="380" height="100">

  <h3 align="center">OAS 3 Template</h3>
</div>


# OAS 3 Template for Mulesoft

This is a template for a sample api in OAS 3 with re-usable assets that could be stored in a central repository to improve composability. The template contains a list of rules for OAS validation that could be customized.

You will need to find and retrieve the template for your desired API in order to redefine structures, documentation, or implementation logic. We cover template customization in the following sections.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#installation">Contributing</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Template Content</a>
      <ul>
        <li><a href="#prerequisites">Security</a></li>
        <li><a href="#installation">Data types</a></li>
        <li><a href="#installation">Endpoints</a></li>
        <li><a href="#installation">Governance</a></li>
        <li><a href="#installation">Continuous deployment</a></li>
      </ul>
    </li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](https://example.com)

OpenAPI (OAS) is more widely used than RAML (RESTful API Modeling Language) for several reasons. One reason is that OAS has been around for longer and has had more time to establish itself as a standard. Additionally, OAS is backed by a large, active community of developers and organizations, which has helped to increase its popularity.
Mulesoft supports API design with both of the standards and this template provides an end-to-end way for `API Design`, `Governance` and publishing in `Exchange` with `OAS 3`.

```
src
   |-- ruleset
   |---|-- myruleset.yaml
   |
   |
   |-- securitySchemes
   |---|-- api-key.yaml
   |---|-- basic-auth.yaml
   |---|-- client-id-secret.yaml
   |---|-- jwt.yaml
   |---|-- oauth.yaml
   |
   |
   |-- types
   |---|-- Account.yaml
   |---|-- Lead.yaml
   |---|-- ApiResponse.yaml
   |
   |
   |-- .gitlab-ci.yml
   |-- README.md
   |-- sample-api.yaml
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Built With


* ![yaml-image]

<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

As we are going to use some javascript libraries, it's important to make sure that `npm` is installed in your machine. If not please run the following command

* npm
  ```sh
  npm install npm@latest -g
  ```

Anypoint CLI (Command Line Interface) is a command-line tool that allows developers to interact with the Anypoint Platform
* Anypoint CLI
  ```sh
  npm install -g anypoint-cli-v4
  ```

Swagger CLI (Command Line Interface) is a command-line tool that allows developers to interact with the Swagger ecosystem, which is a set of tools and technologies for designing, building, and documenting RESTful APIs.
* Swagger CLI
  ```sh
  npm install -g @apidevtools/swagger-cli
  ```

Spectral CLI (Command Line Interface) is a command-line tool that allows developers to interact with Spectral, which is a tool for linting and validating OpenAPI/Swagger files.
* Spectral CLI
  ```sh
  npm install -g @stoplight/spectral-cli
  ```

Visual Studio Code (often referred to as VS Code) is a free and open-source code editor developed by Microsoft. It is available for Windows, macOS, and Linux operating systems.
* VS Code
  Refer to this [link](https://code.visualstudio.com/docs/setup/setup-overview) 

Any other type of IDEs could be supported 

Swagger Viewer lets you preview Swagger 2.0 and OpenAPI files as you type in Visual Studio Code. Additionally provide intellisense/linting for the files as well.

* Swagger Viewer
  Refer to this [link](https://marketplace.visualstudio.com/items?itemName=Arjun.swagger-viewer)

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/SamyTb/mule-oas-3-template
   ```
2. Open repo content in vs code

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
### Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- TEMPLATE CONTENT -->
## Template content

This template is an OAS 3 Design for a sample API exposing CRUD operations for lead & account data over http resources.
Only YAML version exists in this template.

For more information about OAS 3, please refer to this [link](https://github.com/OAI/OpenAPI-Specification)

### Security

OpenAPI uses the term security scheme for authentication and authorization schemes. OpenAPI 3.0 lets you describe APIs protected using the following security schemes:
HTTP authentication schemes (they use the Authorization header):

* Basic :

  Basic authentication is a simple authentication scheme built into the HTTP protocol. The client sends HTTP requests with the `Authorization` header that contains the word `Basic` word followed by a space and a base64-encoded string `username:password`. For example, to authorize as `demo / p@55w0rd` the client would send
  ```
  Authorization: Basic ZGVtbzpwQDU1dzByZA==
  ```

  *Note:* Because base64 is easily decoded, Basic authentication should only be used together with other security mechanisms such as HTTPS/SSL.

  *Describing Basic Authentication*
  Using OpenAPI 3.0, you can describe Basic authentication as follows:
  ```
  openapi: 3.0.0
  ...
  components:
    securitySchemes:
      basicAuth:     # <-- arbitrary name for the security scheme
        type: http
        scheme: basic
  security:
    - basicAuth: []  # <-- use the same name here
  ```

  The first section, `securitySchemes`, defines a security scheme named basicAuth (an arbitrary name). This scheme must have `type: http` and `scheme: basic`. The `security` section then applies Basic authentication to the entire API. The square brackets `[]` denote the security scopes used; the list is empty because Basic authentication does not use scopes. `security` can be set globally (as in the example above) or on the operation level. The latter is useful if only a subset of operations require Basic authentication:

    ```
    paths:
      /something:
        get:
          security:
            - basicAuth: []
    ```

  Basic authentication can also be combined with other authentication methods as explained in [Using Multiple Authentication Types](https://swagger.io/docs/specification/authentication/#multiple).

  *401 Response*
  
  You can also define the 401 “Unauthorized” response returned for requests with missing or incorrect credentials. This response includes the `WWW-Authenticate` header, which you may want to mention. As with other common responses, the 401 response can be defined in the global `components/responses` section and referenced elsewhere via `$ref`.

    ```
    paths:
      /something:
        get:
          ...
          responses:
            ...
            '401':
              $ref: '#/components/responses/UnauthorizedError'
        post:
          ...
          responses:
            ...
            '401':
              $ref: '#/components/responses/UnauthorizedError'
    ...
    components:
      responses:
        UnauthorizedError:
          description: Authentication information is missing or invalid
          headers:
            WWW_Authenticate:
              schema:
                type: string
    ```

* Bearer

  Bearer authentication (also called token authentication) is an HTTP authentication scheme that involves security tokens called bearer tokens. The name “Bearer authentication” can be understood as “give access to the bearer of this token.” The bearer token is a cryptic string, usually generated by the server in response to a login request. The client must send this token in the `Authorization` header when making requests to protected resources:
  ```
  Authorization: Bearer <token>
  ```

The Bearer authentication scheme was originally created as part of OAuth 2.0 in RFC 6750, but is sometimes also used on its own. Similarly to Basic authentication, Bearer authentication should only be used over HTTPS (SSL).

*Describing Bearer Authentication*
In OpenAPI 3.0, Bearer authentication is a security scheme with `type: http` and `scheme: bearer`. You first need to define the security scheme under `components/securitySchemes`, then use the `security` keyword to apply this scheme to the desired scope – global (as in the example below) or specific operations:

```
openapi: 3.0.0
...
# 1) Define the security scheme type (HTTP bearer)
components:
  securitySchemes:
    bearerAuth:            # arbitrary name for the security scheme
      type: http
      scheme: bearer
      bearerFormat: JWT    # optional, arbitrary value for documentation purposes
# 2) Apply the security globally to all operations
security:
  - bearerAuth: []         # use the same name as above
```

Optional `bearerFormat` is an arbitrary string that specifies how the bearer token is formatted. Since bearer tokens are usually generated by the server, `bearerFormat` is used mainly for documentation purposes, as a hint to the clients. In the example above, it is "JWT", meaning JSON Web Token. The square brackets [] in bearerAuth: [] contain a list of `security` scopes required for API calls. The list is empty because scopes are only used with OAuth 2 and OpenID Connect. In the example above, Bearer authentication is applied globally to the whole API. If you need to apply it to just a few operations, add security on the operation level instead of doing this globally:

```
paths:
  /something:
    get:
      security:
        - bearerAuth: []
```

Bearer authentication can also be combined with other authentication methods as explained in Using Multiple Authentication Types.
401 Response
You can also define the 401 “Unauthorized” response returned for requests that do not contain a proper bearer token. Since the 401 response will be used by multiple operations, you can define it in the global `components/responses` section and reference elsewhere via `$ref`.

```
paths:
  /something:
    get:
      ...
      responses:
        '401':
          $ref: '#/components/responses/UnauthorizedError'
        ...
    post:
      ...
      responses:
        '401':
          $ref: '#/components/responses/UnauthorizedError'
        ...
components:
  responses:
    UnauthorizedError:
      description: Access token is missing or invalid
```

To learn more about responses, see [Describing Responses](https://swagger.io/docs/specification/describing-responses/).

* API keys

Some APIs use API keys for authorization. An API key is a token that a client provides when making API calls. The key can be sent in the query string:
```
GET /something?api_key=abcdef12345
```

or as a request header:
```
GET /something HTTP/1.1
X-API-Key: abcdef12345
```

or as a cookie:
```
GET /something HTTP/1.1
Cookie: X-API-KEY=abcdef12345
```

API keys are supposed to be a secret that only the client and server know. Like Basic authentication, API key-based authentication is only considered secure if used together with other security mechanisms such as HTTPS/SSL.
Describing API Keys
In OpenAPI 3.0, API keys are described as follows:

```
openapi: 3.0.0
...
# 1) Define the key name and location
components:
  securitySchemes:
    ApiKeyAuth:        # arbitrary name for the security scheme
      type: apiKey
      in: header       # can be "header", "query" or "cookie"
      name: X-API-KEY  # name of the header, query parameter or cookie
# 2) Apply the API key globally to all operations
security:
  - ApiKeyAuth: []     # use the same name as under securitySchemes
```

This example defines an API key named X-API-Key sent as a request header X-API-Key: <key>. The key name ApiKeyAuth is an arbitrary name for the security scheme (not to be confused with the API key name, which is specified by the name key). The name ApiKeyAuth is used again in the security section to apply this security scheme to the API. Note: The securitySchemes section alone is not enough; you must also use security for the API key to have effect. security can also be set on the operation level instead of globally. This is useful if just a subset of the operations need the API key:

```
paths:
  /something:
    get:
      # Operation-specific security:
      security:
        - ApiKeyAuth: []
      responses:
        '200':
          description: OK (successfully authenticated)
```

Note that it is possible to support multiple authorization types in an API. See Using Multiple Authentication Types.

* Client-id-secret
Some APIs use a pair of security keys, say, API Key and App ID. To specify that the keys are used together (as in logical AND), list them in the same array item in the security array:

```
components:
  securitySchemes:
    client-id:
      type: apiKey
      in: header
      name: x-client-id
    client-secret:
      type: apiKey
      in: header
      name: x-client-secret
security:
  - client-id: []
    client-secret:  []
```

Note the difference from:

```
security:
  - client-id: []
  - client-secret:  []
```

which means either key can be used (as in logical OR). For more examples, see Using Multiple Authentication Types.

*401 Response*

You can define the 401 “Unauthorized” response returned for requests with missing or invalid API key. This response includes the WWW-Authenticate header, which you may want to mention. As with other common responses, the 401 response can be defined in the global components/responses section and referenced elsewhere via $ref.

```
paths:
  /something:
    get:
      ...
      responses:
        ...
        '401':
           $ref: "#/components/responses/UnauthorizedError"
    post:
      ...
      responses:
        ...
        '401':
          $ref: "#/components/responses/UnauthorizedError"
components:
  responses:
    UnauthorizedError:
      description: API key is missing or invalid
      headers:
        WWW_Authenticate:
          schema:
            type: string
```






########################################################################################################################
* OAuth 2
  
* JWT

All these types of security schemes are under the folder `/securitySchemes` available for re-use

## Endpoints
The following endpoints are available in this API:

| Method  | Endpoint | Description |
| ------------- |:-------------:|:-------------:|
| GET | /leads | Retrieve a list of leads |
| GET | /leads/{id} | Retrieve a specific item by ID |
| POST | /leads | Create a new lead |
| PUT | /leads/{id} | Update an existing lead |
| DELETE | /leads/{id} | Delete an existing lead |


## Data Types
The following data types are used in this API:

```
Lead:
  required:
    - name
    - email
  type: object
  properties:
    id:
      type: string
      example: 00Q68000005RITMEA4
    name:
      type: string
      example: Frederick Mann
    email:
      type: string
      example: fmann@example.com
    industry:
      type: string
      description: industry of the lead
      enum:
        - agriculture
        - banking
        - web3
```

## Security
This API uses Basic Authentication for security. You will need to include the Authorization header with a valid username and password in each request.

## Examples
Here is an example of how to retrieve a list of leads:

```
GET https://my-api.com/v1/items
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

## Contribute
To contribute to this API, please fork the repository and submit a pull request.

## License

This README describes the basic structure of the API, including the available endpoints, data types, and security schemes. It also provides an example of how to use the API.
You can add more information like the types of parameters, request and response headers, and the different status codes of the API responses.
It's important to note that the example is just that, an example, the actual format of the API may vary and should be described in the OAS file.
Also the template should be written in YAML or JSON format, and the security scheme should be described in the OAS file.

[product-screenshot]: images/product-screenshot.png
[oas-icon]: images/oas.png
[yaml-icon]: images/yaml.png
[yaml-image]: https://img.shields.io/static/v1?label=oas3&message=yaml&color=red

