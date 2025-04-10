---
title: Trackit API Documentation v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="trackit-api-documentation">Trackit API Documentation v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the official API documentation for **Trackit**, a collaborative project and task management tool.

🚀 Core Features:
- Create and manage tasks within projects
- Real-time collaboration through comments and mentions
- Track task history and progress updates
- Use the integrated ChatGPT assistant for help

🔒 Security:
- Supports Bearer Token, API Key, and OAuth 2.0 flows

📌 Special Behaviors:
- Use `@mention` in comment content to trigger notifications
- Query the `/assistant/ask` endpoint for help using ChatGPT 

Base URLs:

* <a href="https://localhost/:8080">https://localhost/:8080</a>

* <a href="https://example.com/v1">https://example.com/v1</a>

* <a href="https://example.com/sandbox">https://example.com/sandbox</a>

* <a href="https://6555ad9d-d24f-4107-b46f-e2343c0d65b7.mock.pstmn.io">https://6555ad9d-d24f-4107-b46f-e2343c0d65b7.mock.pstmn.io</a>

<a href="https://example.com/terms/">Terms of service</a>
Email: <a href="mailto:api-support@trackitapp.com">Trackit API Support</a> Web: <a href="https://example.com/support/">Trackit API Support</a> 
License: <a href="https://opensource.org/license/MIT">MIT license</a>

# Authentication

- HTTP Authentication, scheme: bearer 

* API Key (ApiKeyAuth)
    - Parameter Name: **X-API-KEY**, in: header. 

