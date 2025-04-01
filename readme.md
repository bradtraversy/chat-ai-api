# Chat AI API

This is the backend for the Chat AI application. It is a Node/Express/TypeScript API that uses [Stream](https://www.getStream.io) for chat, chat history, and user management. It also uses a PostgreSQL database from [Neon](https://www.neon.tech) to store user information and chat history. We use the Drizzle ORM to interact with the database. [Open AI](https://platform.openai.com/) is used for the AI chatbot.

The Vue.js frontend for this application can be found [here](https://github.com/bradtraversy/chat-ai-ui).

## Installation

1. Clone the repository
2. Run `npm install`
3. Create a `.env` file in the root directory and add the following environment variables:

```
PORT=5000
STREAM_API_KEY=""
STREAM_API_SECRET=""
OPENAI_API_KEY=""
DATABASE_URL="postgresql://username:password@localhost:5432/dbname"
```

You can get these keys by signing up for Stream, Open AI, and Neon.

4. Run database migrations with Drizzle Kit:

```
npx drizzle-kit generate
npx drizzle-kit migrate
```

This will create the necessary tables in your database.

5. Run the server with `npm run dev` and open on `http://localhost:5000`

## Endpoints

- POST `/register-user` - Create a user in Stream chat and in our own database
- POST `/chat` - Creates a new Stream chat channel, sends a request to Open AI to generate a response, and saves the chat history in our database
- POST `/get-messages` - Get's the chat history for a specific user

## Building For Production

This is a TypeScript project, so you will need to build the project before running in production. Run `npm run build` to build the project. You can then run the server with `npm start`. The files will be in the `dist` directory.
