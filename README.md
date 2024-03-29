# be_medium

NestJS, TS, PrismaJS, PostgreSQL, Docker

## Installation

```bash
$ npm install

npx prisma migrate dev         
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

Medium Lite
Write a simple backend equivalent to the popular service Medium

Entities in the project:

```typescript
enum UserRole {
  admin = 'admin',
  user = 'user',
}

interface User {
  id: number;
  name: string;
  email: string; // unique
  password: string;
  role: UserRole;
  posts: Post[];
  viewedPosts: Post[];
}

interface Post {
  id: number;
  title: string;
  content: string;
  author: User;
  viewers: User[];
}
```

Backend Features:

1. Authorization (access token + refresh token)
2. User creation (Admin only)
3. Get a list of users (Admin only) + pagination via offsets
4. Get a single user (Admin only)
5. Post creation (Admin and user)
6. Get a list of posts (Admin and user) + pagination via cursors
7. Get a single post (Admin and user) (record the requester as a viewer)
8. Each request implies validation of passed parameters, error handling, and clear error responses in case of errors.

Mandatory technical stack:

- NestJS framework
- Database: PostgreSQL with PrismaJS
- API: GraphQL (Code-first)
- Wrap the entire project in Docker
- It will be a plus if you cover the Post module with unit tests.