- oAuth2 authentication. 

    - Flow: authorizationCode
    - Authorization URL = [https://auth.example.com/oauth/authorize](https://auth.example.com/oauth/authorize)
    - Token URL = [https://auth.example.com/oauth/token](https://auth.example.com/oauth/token)

|Scope|Scope Description|
|---|---|
|profile|Access to user profile|
|tasks|Access to task resource|
|projects|Access to project resources|

- oAuth2 authentication. 

    - Flow: clientCredentials

    - Token URL = [https://auth.example.com/oauth/token](https://auth.example.com/oauth/token)

|Scope|Scope Description|
|---|---|
|read|Read only access to tasks|
|write|Read Write access to tasks|
|projects|Access to project data|
|admin|Admin-level permissions|

<h1 id="trackit-api-documentation-authentication">Authentication</h1>

User registration and login

## Register a new user

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/auth/register \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://localhost/:8080/auth/register HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "registration": {
    "email": "summer.lee@example.com",
    "password": "passwordforsummer123",
    "fullName": "Summer Lee"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/auth/register',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://localhost/:8080/auth/register',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://localhost/:8080/auth/register', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/auth/register', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/auth/register");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/auth/register", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/register`

Submit user information to create a new Trackit account.

> Body parameter

```json
{
  "registration": {
    "email": "summer.lee@example.com",
    "password": "passwordforsummer123",
    "fullName": "Summer Lee"
  }
}
```

<h3 id="register-a-new-user-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» registration|body|[Registration](#schemaregistration)|false|Schema for registering a new user.|
|»» email|body|string|false|Email address of the user.|
|»» password|body|string|false|Password for the user account.|
|»» fullName|body|string|false|Full name of the user.|

> Example responses

> 201 Response

```json
{
  "fullName": "Summer Lee"
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

<h3 id="register-a-new-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|User registered successfully with provided credentials.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|

<h3 id="register-a-new-user-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» fullName|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Login to receive a JWT token

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/auth/login \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'X-API-KEY: API_KEY'

```

```http
POST https://localhost/:8080/auth/login HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "string",
  "password": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'X-API-KEY':'API_KEY'
};

fetch('https://localhost/:8080/auth/login',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'X-API-KEY' => 'API_KEY'
}

result = RestClient.post 'https://localhost/:8080/auth/login',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-API-KEY': 'API_KEY'
}

r = requests.post('https://localhost/:8080/auth/login', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'X-API-KEY' => 'API_KEY',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/auth/login', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/auth/login");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "X-API-KEY": []string{"API_KEY"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/auth/login", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /auth/login`

Authenticate an existing user and return a JWT access token for subsequent requests.

> Body parameter

```json
{
  "email": "string",
  "password": "string"
}
```

<h3 id="login-to-receive-a-jwt-token-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» email|body|string|true|Email address used for login.|
|» password|body|string|true|User account password.|

> Example responses

> 200 Response

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

<h3 id="login-to-receive-a-jwt-token-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User successfully authenticated and token returned.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|

<h3 id="login-to-receive-a-jwt-token-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» token|string|false|none|JWT token for authenticated requests.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKeyAuth
</aside>

## OAuth2 Callback Redirect URI

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/auth/callback?code=string \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/auth/callback?code=string HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/auth/callback?code=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/auth/callback',
  params: {
  'code' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/auth/callback', params={
  'code': 'string'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/auth/callback', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/auth/callback?code=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/auth/callback", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /auth/callback`

The redirect URI where Trackit receives the authorization code after user login.

<h3 id="oauth2-callback-redirect-uri-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|code|query|string|true|Authorization code returned by the OAuth provider.|
|state|query|string|false|Optional state parameter for CSRF protection|

> Example responses

> 200 Response

```json
{
  "message": "OAuth callback successfully handled."
}
```

> 400 Response

```json
{
  "status": 400,
  "message": "Missing or invalid authorization code."
}
```

<h3 id="oauth2-callback-redirect-uri-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OAuth callback successfully processed.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request or missing authorization code.|[ErrorResponse](#schemaerrorresponse)|

<h3 id="oauth2-callback-redirect-uri-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» message|string|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-users">Users</h1>

Registered user

## Get current authenticated user.

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/users/me \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://localhost/:8080/users/me HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost/:8080/users/me',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://localhost/:8080/users/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://localhost/:8080/users/me', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/users/me', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/users/me");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/users/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /users/me`

Retrieve information about the currently authenticated user.

> Example responses

> 200 Response

```json
{
  "data": {
    "userId": "user_001",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com",
    "username": "winter"
  }
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

> 403 Response

```json
{
  "status": 403,
  "message": "You are not authorized to acess this resource."
}
```

<h3 id="get-current-authenticated-user.-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User profile successfully retrieved.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden - You do not have access to this resource.|[ErrorResponse](#schemaerrorresponse)|

<h3 id="get-current-authenticated-user.-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»» userId|string|false|none|Unique identifier for the user.|
|»» username|string|false|none|Public-facing username.|
|»» fullName|string|false|none|Full name of the user.|
|»» email|string|false|none|Email address of the user.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oAuth2AuthCode ( Scopes: profile )
</aside>

## Get a user by ID

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/users/{userId} \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/users/{userId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/users/{userId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/users/{userId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/users/{userId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/users/{userId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/users/{userId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /users/{userId}`

Retrieve user details for a given user ID.

<h3 id="get-a-user-by-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|path|string|true|The unique identifier of the user.|

> Example responses

> 200 Response

```json
{
  "data": {
    "userId": "user_003",
    "username": "summer",
    "fullName": "Summer Mi",
    "email": "summer.mi@example.com"
  }
}
```

<h3 id="get-a-user-by-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|User data successfully retrieved.|Inline|

<h3 id="get-a-user-by-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»» userId|string|false|none|Unique identifier for the user.|
|»» username|string|false|none|Public-facing username.|
|»» fullName|string|false|none|Full name of the user.|
|»» email|string|false|none|Email address of the user.|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-projects">Projects</h1>

Project-level operations

## Get all projects

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/projects \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://localhost/:8080/projects HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost/:8080/projects',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://localhost/:8080/projects',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://localhost/:8080/projects', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/projects', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/projects", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /projects`

Retrieve a list of all accessible projects for the authenticated user.

<h3 id="get-all-projects-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number of the result set.|
|limit|query|integer|false|Number of projects per page.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "projectId": "proj_001",
      "title": "Trackit Redesign",
      "description": "UI/UX overhaul of the Trackit platform.",
      "createdAt": "2025-03-01T10:00:00Z",
      "updatedAt": "2025-03-03T15:30:00Z"
    },
    {
      "projectId": "proj_002",
      "title": "Marketing Dashboard",
      "description": "A new dashboard for visualizing marketing KPIs.",
      "createdAt": "2025-03-10T09:15:00Z",
      "updatedAt": "2025-03-11T11:20:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "totalPages": 2,
    "totalProjects": 12
  }
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

> 403 Response

```json
{
  "status": 403,
  "message": "You are not authorized to acess this resource."
}
```

<h3 id="get-all-projects-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of projects successfully retrieved.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden - You do not have access to this resource.|[ErrorResponse](#schemaerrorresponse)|

<h3 id="get-all-projects-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Project](#schemaproject)]|false|none|[Represents a project that contains tasks.]|
|»» projectId|string|false|none|Unique identifier of the project.|
|»» title|string|false|none|Title of the project.|
|»» description|string|false|none|Detailed description of the project.|
|»» createdAt|string(date-time)|false|none|Timestamp when the project was created.|
|»» updatedAt|string(date-time)|false|none|Timestamp when the project was last updated.|
|» meta|object|false|none|none|
|»» page|integer|false|none|none|
|»» totalPages|integer|false|none|none|
|»» totalProjects|integer|false|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Create a new project

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/projects \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://localhost/:8080/projects HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "title": "string",
  "description": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/projects',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://localhost/:8080/projects',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://localhost/:8080/projects', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/projects', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/projects", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /projects`

Submit project title and description to create a new project.

> Body parameter

```json
{
  "title": "string",
  "description": "string"
}
```

<h3 id="create-a-new-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» title|body|string|true|The title of the project.|
|» description|body|string|false|A short explanation of the project's purpose or goals.|

> Example responses

> 201 Response

```json
{
  "data": {
    "projectId": "proj_003",
    "title": "Website Redesign",
    "description": "A complete overhaul of the corporate website, including branding and UX.",
    "createdAt": "2025-04-08T09:00:00Z",
    "updatedAt": "2025-04-08T09:00:00Z"
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

<h3 id="create-a-new-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Project successfully created.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|

<h3 id="create-a-new-project-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Project](#schemaproject)|false|none|Represents a project that contains tasks.|
|»» projectId|string|false|none|Unique identifier of the project.|
|»» title|string|false|none|Title of the project.|
|»» description|string|false|none|Detailed description of the project.|
|»» createdAt|string(date-time)|false|none|Timestamp when the project was created.|
|»» updatedAt|string(date-time)|false|none|Timestamp when the project was last updated.|

<aside class="success">
This operation does not require authentication
</aside>

## Get a specific project ID

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/projects/{projectId} \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/projects/{projectId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/projects/{projectId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/projects/{projectId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/projects/{projectId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/projects/{projectId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects/{projectId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/projects/{projectId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /projects/{projectId}`

Retrieve the details of a project by providing its unique ID.

<h3 id="get-a-specific-project-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|projectId|path|string|true|Unique identifier of the project.|

> Example responses

> 200 Response

```json
{
  "data": {
    "projectId": "proj_112",
    "title": "Website Redesign",
    "description": "Redesign the marketing site with new branding.",
    "owner": {
      "userId": "user_001",
      "username": "winter"
    },
    "createdAt": "2025-03-15T09:00:00Z"
  }
}
```

> 404 Response

```json
{
  "status": 404,
  "message": "Project not found."
}
```

<h3 id="get-a-specific-project-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Project details successfully retrieved.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found.|[#/components/responses/NotFoundError](#schema#/components/responses/notfounderror)|

<h3 id="get-a-specific-project-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Project](#schemaproject)|false|none|Represents a project that contains tasks.|
|»» projectId|string|false|none|Unique identifier of the project.|
|»» title|string|false|none|Title of the project.|
|»» description|string|false|none|Detailed description of the project.|
|»» createdAt|string(date-time)|false|none|Timestamp when the project was created.|
|»» updatedAt|string(date-time)|false|none|Timestamp when the project was last updated.|

<aside class="success">
This operation does not require authentication
</aside>

## Update a specific project

> Code samples

```shell
# You can also use wget
curl -X PUT https://localhost/:8080/projects/{projectId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://localhost/:8080/projects/{projectId} HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "title": "string",
  "description": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/projects/{projectId}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.put 'https://localhost/:8080/projects/{projectId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('https://localhost/:8080/projects/{projectId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://localhost/:8080/projects/{projectId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects/{projectId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://localhost/:8080/projects/{projectId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /projects/{projectId}`

Modify an existing project's title or description by providing its ID.

> Body parameter

```json
{
  "title": "string",
  "description": "string"
}
```

<h3 id="update-a-specific-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|projectId|path|string|true|none|
|body|body|object|true|none|
|» title|body|string|false|none|
|» description|body|string|false|none|

> Example responses

> 200 Response

```json
{
  "data": {
    "projectId": "proj_003",
    "title": "Website Revamp",
    "description": "Update layout and content for the new campaign.",
    "createdAt": "2025-04-08T09:00:00Z",
    "updatedAt": "2025-04-09T10:15:00Z"
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

> 404 Response

```json
{
  "status": 404,
  "message": "Project not found."
}
```

<h3 id="update-a-specific-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Project successfully updated.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Project not found.|[#/components/responses/NotFoundError](#schema#/components/responses/notfounderror)|

<h3 id="update-a-specific-project-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Project](#schemaproject)|false|none|Represents a project that contains tasks.|
|»» projectId|string|false|none|Unique identifier of the project.|
|»» title|string|false|none|Title of the project.|
|»» description|string|false|none|Detailed description of the project.|
|»» createdAt|string(date-time)|false|none|Timestamp when the project was created.|
|»» updatedAt|string(date-time)|false|none|Timestamp when the project was last updated.|

<aside class="success">
This operation does not require authentication
</aside>

## Delete a project

> Code samples

```shell
# You can also use wget
curl -X DELETE https://localhost/:8080/projects/{projectId} \
  -H 'Accept: application/json'

```

```http
DELETE https://localhost/:8080/projects/{projectId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/projects/{projectId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://localhost/:8080/projects/{projectId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://localhost/:8080/projects/{projectId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://localhost/:8080/projects/{projectId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects/{projectId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://localhost/:8080/projects/{projectId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /projects/{projectId}`

Deletes a project by ID. All associated tasks will also be removed.

<h3 id="delete-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|projectId|path|string|true|Unique identifier of the project.|

> Example responses

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="delete-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Project successfully deleted. No content returned.|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-tasks">Tasks</h1>

Create and manage individual tasks

## Get all tasks

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/tasks \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/tasks HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/tasks',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/tasks', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/tasks', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/tasks", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tasks`

Retrieve a paginated list of all tasks assigned to the user. Supports filtering and sorting.

<h3 id="get-all-tasks-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number (default is 1)|
|limit|query|integer|false|Number of tasks per page (default is 20)|
|status|query|string|false|Filter tasks by status|
|sortBy|query|string|false|Sort tasks by a field|
|order|query|string|false|Sort direction (ascending or descending)|

#### Enumerated Values

|Parameter|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|
|sortBy|createdAt|
|sortBy|dueDate|
|sortBy|title|
|order|asc|
|order|desc|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "taskId": "task_001",
      "title": "Design homepage",
      "description": "Create layout wireframes for the homepage",
      "status": "in_progress",
      "assignee": {
        "userId": "user_001",
        "username": "winter",
        "fullName": "Winter Doe",
        "email": "winter.doe@example.com"
      },
      "projectId": "proj_001",
      "createdAt": "2025-04-01T10:00:00Z",
      "dueDate": "2025-04-10"
    }
  ],
  "meta": {
    "totalItems": 48,
    "page": 1,
    "limit": 10,
    "totalPages": 5
  }
}
```

<h3 id="get-all-tasks-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all tasks successfully retrieved.|Inline|

<h3 id="get-all-tasks-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Task](#schematask)]|false|none|[A task assigned to a user within a project.]|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|
|» meta|[PaginationMeta](#schemapaginationmeta)|false|none|Pagination metadata for paginated responses.|
|»» totalItems|integer|false|none|Total number of items available|
|»» page|integer|false|none|Current page number|
|»» limit|integer|false|none|Number of items per page|
|»» totalPages|integer|false|none|Total number of available pages|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

## Create a new task

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/tasks \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://localhost/:8080/tasks HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "projectId": "string",
  "title": "string",
  "description": "string",
  "assignee": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "dueDate": "2019-08-24"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://localhost/:8080/tasks',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://localhost/:8080/tasks', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/tasks', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/tasks", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /tasks`

