# Repository Management API

A FastAPI-based service for managing user-specific Git repositories. This API allows authenticated users to create and manage bare Git repositories on the server, supporting automation and integration with developer workflows.

## Features

- **User Authentication**: Secure endpoints with authentication (see `auth.py`).
- **Repository Creation**: Create bare Git repositories per user via API.
- **Filesystem Isolation**: Each user's repositories are stored in their own directory.
- **Extensible**: Designed for easy addition of more repository management features.

## API Endpoints

### Create Repository

```
POST /repos/{repo_name}
```

- **Description**: Creates a new bare Git repository for the authenticated user.
- **Path Parameter**: `repo_name` – Name of the repository to create.
- **Authentication**: Required (see below).
- **Response**: `{ "message": "Repository created", "repo": "<repo_name>", "user": "<username>" }`

## Authentication

This API uses a custom authentication system. See `repository_management_api/auth.py` for details. You must provide valid credentials to access protected endpoints.

## Getting Started

### Prerequisites
- Python 3.10+
- Git installed on the server

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your-org/repository-management-api.git
   cd repository-management-api
   ```
2. Install dependencies:
   ```sh
   uv sync
   ```
3. Run the application:
   ```sh
   uvicorn repository_management_api.main:app --reload
   ```

### Directory Structure
- User repositories are stored under `/srv/git/<username>/<repo_name>.git`.

## Development

- Tests are located in the `tests/` directory.
- Use VSCode's test runner or run `pytest` manually.
- Lint and format code before submitting changes.

## Contributing

Contributions are welcome! Please open issues or submit pull requests. Ensure your code is tested and documented.

## License

This project is licensed under the MIT License.
