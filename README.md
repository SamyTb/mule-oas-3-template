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
      </ul>
    </li>
    <li><a href="#security">Security</a></li>
    <li><a href="#data-types">Data types</a></li>
    <li><a href="#contact">Endpoints</a></li>
    <li><a href="#governance">Governance</a></li>
    <li><a href="#ci">Continuous deployment</a></li>
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



<p align="right">(<a href="#readme-top">back to top</a>)</p>

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