Submit task details to create a new task under a specific project.

> Body parameter

```json
{
  "projectId": "string",
  "title": "string",
  "description": "string",
  "assignee": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "dueDate": "2019-08-24"
}
```

<h3 id="create-a-new-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» projectId|body|string|true|The ID of the project to associate the task with.|
|» title|body|string|true|The title or name of the task.|
|» description|body|string|false|Detailed information or instructions about the task.|
|» assignee|body|[User](#schemauser)|false|Represents a user of the Trackit system.|
|»» userId|body|string|false|Unique identifier for the user.|
|»» username|body|string|false|Public-facing username.|
|»» fullName|body|string|false|Full name of the user.|
|»» email|body|string|false|Email address of the user.|
|» dueDate|body|string(date)|false|The due date for the task in YYYY-MM-DD format.|

> Example responses

> 201 Response

```json
{
  "data": {
    "taskId": "task_045",
    "projectId": "proj_001",
    "title": "Create landing page",
    "description": "Landing page for new product launch.",
    "status": "pending",
    "assignee": {
      "userId": "user_003",
      "username": "summer",
      "fullName": "Summer Mi",
      "email": "summer.mi@example.com"
    },
    "dueDate": "2025-04-15",
    "createdAt": "2025-04-08T11:12:00Z"
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

<h3 id="create-a-new-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Task successfully created.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|

<h3 id="create-a-new-task-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Task](#schematask)|false|none|A task assigned to a user within a project.|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

## Get a task by task ID

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/tasks/{taskId} \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://localhost/:8080/tasks/{taskId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost/:8080/tasks/{taskId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://localhost/:8080/tasks/{taskId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://localhost/:8080/tasks/{taskId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/tasks/{taskId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/tasks/{taskId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tasks/{taskId}`

Retrieve a single task by its ID.

<h3 id="get-a-task-by-task-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task.|

> Example responses

> 200 Response

```json
{
  "data": {
    "taskId": "task_001",
    "title": "Design homepage",
    "description": "Create layout wireframes for the homepage",
    "status": "in_progress",
    "assignee": {
      "userId": "user_001",
      "username": "winter",
      "fullName": "Winter Doe",
      "email": "winter.doe@example.com"
    },
    "projectId": "proj_001",
    "createdAt": "2025-04-01T10:00:00Z",
    "dueDate": "2025-04-10"
  }
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

> 403 Response

```json
{
  "status": 403,
  "message": "You are not authorized to acess this resource."
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="get-a-task-by-task-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Task successfully retrieved.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden - You do not have access to this resource.|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="get-a-task-by-task-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Task](#schematask)|false|none|A task assigned to a user within a project.|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## Update an entire task

> Code samples

```shell
# You can also use wget
curl -X PUT https://localhost/:8080/tasks/{taskId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://localhost/:8080/tasks/{taskId} HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "taskId": "task_001",
  "title": "Design homepage",
  "description": "Create layout wireframes for the homepage",
  "status": "in_progress",
  "assignee": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "dueDate": "2025-04-10"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.put 'https://localhost/:8080/tasks/{taskId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('https://localhost/:8080/tasks/{taskId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://localhost/:8080/tasks/{taskId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://localhost/:8080/tasks/{taskId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /tasks/{taskId}`

Replaces all attributes of a task with new values.

> Body parameter

```json
{
  "taskId": "task_001",
  "title": "Design homepage",
  "description": "Create layout wireframes for the homepage",
  "status": "in_progress",
  "assignee": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "dueDate": "2025-04-10"
}
```

<h3 id="update-an-entire-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task.|
|body|body|[Task](#schematask)|true|none|

> Example responses

> 200 Response

```json
{
  "data": {
    "taskId": "task_045",
    "title": "Revise landing page copy",
    "description": "Update text and hero section of the landing page",
    "status": "in_progress",
    "assignee": {
      "userId": "user_002",
      "username": "spring",
      "fullName": "Spring Lee",
      "email": "spring.lee@example.com"
    },
    "dueDate": "2025-04-16",
    "createdAt": "2025-04-08T11:12:00Z",
    "updatedAt": "2025-04-09T13:40:00Z"
  }
}
```

<h3 id="update-an-entire-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Task successfully updated.|Inline|

<h3 id="update-an-entire-task-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Task](#schematask)|false|none|A task assigned to a user within a project.|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

## Partially update a task

> Code samples

```shell
# You can also use wget
curl -X PATCH https://localhost/:8080/tasks/{taskId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://localhost/:8080/tasks/{taskId} HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "title": "string",
  "status": "pending",
  "dueDate": "2019-08-24"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://localhost/:8080/tasks/{taskId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://localhost/:8080/tasks/{taskId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PATCH','https://localhost/:8080/tasks/{taskId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://localhost/:8080/tasks/{taskId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /tasks/{taskId}`

Updates one or more attributes of a task (e.g. status or assignee).

> Body parameter

```json
{
  "title": "string",
  "status": "pending",
  "dueDate": "2019-08-24"
}
```

<h3 id="partially-update-a-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task|
|body|body|object|true|none|
|» title|body|string|false|none|
|» status|body|string|false|none|
|» dueDate|body|string(date)|false|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|pending|
|» status|in_progress|
|» status|completed|

> Example responses

> 200 Response

```json
{
  "data": {
    "taskId": "task_045",
    "title": "Refactor landing page layout",
    "description": "Update text and hero section of the landing page.",
    "status": "in_progress",
    "assignee": {
      "userId": "user_002",
      "username": "spring",
      "fullName": "Spring Lee",
      "email": "spring.lee@example.com"
    },
    "projectId": "proj_001",
    "dueDate": "2025-04-20",
    "createdAt": "2025-04-08T11:12:00Z",
    "updatedAt": "2025-04-09T15:45:00Z"
  }
}
```

<h3 id="partially-update-a-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Task successfully patched.|Inline|

<h3 id="partially-update-a-task-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Task](#schematask)|false|none|A task assigned to a user within a project.|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

## Delete a task

> Code samples

```shell
# You can also use wget
curl -X DELETE https://localhost/:8080/tasks/{taskId} \
  -H 'Accept: application/json'

```

```http
DELETE https://localhost/:8080/tasks/{taskId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.delete 'https://localhost/:8080/tasks/{taskId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://localhost/:8080/tasks/{taskId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://localhost/:8080/tasks/{taskId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://localhost/:8080/tasks/{taskId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /tasks/{taskId}`

Permanently removes a task by its ID.

<h3 id="delete-a-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task|

> Example responses

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="delete-a-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Task successfully deleted. No content returned.|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="delete-a-task-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## Get all tasks for a project

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/projects/{projectId}/tasks \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/projects/{projectId}/tasks HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/projects/{projectId}/tasks',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/projects/{projectId}/tasks',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/projects/{projectId}/tasks', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/projects/{projectId}/tasks', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/projects/{projectId}/tasks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/projects/{projectId}/tasks", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /projects/{projectId}/tasks`

Retrieve all tasks belonging to the specified project.

<h3 id="get-all-tasks-for-a-project-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|projectId|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "taskId": "task_001",
      "title": "Design homepage",
      "description": "Create layout wireframes for the homepage",
      "status": "in_progress",
      "assignee": {
        "userId": "user_001",
        "username": "winter"
      },
      "projectId": "proj_001",
      "createdAt": "2025-04-01T10:00:00Z",
      "dueDate": "2025-04-10"
    }
  ],
  "meta": {
    "totalItems": 2,
    "page": 1,
    "limit": 10,
    "totalPages": 1
  }
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

> 403 Response

```json
{
  "status": 403,
  "message": "You are not authorized to acess this resource."
}
```

<h3 id="get-all-tasks-for-a-project-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of tasks retrieved for the specified project.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden - You do not have access to this resource.|[ErrorResponse](#schemaerrorresponse)|

<h3 id="get-all-tasks-for-a-project-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Task](#schematask)]|false|none|[A task assigned to a user within a project.]|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|
|» meta|[PaginationMeta](#schemapaginationmeta)|false|none|Pagination metadata for paginated responses.|
|»» totalItems|integer|false|none|Total number of items available|
|»» page|integer|false|none|Current page number|
|»» limit|integer|false|none|Number of items per page|
|»» totalPages|integer|false|none|Total number of available pages|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

## Update task status

> Code samples

```shell
# You can also use wget
curl -X PATCH https://localhost/:8080/tasks/{taskId}/status \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://localhost/:8080/tasks/{taskId}/status HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "status": "pending"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}/status',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://localhost/:8080/tasks/{taskId}/status',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://localhost/:8080/tasks/{taskId}/status', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PATCH','https://localhost/:8080/tasks/{taskId}/status', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}/status");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://localhost/:8080/tasks/{taskId}/status", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /tasks/{taskId}/status`

Change the status of a task to reflect its progress.

> Body parameter

```json
{
  "status": "pending"
}
```

<h3 id="update-task-status-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task.|
|body|body|object|true|none|
|» status|body|string|true|The new status to assign to the task.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» status|pending|
|» status|in_progress|
|» status|completed|

> Example responses

> 200 Response

```json
{
  "data": {
    "taskId": "task_045",
    "title": "Revise landing page copy",
    "description": "Update text and hero section of the landing page",
    "status": "completed",
    "assignee": {
      "userId": "user_002",
      "username": "spring",
      "fullName": "Spring Lee",
      "email": "spring.lee@example.com"
    },
    "dueDate": "2025-04-16",
    "createdAt": "2025-04-08T11:12:00Z",
    "updatedAt": "2025-04-09T14:30:00Z"
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="update-task-status-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Task status successfully updated.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="update-task-status-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Task](#schematask)|false|none|A task assigned to a user within a project.|
|»» taskId|string|false|none|Unique identifier for the task.|
|»» title|string|false|none|Title of the task.|
|»» description|string|false|none|Detailed description of the task.|
|»» status|string|false|none|Current status of the task.|
|»» assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-comments">Comments</h1>

Comment threads with @mentions

## Add a comment to a task

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/comments \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://localhost/:8080/comments HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "commentId": "cmt_001",
  "taskId": "task_001",
  "author": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "content": "@john please review the UI update.",
  "createdAt": "2025-04-02T09:20:00Z"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/comments',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://localhost/:8080/comments',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://localhost/:8080/comments', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/comments', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/comments");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/comments", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /comments`

Submit a comment to a specific task. Supports @mention syntax (e.g., `@username`) to notify users.

> Body parameter

```json
{
  "commentId": "cmt_001",
  "taskId": "task_001",
  "author": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "content": "@john please review the UI update.",
  "createdAt": "2025-04-02T09:20:00Z"
}
```

<h3 id="add-a-comment-to-a-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Comment](#schemacomment)|true|none|

> Example responses

> 200 Response

```json
{
  "data": {
    "commentId": "cmt_001",
    "taskId": "task_001",
    "author": {
      "userId": "user_001",
      "username": "winter",
      "fullName": "Winter Lee",
      "email": "winter.lee@example.com"
    },
    "content": "@john Please check the latest update on the dashboard.",
    "createdAt": "2025-04-02T10:30:00Z"
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

<h3 id="add-a-comment-to-a-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Comment successfully added to the task.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|

<h3 id="add-a-comment-to-a-task-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Comment](#schemacomment)|false|none|Schema representing a comment on a task, optionally with a mention.|
|»» commentId|string|false|none|Unique identifier for the comment.|
|»» taskId|string|false|none|The ID of the task to comment on.|
|»» author|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» content|string|false|none|The content of the comment.|
|»» createdAt|string(date-time)|false|none|Timestamp of when the comment was created.|

<aside class="success">
This operation does not require authentication
</aside>

## Get comments for a task

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/tasks/{taskId}/comments \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/tasks/{taskId}/comments HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}/comments',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/tasks/{taskId}/comments',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/tasks/{taskId}/comments', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/tasks/{taskId}/comments', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}/comments");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/tasks/{taskId}/comments", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tasks/{taskId}/comments`

Retrieve all comments associated with a specific task.

<h3 id="get-comments-for-a-task-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|The ID of the task to retrieve comments for.|
|preview|query|boolean|false|If true, returns only a preview of each comment.|
|page|query|integer|false|Page number for paginated results.|
|limit|query|integer|false|Maximum number of comments to return per page.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "commentId": "cmt_001",
      "author": {
        "userId": "user_001",
        "username": "winter",
        "fullName": "Winter Doe",
        "email": "winter.doe@example.com"
      },
      "content": "@mike Please add final logo.",
      "createdAt": "2025-04-01T12:00:00Z"
    },
    {
      "commentId": "cmt_002",
      "author": {
        "userId": "user_002",
        "username": "spring",
        "fullName": "Spring Lee",
        "email": "spring.lee@example.com"
      },
      "content": "Final logo added in Figma.",
      "createdAt": "2025-04-01T14:45:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "totalPages": 3,
    "totalComments": 25
  }
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="get-comments-for-a-task-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of comments successfully retrieved for the task.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="get-comments-for-a-task-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Comment](#schemacomment)]|false|none|[Schema representing a comment on a task, optionally with a mention.]|
|»» commentId|string|false|none|Unique identifier for the comment.|
|»» taskId|string|false|none|The ID of the task to comment on.|
|»» author|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|»»» userId|string|false|none|Unique identifier for the user.|
|»»» username|string|false|none|Public-facing username.|
|»»» fullName|string|false|none|Full name of the user.|
|»»» email|string|false|none|Email address of the user.|
|»» content|string|false|none|The content of the comment.|
|»» createdAt|string(date-time)|false|none|Timestamp of when the comment was created.|
|» meta|object|false|none|none|
|»» page|integer|false|none|none|
|»» totalPages|integer|false|none|none|
|»» totalItems|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-notifications">Notifications</h1>

In-app or email-based alerts

## Get all notifications

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/notifications \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/notifications HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/notifications',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/notifications',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/notifications', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/notifications', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/notifications");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/notifications", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /notifications`

Retrieve a list of notifications for the authenticated user.

<h3 id="get-all-notifications-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|page|query|integer|false|Page number of the result set.|
|limit|query|integer|false|Number of notifications per page.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "notificationId": "notif_001",
      "type": "mention",
      "message": "@winter mentioned you in a task.",
      "isRead": false,
      "createdAt": "2025-04-01T08:30:00Z",
      "mentionedUser": {
        "userId": "user_002",
        "username": "spring"
      }
    },
    {
      "notificationId": "notif_002",
      "type": "status_update",
      "message": "Task marked as completed.",
      "isRead": true,
      "createdAt": "2025-04-07T09:00:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "totalPages": 2,
    "totalNotifications": 12
  }
}
```

<h3 id="get-all-notifications-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of notifications successfully retrieved.|Inline|

<h3 id="get-all-notifications-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Notification](#schemanotification)]|false|none|[Notification returned to user based on type.]|
|»» notificationId|string|true|none|none|
|»» type|string|true|none|none|
|»» message|string|true|none|none|
|»» isRead|boolean|true|none|none|
|»» createdAt|string(date-time)|true|none|none|
|» meta|object|false|none|none|
|»» page|integer|false|none|none|
|»» totalPages|integer|false|none|none|
|»» totalNotifications|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Get a notification by its ID

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/notifications/{notificationId} \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/notifications/{notificationId} HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/notifications/{notificationId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/notifications/{notificationId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/notifications/{notificationId}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/notifications/{notificationId}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/notifications/{notificationId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/notifications/{notificationId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /notifications/{notificationId}`

Retrieve details about a specific notification by its ID.

<h3 id="get-a-notification-by-its-id-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|notificationId|path|string|true|Unique identifier of the notification.|

> Example responses

> 200 Response

```json
{
  "data": {
    "notificationId": "notif_001",
    "type": "mention",
    "message": "You were mentioned in a comment.",
    "createdAt": "2025-04-01T13:45:00Z",
    "mentionedUser": {
      "userId": "user_002",
      "username": "spring"
    }
  }
}
```

<h3 id="get-a-notification-by-its-id-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Notification details successfully retrieved.|Inline|

<h3 id="get-a-notification-by-its-id-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Notification](#schemanotification)|false|none|Notification returned to user based on type.|
|»» notificationId|string|true|none|none|
|»» type|string|true|none|none|
|»» message|string|true|none|none|
|»» isRead|boolean|true|none|none|
|»» createdAt|string(date-time)|true|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Mark a notification as read (full update)

> Code samples

```shell
# You can also use wget
curl -X PUT https://localhost/:8080/notifications/{notificationId}/read \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://localhost/:8080/notifications/{notificationId}/read HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "isRead": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/notifications/{notificationId}/read',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.put 'https://localhost/:8080/notifications/{notificationId}/read',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('https://localhost/:8080/notifications/{notificationId}/read', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PUT','https://localhost/:8080/notifications/{notificationId}/read', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/notifications/{notificationId}/read");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "https://localhost/:8080/notifications/{notificationId}/read", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /notifications/{notificationId}/read`

Fully updates the read status of a specific notification by ID.

> Body parameter

```json
{
  "isRead": true
}
```

<h3 id="mark-a-notification-as-read-(full-update)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|notificationId|path|string|true|The unique ID of the notification to update.|
|body|body|object|true|none|
|» isRead|body|boolean|true|Whether the notification has been read.|

> Example responses

> 200 Response

```json
{
  "data": {
    "notificationId": "notif_001",
    "type": "MentionNotification",
    "message": "@spring mentioned you in a comment.",
    "isRead": true,
    "createdAt": "2025-04-07T13:10:00Z"
  }
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="mark-a-notification-as-read-(full-update)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Notification read status successfully updated.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="mark-a-notification-as-read-(full-update)-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|object|false|none|none|
|»» notificationId|string|false|none|none|
|»» type|string|false|none|none|
|»» message|string|false|none|none|
|»» isRead|boolean|false|none|none|
|»» createdAt|string(date-time)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## Mark a notification as read (partial update)

> Code samples

```shell
# You can also use wget
curl -X PATCH https://localhost/:8080/notifications/{notificationId}/read \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://localhost/:8080/notifications/{notificationId}/read HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "isRead": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://localhost/:8080/notifications/{notificationId}/read',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://localhost/:8080/notifications/{notificationId}/read',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://localhost/:8080/notifications/{notificationId}/read', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('PATCH','https://localhost/:8080/notifications/{notificationId}/read', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/notifications/{notificationId}/read");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://localhost/:8080/notifications/{notificationId}/read", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /notifications/{notificationId}/read`

Update the specified notification to be marked as read.

> Body parameter

```json
{
  "isRead": true
}
```

<h3 id="mark-a-notification-as-read-(partial-update)-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|notificationId|path|string|true|The unique ID of the notification to update.|
|body|body|object|true|none|
|» isRead|body|boolean|true|none|

> Example responses

> 200 Response

```json
{
  "data": {
    "notificationId": "notif_001",
    "type": "MentionNotification",
    "message": "@spring mentioned you in a comment",
    "isRead": true,
    "createdAt": "2025-04-07T13:10:00Z"
  }
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="mark-a-notification-as-read-(partial-update)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Notification successfully marked as read.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="mark-a-notification-as-read-(partial-update)-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|object|false|none|none|
|»» notificationId|string|false|none|none|
|»» type|string|false|none|none|
|»» message|string|false|none|none|
|»» isRead|boolean|false|none|none|
|»» createdAt|string(date-time)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-history">History</h1>

Task status change logs

## Get all task status change history

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/history \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://localhost/:8080/history HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost/:8080/history',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://localhost/:8080/history',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://localhost/:8080/history', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/history', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/history");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/history", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /history`

Retrieve a list of status change events across tasks to the authenticated user.

<h3 id="get-all-task-status-change-history-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|userId|query|string|false|Filter history by user ID (optional)|
|projectId|query|string|false|Filter history by project ID (optional)|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "taskId": "task_001",
      "userId": "user_003",
      "projectId": "proj_001",
      "changedAt": "2025-04-02T14:00:00Z",
      "oldStatus": "in_progress",
      "newStatus": "completed"
    }
  ]
}
```

> 401 Response

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="get-all-task-status-change-history-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A list of all task status change records successfully retrieved.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized - JWT token missing or invalid.|[ErrorResponse](#schemaerrorresponse)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="get-all-task-status-change-history-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[History](#schemahistory)]|false|none|[Represents a task status change history record.]|
|»» taskId|string|false|none|ID of the task that was updated.|
|»» userId|string|false|none|none|
|»» projectId|string|false|none|none|
|»» changedAt|string(date-time)|false|none|Time when the status change occurred.|
|»» oldStatus|string|false|none|Previous status before the update.|
|»» newStatus|string|false|none|Updated status after the change.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oAuth2ClientCredentials ( Scopes: read )
</aside>

## Get task status change history

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/tasks/{taskId}/history \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/tasks/{taskId}/history HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/tasks/{taskId}/history',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/tasks/{taskId}/history',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/tasks/{taskId}/history', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/tasks/{taskId}/history', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/tasks/{taskId}/history");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/tasks/{taskId}/history", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /tasks/{taskId}/history`

Retrieve the history of status changes for a specific task.

<h3 id="get-task-status-change-history-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|taskId|path|string|true|Unique identifier of the task.|
|page|query|integer|false|Page number of the result set.|
|limit|query|integer|false|Number of history items per page.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "changedAt": "2025-03-30T09:00:00Z",
      "oldStatus": "pending",
      "newStatus": "in_progress"
    },
    {
      "changedAt": "2025-04-01T17:15:00Z",
      "oldStatus": "in_progress",
      "newStatus": "completed"
    }
  ],
  "meta": {
    "page": 1,
    "totalPages": 1,
    "totalHistory": 2
  }
}
```

> 404 Response

```json
{
  "error": {
    "code": 404,
    "message": "Resource not found"
  }
}
```

<h3 id="get-task-status-change-history-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of status change events for the task.|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="get-task-status-change-history-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[History](#schemahistory)]|false|none|[Represents a task status change history record.]|
|»» taskId|string|false|none|ID of the task that was updated.|
|»» userId|string|false|none|none|
|»» projectId|string|false|none|none|
|»» changedAt|string(date-time)|false|none|Time when the status change occurred.|
|»» oldStatus|string|false|none|Previous status before the update.|
|»» newStatus|string|false|none|Updated status after the change.|
|» meta|object|false|none|none|
|»» page|integer|false|none|none|
|»» totalPages|integer|false|none|none|
|»» totalHistory|integer|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-analytics">Analytics</h1>

Overview and insights of user and project activity

## Get overview analytics for the user

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost/:8080/analytics/overview \
  -H 'Accept: application/json'

```

