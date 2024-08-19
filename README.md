Vidly API
## Endpoints

### 1. Get All Courses

- **Endpoint**: `/api/courses`
- **Method**: `GET`
- **Description**: Retrieve a list of all courses.
- **Response**:
  - **Status**: `200 OK`
  - **Body**:
    ```json
    [
      {
        "id": 1,
        "name": "course 1"
      },
      {
        "id": 2,
        "name": "course 2"
      }
    ]
    ```

### 2. Get a Single Course

- **Endpoint**: `/api/courses/:id`
- **Method**: `GET`
- **Description**: Retrieve details of a single course by its ID.
- **URL Params**:
  - `id` (required): The ID of the course to retrieve.
- **Response**:
  - **Status**: `200 OK`
  - **Body**:
    ```json
    {
      "id": 1,
      "name": "course 1"
    }
    ```
  - **Status**: `404 Not Found` (if course does not exist)
  - **Body**:
    ```json
    "Course not found"
    ```

### 3. Create a New Course

- **Endpoint**: `/api/courses`
- **Method**: `POST`
- **Description**: Add a new course to the list.
- **Request Body**:
  - **Content-Type**: `application/json`
  - **Body**:
    ```json
    {
      "name": "New Course Name"
    }
    ```
- **Response**:
  - **Status**: `201 Created`
  - **Body**:
    ```json
    {
      "id": 3,
      "name": "New Course Name"
    }
    ```
  - **Status**: `400 Bad Request` (if validation fails)
  - **Body**:
    ```json
    "Name is required and should be at least 3 characters long"
    ```

### 4. Update an Existing Course

- **Endpoint**: `/api/courses/:id`
- **Method**: `PUT`
- **Description**: Update the details of an existing course by its ID.
- **URL Params**:
  - `id` (required): The ID of the course to update.
- **Request Body**:
  - **Content-Type**: `application/json`
  - **Body**:
    ```json
    {
      "name": "Updated Course Name"
    }
    ```
- **Response**:
  - **Status**: `200 OK`
  - **Body**:
    ```json
    {
      "id": 1,
      "name": "Updated Course Name"
    }
    ```
  - **Status**: `404 Not Found` (if course does not exist)
  - **Body**:
    ```json
    "Course not found"
    ```
  - **Status**: `400 Bad Request` (if validation fails)
  - **Body**:
    ```json
    "Name is required and should be at least 3 characters long"
    ```

### 5. Delete a Course

- **Endpoint**: `/api/courses/:id`
- **Method**: `DELETE`
- **Description**: Delete a course by its ID.
- **URL Params**:
  - `id` (required): The ID of the course to delete.
- **Response**:
  - **Status**: `200 OK`
  - **Body**:
    ```json
    {
      "id": 1,
      "name": "course 1"
    }
    ```
  - **Status**: `404 Not Found` (if course does not exist)
  - **Body**:
    ```json
    "Course not found"
    ```

## Validation

The API uses `Joi` for input validation. The `name` field is required and must be at least 3 characters long.

## Setup and Running

1. **Install Dependencies**:
   ```bash
   npm install express joi
