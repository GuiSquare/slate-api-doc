---
title: Falcon Alpha Phoenix
language_tabs:
  - bash: Shell
  - http: HTTP
  - ruby: Ruby
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - go: Go
  - java: Java
toc_footers:
  - '<a href="https://www.paxfamilia.com/">Find out more about PaxFamilia</a>'
includes: []
search: true
highlight_theme: mono blue
headingLevel: 2

---

<h1 id="falcon-alpha-phoenix">Falcon Alpha Phoenix v1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the first version of the PaxFamilia 'public' API. You can find out more about **PaxFamilia** at our [website](https://www.paxfamilia.com/). **(W.I.P.)**

Base URLs:

* <a href="https://[your-subdomain].paxfamilia.com/api/v1">https://[your-subdomain].paxfamilia.com/api/v1</a>

<a href="https://www.paxfamilia.com/hubfs/Conditions%20g%C3%A9n%C3%A9rales/CGU_PaxFamilia_B2B_V3_clean%2026112018.pdf?hsLang=fr-fr">Terms of service</a>
Email: <a href="mailto:msousa@paxfamilia.com">Support</a>
License: <a href="http://www.license.com">License Name</a>

# Authentication

* API Key (ApiKey)
    - Parameter Name: **X-Api-Key**, in: header. 1) After activating the Public API for your company's subdomain ask your company admin to generate an
   Api-Key at ".com/management/{your-company-comercial-name}/user_profile" and keep it safely.
   ATTENTION - this Api-Key will be hidden after this and it is the responsibility of you company to
   keep it safe, losing it will incur an identity scrutinization process to get a new one.
   NOTE - PaxFamilia reserves the right to invalidate this Api-key in case of gross missuse or any
   kind of suspicious activity / server overload
2) Use the Authentication (/users/login) resource to generate a JWT with email + password + api-key in the
   body params. The email and password must be of a company employee account to which the admin_right
   :api_user has been given, to do so the company admin must edit that employee's account. This will
   return a JWT in the response header and body which is valid for 2hrs.

* API Key (JsonWebToken)
    - Parameter Name: **Authorization**, in: header. 2) Use the Authentication (/users/login) resource to generate a JWT with email + password + api-key in the
   body params. The email and password must be of a company employee account to which the admin_right
   :api_user has been given, to do so the company admin must edit that employee's account. This will
   return a JWT in the response header and body which is valid for 2hrs.
3) Every call to the remaining resources in this API must be done with that JWT in the
   'Authorization' header and the Api-Key in the 'X-Api-Key' header.

<h1 id="falcon-alpha-phoenix-api-logs">Api Logs</h1>

## Retrieves the list of api logs

<a id="opIdgetApiLogs"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/api-logs HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/api-logs',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/api-logs',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/api-logs',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/api-logs", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/api-logs");
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

`GET /api-logs`

<h3 id="retrieves-the-list-of-api-logs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|page object query with number and size in the format page%5Bnumber%5D=1&page%5Bsize%5D=50 which would be page[number]=1&page[size]=50 before encoding the square brackets|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "a7b9cv76eb",
      "type": "apiLog",
      "attributes": {
        "id": "a7b9cv76eb",
        "companyMembershipId": "uyd86tb",
        "success": false,
        "status": "not_found",
        "description": "Invalid ID: EstateAsset 12345",
        "groupPublicId": "suygd97",
        "resourceId": "86757h",
        "controller": "estate_liabilities",
        "action": "create",
        "requestMethod": "POST"
      }
    }
  ],
  "links": {
    "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="retrieves-the-list-of-api-logs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Api logs found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<h3 id="retrieves-the-list-of-api-logs-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[ApiLog](#schemaapilog)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-lifecycle">Lifecycle</h1>

## Creates one Group with its DummyUsers and current spouse GroupMembership

<a id="opIdaddDraft"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/draft HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/draft',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/draft',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": {
    "type": "draft",
    "attributes": {
      "dummyUsers": [
        {
          "id": "family_head_id_123",
          "firstName": "Luc",
          "lastName": "Beson",
          "gender": "M",
          "birthday": "1960-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        },
        {
          "id": "current_spouse_id_123",
          "firstName": "Madeleine",
          "lastName": "Beson",
          "gender": "F",
          "birthday": "1970-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        }
      ],
      "group": {
        "internalName": "Lucas Niets Beson",
        "id": "group_id_123",
        "clientId": "family_head_id_123",
        "companyAdvisorId": "987gfr"
      },
      "groupMembership": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "currentSpouseId": "family_head_id_123",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "current_spouse_id_123"
      }
    }
  }
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/draft',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/draft", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/draft");
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

`POST /groups/draft`

> Body parameter

```json
{
  "data": {
    "type": "draft",
    "attributes": {
      "dummyUsers": [
        {
          "id": "family_head_id_123",
          "firstName": "Luc",
          "lastName": "Beson",
          "gender": "M",
          "birthday": "1960-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        },
        {
          "id": "current_spouse_id_123",
          "firstName": "Madeleine",
          "lastName": "Beson",
          "gender": "F",
          "birthday": "1970-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        }
      ],
      "group": {
        "internalName": "Lucas Niets Beson",
        "id": "group_id_123",
        "clientId": "family_head_id_123",
        "companyAdvisorId": "987gfr"
      },
      "groupMembership": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "currentSpouseId": "family_head_id_123",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "current_spouse_id_123"
      }
    }
  }
}
```

<h3 id="creates-one-group-with-its-dummyusers-and-current-spouse-groupmembership-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|

> Example responses

> 201 Response

```json
{
  "data": {
    "type": "draft",
    "attributes": {
      "dummyUsers": [
        {
          "id": "family_head_id_123",
          "firstName": "Luc",
          "lastName": "Beson",
          "gender": "M",
          "birthday": "1960-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        },
        {
          "id": "current_spouse_id_123",
          "firstName": "Madeleine",
          "lastName": "Beson",
          "gender": "F",
          "birthday": "1970-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        }
      ],
      "group": {
        "internalName": "Lucas Niets Beson",
        "id": "group_id_123",
        "clientId": "family_head_id_123",
        "companyAdvisorId": "987gfr"
      },
      "groupMembership": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "currentSpouseId": "family_head_id_123",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "current_spouse_id_123"
      }
    }
  }
}
```

<h3 id="creates-one-group-with-its-dummyusers-and-current-spouse-groupmembership-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Draft created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-group-with-its-dummyusers-and-current-spouse-groupmembership-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Activates Group

<a id="opIdactivateGroup"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate',
{
  method: 'PATCH',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/activate");
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

`PATCH /groups/{id}/activate`

<h3 id="activates-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 201 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "internalName": "Lucas Niets",
      "id": "acbdj6472",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="activates-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Group Activated|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="activates-group-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Suspends Group

<a id="opIdsuspendGroup"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": {
    "id": "12345h",
    "type": "group",
    "attributes": {
      "id": "12345h",
      "cause": "divorce"
    }
  }
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/suspend");
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

`PATCH /groups/{id}/suspend`

> Body parameter

```json
{
  "data": {
    "id": "12345h",
    "type": "group",
    "attributes": {
      "id": "12345h",
      "cause": "divorce"
    }
  }
}
```

<h3 id="suspends-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|
|body|body|object|true|none|
|» data|body|object|true|none|
|»» id|body|string|true|Internal ID of the group|
|»» type|body|string|true|none|
|»» attributes|body|object|true|none|
|»»» id|body|string|true|Internal ID of the group|
|»»» cause|body|string|true|cause of the suspension|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»» type|group|
|»»» cause|divorce|
|»»» cause|death|

> Example responses

> 201 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "internalName": "Lucas Niets",
      "id": "acbdj6472",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="suspends-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Group Suspended|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="suspends-group-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Marks Group for Deletion

<a id="opIdmarkGroupForDeletion"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": {
    "id": "12345h",
    "type": "group",
    "attributes": {
      "id": "12345h",
      "days": 30
    }
  }
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/mark_for_deletion");
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

`PATCH /groups/{id}/mark_for_deletion`

> Body parameter

```json
{
  "data": {
    "id": "12345h",
    "type": "group",
    "attributes": {
      "id": "12345h",
      "days": 30
    }
  }
}
```

<h3 id="marks-group-for-deletion-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|
|body|body|object|true|none|
|» data|body|object|true|none|
|»» id|body|string|true|Internal ID of the group|
|»» type|body|string|true|none|
|»» attributes|body|object|true|none|
|»»» id|body|string|true|Internal ID of the group|
|»»» days|body|number|false|days until deletion|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»» type|group|

> Example responses

> 201 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "internalName": "Lucas Niets",
      "id": "acbdj6472",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="marks-group-for-deletion-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Group Marked for Deletion|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="marks-group-for-deletion-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-asset-ownerships">Asset Ownerships</h1>

## Resets one or more Asset Ownerships

<a id="opIdresetAssetOwnerships"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships HTTP/1.1

Content-Type: application/json
Accept: */*

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => '*/*',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "assetOwnerships": [
          {
            "type": "assetOwnership",
            "attributes": {
              "ownerId": "12345abcd",
              "percentage": 2,
              "ownershipType": "fp"
            }
          }
        ]
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"*/*"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/asset-ownerships");
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

`POST /groups/{groupId}/asset-ownerships`