```http
GET https://localhost/:8080/analytics/overview HTTP/1.1
Host: localhost
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('https://localhost/:8080/analytics/overview',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://localhost/:8080/analytics/overview',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://localhost/:8080/analytics/overview', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost/:8080/analytics/overview', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/analytics/overview");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost/:8080/analytics/overview", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /analytics/overview`

Retrieve an overview of key productivity metrics for the authenticated user, such as task counts and completion rate.

> Example responses

> 200 Response

```json
{
  "totalProjects": 5,
  "totalTasks": 45,
  "completedTasks": 38,
  "pendingTasks": 5,
  "overdueTasks": 2,
  "completionRate": 0.84
}
```

<h3 id="get-overview-analytics-for-the-user-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Overview analytics successfully retrieved.|Inline|

<h3 id="get-overview-analytics-for-the-user-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» totalProjects|integer|false|none|Total number of projects owned or joined by the user.|
|» totalTasks|integer|false|none|Total number of tasks across all projects.|
|» completedTasks|integer|false|none|Number of tasks marked as completed.|
|» pendingTasks|integer|false|none|Number of tasks currently pending.|
|» overdueTasks|integer|false|none|Number of tasks past their due date.|
|» completionRate|number(float)|false|none|Ratio of completed tasks to total tasks.|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="trackit-api-documentation-assistant">Assistant</h1>

