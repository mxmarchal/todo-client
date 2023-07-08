# Todo-client

This is a personal project to try SveteKit and Svelte. It is a simple todo app client that uses a REST API to store the data.

## Backends

I'm writing several backends to test the client with different languages and frameworks to learn them.

Current backends available are:

- [todo-server-ts](https://github.com/mxmarchal/todo-server-ts) - A REST API written in Typescript

Backends in progress:

- todo-server-go - A REST API written in Go
- todo-server-rust - A REST API written in Rust
- todo-server-java - A REST API written in Java

## How to run

1. Clone the repo
2. Run `npm install` (or `pnpm`) to install dependencies
3. Run `npm run dev -- --open` to start the dev server

The app will be available at [localhost:5173](http://localhost:5173).
The API URL is `http://localhost:3000/` by default. You cannont change it yet.

## API endpoints

- `GET /` - Get all todos
- `GET /:id` - Get a todo by id
- `POST /` - Create a new todo
- `PUT /:id` - Update a todo
- `DELETE /:id` - Delete a todo

## Good to know

- This project is not meant to be used in production. It is a personal project to learn Svelte and SvelteKit.
- Svelte seems pretty straightforward and easy to learn. I like it.
