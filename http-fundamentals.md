# HTTP Fundamentals – Complete Notes

These notes cover the HTTP protocol end to end, including its evolution, message structure, headers, methods, CORS, status codes, caching, compression, and security. This content is aligned with real backend development and system design usage.

---

## 1. Introduction to HTTP

HTTP (HyperText Transfer Protocol) is the foundation of communication on the web and one of the most important protocols for backend applications.

### Core Properties

#### Stateless Protocol

- Each HTTP request is independent
- The server does not remember previous requests
- Any required state must be sent with each request (cookies, tokens, headers)

#### Client–Server Model

- Client initiates the request (browser, mobile app, API client)
- Server processes the request and returns a response
- Communication is always request–response based

#### Transport Layer

- HTTP uses **TCP** as its transport protocol
- TCP provides reliability, ordering, and retransmission

---

## 2. Evolution of HTTP

### HTTP/1.0

- One TCP connection per request
- Very inefficient due to repeated connection setup and teardown

### HTTP/1.1

- Introduced **persistent connections**
- Multiple requests can reuse the same TCP connection
- Major performance improvement

### HTTP/2

- Uses a single connection with **multiplexing**
- Binary framing instead of text
- Header compression
- Solves head-of-line blocking at application level

### HTTP/3

- Built on **QUIC**, which runs over UDP
- Faster connection establishment
- Better handling of packet loss
- Lower latency, especially on unstable networks

---

## 3. HTTP Messages

HTTP communication happens using **messages**.

### Request Message Structure

- Request line (method, URL, HTTP version)
- Headers
- Optional body

Example:

```
GET /users HTTP/1.1
Host: example.com
Authorization: Bearer token
```

### Response Message Structure

- Status line (HTTP version, status code)
- Headers
- Optional body

Example:

```
HTTP/1.1 200 OK
Content-Type: application/json
```

---

## 4. Why HTTP Headers Are Needed

Headers are **key-value pairs** that carry metadata about the request or response.

They allow:

- Quick processing without reading the body
- Instructions to servers, browsers, and intermediaries
- Authentication, caching, compression, and security

Headers act like a **remote control** for HTTP behavior.

---

## 5. Types of HTTP Headers

### Request Headers

Provide information about the client.

Examples:

- `User-Agent`
- `Authorization`
- `Accept`

### General Headers

Apply to both requests and responses.

Examples:

- `Date`
- `Cache-Control`
- `Connection`

### Representation Headers

Describe the body content.

Examples:

- `Content-Type`
- `Content-Length`
- `Content-Encoding`

### Security Headers

Protect against common attacks.

Examples:

- `Strict-Transport-Security`
- `Content-Security-Policy`
- `X-Frame-Options`

### Header Characteristics

- Extensible
- Backward compatible
- Do not break existing clients

---

## 6. HTTP Methods

HTTP methods define **what action the client wants to perform**.

### Common Methods

| Method | Purpose |
|--------|---------|
| GET | Fetch data |
| POST | Create data |
| PATCH | Partial update |
| PUT | Replace resource |
| DELETE | Remove resource |

---

## 7. Idempotent vs Non-Idempotent Methods

### Idempotent Methods

Calling multiple times gives the same result.

- GET
- PUT
- DELETE

### Non-Idempotent Methods

Multiple calls produce different results.

- POST

Idempotency is important for retries and fault tolerance.

---

## 8. OPTIONS Method and CORS

### OPTIONS Method

- Used to ask the server what is allowed
- Commonly used in cross-origin requests

### Same-Origin Policy

Browsers restrict requests to the same origin for security.

### CORS (Cross-Origin Resource Sharing)

A browser-enforced security mechanism that allows controlled cross-origin access.

---

## 9. CORS Request Flows

### Simple Request Flow

- Methods: GET, POST, HEAD
- Browser adds `Origin` header
- Server responds with `Access-Control-Allow-Origin`

### Preflighted Request Flow

- Browser sends an OPTIONS request first
- Triggered by:
  - Non-simple methods
  - Custom headers
- Server responds with allowed methods and headers
- Actual request is sent only if allowed

---

## 10. HTTP Response Status Codes

Status codes are three-digit numbers that indicate the result of a request.

### Categories

#### 1xx – Informational

- Request received, continue processing

#### 2xx – Success

- 200 OK
- 201 Created
- 204 No Content

#### 3xx – Redirection

- 301 Moved Permanently
- 302 Found
- 304 Not Modified

#### 4xx – Client Errors

- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 405 Method Not Allowed
- 409 Conflict
- 429 Too Many Requests

#### 5xx – Server Errors

- Internal server failures
- Timeout issues
- Crashes or misconfigurations

---

## 11. HTTP Caching

Caching improves performance by:

- Reducing server load
- Reducing latency
- Serving responses closer to the client

Common headers:

- `Cache-Control`
- `ETag`
- `If-None-Match`

---

## 12. HTTP Content Negotiation

Allows clients and servers to agree on the best representation.

Examples:

- JSON vs XML
- English vs French

Headers involved:

- `Accept`
- `Accept-Language`
- `Accept-Encoding`

---

## 13. HTTP Compression

Compression reduces response size.

Common algorithms:

- Gzip
- Brotli

Headers used:

- `Content-Encoding`
- `Accept-Encoding`

---

## 14. Persistent Connections and Keep-Alive

- A single TCP connection is reused for multiple requests
- Reduces handshake overhead
- Improves performance

Controlled using:

- `Connection: keep-alive`

---

## 15. Multipart Data and Chunked Transfer

### Multipart Data

- Used for file uploads
- `multipart/form-data`
- Sends multiple parts in one request

### Chunked Transfer Encoding

- Sends data in chunks
- Used for streaming responses
- Size is not known upfront

---

## 16. SSL, TLS, and HTTPS

### HTTPS

- Secure version of HTTP
- Uses TLS for encryption

### What TLS Provides

- Encryption
- Data integrity
- Authentication

HTTPS protects data from:

- Man-in-the-middle attacks
- Eavesdropping
- Data tampering

---

## Summary

- HTTP is stateless and client-server based
- Headers control behavior and metadata
- Methods define intent
- Status codes communicate outcomes
- CORS protects users
- Caching, compression, and persistence improve performance
- HTTPS secures communication