ChatGPT-powered assistant for Trackit-related help

## Ask a question about using trackit

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost/:8080/assistant/ask \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://localhost/:8080/assistant/ask HTTP/1.1
Host: localhost
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "question": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost/:8080/assistant/ask',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://localhost/:8080/assistant/ask',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://localhost/:8080/assistant/ask', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost/:8080/assistant/ask', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost/:8080/assistant/ask");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost/:8080/assistant/ask", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /assistant/ask`

Send a question to the Trackit assistant powered by ChatGPT to receive guidance. Accepts natural language queries such as "How do I assign a task?" or "Show me overdue tasks.".

> Body parameter

```json
{
  "question": "string"
}
```

<h3 id="ask-a-question-about-using-trackit-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» question|body|string|true|A natural language question about how to use Trackit features.|

> Example responses

> 200 Response

```json
{
  "data": {
    "answer": "To assign a task to a team member, go to the task detail view and use the assignee dropdown menu to select a user."
  }
}
```

> 400 Response

```json
{
  "error": {
    "code": 400,
    "message": "Missing required field 'title'"
  }
}
```

<h3 id="ask-a-question-about-using-trackit-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ChatGPT-powered assistant response.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request input is invalid or malformed.|[Error](#schemaerror)|

<h3 id="ask-a-question-about-using-trackit-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|object|false|none|none|
|»» answer|string|false|none|The assistant's generated response.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth, ApiKeyAuth, oAuth2AuthCode, oAuth2ClientCredentials
</aside>

