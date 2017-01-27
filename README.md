## Naming
The allowed and recommended characters for an URL safe naming of members are defined in the format spec. To also standardize member names, the following (more restrictive) rules are recommended:
* Member names SHOULD start and end with the characters “a-z” (U+0061 to U+007A)
* Member names SHOULD contain only the characters “a-z” (U+0061 to U+007A), “0-9” (U+0030 to U+0039), and the hyphen minus (U+002D HYPHEN-MINUS, “-“) as separator between multiple words.

## standard
| Type    | Description                                                                                         | Required Keys   | Optional Keys |
|---------|-----------------------------------------------------------------------------------------------------|-----------------|---------------|
| success | All went well, and (usually) some data was returned.                                                | status, data   |               |
| fail    | There was a problem with the data submitted, or some pre-condition of the API call wasn't satisfied | status, data    |               |
| error   | An error occurred in processing the request, i.e. an exception was thrown                           | status, message | code, data    |

## Success
 GET /posts.json:
```
{
    status : "success",
    data : {
        "posts" : [
            { "id" : 1, "title" : "A blog post", "body" : "Some useful content" },
            { "id" : 2, "title" : "Another blog post", "body" : "More content" },
        ]
     }
}
```
GET /posts/2.json:
```
{
    status : "success",
    data : { "post" : { "id" : 2, "title" : "Another blog post", "body" : "More content" }}
}
```

## Error
```
{
    "status" : "error",
    "message" : "Unable to communicate with database",
}
```

## Fail API Validation
```
{
    "status" : "fail",
    "message": { "title" : "A title is required" }
}
```

## URL (Only Lower Case)
```
/photos/1/relationships/comments
```

## Pagination

```
example?page=1&size=10

```
## Create
```
{
    "status : "success",
    "message":"Data Successfully Created"}
}
```
## Put
```
{
    "status : "success",
    "message":"Data Successfully Updated"}
}
```

## Delete
```
{
    "status : "success",
    "message":"Data Successfully Deleted"}
}
```
## Not Found
```
{
    "status : "fail",
    "message":"Data Not Found"}
}
```

## Status Code

| No | Code | Description                                                                                                                                     |
|----|------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | 200  | OK - Response to a successful GET, PUT, PATCH or DELETE. Can also be used for a POST that doesn't result in a creation.                         |
| 2  | 201  | Created - Response to a POST that results in a creation. Should be combined with a Location header pointing to the location of the new resource |
| 3  | 204  | No Content - Response to a successful request that won't be returning a body (like a DELETE request)                                            |
| 4  | 304  | Not Modified - Used when HTTP caching headers are in play                                                                                       |
| 5  | 400  | Bad Request - The request is malformed, such as if the body does not parse                                                                      |
| 6  | 401  | Unauthorized - When no or invalid authentication details are provided. Also useful to trigger an auth popup if the API is used from a browser   |
| 7  | 403  | Forbidden - When authentication succeeded but authenticated user doesn't have access to the resource                                            |
| 8  | 404  | Not Found - When a non-existent resource is requested                                                                                           |
| 9  | 405  | Method Not Allowed - When an HTTP method is being requested that isn't allowed for the authenticated user                                       |
| 10 | 410  | Gone - Indicates that the resource at this end point is no longer available. Useful as a blanket response for old API versions                  |
| 11 | 415  | Unsupported Media Type - If incorrect content type was provided as part of the request                                                          |
| 12 | 422  | Unprocessable Entity - Used for validation errors                                                                                               |
| 13 | 429  | Too Many Requests - When a request is rejected due to rate limiting                                                                             |
| 14 | 500  | InternalServerErrorException |
| 15 | 503  | ServiceUnavailableException |

## 400 Status Code 
400.1  – Invalid Destination Header <br />
400.2 – Invalid Depth Header <br />
400.3 – Invalid If Header <br />
400.4 – Invalid Overwrite Header <br />
400.5 – Invalid Translate Header <br />
400.6 – Invalid Request Body <br />
400.7 – Invalid Content Length <br />
400.8 – Invalid Timeout <br />
400.9 – Invalid Lock Token <br />

References : 
* https://tools.ietf.org/html/rfc7231#section-6.5.1
* https://dev.twitter.com/overview/api/response-codes
* http://labs.omniti.com/labs/jsend
* http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
* http://www.helpdesksoftware.biz/400-bad-request/ 
