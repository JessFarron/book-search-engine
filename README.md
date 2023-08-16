# book-search-engine
# MERN Challenge: Book Search Engine

Welcome to the **MERN Challenge: Book Search Engine**! In this challenge, you will transform a Google Books API search engine built with a RESTful API into a GraphQL API using Apollo Server. This will involve refactoring both the back-end and front-end components of the application. Here's how to get started:

## Installation and Usage

### Back-End Installation and Setup

1. Clone the repository to your local machine:

   ```
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install the necessary dependencies:

   ```
   npm install
   ```

3. Update the authentication middleware in `auth.js` to work with the GraphQL API.

4. Implement Apollo Server and apply it to the Express server in `server.js`. You can use the following command to install Apollo Server 2:

   ```
   npm install apollo-server-express@2.15.0
   ```

5. Define your GraphQL schema types and resolvers in the `schemas` directory:

   - Define necessary Query and Mutation types in `typeDefs.js`.
   - Define query and mutation functionality using Mongoose models in `resolvers.js`.

6. Export your typeDefs and resolvers from `index.js`.

### Front-End Installation and Setup

1. Create the following front-end files:

   - `queries.js`: Define the `GET_ME` query for executing the `me` query using Apollo Server.
   - `mutations.js`:

     - Define `LOGIN_USER` mutation for executing the `loginUser` mutation.
     - Define `ADD_USER` mutation for executing the `addUser` mutation.
     - Define `SAVE_BOOK` mutation for executing the `saveBook` mutation.
     - Define `REMOVE_BOOK` mutation for executing the `removeBook` mutation.

2. In `App.js`, create an Apollo Provider to make every request work with the Apollo server.

3. In `SearchBooks.js`:

   - Use the Apollo `useMutation()` Hook to execute the `SAVE_BOOK` mutation in the `handleSaveBook()` function instead of the `saveBook()` function imported from the API file.
   - Keep the logic for saving the book's ID to state in the try...catch block.

4. In `SavedBooks.js`:

   - Remove the `useEffect()` Hook that sets the state for `UserData`.
   - Instead, use the Apollo `useQuery()` Hook to execute the `GET_ME` query on load and save it to a variable named `userData`.
   - Use the Apollo `useMutation()` Hook to execute the `REMOVE_BOOK` mutation in the `handleDeleteBook()` function instead of the `deleteBook()` function imported from the API file.

5. In `SignupForm.js`, replace the `addUser()` functionality imported from the API file with the `ADD_USER` mutation functionality.

6. In `LoginForm.js`, replace the `loginUser()` functionality imported from the API file with the `LOGIN_USER` mutation functionality.

## Back-End Specifications

### auth.js

Update the authentication middleware function to work with the GraphQL API.

### server.js

Implement the Apollo Server and apply it to the Express server as middleware. Use the provided script to install Apollo Server 2.

### Schemas Directory

#### index.js

Export your `typeDefs` and `resolvers` from this file.

#### typeDefs.js

Define the necessary `Query` and `Mutation` types:

- `Query` type:
  - `me`: Returns a `User` type.

- `Mutation` type:
  - `login`: Accepts an email and password as parameters; returns an `Auth` type.
  - `addUser`: Accepts a username, email, and password as parameters; returns an `Auth` type.
  - `saveBook`: Accepts book information as parameters; returns a `User` type.
  - `removeBook`: Accepts a book's `bookId` as a parameter; returns a `User` type.

Define `User`, `Book`, and `Auth` types based on the provided specifications.

#### resolvers.js

Define the query and mutation functionality to work with the Mongoose models based on the provided specifications.

### Front-End Specifications

#### queries.js

Define the `GET_ME` query to execute the `me` query using Apollo Server.

#### mutations.js

Define the following mutation functions:

- `LOGIN_USER`: Executes the `loginUser` mutation.
- `ADD_USER`: Executes the `addUser` mutation.
- `SAVE_BOOK`: Executes the `saveBook` mutation.
- `REMOVE_BOOK`: Executes the `removeBook` mutation.

#### App.js

Create an Apollo Provider to make every request work with the Apollo server.

#### SearchBooks.js

- Use the Apollo `useMutation()` Hook to execute the `SAVE_BOOK` mutation in the `handleSaveBook()` function.
- Keep the logic for saving the book's ID to state in the try...catch block.

#### SavedBooks.js

- Remove the `useEffect()` Hook that sets the state for `UserData`.
- Use the Apollo `useQuery()` Hook to execute the `GET_ME` query on load and save it to a variable named `userData`.
- Use the Apollo `useMutation()` Hook to execute the `REMOVE_BOOK` mutation in the `handleDeleteBook()` function.

#### SignupForm.js

Replace the `addUser()` functionality imported from the API file with the `ADD_USER` mutation functionality.

#### LoginForm.js

Replace the `loginUser()` functionality imported from the API file with the `LOGIN_USER` mutation functionality.