# Schemas

<h2 id="tocS_Registration">Registration</h2>
<!-- backwards compatibility -->
<a id="schemaregistration"></a>
<a id="schema_Registration"></a>
<a id="tocSregistration"></a>
<a id="tocsregistration"></a>

```json
{
  "email": "summer.lee@example.com",
  "password": "passwordforsummer123",
  "fullName": "Summer Lee"
}

```

Schema for registering a new user.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string|false|none|Email address of the user.|
|password|string|false|none|Password for the user account.|
|fullName|string|false|none|Full name of the user.|

<h2 id="tocS_User">User</h2>
<!-- backwards compatibility -->
<a id="schemauser"></a>
<a id="schema_User"></a>
<a id="tocSuser"></a>
<a id="tocsuser"></a>

```json
{
  "userId": "user_001",
  "username": "winter",
  "fullName": "Winter Doe",
  "email": "winter.doe@example.com"
}

```

Represents a user of the Trackit system.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|userId|string|false|none|Unique identifier for the user.|
|username|string|false|none|Public-facing username.|
|fullName|string|false|none|Full name of the user.|
|email|string|false|none|Email address of the user.|

<h2 id="tocS_Project">Project</h2>
<!-- backwards compatibility -->
<a id="schemaproject"></a>
<a id="schema_Project"></a>
<a id="tocSproject"></a>
<a id="tocsproject"></a>

