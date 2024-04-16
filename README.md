# Cloud Function Documentation - GPT-API

## Overview
This cloud function, named `helloHttp`, is designed to interact with the OpenAI GPT API. It accepts POST requests containing specific user and system content, processes it, and sends it to the OpenAI GPT API to generate a response based on the input.

## Prerequisites
- Node.js installed along with npm.
- An active Google Cloud project with the Functions Framework (`@google-cloud/functions-framework`).
- Axios (`axios`) for making HTTP requests.
- An API key for the OpenAI GPT service, stored in the environment variable `SECRET_KEY`.

## API Endpoint: `helloHttp`

### Request
- **Method:** POST
- **Headers:**
  - Content-Type: application/json
- **Body:**
  - `content`: JSON object containing:
    - `system`: String representing system context or instructions.
    - `user`: String representing the user's input.

### Response
- **Success:**
  - Status Code: `200`
  - Body: JSON object representing the response from the GPT model.
- **Errors:**
  - `405 Method Not Allowed`: If the request method is not POST.
  - `400 Bad Request`: If the required `content.user` field is missing.
  - `500 Internal Server Error`: Server-side error details.
  - Other status codes as returned by the GPT API.

### Error Handling
The function includes detailed error handling for various scenarios such as unsupported HTTP methods, missing required fields, and errors from the GPT API.

## Example

### Request Example
```json
{
  "content": {
    "system": "System prompts or instructions",
    "user": "User's query or statement"
  }
}
