# API Response Codes

This document details the HTTP response codes you may encounter when interacting with the ChartMuseum API.

## Common Response Codes

| Code | Meaning                                      | Typical Scenarios                                      |
|------|----------------------------------------------|--------------------------------------------------------|
| 200  | OK                                           | Successful GET, HEAD, DELETE requests                  |
| 201  | Created                                      | Chart or provenance file successfully uploaded         |
| 400  | Bad Request                                  | Invalid request parameters, malformed data             |
| 401  | Unauthorized                                 | Authentication required or failed                      |
| 404  | Not Found                                    | Resource does not exist (chart, version, file, etc.)   |
| 409  | Conflict                                     | Chart version already exists, overwrite not allowed    |
| 413  | Payload Too Large                            | Uploaded file exceeds maximum allowed size             |
| 500  | Internal Server Error                        | Unexpected server error                                |
| 507  | Insufficient Storage                         | Repository or server has reached object limit          |

## Example Scenarios

- **GET /api/charts**: Returns `200 OK` with a list of charts.
- **POST /api/charts**: Returns `201 Created` if upload succeeds, `409 Conflict` if chart version exists, `413 Payload Too Large` if file is too big, `507 Insufficient Storage` if repo is full.
- **GET /api/charts/<name>**: Returns `200 OK` if chart exists, `404 Not Found` if not.
- **DELETE /api/charts/<name>/<version>**: Returns `200 OK` if deleted, `404 Not Found` if not found.
- **GET /health**: Returns `200 OK` if server is healthy.

## Error Response Format

Error responses are returned as JSON objects:

```json
{
  "error": "Error message here"
}
```

## Notes
- Some endpoints may require authentication and return `401 Unauthorized` if credentials are missing or invalid.
- For more details on API endpoints, see the project [README](https://github.com/helm/chartmuseum/blob/main/README.md).