```json
{
  "projectId": "proj_001",
  "title": "Trackit Redesign",
  "description": "UI/UX overhaul of the Trackit platform.",
  "createdAt": "2025-03-01T10:00:00Z",
  "updatedAt": "2025-03-03T15:30:00Z"
}

```

Represents a project that contains tasks.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|projectId|string|false|none|Unique identifier of the project.|
|title|string|false|none|Title of the project.|
|description|string|false|none|Detailed description of the project.|
|createdAt|string(date-time)|false|none|Timestamp when the project was created.|
|updatedAt|string(date-time)|false|none|Timestamp when the project was last updated.|

<h2 id="tocS_Task">Task</h2>
<!-- backwards compatibility -->
<a id="schematask"></a>
<a id="schema_Task"></a>
<a id="tocStask"></a>
<a id="tocstask"></a>

```json
{
  "taskId": "task_001",
  "title": "Design homepage",
  "description": "Create layout wireframes for the homepage",
  "status": "in_progress",
  "assignee": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "dueDate": "2025-04-10"
}

```

A task assigned to a user within a project.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|taskId|string|false|none|Unique identifier for the task.|
|title|string|false|none|Title of the task.|
|description|string|false|none|Detailed description of the task.|
|status|string|false|none|Current status of the task.|
|assignee|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|dueDate|string(date)|false|none|Due date of the task.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<h2 id="tocS_PaginationMeta">PaginationMeta</h2>
<!-- backwards compatibility -->
<a id="schemapaginationmeta"></a>
<a id="schema_PaginationMeta"></a>
<a id="tocSpaginationmeta"></a>
<a id="tocspaginationmeta"></a>

