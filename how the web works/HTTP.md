# What is HTTP? (HyperText Transfer Protocol)

HTTP is what's used whenever you view a website, developed by Tim Berners-Lee and his team between 1989-1991. HTTP is the set of rules used for communicating with web servers for the transmitting of webpage data, whether that is HTML, Images, Video, etc.

## What is HTTPS? (HyperText Transfer Protocol Secure)

HTTPS is the secure version of HTTP. HTTPS data is encrypted so it not only stops people from seeing the data you are receiving and sending, but it also gives you assurances that you're talking to the correct web server and not something impersonating it.

---

## Requests and Responses

When we access a website, your browser will need to make requests to a web server for assets such as HTML, Images, and download the responses. Before that, you need to tell the browser specifically how and where to access these resources, this is where URLs will help.

### What is a URL (Uniform Resource Locator)?

If you've used the internet, you've used a URL before. A URL is predominantly an instruction on how to access a resource on the internet. The image below shows what a URL looks like with all of its features (not every request uses all features):

![All the stuffs in a URL](./images/URL_all_in.png)

- **Scheme**: This instructs on what protocol to use for accessing the resource such as HTTP, HTTPS, FTP (File Transfer Protocol).
- **User**: Some services require authentication to log in. You can put a username and password into the URL to log in.
- **Host/Domain**: The domain name or IP address of the server you wish to access.
- **Port**: The port that you are going to connect to, usually 80 for HTTP and 443 for HTTPS, but this can be hosted on any port between 1-65535.
- **Path**: The file name or location of the resource you are trying to access.
- **Query String**: Extra bits of information that can be sent to the requested path. For example, `/blog?id=1` would tell the blog path that you wish to receive the blog article with the ID of 1.
- **Fragment**: A reference to a location on the actual page requested. This is commonly used for pages with long content to link directly to a specific section.

---

## Making a Request

It's possible to make a request to a web server with just one line:

```
GET / HTTP/1.1
```

- **GET**: The request method.
- **/**: The root path of the requested resource.
- **HTTP/1.1**: The HTTP protocol version.

For a richer web experience, additional data is sent in what is called headers. Headers contain extra information for the web server.

### Example Request:

```
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com
```

- **Line 1**: The request is sending the GET method, requesting the home page (`/`), and specifying the HTTP protocol version (1.1).
- **Line 2**: Specifies the host (website) being requested.
- **Line 3**: Indicates the browser being used (Firefox version 87).
- **Line 4**: Shows the referring webpage.
- **Line 5**: HTTP requests always end with a blank line to indicate the request has finished.

### Example Response:

```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 02 Jan 2025 07:27:05 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

- **Line 1**: HTTP version and status code (200 OK), indicating a successful request.
- **Line 2**: The web server software and version.
- **Line 3**: The date, time, and timezone of the web server.
- **Line 4**: Content-Type header, specifying the type of content (HTML).
- **Line 5**: Content-Length, indicating the length of the response.
- **Line 6**: A blank line confirming the end of the HTTP response.
- **Lines 7-14**: The requested information (HTML content).

---

## HTTP Methods

HTTP Methods indicate the client’s intended action when making a request. Common methods include:

- **GET**: Retrieves information from the server.
- **POST**: Submits data to the server, potentially creating new records.
- **PUT**: Updates information on the server.
- **DELETE**: Deletes information/records from the server.

---

## HTTP Status Codes

### Status Code Ranges:

- **100-199**: Information responses.
- **200-299**: Success responses.
- **300-399**: Redirection responses.
- **400-499**: Client error responses.
- **500-599**: Server error responses.

### Common HTTP Status Codes:

| Status Code | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| 200         | OK - Request completed successfully.                                       |
| 201         | Created - A resource has been created.                                     |
| 301         | Moved Permanently - Permanent redirect to another resource.               |
| 302         | Found - Temporary redirect.                                               |
| 400         | Bad Request - The client’s request was invalid or incomplete.               |
| 401         | Not Authorized - Requires authentication.                                 |
| 403         | Forbidden - Permission denied.                                            |
| 404         | Page Not Found - Resource does not exist.                                 |
| 405         | Method Not Allowed - Method not permitted for the resource.               |
| 500         | Internal Server Error - Server-side error.                                |
| 503         | Service Unavailable - Server overloaded or down for maintenance.          |

---

## Headers

Headers are additional data sent with requests or responses.

### Common Request Headers:

- **Host**: Specifies the website being requested.
- **User-Agent**: Indicates the browser software and version.
- **Content-Length**: Specifies the size of the data being sent.
- **Accept-Encoding**: Lists supported compression methods.
- **Cookie**: Contains data for server-side session tracking.

### Common Response Headers:

- **Set-Cookie**: Sends data to the client for future requests.
- **Cache-Control**: Specifies caching duration for resources.
- **Content-Type**: Indicates the type of returned data (HTML, JSON, etc.).
- **Content-Encoding**: Describes compression methods used for the response.

---

## Cookies

Cookies are small pieces of data stored on your computer. They are used for:

- **Authentication**: Maintaining login sessions.
- **Personalization**: Saving user preferences.
- **Tracking**: Remembering previous visits or actions.

Cookies are sent via the "Set-Cookie" header and returned in subsequent requests. To view cookies:

1. Open your browser’s developer tools.
2. Navigate to the "Network" tab.
3. Inspect requests and look for the "Cookies" section.

