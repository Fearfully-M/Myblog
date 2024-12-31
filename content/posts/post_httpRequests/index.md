+++
title = "A Beginner's Guide to HTTP Requests"
date = 2024-12-31
draft = false
tags = ['HTTP', 'Intro']
categories = ['computer science', 'HTTP Requests']

[cover]
    image = 'HttpRequests.jpg'
    alt = 'This is a post image'
    caption = 'This is the caption'

[editPost]
    URL = "https://github.com/link/content"
    Text = "Suggest changes on this repository!!" 
    appendFilePath = true 

+++

**A Beginner's Guide to HTTP Requests**

### What Are HTTP Requests?

HTTP (HyperText Transfer Protocol) is the foundation of communication on the web. When you access a website, your browser sends an HTTP request to the server hosting the site, and the server responds with the requested resources or an error message.

HTTP requests are categorized into methods, and the server’s response includes status codes indicating the result of the request.

---

### Common HTTP Status Codes

HTTP status codes are three-digit numbers that inform you about the result of an HTTP request. Here are some commonly encountered codes:

### Informational Responses (1xx):

- **100: Continue** — Indicates the request can proceed.
- **101: Switching Protocols** — The server is switching to a different protocol, as requested.

### Successful Responses (2xx):

- **200: OK** — The request succeeded, and the server returned the expected response.
- **201: Created** — A resource was successfully created.
- **204: No Content** — The request was successful, but no content is returned.

### Redirection Responses (3xx):

- **301: Moved Permanently** — The resource is now permanently located at a new URL.
- **302: Found** — Temporary redirection to another URL.

### Client Error Responses (4xx):

- **400: Bad Request** — The server couldn’t understand the request.
- **403: Forbidden** — The server refuses to fulfill the request.
- **404: Not Found** — The resource couldn’t be found on the server.

### Server Error Responses (5xx):

- **500: Internal Server Error** — The server encountered an unexpected error.
- **503: Service Unavailable** — The server is temporarily unable to handle the request.

---

### HTTP Methods and Their Uses

HTTP methods specify the desired action for a resource. Here are the most common methods:

### 1. **GET**

Used to retrieve data from a server. GET requests are read-only and do not modify data.

**Example Use Case**: Fetching a webpage or retrieving API data.

```
import requests
response = requests.get('https://jsonplaceholder.typicode.com/posts')
print(response.json())
```

### 2. **POST**

Used to send data to the server, often for creating resources.

**Example Use Case**: Submitting a form or posting a comment.

```
payload = {"title": "New Post", "body": "This is the content.", "userId": 1}
response = requests.post('https://jsonplaceholder.typicode.com/posts', json=payload)
print(response.status_code)  # 201 Created
```

### 3. **PUT**

Used to update an existing resource. Unlike POST, PUT is idempotent—sending the same request multiple times results in the same outcome.

**Example Use Case**: Updating user profile information.

```
updated_data = {"title": "Updated Post", "body": "Updated content.", "userId": 1}
response = requests.put('https://jsonplaceholder.typicode.com/posts/1', json=updated_data)
print(response.status_code)  # 200 OK
```

### 4. **DELETE**

Used to delete a resource from the server.

**Example Use Case**: Removing a user’s account.

```
response = requests.delete('https://jsonplaceholder.typicode.com/posts/1')
print(response.status_code)  # 200 OK or 204 No Content
```

---

### Python's `requests` Library

Python's `requests` library simplifies HTTP requests with its user-friendly interface. It supports all common HTTP methods and provides functions to handle responses.

**Key Features:**

- Easily send GET, POST, PUT, and DELETE requests.
- Handle JSON data seamlessly.
- Manage headers, query parameters, and authentication.

**Example:**

```
import requests

url = 'https://api.example.com/resource'
headers = {'Authorization': 'Bearer YOUR_TOKEN'}
response = requests.get(url, headers=headers)

if response.status_code == 200:
    print("Request successful:", response.json())
else:
    print("Error:", response.status_code)
```

---

### Conclusion

Understanding HTTP requests and status codes is essential for working with web applications. The `requests` library in Python makes handling these requests straightforward, allowing developers to focus on building robust applications. By mastering methods like GET, POST, PUT, and DELETE, you can effectively interact with APIs and other web services.