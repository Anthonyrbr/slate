# Errors

The Signal API uses the following error codes:


| Error Code | Error Message                                                |
| ---------- | ------------------------------------------------------------ |
| 400        | Bad Request - The request could not be understood or was missing required parameters. |
| 401        | Unauthorized - Authentication failed or user does not have permissions for the requested operation. |
| 403        | Forbidden - The requested resource is forbidden and access is not allowed. |
| 404        | Not Found - The requested resource could not be found.       |
| 405        | Method Not Allowed - The HTTP method used is not supported for this resource. |
| 406        | Not Acceptable - The requested resource is capable of generating only content not acceptable according to the Accept headers sent in the request. |
| 410        | Gone - The requested resource is no longer available and has been permanently removed from the server. |
| 429        | Too Many Requests - The user has sent too many requests in a given amount of time ("rate limiting"). |
| 500        | Internal Server Error - The server encountered an unexpected condition that prevented it from fulfilling the request. |
| 503        | Service Unavailable - The server is currently unavailable due to maintenance or overload. Please try again later. |