```json
{
  "totalItems": 48,
  "page": 1,
  "limit": 0,
  "totalPages": 5
}

```

Pagination metadata for paginated responses.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|totalItems|integer|false|none|Total number of items available|
|page|integer|false|none|Current page number|
|limit|integer|false|none|Number of items per page|
|totalPages|integer|false|none|Total number of available pages|

<h2 id="tocS_Comment">Comment</h2>
<!-- backwards compatibility -->
<a id="schemacomment"></a>
<a id="schema_Comment"></a>
<a id="tocScomment"></a>
<a id="tocscomment"></a>

```json
{
  "commentId": "cmt_001",
  "taskId": "task_001",
  "author": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  },
  "content": "@john please review the UI update.",
  "createdAt": "2025-04-02T09:20:00Z"
}

```

Schema representing a comment on a task, optionally with a mention.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|commentId|string|false|none|Unique identifier for the comment.|
|taskId|string|false|none|The ID of the task to comment on.|
|author|[User](#schemauser)|false|none|Represents a user of the Trackit system.|
|content|string|false|none|The content of the comment.|
|createdAt|string(date-time)|false|none|Timestamp of when the comment was created.|

<h2 id="tocS_Notification">Notification</h2>
<!-- backwards compatibility -->
<a id="schemanotification"></a>
<a id="schema_Notification"></a>
<a id="tocSnotification"></a>
<a id="tocsnotification"></a>

```json
{
  "notificationId": "string",
  "type": "string",
  "message": "string",
  "isRead": true,
  "createdAt": "2019-08-24T14:15:22Z"
}

```

Notification returned to user based on type.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|notificationId|string|true|none|none|
|type|string|true|none|none|
|message|string|true|none|none|
|isRead|boolean|true|none|none|
|createdAt|string(date-time)|true|none|none|

<h2 id="tocS_MentionNotification">MentionNotification</h2>
<!-- backwards compatibility -->
<a id="schemamentionnotification"></a>
<a id="schema_MentionNotification"></a>
<a id="tocSmentionnotification"></a>
<a id="tocsmentionnotification"></a>

```json
{
  "notificationId": "string",
  "type": "string",
  "message": "string",
  "isRead": true,
  "createdAt": "2019-08-24T14:15:22Z",
  "mentionedUser": {
    "userId": "user_001",
    "username": "winter",
    "fullName": "Winter Doe",
    "email": "winter.doe@example.com"
  }
}

```

A notification mentioning other user using @syntax.

### Properties

allOf - discriminator: Notification.type

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Notification](#schemanotification)|false|none|Notification returned to user based on type.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» mentionedUser|[User](#schemauser)|false|none|Represents a user of the Trackit system.|

<h2 id="tocS_DueSoonNotification">DueSoonNotification</h2>
<!-- backwards compatibility -->
<a id="schemaduesoonnotification"></a>
<a id="schema_DueSoonNotification"></a>
<a id="tocSduesoonnotification"></a>
<a id="tocsduesoonnotification"></a>

```json
{
  "notificationId": "string",
  "type": "string",
  "message": "string",
  "isRead": true,
  "createdAt": "2019-08-24T14:15:22Z",
  "dueDate": "2019-08-24"
}

```

### Properties

allOf - discriminator: Notification.type

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Notification](#schemanotification)|false|none|Notification returned to user based on type.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» dueDate|string(date)|false|none|none|

<h2 id="tocS_CommentNotification">CommentNotification</h2>
<!-- backwards compatibility -->
<a id="schemacommentnotification"></a>
<a id="schema_CommentNotification"></a>
<a id="tocScommentnotification"></a>
<a id="tocscommentnotification"></a>

```json
{
  "notificationId": "string",
  "type": "string",
  "message": "string",
  "isRead": true,
  "createdAt": "2019-08-24T14:15:22Z",
  "commentId": "string"
}

```

### Properties

allOf - discriminator: Notification.type

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Notification](#schemanotification)|false|none|Notification returned to user based on type.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» commentId|string|false|none|none|

<h2 id="tocS_StatusUpdateNotification">StatusUpdateNotification</h2>
<!-- backwards compatibility -->
<a id="schemastatusupdatenotification"></a>
<a id="schema_StatusUpdateNotification"></a>
<a id="tocSstatusupdatenotification"></a>
<a id="tocsstatusupdatenotification"></a>

```json
{
  "notificationId": "string",
  "type": "string",
  "message": "string",
  "isRead": true,
  "createdAt": "2019-08-24T14:15:22Z",
  "oldStatus": "string",
  "newStatus": "string"
}

```

### Properties

allOf - discriminator: Notification.type

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[Notification](#schemanotification)|false|none|Notification returned to user based on type.|

and

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» oldStatus|string|false|none|none|
|» newStatus|string|false|none|none|

<h2 id="tocS_History">History</h2>
<!-- backwards compatibility -->
<a id="schemahistory"></a>
<a id="schema_History"></a>
<a id="tocShistory"></a>
<a id="tocshistory"></a>

```json
{
  "taskId": "task_001",
  "userId": "user_001",
  "projectId": "proj_001",
  "changedAt": "2025-04-01T17:15:00Z",
  "oldStatus": "in_progress",
  "newStatus": "completed"
}

```

Represents a task status change history record.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|taskId|string|false|none|ID of the task that was updated.|
|userId|string|false|none|none|
|projectId|string|false|none|none|
|changedAt|string(date-time)|false|none|Time when the status change occurred.|
|oldStatus|string|false|none|Previous status before the update.|
|newStatus|string|false|none|Updated status after the change.|

<h2 id="tocS_Error">Error</h2>
<!-- backwards compatibility -->
<a id="schemaerror"></a>
<a id="schema_Error"></a>
<a id="tocSerror"></a>
<a id="tocserror"></a>

```json
{
  "error": {
    "code": 0,
    "message": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|error|object|false|none|none|
|» code|integer|false|none|none|
|» message|string|false|none|none|

<h2 id="tocS_ErrorResponse">ErrorResponse</h2>
<!-- backwards compatibility -->
<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

```json
{
  "status": 401,
  "message": "Authentication token is missing or invalid."
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status|integer|false|none|none|
|message|string|false|none|none|

