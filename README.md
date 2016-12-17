# coffee-and-code-frontend

## Getting Started

_First Time Setup_

`npm install -g json-server`


_Developing_

1. From root: `json-server --watch db.json` to turn on "fake api"
2. From `/src`: `npm run dev` 


### Libraries, Frameworks, and Packages; oh my!

- [Framework7](http://framework7.io/docs/)
- [vue-cli](https://github.com/vuejs-templates/webpack)
	- Explained: [GitBook](http://vuejs-templates.github.io/webpack/)
	- Generates starter project with: vuejs, vuex, webpack, etc.
- [VueJS](https://vuejs.org/v2/guide/)
- [VueX](https://vuex.vuejs.org/en/getting-started.html)
- [Webpack](https://webpack.github.io/)
	- Explained: [Webpack Fundamentals](https://app.pluralsight.com/library/courses/webpack-fundamentals/table-of-contents)
- [json-server](https://github.com/typicode/json-server)

### To Do:

#### Version 1

_Front End_

- Gulp to pull files from node_modules into `/src/static`
- Remove packages.json at top app level
- Get basic routing and magic working with the Framework7 + vue setup
- Configure environment for testing on app
- Setup build credentials for android app stuff through XDK
- Add VueX for state management
- Create interfaces for expected schema
- Mock out all API communications
	- https://github.com/typicode/json-server

_Back End_

- .NET Core for funsies and linux-y hosting?
- Static store of users
- Stats model with inheritence
- Implemented mocked endpoints