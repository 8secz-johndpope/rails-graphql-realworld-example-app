# ![Ruby on Rails GraphQL Example App](logo.png)

[![Build Status](https://travis-ci.com/dostu/rails-graphql-realworld-example-app.svg?branch=master)](https://travis-ci.com/dostu/rails-graphql-realworld-example-app)

> ### Example Ruby on Rails GraphQL codebase containing real world examples (CRUD, auth, advanced patterns, etc) that adheres to the [RealWorld GraphQL API spec](https://github.com/dostu/rails-graphql-realworld-example-app/blob/master/GRAPHQL_API_SPEC.md).

This repo is functionality complete — PRs and issues welcome!

You can also query the schema using [GraphiQL](https://realworld-graphql.herokuapp.com/graphiql).

There is [React + Apollo frontend](https://github.com/dostu/react-apollo-realworld-example-app) implementation which can be used with this backend.

## Installation

Make sure you have PostgreSQL installed.

1. Clone this repo
2. `bundle install` to install required dependencies
3. `rails db:reset` to create database, load schema and seed data
4. `rails s` to start the local server
5. Navigate to http://0.0.0.0:3000/graphiql

## Graphql introspection
Use this query to detail graphql schema

```graphql
    query IntrospectionQuery {
      __schema {
        queryType {
          name
        }
        mutationType {
          name
        }
        types {
          ...FullType
        }
        directives {
          name
          description
          locations
          args {
            ...InputValue
          }
        }
      }
    }
    fragment FullType on __Type {
      kind
      name
      description
      fields(includeDeprecated: true) {
        name
        description
        args {
          ...InputValue
        }
        type {
          ...TypeRef
        }
        isDeprecated
        deprecationReason
      }
      inputFields {
        ...InputValue
      }
      interfaces {
        ...TypeRef
      }
      enumValues(includeDeprecated: true) {
        name
        description
        isDeprecated
        deprecationReason
      }
      possibleTypes {
        ...TypeRef
      }
    }
    fragment InputValue on __InputValue {
      name
      description
      type {
        ...TypeRef
      }
      defaultValue
    }
    fragment TypeRef on __Type {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
          ofType {
            kind
            name
            ofType {
              kind
              name
              ofType {
                kind
                name
                ofType {
                  kind
                  name
                  ofType {
                    kind
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
