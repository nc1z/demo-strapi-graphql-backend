# Strapi GraphQL backend

The GraphQL plugin enables querying the existing endpoints using GraphQL language and syntax, while keeping the content types and APIs set up and customized in a similar manner as the <a href="https://github.com/nc1z/demo-strapi-rest-backend">Strapi REST backend</a>. The development process for APIs and endpoints remains relatively unchanged.

## Quickstart

### Register

For quick testing, user can register via the below method.

POST: `localhost:3001/api/auth/local/register`

Request body example

```json
{
    "username": "your-username",
    "email": "your-email@gmail.com",
    "password": "your-password",
    "gender": "your-gender"
}
```

### Login

POST: `localhost:3001/api/auth/local`

```json
{
    "identifier": "your-email@gmail.com",
    "password": "your-password"
}
```

### Next Steps

Once logged in or registered, please retrieve and store the `jwt` in the response object.
It will be required in the next steps.

## How to query

### Method 1: POSTMAN

1. Once authenticated and logged in, retrieve JWT in return object
2. Set jwt as bearer token in authorization headers
3. Use the `POST` request method
4. Enter `localhost:3001/graphql` as the URL endpoint
5. Select GraphQL as the request body format and use these queries to test it out

    ```gql
    query getMemberships {
        memberships {
            data {
                attributes {
                    fullName
                    emailAddress
                    gender
                }
            }
        }
    }
    ```

    OR simply

    ```gql
    { 
        memberships {
            data{
                attributes {
                    fullName
                    emailAddress
                    gender
                }
            }
        }
    }

    ```

    Other examples:

    ```gql
    query GetReviews {
        reviews {
            data {
                attributes {
                    title
                    rating
                    description
                }
            }
        }
    }
    ```

### Method 2: GRAPHQL PLAYGROUND

1. Once authenticated and logged in, retrieve JWT in return object
2. Visit `localhost:3001/graphql` to view the GraphQL playground
3. In the bottom panel, you should see a button `HTTP HEADERS`
4. Click on the button, and in the input field, enter your jwt as the bearer token for the authorization headers

    ```json
    {
        "Authorization": "Bearer your-jwt-value"
    }
    ```

5. Input gql queries similar to the above examples in method 1.
