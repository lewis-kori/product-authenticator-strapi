# Product authenticator backend

## setup

have node.js > v12.x installed

run `yarn install`

after dependencies have been installed
create a .env file and populate it with relevant info from the `.env.example`

finally, run

`yarn develop`

## auth endpoints

### register user

    auth/local/register

keys are

* username
* email
* password

this will [log you in automatically](#login)

### login

    auth/local

keys are

* identifier (username or email)
* password

expected results are:

    ```
    {
        "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNjA4NDk0ODA4LCJleHAiOjE2MTEwODY4MDh9.C-KgKYQcwZvAY4gigyB0-kU7B26Zy6fRe3eh4YU2z7U",
        "user": {
            "id": 1,
            "username": "example@me.com",
            "email": "example@me.com",
            "provider": "local",
            "confirmed": true,
            "blocked": false,
            "role": {
                "id": 1,
                "name": "Authenticated",
                "description": "Default role given to authenticated user.",
                "type": "authenticated"
            },
            "created_at": "2020-12-18T06:54:06.586Z",
            "updated_at": "2020-12-20T19:59:49.908Z"
        }
    }
    ```

use the jwt in request headers in subsequent api calls.

### forgot password

    auth/forgot-password

pass `email` as key and make a POST request to the endpoint

## products endpoints

### list all products

    /products

a GET request lists all the products in the db

### view product details

    products/{product_id}

retrieves a single instance of a product

### list all products categories

    /categories

a GET request lists all the product categories in the db.

### view product category details

    categories/{category_id}

retrieves a single instance of a product category.
