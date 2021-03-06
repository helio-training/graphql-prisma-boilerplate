<h1 align="center">Refactored Fullstack Boilerplate using GraphQL, React, & Prisma</h1>
<br />

![](https://imgur.com/ousyQaC.png)

<div align="center"><strong>🚀 Bootstrap your fullstack GraphQL app within seconds</strong></div>
<div align="center">Advanced starter kit for a fullstack GraphQL app with React and Node.js - based on best practices from the GraphQL community.</div>

## Features

- **Scalable GraphQL server:** The server uses [`graphql-yoga`](https://github.com/prisma/graphql-yoga) which is based on Apollo Server & Express
- **Pre-configured Apollo Client:** The project comes with a preconfigured setup for Apollo Client
- **GraphQL database:** Includes GraphQL database binding to [Prisma](https://www.prismagraphql.com) (running on MySQL)
- **Tooling**: Out-of-the-box support for [GraphQL Playground](https://github.com/prisma/graphql-playground) & [query performance tracing](https://github.com/apollographql/apollo-tracing)
- **Extensible**: Simple and flexible [data model](./database/datamodel.graphql) – easy to adjust and extend
- **No configuration overhead**: Preconfigured [`graphql-config`](https://github.com/prisma/graphql-config) setup

For a fully-fledged **React & Apollo tutorial**, visit [How to GraphQL](https://www.howtographql.com/react-apollo/0-introduction/). You can more learn about the idea behind GraphQL boilerplates [here](https://blog.graph.cool/graphql-boilerplates-graphql-create-how-to-setup-a-graphql-project-6428be2f3a5).

## Requirements

You need to have the [GIT](https://gist.github.com/derhuerst/1b15ff4652a867391f03) installed to clone down the Repository

## Getting started

Before you can get started with this boilerplate there are some initial configurations that need to occur. These configurations involve deploying to a [Prisma](https://www.prisma.io/docs/tutorials/setup-prisma/demo-server-ouzia3ahqu) endpoint and setting up environment variables. In this example, we will be using a Prisma demo server and thus will require a Prisma [account](https://app.prisma.io/). 

```sh
# 1. Clone the Repo from GitHub
        - optionally rename the cloned Repo by providing a project name
git clone https://github.com/helio-training/graphql-prisma-boilerplate <project-name>

# 2. Detach your GIT repo from this boilerplate and connect it to your own repository. 
        - Create an empty Repo on GitHub
        - Remove the remote connection from the local repo you just cloned
git remote remove origin
        - Follow the instruction on your empty GitHub repo to add it as a remote connection
        
# 3. In your favorite terminal navigate into the `database` directory of the new project
cd <project-name>/server/database

# 4. Deploy your database using prisma
prisma deploy

# 5. Open your project in your desired IDE and open the 'prisma.yml' file
        - <project-name>/server/database/prisma.yml
        - this file is used to deploy your datamodel to a prisma endpoint
        - note the field 'endpoint: <prisma-url>'

# 6. Comment In/Out 'endpoint: ' lines in your prisma.yml
        - Line 2 has this line 'endpoint: ${env:PRISMA_ENDPOINT}' commented out
        - The last line, as of the deploymnet to Prisma, should show 'endpoint: <prisma-url>'
        - Invert those comments, bring Line 2 back into focus and comment out the new line

# 7. In the 'server' directory create an environment variable file named '.env' 
touch .env 

# 8. In your desired IDE add in the falling values to .env file
        - Paste in the Prisma URL from above in the prisma.yml
        - You make up two passwords
PRISMA_ENDPOINT="<replace-with-prisma-url>"
PRISMA_SECRET="<insert-password-1>"
APP_SECRET="<insert-password-2>"

# 9. Configuration Complete

# 10. In order to run your application you need to launch your client and server separately
    # in one terminal window
        cd <project-name>/server
        npm install 
        npm start
    # in another terminal window
        cd <project-name>/client
        npm install
        npm start

```

## Documentation

### Commands

* `yarn start` starts GraphQL server on `http://localhost:4000`
* `yarn dev` starts GraphQL server on `http://localhost:4000` _and_ opens GraphQL Playground
* `yarn playground` opens the GraphQL Playground for the `projects` from [`.graphqlconfig.yml`](./.graphqlconfig.yml)
* `yarn prisma <subcommand>` gives access to local version of Prisma CLI (e.g. `yarn prisma deploy`)

> **Note**: We recommend that you're using `yarn dev` during development as it will give you access to the GraphQL API or your server (defined by the [application schema](./src/schema.graphql)) as well as to the Prisma API directly (defined by the [Prisma database schema](./generated/prisma.graphql)). If you're starting the server with `yarn start`, you'll only be able to access the API of the application schema.

### Server structure

![](https://imgur.com/95faUsa.png)

| File name 　　　　　　　　　　　　　　| Description 　　　　　　　　<br><br>| 
| :--  | :--         |
| `├── .graphqlconfig.yml` | Configuration file based on [`graphql-config`](https://github.com/prisma/graphql-config) (e.g. used by GraphQL Playground).|
| `└── database ` (_directory_) | _Contains all files that are related to the Prisma database service_ |\
| `　　├── prisma.yml` | The root configuration file for your Prisma database service ([docs](https://www.prismagraphql.com/docs/reference/prisma.yml/overview-and-example-foatho8aip)) |
| `　　└── datamodel.graphql` | Defines your data model (written in [GraphQL SDL](https://blog.graph.cool/graphql-sdl-schema-definition-language-6755bcb9ce51)) |
| `└── src ` (_directory_) | _Contains the source files for your GraphQL server_ |
| `　　├── index.js` | The entry point for your GraphQL server |
| `　　├── schema.graphql` | The **application schema** defining the API exposed to client applications  |
| `　　└── generated` (_directory_) | _Contains generated files_ |
| `　　　　└── prisma.grapghql` | The **Prisma database schema** defining the Prisma GraphQL API  |

## Contributing

The GraphQL boilerplates are maintained by the GraphQL community, with official support from the [Apollo](https://dev-blog.apollodata.com) & [Graphcool](https://blog.graph.cool/) teams.

Your feedback is **very helpful**, please share your opinion and thoughts! If you have any questions or want to contribute yourself, join the [`#graphql-boilerplate`](https://graphcool.slack.com/messages/graphql-boilerplate) channel on our [Slack](https://graphcool.slack.com/).