> Body parameter

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "assetOwnerships": [
          {
            "type": "assetOwnership",
            "attributes": {
              "ownerId": "12345abcd",
              "percentage": 2,
              "ownershipType": "fp"
            }
          }
        ]
      }
    }
  ]
}
```

<h3 id="resets-one-or-more-asset-ownerships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[object]|true|none|
|»» id|body|string|true|Internal ID of the estateAsset|
|»» type|body|string|true|none|
|»» attributes|body|object|true|none|
|»»» assetOwnerships|body|[[AssetOwnership](#schemaassetownership)]|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»» type|estateAsset|

> Example responses

> 201 Response

<h3 id="resets-one-or-more-asset-ownerships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Asset Ownerships reset|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="resets-one-or-more-asset-ownerships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[object]|true|none|none|
|»» id|string|true|none|Internal ID of the estateAsset|
|»» type|string|true|none|none|
|»» attributes|object|true|none|none|
|»»» assetOwnerships|[[AssetOwnership](#schemaassetownership)]|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-group-access">Company Group Access</h1>

## Creates one or more Company Group Access

<a id="opIdaddCompanyGroupAccesses"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "groupID567",
      "type": "group",
      "attributes": {
        "id": "groupID567",
        "companyAdvisorId": "advisorID345",
        "authorizedCompanyUserIds": [
          "employeeID743",
          "employeeID744",
          "employeeID745",
          "employeeID746",
          "employeeID747"
        ]
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/confidentiality-rules");
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

`PATCH /groups/confidentiality-rules`

> Body parameter

```json
{
  "data": [
    {
      "id": "groupID567",
      "type": "group",
      "attributes": {
        "id": "groupID567",
        "companyAdvisorId": "advisorID345",
        "authorizedCompanyUserIds": [
          "employeeID743",
          "employeeID744",
          "employeeID745",
          "employeeID746",
          "employeeID747"
        ]
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-group-access-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[CompanyGroupAccess](#schemacompanygroupaccess)]|true|none|

> Example responses

> 202 Response

```json
{
  "data": [
    {
      "id": "groupID567",
      "type": "group",
      "attributes": {
        "id": "groupID567",
        "companyAdvisorId": "advisorID345",
        "authorizedCompanyUserIds": [
          "employeeID743",
          "employeeID744",
          "employeeID745",
          "employeeID746",
          "employeeID747"
        ]
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-group-access-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Company Group Accesses updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-company-group-access-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyGroupAccess](#schemacompanygroupaccess)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-memberships">Company Memberships</h1>

## Creates one or more company memberships

<a id="opIdaddCompanyMemberships"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/company-memberships HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "123abc123",
      "type": "companyMembership",
      "attributes": {
        "companyUnitId": "12345abcd",
        "memberRight": "read",
        "id": "123abc123",
        "email": "person_abc@example.com",
        "firstName": "Freddy",
        "lastName": "Luke",
        "gender": "M",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "BE",
        "zipcode": "1040",
        "locale": "fr"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/company-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-memberships");
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

`POST /company-memberships`

> Body parameter

```json
{
  "data": [
    {
      "id": "123abc123",
      "type": "companyMembership",
      "attributes": {
        "companyUnitId": "12345abcd",
        "memberRight": "read",
        "id": "123abc123",
        "email": "person_abc@example.com",
        "firstName": "Freddy",
        "lastName": "Luke",
        "gender": "M",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "BE",
        "zipcode": "1040",
        "locale": "fr"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-memberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[CompanyMembership](#schemacompanymembership)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "123abc123",
      "type": "companyMembership",
      "attributes": {
        "companyUnitId": "12345abcd",
        "memberRight": "read",
        "id": "123abc123",
        "email": "person_abc@example.com",
        "firstName": "Freddy",
        "lastName": "Luke",
        "gender": "M",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "BE",
        "zipcode": "1040",
        "locale": "fr"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-memberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Company memberships created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-company-memberships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyMembership](#schemacompanymembership)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Retrieves the list of company memberships

<a id="opIdgetCompanyMemberships"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/company-memberships HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-memberships',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/company-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-memberships");
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

`GET /company-memberships`

<h3 id="retrieves-the-list-of-company-memberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|page object query with number and size in the format page%5Bnumber%5D=1&page%5Bsize%5D=50 which would be page[number]=1&page[size]=50 before encoding the square brackets|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "123abc123",
      "type": "companyMembership",
      "attributes": {
        "companyUnitId": "12345abcd",
        "memberRight": "read",
        "id": "123abc123",
        "email": "person_abc@example.com",
        "firstName": "Freddy",
        "lastName": "Luke",
        "gender": "M",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "BE",
        "zipcode": "1040",
        "locale": "fr"
      }
    }
  ],
  "links": {
    "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="retrieves-the-list-of-company-memberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Company memberships found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<h3 id="retrieves-the-list-of-company-memberships-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyMembership](#schemacompanymembership)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Updates a company membership

<a id="opIdfindCompanyMembershipById"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id} HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": {
    "id": "123abc123",
    "type": "companyMembership",
    "attributes": {
      "companyUnitId": "12345abcd",
      "memberRight": "read",
      "id": "123abc123",
      "email": "person_abc@example.com",
      "firstName": "Freddy",
      "lastName": "Luke",
      "gender": "M",
      "birthday": "1970-02-20",
      "nationality": "BE",
      "countryCode": "BE",
      "zipcode": "1040",
      "locale": "fr"
    }
  }
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}");
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

`PATCH /company-memberships/{id}`

> Body parameter

```json
{
  "data": {
    "id": "123abc123",
    "type": "companyMembership",
    "attributes": {
      "companyUnitId": "12345abcd",
      "memberRight": "read",
      "id": "123abc123",
      "email": "person_abc@example.com",
      "firstName": "Freddy",
      "lastName": "Luke",
      "gender": "M",
      "birthday": "1970-02-20",
      "nationality": "BE",
      "countryCode": "BE",
      "zipcode": "1040",
      "locale": "fr"
    }
  }
}
```

<h3 id="updates-a-company-membership-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|
|body|body|object|false|none|

> Example responses

> 202 Response

```json
{
  "data": {
    "id": "123abc123",
    "type": "companyMembership",
    "attributes": {
      "companyUnitId": "12345abcd",
      "memberRight": "read",
      "id": "123abc123",
      "email": "person_abc@example.com",
      "firstName": "Freddy",
      "lastName": "Luke",
      "gender": "M",
      "birthday": "1970-02-20",
      "nationality": "BE",
      "countryCode": "BE",
      "zipcode": "1040",
      "locale": "fr"
    }
  }
}
```

<h3 id="updates-a-company-membership-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|not valid company membership attributes|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="updates-a-company-membership-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Destroys a company membership

<a id="opIddeleteCompanyMembership"></a>

> Code samples

```http
DELETE https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id} HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.delete 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-memberships/{id}");
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

`DELETE /company-memberships/{id}`

<h3 id="destroys-a-company-membership-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "data": {
    "id": "123abc123",
    "type": "companyMembership",
    "attributes": {
      "companyUnitId": "12345abcd",
      "memberRight": "read",
      "id": "123abc123",
      "email": "person_abc@example.com",
      "firstName": "Freddy",
      "lastName": "Luke",
      "gender": "M",
      "birthday": "1970-02-20",
      "nationality": "BE",
      "countryCode": "BE",
      "zipcode": "1040",
      "locale": "fr"
    }
  }
}
```

<h3 id="destroys-a-company-membership-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|company membership deleted|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="destroys-a-company-membership-responseschema">Response Schema</h3>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-units">Company Units</h1>

## Creates one or more company units

<a id="opIdaddCompanyUnits"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/company-units HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/company-units',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-units',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "321dsa",
      "type": "companyUnit",
      "attributes": {
        "name": "Procurement Department",
        "address": "Rue Lac Lemanid",
        "countryCode": "BE",
        "zipcode": "1050",
        "locale": "fr",
        "parentId": "123asd",
        "id": "321dsa"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-units',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/company-units", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-units");
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

`POST /company-units`

> Body parameter

```json
{
  "data": [
    {
      "id": "321dsa",
      "type": "companyUnit",
      "attributes": {
        "name": "Procurement Department",
        "address": "Rue Lac Lemanid",
        "countryCode": "BE",
        "zipcode": "1050",
        "locale": "fr",
        "parentId": "123asd",
        "id": "321dsa"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-units-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[CompanyUnit](#schemacompanyunit)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "321dsa",
      "type": "companyUnit",
      "attributes": {
        "name": "Procurement Department",
        "address": "Rue Lac Lemanid",
        "countryCode": "BE",
        "zipcode": "1050",
        "locale": "fr",
        "parentId": "123asd",
        "id": "321dsa"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-company-units-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Company units created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-company-units-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyUnit](#schemacompanyunit)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Retrieves the list of company units

<a id="opIdgetCompanyUnits"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/company-units HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/company-units',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/company-units',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/company-units',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/company-units", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/company-units");
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

`GET /company-units`

<h3 id="retrieves-the-list-of-company-units-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|page object query with number and size in the format page%5Bnumber%5D=1&page%5Bsize%5D=50 which would be page[number]=1&page[size]=50 before encoding the square brackets|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "321dsa",
      "type": "companyUnit",
      "attributes": {
        "name": "Procurement Department",
        "address": "Rue Lac Lemanid",
        "countryCode": "BE",
        "zipcode": "1050",
        "locale": "fr",
        "parentId": "123asd",
        "id": "321dsa"
      }
    }
  ],
  "links": {
    "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="retrieves-the-list-of-company-units-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Company units found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<h3 id="retrieves-the-list-of-company-units-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyUnit](#schemacompanyunit)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-donations">Donations</h1>

## Creates one or more Donations

<a id="opIdaddDonations"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "id987fd",
      "type": "donation",
      "attributes": {
        "name": "Annual Donation",
        "transactionDate": "1970-02-20",
        "amount": 5000,
        "donationType": "movable",
        "ownershipType": "fp",
        "annuityClause": false,
        "annuityPc": 0,
        "registered": false,
        "id": "id987fd",
        "donorIds": [
          "123abc",
          "0",
          "123abcd"
        ],
        "doneeIds": [
          "123abc2",
          "123abcd1"
        ]
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/donations");
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

`POST /groups/{groupId}/donations`

> Body parameter

```json
{
  "data": [
    {
      "id": "id987fd",
      "type": "donation",
      "attributes": {
        "name": "Annual Donation",
        "transactionDate": "1970-02-20",
        "amount": 5000,
        "donationType": "movable",
        "ownershipType": "fp",
        "annuityClause": false,
        "annuityPc": 0,
        "registered": false,
        "id": "id987fd",
        "donorIds": [
          "123abc",
          "0",
          "123abcd"
        ],
        "doneeIds": [
          "123abc2",
          "123abcd1"
        ]
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-donations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[[Donation](#schemadonation)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "id987fd",
      "type": "donation",
      "attributes": {
        "name": "Annual Donation",
        "transactionDate": "1970-02-20",
        "amount": 5000,
        "donationType": "movable",
        "ownershipType": "fp",
        "annuityClause": false,
        "annuityPc": 0,
        "registered": false,
        "id": "id987fd",
        "donorIds": [
          "123abc",
          "0",
          "123abcd"
        ],
        "doneeIds": [
          "123abc2",
          "123abcd1"
        ]
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-donations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Donations created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-donations-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Donation](#schemadonation)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-dummy-users">Dummy Users</h1>

## Creates one or more dummy users

<a id="opIdaddDummyUsers"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/dummy-users HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "123abcde",
      "type": "dummyUser",
      "attributes": {
        "id": "123abcde",
        "firstName": "Luc",
        "lastName": "Beson",
        "gender": "F",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/dummy-users", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/dummy-users");
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

`POST /dummy-users`

> Body parameter

```json
{
  "data": [
    {
      "id": "123abcde",
      "type": "dummyUser",
      "attributes": {
        "id": "123abcde",
        "firstName": "Luc",
        "lastName": "Beson",
        "gender": "F",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-dummy-users-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[DummyUser](#schemadummyuser)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "123abcde",
      "type": "dummyUser",
      "attributes": {
        "id": "123abcde",
        "firstName": "Luc",
        "lastName": "Beson",
        "gender": "F",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-dummy-users-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Dummy users created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-dummy-users-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[DummyUser](#schemadummyuser)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Retrieves the list of dummy users

<a id="opIdgetDummyUsers"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/dummy-users HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/dummy-users',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/dummy-users", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/dummy-users");
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

`GET /dummy-users`

<h3 id="retrieves-the-list-of-dummy-users-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|page object query with number and size in the format page%5Bnumber%5D=1&page%5Bsize%5D=50 which would be page[number]=1&page[size]=50 before encoding the square brackets|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "123abcde",
      "type": "dummyUser",
      "attributes": {
        "id": "123abcde",
        "firstName": "Luc",
        "lastName": "Beson",
        "gender": "F",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      }
    }
  ],
  "links": {
    "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="retrieves-the-list-of-dummy-users-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Dummy users found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<h3 id="retrieves-the-list-of-dummy-users-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[DummyUser](#schemadummyuser)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estate-assets">Estate Assets</h1>

## Creates one or more Estate Assets

<a id="opIdaddEstateAssets"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "id": "123dfer",
        "currentValue": 2344
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-assets");
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

`POST /groups/{groupId}/estate-assets`

> Body parameter

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "id": "123dfer",
        "currentValue": 2344
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-estate-assets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[allOf]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "id": "123dfer",
        "currentValue": 2344
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-estate-assets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Estate Assets created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-estate-assets-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[allOf]|true|none|none|

*allOf - discriminator: type*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estate-liabilities">Estate Liabilities</h1>

## Creates one or more Estate Liabilities

<a id="opIdaddEstateLiabilities"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "id": "123dfer",
        "rate": 2
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/estate-liabilities");
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

`POST /groups/{groupId}/estate-liabilities`

> Body parameter

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset",
      "attributes": {
        "id": "123dfer",
        "rate": 2
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-estate-liabilities-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[allOf]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "abcd1234",
      "type": "estateLiability",
      "attributes": {
        "id": "abcd1234",
        "name": "Birthday gift to my son's 30th",
        "countryCode": "BE",
        "currency": "EUR",
        "initialDate": "1970-02-20",
        "initialAmount": 5001,
        "bankName": "Grifindor Vault",
        "apiOnly": false,
        "liabilityType": "bank_loan",
        "repaymentType": "constant_periodicity",
        "periodicity": "monthly",
        "periodsDuration": 1,
        "rate": 0,
        "sameOwnershipAsAsset": true,
        "borrowers": [
          "0",
          "12345mn",
          "0"
        ],
        "lenders": [
          "12345mnoo0"
        ],
        "linkedToAsset": false,
        "rateType": "fixed",
        "balanceInsurance": false,
        "balanceInsurancePc": 0,
        "swiftCode": "GEBABEBB00",
        "guarantees": [
          {
            "amount": 23000,
            "guaranteeType": "other_guarantee",
            "guarantorableId": "estate_asset_id_653",
            "guarantorableType": "EstateAsset"
          },
          {
            "amount": 73810,
            "guaranteeType": "other_guarantee",
            "guarantorableId": "dummy_user_id_456",
            "guarantorableType": "GroupMembership"
          }
        ]
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-estate-liabilities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Estate Liabilities created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-estate-liabilities-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[EstateLiabilityWithGuarantees](#schemaestateliabilitywithguarantees)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-group-memberships">Group Memberships</h1>

## Creates one or more Group Memberships

<a id="opIdaddGroupMemberships"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "Yu1234ac"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/group-memberships");
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

`POST /groups/{groupId}/group-memberships`

> Body parameter

```json
{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "Yu1234ac"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-group-memberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[[GroupMembership](#schemagroupmembership)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false,
        "dummyUserId": "Yu1234ac"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-group-memberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Group Memberships created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-group-memberships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[GroupMembership](#schemagroupmembership)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-groups">Groups</h1>

## Creates one or more Groups

<a id="opIdaddGroups"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "internalName": "Lucas Niets",
        "id": "acbdj6472",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups");
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

`POST /groups`

> Body parameter

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "internalName": "Lucas Niets",
        "id": "acbdj6472",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-groups-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[Group](#schemagroup)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "internalName": "Lucas Niets",
        "id": "acbdj6472",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-groups-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Groups created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-groups-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Group](#schemagroup)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Retrieves the list of Groups

<a id="opIdgetGroups"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/groups HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/groups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups");
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

`GET /groups`

<h3 id="retrieves-the-list-of-groups-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|page object query with number and size in the format page%5Bnumber%5D=1&page%5Bsize%5D=50 which would be page[number]=1&page[size]=50 before encoding the square brackets|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "internalName": "Lucas Niets",
        "id": "acbdj6472",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ],
  "links": {
    "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="retrieves-the-list-of-groups-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Groups found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<h3 id="retrieves-the-list-of-groups-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Group](#schemagroup)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Deletes the Group ::WARNING:: will be deleted in favour of lifecycle/mark_for_deletion

<a id="opIddeleteGroup"></a>

> Code samples

```http
DELETE https://[your-subdomain].paxfamilia.com/api/v1/groups/{id} HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.delete 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}");
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

`DELETE /groups/{id}`

<h3 id="deletes-the-group-::warning::-will-be-deleted-in-favour-of-lifecycle/mark_for_deletion-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Group ID of the group to be deleted|
|days|query|number|false|deactivate the group and set the days until the group should be deleted|

> Example responses

> 401 Response

```json
{
  "errors": [
    {
      "status": "unauthorized",
      "detail": "Invalid credentials"
    }
  ]
}
```

<h3 id="deletes-the-group-::warning::-will-be-deleted-in-favour-of-lifecycle/mark_for_deletion-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Group deleted|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Get the Estate of one Group

<a id="opIdgetGroupEstate"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/estate");
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

`GET /groups/{id}/estate`

Retrieve the lists of Estate Assets, Estate Liabilities and Insurances of a Group

<h3 id="get-the-estate-of-one-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Group ID of the group|

> Example responses

> 200 Response

```json
{
  "data": {
    "id": "string",
    "type": "group",
    "attributes": {
      "estateAssets": [
        {
          "id": "345abcd",
          "category": "account",
          "apiOnly": true,
          "name": "Home expense account",
          "countryCode": "BE",
          "zipcode": "1050",
          "currentValue": 3234,
          "currency": "EUR",
          "defaultOwnershipType": "owner"
        }
      ],
      "estateLiabilities": [
        {
          "id": "string",
          "apiOnly": false,
          "name": "string",
          "liabilityType": "bank_loan",
          "linkedToAsset": false,
          "estateAssetId": "string",
          "swiftCode": "string",
          "bankName": "string",
          "countryCode": "BE",
          "initialAmount": 0,
          "initialDate": "string",
          "currency": "EUR",
          "repaymentType": "constant_periodicity",
          "periodicity": "monthly",
          "periodsDuration": 1,
          "rate": 0,
          "rateType": "fixed",
          "sameOwnershipAsAsset": true,
          "borrowers": [
            "string"
          ],
          "lenders": [
            "string"
          ],
          "balanceInsurance": false,
          "balanceInsurancePc": 0,
          "guarantees": [
            {
              "amount": 0,
              "guaranteeType": "other_guarantee",
              "guarantorableId": "string",
              "guarantorableType": "EstateAsset"
            }
          ]
        }
      ],
      "insurances": [
        {
          "id": "string",
          "apiOnly": false,
          "name": "string",
          "reference": "string",
          "insuranceType": "other_insurance",
          "startDate": "string",
          "noTerm": false,
          "endDate": "string",
          "fixedTerm": false,
          "situationDate": "2019-01-01",
          "currency": "EUR",
          "onlyDeathCover": false,
          "acquiredReserve": 0,
          "deathPayout": "premium",
          "deathValue": 0,
          "acquiredLifeValue": 0,
          "reduced": false,
          "premiumsPaid": 0,
          "premiumPeriodicity": "annual",
          "premiumEndDate": "string",
          "premium": 0,
          "lifeValue": 0,
          "enumPolicyholder": "other",
          "employerId": "string",
          "employerName": "string",
          "policyholderIds": [
            "string"
          ],
          "enumInsuredParty": "policyholders",
          "insuredPartyIds": [
            "string"
          ],
          "beneficiaryIsCompany": false,
          "enumLifeBeneficiary": "policyholders",
          "lifeBeneficiaryIds": [
            "string"
          ],
          "enumDeathBeneficiary": "succession",
          "deathBeneficiaryIds": [
            "string"
          ],
          "insuranceCompanyName": "string",
          "ecbCode": "string",
          "countryCode": "BE",
          "category": "protection",
          "managerName": "string",
          "swiftCode": "string",
          "bankName": "string",
          "listedRealEstateUnderlyingShare": 0,
          "equityUnderlyingShare": 0,
          "privateEquityUnderlyingShare": 0,
          "bondsUnderlyingShare": 0,
          "cashUnderlyingShare": 100,
          "otherUnderlyingShare": 0
        }
      ]
    }
  }
}
```

<h3 id="get-the-estate-of-one-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Group found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="get-the-estate-of-one-group-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|object|true|none|none|
|»» id|string|false|none|none|
|»» type|string|false|none|none|
|»» attributes|object|false|none|none|
|»»» estateAssets|[[EstateAssetAttributes](#schemaestateassetattributes)]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Get the Family of one Group

<a id="opIdgetGroupFamily"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{id}/Family");
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

`GET /groups/{id}/Family`

Retrieve the family GroupMemberships and respective DummyUsers of a Group

<h3 id="get-the-family-of-one-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Group ID of the group|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "dummy_user_id_Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "coHolder": false,
        "dead": false,
        "fatherId": "dummy_user_id_1234acds3",
        "motherId": "dummy_user_id_dg7s6cdw5f",
        "currentSpouseId": "dummy_user_id_bcsudg6w3",
        "dummyUser": {
          "id": "dummy_user_id_Yu1234ac",
          "firstName": "Luc",
          "lastName": "Beson",
          "gender": "F",
          "birthday": "1970-02-20",
          "nationality": "BE",
          "countryCode": "FR",
          "zipcode": "75008"
        }
      }
    }
  ]
}
```

<h3 id="get-the-family-of-one-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Group found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="get-the-family-of-one-group-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[GroupMembershipWithDummyUser](#schemagroupmembershipwithdummyuser)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-insurances">Insurances</h1>

## Creates one or more Insurances

<a id="opIdaddInsurances"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "16243hudy",
      "type": "insurance",
      "attributes": {
        "id": "16243hudy",
        "name": "Present to Family",
        "reference": "123drfcvb",
        "startDate": "1970-02-20",
        "currency": "EUR",
        "acquiredReserve": 5003,
        "countryCode": "BE",
        "endDate": "Wed 17 Jul 2019",
        "apiOnly": false,
        "insuranceType": "other_insurance",
        "noTerm": false,
        "fixedTerm": false,
        "situationDate": "2019-01-01",
        "onlyDeathCover": false,
        "deathPayout": "reserve",
        "deathValue": 0,
        "acquiredLifeValue": 5003,
        "reduced": false,
        "premiumsPaid": 0,
        "premiumPeriodicity": "annual",
        "premiumEndDate": "Wed 17 Jul 2019",
        "premium": 0,
        "lifeValue": 5003,
        "enumPolicyholder": "other",
        "policyholderIds": [
          "18273gdh",
          "0",
          "0"
        ],
        "enumInsuredParty": "policyholders",
        "beneficiaryIsCompany": false,
        "enumLifeBeneficiary": "policyholders",
        "enumDeathBeneficiary": "succession",
        "lifeBeneficiaryIds": [
          "0",
          "123df",
          "0"
        ],
        "deathBeneficiaryIds": [
          "0"
        ],
        "insuranceCompanyName": "Big Co Ltd",
        "category": "protection",
        "managerName": "Dr. Mixalot O'Gin",
        "bankName": "Greendwalds Bank",
        "listedRealEstateShare": 0,
        "equityShare": 0,
        "privateEquityShare": 0,
        "bondsShare": 0,
        "cashShare": 100,
        "otherShare": 0,
        "swiftCode": "GEBABEBB00"
      }
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/groups/{groupId}/insurances");
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

`POST /groups/{groupId}/insurances`

> Body parameter

```json
{
  "data": [
    {
      "id": "16243hudy",
      "type": "insurance",
      "attributes": {
        "id": "16243hudy",
        "name": "Present to Family",
        "reference": "123drfcvb",
        "startDate": "1970-02-20",
        "currency": "EUR",
        "acquiredReserve": 5003,
        "countryCode": "BE",
        "endDate": "Wed 17 Jul 2019",
        "apiOnly": false,
        "insuranceType": "other_insurance",
        "noTerm": false,
        "fixedTerm": false,
        "situationDate": "2019-01-01",
        "onlyDeathCover": false,
        "deathPayout": "reserve",
        "deathValue": 0,
        "acquiredLifeValue": 5003,
        "reduced": false,
        "premiumsPaid": 0,
        "premiumPeriodicity": "annual",
        "premiumEndDate": "Wed 17 Jul 2019",
        "premium": 0,
        "lifeValue": 5003,
        "enumPolicyholder": "other",
        "policyholderIds": [
          "18273gdh",
          "0",
          "0"
        ],
        "enumInsuredParty": "policyholders",
        "beneficiaryIsCompany": false,
        "enumLifeBeneficiary": "policyholders",
        "enumDeathBeneficiary": "succession",
        "lifeBeneficiaryIds": [
          "0",
          "123df",
          "0"
        ],
        "deathBeneficiaryIds": [
          "0"
        ],
        "insuranceCompanyName": "Big Co Ltd",
        "category": "protection",
        "managerName": "Dr. Mixalot O'Gin",
        "bankName": "Greendwalds Bank",
        "listedRealEstateShare": 0,
        "equityShare": 0,
        "privateEquityShare": 0,
        "bondsShare": 0,
        "cashShare": 100,
        "otherShare": 0,
        "swiftCode": "GEBABEBB00"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-insurances-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|none|
|body|body|object|false|none|
|» data|body|[[InsuranceObject](#schemainsuranceobject)]|true|none|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "16243hudy",
      "type": "insurance",
      "attributes": {
        "id": "16243hudy",
        "name": "Present to Family",
        "reference": "123drfcvb",
        "startDate": "1970-02-20",
        "currency": "EUR",
        "acquiredReserve": 5003,
        "countryCode": "BE",
        "endDate": "Wed 17 Jul 2019",
        "apiOnly": false,
        "insuranceType": "other_insurance",
        "noTerm": false,
        "fixedTerm": false,
        "situationDate": "2019-01-01",
        "onlyDeathCover": false,
        "deathPayout": "reserve",
        "deathValue": 0,
        "acquiredLifeValue": 5003,
        "reduced": false,
        "premiumsPaid": 0,
        "premiumPeriodicity": "annual",
        "premiumEndDate": "Wed 17 Jul 2019",
        "premium": 0,
        "lifeValue": 5003,
        "enumPolicyholder": "other",
        "policyholderIds": [
          "18273gdh",
          "0",
          "0"
        ],
        "enumInsuredParty": "policyholders",
        "beneficiaryIsCompany": false,
        "enumLifeBeneficiary": "policyholders",
        "enumDeathBeneficiary": "succession",
        "lifeBeneficiaryIds": [
          "0",
          "123df",
          "0"
        ],
        "deathBeneficiaryIds": [
          "0"
        ],
        "insuranceCompanyName": "Big Co Ltd",
        "category": "protection",
        "managerName": "Dr. Mixalot O'Gin",
        "bankName": "Greendwalds Bank",
        "listedRealEstateShare": 0,
        "equityShare": 0,
        "privateEquityShare": 0,
        "bondsShare": 0,
        "cashShare": 100,
        "otherShare": 0,
        "swiftCode": "GEBABEBB00"
      }
    }
  ]
}
```

<h3 id="creates-one-or-more-insurances-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Insurances created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-insurances-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[InsuranceObject](#schemainsuranceobject)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estates">Estates</h1>

## Creates one or more Refresh Values

<a id="opIdrefreshEstateValues"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset"
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/estates/refresh-values");
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

`PATCH /estates/refresh-values`

> Body parameter

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset"
    }
  ]
}
```

<h3 id="creates-one-or-more-refresh-values-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[RefreshValues](#schemarefreshvalues)]|true|none|

> Example responses

> 202 Response

```json
{
  "data": [
    {
      "id": "12345h",
      "type": "estateAsset"
    }
  ]
}
```

<h3 id="creates-one-or-more-refresh-values-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Refresh Values updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<h3 id="creates-one-or-more-refresh-values-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[RefreshValues](#schemarefreshvalues)]|true|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Return Estate object IDs per group

<a id="opIdgetEstateObjectIdsByGroup"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "apiOnly": true,
  "type": "estateAsset",
  "groupIds": [
    "groupID123",
    "groupID124",
    "groupID125",
    "groupID126"
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/estates/object-ids");
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

`POST /estates/object-ids`

POST used instead of GET due to size of groupIds array and array encoding

> Body parameter

```json
{
  "apiOnly": true,
  "type": "estateAsset",
  "groupIds": [
    "groupID123",
    "groupID124",
    "groupID125",
    "groupID126"
  ]
}
```

<h3 id="return-estate-object-ids-per-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[EstateObjectIdsFilter](#schemaestateobjectidsfilter)|false|none|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "groupId": "groupID123",
      "type": "estateLiability",
      "ids": [
        "liabilityID12",
        "liabilityID13",
        "liabilityID14"
      ]
    },
    {
      "groupId": "groupID124",
      "type": "estateLiability",
      "ids": [
        "liabilityID14",
        "liabilityID15",
        "liabilityID16"
      ]
    }
  ]
}
```

<h3 id="return-estate-object-ids-per-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Estate Object Ids per Group fetched|[EstateObjectIdsByGroup](#schemaestateobjectidsbygroup)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## Deletes Estate objects by ID per group

<a id="opIddeleteEstateObjectsByGroup"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "groupId": "groupID123",
      "type": "insurance",
      "ids": [
        "insuranceID123",
        "insuranceID124",
        "insuranceID125",
        "insuranceID126"
      ]
    }
  ]
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/estates/delete-ids");
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

`POST /estates/delete-ids`

> Body parameter

```json
{
  "data": [
    {
      "groupId": "groupID123",
      "type": "insurance",
      "ids": [
        "insuranceID123",
        "insuranceID124",
        "insuranceID125",
        "insuranceID126"
      ]
    }
  ]
}
```

<h3 id="deletes-estate-objects-by-id-per-group-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» data|body|[[EstateDeleteIds](#schemaestatedeleteids)]|true|none|

> Example responses

> 400 Response

```json
{
  "errors": [
    {
      "status": "bad_request",
      "detail": "The entry 'invalid', at /data/attributes/cause does not match the schema at /properties/data/properties/attributes/properties/cause because of enum"
    }
  ]
}
```

<h3 id="deletes-estate-objects-by-id-per-group-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Estate Objects successfully deleted|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-alive">Alive</h1>

## Check if the API connection is alive

<a id="opIdcheckIfAlive"></a>

> Code samples

```http
GET https://[your-subdomain].paxfamilia.com/api/v1/is-alive HTTP/1.1

Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://[your-subdomain].paxfamilia.com/api/v1/is-alive',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/is-alive',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/is-alive',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://[your-subdomain].paxfamilia.com/api/v1/is-alive", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/is-alive");
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

`GET /is-alive`

> Example responses

> 401 Response

```json
{
  "errors": [
    {
      "status": "unauthorized",
      "detail": "Invalid credentials"
    }
  ]
}
```

<h3 id="check-if-the-api-connection-is-alive-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|API is alive|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-general-purpose">General Purpose</h1>

## Change the internal ID of a saved resource

<a id="opIdupdateId"></a>

> Code samples

```http
PATCH https://[your-subdomain].paxfamilia.com/api/v1/update-id HTTP/1.1

Content-Type: application/vnd.api+json
Accept: application/vnd.api+json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/vnd.api+json',
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://[your-subdomain].paxfamilia.com/api/v1/update-id',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/update-id',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": {
    "id": "old_id_345",
    "type": "dummyUser",
    "newId": "new_id_345"
  }
}';
const headers = {
  'Content-Type':'application/vnd.api+json',
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/update-id',
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

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/vnd.api+json"},
        "Accept": []string{"application/vnd.api+json"},
        "X-Api-Key": []string{"4P1k3y87sGd"},
        "Authorization": []string{"4P1k3y87sGd"},

    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "https://[your-subdomain].paxfamilia.com/api/v1/update-id", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/update-id");
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

`PATCH /update-id`

> Body parameter

```json
{
  "data": {
    "id": "old_id_345",
    "type": "dummyUser",
    "newId": "new_id_345"
  }
}
```

<h3 id="change-the-internal-id-of-a-saved-resource-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[NewId](#schemanewid)|false|none|

> Example responses

> 202 Response

```json
{
  "data": {
    "id": "old_id_345",
    "type": "dummyUser",
    "newId": "new_id_345"
  }
}
```

<h3 id="change-the-internal-id-of-a-saved-resource-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Id successfully updated|[NewId](#schemanewid)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[BadRequestError](#schemabadrequesterror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[UnauthorizedError](#schemaunauthorizederror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[NotFoundError](#schemanotfounderror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[UnprocessableEntityError](#schemaunprocessableentityerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-authentication">Authentication</h1>

## Generate JSON Web Token with valid user credentials + Api-Key

<a id="opIdcreateAuthToken"></a>

> Code samples

```http
POST https://[your-subdomain].paxfamilia.com/api/v1/users/login HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://[your-subdomain].paxfamilia.com/api/v1/users/login',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://[your-subdomain].paxfamilia.com/api/v1/users/login',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "user": {
    "password": "+3o2YlWUg1mg=",
    "email": "example_api_user@email.com"
  },
  "company": {
    "apiKey": "zVcrB5ZOQOwnBiqlodQItgtt"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://[your-subdomain].paxfamilia.com/api/v1/users/login',
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
    req, err := http.NewRequest("POST", "https://[your-subdomain].paxfamilia.com/api/v1/users/login", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://[your-subdomain].paxfamilia.com/api/v1/users/login");
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

`POST /users/login`

> Body parameter

```json
{
  "user": {
    "password": "+3o2YlWUg1mg=",
    "email": "example_api_user@email.com"
  },
  "company": {
    "apiKey": "zVcrB5ZOQOwnBiqlodQItgtt"
  }
}
```

<h3 id="generate-json-web-token-with-valid-user-credentials-+-api-key-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|false|none|
|» user|body|object|true|none|
|»» email|body|string|true|none|
|»» password|body|string|true|none|
|» company|body|object|true|none|
|»» apiKey|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoiMTQwODdiN2QtMTI4ZC00YWM5LTljYmMtZTJiMTI5ZWQ3NDcxIiwiZXhwIjoxNTcyMzYwMTEzfQ.ciy_lAZUkj1PBNQvGGUhoaZY-Yei3M3ZiCZhZouiLAY",
  "message": "Login Successful"
}
```

<h3 id="generate-json-web-token-with-valid-user-credentials-+-api-key-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Login Successful|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Invalid credentials|Inline|

<h3 id="generate-json-web-token-with-valid-user-credentials-+-api-key-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» accessToken|string|false|none|none|
|» message|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|message|Login Successful|

Status Code **401**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|object|false|none|none|
|»» userAuthentication|[string]|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocSbadrequesterror">BadRequestError</h2>

<a id="schemabadrequesterror"></a>

```json
{
  "errors": [
    {
      "status": "bad_request",
      "detail": "The entry 'invalid', at /data/attributes/cause does not match the schema at /properties/data/properties/attributes/properties/cause because of enum"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errors|[object]|true|none|none|
|» status|string|true|none|none|
|» detail|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|bad_request|

<h2 id="tocSunauthorizederror">UnauthorizedError</h2>

<a id="schemaunauthorizederror"></a>

```json
{
  "errors": [
    {
      "status": "unauthorized",
      "detail": "Invalid credentials"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errors|[object]|true|none|none|
|» status|string|true|none|none|
|» detail|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|unauthorized|

<h2 id="tocSunprocessableentityerror">UnprocessableEntityError</h2>

<a id="schemaunprocessableentityerror"></a>

```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "detail": "Dummy User ID: 1234 is/are not family member(s) of group: 9876"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errors|[object]|true|none|none|
|» status|string|true|none|none|
|» detail|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|unprocessable_entity|

<h2 id="tocSnotfounderror">NotFoundError</h2>

<a id="schemanotfounderror"></a>

```json
{
  "errors": [
    {
      "status": "not_found",
      "detail": "Invalid ID: CompanyMembership 12345"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|errors|[object]|true|none|none|
|» status|string|true|none|none|
|» detail|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status|not_found|

<h2 id="tocSapilog">ApiLog</h2>

<a id="schemaapilog"></a>

```json
{
  "id": "a7b9cv76eb",
  "type": "apiLog",
  "attributes": {
    "id": "a7b9cv76eb",
    "companyMembershipId": "uyd86tb",
    "success": false,
    "status": "not_found",
    "description": "Invalid ID: EstateAsset 12345",
    "groupPublicId": "suygd97",
    "resourceId": "86757h",
    "controller": "estate_liabilities",
    "action": "create",
    "requestMethod": "POST"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|false|none|api log id|
|» companyMembershipId|string|false|none|employee public id if their is en employee associated to this log|
|» success|boolean|true|none|request success or failure,|
|» status|string|false|none|request status http code in word|
|» description|string|false|none|any valid description needed, for success ususally amount saved, for failure usually error text|
|» groupPublicId|string|false|none|group public id associated to the log when group scoped resource|
|» resourceId|string|false|none|public id of the resource in question when in the case of a specific resource error|
|» controller|string|false|none|resource controller log originated from|
|» action|string|false|none|resource action log originated from|
|» requestMethod|string|false|none|http request method (post, patch, delete, get)|

#### Enumerated Values

|Property|Value|
|---|---|
|type|apiLog|

<h2 id="tocScommonpercentattributes">CommonPercentAttributes</h2>

<a id="schemacommonpercentattributes"></a>

```json
{
  "listedRealEstateShare": 15,
  "privateEquityShare": 15,
  "equityShare": 15,
  "bondsShare": 15,
  "cashShare": 15,
  "otherShare": 25
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|listedRealEstateShare|number|false|none|Real estate percent-share of the asset, shares must add up to 100|
|equityShare|number|false|none|Equity percent-share of the asset, shares must add up to 100|
|privateEquityShare|number|false|none|Private equity percent-share of the asset, shares must add up to 100|
|bondsShare|number|false|none|Bonds percent-share of the asset, shares must add up to 100|
|cashShare|number|false|none|Cash percent-share of the asset, shares must add up to 100|
|otherShare|number|false|none|Other percent-share of the asset, shares must add up to 100|

<h2 id="tocSestateasset">EstateAsset</h2>

<a id="schemaestateasset"></a>

```json
{
  "id": "12345h",
  "type": "estateAsset",
  "attributes": {
    "id": "123dfer",
    "currentValue": 2344
  }
}

```

### Properties

*allOf - discriminator: RefreshValues.type*

*and*

<h2 id="tocSestateassetattributes">EstateAssetAttributes</h2>

<a id="schemaestateassetattributes"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|internal reference to asset, must be unique in the group scope. Will be generated randomly if not provided|
|category|string|true|none|none|
|apiOnly|boolean|false|none|can only be edited through the api endpoint|
|name|string|false|none|Custom name of the asset. If left empty will be constructed from the address|
|countryCode|string|false|none|Country where the asset is located|
|zipcode|string|false|none|Zipcode where the asset is located. Required for real estate in Belgium to calculate property tax from cadastral income|
|currentValue|number|true|none|Current value of the asset|
|currency|string|false|none|Currency of the value(s)|
|defaultOwnershipType|string|false|none|Ownership of the asset. Owner refers to the 'main client', partner refers to the main client spouse or partner|
|community|boolean|false|none|Is the asset owned by the community? If not specified, defaults according to the matrimonial regime|

#### Enumerated Values

|Property|Value|
|---|---|
|category|account|
|category|company|
|category|investment|
|category|other_asset|
|category|real_estate|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|
|currency|AED|
|currency|AFN|
|currency|ALL|
|currency|AMD|
|currency|ANG|
|currency|AOA|
|currency|ARS|
|currency|AUD|
|currency|AWG|
|currency|AZN|
|currency|BAM|
|currency|BBD|
|currency|BDT|
|currency|BGN|
|currency|BHD|
|currency|BIF|
|currency|BMD|
|currency|BND|
|currency|BOB|
|currency|BRL|
|currency|BSD|
|currency|BTN|
|currency|BWP|
|currency|BYN|
|currency|BYR|
|currency|BZD|
|currency|CAD|
|currency|CDF|
|currency|CHF|
|currency|CLF|
|currency|CLP|
|currency|CNY|
|currency|COP|
|currency|CRC|
|currency|CUC|
|currency|CUP|
|currency|CVE|
|currency|CZK|
|currency|DJF|
|currency|DKK|
|currency|DOP|
|currency|DZD|
|currency|EGP|
|currency|ERN|
|currency|ETB|
|currency|EUR|
|currency|FJD|
|currency|FKP|
|currency|GBP|
|currency|GEL|
|currency|GHS|
|currency|GIP|
|currency|GMD|
|currency|GNF|
|currency|GTQ|
|currency|GYD|
|currency|HKD|
|currency|HNL|
|currency|HRK|
|currency|HTG|
|currency|HUF|
|currency|IDR|
|currency|ILS|
|currency|INR|
|currency|IQD|
|currency|IRR|
|currency|ISK|
|currency|JMD|
|currency|JOD|
|currency|JPY|
|currency|KES|
|currency|KGS|
|currency|KHR|
|currency|KMF|
|currency|KPW|
|currency|KRW|
|currency|KWD|
|currency|KYD|
|currency|KZT|
|currency|LAK|
|currency|LBP|
|currency|LKR|
|currency|LRD|
|currency|LSL|
|currency|LTL|
|currency|LVL|
|currency|LYD|
|currency|MAD|
|currency|MDL|
|currency|MGA|
|currency|MKD|
|currency|MMK|
|currency|MNT|
|currency|MOP|
|currency|MRO|
|currency|MUR|
|currency|MVR|
|currency|MWK|
|currency|MXN|
|currency|MYR|
|currency|MZN|
|currency|NAD|
|currency|NGN|
|currency|NIO|
|currency|NOK|
|currency|NPR|
|currency|NZD|
|currency|OMR|
|currency|PAB|
|currency|PEN|
|currency|PGK|
|currency|PHP|
|currency|PKR|
|currency|PLN|
|currency|PYG|
|currency|QAR|
|currency|RON|
|currency|RSD|
|currency|RUB|
|currency|RWF|
|currency|SAR|
|currency|SBD|
|currency|SCR|
|currency|SDG|
|currency|SEK|
|currency|SGD|
|currency|SHP|
|currency|SKK|
|currency|SLL|
|currency|SOS|
|currency|SRD|
|currency|SSP|
|currency|STD|
|currency|SVC|
|currency|SYP|
|currency|SZL|
|currency|THB|
|currency|TJS|
|currency|TMT|
|currency|TND|
|currency|TOP|
|currency|TRY|
|currency|TTD|
|currency|TWD|
|currency|TZS|
|currency|UAH|
|currency|UGX|
|currency|USD|
|currency|UYU|
|currency|UZS|
|currency|VEF|
|currency|VND|
|currency|VUV|
|currency|WST|
|currency|XAF|
|currency|XAG|
|currency|XAU|
|currency|XBA|
|currency|XBB|
|currency|XBC|
|currency|XBD|
|currency|XCD|
|currency|XDR|
|currency|XOF|
|currency|XPD|
|currency|XPF|
|currency|XPT|
|currency|XTS|
|currency|YER|
|currency|ZAR|
|currency|ZMK|
|currency|ZMW|
|currency|BTC|
|currency|JEP|
|currency|GGP|
|currency|IMP|
|currency|XFU|
|currency|GBX|
|currency|CNH|
|currency|EEK|
|currency|MTL|
|currency|TMM|
|currency|ZWD|
|currency|ZWL|
|currency|ZWN|
|currency|ZWR|
|defaultOwnershipType|owner|
|defaultOwnershipType|partner|
|defaultOwnershipType|common|
|defaultOwnershipType|owner_np_children|
|defaultOwnershipType|partner_np_children|
|defaultOwnershipType|common_np_children|
|defaultOwnershipType|owner_us_parent|
|defaultOwnershipType|partner_us_parent|
|defaultOwnershipType|other|

<h2 id="tocSrealestate">realEstate</h2>

<a id="schemarealestate"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "address": "St. St. Pierre de Levanaco",
  "realEstateType": "offices",
  "autoPropertyTax": false,
  "annualRent": 10,
  "cadastralIncome": 130,
  "propertyTax": 10,
  "otherCharges": 120,
  "workValue": 1230
}

```

### Properties

*allOf - discriminator: EstateAssetAttributes.category*

*and*

<h2 id="tocSinvestment">investment</h2>

<a id="schemainvestment"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "listedRealEstateShare": 15,
  "privateEquityShare": 15,
  "equityShare": 15,
  "bondsShare": 15,
  "cashShare": 15,
  "otherShare": 25,
  "bankName": "ING Belgium",
  "manager": "Fred Perry",
  "reference": "126732",
  "swiftCode": "GBABDD88",
  "rateOfReturn": 2,
  "capitalisationPc": 3
}

```

### Properties

*allOf - discriminator: EstateAssetAttributes.category*

*and*

*and*

<h2 id="tocSaccount">account</h2>

<a id="schemaaccount"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "bankName": "ING Belgium",
  "accountType": "current_account",
  "iban": "0022333344445555",
  "swiftCode": "GBABDD88",
  "rateOfReturn": 2
}

```

### Properties

*allOf - discriminator: EstateAssetAttributes.category*

*and*

<h2 id="tocScompany">company</h2>

<a id="schemacompany"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "listedRealEstateShare": 15,
  "privateEquityShare": 15,
  "equityShare": 15,
  "bondsShare": 15,
  "cashShare": 15,
  "otherShare": 25,
  "address": "Str. St Patrick Bateapo",
  "officialName": "Car Wash Enterprises",
  "vatNumber": "12345",
  "realEstateShare": 0,
  "hasDividend": false,
  "dividendIndexation": false,
  "annualDividend": 2,
  "companyObject": "patrimonial",
  "companyType": "SPRL",
  "receivablesShare": 0,
  "agriSpecificShare": 0
}

```

### Properties

*allOf - discriminator: EstateAssetAttributes.category*

*and*

*and*

<h2 id="tocSotherasset">otherAsset</h2>

<a id="schemaotherasset"></a>

```json
{
  "id": "345abcd",
  "category": "account",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "otherAssetType": "precious_metal",
  "privateUse": false
}

```

### Properties

*allOf - discriminator: EstateAssetAttributes.category*

*and*

<h2 id="tocSassetownership">AssetOwnership</h2>

<a id="schemaassetownership"></a>

```json
{
  "type": "assetOwnership",
  "attributes": {
    "ownerId": "12345abcd",
    "percentage": 2,
    "ownershipType": "fp"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» ownerId|string|true|none|Internal ID of the owner. If blank, will expect companyId.|
|» companyId|string|false|none|Internal ID of the company that owns the asset. Ignored if ownerId is provided.|
|» ownerCategory|string|false|none|Owner category. A physical person ('person'), the community ('community') or a moral person ('company')|
|» communityOwner|string|false|none|Only in case of 'community ownerCategory'. Whether the asset is under both names or the main data subject or it's partner/spouse",|
|» ownershipType|string|false|none|Type of the ownership. Full property ('fp'), bare ownership ('np') or usufruct ('us')|
|» percentage|number|true|none|Percentage ownership. Decimals must be separated by a dot. Eg. 25.5|
|» otherOwnerId|string|false|none|Internal ID of the owner holding the other side of the dismembered ownership, if applicable. Ignored if ownershipType is 'fp'.|
|» otherCompanyId|string|false|none|Internal ID of the company holding the other side of the dismembered ownership, if applicable. Ignored if ownershipType is 'fp' and/or if otherOwnerId is provided.|
|» usufructStartDate|string|false|none|YYYY-MM-DD. Start date of the usufruct. Only when a company owns the usufruct. Will default to current date|
|» usufructPcValue|number|false|none|Initial percentage of the full property value. Only when a company owns the usufruct.|
|» usufructYearsDuration|integer|false|none|Number of years the usufruct was initially granted to the company. Only when a company owns the usufruct.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|assetOwnership|
|ownerCategory|person|
|ownerCategory|community|
|ownerCategory|company|
|communityOwner|both_names|
|communityOwner|owner_name|
|communityOwner|partner_name|
|ownershipType|fp|
|ownershipType|np|
|ownershipType|us|

<h2 id="tocScompanymembership">CompanyMembership</h2>

<a id="schemacompanymembership"></a>

```json
{
  "id": "123abc123",
  "type": "companyMembership",
  "attributes": {
    "companyUnitId": "12345abcd",
    "memberRight": "read",
    "id": "123abc123",
    "email": "person_abc@example.com",
    "firstName": "Freddy",
    "lastName": "Luke",
    "gender": "M",
    "birthday": "1970-02-20",
    "nationality": "BE",
    "countryCode": "BE",
    "zipcode": "1040",
    "locale": "fr"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|» lastName|string|true|none|none|
|» firstName|string|true|none|none|
|» gender|string|true|none|none|
|» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the phony library https://github.com/floere/phony to validate plausibility of number. Country extension defaults to +32 unless provided|
|» countryCode|string|false|none|Country (residence) of the employee|
|» locale|string|true|none|none|
|» memberRight|string|true|none|right of the employee. read and write means can create new clients, read only means the employee can't create clients but can access clients he has been given access to|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|
|locale|fr|
|locale|nl|
|memberRight|read_and_write|
|memberRight|read|

<h2 id="tocScompanyunit">CompanyUnit</h2>

<a id="schemacompanyunit"></a>

```json
{
  "id": "321dsa",
  "type": "companyUnit",
  "attributes": {
    "name": "Procurement Department",
    "address": "Rue Lac Lemanid",
    "countryCode": "BE",
    "zipcode": "1050",
    "locale": "fr",
    "parentId": "123asd",
    "id": "321dsa"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|true|none|Internal id of the unit, center or department. Will be generated randomly if not provided|
|» parentUnitId|string|false|none|A unit can be a sub unit of another unit (parentUnit).|
|» name|string|true|none|Name the unit, center or department|
|» countryCode|string|false|none|Country of the unit. Default to the country of the company it belongs to.|
|» address|string|false|none|Address of the unit|
|» zipcode|string|false|none|Zipcode of the unit|
|» locale|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyUnit|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|
|locale|fr|
|locale|nl|

<h2 id="tocSdonation">Donation</h2>

<a id="schemadonation"></a>

```json
{
  "id": "id987fd",
  "type": "donation",
  "attributes": {
    "name": "Annual Donation",
    "transactionDate": "1970-02-20",
    "amount": 5000,
    "donationType": "movable",
    "ownershipType": "fp",
    "annuityClause": false,
    "annuityPc": 0,
    "registered": false,
    "id": "id987fd",
    "donorIds": [
      "123abc",
      "0",
      "123abcd"
    ],
    "doneeIds": [
      "123abc2",
      "123abcd1"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|true|none|Internal id of the donation. Must be unique. Will be generated randomly if not provided|
|» estateAssetId|string|false|none|Id of the asset it relates to.|
|» name|string|true|none|Name or reference for the donation|
|» transactionDate|string|true|none|Donation date. YYYY-MM-DD|
|» donationType|string|true|none|type of donation|
|» amount|number|true|none|Total intrinsic value of the donation. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|» currentValue|string|false|none|Current value of the donation. Default to amount|
|» donorIds|[string]|true|none|Array of donor ids.|
|» doneeIds|[string]|true|none|Array of donee ids.|
|» calleeIds|[string]|false|none|Internal IDs of the callee(s). Only in case residuo clause is true.|
|» ownershipType|string|true|none|Specify if the donation is not for the full ownership. Full property ('fp'), bare ownership ('np') or bare ownership with reserve of usufruct ('np_reserve_us')|
|» inheritanceTreatment|string|false|none|Treatment at succession. advance = advance on inheritance, no_report = par preciput et hors part, advance_with_no_report = advance on inheritance with no report in nature|
|» nonTransferabilityClause|string|false|none|type of non transferability clause (inalienability) if any|
|» nonTransferabilityDuration|integer|false|none|Number of years of inalienability. Required if nonTransferabilityClause is forYears|
|» noCommunityCondition|boolean|false|none|Clause preventing to bring the given assets to a community|
|» returnClause|string|false|none|Clause of conventional return|
|» returnClauseOptional|boolean|false|none|Is the return clause optional?|
|» annuityClause|boolean|false|none|Is there a charge/rente (Charge de rente)|
|» annuityAmount|number|false|none|Annual annuity amount. Required if annuityClause is true|
|» annuityPc|number|false|none|Annual annuity indexation.|
|» description|string|false|none|Description|
|» registered|boolean|true|none|Is the donation registered?|
|» contractForm|string|false|none|What contractual form did the donation take?|
|» notaris|string|false|none|Name of the notaris|

#### Enumerated Values

|Property|Value|
|---|---|
|type|donation|
|donationType|movable|
|donationType|immovable|
|ownershipType|fp|
|ownershipType|np_reserve_us|
|ownershipType|np|
|inheritanceTreatment|advance|
|inheritanceTreatment|no_report|
|inheritanceTreatment|advance_with_no_report|
|inheritanceTreatment|dunno|
|nonTransferabilityClause|none|
|nonTransferabilityClause|for_years|
|nonTransferabilityClause|till_donor_death|
|returnClause|none|
|returnClause|yes_no_descendance|
|returnClause|yes_with_descendance|
|returnClause|dunno|
|contractForm|notarial_deed|
|contractForm|foreign_notarial_deed|
|contractForm|none|
|contractForm|null|

<h2 id="tocSdummyuserattributes">DummyUserAttributes</h2>

<a id="schemadummyuserattributes"></a>

```json
{
  "id": "123abcde",
  "firstName": "Luc",
  "lastName": "Beson",
  "gender": "F",
  "birthday": "1970-02-20",
  "nationality": "BE",
  "countryCode": "FR",
  "zipcode": "75008"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|lastName|string|true|none|required|
|firstName|string|true|none|required|
|email|string|false|none|Email of the client. Optional.|
|gender|string|true|none|none|
|birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|nationality|string|true|none|Country code of nationality|
|countryCode|string|true|none|Country code of residence|
|zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|

#### Enumerated Values

|Property|Value|
|---|---|
|gender|M|
|gender|F|
|nationality|TJ|
|nationality|JM|
|nationality|HT|
|nationality|ST|
|nationality|MS|
|nationality|AE|
|nationality|PK|
|nationality|NL|
|nationality|LU|
|nationality|BZ|
|nationality|IR|
|nationality|BO|
|nationality|UY|
|nationality|GH|
|nationality|SA|
|nationality|CI|
|nationality|MF|
|nationality|TF|
|nationality|AI|
|nationality|QA|
|nationality|SX|
|nationality|LY|
|nationality|BV|
|nationality|PG|
|nationality|KG|
|nationality|GQ|
|nationality|EH|
|nationality|NU|
|nationality|PR|
|nationality|GD|
|nationality|KR|
|nationality|HM|
|nationality|SM|
|nationality|SL|
|nationality|CD|
|nationality|MK|
|nationality|TR|
|nationality|DZ|
|nationality|GE|
|nationality|PS|
|nationality|BB|
|nationality|UA|
|nationality|GP|
|nationality|PF|
|nationality|NA|
|nationality|BW|
|nationality|SY|
|nationality|TG|
|nationality|DO|
|nationality|AQ|
|nationality|CH|
|nationality|MG|
|nationality|FO|
|nationality|VG|
|nationality|GI|
|nationality|BN|
|nationality|LA|
|nationality|IS|
|nationality|EE|
|nationality|UM|
|nationality|LT|
|nationality|RS|
|nationality|MR|
|nationality|AD|
|nationality|HU|
|nationality|TK|
|nationality|MY|
|nationality|AO|
|nationality|CV|
|nationality|NF|
|nationality|PA|
|nationality|GW|
|nationality|BE|
|nationality|PT|
|nationality|GB|
|nationality|IM|
|nationality|US|
|nationality|YE|
|nationality|HK|
|nationality|AZ|
|nationality|CC|
|nationality|ML|
|nationality|SK|
|nationality|VU|
|nationality|TL|
|nationality|HR|
|nationality|SR|
|nationality|MU|
|nationality|CZ|
|nationality|PM|
|nationality|LS|
|nationality|WS|
|nationality|KM|
|nationality|IT|
|nationality|BI|
|nationality|WF|
|nationality|GN|
|nationality|SG|
|nationality|CO|
|nationality|CN|
|nationality|AW|
|nationality|MA|
|nationality|FI|
|nationality|VA|
|nationality|ZW|
|nationality|KY|
|nationality|BH|
|nationality|PY|
|nationality|EC|
|nationality|LR|
|nationality|RU|
|nationality|PL|
|nationality|OM|
|nationality|MT|
|nationality|SS|
|nationality|DE|
|nationality|TM|
|nationality|SJ|
|nationality|MM|
|nationality|TT|
|nationality|IL|
|nationality|BD|
|nationality|NR|
|nationality|LK|
|nationality|UG|
|nationality|NG|
|nationality|BQ|
|nationality|MX|
|nationality|CW|
|nationality|SI|
|nationality|MN|
|nationality|CA|
|nationality|AX|
|nationality|VN|
|nationality|TW|
|nationality|JP|
|nationality|IO|
|nationality|RO|
|nationality|BG|
|nationality|GU|
|nationality|BR|
|nationality|AM|
|nationality|ZM|
|nationality|DJ|
|nationality|JE|
|nationality|AT|
|nationality|CM|
|nationality|SE|
|nationality|FJ|
|nationality|KZ|
|nationality|GL|
|nationality|GY|
|nationality|CX|
|nationality|MW|
|nationality|TN|
|nationality|ZA|
|nationality|TO|
|nationality|CY|
|nationality|MV|
|nationality|PN|
|nationality|RW|
|nationality|NI|
|nationality|KN|
|nationality|BJ|
|nationality|ET|
|nationality|GM|
|nationality|TZ|
|nationality|VC|
|nationality|FK|
|nationality|SD|
|nationality|MC|
|nationality|AU|
|nationality|CL|
|nationality|DK|
|nationality|FR|
|nationality|TC|
|nationality|CU|
|nationality|AL|
|nationality|MZ|
|nationality|BS|
|nationality|NE|
|nationality|GT|
|nationality|LI|
|nationality|NP|
|nationality|BF|
|nationality|PW|
|nationality|KW|
|nationality|IN|
|nationality|GA|
|nationality|TV|
|nationality|MO|
|nationality|SH|
|nationality|MD|
|nationality|CK|
|nationality|AR|
|nationality|SC|
|nationality|IE|
|nationality|ES|
|nationality|LB|
|nationality|BM|
|nationality|RE|
|nationality|KI|
|nationality|AG|
|nationality|MQ|
|nationality|SV|
|nationality|JO|
|nationality|TH|
|nationality|SO|
|nationality|MH|
|nationality|CG|
|nationality|KP|
|nationality|GF|
|nationality|BA|
|nationality|YT|
|nationality|GS|
|nationality|KE|
|nationality|PE|
|nationality|BT|
|nationality|SZ|
|nationality|CR|
|nationality|TD|
|nationality|DM|
|nationality|NC|
|nationality|GR|
|nationality|GG|
|nationality|HN|
|nationality|VI|
|nationality|CF|
|nationality|SN|
|nationality|AF|
|nationality|MP|
|nationality|PH|
|nationality|BY|
|nationality|LV|
|nationality|NO|
|nationality|EG|
|nationality|KH|
|nationality|IQ|
|nationality|LC|
|nationality|NZ|
|nationality|BL|
|nationality|UZ|
|nationality|ID|
|nationality|ER|
|nationality|VE|
|nationality|FM|
|nationality|SB|
|nationality|ME|
|nationality|AS|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|

<h2 id="tocSdummyuser">DummyUser</h2>

<a id="schemadummyuser"></a>

```json
{
  "id": "123abcde",
  "type": "dummyUser",
  "attributes": {
    "id": "123abcde",
    "firstName": "Luc",
    "lastName": "Beson",
    "gender": "F",
    "birthday": "1970-02-20",
    "nationality": "BE",
    "countryCode": "FR",
    "zipcode": "75008"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|dummyUser|

<h2 id="tocSestateliability">EstateLiability</h2>

<a id="schemaestateliability"></a>

```json
{
  "id": "12345h",
  "type": "estateAsset",
  "attributes": {
    "id": "123dfer",
    "rate": 2
  }
}

```

### Properties

*allOf - discriminator: RefreshValues.type*

*and*

<h2 id="tocSestateliabilitywithguarantees">EstateLiabilityWithGuarantees</h2>

<a id="schemaestateliabilitywithguarantees"></a>

```json
{
  "id": "abcd1234",
  "type": "estateLiability",
  "attributes": {
    "id": "abcd1234",
    "name": "Birthday gift to my son's 30th",
    "countryCode": "BE",
    "currency": "EUR",
    "initialDate": "1970-02-20",
    "initialAmount": 5001,
    "bankName": "Grifindor Vault",
    "apiOnly": false,
    "liabilityType": "bank_loan",
    "repaymentType": "constant_periodicity",
    "periodicity": "monthly",
    "periodsDuration": 1,
    "rate": 0,
    "sameOwnershipAsAsset": true,
    "borrowers": [
      "0",
      "12345mn",
      "0"
    ],
    "lenders": [
      "12345mnoo0"
    ],
    "linkedToAsset": false,
    "rateType": "fixed",
    "balanceInsurance": false,
    "balanceInsurancePc": 0,
    "swiftCode": "GEBABEBB00",
    "guarantees": [
      {
        "amount": 23000,
        "guaranteeType": "other_guarantee",
        "guarantorableId": "estate_asset_id_653",
        "guarantorableType": "EstateAsset"
      },
      {
        "amount": 73810,
        "guaranteeType": "other_guarantee",
        "guarantorableId": "dummy_user_id_456",
        "guarantorableType": "GroupMembership"
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|false|none|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|» apiOnly|boolean|false|none|can only be edited through the api endpoint|
|» name|string|true|none|Custom name of the liability. Can also be a reference.|
|» liabilityType|string|true|none|type of account|
|» linkedToAsset|boolean|false|none|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|» estateAssetId|string|false|none|Internal reference to asset. Will be ignored if linkedToAsset is false. Required if linkedToAsset is true.|
|» swiftCode|string|false|none|Swift code of the bank, eg. 'GEBABEBB'. If not provided, bank will be created from the bankName but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if liabilityType is bank_loan, otherwise ignored.|
|» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its swiftCode if a valid one is provided. Required if liabilityType is bank_loan, otherwise ignored.|
|» countryCode|string|false|none|Country of the applicable law.|
|» initialAmount|number|true|none|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|» initialDate|string|true|none|Initial date of the loan. YYYY-MM-DD|
|» currency|string|false|none|Currency of the value(s)|
|» repaymentType|string|true|none|type of account|
|» periodicity|string|true|none|periodicity of the principal and/or interest payment|
|» periodsDuration|integer|true|none|Number of repayment periods. Ignored if repaymentType has no end date (no_end_pay_interest or no_end_capitalized_interest)|
|» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|» rateType|string|false|none|fixed or variable interest rate|
|» sameOwnershipAsAsset|boolean|false|none|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if linkedToAsset is set to false.|
|» borrowers|[string]|false|none|Ignored if sameOwnershipAsAsset is true, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example "['clientId', 'companyId', '0', '0']" will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|» lenders|[string]|false|none|Ignored if liabilityType is bank_loan. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example "['clientId', 'companyId', '0', '0']" will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|» balanceInsurance|boolean|false|none|Is the liability covered by a balance insurance (ASRD)?|
|» balanceInsurancePc|number|false|none|Percentage of the loan covered by a balance insurance. Ignored if balanceInsurance is false|
|» guarantees|[object]|false|none|none|
|»» amount|number|true|none|Amount of the guarantee. Will default to the initialAmount. Ignored unless guarantee is true.|
|»» guaranteeType|string|true|none|Type of guarantee. Ignored unless guarantee is true.|
|»» guarantorableId|string|true|none|ID of the asset or person guaranteeing the liability. Will default to the estateAssetId if present. Ignored unless guarantee is true. ID need to exists within PaxFamilia|
|»» guarantorableType|string|true|none|Resource type of the guarantee, can be GroupMembership or EstateAsset|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|liabilityType|bank_loan|
|liabilityType|private_loan|
|liabilityType|other_type|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|
|currency|AED|
|currency|AFN|
|currency|ALL|
|currency|AMD|
|currency|ANG|
|currency|AOA|
|currency|ARS|
|currency|AUD|
|currency|AWG|
|currency|AZN|
|currency|BAM|
|currency|BBD|
|currency|BDT|
|currency|BGN|
|currency|BHD|
|currency|BIF|
|currency|BMD|
|currency|BND|
|currency|BOB|
|currency|BRL|
|currency|BSD|
|currency|BTN|
|currency|BWP|
|currency|BYN|
|currency|BYR|
|currency|BZD|
|currency|CAD|
|currency|CDF|
|currency|CHF|
|currency|CLF|
|currency|CLP|
|currency|CNY|
|currency|COP|
|currency|CRC|
|currency|CUC|
|currency|CUP|
|currency|CVE|
|currency|CZK|
|currency|DJF|
|currency|DKK|
|currency|DOP|
|currency|DZD|
|currency|EGP|
|currency|ERN|
|currency|ETB|
|currency|EUR|
|currency|FJD|
|currency|FKP|
|currency|GBP|
|currency|GEL|
|currency|GHS|
|currency|GIP|
|currency|GMD|
|currency|GNF|
|currency|GTQ|
|currency|GYD|
|currency|HKD|
|currency|HNL|
|currency|HRK|
|currency|HTG|
|currency|HUF|
|currency|IDR|
|currency|ILS|
|currency|INR|
|currency|IQD|
|currency|IRR|
|currency|ISK|
|currency|JMD|
|currency|JOD|
|currency|JPY|
|currency|KES|
|currency|KGS|
|currency|KHR|
|currency|KMF|
|currency|KPW|
|currency|KRW|
|currency|KWD|
|currency|KYD|
|currency|KZT|
|currency|LAK|
|currency|LBP|
|currency|LKR|
|currency|LRD|
|currency|LSL|
|currency|LTL|
|currency|LVL|
|currency|LYD|
|currency|MAD|
|currency|MDL|
|currency|MGA|
|currency|MKD|
|currency|MMK|
|currency|MNT|
|currency|MOP|
|currency|MRO|
|currency|MUR|
|currency|MVR|
|currency|MWK|
|currency|MXN|
|currency|MYR|
|currency|MZN|
|currency|NAD|
|currency|NGN|
|currency|NIO|
|currency|NOK|
|currency|NPR|
|currency|NZD|
|currency|OMR|
|currency|PAB|
|currency|PEN|
|currency|PGK|
|currency|PHP|
|currency|PKR|
|currency|PLN|
|currency|PYG|
|currency|QAR|
|currency|RON|
|currency|RSD|
|currency|RUB|
|currency|RWF|
|currency|SAR|
|currency|SBD|
|currency|SCR|
|currency|SDG|
|currency|SEK|
|currency|SGD|
|currency|SHP|
|currency|SKK|
|currency|SLL|
|currency|SOS|
|currency|SRD|
|currency|SSP|
|currency|STD|
|currency|SVC|
|currency|SYP|
|currency|SZL|
|currency|THB|
|currency|TJS|
|currency|TMT|
|currency|TND|
|currency|TOP|
|currency|TRY|
|currency|TTD|
|currency|TWD|
|currency|TZS|
|currency|UAH|
|currency|UGX|
|currency|USD|
|currency|UYU|
|currency|UZS|
|currency|VEF|
|currency|VND|
|currency|VUV|
|currency|WST|
|currency|XAF|
|currency|XAG|
|currency|XAU|
|currency|XBA|
|currency|XBB|
|currency|XBC|
|currency|XBD|
|currency|XCD|
|currency|XDR|
|currency|XOF|
|currency|XPD|
|currency|XPF|
|currency|XPT|
|currency|XTS|
|currency|YER|
|currency|ZAR|
|currency|ZMK|
|currency|ZMW|
|currency|BTC|
|currency|JEP|
|currency|GGP|
|currency|IMP|
|currency|XFU|
|currency|GBX|
|currency|CNH|
|currency|EEK|
|currency|MTL|
|currency|TMM|
|currency|ZWD|
|currency|ZWL|
|currency|ZWN|
|currency|ZWR|
|repaymentType|constant_periodicity|
|repaymentType|constant_principal|
|repaymentType|bullet|
|repaymentType|no_end_pay_interest|
|repaymentType|no_end_capitalized_interest|
|repaymentType|bullet_capitalized_interest|
|periodicity|monthly|
|periodicity|quarterly|
|periodicity|semi_annual|
|periodicity|annual|
|rateType|fixed|
|rateType|variable|
|guaranteeType|mortgage|
|guaranteeType|mortgage_mandate|
|guaranteeType|personal_guarantee|
|guaranteeType|pledge|
|guaranteeType|other_guarantee|
|guarantorableType|EstateAsset|
|guarantorableType|GroupMembership|

<h2 id="tocSgroupmembershipattributes">GroupMembershipAttributes</h2>

<a id="schemagroupmembershipattributes"></a>

```json
{
  "sex": "F",
  "status": "approved",
  "memberRight": "no_right",
  "dead": false,
  "fatherId": "1234acds3",
  "adoption": "none",
  "extendedMinority": true,
  "provisionalAdministration": true,
  "judicialProtection": false,
  "extrajudicialProtection": false,
  "dummyUserId": "Yu1234ac"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|dummyUserId|string|true|none|Id of an existing dummy user.|
|coHolder|boolean|false|none|Is the person a main data subject of the group|
|dead|boolean|false|none|Is the person deceased?|
|fatherId|string|false|none|Internal reference to the father, must be an id of an existing dummy user|
|motherId|string|false|none|internal reference to the mother, must be an id of an existing dummy user|
|currentSpouseId|string|false|none|internal reference to the partner, must be an id of an existing dummy user|
|spouseType|string|false|none|type of partner relationship if current spouse exist|
|regimeType|string|false|none|type of matrimonial regime if spouse_type is spouse|
|adoption|string|false|none|type of adoption if any|
|extendedMinority|boolean|false|none|none|
|provisionalAdministration|boolean|false|none|none|
|judicialProtection|boolean|false|none|none|
|extrajudicialProtection|boolean|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|spouseType|spouse|
|spouseType|legal_cohabitant|
|spouseType|simple_cohabitant|
|regimeType|common_only_acquets|
|regimeType|separate_ownership|
|regimeType|separate_ownership_with_participation_clause|
|regimeType|separate_ownership_with_community_addition|
|regimeType|conventional_community|
|regimeType|full_community|
|adoption|none|
|adoption|simple|
|adoption|full|

<h2 id="tocSgroupmembership">GroupMembership</h2>

<a id="schemagroupmembership"></a>

```json
{
  "id": "Yu1234ac",
  "type": "groupMembership",
  "attributes": {
    "sex": "F",
    "status": "approved",
    "memberRight": "no_right",
    "dead": false,
    "fatherId": "1234acds3",
    "adoption": "none",
    "extendedMinority": true,
    "provisionalAdministration": true,
    "judicialProtection": false,
    "extrajudicialProtection": false,
    "dummyUserId": "Yu1234ac"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|same as dummyUserId below|
|type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|

<h2 id="tocSgroupmembershipwithdummyuser">GroupMembershipWithDummyUser</h2>

<a id="schemagroupmembershipwithdummyuser"></a>

```json
{
  "id": "dummy_user_id_Yu1234ac",
  "type": "groupMembership",
  "attributes": {
    "coHolder": false,
    "dead": false,
    "fatherId": "dummy_user_id_1234acds3",
    "motherId": "dummy_user_id_dg7s6cdw5f",
    "currentSpouseId": "dummy_user_id_bcsudg6w3",
    "dummyUser": {
      "id": "dummy_user_id_Yu1234ac",
      "firstName": "Luc",
      "lastName": "Beson",
      "gender": "F",
      "birthday": "1970-02-20",
      "nationality": "BE",
      "countryCode": "FR",
      "zipcode": "75008"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|dummyUserId of the family member|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» coHolder|boolean|false|none|Is the person a main data subject of the group|
|» dead|boolean|false|none|Is the person deceased?|
|» fatherId|string|false|none|Internal reference to the father, must be an id of an existing dummy user|
|» motherId|string|false|none|internal reference to the mother, must be an id of an existing dummy user|
|» currentSpouseId|string|false|none|internal reference to the partner, must be an id of an existing dummy user|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|

<h2 id="tocSgroupattributes">GroupAttributes</h2>

<a id="schemagroupattributes"></a>

```json
{
  "internalName": "Lucas Niets",
  "id": "acbdj6472",
  "clientId": "a675742",
  "state": "active",
  "companyAdvisorId": "987gfr"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal group id. Must be unique. Will be generated randomly if not provided|
|internalName|string|false|none|Internal client name, won't be visible to client|
|companyAdvisorId|string|true|none|Id of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|clientId|string|true|none|Id of the 'main' client. Must be an existing dummy user.|
|state|string|false|none|state of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<h2 id="tocSgroup">Group</h2>

<a id="schemagroup"></a>

```json
{
  "id": "acbdj6472",
  "type": "group",
  "attributes": {
    "internalName": "Lucas Niets",
    "id": "acbdj6472",
    "clientId": "a675742",
    "companyAdvisorId": "987gfr"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|

<h2 id="tocSinsuranceobject">InsuranceObject</h2>

<a id="schemainsuranceobject"></a>

```json
{
  "id": "16243hudy",
  "type": "insurance",
  "attributes": {
    "id": "16243hudy",
    "name": "Present to Family",
    "reference": "123drfcvb",
    "startDate": "1970-02-20",
    "currency": "EUR",
    "acquiredReserve": 5003,
    "countryCode": "BE",
    "endDate": "Wed 17 Jul 2019",
    "apiOnly": false,
    "insuranceType": "other_insurance",
    "noTerm": false,
    "fixedTerm": false,
    "situationDate": "2019-01-01",
    "onlyDeathCover": false,
    "deathPayout": "reserve",
    "deathValue": 0,
    "acquiredLifeValue": 5003,
    "reduced": false,
    "premiumsPaid": 0,
    "premiumPeriodicity": "annual",
    "premiumEndDate": "Wed 17 Jul 2019",
    "premium": 0,
    "lifeValue": 5003,
    "enumPolicyholder": "other",
    "policyholderIds": [
      "18273gdh",
      "0",
      "0"
    ],
    "enumInsuredParty": "policyholders",
    "beneficiaryIsCompany": false,
    "enumLifeBeneficiary": "policyholders",
    "enumDeathBeneficiary": "succession",
    "lifeBeneficiaryIds": [
      "0",
      "123df",
      "0"
    ],
    "deathBeneficiaryIds": [
      "0"
    ],
    "insuranceCompanyName": "Big Co Ltd",
    "category": "protection",
    "managerName": "Dr. Mixalot O'Gin",
    "bankName": "Greendwalds Bank",
    "listedRealEstateShare": 0,
    "equityShare": 0,
    "privateEquityShare": 0,
    "bondsShare": 0,
    "cashShare": 100,
    "otherShare": 0,
    "swiftCode": "GEBABEBB00"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|false|none|Internal id to the insurance, must be unique in the group scope. Will be generated randomly if not provided|
|» apiOnly|string|false|none|can only be edited through the api endpoint|
|» name|string|false|none|Custom name of the policy/insurance. If left empty will be constructed from the reference|
|» reference|string|true|none|Reference of the policy|
|» insuranceType|string|true|none|type of insurance contract|
|» startDate|string|true|none|Start date of the contract. YYYY-MM-DD|
|» noTerm|boolean|false|none|Is the contract without term?|
|» endDate|string|true|none|End date of the contract. Required if no_term is false. Ignored if no_term is true. YYYY-MM-DD|
|» fixedTerm|boolean|false|none|Is it a fixed term contract? Ignored if no_term is true.|
|» situationDate|string|false|none|Date at which the amounts where calculated. Defaults to the begining of the current year. YYYY-MM-DD|
|» currency|string|false|none|Currency of the value(s)|
|» onlyDeathCover|boolean|false|none|Does the contract only include death insurance, ie. no capital is paid in case of life at term.|
|» acquiredReserve|number|true|none|Acquired reserve / current contract value. Ignored if onlyDeathCover is true. Decimals must be separated by a dot. Eg. 200000.55|
|» deathPayout|string|false|none|Payout in case of death. Degressive is assumed linear over the contract duration, fixed_amount if onlyDeathCover, reserve otherwise|
|» deathValue|number|false|none|Death cover amount. Only if deathPayout is 'fixed_amount' or 'degressive'.|
|» acquiredLifeValue|number|false|none|Acquired value in case of life at term (assuming no additional premiums are paid). Ignored if onlyDeathCover is true. Defaults to same as acquiredReserve|
|» reduced|boolean|false|none|answer 'true' if the contract was reduced or the premium was unique|
|» premiumsPaid|number|false|none|Premiums paid up to the situation date (net of taxes, fees...).|
|» premiumPeriodicity|string|false|none|Periodicity of the premiums. Ignored if reduced is 'true'|
|» premiumEndDate|string|false|none|Date until premiums are to be paid. Ignored if reduced is 'true'. Default contract end_date if any YYYY-MM-DD|
|» premium|number|false|none|Periodic premium expected to be paid. Ignored if reduced is 'true'|
|» lifeValue|number|false|none|Expected capital in case of life at term (including additional premiums). Ignored if only_death_cover is true. Default to acquiredLifeValue if reduced.|
|» enumPolicyholder|string|true|none|Is the policyholder a company or a physical person (other)|
|» employerId|string|false|none|Id of the company (group asset) in case the policyholder is a company. eg. group insurance. Ignored if enumPolicyholder is 'other'.|
|» employerName|string|false|none|Name of the employer in case the policyholder is a company. eg. group insurance. Ignored if enumPolicyholder is 'other'.|
|» policyholderIds|[string]|false|none|Ignored if enumPolicyholder is 'company'. Will assume each borrower holds an equivalent share of the policy.|
|» enumInsuredParty|string|false|none|Is the insured the 'policyholders' or other designated person(s)?|
|» insuredPartyIds|[string]|false|none|Ignored if enumInsuredParty is 'policyholders'.|
|» beneficiaryIsCompany|boolean|false|none|In case a company is the policyholder, is the company the beneficiary of the contract? Ignored unless enumPolicyholder is 'company'|
|» enumLifeBeneficiary|string|false|none|Who is(are) the life beneficiary(ies)? Ignored if company is 'beneficiaryIsCompany'|
|» lifeBeneficiaryIds|[string]|false|none|Ignored if enumLifeBeneficiary is not 'other'.|
|» enumDeathBeneficiary|string|false|none|Who is(are) the death beneficiary(ies)? Ignored if company is 'beneficiaryIsCompany'|
|» deathBeneficiaryIds|[string]|false|none|Ignored if enumDeathBeneficiary is not 'other'.|
|» insuranceCompanyName|string|true|none|The name of the insurance company. Use existing company id in PaxFamilia to ensure consistency?.|
|» ecbCode|string|false|none|ECB code of the insurance company. If not provided, insurance company will be created from the insuranceCompanyName but accounts won't therefore be linked to proper insurance info and reconciliation and aggregation will therefore be more complicated.|
|» countryCode|string|false|none|Country of the policy.|
|» category|string|false|none|category/type of insurance|
|» managerName|string|false|none|Name of the asset manager|
|» swiftCode|string|false|none|Swift code of the depository bank, eg. 'GEBABEBB'. If not provided, bank will be created from the bankName but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated.|
|» bankName|string|false|none|The name of the depository bank. The name of the bank will be derived from its swiftCode if a valid one is provided.|
|» listedRealEstateUnderlyingShare|number|false|none|Underlying portfolio asset composition - listed real estate share|
|» equityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in listed companies share|
|» privateEquityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in non listed companies share|
|» bondsUnderlyingShare|number|false|none|Underlying portfolio asset composition - investment in bonds share|
|» cashUnderlyingShare|number|false|none|Underlying portfolio asset composition - cash / liquidity share|
|» otherUnderlyingShare|number|false|none|Underlying portfolio asset composition - other / alternative share|

#### Enumerated Values

|Property|Value|
|---|---|
|type|insurance|
|insuranceType|EP|
|insuranceType|PLCI|
|insuranceType|AG|
|insuranceType|EIP|
|insuranceType|ELT|
|insuranceType|branch21|
|insuranceType|branch23|
|insuranceType|branch44|
|insuranceType|branch26|
|insuranceType|other_insurance|
|currency|AED|
|currency|AFN|
|currency|ALL|
|currency|AMD|
|currency|ANG|
|currency|AOA|
|currency|ARS|
|currency|AUD|
|currency|AWG|
|currency|AZN|
|currency|BAM|
|currency|BBD|
|currency|BDT|
|currency|BGN|
|currency|BHD|
|currency|BIF|
|currency|BMD|
|currency|BND|
|currency|BOB|
|currency|BRL|
|currency|BSD|
|currency|BTN|
|currency|BWP|
|currency|BYN|
|currency|BYR|
|currency|BZD|
|currency|CAD|
|currency|CDF|
|currency|CHF|
|currency|CLF|
|currency|CLP|
|currency|CNY|
|currency|COP|
|currency|CRC|
|currency|CUC|
|currency|CUP|
|currency|CVE|
|currency|CZK|
|currency|DJF|
|currency|DKK|
|currency|DOP|
|currency|DZD|
|currency|EGP|
|currency|ERN|
|currency|ETB|
|currency|EUR|
|currency|FJD|
|currency|FKP|
|currency|GBP|
|currency|GEL|
|currency|GHS|
|currency|GIP|
|currency|GMD|
|currency|GNF|
|currency|GTQ|
|currency|GYD|
|currency|HKD|
|currency|HNL|
|currency|HRK|
|currency|HTG|
|currency|HUF|
|currency|IDR|
|currency|ILS|
|currency|INR|
|currency|IQD|
|currency|IRR|
|currency|ISK|
|currency|JMD|
|currency|JOD|
|currency|JPY|
|currency|KES|
|currency|KGS|
|currency|KHR|
|currency|KMF|
|currency|KPW|
|currency|KRW|
|currency|KWD|
|currency|KYD|
|currency|KZT|
|currency|LAK|
|currency|LBP|
|currency|LKR|
|currency|LRD|
|currency|LSL|
|currency|LTL|
|currency|LVL|
|currency|LYD|
|currency|MAD|
|currency|MDL|
|currency|MGA|
|currency|MKD|
|currency|MMK|
|currency|MNT|
|currency|MOP|
|currency|MRO|
|currency|MUR|
|currency|MVR|
|currency|MWK|
|currency|MXN|
|currency|MYR|
|currency|MZN|
|currency|NAD|
|currency|NGN|
|currency|NIO|
|currency|NOK|
|currency|NPR|
|currency|NZD|
|currency|OMR|
|currency|PAB|
|currency|PEN|
|currency|PGK|
|currency|PHP|
|currency|PKR|
|currency|PLN|
|currency|PYG|
|currency|QAR|
|currency|RON|
|currency|RSD|
|currency|RUB|
|currency|RWF|
|currency|SAR|
|currency|SBD|
|currency|SCR|
|currency|SDG|
|currency|SEK|
|currency|SGD|
|currency|SHP|
|currency|SKK|
|currency|SLL|
|currency|SOS|
|currency|SRD|
|currency|SSP|
|currency|STD|
|currency|SVC|
|currency|SYP|
|currency|SZL|
|currency|THB|
|currency|TJS|
|currency|TMT|
|currency|TND|
|currency|TOP|
|currency|TRY|
|currency|TTD|
|currency|TWD|
|currency|TZS|
|currency|UAH|
|currency|UGX|
|currency|USD|
|currency|UYU|
|currency|UZS|
|currency|VEF|
|currency|VND|
|currency|VUV|
|currency|WST|
|currency|XAF|
|currency|XAG|
|currency|XAU|
|currency|XBA|
|currency|XBB|
|currency|XBC|
|currency|XBD|
|currency|XCD|
|currency|XDR|
|currency|XOF|
|currency|XPD|
|currency|XPF|
|currency|XPT|
|currency|XTS|
|currency|YER|
|currency|ZAR|
|currency|ZMK|
|currency|ZMW|
|currency|BTC|
|currency|JEP|
|currency|GGP|
|currency|IMP|
|currency|XFU|
|currency|GBX|
|currency|CNH|
|currency|EEK|
|currency|MTL|
|currency|TMM|
|currency|ZWD|
|currency|ZWL|
|currency|ZWN|
|currency|ZWR|
|deathPayout|premium|
|deathPayout|reserve|
|deathPayout|fixed_amount|
|deathPayout|degressive|
|deathPayout|none|
|premiumPeriodicity|monthly|
|premiumPeriodicity|quarterly|
|premiumPeriodicity|semi_annual|
|premiumPeriodicity|annual|
|enumPolicyholder|company|
|enumPolicyholder|other|
|enumInsuredParty|policyholders|
|enumInsuredParty|other|
|enumLifeBeneficiary|policyholders|
|enumLifeBeneficiary|insured_parties|
|enumLifeBeneficiary|partner|
|enumLifeBeneficiary|children|
|enumLifeBeneficiary|parents|
|enumLifeBeneficiary|siblings|
|enumLifeBeneficiary|grand_children:|
|enumLifeBeneficiary|nephews|
|enumLifeBeneficiary|other|
|enumDeathBeneficiary|succession|
|enumDeathBeneficiary|legal_heirs|
|enumDeathBeneficiary|partner|
|enumDeathBeneficiary|children|
|enumDeathBeneficiary|parents|
|enumDeathBeneficiary|siblings|
|enumDeathBeneficiary|grand_children|
|enumDeathBeneficiary|nephews|
|enumDeathBeneficiary|foundation|
|enumDeathBeneficiary|bank|
|enumDeathBeneficiary|other|
|countryCode|TJ|
|countryCode|JM|
|countryCode|HT|
|countryCode|ST|
|countryCode|MS|
|countryCode|AE|
|countryCode|PK|
|countryCode|NL|
|countryCode|LU|
|countryCode|BZ|
|countryCode|IR|
|countryCode|BO|
|countryCode|UY|
|countryCode|GH|
|countryCode|SA|
|countryCode|CI|
|countryCode|MF|
|countryCode|TF|
|countryCode|AI|
|countryCode|QA|
|countryCode|SX|
|countryCode|LY|
|countryCode|BV|
|countryCode|PG|
|countryCode|KG|
|countryCode|GQ|
|countryCode|EH|
|countryCode|NU|
|countryCode|PR|
|countryCode|GD|
|countryCode|KR|
|countryCode|HM|
|countryCode|SM|
|countryCode|SL|
|countryCode|CD|
|countryCode|MK|
|countryCode|TR|
|countryCode|DZ|
|countryCode|GE|
|countryCode|PS|
|countryCode|BB|
|countryCode|UA|
|countryCode|GP|
|countryCode|PF|
|countryCode|NA|
|countryCode|BW|
|countryCode|SY|
|countryCode|TG|
|countryCode|DO|
|countryCode|AQ|
|countryCode|CH|
|countryCode|MG|
|countryCode|FO|
|countryCode|VG|
|countryCode|GI|
|countryCode|BN|
|countryCode|LA|
|countryCode|IS|
|countryCode|EE|
|countryCode|UM|
|countryCode|LT|
|countryCode|RS|
|countryCode|MR|
|countryCode|AD|
|countryCode|HU|
|countryCode|TK|
|countryCode|MY|
|countryCode|AO|
|countryCode|CV|
|countryCode|NF|
|countryCode|PA|
|countryCode|GW|
|countryCode|BE|
|countryCode|PT|
|countryCode|GB|
|countryCode|IM|
|countryCode|US|
|countryCode|YE|
|countryCode|HK|
|countryCode|AZ|
|countryCode|CC|
|countryCode|ML|
|countryCode|SK|
|countryCode|VU|
|countryCode|TL|
|countryCode|HR|
|countryCode|SR|
|countryCode|MU|
|countryCode|CZ|
|countryCode|PM|
|countryCode|LS|
|countryCode|WS|
|countryCode|KM|
|countryCode|IT|
|countryCode|BI|
|countryCode|WF|
|countryCode|GN|
|countryCode|SG|
|countryCode|CO|
|countryCode|CN|
|countryCode|AW|
|countryCode|MA|
|countryCode|FI|
|countryCode|VA|
|countryCode|ZW|
|countryCode|KY|
|countryCode|BH|
|countryCode|PY|
|countryCode|EC|
|countryCode|LR|
|countryCode|RU|
|countryCode|PL|
|countryCode|OM|
|countryCode|MT|
|countryCode|SS|
|countryCode|DE|
|countryCode|TM|
|countryCode|SJ|
|countryCode|MM|
|countryCode|TT|
|countryCode|IL|
|countryCode|BD|
|countryCode|NR|
|countryCode|LK|
|countryCode|UG|
|countryCode|NG|
|countryCode|BQ|
|countryCode|MX|
|countryCode|CW|
|countryCode|SI|
|countryCode|MN|
|countryCode|CA|
|countryCode|AX|
|countryCode|VN|
|countryCode|TW|
|countryCode|JP|
|countryCode|IO|
|countryCode|RO|
|countryCode|BG|
|countryCode|GU|
|countryCode|BR|
|countryCode|AM|
|countryCode|ZM|
|countryCode|DJ|
|countryCode|JE|
|countryCode|AT|
|countryCode|CM|
|countryCode|SE|
|countryCode|FJ|
|countryCode|KZ|
|countryCode|GL|
|countryCode|GY|
|countryCode|CX|
|countryCode|MW|
|countryCode|TN|
|countryCode|ZA|
|countryCode|TO|
|countryCode|CY|
|countryCode|MV|
|countryCode|PN|
|countryCode|RW|
|countryCode|NI|
|countryCode|KN|
|countryCode|BJ|
|countryCode|ET|
|countryCode|GM|
|countryCode|TZ|
|countryCode|VC|
|countryCode|FK|
|countryCode|SD|
|countryCode|MC|
|countryCode|AU|
|countryCode|CL|
|countryCode|DK|
|countryCode|FR|
|countryCode|TC|
|countryCode|CU|
|countryCode|AL|
|countryCode|MZ|
|countryCode|BS|
|countryCode|NE|
|countryCode|GT|
|countryCode|LI|
|countryCode|NP|
|countryCode|BF|
|countryCode|PW|
|countryCode|KW|
|countryCode|IN|
|countryCode|GA|
|countryCode|TV|
|countryCode|MO|
|countryCode|SH|
|countryCode|MD|
|countryCode|CK|
|countryCode|AR|
|countryCode|SC|
|countryCode|IE|
|countryCode|ES|
|countryCode|LB|
|countryCode|BM|
|countryCode|RE|
|countryCode|KI|
|countryCode|AG|
|countryCode|MQ|
|countryCode|SV|
|countryCode|JO|
|countryCode|TH|
|countryCode|SO|
|countryCode|MH|
|countryCode|CG|
|countryCode|KP|
|countryCode|GF|
|countryCode|BA|
|countryCode|YT|
|countryCode|GS|
|countryCode|KE|
|countryCode|PE|
|countryCode|BT|
|countryCode|SZ|
|countryCode|CR|
|countryCode|TD|
|countryCode|DM|
|countryCode|NC|
|countryCode|GR|
|countryCode|GG|
|countryCode|HN|
|countryCode|VI|
|countryCode|CF|
|countryCode|SN|
|countryCode|AF|
|countryCode|MP|
|countryCode|PH|
|countryCode|BY|
|countryCode|LV|
|countryCode|NO|
|countryCode|EG|
|countryCode|KH|
|countryCode|IQ|
|countryCode|LC|
|countryCode|NZ|
|countryCode|BL|
|countryCode|UZ|
|countryCode|ID|
|countryCode|ER|
|countryCode|VE|
|countryCode|FM|
|countryCode|SB|
|countryCode|ME|
|countryCode|AS|
|category|protection|
|category|investment|

<h2 id="tocScompanygroupaccess">CompanyGroupAccess</h2>

<a id="schemacompanygroupaccess"></a>

```json
{
  "id": "groupID567",
  "type": "group",
  "attributes": {
    "id": "groupID567",
    "companyAdvisorId": "advisorID345",
    "authorizedCompanyUserIds": [
      "employeeID743",
      "employeeID744",
      "employeeID745",
      "employeeID746",
      "employeeID747"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal ID of group|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» id|string|true|none|Internal ID of group|
|» companyAdvisorId|string|true|none|Internal ID of company advisor for this group. Must be an existing companyMembership.|
|» authorizedCompanyUserIds|[string]|true|none|Internal IDs of other company employees allowed access to the group. Must be existing companyMemberships.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|

<h2 id="tocSrefreshvalues">RefreshValues</h2>

<a id="schemarefreshvalues"></a>

```json
{
  "id": "12345h",
  "type": "estateAsset"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|none|
|type|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
|type|estateLiability|
|type|insurance|

<h2 id="tocSinsurance">insurance</h2>

<a id="schemainsurance"></a>

```json
{
  "id": "12345h",
  "type": "estateAsset",
  "attributes": {
    "id": "123dfer",
    "acquiredReserve": 2344,
    "acquiredLifeValue": 7386,
    "deathValue": 936842
  }
}

```

### Properties

*allOf - discriminator: RefreshValues.type*

*and*

<h2 id="tocSestateobjectidsfilter">EstateObjectIdsFilter</h2>

<a id="schemaestateobjectidsfilter"></a>

```json
{
  "apiOnly": true,
  "type": "estateAsset",
  "groupIds": [
    "groupID123",
    "groupID124",
    "groupID125",
    "groupID126"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|apiOnly|boolean|false|none|filter for 'api_only' true or not|
|type|string|true|none|filter for estate object type to search for|
|groupIds|[string]|false|none|group ids to filter for|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
|type|estateLiability|
|type|insurance|

<h2 id="tocSestateobjectidsbygroup">EstateObjectIdsByGroup</h2>

<a id="schemaestateobjectidsbygroup"></a>

```json
{
  "data": [
    {
      "groupId": "groupID123",
      "type": "estateLiability",
      "ids": [
        "liabilityID12",
        "liabilityID13",
        "liabilityID14"
      ]
    },
    {
      "groupId": "groupID124",
      "type": "estateLiability",
      "ids": [
        "liabilityID14",
        "liabilityID15",
        "liabilityID16"
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|[object]|true|none|none|
|» groupId|string|false|none|none|
|» type|string|false|none|none|
|» ids|[string]|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
|type|estateLiability|
|type|insurance|

<h2 id="tocSestatedeleteids">EstateDeleteIds</h2>

<a id="schemaestatedeleteids"></a>

```json
{
  "groupId": "groupID123",
  "type": "insurance",
  "ids": [
    "insuranceID123",
    "insuranceID124",
    "insuranceID125",
    "insuranceID126"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|groupId|string|true|none|none|
|type|string|true|none|type of estate objects to be deleted|
|ids|[string]|true|none|estate objects ids to be deleted|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
|type|estateLiability|
|type|insurance|

<h2 id="tocSdraft">Draft</h2>

<a id="schemadraft"></a>

```json
{
  "type": "draft",
  "attributes": {
    "dummyUsers": [
      {
        "id": "family_head_id_123",
        "firstName": "Luc",
        "lastName": "Beson",
        "gender": "M",
        "birthday": "1960-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      },
      {
        "id": "current_spouse_id_123",
        "firstName": "Madeleine",
        "lastName": "Beson",
        "gender": "F",
        "birthday": "1970-02-20",
        "nationality": "BE",
        "countryCode": "FR",
        "zipcode": "75008"
      }
    ],
    "group": {
      "internalName": "Lucas Niets Beson",
      "id": "group_id_123",
      "clientId": "family_head_id_123",
      "companyAdvisorId": "987gfr"
    },
    "groupMembership": {
      "sex": "F",
      "status": "approved",
      "memberRight": "no_right",
      "dead": false,
      "currentSpouseId": "family_head_id_123",
      "adoption": "none",
      "extendedMinority": true,
      "provisionalAdministration": true,
      "judicialProtection": false,
      "extrajudicialProtection": false,
      "dummyUserId": "current_spouse_id_123"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|true|none|none|
|attributes|object|true|none|none|
|» dummyUsers|[[DummyUserAttributes](#schemadummyuserattributes)]|true|none|DummyUser objects that represent the familyHead and optionally, the partner|

#### Enumerated Values

|Property|Value|
|---|---|
|type|draft|

<h2 id="tocSnewid">NewId</h2>

<a id="schemanewid"></a>

```json
{
  "data": {
    "id": "old_id_345",
    "type": "dummyUser",
    "newId": "new_id_345"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|object|true|none|none|
|» id|string|true|none|Internal ID of the resource to be updated|
|» type|string|true|none|Type of the resource to be updated|
|» newId|string|true|none|New ID of the resource to be updated to|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyUnit|
|type|companyMembership|
|type|dummyUser|
|type|group|
|type|estateAsset|
|type|estateLiability|
|type|insurance|
|type|donation|

<h2 id="tocSpaginationlinks">PaginationLinks</h2>

<a id="schemapaginationlinks"></a>

```json
{
  "self": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
  "first": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
  "prev": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
  "next": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
  "last": "http://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|self|string|true|none|Link to the current page of the collection|
|first|string|true|none|Link to the first page of the collection|
|prev|string|true|none|Link to the previous page of the collection|
|next|string|true|none|Link to the next page of the collection|
|last|string|true|none|Link to the last page of the collection|

<h2 id="tocSpaginationmeta">PaginationMeta</h2>

<a id="schemapaginationmeta"></a>

```json
{
  "totalPages": 5
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|totalPages|number|false|none|Total pages paginated|

<script type="application/ld+json">
{
  "@context": "http://schema.org/",
  "@type": "WebAPI",
  "description": "This is the first version of the PaxFamilia 'public' API. You can find out more about **PaxFamilia** at our [website](https://www.paxfamilia.com/). **(W.I.P.)**",
  "documentation": "https://www.paxfamilia.com/",
  "termsOfService": "https://www.paxfamilia.com/hubfs/Conditions%20g%C3%A9n%C3%A9rales/CGU_PaxFamilia_B2B_V3_clean%2026112018.pdf?hsLang=fr-fr",

  "name": "Falcon Alpha Phoenix"
}
</script>

