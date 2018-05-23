# A Loopback GraphQL Example 

This repo serves as an Loopback GraphQL starter for everyone looking to setup and running with Loopback and GraphQL server.

## Installation
```
$ git clone https://github.com/khanhoatink4/loopback-graphql-example.git
$ cd loopback-graphql-example
$ npm i
$ node .
```

You will see the following message on screen:
```
Web server listening at: http://localhost:3000
Browse your REST API at http://localhost:3000/explorer
Copy this access token for test:  xxxxxxxxx
 ```
 
 Copy the access token and go to (http://localhost:3000/graphiql?access_token=[access_token]) to play the new game. Also you can go to (localhost:3000/explorer) to test the Rest API.
 
 ## Create a new model
 Let's finish the task easily and quickly. I recommend to install [Loopback Cli tool](https://github.com/strongloop/loopback-cli)
 ```
$ npm install -g loopback-cli
$ lb model 
```

## Play with GraphQL
Go to (http://localhost:3000/graphiql?access_token=[access_token]) and paste following query to run
```
// page 1, limit 1 item
{
  product{
    productFind(options: {
      offset:0, limit: 1
    }) {
      edges {
        node {
          name
          price
          brand{
            name
          }
        }
      }
    }
  }
}
```

```
// Get all products which name like 'iPhone'
{
  product{
    productFind(filter:{
      where: {
        name: {
          like: "iPhone"
        }
      }
    }) {
      edges {
        node {
          name
          price
          brand{
            name
          }
        }
      }
    }
  }
}
```

```
// filter in sub query
{ 
  brand {
    brandFind{
      edges {
        node {
          products (filter: {
            where: {
              name: {
                ilike: "%plus%"
              }
            }
          }) {
            edges {
              node {
                id
                name
              }
            }
          }
        } 
      }
    }
  }
}
```
