# User Microservice

A lightweight microservice that fetches user data from the GitHub API.

## Features

- **GitHub API Integration**: Fetches user profiles from GitHub
- **RESTful API**: Simple GET endpoint for retrieving users
- **Error Handling**: Proper error responses for failed requests

## Dependencies

- **express**: Web framework for Node.js
- **axios**: HTTP client for making external API requests
- **nodemon**: Development tool for hot reloading

## Configuration

- **Port**: 3006
- **External API**: https://api.github.com

## API Endpoints

### GET /users/:id

Fetches a GitHub user by username.

**Parameters:**
- `id` (path parameter): GitHub username

**Example Request:**
```bash
curl http://localhost:3006/users/octocat
```

**Success Response (200):**
```json
{
  "login": "octocat",
  "id": 583231,
  "avatar_url": "https://avatars.githubusercontent.com/u/583231?v=4",
  "name": "The Octocat",
  "company": "@github",
  "blog": "https://github.blog",
  "location": "San Francisco",
  "email": null,
  "bio": null,
  "public_repos": 8,
  "followers": 9000,
  "following": 9,
  "followers_url": "https://api.github.com/users/octocat/followers",
  "following_url": "https://api.github.com/users/octocat/following{/other_user}",
  "repos_url": "https://api.github.com/users/octocat/repos",
  "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
  ...
}
```

**Error Responses:**
- `404 Not Found`: User not found
- `500 Internal Server Error`: Server error or external API failure

## Running the Service

### With Docker

```bash
docker build -t user-microservice .
docker run -p 3006:3006 user-microservice
```

### Locally

```bash
npm install
npm run dev
```

## Development

Use nodemon for development with hot reloading:

```bash
npm run dev
```

The service will automatically restart when you make changes to the code.

## Testing

Test the endpoint with curl:

```bash
# Fetch a specific user
curl http://localhost:3006/users/octocat

# Test with different usernames
curl http://localhost:3006/users/torvalds
```

## GitHub API Rate Limiting

Note: The GitHub API has rate limits for unauthenticated requests (60 requests per hour). For production use, consider:
- Adding GitHub API authentication
- Implementing caching
- Adding rate limiting

## Author

Efrain Guerrero
