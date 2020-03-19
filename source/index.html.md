---
title: Falcon Alpha Phoenix
language_tabs:
  - shell: cURL
  - ruby: Ruby
  - javascript--nodejs: JavaScript
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

This is the first version of the **PaxFamilia API**. You can find out more about **PaxFamilia** at our [website](https://www.paxfamilia.com/).

Base URLs:

* <a href="https://subdomain.api.paxfamilia.com/v1">https://subdomain.api.paxfamilia.com/v1</a>

<a href="https://www.paxfamilia.com/hubfs/Conditions%20g%C3%A9n%C3%A9rales/CGU_PaxFamilia_B2B_V3_clean%2026112018.pdf?hsLang=fr-fr">Terms of service</a>
Email: <a href="mailto:msousa@paxfamilia.com">Support</a>
 License: Copyright - Do Not Distribute

# Authentication

* API Key (ApiKey)
    - Parameter Name: **X-Api-Key**, in: header. . **1** After activating the Public API for your company's subdomain ask your company admin to generate an `Api-Key` in the [user profile section](/en/management/company_commercial_name/user_profile) and keep it safely. **ATTENTION:** this `Api-Key` will be hidden after this and it is the responsibility of your company to keep it safe, losing it will incur an identity scrutinization process to get a new one. **NOTE** PaxFamilia reserves the right to invalidate this `Api-key` in case of gross missuse or any kind of suspicious activity / server overload.

* API Key (JsonWebToken)
    - Parameter Name: **Authorization**, in: header. . **2** Use the User Session (/users/login) resource to generate a `Jason Web Token` with *email* + *password* + *api-key* in the body params. The email and password must be of a company employee account to which the admin_right `:api_user` has been given, to do so the company admin must edit that employee's account. This will return a `JWT` in the response header and body which is valid for 2hrs. . **3** Every call to the remaining resources in this API must be done with that `JWT` in the *'Authorization'* header and the `Api-Key` in the *'X-Api-Key'* header.

<h1 id="falcon-alpha-phoenix-api-logs">Api Logs</h1>

## getApiLogs

<a id="opIdgetApiLogs"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/api-logs \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/api-logs',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/api-logs',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/api-logs", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/api-logs");
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

*Retrieves the list of api logs*

<h3 id="getapilogs-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|Page object query with number and size in the format `page%5Bnumber%5D=1&page%5Bsize%5D=50` which would be `page[number]=1&page[size]=50` before encoding the square brackets.|

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
    "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="getapilogs-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Api logs found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<h3 id="getapilogs-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[ApiLog](#schemaapilog)]|true|none|none|
|»» id|string|true|none|Api log ID|
|»» type|string|true|none|Resource type - `apiLog`|
|»» attributes|object|true|none|none|
|»»» id|string|false|none|Api log ID|
|»»» companyMembershipId|string|false|none|Employee public id if their is an employee associated to this log|
|»»» success|boolean|true|none|Request success or failure|
|»»» status|string|false|none|Request status HTTP code in word form|
|»»» description|string|false|none|Any valid description needed, for **success** usually amount saved, for **failure** usually error message|
|»»» groupPublicId|string|false|none|Group public id associated to the log when it is a group scoped resource, such as: `estateAsset`, `estateLiability`|
|»»» resourceId|string|false|none|Public id of the resource in question when in the case of a specific resource error|
|»»» controller|string|false|none|Resource controller from which the log originated|
|»»» action|string|false|none|Resource action from which the log originated|
|»»» requestMethod|string|false|none|HTTP request method|
|»» links|[PaginationLinks](#schemapaginationlinks)|false|none|none|
|»»» self|string|true|none|Link to the current page of the collection.|
|»»» first|string|true|none|Link to the first page of the collection.|
|»»» prev|string|true|none|Link to the previous page of the collection.|
|»»» next|string|true|none|Link to the next page of the collection.|
|»»» last|string|true|none|Link to the last page of the collection.|
|»» meta|[PaginationMeta](#schemapaginationmeta)|false|none|none|
|»»» totalPages|number|false|none|Total pages paginated|

#### Enumerated Values

|Property|Value|
|---|---|
|type|apiLog|
|requestMethod|POST|
|requestMethod|PATCH|
|requestMethod|DELETE|
|requestMethod|GET|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-lifecycle">Lifecycle</h1>

## addDraft

<a id="opIdaddDraft"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/draft \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/draft',
  params: {
  }, headers: headers

p JSON.parse(result)

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
        "locale": "nl",
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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/draft',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/draft", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/draft");
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

*Creates one `Group` with its `DummyUsers` and current spouse `GroupMembership`*

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
        "locale": "nl",
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

<h3 id="adddraft-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[Draft](#schemadraft)|true|none|
|» type|body|string|true|Resource type, not the same as `group` to not confuse with that one, this includes `group`, `groupMembership` and `dummyUser` as a whole|
|» attributes|body|object|true|none|
|»» dummyUsers|body|[[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)]|true|DummyUser objects that represent the `familyHead` and optionally, the `partner`|
|»»» id|body|string|false|Internal client/person id. Will be generated randomly if not provided|
|»»» lastName|body|string|true|Last name of the client.|
|»»» firstName|body|string|true|First name of the client.|
|»»» email|body|string|false|Email of the client. Optional.|
|»»» gender|body|string|true|Gender of the client.|
|»»» birthday|body|string|false|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»»» nationality|body|string|true|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» countryCode|body|string|true|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» zipcode|body|string|false|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|
|»» group|body|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|
|»»» id|body|string|true|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|body|string|false|Internal client name, won't be visible to client|
|»»» companyAdvisorId|body|string|true|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|body|string|true|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|body|string|false|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|body|string|false|State of the group|
|»» groupMembership|body|[GroupMembership/properties/attributes](#schemagroupmembership/properties/attributes)|false|none|
|»»» dummyUserId|body|string|true|Id of an existing dummy user.|
|»»» coHolder|body|boolean|false|Is the person a main data subject of the group|
|»»» dead|body|boolean|false|Is the person deceased?|
|»»» fatherId|body|string|false|Internal reference to the father, must be an ID of an existing dummy user.|
|»»» motherId|body|string|false|Internal reference to the mother, must be an ID of an existing dummy user.|
|»»» currentSpouseId|body|string|false|Internal reference to the partner, must be an ID of an existing dummy user.|
|»»» spouseType|body|string|false|Type of partner relationship if current spouse exist.|
|»»» regimeType|body|string|false|Type of matrimonial regime if `spouseType` is spouse|
|»»» adoption|body|string|false|Type of adoption if any|
|»»» extendedMinority|body|boolean|false|Does the group membership have an extended minority?|
|»»» provisionalAdministration|body|boolean|false|Does the group membership have a provisional administration?|
|»»» judicialProtection|body|boolean|false|Does the group membership have a judicial protection?|
|»»» extrajudicialProtection|body|boolean|false|Does the group membership have an extrajudicial protection?|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|draft|
|»»» gender|M|
|»»» gender|F|
|»»» locale|fr|
|»»» locale|nl|
|»»» locale|en|
|»»» state|draft|
|»»» state|active|
|»»» state|suspended|
|»»» state|marked_for_deletion|
|»»» spouseType|spouse|
|»»» spouseType|legal_cohabitant|
|»»» spouseType|simple_cohabitant|
|»»» regimeType|legal_regime|
|»»» regimeType|separate_ownership|
|»»» regimeType|acquests_participation|
|»»» regimeType|separate_ownership_with_community_addition|
|»»» regimeType|conventional_community|
|»»» regimeType|full_community|
|»»» adoption|none|
|»»» adoption|simple|
|»»» adoption|full|

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
        "locale": "nl",
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

<h3 id="adddraft-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Draft created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="adddraft-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Draft](#schemadraft)|true|none|none|
|»» type|string|true|none|Resource type, not the same as `group` to not confuse with that one, this includes `group`, `groupMembership` and `dummyUser` as a whole|
|»» attributes|object|true|none|none|
|»»» dummyUsers|[[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)]|true|none|DummyUser objects that represent the `familyHead` and optionally, the `partner`|
|»»»» id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|»»»» lastName|string|true|none|Last name of the client.|
|»»»» firstName|string|true|none|First name of the client.|
|»»»» email|string|false|none|Email of the client. Optional.|
|»»»» gender|string|true|none|Gender of the client.|
|»»»» birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»»»» nationality|string|true|none|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»» countryCode|string|true|none|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»» zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|
|»»» group|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»»» state|string|false|none|State of the group|
|»»» groupMembership|[GroupMembership/properties/attributes](#schemagroupmembership/properties/attributes)|false|none|none|
|»»»» dummyUserId|string|true|none|Id of an existing dummy user.|
|»»»» coHolder|boolean|false|none|Is the person a main data subject of the group|
|»»»» dead|boolean|false|none|Is the person deceased?|
|»»»» fatherId|string|false|none|Internal reference to the father, must be an ID of an existing dummy user.|
|»»»» motherId|string|false|none|Internal reference to the mother, must be an ID of an existing dummy user.|
|»»»» currentSpouseId|string|false|none|Internal reference to the partner, must be an ID of an existing dummy user.|
|»»»» spouseType|string|false|none|Type of partner relationship if current spouse exist.|
|»»»» regimeType|string|false|none|Type of matrimonial regime if `spouseType` is spouse|
|»»»» adoption|string|false|none|Type of adoption if any|
|»»»» extendedMinority|boolean|false|none|Does the group membership have an extended minority?|
|»»»» provisionalAdministration|boolean|false|none|Does the group membership have a provisional administration?|
|»»»» judicialProtection|boolean|false|none|Does the group membership have a judicial protection?|
|»»»» extrajudicialProtection|boolean|false|none|Does the group membership have an extrajudicial protection?|

#### Enumerated Values

|Property|Value|
|---|---|
|type|draft|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|
|spouseType|spouse|
|spouseType|legal_cohabitant|
|spouseType|simple_cohabitant|
|regimeType|legal_regime|
|regimeType|separate_ownership|
|regimeType|acquests_participation|
|regimeType|separate_ownership_with_community_addition|
|regimeType|conventional_community|
|regimeType|full_community|
|adoption|none|
|adoption|simple|
|adoption|full|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## activateGroup

<a id="opIdactivateGroup"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/groups/{id}/activate \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/groups/{id}/activate',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{id}/activate',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/groups/{id}/activate", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{id}/activate");
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

*Activates Group*

<h3 id="activategroup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Internal ID of the group|

> Example responses

> 202 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "id": "acbdj6472",
      "internalName": "Lucas Niets",
      "state": "active",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="activategroup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Group Activated|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="activategroup-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Group](#schemagroup)|true|none|none|
|»» id|string|true|none|Internal group ID.|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|string|false|none|State of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## suspendGroup

<a id="opIdsuspendGroup"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/groups/{id}/suspend \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/groups/{id}/suspend',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{id}/suspend',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/groups/{id}/suspend", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{id}/suspend");
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

*Suspends Group*

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

<h3 id="suspendgroup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Internal ID of the group|
|data|body|object|true|none|
|» id|body|string|true|Internal ID of the group|
|» type|body|string|true|Resource type - `group`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal ID of the group|
|»» cause|body|string|true|Cause of the suspension|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|group|
|»» cause|divorce|
|»» cause|death|

> Example responses

> 202 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "id": "acbdj6472",
      "internalName": "Lucas Niets",
      "state": "active",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="suspendgroup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Group Suspended|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="suspendgroup-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Group](#schemagroup)|true|none|none|
|»» id|string|true|none|Internal group ID.|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|string|false|none|State of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## markGroupForDeletion

<a id="opIdmarkGroupForDeletion"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/groups/{id}/mark-for-deletion \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/groups/{id}/mark-for-deletion',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{id}/mark-for-deletion',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/groups/{id}/mark-for-deletion", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{id}/mark-for-deletion");
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

`PATCH /groups/{id}/mark-for-deletion`

*Marks Group for Deletion*

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

<h3 id="markgroupfordeletion-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|Internal ID of the group|
|data|body|object|true|none|
|» id|body|string|true|Internal ID of the group|
|» type|body|string|true|Resource type - `group`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal ID of the group|
|»» days|body|number|false|days until deletion|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|group|

> Example responses

> 202 Response

```json
{
  "data": {
    "id": "acbdj6472",
    "type": "group",
    "attributes": {
      "id": "acbdj6472",
      "internalName": "Lucas Niets",
      "state": "active",
      "clientId": "a675742",
      "companyAdvisorId": "987gfr"
    }
  }
}
```

<h3 id="markgroupfordeletion-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Group Marked for Deletion|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="markgroupfordeletion-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[Group](#schemagroup)|true|none|none|
|»» id|string|true|none|Internal group ID.|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|string|false|none|State of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-asset-ownerships">Asset Ownerships</h1>

## resetAssetOwnerships

<a id="opIdresetAssetOwnerships"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/asset-ownerships \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/asset-ownerships',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/asset-ownerships',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/asset-ownerships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/asset-ownerships");
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

*Resets one or more Asset Ownerships*

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

<h3 id="resetassetownerships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|Internal ID of the group|
|data|body|[object]|true|none|
|» id|body|string|true|Internal ID of the `estateAsset`|
|» type|body|string|true|Resource type - `estateAsset`|
|» attributes|body|object|true|none|
|»» assetOwnerships|body|[[AssetOwnership](#schemaassetownership)]|true|none|
|»»» type|body|string|true|Resource type - `assetOwnership`|
|»»» attributes|body|object|true|none|
|»»»» ownerId|body|string|true|Internal ID of the owner. If blank, will expect `companyId`.|
|»»»» companyId|body|string|false|Internal ID of the company that owns the asset. Ignored if `ownerId` is provided.|
|»»»» ownerCategory|body|string|false|Owner category. A physical person ('person'), the community ('community') or a moral person ('company')|
|»»»» communityOwner|body|string|false|Only in case of 'community `ownerCategory`'. Whether the asset is under both names or the main data subject or it's partner/spouse",|
|»»»» ownershipType|body|string|false|Type of the ownership. Full property ('fp'), bare ownership ('np') or usufruct ('us')|
|»»»» percentage|body|number|true|Percentage ownership. Decimals must be separated by a dot. Eg. 25.5|
|»»»» otherOwnerId|body|string|false|Internal ID of the owner holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp'.|
|»»»» otherCompanyId|body|string|false|Internal ID of the company holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp' and/or if `otherOwnerId` is provided.|
|»»»» usufructStartDate|body|string|false|YYYY-MM-DD. Start date of the usufruct. Only when a company owns the usufruct. Will default to current date|
|»»»» usufructPcValue|body|number|false|Initial percentage of the full property value. Only when a company owns the usufruct.|
|»»»» usufructYearsDuration|body|integer|false|Number of years the usufruct was initially granted to the company. Only when a company owns the usufruct.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|estateAsset|
|»»» type|assetOwnership|
|»»»» ownerCategory|person|
|»»»» ownerCategory|community|
|»»»» ownerCategory|company|
|»»»» communityOwner|both_names|
|»»»» communityOwner|owner_name|
|»»»» communityOwner|partner_name|
|»»»» ownershipType|fp|
|»»»» ownershipType|np|
|»»»» ownershipType|us|

> Example responses

> 201 Response

<h3 id="resetassetownerships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Asset Ownerships reset|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="resetassetownerships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[object]|true|none|none|
|»» id|string|true|none|Internal ID of the `estateAsset`.|
|»» type|string|true|none|Resource type - `estateAsset`.|
|»» attributes|object|true|none|none|
|»»» assetOwnerships|[[AssetOwnership](#schemaassetownership)]|true|none|Asset ownership objects for this `estateAsset`|
|»»»» type|string|true|none|Resource type - `assetOwnership`|
|»»»» attributes|object|true|none|none|
|»»»»» ownerId|string|true|none|Internal ID of the owner. If blank, will expect `companyId`.|
|»»»»» companyId|string|false|none|Internal ID of the company that owns the asset. Ignored if `ownerId` is provided.|
|»»»»» ownerCategory|string|false|none|Owner category. A physical person ('person'), the community ('community') or a moral person ('company')|
|»»»»» communityOwner|string|false|none|Only in case of 'community `ownerCategory`'. Whether the asset is under both names or the main data subject or it's partner/spouse",|
|»»»»» ownershipType|string|false|none|Type of the ownership. Full property ('fp'), bare ownership ('np') or usufruct ('us')|
|»»»»» percentage|number|true|none|Percentage ownership. Decimals must be separated by a dot. Eg. 25.5|
|»»»»» otherOwnerId|string|false|none|Internal ID of the owner holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp'.|
|»»»»» otherCompanyId|string|false|none|Internal ID of the company holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp' and/or if `otherOwnerId` is provided.|
|»»»»» usufructStartDate|string|false|none|YYYY-MM-DD. Start date of the usufruct. Only when a company owns the usufruct. Will default to current date|
|»»»»» usufructPcValue|number|false|none|Initial percentage of the full property value. Only when a company owns the usufruct.|
|»»»»» usufructYearsDuration|integer|false|none|Number of years the usufruct was initially granted to the company. Only when a company owns the usufruct.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-group-access">Company Group Access</h1>

## addCompanyGroupAccesses

<a id="opIdaddCompanyGroupAccesses"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/groups/confidentiality-rules \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/groups/confidentiality-rules',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/confidentiality-rules',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/groups/confidentiality-rules", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/confidentiality-rules");
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

*Creates one or more Company Group Access*

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

<h3 id="addcompanygroupaccesses-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[CompanyGroupAccess](#schemacompanygroupaccess)]|true|none|
|» id|body|string|true|Internal ID of group|
|» type|body|string|true|Resource type - `group`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal ID of group|
|»» companyAdvisorId|body|string|true|Internal ID of company advisor for this group. Must be an existing `companyMembership`.|
|»» authorizedCompanyUserIds|body|[string]|true|Internal IDs of other company employees allowed access to the group. Must be existing `companyMemberships`.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|group|

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

<h3 id="addcompanygroupaccesses-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Company Group Accesses updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addcompanygroupaccesses-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyGroupAccess](#schemacompanygroupaccess)]|true|none|none|
|»» id|string|true|none|Internal ID of group|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal ID of group|
|»»» companyAdvisorId|string|true|none|Internal ID of company advisor for this group. Must be an existing `companyMembership`.|
|»»» authorizedCompanyUserIds|[string]|true|none|Internal IDs of other company employees allowed access to the group. Must be existing `companyMemberships`.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-memberships">Company Memberships</h1>

## addCompanyMemberships

<a id="opIdaddCompanyMemberships"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/company-memberships \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/company-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/company-memberships',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/company-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-memberships");
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

*Creates one or more company memberships*

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

<h3 id="addcompanymemberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[CompanyMembership](#schemacompanymembership)]|true|none|
|» id|body|string|true|Internal employee id. Must be unique.|
|» type|body|string|true|Resource type - `companyMembership`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»» companyUnitId|body|string|false|Id of the unit, center or department the employee belongs to.|
|»» lastName|body|string|true|Last name of the employee|
|»» firstName|body|string|true|First name of the employee|
|»» gender|body|string|true|Gender of the employee|
|»» email|body|string|true|Email of the employee. used as username for login. needs to be unique.|
|»» mobilePhone|body|string|true|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»» countryCode|body|string|false|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» locale|body|string|true|Language used for the PaxFamilia application|
|»» memberRight|body|string|true|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|companyMembership|
|»» gender|M|
|»» gender|F|
|»» locale|fr|
|»» locale|nl|
|»» locale|en|
|»» memberRight|read_and_write|
|»» memberRight|read|

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

<h3 id="addcompanymemberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Company memberships created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addcompanymemberships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyMembership](#schemacompanymembership)]|true|none|none|
|»» id|string|true|none|Internal employee id. Must be unique.|
|»» type|string|true|none|Resource type - `companyMembership`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»»» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|»»» lastName|string|true|none|Last name of the employee|
|»»» firstName|string|true|none|First name of the employee|
|»»» gender|string|true|none|Gender of the employee|
|»»» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|»»» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»»» countryCode|string|false|none|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» locale|string|true|none|Language used for the PaxFamilia application|
|»»» memberRight|string|true|none|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
|memberRight|read_and_write|
|memberRight|read|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getCompanyMemberships

<a id="opIdgetCompanyMemberships"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/company-memberships \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/company-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/company-memberships',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/company-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-memberships");
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

*Retrieves the list of company memberships*

<h3 id="getcompanymemberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|Page object query with number and size in the format `page%5Bnumber%5D=1&page%5Bsize%5D=50` which would be `page[number]=1&page[size]=50` before encoding the square brackets.|

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
    "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="getcompanymemberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Company memberships found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<h3 id="getcompanymemberships-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyMembership](#schemacompanymembership)]|true|none|none|
|»» id|string|true|none|Internal employee id. Must be unique.|
|»» type|string|true|none|Resource type - `companyMembership`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»»» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|»»» lastName|string|true|none|Last name of the employee|
|»»» firstName|string|true|none|First name of the employee|
|»»» gender|string|true|none|Gender of the employee|
|»»» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|»»» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»»» countryCode|string|false|none|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» locale|string|true|none|Language used for the PaxFamilia application|
|»»» memberRight|string|true|none|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|
|»» links|[PaginationLinks](#schemapaginationlinks)|false|none|none|
|»»» self|string|true|none|Link to the current page of the collection.|
|»»» first|string|true|none|Link to the first page of the collection.|
|»»» prev|string|true|none|Link to the previous page of the collection.|
|»»» next|string|true|none|Link to the next page of the collection.|
|»»» last|string|true|none|Link to the last page of the collection.|
|»» meta|[PaginationMeta](#schemapaginationmeta)|false|none|none|
|»»» totalPages|number|false|none|Total pages paginated|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
|memberRight|read_and_write|
|memberRight|read|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## findCompanyMembershipById

<a id="opIdfindCompanyMembershipById"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/company-memberships/{id} \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}");
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

*Updates a company membership*

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

<h3 id="findcompanymembershipbyid-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|ID of the company membership|
|data|body|[CompanyMembership](#schemacompanymembership)|true|none|
|» id|body|string|true|Internal employee id. Must be unique.|
|» type|body|string|true|Resource type - `companyMembership`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»» companyUnitId|body|string|false|Id of the unit, center or department the employee belongs to.|
|»» lastName|body|string|true|Last name of the employee|
|»» firstName|body|string|true|First name of the employee|
|»» gender|body|string|true|Gender of the employee|
|»» email|body|string|true|Email of the employee. used as username for login. needs to be unique.|
|»» mobilePhone|body|string|true|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»» countryCode|body|string|false|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» locale|body|string|true|Language used for the PaxFamilia application|
|»» memberRight|body|string|true|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|companyMembership|
|»» gender|M|
|»» gender|F|
|»» locale|fr|
|»» locale|nl|
|»» locale|en|
|»» memberRight|read_and_write|
|»» memberRight|read|

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

<h3 id="findcompanymembershipbyid-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Not valid company membership attributes|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="findcompanymembershipbyid-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[CompanyMembership](#schemacompanymembership)|true|none|none|
|»» id|string|true|none|Internal employee id. Must be unique.|
|»» type|string|true|none|Resource type - `companyMembership`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»»» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|»»» lastName|string|true|none|Last name of the employee|
|»»» firstName|string|true|none|First name of the employee|
|»»» gender|string|true|none|Gender of the employee|
|»»» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|»»» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»»» countryCode|string|false|none|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» locale|string|true|none|Language used for the PaxFamilia application|
|»»» memberRight|string|true|none|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
|memberRight|read_and_write|
|memberRight|read|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## deleteCompanyMembership

<a id="opIddeleteCompanyMembership"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://subdomain.api.paxfamilia.com/v1/company-memberships/{id} \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.delete 'https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}',
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
    req, err := http.NewRequest("DELETE", "https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-memberships/{id}");
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

*Destroys a company membership*

<h3 id="deletecompanymembership-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|ID of the company membership|

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

<h3 id="deletecompanymembership-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|company membership deleted|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="deletecompanymembership-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[CompanyMembership](#schemacompanymembership)|true|none|none|
|»» id|string|true|none|Internal employee id. Must be unique.|
|»» type|string|true|none|Resource type - `companyMembership`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|»»» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|»»» lastName|string|true|none|Last name of the employee|
|»»» firstName|string|true|none|First name of the employee|
|»»» gender|string|true|none|Gender of the employee|
|»»» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|»»» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|»»» countryCode|string|false|none|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» locale|string|true|none|Language used for the PaxFamilia application|
|»»» memberRight|string|true|none|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
|memberRight|read_and_write|
|memberRight|read|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-company-units">Company Units</h1>

## addCompanyUnits

<a id="opIdaddCompanyUnits"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/company-units \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/company-units',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/company-units',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/company-units", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-units");
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

*Creates one or more company units*

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

<h3 id="addcompanyunits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[CompanyUnit](#schemacompanyunit)]|true|none|
|» id|body|string|true|Internal id of the unit, center or department.|
|» type|body|string|true|Resource type - `companyUnit`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal id of the unit, center or department. Will be generated randomly if not provided|
|»» parentUnitId|body|string|false|A unit can be a sub unit of another unit (parentUnit).|
|»» name|body|string|true|Name the unit, center or department|
|»» countryCode|body|string|false|Country of the unit. Default to the country of the company it belongs to. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» address|body|string|false|Address of the unit|
|»» zipcode|body|string|false|Zipcode of the unit|
|»» locale|body|string|true|Language of the unit|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|companyUnit|
|»» locale|fr|
|»» locale|nl|

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

<h3 id="addcompanyunits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Company units created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addcompanyunits-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyUnit](#schemacompanyunit)]|true|none|none|
|»» id|string|true|none|Internal id of the unit, center or department.|
|»» type|string|true|none|Resource type - `companyUnit`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal id of the unit, center or department. Will be generated randomly if not provided|
|»»» parentUnitId|string|false|none|A unit can be a sub unit of another unit (parentUnit).|
|»»» name|string|true|none|Name the unit, center or department|
|»»» countryCode|string|false|none|Country of the unit. Default to the country of the company it belongs to. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» address|string|false|none|Address of the unit|
|»»» zipcode|string|false|none|Zipcode of the unit|
|»»» locale|string|true|none|Language of the unit|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyUnit|
|locale|fr|
|locale|nl|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getCompanyUnits

<a id="opIdgetCompanyUnits"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/company-units \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/company-units',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/company-units',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/company-units", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/company-units");
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

*Retrieves the list of company units*

<h3 id="getcompanyunits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|Page object query with number and size in the format `page%5Bnumber%5D=1&page%5Bsize%5D=50` which would be `page[number]=1&page[size]=50` before encoding the square brackets.|

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
    "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="getcompanyunits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Company units found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<h3 id="getcompanyunits-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[CompanyUnit](#schemacompanyunit)]|true|none|none|
|»» id|string|true|none|Internal id of the unit, center or department.|
|»» type|string|true|none|Resource type - `companyUnit`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal id of the unit, center or department. Will be generated randomly if not provided|
|»»» parentUnitId|string|false|none|A unit can be a sub unit of another unit (parentUnit).|
|»»» name|string|true|none|Name the unit, center or department|
|»»» countryCode|string|false|none|Country of the unit. Default to the country of the company it belongs to. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» address|string|false|none|Address of the unit|
|»»» zipcode|string|false|none|Zipcode of the unit|
|»»» locale|string|true|none|Language of the unit|
|»» links|[PaginationLinks](#schemapaginationlinks)|false|none|none|
|»»» self|string|true|none|Link to the current page of the collection.|
|»»» first|string|true|none|Link to the first page of the collection.|
|»»» prev|string|true|none|Link to the previous page of the collection.|
|»»» next|string|true|none|Link to the next page of the collection.|
|»»» last|string|true|none|Link to the last page of the collection.|
|»» meta|[PaginationMeta](#schemapaginationmeta)|false|none|none|
|»»» totalPages|number|false|none|Total pages paginated|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyUnit|
|locale|fr|
|locale|nl|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-donations">Donations</h1>

## addDonations

<a id="opIdaddDonations"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/donations \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/donations',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/donations',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/donations", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/donations");
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

*Creates one or more Donations*

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

<h3 id="adddonations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|ID of the group|
|data|body|[[Donation](#schemadonation)]|true|none|
|» id|body|string|true|Internal id of the donation.|
|» type|body|string|true|Resource type - `donation`|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal id of the donation. Must be unique. Will be generated randomly if not provided.|
|»» estateAssetId|body|string|false|Id of the asset it relates to.|
|»» name|body|string|true|Name or reference for the donation|
|»» transactionDate|body|string|true|Donation date. YYYY-MM-DD|
|»» donationType|body|string|true|Type of donation|
|»» amount|body|number|true|Total intrinsic value of the donation. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|»» currentValue|body|string|false|Current value of the donation. Defaults to `amount`|
|»» donorIds|body|[string]|true|Array of donor ids.|
|»» doneeIds|body|[string]|true|Array of donee ids.|
|»» calleeIds|body|[string]|false|Internal IDs of the callee(s). Only in case residuo clause is true.|
|»» ownershipType|body|string|true|Specify if the donation is not for the full ownership. Full property ('fp'), bare ownership ('np') or bare ownership with reserve of usufruct ('np_reserve_us').|
|»» inheritanceTreatment|body|string|false|Treatment at succession. `advance`:- advance on inheritance, `no_report`:- par preciput et hors part, `advance_with_no_report`:- advance on inheritance with no report in nature.|
|»» nonTransferabilityClause|body|string|false|Type of non transferability clause (inalienability) if any|
|»» nonTransferabilityDuration|body|integer|false|Number of years of inalienability. Required if `nonTransferabilityClause` is forYears|
|»» noCommunityCondition|body|boolean|false|Clause preventing to bring the given assets to a community|
|»» returnClause|body|string|false|Clause of conventional return|
|»» returnClauseOptional|body|boolean|false|Is the return clause optional?|
|»» annuityClause|body|boolean|false|Is there a charge/rent (Charge de rente)?|
|»» annuityAmount|body|number|false|Annual annuity amount. Required if `annuityClause` is *true*|
|»» annuityPc|body|number|false|Annual annuity indexation.|
|»» description|body|string|false|Description|
|»» registered|body|boolean|true|Is the donation registered?|
|»» contractForm|body|string|false|What contractual form did the donation take?|
|»» notaris|body|string|false|Name of the notaris|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|donation|
|»» donationType|movable|
|»» donationType|immovable|
|»» ownershipType|fp|
|»» ownershipType|np_reserve_us|
|»» ownershipType|np|
|»» inheritanceTreatment|advance|
|»» inheritanceTreatment|no_report|
|»» inheritanceTreatment|advance_with_no_report|
|»» inheritanceTreatment|dunno|
|»» nonTransferabilityClause|none|
|»» nonTransferabilityClause|for_years|
|»» nonTransferabilityClause|till_donor_death|
|»» returnClause|none|
|»» returnClause|yes_no_descendance|
|»» returnClause|yes_with_descendance|
|»» returnClause|dunno|
|»» contractForm|notarial_deed|
|»» contractForm|foreign_notarial_deed|
|»» contractForm|none|

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

<h3 id="adddonations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Donations created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="adddonations-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Donation](#schemadonation)]|true|none|none|
|»» id|string|true|none|Internal id of the donation.|
|»» type|string|true|none|Resource type - `donation`|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal id of the donation. Must be unique. Will be generated randomly if not provided.|
|»»» estateAssetId|string|false|none|Id of the asset it relates to.|
|»»» name|string|true|none|Name or reference for the donation|
|»»» transactionDate|string|true|none|Donation date. YYYY-MM-DD|
|»»» donationType|string|true|none|Type of donation|
|»»» amount|number|true|none|Total intrinsic value of the donation. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|»»» currentValue|string|false|none|Current value of the donation. Defaults to `amount`|
|»»» donorIds|[string]|true|none|Array of donor ids.|
|»»» doneeIds|[string]|true|none|Array of donee ids.|
|»»» calleeIds|[string]|false|none|Internal IDs of the callee(s). Only in case residuo clause is true.|
|»»» ownershipType|string|true|none|Specify if the donation is not for the full ownership. Full property ('fp'), bare ownership ('np') or bare ownership with reserve of usufruct ('np_reserve_us').|
|»»» inheritanceTreatment|string|false|none|Treatment at succession. `advance`:- advance on inheritance, `no_report`:- par preciput et hors part, `advance_with_no_report`:- advance on inheritance with no report in nature.|
|»»» nonTransferabilityClause|string|false|none|Type of non transferability clause (inalienability) if any|
|»»» nonTransferabilityDuration|integer|false|none|Number of years of inalienability. Required if `nonTransferabilityClause` is forYears|
|»»» noCommunityCondition|boolean|false|none|Clause preventing to bring the given assets to a community|
|»»» returnClause|string|false|none|Clause of conventional return|
|»»» returnClauseOptional|boolean|false|none|Is the return clause optional?|
|»»» annuityClause|boolean|false|none|Is there a charge/rent (Charge de rente)?|
|»»» annuityAmount|number|false|none|Annual annuity amount. Required if `annuityClause` is *true*|
|»»» annuityPc|number|false|none|Annual annuity indexation.|
|»»» description|string|false|none|Description|
|»»» registered|boolean|true|none|Is the donation registered?|
|»»» contractForm|string|false|none|What contractual form did the donation take?|
|»»» notaris|string|false|none|Name of the notaris|

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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-dummy-users">Dummy Users</h1>

## addDummyUsers

<a id="opIdaddDummyUsers"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/dummy-users \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/dummy-users',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/dummy-users',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/dummy-users", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/dummy-users");
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

*Creates one or more dummy users*

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

<h3 id="adddummyusers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[DummyUser](#schemadummyuser)]|true|none|
|» id|body|string|true|Internal client/person id.|
|» type|body|string|true|Resource type - `dummyUser`|
|» attributes|body|[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)|true|none|
|»» id|body|string|false|Internal client/person id. Will be generated randomly if not provided|
|»» lastName|body|string|true|Last name of the client.|
|»» firstName|body|string|true|First name of the client.|
|»» email|body|string|false|Email of the client. Optional.|
|»» gender|body|string|true|Gender of the client.|
|»» birthday|body|string|false|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»» nationality|body|string|true|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» countryCode|body|string|true|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» zipcode|body|string|false|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|dummyUser|
|»» gender|M|
|»» gender|F|

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

<h3 id="adddummyusers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Dummy users created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="adddummyusers-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[DummyUser](#schemadummyuser)]|true|none|none|
|»» id|string|true|none|Internal client/person id.|
|»» type|string|true|none|Resource type - `dummyUser`|
|»» attributes|[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)|true|none|none|
|»»» id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|»»» lastName|string|true|none|Last name of the client.|
|»»» firstName|string|true|none|First name of the client.|
|»»» email|string|false|none|Email of the client. Optional.|
|»»» gender|string|true|none|Gender of the client.|
|»»» birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»»» nationality|string|true|none|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» countryCode|string|true|none|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|

#### Enumerated Values

|Property|Value|
|---|---|
|type|dummyUser|
|gender|M|
|gender|F|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getDummyUsers

<a id="opIdgetDummyUsers"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/dummy-users \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/dummy-users',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/dummy-users',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/dummy-users", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/dummy-users");
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

*Retrieves the list of dummy users*

<h3 id="getdummyusers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|Page object query with number and size in the format `page%5Bnumber%5D=1&page%5Bsize%5D=50` which would be `page[number]=1&page[size]=50` before encoding the square brackets.|

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
    "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="getdummyusers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Dummy users found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<h3 id="getdummyusers-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[DummyUser](#schemadummyuser)]|true|none|none|
|»» id|string|true|none|Internal client/person id.|
|»» type|string|true|none|Resource type - `dummyUser`|
|»» attributes|[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)|true|none|none|
|»»» id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|»»» lastName|string|true|none|Last name of the client.|
|»»» firstName|string|true|none|First name of the client.|
|»»» email|string|false|none|Email of the client. Optional.|
|»»» gender|string|true|none|Gender of the client.|
|»»» birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»»» nationality|string|true|none|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» countryCode|string|true|none|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|
|»» links|[PaginationLinks](#schemapaginationlinks)|false|none|none|
|»»» self|string|true|none|Link to the current page of the collection.|
|»»» first|string|true|none|Link to the first page of the collection.|
|»»» prev|string|true|none|Link to the previous page of the collection.|
|»»» next|string|true|none|Link to the next page of the collection.|
|»»» last|string|true|none|Link to the last page of the collection.|
|»» meta|[PaginationMeta](#schemapaginationmeta)|false|none|none|
|»»» totalPages|number|false|none|Total pages paginated|

#### Enumerated Values

|Property|Value|
|---|---|
|type|dummyUser|
|gender|M|
|gender|F|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estate-assets">Estate Assets</h1>

## addEstateAssets

<a id="opIdaddEstateAssets"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-assets \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "string",
      "type": "estateAsset",
      "attributes": {
        "id": "345abcd",
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
        "rateOfReturn": 2,
        "category": "account"
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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-assets',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-assets", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-assets");
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

*Creates one or more Estate Assets*

'Endpoint to mass upload `EstateAssets`. These have five diferent categories: company, real estate, other asset, investment and account. Each is described in further detail in the Schemas section of this document, they are named respectively `EstateAssetCompany`, `EstateAssetRealEstate`, `EstateAssetOtherAsset`, `EstateAssetInvestment` and `EstateAssetAccount`. Each share `EstateAssetBaseAttributes` and then include specific extra properties of their own. Below the examples are demonstrated using the *account* category. Be aware that the endpoint accepts **any number** of the five categories non-exclusively, which means you can send more then one category at a time.'

> Body parameter

```json
{
  "data": [
    {
      "id": "string",
      "type": "estateAsset",
      "attributes": {
        "id": "345abcd",
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
        "rateOfReturn": 2,
        "category": "account"
      }
    }
  ]
}
```

<h3 id="addestateassets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|ID of the group|
|data|body|[object]|true|none|
|» id|body|string|false|ID of the estate asset|
|» type|body|string|false|Resource type - `estateAsset`|
|» attributes|body|any|false|none|
|»» *anonymous*|body|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|
|»»» id|body|string|false|Internal reference to asset, must be unique in the group scope. Will be generated randomly if not provided|
|»»» apiOnly|body|boolean|false|Can only be edited through the api endpoint|
|»»» name|body|string|false|Custom name of the asset. If left empty will be constructed from the address|
|»»» countryCode|body|string|false|Country where the asset is located. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» zipcode|body|string|false|Zipcode where the asset is located. Required for real estate in Belgium to calculate property tax from cadastral income|
|»»» currentValue|body|number|true|Current value of the asset|
|»»» currency|body|string|false|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»» situationDate|body|string|false|Date at which the amounts where calculated. Must be in the past. Defaults to the creation date. *YYYY-MM-DD*.|
|»»» defaultOwnershipType|body|string|false|Ownership of the asset. Owner refers to the 'main client', partner refers to the main client spouse or partner|
|»»» community|body|boolean|false|Is the asset owned by the community? If not specified, defaults according to the matrimonial regime|
|»» *anonymous*|body|object|false|none|
|»»» accountType|body|string|true|Type of account|
|»»» bankName|body|string|true|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|»»» iban|body|string|false|Account IBAN number.|
|»»» rateOfReturn|body|number|false|Expected annual value increase of the company.|
|»»» swiftCode|body|string|false|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated|
|»»» category|body|string|true|none|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|estateAsset|
|»»» defaultOwnershipType|owner|
|»»» defaultOwnershipType|partner|
|»»» defaultOwnershipType|common|
|»»» defaultOwnershipType|owner_np_children|
|»»» defaultOwnershipType|partner_np_children|
|»»» defaultOwnershipType|common_np_children|
|»»» defaultOwnershipType|owner_us_parent|
|»»» defaultOwnershipType|partner_us_parent|
|»»» defaultOwnershipType|other|
|»»» accountType|current_account|
|»»» accountType|saving_account|
|»»» accountType|term_account|
|»»» accountType|other_type|
|»»» category|account|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "string",
      "type": "estateAsset",
      "attributes": {
        "id": "345abcd",
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
        "rateOfReturn": 2,
        "category": "account"
      }
    }
  ]
}
```

<h3 id="addestateassets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Estate Assets created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addestateassets-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[object]|true|none|none|
|»» id|string|false|none|ID of the estate asset|
|»» type|string|false|none|Resource type - `estateAsset`|
|»» attributes|any|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|
|»»»» id|string|false|none|Internal reference to asset, must be unique in the group scope. Will be generated randomly if not provided|
|»»»» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|»»»» name|string|false|none|Custom name of the asset. If left empty will be constructed from the address|
|»»»» countryCode|string|false|none|Country where the asset is located. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»» zipcode|string|false|none|Zipcode where the asset is located. Required for real estate in Belgium to calculate property tax from cadastral income|
|»»»» currentValue|number|true|none|Current value of the asset|
|»»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»»» situationDate|string|false|none|Date at which the amounts where calculated. Must be in the past. Defaults to the creation date. *YYYY-MM-DD*.|
|»»»» defaultOwnershipType|string|false|none|Ownership of the asset. Owner refers to the 'main client', partner refers to the main client spouse or partner|
|»»»» community|boolean|false|none|Is the asset owned by the community? If not specified, defaults according to the matrimonial regime|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» *anonymous*|object|false|none|none|
|»»»» accountType|string|true|none|Type of account|
|»»»» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|»»»» iban|string|false|none|Account IBAN number.|
|»»»» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|»»»» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated|
|»»»» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|
|defaultOwnershipType|owner|
|defaultOwnershipType|partner|
|defaultOwnershipType|common|
|defaultOwnershipType|owner_np_children|
|defaultOwnershipType|partner_np_children|
|defaultOwnershipType|common_np_children|
|defaultOwnershipType|owner_us_parent|
|defaultOwnershipType|partner_us_parent|
|defaultOwnershipType|other|
|accountType|current_account|
|accountType|saving_account|
|accountType|term_account|
|accountType|other_type|
|category|account|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estate-liabilities">Estate Liabilities</h1>

## addEstateLiabilities

<a id="opIdaddEstateLiabilities"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-liabilities \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-liabilities',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "abcd1234",
      "type": "estateLiability",
      "attributes": {
        "id": "abcd1234",
        "name": "Birthday gift to my son's 30th",
        "countryCode": "BE",
        "currency": "EUR",
        "contractDate": "1970-02-20",
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
        "guarantee": true,
        "guaranteeType": "other_guarantee",
        "guaranteeAmount": 73810,
        "guarantorInternalId": "estate_asset_id_653",
        "prepaid": false,
        "prepaymentDate": "1987-08-16T00:00:00.000Z"
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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-liabilities',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-liabilities", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/estate-liabilities");
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

*Creates one or more Estate Liabilities*

> Body parameter

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
        "contractDate": "1970-02-20",
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
        "guarantee": true,
        "guaranteeType": "other_guarantee",
        "guaranteeAmount": 73810,
        "guarantorInternalId": "estate_asset_id_653",
        "prepaid": false,
        "prepaymentDate": "1987-08-16T00:00:00.000Z"
      }
    }
  ]
}
```

<h3 id="addestateliabilities-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|ID of the group|
|data|body|[[EstateLiability](#schemaestateliability)]|true|none|
|» id|body|string|true|Internal reference to the liability, must be unique in the group scope.|
|» type|body|string|true|Resource type - `estateLiability`|
|» attributes|body|object|true|none|
|»» id|body|string|false|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|»» apiOnly|body|boolean|false|Can only be edited through the api endpoint|
|»» name|body|string|true|Custom name of the liability. Can also be a reference.|
|»» liabilityType|body|string|true|Type of account|
|»» linkedToAsset|body|boolean|false|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|»» estateAssetId|body|string|false|Internal reference to asset. Will be ignored if `linkedToAsset` is false. Required if `linkedToAsset` is *true*.|
|»» swiftCode|body|string|false|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»» bankName|body|string|true|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»» countryCode|body|string|false|Country of the applicable law. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» initialAmount|body|number|true|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|»» contractDate|body|string|true|Contract signature date. Must be in the past. *YYYY-MM-DD*|
|»» currency|body|string|false|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»» repaymentType|body|string|true|Type of account|
|»» periodicity|body|string|true|Periodicity of the principal and/or interest payment|
|»» periodsDuration|body|integer|true|Number of repayment periods. Ignored if `repaymentType` has no end date (*no_end_pay_interest* or *no_end_capitalized_interest*)|
|»» rate|body|number|true|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|»» rateType|body|string|false|Fixed or variable interest rate|
|»» sameOwnershipAsAsset|body|boolean|false|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if `linkedToAsset` is set to *false*.|
|»» borrowers|body|[string]|false|"Ignored if `sameOwnershipAsAsset` is *true*, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan."|
|»» lenders|body|[string]|false|Ignored if `liabilityType` is *bank_loan*. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with an ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|»» balanceInsurance|body|boolean|false|Is the liability covered by a balance insurance (ASRD)?|
|»» balanceInsurancePc|body|number|false|Percentage of the loan covered by a balance insurance. Ignored if `balanceInsurance` is *false*|
|»» guarantee|body|boolean|false|Is the liability secured by a guarantee?|
|»» guaranteeType|body|string|false|Type of guarantee. Ignored unless `guarantee` is *true*.|
|»» guaranteeAmount|body|number|false|Amount of the guarantee. Will default to the `initialAmount`. Ignored unless `guarantee` is *true*.|
|»» guarantorInternalId|body|string|false|ID of the asset or person guaranteeing the liability. Will default to the `estateAssetId` if present. Ignored unless `guarantee` is *true*. ID needs to exists within PaxFamilia|
|»» prepaid|body|boolean|false|Has the loan been prepaid? (or is it expected to be prepaid at some future date?)|
|»» prepaymentDate|body|string|false|Prepayment date. Defaults to current date if prepaid is set to true, otherwise ignored. *YYYY-MM-DD*|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|estateLiability|
|»» liabilityType|bank_loan|
|»» liabilityType|private_loan|
|»» liabilityType|loan_account|
|»» liabilityType|other_type|
|»» repaymentType|constant_periodicity|
|»» repaymentType|constant_principal|
|»» repaymentType|bullet|
|»» repaymentType|no_end_pay_interest|
|»» repaymentType|no_end_capitalized_interest|
|»» repaymentType|bullet_capitalized_interest|
|»» periodicity|monthly|
|»» periodicity|quarterly|
|»» periodicity|semi_annual|
|»» periodicity|annual|
|»» rateType|fixed|
|»» rateType|variable|
|»» guaranteeType|mortgage,|
|»» guaranteeType|mortgage_mandate,|
|»» guaranteeType|personal_guarantee,|
|»» guaranteeType|pledge,|
|»» guaranteeType|other_guarantee|

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
        "contractDate": "1970-02-20",
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

<h3 id="addestateliabilities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Estate Liabilities created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addestateliabilities-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[EstateLiabilityWithGuarantees](#schemaestateliabilitywithguarantees)]|true|none|none|
|»» id|string|true|none|Internal reference to the liability, must be unique in the group scope.|
|»» type|string|true|none|Resource type - `estateLiability`|
|»» attributes|[EstateLiabilityWithGuarantees/properties/attributes](#schemaestateliabilitywithguarantees/properties/attributes)|true|none|none|
|»»» id|string|false|none|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|»»» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|»»» name|string|true|none|Custom name of the liability. Can also be a reference.|
|»»» liabilityType|string|true|none|Type of account|
|»»» linkedToAsset|boolean|false|none|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|»»» estateAssetId|string|false|none|Internal reference to asset. Will be ignored if `linkedToAsset` is false. Required if `linkedToAsset` is *true*.|
|»»» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»»» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»»» countryCode|string|false|none|Country of the applicable law. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» initialAmount|number|true|none|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|»»» contractDate|string|true|none|Contract signature date. *YYYY-MM-DD*|
|»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»» repaymentType|string|true|none|Type of account|
|»»» periodicity|string|true|none|Periodicity of the principal and/or interest payment|
|»»» periodsDuration|integer|true|none|Number of repayment periods. Ignored if `repaymentType` has no end date (*no_end_pay_interest* or *no_end_capitalized_interest*)|
|»»» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|»»» rateType|string|false|none|Fixed or variable interest rate|
|»»» sameOwnershipAsAsset|boolean|false|none|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if `linkedToAsset` is set to *false*.|
|»»» borrowers|[string]|false|none|"Ignored if `sameOwnershipAsAsset` is *true*, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan."|
|»»» lenders|[string]|false|none|Ignored if `liabilityType` is *bank_loan*. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with an ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|»»» balanceInsurance|boolean|false|none|Is the liability covered by a balance insurance (ASRD)?|
|»»» balanceInsurancePc|number|false|none|Percentage of the loan covered by a balance insurance. Ignored if `balanceInsurance` is *false*|
|»»» guarantees|[object]|false|none|none|
|»»»» amount|number|true|none|Amount of the guarantee. Will default to the `initialAmount`. Ignored unless `guarantee` is *true*.|
|»»»» guaranteeType|string|true|none|Type of guarantee. Ignored unless `guarantee` is *true*.|
|»»»» guarantorableId|string|true|none|ID of the asset or person guaranteeing the liability. Will default to the `estateAssetId` if present. Ignored unless `guarantee` is *true*. ID need to exists within PaxFamilia.|
|»»»» guarantorableType|string|true|none|Resource type of the guarantee, can be `GroupMembership` or `EstateAsset`.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|liabilityType|bank_loan|
|liabilityType|private_loan|
|liabilityType|loan_account|
|liabilityType|other_type|
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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-group-memberships">Group Memberships</h1>

## addGroupMemberships

<a id="opIdaddGroupMemberships"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/group-memberships \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/group-memberships',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "dummyUserId": "Yu1234ac",
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false
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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/group-memberships',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/group-memberships", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/group-memberships");
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

*Creates one or more Group Memberships*

> Body parameter

```json
{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "dummyUserId": "Yu1234ac",
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false
      }
    }
  ]
}
```

<h3 id="addgroupmemberships-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|ID of the group|
|data|body|[[GroupMembership](#schemagroupmembership)]|true|none|
|» id|body|string|true|Same as `dummyUserId` below|
|» type|body|string|true|Resource type - `groupMembership`|
|» attributes|body|[GroupMembership/properties/attributes](#schemagroupmembership/properties/attributes)|true|none|
|»» dummyUserId|body|string|true|Id of an existing dummy user.|
|»» coHolder|body|boolean|false|Is the person a main data subject of the group|
|»» dead|body|boolean|false|Is the person deceased?|
|»» fatherId|body|string|false|Internal reference to the father, must be an ID of an existing dummy user.|
|»» motherId|body|string|false|Internal reference to the mother, must be an ID of an existing dummy user.|
|»» currentSpouseId|body|string|false|Internal reference to the partner, must be an ID of an existing dummy user.|
|»» spouseType|body|string|false|Type of partner relationship if current spouse exist.|
|»» regimeType|body|string|false|Type of matrimonial regime if `spouseType` is spouse|
|»» adoption|body|string|false|Type of adoption if any|
|»» extendedMinority|body|boolean|false|Does the group membership have an extended minority?|
|»» provisionalAdministration|body|boolean|false|Does the group membership have a provisional administration?|
|»» judicialProtection|body|boolean|false|Does the group membership have a judicial protection?|
|»» extrajudicialProtection|body|boolean|false|Does the group membership have an extrajudicial protection?|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|groupMembership|
|»» spouseType|spouse|
|»» spouseType|legal_cohabitant|
|»» spouseType|simple_cohabitant|
|»» regimeType|legal_regime|
|»» regimeType|separate_ownership|
|»» regimeType|acquests_participation|
|»» regimeType|separate_ownership_with_community_addition|
|»» regimeType|conventional_community|
|»» regimeType|full_community|
|»» adoption|none|
|»» adoption|simple|
|»» adoption|full|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "Yu1234ac",
      "type": "groupMembership",
      "attributes": {
        "dummyUserId": "Yu1234ac",
        "sex": "F",
        "status": "approved",
        "memberRight": "no_right",
        "dead": false,
        "fatherId": "1234acds3",
        "adoption": "none",
        "extendedMinority": true,
        "provisionalAdministration": true,
        "judicialProtection": false,
        "extrajudicialProtection": false
      }
    }
  ]
}
```

<h3 id="addgroupmemberships-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Group Memberships created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addgroupmemberships-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[GroupMembership](#schemagroupmembership)]|true|none|none|
|»» id|string|true|none|Same as `dummyUserId` below|
|»» type|string|true|none|Resource type - `groupMembership`|
|»» attributes|[GroupMembership/properties/attributes](#schemagroupmembership/properties/attributes)|true|none|none|
|»»» dummyUserId|string|true|none|Id of an existing dummy user.|
|»»» coHolder|boolean|false|none|Is the person a main data subject of the group|
|»»» dead|boolean|false|none|Is the person deceased?|
|»»» fatherId|string|false|none|Internal reference to the father, must be an ID of an existing dummy user.|
|»»» motherId|string|false|none|Internal reference to the mother, must be an ID of an existing dummy user.|
|»»» currentSpouseId|string|false|none|Internal reference to the partner, must be an ID of an existing dummy user.|
|»»» spouseType|string|false|none|Type of partner relationship if current spouse exist.|
|»»» regimeType|string|false|none|Type of matrimonial regime if `spouseType` is spouse|
|»»» adoption|string|false|none|Type of adoption if any|
|»»» extendedMinority|boolean|false|none|Does the group membership have an extended minority?|
|»»» provisionalAdministration|boolean|false|none|Does the group membership have a provisional administration?|
|»»» judicialProtection|boolean|false|none|Does the group membership have a judicial protection?|
|»»» extrajudicialProtection|boolean|false|none|Does the group membership have an extrajudicial protection?|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|
|spouseType|spouse|
|spouseType|legal_cohabitant|
|spouseType|simple_cohabitant|
|regimeType|legal_regime|
|regimeType|separate_ownership|
|regimeType|acquests_participation|
|regimeType|separate_ownership_with_community_addition|
|regimeType|conventional_community|
|regimeType|full_community|
|adoption|none|
|adoption|simple|
|adoption|full|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-groups">Groups</h1>

## addGroups

<a id="opIdaddGroups"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "id": "acbdj6472",
        "internalName": "Lucas Niets",
        "state": "active",
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

fetch('https://subdomain.api.paxfamilia.com/v1/groups',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups");
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

*Creates one or more Groups*

> Body parameter

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "id": "acbdj6472",
        "internalName": "Lucas Niets",
        "state": "active",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ]
}
```

<h3 id="addgroups-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[Group](#schemagroup)]|true|none|
|» id|body|string|true|Internal group ID.|
|» type|body|string|true|Resource type - `group`|
|» attributes|body|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|
|»» id|body|string|true|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»» internalName|body|string|false|Internal client name, won't be visible to client|
|»» companyAdvisorId|body|string|true|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»» clientId|body|string|true|ID of the 'main' client. Must be an existing dummy user.|
|»» locale|body|string|false|Default language for the group. Defaults to the locale of the company advisor.|
|»» state|body|string|false|State of the group|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|group|
|»» locale|fr|
|»» locale|nl|
|»» locale|en|
|»» state|draft|
|»» state|active|
|»» state|suspended|
|»» state|marked_for_deletion|

> Example responses

> 201 Response

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "id": "acbdj6472",
        "internalName": "Lucas Niets",
        "state": "active",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ]
}
```

<h3 id="addgroups-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Groups created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addgroups-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Group](#schemagroup)]|true|none|none|
|»» id|string|true|none|Internal group ID.|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|string|false|none|State of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getGroups

<a id="opIdgetGroups"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/groups \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/groups',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/groups',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/groups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups");
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

*Retrieves the list of Groups*

<h3 id="getgroups-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|paginationQuery|query|string|false|Page object query with number and size in the format `page%5Bnumber%5D=1&page%5Bsize%5D=50` which would be `page[number]=1&page[size]=50` before encoding the square brackets.|

> Example responses

> 200 Response

```json
{
  "data": [
    {
      "id": "acbdj6472",
      "type": "group",
      "attributes": {
        "id": "acbdj6472",
        "internalName": "Lucas Niets",
        "state": "active",
        "clientId": "a675742",
        "companyAdvisorId": "987gfr"
      }
    }
  ],
  "links": {
    "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
    "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
    "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
    "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
    "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
  },
  "meta": {
    "totalPages": 5
  }
}
```

<h3 id="getgroups-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Groups found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<h3 id="getgroups-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Group](#schemagroup)]|true|none|none|
|»» id|string|true|none|Internal group ID.|
|»» type|string|true|none|Resource type - `group`|
|»» attributes|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|none|
|»»» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|»»» internalName|string|false|none|Internal client name, won't be visible to client|
|»»» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|»»» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|»»» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|»»» state|string|false|none|State of the group|
|»» links|[PaginationLinks](#schemapaginationlinks)|false|none|none|
|»»» self|string|true|none|Link to the current page of the collection.|
|»»» first|string|true|none|Link to the first page of the collection.|
|»»» prev|string|true|none|Link to the previous page of the collection.|
|»»» next|string|true|none|Link to the next page of the collection.|
|»»» last|string|true|none|Link to the last page of the collection.|
|»» meta|[PaginationMeta](#schemapaginationmeta)|false|none|none|
|»»» totalPages|number|false|none|Total pages paginated|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getGroupEstate

<a id="opIdgetGroupEstate"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/groups/{id}/estate \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/groups/{id}/estate',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{id}/estate',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/groups/{id}/estate", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{id}/estate");
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

*Get the Estate of one Group*

Retrieve the lists of 'Estate Assets', 'Estate Liabilities' and 'Insurances' of a 'Group'

<h3 id="getgroupestate-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|ID of the group|

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
          "apiOnly": true,
          "name": "Home expense account",
          "countryCode": "BE",
          "zipcode": "1050",
          "currentValue": 3234,
          "currency": "EUR",
          "defaultOwnershipType": "owner",
          "address": "St. Pierre de Levanaco",
          "realEstateType": "offices",
          "autoPropertyTax": false,
          "annualRent": 10,
          "cadastralIncome": 130,
          "propertyTax": 10,
          "otherCharges": 120,
          "workValue": 1230,
          "category": "real_estate"
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
          "contractDate": "string",
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

<h3 id="getgroupestate-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Group found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="getgroupestate-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|object|true|none|none|
|»» id|string|false|none|ID of the group|
|»» type|string|false|none|Resource type - `group`|
|»» attributes|object|false|none|none|
|»»» estateAssets|[allOf]|false|none|none|

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|
|»»»»» id|string|false|none|Internal reference to asset, must be unique in the group scope. Will be generated randomly if not provided|
|»»»»» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|»»»»» name|string|false|none|Custom name of the asset. If left empty will be constructed from the address|
|»»»»» countryCode|string|false|none|Country where the asset is located. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»»» zipcode|string|false|none|Zipcode where the asset is located. Required for real estate in Belgium to calculate property tax from cadastral income|
|»»»»» currentValue|number|true|none|Current value of the asset|
|»»»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»»»» situationDate|string|false|none|Date at which the amounts where calculated. Must be in the past. Defaults to the creation date. *YYYY-MM-DD*.|
|»»»»» defaultOwnershipType|string|false|none|Ownership of the asset. Owner refers to the 'main client', partner refers to the main client spouse or partner|
|»»»»» community|boolean|false|none|Is the asset owned by the community? If not specified, defaults according to the matrimonial regime|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|object|false|none|none|
|»»»»» address|string|false|none|Address where the asset is located|
|»»»»» realEstateType|string|true|none|Type of real estate asset|
|»»»»» privateUse|boolean|false|none|Is this property for private use or investment?|
|»»»»» annualRent|number|false|none|Total annual rent|
|»»»»» cadastralIncome|number|false|none|Unindexed cadastral income. For assets located in Belgium only.|
|»»»»» autoPropertyTax|boolean|false|none|Should the property tax be calculated from the cadastral income? For assets located in Belgium only.|
|»»»»» propertyTax|number|false|none|Annual property tax|
|»»»»» otherCharges|number|false|none|Other annual charges|
|»»»»» acquisitionValue|number|false|none|Initial acquisition value (incl. tax and fees)|
|»»»»» acquisitionYear|string|false|none|'YYYY' - Acquisition year of the asset.|
|»»»»» workValue|number|false|none|Total amount of investment made since the acquisition|
|»»»»» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|»»»»» category|string|true|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» estateLiabilities|[[EstateLiabilityWithGuarantees/properties/attributes](#schemaestateliabilitywithguarantees/properties/attributes)]|false|none|none|
|»»»»» id|string|false|none|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|»»»»» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|»»»»» name|string|true|none|Custom name of the liability. Can also be a reference.|
|»»»»» liabilityType|string|true|none|Type of account|
|»»»»» linkedToAsset|boolean|false|none|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|»»»»» estateAssetId|string|false|none|Internal reference to asset. Will be ignored if `linkedToAsset` is false. Required if `linkedToAsset` is *true*.|
|»»»»» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»»»»» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|»»»»» countryCode|string|false|none|Country of the applicable law. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»»» initialAmount|number|true|none|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|»»»»» contractDate|string|true|none|Contract signature date. *YYYY-MM-DD*|
|»»»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»»»» repaymentType|string|true|none|Type of account|
|»»»»» periodicity|string|true|none|Periodicity of the principal and/or interest payment|
|»»»»» periodsDuration|integer|true|none|Number of repayment periods. Ignored if `repaymentType` has no end date (*no_end_pay_interest* or *no_end_capitalized_interest*)|
|»»»»» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|»»»»» rateType|string|false|none|Fixed or variable interest rate|
|»»»»» sameOwnershipAsAsset|boolean|false|none|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if `linkedToAsset` is set to *false*.|
|»»»»» borrowers|[string]|false|none|"Ignored if `sameOwnershipAsAsset` is *true*, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan."|
|»»»»» lenders|[string]|false|none|Ignored if `liabilityType` is *bank_loan*. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with an ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|»»»»» balanceInsurance|boolean|false|none|Is the liability covered by a balance insurance (ASRD)?|
|»»»»» balanceInsurancePc|number|false|none|Percentage of the loan covered by a balance insurance. Ignored if `balanceInsurance` is *false*|
|»»»»» guarantees|[object]|false|none|none|
|»»»»»» amount|number|true|none|Amount of the guarantee. Will default to the `initialAmount`. Ignored unless `guarantee` is *true*.|
|»»»»»» guaranteeType|string|true|none|Type of guarantee. Ignored unless `guarantee` is *true*.|
|»»»»»» guarantorableId|string|true|none|ID of the asset or person guaranteeing the liability. Will default to the `estateAssetId` if present. Ignored unless `guarantee` is *true*. ID need to exists within PaxFamilia.|
|»»»»»» guarantorableType|string|true|none|Resource type of the guarantee, can be `GroupMembership` or `EstateAsset`.|
|»»»»» insurances|[[Insurance/properties/attributes](#schemainsurance/properties/attributes)]|false|none|none|
|»»»»»» id|string|false|none|Internal ID of the insurance, must be unique in the group scope. Will be generated randomly if not provided.|
|»»»»»» apiOnly|boolean|false|none|Can only be edited through the API endpoint.|
|»»»»»» name|string|false|none|Custom name of the policy/insurance. If left empty will be constructed from the reference.|
|»»»»»» reference|string|true|none|Reference of the policy.|
|»»»»»» insuranceType|string|true|none|Type of insurance contract.|
|»»»»»» startDate|string|true|none|Start date of the contract. *YYYY-MM-DD*.|
|»»»»»» noTerm|boolean|false|none|Is the contract without term?|
|»»»»»» endDate|string|true|none|End date of the contract. Required if `noTerm` is **false**. Ignored if `noTerm` is **true**. *YYYY-MM-DD*.|
|»»»»»» fixedTerm|boolean|false|none|Is it a fixed term contract? Ignored if `noTerm` is *true*.|
|»»»»»» situationDate|string|false|none|Date at which the amounts where calculated. Defaults to the begining of the current year. *YYYY-MM-DD*.|
|»»»»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»»»»» onlyDeathCover|boolean|false|none|Does the contract only include death insurance, ie. no capital is paid in case of life at term.|
|»»»»»» acquiredReserve|number|true|none|Acquired reserve / current contract value. Ignored if `onlyDeathCover` is *true*. Decimals must be separated by a dot. Eg. 200000.55|
|»»»»»» deathPayout|string|false|none|Payout in case of death. Degressive is assumed linear over the contract duration, **fixed_amount** if `onlyDeathCover`, **reserve** otherwise.|
|»»»»»» deathValue|number|false|none|Death cover amount. Only if `deathPayout` is *'fixed_amount'* or *'degressive'*.|
|»»»»»» acquiredLifeValue|number|false|none|Acquired value in case of life at term (assuming no additional premiums are paid). Ignored if `onlyDeathCover` is *true*. Defaults to same as `acquiredReserve`.|
|»»»»»» reduced|boolean|false|none|Answer *'true'* if the contract was reduced or the premium was unique.|
|»»»»»» premiumsPaid|number|false|none|Premiums paid up to the situation date (net of taxes, fees...).|
|»»»»»» premiumPeriodicity|string|false|none|Periodicity of the premiums. Ignored if reduced is *'true'*|
|»»»»»» premiumEndDate|string|false|none|Date until premiums are to be paid. Ignored if reduced is *'true'*. Default contract end_date if any *YYYY-MM-DD*.|
|»»»»»» premium|number|false|none|Periodic premium expected to be paid. Ignored if reduced is *'true'*.|
|»»»»»» lifeValue|number|false|none|Expected capital in case of life at term (including additional premiums). Ignored if `onlyDeathCover` is *'true'*. Default to `acquiredLifeValue` if reduced.|
|»»»»»» enumPolicyholder|string|true|none|Is the policyholder a company or a physical person (other).|
|»»»»»» employerId|string|false|none|Id of the company (group asset) in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»»»»»» employerName|string|false|none|Name of the employer in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»»»»»» policyholderIds|[string]|false|none|Ignored if `enumPolicyholder` is *'company'*. Will assume each borrower holds an equivalent share of the policy.|
|»»»»»» enumInsuredParty|string|false|none|Is the insured the *'policyholders'* or other designated person(s)?|
|»»»»»» insuredPartyIds|[string]|false|none|Ignored if `enumInsuredParty` is *'policyholders'*.|
|»»»»»» beneficiaryIsCompany|boolean|false|none|In case a company is the policyholder, is the company the beneficiary of the contract? Ignored unless `enumPolicyholder` is *'company'*.|
|»»»»»» enumLifeBeneficiary|string|false|none|Who is(are) the life beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»»»»»» lifeBeneficiaryIds|[string]|false|none|Ignored if `enumLifeBeneficiary` is not *'other'*.|
|»»»»»» enumDeathBeneficiary|string|false|none|Who is(are) the death beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»»»»»» deathBeneficiaryIds|[string]|false|none|Ignored if `enumDeathBeneficiary` is not *'other'*.|
|»»»»»» insuranceCompanyName|string|true|none|The name of the insurance company. Use existing company ID in PaxFamilia to ensure consistency?.|
|»»»»»» ecbCode|string|false|none|ECB code of the insurance company. If not provided, insurance company will be created from the `insuranceCompanyName` but accounts won't therefore be linked to proper insurance info and reconciliation and aggregation will therefore be more complicated.|
|»»»»»» countryCode|string|false|none|Country of the policy. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»»»» category|string|false|none|Category/type of insurance.|
|»»»»»» managerName|string|false|none|Name of the asset manager.|
|»»»»»» swiftCode|string|false|none|Swift code of the depository bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated.|
|»»»»»» bankName|string|false|none|The name of the depository bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|»»»»»» listedRealEstateUnderlyingShare|number|false|none|Underlying portfolio asset composition - listed real estate share|
|»»»»»» equityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in listed companies share|
|»»»»»» privateEquityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in non listed companies share|
|»»»»»» bondsUnderlyingShare|number|false|none|Underlying portfolio asset composition - investment in bonds share|
|»»»»»» cashUnderlyingShare|number|false|none|Underlying portfolio asset composition - cash / liquidity share|
|»»»»»» otherUnderlyingShare|number|false|none|Underlying portfolio asset composition - other / alternative share|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|defaultOwnershipType|owner|
|defaultOwnershipType|partner|
|defaultOwnershipType|common|
|defaultOwnershipType|owner_np_children|
|defaultOwnershipType|partner_np_children|
|defaultOwnershipType|common_np_children|
|defaultOwnershipType|owner_us_parent|
|defaultOwnershipType|partner_us_parent|
|defaultOwnershipType|other|
|realEstateType|residence|
|realEstateType|residential|
|realEstateType|investment|
|realEstateType|offices|
|realEstateType|commercial|
|realEstateType|building_land|
|realEstateType|forest_land|
|realEstateType|other_land|
|realEstateType|agri_land|
|realEstateType|parking|
|realEstateType|other_property_type|
|category|real_estate|
|liabilityType|bank_loan|
|liabilityType|private_loan|
|liabilityType|loan_account|
|liabilityType|other_type|
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
|insuranceType|EP|
|insuranceType|PLCI|
|insuranceType|AG|
|insuranceType|EIP|
|insuranceType|ELT|
|insuranceType|branch21|
|insuranceType|branch23|
|insuranceType|branch44|
|insuranceType|branch26|
|insuranceType|euro_fund|
|insuranceType|unit_linked|
|insuranceType|multi_vehicle|
|insuranceType|capitalization|
|insuranceType|other_insurance|
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
|category|protection|
|category|investment|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getGroupFamily

<a id="opIdgetGroupFamily"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/groups/{id}/family \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/groups/{id}/family',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{id}/family',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/groups/{id}/family", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{id}/family");
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

`GET /groups/{id}/family`

*Get the Family of one Group*

Retrieve the family GroupMemberships and respective DummyUsers of a Group

<h3 id="getgroupfamily-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|ID of the group|

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

<h3 id="getgroupfamily-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Group found|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="getgroupfamily-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[GroupMembershipWithDummyUser](#schemagroupmembershipwithdummyuser)]|true|none|none|
|»» id|string|true|none|`dummyUserId` of the family member|
|»» type|string|true|none|Resource type - `groupMembership`|
|»» attributes|object|true|none|none|
|»»» coHolder|boolean|false|none|Is the person a main data subject of the group.|
|»»» dead|boolean|false|none|Is the person deceased?|
|»»» fatherId|string|false|none|Internal reference to the father, must be an ID of an existing dummy user.|
|»»» motherId|string|false|none|Internal reference to the mother, must be an ID of an existing dummy user.|
|»»» currentSpouseId|string|false|none|Internal reference to the partner, must be an ID of an existing dummy user.|
|»»» dummyUser|[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)|false|none|none|
|»»»» id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|»»»» lastName|string|true|none|Last name of the client.|
|»»»» firstName|string|true|none|First name of the client.|
|»»»» email|string|false|none|Email of the client. Optional.|
|»»»» gender|string|true|none|Gender of the client.|
|»»»» birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|»»»» nationality|string|true|none|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»» countryCode|string|true|none|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»»» zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|
|gender|M|
|gender|F|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-insurances">Insurances</h1>

## addInsurances

<a id="opIdaddInsurances"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/insurances \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/insurances',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/insurances',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/insurances", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/groups/{groupId}/insurances");
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

*Creates one or more Insurances*

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

<h3 id="addinsurances-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|groupId|path|string|true|ID of the group|
|data|body|[[Insurance](#schemainsurance)]|true|none|
|» id|body|string|true|Internal ID of the insurance.|
|» type|body|string|true|Resource type - `insurance`|
|» attributes|body|[Insurance/properties/attributes](#schemainsurance/properties/attributes)|true|none|
|»» id|body|string|false|Internal ID of the insurance, must be unique in the group scope. Will be generated randomly if not provided.|
|»» apiOnly|body|boolean|false|Can only be edited through the API endpoint.|
|»» name|body|string|false|Custom name of the policy/insurance. If left empty will be constructed from the reference.|
|»» reference|body|string|true|Reference of the policy.|
|»» insuranceType|body|string|true|Type of insurance contract.|
|»» startDate|body|string|true|Start date of the contract. *YYYY-MM-DD*.|
|»» noTerm|body|boolean|false|Is the contract without term?|
|»» endDate|body|string|true|End date of the contract. Required if `noTerm` is **false**. Ignored if `noTerm` is **true**. *YYYY-MM-DD*.|
|»» fixedTerm|body|boolean|false|Is it a fixed term contract? Ignored if `noTerm` is *true*.|
|»» situationDate|body|string|false|Date at which the amounts where calculated. Defaults to the begining of the current year. *YYYY-MM-DD*.|
|»» currency|body|string|false|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»» onlyDeathCover|body|boolean|false|Does the contract only include death insurance, ie. no capital is paid in case of life at term.|
|»» acquiredReserve|body|number|true|Acquired reserve / current contract value. Ignored if `onlyDeathCover` is *true*. Decimals must be separated by a dot. Eg. 200000.55|
|»» deathPayout|body|string|false|Payout in case of death. Degressive is assumed linear over the contract duration, **fixed_amount** if `onlyDeathCover`, **reserve** otherwise.|
|»» deathValue|body|number|false|Death cover amount. Only if `deathPayout` is *'fixed_amount'* or *'degressive'*.|
|»» acquiredLifeValue|body|number|false|Acquired value in case of life at term (assuming no additional premiums are paid). Ignored if `onlyDeathCover` is *true*. Defaults to same as `acquiredReserve`.|
|»» reduced|body|boolean|false|Answer *'true'* if the contract was reduced or the premium was unique.|
|»» premiumsPaid|body|number|false|Premiums paid up to the situation date (net of taxes, fees...).|
|»» premiumPeriodicity|body|string|false|Periodicity of the premiums. Ignored if reduced is *'true'*|
|»» premiumEndDate|body|string|false|Date until premiums are to be paid. Ignored if reduced is *'true'*. Default contract end_date if any *YYYY-MM-DD*.|
|»» premium|body|number|false|Periodic premium expected to be paid. Ignored if reduced is *'true'*.|
|»» lifeValue|body|number|false|Expected capital in case of life at term (including additional premiums). Ignored if `onlyDeathCover` is *'true'*. Default to `acquiredLifeValue` if reduced.|
|»» enumPolicyholder|body|string|true|Is the policyholder a company or a physical person (other).|
|»» employerId|body|string|false|Id of the company (group asset) in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»» employerName|body|string|false|Name of the employer in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»» policyholderIds|body|[string]|false|Ignored if `enumPolicyholder` is *'company'*. Will assume each borrower holds an equivalent share of the policy.|
|»» enumInsuredParty|body|string|false|Is the insured the *'policyholders'* or other designated person(s)?|
|»» insuredPartyIds|body|[string]|false|Ignored if `enumInsuredParty` is *'policyholders'*.|
|»» beneficiaryIsCompany|body|boolean|false|In case a company is the policyholder, is the company the beneficiary of the contract? Ignored unless `enumPolicyholder` is *'company'*.|
|»» enumLifeBeneficiary|body|string|false|Who is(are) the life beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»» lifeBeneficiaryIds|body|[string]|false|Ignored if `enumLifeBeneficiary` is not *'other'*.|
|»» enumDeathBeneficiary|body|string|false|Who is(are) the death beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»» deathBeneficiaryIds|body|[string]|false|Ignored if `enumDeathBeneficiary` is not *'other'*.|
|»» insuranceCompanyName|body|string|true|The name of the insurance company. Use existing company ID in PaxFamilia to ensure consistency?.|
|»» ecbCode|body|string|false|ECB code of the insurance company. If not provided, insurance company will be created from the `insuranceCompanyName` but accounts won't therefore be linked to proper insurance info and reconciliation and aggregation will therefore be more complicated.|
|»» countryCode|body|string|false|Country of the policy. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»» category|body|string|false|Category/type of insurance.|
|»» managerName|body|string|false|Name of the asset manager.|
|»» swiftCode|body|string|false|Swift code of the depository bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated.|
|»» bankName|body|string|false|The name of the depository bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|»» listedRealEstateUnderlyingShare|body|number|false|Underlying portfolio asset composition - listed real estate share|
|»» equityUnderlyingShare|body|number|false|Underlying portfolio asset composition - participations in listed companies share|
|»» privateEquityUnderlyingShare|body|number|false|Underlying portfolio asset composition - participations in non listed companies share|
|»» bondsUnderlyingShare|body|number|false|Underlying portfolio asset composition - investment in bonds share|
|»» cashUnderlyingShare|body|number|false|Underlying portfolio asset composition - cash / liquidity share|
|»» otherUnderlyingShare|body|number|false|Underlying portfolio asset composition - other / alternative share|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|insurance|
|»» insuranceType|EP|
|»» insuranceType|PLCI|
|»» insuranceType|AG|
|»» insuranceType|EIP|
|»» insuranceType|ELT|
|»» insuranceType|branch21|
|»» insuranceType|branch23|
|»» insuranceType|branch44|
|»» insuranceType|branch26|
|»» insuranceType|euro_fund|
|»» insuranceType|unit_linked|
|»» insuranceType|multi_vehicle|
|»» insuranceType|capitalization|
|»» insuranceType|other_insurance|
|»» deathPayout|premium|
|»» deathPayout|reserve|
|»» deathPayout|fixed_amount|
|»» deathPayout|degressive|
|»» deathPayout|none|
|»» premiumPeriodicity|monthly|
|»» premiumPeriodicity|quarterly|
|»» premiumPeriodicity|semi_annual|
|»» premiumPeriodicity|annual|
|»» enumPolicyholder|company|
|»» enumPolicyholder|other|
|»» enumInsuredParty|policyholders|
|»» enumInsuredParty|other|
|»» enumLifeBeneficiary|policyholders|
|»» enumLifeBeneficiary|insured_parties|
|»» enumLifeBeneficiary|partner|
|»» enumLifeBeneficiary|children|
|»» enumLifeBeneficiary|parents|
|»» enumLifeBeneficiary|siblings|
|»» enumLifeBeneficiary|grand_children:|
|»» enumLifeBeneficiary|nephews|
|»» enumLifeBeneficiary|other|
|»» enumDeathBeneficiary|succession|
|»» enumDeathBeneficiary|legal_heirs|
|»» enumDeathBeneficiary|partner|
|»» enumDeathBeneficiary|children|
|»» enumDeathBeneficiary|parents|
|»» enumDeathBeneficiary|siblings|
|»» enumDeathBeneficiary|grand_children|
|»» enumDeathBeneficiary|nephews|
|»» enumDeathBeneficiary|foundation|
|»» enumDeathBeneficiary|bank|
|»» enumDeathBeneficiary|other|
|»» category|protection|
|»» category|investment|

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

<h3 id="addinsurances-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Insurances created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="addinsurances-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[Insurance](#schemainsurance)]|true|none|none|
|»» id|string|true|none|Internal ID of the insurance.|
|»» type|string|true|none|Resource type - `insurance`|
|»» attributes|[Insurance/properties/attributes](#schemainsurance/properties/attributes)|true|none|none|
|»»» id|string|false|none|Internal ID of the insurance, must be unique in the group scope. Will be generated randomly if not provided.|
|»»» apiOnly|boolean|false|none|Can only be edited through the API endpoint.|
|»»» name|string|false|none|Custom name of the policy/insurance. If left empty will be constructed from the reference.|
|»»» reference|string|true|none|Reference of the policy.|
|»»» insuranceType|string|true|none|Type of insurance contract.|
|»»» startDate|string|true|none|Start date of the contract. *YYYY-MM-DD*.|
|»»» noTerm|boolean|false|none|Is the contract without term?|
|»»» endDate|string|true|none|End date of the contract. Required if `noTerm` is **false**. Ignored if `noTerm` is **true**. *YYYY-MM-DD*.|
|»»» fixedTerm|boolean|false|none|Is it a fixed term contract? Ignored if `noTerm` is *true*.|
|»»» situationDate|string|false|none|Date at which the amounts where calculated. Defaults to the begining of the current year. *YYYY-MM-DD*.|
|»»» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|»»» onlyDeathCover|boolean|false|none|Does the contract only include death insurance, ie. no capital is paid in case of life at term.|
|»»» acquiredReserve|number|true|none|Acquired reserve / current contract value. Ignored if `onlyDeathCover` is *true*. Decimals must be separated by a dot. Eg. 200000.55|
|»»» deathPayout|string|false|none|Payout in case of death. Degressive is assumed linear over the contract duration, **fixed_amount** if `onlyDeathCover`, **reserve** otherwise.|
|»»» deathValue|number|false|none|Death cover amount. Only if `deathPayout` is *'fixed_amount'* or *'degressive'*.|
|»»» acquiredLifeValue|number|false|none|Acquired value in case of life at term (assuming no additional premiums are paid). Ignored if `onlyDeathCover` is *true*. Defaults to same as `acquiredReserve`.|
|»»» reduced|boolean|false|none|Answer *'true'* if the contract was reduced or the premium was unique.|
|»»» premiumsPaid|number|false|none|Premiums paid up to the situation date (net of taxes, fees...).|
|»»» premiumPeriodicity|string|false|none|Periodicity of the premiums. Ignored if reduced is *'true'*|
|»»» premiumEndDate|string|false|none|Date until premiums are to be paid. Ignored if reduced is *'true'*. Default contract end_date if any *YYYY-MM-DD*.|
|»»» premium|number|false|none|Periodic premium expected to be paid. Ignored if reduced is *'true'*.|
|»»» lifeValue|number|false|none|Expected capital in case of life at term (including additional premiums). Ignored if `onlyDeathCover` is *'true'*. Default to `acquiredLifeValue` if reduced.|
|»»» enumPolicyholder|string|true|none|Is the policyholder a company or a physical person (other).|
|»»» employerId|string|false|none|Id of the company (group asset) in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»»» employerName|string|false|none|Name of the employer in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|»»» policyholderIds|[string]|false|none|Ignored if `enumPolicyholder` is *'company'*. Will assume each borrower holds an equivalent share of the policy.|
|»»» enumInsuredParty|string|false|none|Is the insured the *'policyholders'* or other designated person(s)?|
|»»» insuredPartyIds|[string]|false|none|Ignored if `enumInsuredParty` is *'policyholders'*.|
|»»» beneficiaryIsCompany|boolean|false|none|In case a company is the policyholder, is the company the beneficiary of the contract? Ignored unless `enumPolicyholder` is *'company'*.|
|»»» enumLifeBeneficiary|string|false|none|Who is(are) the life beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»»» lifeBeneficiaryIds|[string]|false|none|Ignored if `enumLifeBeneficiary` is not *'other'*.|
|»»» enumDeathBeneficiary|string|false|none|Who is(are) the death beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|»»» deathBeneficiaryIds|[string]|false|none|Ignored if `enumDeathBeneficiary` is not *'other'*.|
|»»» insuranceCompanyName|string|true|none|The name of the insurance company. Use existing company ID in PaxFamilia to ensure consistency?.|
|»»» ecbCode|string|false|none|ECB code of the insurance company. If not provided, insurance company will be created from the `insuranceCompanyName` but accounts won't therefore be linked to proper insurance info and reconciliation and aggregation will therefore be more complicated.|
|»»» countryCode|string|false|none|Country of the policy. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|»»» category|string|false|none|Category/type of insurance.|
|»»» managerName|string|false|none|Name of the asset manager.|
|»»» swiftCode|string|false|none|Swift code of the depository bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated.|
|»»» bankName|string|false|none|The name of the depository bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|»»» listedRealEstateUnderlyingShare|number|false|none|Underlying portfolio asset composition - listed real estate share|
|»»» equityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in listed companies share|
|»»» privateEquityUnderlyingShare|number|false|none|Underlying portfolio asset composition - participations in non listed companies share|
|»»» bondsUnderlyingShare|number|false|none|Underlying portfolio asset composition - investment in bonds share|
|»»» cashUnderlyingShare|number|false|none|Underlying portfolio asset composition - cash / liquidity share|
|»»» otherUnderlyingShare|number|false|none|Underlying portfolio asset composition - other / alternative share|

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
|insuranceType|euro_fund|
|insuranceType|unit_linked|
|insuranceType|multi_vehicle|
|insuranceType|capitalization|
|insuranceType|other_insurance|
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
|category|protection|
|category|investment|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-estates">Estates</h1>

## refreshEstateValues

<a id="opIdrefreshEstateValues"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/estates/refresh-values \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/estates/refresh-values',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');
const inputBody = '{
  "data": [
    {
      "id": "123dfer",
      "type": "estateLiability",
      "attributes": {
        "id": "123dfer",
        "rate": 2,
        "rateType": "fixed",
        "repaymentStart": "custom_date",
        "customRepaymentStartDate": "1987-08-16",
        "amountAtRepaymentStart": 38626,
        "periodicity": "monthly",
        "periodsDuration": 28,
        "prepaid": false,
        "prepaymentDate": "2007-08-16"
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

fetch('https://subdomain.api.paxfamilia.com/v1/estates/refresh-values',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/estates/refresh-values", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/estates/refresh-values");
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

*Creates one or more Refresh Values*

Endpoint to mass update certain values on the main estate resources - EstateLiability, Insurance, EstateAsset (company, other asset, real estate, account and investment), only one is referenced as an example response. Below are the remaining expected for EstateAsset and Insurance, a more detailed definition can be found in the Schemas section of this documentation under `RefreshValuesEstateAsset` and `RefreshValuesInsurance` respectively.

> Body parameter

```json
{
  "data": [
    {
      "id": "123dfer",
      "type": "estateLiability",
      "attributes": {
        "id": "123dfer",
        "rate": 2,
        "rateType": "fixed",
        "repaymentStart": "custom_date",
        "customRepaymentStartDate": "1987-08-16",
        "amountAtRepaymentStart": 38626,
        "periodicity": "monthly",
        "periodsDuration": 28,
        "prepaid": false,
        "prepaymentDate": "2007-08-16"
      }
    }
  ]
}
```

<h3 id="refreshestatevalues-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[RefreshValuesEstateLiability](#schemarefreshvaluesestateliability)]|true|none|
|» id|body|string|true|Internal reference to the liability|
|» type|body|string|true|Resource type|
|» attributes|body|object|true|none|
|»» id|body|string|true|Internal reference to the liability|
|»» rate|body|number|true|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|»» rateType|body|string|false|Fixed or variable interest rate|
|»» repaymentStart|body|string|false|Repayment start|
|»» customRepaymentStartDate|body|string|false|First repayment date. YYYY-MM-DD. Ignored unless `repaymentStart` is *custom_date*.|
|»» amountAtRepaymentStart|body|number|false|Loan balance on the repayment start date. Defaults to initialAmount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55,|
|»» periodicity|body|string|false|Periodicity of the principal and/or interest payment.|
|»» periodsDuration|body|integer|false|Number of repayment periods. Ignored if `repaymentType` has no end date (no_end_pay_interest or no_end_capitalized_interest)|
|»» prepaid|body|boolean|false|Has the loan been prepaid? (or is it expected to be prepaid at some future date?)|
|»» prepaymentDate|body|string|false|Prepayment date. Defaults to current date if prepaid is set to true, otherwise ignored. *'YYYY-MM-DD'*|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|estateLiability|
|»» rateType|fixed|
|»» rateType|variable|
|»» repaymentStart|one_period_after_contract_date|
|»» repaymentStart|first_day_of_next_period|
|»» repaymentStart|last_day_of_current_period|
|»» repaymentStart|custom_date|
|»» periodicity|monthly|
|»» periodicity|quarterly|
|»» periodicity|semi_annual|
|»» periodicity|annual|

> Example responses

> 202 Response

```json
{
  "data": [
    {
      "id": "123dfer",
      "type": "estateLiability",
      "attributes": {
        "id": "123dfer",
        "rate": 2,
        "rateType": "fixed",
        "repaymentStart": "custom_date",
        "customRepaymentStartDate": "1987-08-16",
        "amountAtRepaymentStart": 38626,
        "periodicity": "monthly",
        "periodsDuration": 28,
        "prepaid": false,
        "prepaymentDate": "2007-08-16"
      }
    }
  ]
}
```

<h3 id="refreshestatevalues-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Refresh Values updated|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<h3 id="refreshestatevalues-responseschema">Response Schema</h3>

Status Code **202**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» data|[[RefreshValuesEstateLiability](#schemarefreshvaluesestateliability)]|true|none|none|
|»» id|string|true|none|Internal reference to the liability|
|»» type|string|true|none|Resource type|
|»» attributes|object|true|none|none|
|»»» id|string|true|none|Internal reference to the liability|
|»»» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|»»» rateType|string|false|none|Fixed or variable interest rate|
|»»» repaymentStart|string|false|none|Repayment start|
|»»» customRepaymentStartDate|string|false|none|First repayment date. YYYY-MM-DD. Ignored unless `repaymentStart` is *custom_date*.|
|»»» amountAtRepaymentStart|number|false|none|Loan balance on the repayment start date. Defaults to initialAmount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55,|
|»»» periodicity|string|false|none|Periodicity of the principal and/or interest payment.|
|»»» periodsDuration|integer|false|none|Number of repayment periods. Ignored if `repaymentType` has no end date (no_end_pay_interest or no_end_capitalized_interest)|
|»»» prepaid|boolean|false|none|Has the loan been prepaid? (or is it expected to be prepaid at some future date?)|
|»»» prepaymentDate|string|false|none|Prepayment date. Defaults to current date if prepaid is set to true, otherwise ignored. *'YYYY-MM-DD'*|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|rateType|fixed|
|rateType|variable|
|repaymentStart|one_period_after_contract_date|
|repaymentStart|first_day_of_next_period|
|repaymentStart|last_day_of_current_period|
|repaymentStart|custom_date|
|periodicity|monthly|
|periodicity|quarterly|
|periodicity|semi_annual|
|periodicity|annual|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## getEstateObjectIdsByGroup

<a id="opIdgetEstateObjectIdsByGroup"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/estates/object-ids \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/estates/object-ids',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/estates/object-ids',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/estates/object-ids", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/estates/object-ids");
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

*Return Estate object IDs per group*

POST used instead of GET due to size of `groupIds` array and array encoding

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

<h3 id="getestateobjectidsbygroup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[EstateObjectIdsFilter](#schemaestateobjectidsfilter)|false|none|
|apiOnly|body|boolean|false|Filter for *'api_only'* *true* or not.|
|type|body|string|true|Filter for estate object type to search for.|
|groupIds|body|[string]|false|Group IDs to filter for.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|type|estateAsset|
|type|estateLiability|
|type|insurance|

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

<h3 id="getestateobjectidsbygroup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Estate Object Ids per Group fetched|[EstateObjectIdsByGroup](#schemaestateobjectidsbygroup)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

## deleteEstateObjectsByGroup

<a id="opIddeleteEstateObjectsByGroup"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/estates/delete-ids \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/estates/delete-ids',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/estates/delete-ids',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/estates/delete-ids", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/estates/delete-ids");
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

*Deletes Estate objects by ID per group*

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

<h3 id="deleteestateobjectsbygroup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|data|body|[[EstateDeleteIds](#schemaestatedeleteids)]|true|none|
|» groupId|body|string|true|Internal ID of a group|
|» type|body|string|true|Type of estate objects to be deleted|
|» ids|body|[string]|true|Estate objects ids to be deleted|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|estateAsset|
|» type|estateLiability|
|» type|insurance|

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

<h3 id="deleteestateobjectsbygroup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Estate Objects successfully deleted|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-alive">Alive</h1>

## checkIfAlive

<a id="opIdcheckIfAlive"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://subdomain.api.paxfamilia.com/v1/is-alive \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/vnd.api+json',
  'X-Api-Key' => '4P1k3y87sGd',
  'Authorization' => '4P1k3y87sGd'
}

result = RestClient.get 'https://subdomain.api.paxfamilia.com/v1/is-alive',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'application/vnd.api+json',
  'X-Api-Key':'4P1k3y87sGd',
  'Authorization':'4P1k3y87sGd'

};

fetch('https://subdomain.api.paxfamilia.com/v1/is-alive',
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
    req, err := http.NewRequest("GET", "https://subdomain.api.paxfamilia.com/v1/is-alive", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/is-alive");
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

*Check if the API connection is alive*

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

<h3 id="checkifalive-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|API is alive|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-general-purpose">General Purpose</h1>

## updateId

<a id="opIdupdateId"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH https://subdomain.api.paxfamilia.com/v1/update-id \
  -H 'Content-Type: application/vnd.api+json' \
  -H 'Accept: application/vnd.api+json' \
  -H 'X-Api-Key: 4P1k3y87sGd' \
  -H 'Authorization: 4P1k3y87sGd'

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

result = RestClient.patch 'https://subdomain.api.paxfamilia.com/v1/update-id',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/update-id',
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
    req, err := http.NewRequest("PATCH", "https://subdomain.api.paxfamilia.com/v1/update-id", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/update-id");
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

*Change the internal ID of a saved resource*

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

<h3 id="updateid-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[NewId](#schemanewid)|false|none|
|data|body|object|true|none|
|» id|body|string|true|Internal ID of the resource to be updated.|
|» type|body|string|true|Type of the resource to be updated|
|» newId|body|string|true|New ID of the resource to be updated to|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» type|companyUnit|
|» type|companyMembership|
|» type|dummyUser|
|» type|group|
|» type|estateAsset|
|» type|estateLiability|
|» type|insurance|
|» type|donation|

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

<h3 id="updateid-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Id successfully updated|[NewId](#schemanewid)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Doesn't match schema|[ErrorBadRequest](#schemaerrorbadrequest)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|[ErrorUnauthorized](#schemaerrorunauthorized)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|[ErrorNotFound](#schemaerrornotfound)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable Entity|[ErrorUnprocessableEntity](#schemaerrorunprocessableentity)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ApiKey & JsonWebToken
</aside>

<h1 id="falcon-alpha-phoenix-user-session">User Session</h1>

## createAuthToken

<a id="opIdcreateAuthToken"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://subdomain.api.paxfamilia.com/v1/users/login \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://subdomain.api.paxfamilia.com/v1/users/login',
  params: {
  }, headers: headers

p JSON.parse(result)

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

fetch('https://subdomain.api.paxfamilia.com/v1/users/login',
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
    req, err := http.NewRequest("POST", "https://subdomain.api.paxfamilia.com/v1/users/login", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

```java
URL obj = new URL("https://subdomain.api.paxfamilia.com/v1/users/login");
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

*Generate JSON Web Token with valid user credentials + Api-Key*

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

<h3 id="createauthtoken-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|user|body|object|true|User credentials|
|» email|body|string|true|Valid user email|
|» password|body|string|true|Valid user password|
|company|body|object|true|Company credentials|
|» apiKey|body|string|true|Valid company apiKey|

> Example responses

> 200 Response

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoiMTQwODdiN2QtMTI4ZC00YWM5LTljYmMtZTJiMTI5ZWQ3NDcxIiwiZXhwIjoxNTcyMzYwMTEzfQ.ciy_lAZUkj1PBNQvGGUhoaZY-Yei3M3ZiCZhZouiLAY",
  "message": "Login Successful"
}
```

<h3 id="createauthtoken-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Login Successful|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Invalid credentials|Inline|

<h3 id="createauthtoken-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» accessToken|string|false|none|Json Web Token to use for authentication|
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

<h2 id="tocSerrorbadrequest">ErrorBadRequest</h2>

<a id="schemaerrorbadrequest"></a>

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
|errors|[object]|true|none|Errors array|
|» status|string|true|none|HTTP error name *400 Bad Request*|
|» detail|string|true|none|Error message|

#### Enumerated Values

|Property|Value|
|---|---|
|status|bad_request|

<h2 id="tocSerrorunauthorized">ErrorUnauthorized</h2>

<a id="schemaerrorunauthorized"></a>

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
|errors|[object]|true|none|Errors array|
|» status|string|true|none|HTTP error name *401 Unauthorized*|
|» detail|string|true|none|Error message|

#### Enumerated Values

|Property|Value|
|---|---|
|status|unauthorized|

<h2 id="tocSerrorunprocessableentity">ErrorUnprocessableEntity</h2>

<a id="schemaerrorunprocessableentity"></a>

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
|errors|[object]|true|none|Errors array|
|» status|string|true|none|HTTP error name *422 Unprocessable Entity*|
|» detail|string|true|none|Error message|

#### Enumerated Values

|Property|Value|
|---|---|
|status|unprocessable_entity|

<h2 id="tocSerrornotfound">ErrorNotFound</h2>

<a id="schemaerrornotfound"></a>

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
|errors|[object]|true|none|Errors array|
|» status|string|true|none|HTTP error name *404 Not Found*|
|» detail|string|true|none|Error message|

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
|id|string|true|none|Api log ID|
|type|string|true|none|Resource type - `apiLog`|
|attributes|object|true|none|none|
|» id|string|false|none|Api log ID|
|» companyMembershipId|string|false|none|Employee public id if their is an employee associated to this log|
|» success|boolean|true|none|Request success or failure|
|» status|string|false|none|Request status HTTP code in word form|
|» description|string|false|none|Any valid description needed, for **success** usually amount saved, for **failure** usually error message|
|» groupPublicId|string|false|none|Group public id associated to the log when it is a group scoped resource, such as: `estateAsset`, `estateLiability`|
|» resourceId|string|false|none|Public id of the resource in question when in the case of a specific resource error|
|» controller|string|false|none|Resource controller from which the log originated|
|» action|string|false|none|Resource action from which the log originated|
|» requestMethod|string|false|none|HTTP request method|

#### Enumerated Values

|Property|Value|
|---|---|
|type|apiLog|
|requestMethod|POST|
|requestMethod|PATCH|
|requestMethod|DELETE|
|requestMethod|GET|

<h2 id="tocSestateassetpercentattributes">EstateAssetPercentAttributes</h2>

<a id="schemaestateassetpercentattributes"></a>

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

<h2 id="tocSestateassetbaseattributes">EstateAssetBaseAttributes</h2>

<a id="schemaestateassetbaseattributes"></a>

```json
{
  "id": "345abcd",
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
|id|string|false|none|Internal reference to asset, must be unique in the group scope. Will be generated randomly if not provided|
|apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|name|string|false|none|Custom name of the asset. If left empty will be constructed from the address|
|countryCode|string|false|none|Country where the asset is located. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|zipcode|string|false|none|Zipcode where the asset is located. Required for real estate in Belgium to calculate property tax from cadastral income|
|currentValue|number|true|none|Current value of the asset|
|currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|situationDate|string|false|none|Date at which the amounts where calculated. Must be in the past. Defaults to the creation date. *YYYY-MM-DD*.|
|defaultOwnershipType|string|false|none|Ownership of the asset. Owner refers to the 'main client', partner refers to the main client spouse or partner|
|community|boolean|false|none|Is the asset owned by the community? If not specified, defaults according to the matrimonial regime|

#### Enumerated Values

|Property|Value|
|---|---|
|defaultOwnershipType|owner|
|defaultOwnershipType|partner|
|defaultOwnershipType|common|
|defaultOwnershipType|owner_np_children|
|defaultOwnershipType|partner_np_children|
|defaultOwnershipType|common_np_children|
|defaultOwnershipType|owner_us_parent|
|defaultOwnershipType|partner_us_parent|
|defaultOwnershipType|other|

<h2 id="tocSestateassetrealestate">EstateAssetRealEstate</h2>

<a id="schemaestateassetrealestate"></a>

```json
{
  "id": "345abcd",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "address": "St. Pierre de Levanaco",
  "realEstateType": "offices",
  "autoPropertyTax": false,
  "annualRent": 10,
  "cadastralIncome": 130,
  "propertyTax": 10,
  "otherCharges": 120,
  "workValue": 1230,
  "category": "real_estate"
}

```

### Properties

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» address|string|false|none|Address where the asset is located|
|» realEstateType|string|true|none|Type of real estate asset|
|» privateUse|boolean|false|none|Is this property for private use or investment?|
|» annualRent|number|false|none|Total annual rent|
|» cadastralIncome|number|false|none|Unindexed cadastral income. For assets located in Belgium only.|
|» autoPropertyTax|boolean|false|none|Should the property tax be calculated from the cadastral income? For assets located in Belgium only.|
|» propertyTax|number|false|none|Annual property tax|
|» otherCharges|number|false|none|Other annual charges|
|» acquisitionValue|number|false|none|Initial acquisition value (incl. tax and fees)|
|» acquisitionYear|string|false|none|'YYYY' - Acquisition year of the asset.|
|» workValue|number|false|none|Total amount of investment made since the acquisition|
|» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|realEstateType|residence|
|realEstateType|residential|
|realEstateType|investment|
|realEstateType|offices|
|realEstateType|commercial|
|realEstateType|building_land|
|realEstateType|forest_land|
|realEstateType|other_land|
|realEstateType|agri_land|
|realEstateType|parking|
|realEstateType|other_property_type|
|category|real_estate|

<h2 id="tocSestateassetinvestment">EstateAssetInvestment</h2>

<a id="schemaestateassetinvestment"></a>

```json
{
  "id": "345abcd",
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
  "capitalisationPc": 3,
  "category": "investment"
}

```

### Properties

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetPercentAttributes](#schemaestateassetpercentattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» reference|string|true|none|Reference of the portfolio|
|» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated|
|» bankName|string|true|none|The name of the (depositary) bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|» capitalisationPc|number|false|none|Percentage of return that is expected to be capitalized. Used for CF projections|
|» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|» manager|string|false|none|Name of the asset manager|
|» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|category|investment|

<h2 id="tocSestateassetaccount">EstateAssetAccount</h2>

<a id="schemaestateassetaccount"></a>

```json
{
  "id": "345abcd",
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
  "rateOfReturn": 2,
  "category": "account"
}

```

### Properties

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» accountType|string|true|none|Type of account|
|» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
|» iban|string|false|none|Account IBAN number.|
|» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated|
|» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|accountType|current_account|
|accountType|saving_account|
|accountType|term_account|
|accountType|other_type|
|category|account|

<h2 id="tocSestateassetcompany">EstateAssetCompany</h2>

<a id="schemaestateassetcompany"></a>

```json
{
  "id": "345abcd",
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
  "agriSpecificShare": 0,
  "category": "company"
}

```

### Properties

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetPercentAttributes](#schemaestateassetpercentattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» companyType|string|false|none|Type of company / legal form|
|» companyObject|string|true|none|Type of company object|
|» companyNumber|string|false|none|Company registration number. Numbers only.|
|» vatNumber|string|false|none|Company VAT number. Will be derived from `companyNumber` where possible, eg. Belgian companies|
|» officialName|string|true|none|Official/legal name of the company. If `companyNumber` and `countryCode` are valid, will be obtained from [Open Corporate](opencorporates.com)|
|» legalPersonality|boolean|false|none|Does the company have a legal personality? Eg. indivisions, 'société civile/de droit commun' don't have legal personality|
|» address|string|false|none|Address of the company. If `companyNumber` and `countryCode` are valid, will be obtained from [Open Corporate](opencorporates.com)|
|» linkUnderlyingValue|boolean|false|none|Company value can be determined based on the value of the underlying company assets and liabilities added in the system or from a value you determine yourself.|
|» hasDividend|boolean|false|none|Is the company paying a dividend?|
|» annualDividend|number|false|none|Estimated annual dividend. Ignore if `hasDividend` is *false*.|
|» dividendIndexation|boolean|false|none|Should the dividend be indexed with the company value?|
|» linkUnderlyingComposition|boolean|false|none|Company asset composition can be determined based on the underlying company assets and liabilities added in the system or from a composition you specifity. If set to *true*, provided asset composition will be ignored.|
|» rateOfReturn|number|false|none|Expected annual value increase of the company.|
|» realEstateShare|number|false|none|Underlying company asset composition - real estate share|
|» receivablesShare|number|false|none|Underlying company asset composition - receivables / private loans|
|» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|companyObject|operational|
|companyObject|management|
|companyObject|holding|
|companyObject|patrimonial|
|companyObject|agriculture|
|companyObject|other_object|
|category|company|

<h2 id="tocSestateassetotherasset">EstateAssetOtherAsset</h2>

<a id="schemaestateassetotherasset"></a>

```json
{
  "id": "345abcd",
  "apiOnly": true,
  "name": "Home expense account",
  "countryCode": "BE",
  "zipcode": "1050",
  "currentValue": 3234,
  "currency": "EUR",
  "defaultOwnershipType": "owner",
  "otherAssetType": "precious_metal",
  "privateUse": false,
  "category": "other_asset"
}

```

### Properties

*allOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[EstateAssetBaseAttributes](#schemaestateassetbaseattributes)|false|none|none|

*and*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|object|false|none|none|
|» otherAssetType|string|true|none|Type of other asset|
|» privateUse|boolean|false|none|Is this asset for private use or investment?|
|» category|string|true|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|otherAssetType|jewelry|
|otherAssetType|art|
|otherAssetType|car|
|otherAssetType|wine|
|otherAssetType|books|
|otherAssetType|precious_metal|
|otherAssetType|furniture|
|otherAssetType|immaterial_asset|
|otherAssetType|other_type|
|category|other_asset|

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
|type|string|true|none|Resource type - `assetOwnership`|
|attributes|object|true|none|none|
|» ownerId|string|true|none|Internal ID of the owner. If blank, will expect `companyId`.|
|» companyId|string|false|none|Internal ID of the company that owns the asset. Ignored if `ownerId` is provided.|
|» ownerCategory|string|false|none|Owner category. A physical person ('person'), the community ('community') or a moral person ('company')|
|» communityOwner|string|false|none|Only in case of 'community `ownerCategory`'. Whether the asset is under both names or the main data subject or it's partner/spouse",|
|» ownershipType|string|false|none|Type of the ownership. Full property ('fp'), bare ownership ('np') or usufruct ('us')|
|» percentage|number|true|none|Percentage ownership. Decimals must be separated by a dot. Eg. 25.5|
|» otherOwnerId|string|false|none|Internal ID of the owner holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp'.|
|» otherCompanyId|string|false|none|Internal ID of the company holding the other side of the dismembered ownership, if applicable. Ignored if `ownershipType` is 'fp' and/or if `otherOwnerId` is provided.|
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
|id|string|true|none|Internal employee id. Must be unique.|
|type|string|true|none|Resource type - `companyMembership`|
|attributes|object|true|none|none|
|» id|string|true|none|Internal employee id. Must be unique. Will be generated randomly if not provided|
|» companyUnitId|string|false|none|Id of the unit, center or department the employee belongs to.|
|» lastName|string|true|none|Last name of the employee|
|» firstName|string|true|none|First name of the employee|
|» gender|string|true|none|Gender of the employee|
|» email|string|true|none|Email of the employee. used as username for login. needs to be unique.|
|» mobilePhone|string|true|none|Mobile phone number of the employee. required for 2fa. uses the [phony library](https://github.com/floere/phony) to validate plausibility of number. Country extension defaults to *+32* unless provided|
|» countryCode|string|false|none|Country (residence) of the employee. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» locale|string|true|none|Language used for the PaxFamilia application|
|» memberRight|string|true|none|Right of the employee. `read_and_write` means the employee can create new clients, `read` only means the employee can't create clients but can access clients he has been given access to.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyMembership|
|gender|M|
|gender|F|
|locale|fr|
|locale|nl|
|locale|en|
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
|id|string|true|none|Internal id of the unit, center or department.|
|type|string|true|none|Resource type - `companyUnit`|
|attributes|object|true|none|none|
|» id|string|true|none|Internal id of the unit, center or department. Will be generated randomly if not provided|
|» parentUnitId|string|false|none|A unit can be a sub unit of another unit (parentUnit).|
|» name|string|true|none|Name the unit, center or department|
|» countryCode|string|false|none|Country of the unit. Default to the country of the company it belongs to. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» address|string|false|none|Address of the unit|
|» zipcode|string|false|none|Zipcode of the unit|
|» locale|string|true|none|Language of the unit|

#### Enumerated Values

|Property|Value|
|---|---|
|type|companyUnit|
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
|id|string|true|none|Internal id of the donation.|
|type|string|true|none|Resource type - `donation`|
|attributes|object|true|none|none|
|» id|string|true|none|Internal id of the donation. Must be unique. Will be generated randomly if not provided.|
|» estateAssetId|string|false|none|Id of the asset it relates to.|
|» name|string|true|none|Name or reference for the donation|
|» transactionDate|string|true|none|Donation date. YYYY-MM-DD|
|» donationType|string|true|none|Type of donation|
|» amount|number|true|none|Total intrinsic value of the donation. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|» currentValue|string|false|none|Current value of the donation. Defaults to `amount`|
|» donorIds|[string]|true|none|Array of donor ids.|
|» doneeIds|[string]|true|none|Array of donee ids.|
|» calleeIds|[string]|false|none|Internal IDs of the callee(s). Only in case residuo clause is true.|
|» ownershipType|string|true|none|Specify if the donation is not for the full ownership. Full property ('fp'), bare ownership ('np') or bare ownership with reserve of usufruct ('np_reserve_us').|
|» inheritanceTreatment|string|false|none|Treatment at succession. `advance`:- advance on inheritance, `no_report`:- par preciput et hors part, `advance_with_no_report`:- advance on inheritance with no report in nature.|
|» nonTransferabilityClause|string|false|none|Type of non transferability clause (inalienability) if any|
|» nonTransferabilityDuration|integer|false|none|Number of years of inalienability. Required if `nonTransferabilityClause` is forYears|
|» noCommunityCondition|boolean|false|none|Clause preventing to bring the given assets to a community|
|» returnClause|string|false|none|Clause of conventional return|
|» returnClauseOptional|boolean|false|none|Is the return clause optional?|
|» annuityClause|boolean|false|none|Is there a charge/rent (Charge de rente)?|
|» annuityAmount|number|false|none|Annual annuity amount. Required if `annuityClause` is *true*|
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
|id|string|true|none|Internal client/person id.|
|type|string|true|none|Resource type - `dummyUser`|
|attributes|object|true|none|none|
|» id|string|false|none|Internal client/person id. Will be generated randomly if not provided|
|» lastName|string|true|none|Last name of the client.|
|» firstName|string|true|none|First name of the client.|
|» email|string|false|none|Email of the client. Optional.|
|» gender|string|true|none|Gender of the client.|
|» birthday|string|false|none|YYYY-MM-DD. Must be left empty is unknown. Optional but recommended.|
|» nationality|string|true|none|Country code of nationality. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» countryCode|string|true|none|Country code of residence. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» zipcode|string|false|none|Zipcode in the country of residence. Must be a valid zipcode in the country or empty|

#### Enumerated Values

|Property|Value|
|---|---|
|type|dummyUser|
|gender|M|
|gender|F|

<h2 id="tocSestateliability">EstateLiability</h2>

<a id="schemaestateliability"></a>

```json
{
  "id": "abcd1234",
  "type": "estateLiability",
  "attributes": {
    "id": "abcd1234",
    "name": "Birthday gift to my son's 30th",
    "countryCode": "BE",
    "currency": "EUR",
    "contractDate": "1970-02-20",
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
    "guarantee": true,
    "guaranteeType": "other_guarantee",
    "guaranteeAmount": 73810,
    "guarantorInternalId": "estate_asset_id_653",
    "prepaid": false,
    "prepaymentDate": "1987-08-16T00:00:00.000Z"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal reference to the liability, must be unique in the group scope.|
|type|string|true|none|Resource type - `estateLiability`|
|attributes|object|true|none|none|
|» id|string|false|none|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|» name|string|true|none|Custom name of the liability. Can also be a reference.|
|» liabilityType|string|true|none|Type of account|
|» linkedToAsset|boolean|false|none|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|» estateAssetId|string|false|none|Internal reference to asset. Will be ignored if `linkedToAsset` is false. Required if `linkedToAsset` is *true*.|
|» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|» countryCode|string|false|none|Country of the applicable law. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» initialAmount|number|true|none|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|» contractDate|string|true|none|Contract signature date. Must be in the past. *YYYY-MM-DD*|
|» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|» repaymentType|string|true|none|Type of account|
|» periodicity|string|true|none|Periodicity of the principal and/or interest payment|
|» periodsDuration|integer|true|none|Number of repayment periods. Ignored if `repaymentType` has no end date (*no_end_pay_interest* or *no_end_capitalized_interest*)|
|» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|» rateType|string|false|none|Fixed or variable interest rate|
|» sameOwnershipAsAsset|boolean|false|none|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if `linkedToAsset` is set to *false*.|
|» borrowers|[string]|false|none|"Ignored if `sameOwnershipAsAsset` is *true*, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan."|
|» lenders|[string]|false|none|Ignored if `liabilityType` is *bank_loan*. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with an ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|» balanceInsurance|boolean|false|none|Is the liability covered by a balance insurance (ASRD)?|
|» balanceInsurancePc|number|false|none|Percentage of the loan covered by a balance insurance. Ignored if `balanceInsurance` is *false*|
|» guarantee|boolean|false|none|Is the liability secured by a guarantee?|
|» guaranteeType|string|false|none|Type of guarantee. Ignored unless `guarantee` is *true*.|
|» guaranteeAmount|number|false|none|Amount of the guarantee. Will default to the `initialAmount`. Ignored unless `guarantee` is *true*.|
|» guarantorInternalId|string|false|none|ID of the asset or person guaranteeing the liability. Will default to the `estateAssetId` if present. Ignored unless `guarantee` is *true*. ID needs to exists within PaxFamilia|
|» prepaid|boolean|false|none|Has the loan been prepaid? (or is it expected to be prepaid at some future date?)|
|» prepaymentDate|string|false|none|Prepayment date. Defaults to current date if prepaid is set to true, otherwise ignored. *YYYY-MM-DD*|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|liabilityType|bank_loan|
|liabilityType|private_loan|
|liabilityType|loan_account|
|liabilityType|other_type|
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
|guaranteeType|mortgage,|
|guaranteeType|mortgage_mandate,|
|guaranteeType|personal_guarantee,|
|guaranteeType|pledge,|
|guaranteeType|other_guarantee|

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
    "contractDate": "1970-02-20",
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
|id|string|true|none|Internal reference to the liability, must be unique in the group scope.|
|type|string|true|none|Resource type - `estateLiability`|
|attributes|object|true|none|none|
|» id|string|false|none|Internal reference to the liability, must be unique in the group scope. Will be generated randomly if not provided|
|» apiOnly|boolean|false|none|Can only be edited through the api endpoint|
|» name|string|true|none|Custom name of the liability. Can also be a reference.|
|» liabilityType|string|true|none|Type of account|
|» linkedToAsset|boolean|false|none|Has the liability been used to finance an asset that has already been created within PaxFamilia?|
|» estateAssetId|string|false|none|Internal reference to asset. Will be ignored if `linkedToAsset` is false. Required if `linkedToAsset` is *true*.|
|» swiftCode|string|false|none|Swift code of the bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|» bankName|string|true|none|The name of the bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided. Required if `liabilityType` is **bank_loan**, otherwise ignored.|
|» countryCode|string|false|none|Country of the applicable law. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» initialAmount|number|true|none|Initial loan amount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55|
|» contractDate|string|true|none|Contract signature date. *YYYY-MM-DD*|
|» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|» repaymentType|string|true|none|Type of account|
|» periodicity|string|true|none|Periodicity of the principal and/or interest payment|
|» periodsDuration|integer|true|none|Number of repayment periods. Ignored if `repaymentType` has no end date (*no_end_pay_interest* or *no_end_capitalized_interest*)|
|» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|» rateType|string|false|none|Fixed or variable interest rate|
|» sameOwnershipAsAsset|boolean|false|none|Is the liability held by the same owners of the linked asset and in the same proportions? Ignored if `linkedToAsset` is set to *false*.|
|» borrowers|[string]|false|none|"Ignored if `sameOwnershipAsAsset` is *true*, otherwise at least one required. Will assume each borrower holds an equivalent share of the loan. Other borrowers, i.e. that do not exist in the PaxFamilia group scope, can be referenced with and ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four borrowers (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan."|
|» lenders|[string]|false|none|Ignored if `liabilityType` is *bank_loan*. Will assume each lender holds an equivalent share of the loan. Other lenders, i.e. that do not exist in the PaxFamilia group scope, can be referenced with an ID of '0'. => Example `[clientId, companyId, 0, 0]` will create four lenders (one linked to a client, one linked to a company and two linked to 'no one') each with 25% of the loan.|
|» balanceInsurance|boolean|false|none|Is the liability covered by a balance insurance (ASRD)?|
|» balanceInsurancePc|number|false|none|Percentage of the loan covered by a balance insurance. Ignored if `balanceInsurance` is *false*|
|» guarantees|[object]|false|none|none|
|»» amount|number|true|none|Amount of the guarantee. Will default to the `initialAmount`. Ignored unless `guarantee` is *true*.|
|»» guaranteeType|string|true|none|Type of guarantee. Ignored unless `guarantee` is *true*.|
|»» guarantorableId|string|true|none|ID of the asset or person guaranteeing the liability. Will default to the `estateAssetId` if present. Ignored unless `guarantee` is *true*. ID need to exists within PaxFamilia.|
|»» guarantorableType|string|true|none|Resource type of the guarantee, can be `GroupMembership` or `EstateAsset`.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|liabilityType|bank_loan|
|liabilityType|private_loan|
|liabilityType|loan_account|
|liabilityType|other_type|
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

<h2 id="tocSgroupmembership">GroupMembership</h2>

<a id="schemagroupmembership"></a>

```json
{
  "id": "Yu1234ac",
  "type": "groupMembership",
  "attributes": {
    "dummyUserId": "Yu1234ac",
    "sex": "F",
    "status": "approved",
    "memberRight": "no_right",
    "dead": false,
    "fatherId": "1234acds3",
    "adoption": "none",
    "extendedMinority": true,
    "provisionalAdministration": true,
    "judicialProtection": false,
    "extrajudicialProtection": false
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Same as `dummyUserId` below|
|type|string|true|none|Resource type - `groupMembership`|
|attributes|object|true|none|none|
|» dummyUserId|string|true|none|Id of an existing dummy user.|
|» coHolder|boolean|false|none|Is the person a main data subject of the group|
|» dead|boolean|false|none|Is the person deceased?|
|» fatherId|string|false|none|Internal reference to the father, must be an ID of an existing dummy user.|
|» motherId|string|false|none|Internal reference to the mother, must be an ID of an existing dummy user.|
|» currentSpouseId|string|false|none|Internal reference to the partner, must be an ID of an existing dummy user.|
|» spouseType|string|false|none|Type of partner relationship if current spouse exist.|
|» regimeType|string|false|none|Type of matrimonial regime if `spouseType` is spouse|
|» adoption|string|false|none|Type of adoption if any|
|» extendedMinority|boolean|false|none|Does the group membership have an extended minority?|
|» provisionalAdministration|boolean|false|none|Does the group membership have a provisional administration?|
|» judicialProtection|boolean|false|none|Does the group membership have a judicial protection?|
|» extrajudicialProtection|boolean|false|none|Does the group membership have an extrajudicial protection?|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|
|spouseType|spouse|
|spouseType|legal_cohabitant|
|spouseType|simple_cohabitant|
|regimeType|legal_regime|
|regimeType|separate_ownership|
|regimeType|acquests_participation|
|regimeType|separate_ownership_with_community_addition|
|regimeType|conventional_community|
|regimeType|full_community|
|adoption|none|
|adoption|simple|
|adoption|full|

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
|id|string|true|none|`dummyUserId` of the family member|
|type|string|true|none|Resource type - `groupMembership`|
|attributes|object|true|none|none|
|» coHolder|boolean|false|none|Is the person a main data subject of the group.|
|» dead|boolean|false|none|Is the person deceased?|
|» fatherId|string|false|none|Internal reference to the father, must be an ID of an existing dummy user.|
|» motherId|string|false|none|Internal reference to the mother, must be an ID of an existing dummy user.|
|» currentSpouseId|string|false|none|Internal reference to the partner, must be an ID of an existing dummy user.|
|» dummyUser|[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type|groupMembership|

<h2 id="tocSgroup">Group</h2>

<a id="schemagroup"></a>

```json
{
  "id": "acbdj6472",
  "type": "group",
  "attributes": {
    "id": "acbdj6472",
    "internalName": "Lucas Niets",
    "state": "active",
    "clientId": "a675742",
    "companyAdvisorId": "987gfr"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal group ID.|
|type|string|true|none|Resource type - `group`|
|attributes|object|true|none|none|
|» id|string|true|none|Internal group ID. Must be unique. Will be generated randomly if not provided.|
|» internalName|string|false|none|Internal client name, won't be visible to client|
|» companyAdvisorId|string|true|none|ID of the employee that will be assigned the relationship manager role for this group, must be existing user that is authorized to create client. Will default to company admin.|
|» clientId|string|true|none|ID of the 'main' client. Must be an existing dummy user.|
|» locale|string|false|none|Default language for the group. Defaults to the locale of the company advisor.|
|» state|string|false|none|State of the group|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|
|locale|fr|
|locale|nl|
|locale|en|
|state|draft|
|state|active|
|state|suspended|
|state|marked_for_deletion|

<h2 id="tocSinsurance">Insurance</h2>

<a id="schemainsurance"></a>

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
|id|string|true|none|Internal ID of the insurance.|
|type|string|true|none|Resource type - `insurance`|
|attributes|object|true|none|none|
|» id|string|false|none|Internal ID of the insurance, must be unique in the group scope. Will be generated randomly if not provided.|
|» apiOnly|boolean|false|none|Can only be edited through the API endpoint.|
|» name|string|false|none|Custom name of the policy/insurance. If left empty will be constructed from the reference.|
|» reference|string|true|none|Reference of the policy.|
|» insuranceType|string|true|none|Type of insurance contract.|
|» startDate|string|true|none|Start date of the contract. *YYYY-MM-DD*.|
|» noTerm|boolean|false|none|Is the contract without term?|
|» endDate|string|true|none|End date of the contract. Required if `noTerm` is **false**. Ignored if `noTerm` is **true**. *YYYY-MM-DD*.|
|» fixedTerm|boolean|false|none|Is it a fixed term contract? Ignored if `noTerm` is *true*.|
|» situationDate|string|false|none|Date at which the amounts where calculated. Defaults to the begining of the current year. *YYYY-MM-DD*.|
|» currency|string|false|none|Currency of the value(s). Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#currencies) for the complete list of allowed currencies.|
|» onlyDeathCover|boolean|false|none|Does the contract only include death insurance, ie. no capital is paid in case of life at term.|
|» acquiredReserve|number|true|none|Acquired reserve / current contract value. Ignored if `onlyDeathCover` is *true*. Decimals must be separated by a dot. Eg. 200000.55|
|» deathPayout|string|false|none|Payout in case of death. Degressive is assumed linear over the contract duration, **fixed_amount** if `onlyDeathCover`, **reserve** otherwise.|
|» deathValue|number|false|none|Death cover amount. Only if `deathPayout` is *'fixed_amount'* or *'degressive'*.|
|» acquiredLifeValue|number|false|none|Acquired value in case of life at term (assuming no additional premiums are paid). Ignored if `onlyDeathCover` is *true*. Defaults to same as `acquiredReserve`.|
|» reduced|boolean|false|none|Answer *'true'* if the contract was reduced or the premium was unique.|
|» premiumsPaid|number|false|none|Premiums paid up to the situation date (net of taxes, fees...).|
|» premiumPeriodicity|string|false|none|Periodicity of the premiums. Ignored if reduced is *'true'*|
|» premiumEndDate|string|false|none|Date until premiums are to be paid. Ignored if reduced is *'true'*. Default contract end_date if any *YYYY-MM-DD*.|
|» premium|number|false|none|Periodic premium expected to be paid. Ignored if reduced is *'true'*.|
|» lifeValue|number|false|none|Expected capital in case of life at term (including additional premiums). Ignored if `onlyDeathCover` is *'true'*. Default to `acquiredLifeValue` if reduced.|
|» enumPolicyholder|string|true|none|Is the policyholder a company or a physical person (other).|
|» employerId|string|false|none|Id of the company (group asset) in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|» employerName|string|false|none|Name of the employer in case the policyholder is a *'company'*. eg. group insurance. Ignored if `enumPolicyholder` is *'other'*.|
|» policyholderIds|[string]|false|none|Ignored if `enumPolicyholder` is *'company'*. Will assume each borrower holds an equivalent share of the policy.|
|» enumInsuredParty|string|false|none|Is the insured the *'policyholders'* or other designated person(s)?|
|» insuredPartyIds|[string]|false|none|Ignored if `enumInsuredParty` is *'policyholders'*.|
|» beneficiaryIsCompany|boolean|false|none|In case a company is the policyholder, is the company the beneficiary of the contract? Ignored unless `enumPolicyholder` is *'company'*.|
|» enumLifeBeneficiary|string|false|none|Who is(are) the life beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|» lifeBeneficiaryIds|[string]|false|none|Ignored if `enumLifeBeneficiary` is not *'other'*.|
|» enumDeathBeneficiary|string|false|none|Who is(are) the death beneficiary(ies)? Ignored if company is *'beneficiaryIsCompany'*.|
|» deathBeneficiaryIds|[string]|false|none|Ignored if `enumDeathBeneficiary` is not *'other'*.|
|» insuranceCompanyName|string|true|none|The name of the insurance company. Use existing company ID in PaxFamilia to ensure consistency?.|
|» ecbCode|string|false|none|ECB code of the insurance company. If not provided, insurance company will be created from the `insuranceCompanyName` but accounts won't therefore be linked to proper insurance info and reconciliation and aggregation will therefore be more complicated.|
|» countryCode|string|false|none|Country of the policy. Refer to the following [link](https://github.com/mlrcbsousa/paxfamilia-enums#country-codes) for the complete list of allowed country codes.|
|» category|string|false|none|Category/type of insurance.|
|» managerName|string|false|none|Name of the asset manager.|
|» swiftCode|string|false|none|Swift code of the depository bank, eg. *'GEBABEBB'*. If not provided, bank will be created from the `bankName` but accounts won't therefore be linked to proper bank info and reconciliation and aggregation will therefore be more complicated.|
|» bankName|string|false|none|The name of the depository bank. The name of the bank will be derived from its `swiftCode` if a valid one is provided.|
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
|insuranceType|euro_fund|
|insuranceType|unit_linked|
|insuranceType|multi_vehicle|
|insuranceType|capitalization|
|insuranceType|other_insurance|
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
|type|string|true|none|Resource type - `group`|
|attributes|object|true|none|none|
|» id|string|true|none|Internal ID of group|
|» companyAdvisorId|string|true|none|Internal ID of company advisor for this group. Must be an existing `companyMembership`.|
|» authorizedCompanyUserIds|[string]|true|none|Internal IDs of other company employees allowed access to the group. Must be existing `companyMemberships`.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|group|

<h2 id="tocSrefreshvaluesestateasset">RefreshValuesEstateAsset</h2>

<a id="schemarefreshvaluesestateasset"></a>

```json
{
  "id": "123dfer",
  "type": "estateAsset",
  "attributes": {
    "id": "123dfer",
    "currentValue": 2344
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal ID reference to the asset|
|type|string|true|none|Resource type|
|attributes|object|true|none|none|
|» id|string|true|none|Internal ID reference to the asset|
|» currentValue|number|true|none|Current value of the asset|
|» situationDate|string|false|none|Date at which the amounts where calculated. Must be in the past. Defaults to the refresh date. *YYYY-MM-DD*.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateAsset|

<h2 id="tocSrefreshvaluesestateliability">RefreshValuesEstateLiability</h2>

<a id="schemarefreshvaluesestateliability"></a>

```json
{
  "id": "123dfer",
  "type": "estateLiability",
  "attributes": {
    "id": "123dfer",
    "rate": 2,
    "rateType": "fixed",
    "repaymentStart": "custom_date",
    "customRepaymentStartDate": "1987-08-16",
    "amountAtRepaymentStart": 38626,
    "periodicity": "monthly",
    "periodsDuration": 28,
    "prepaid": false,
    "prepaymentDate": "2007-08-16"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal reference to the liability|
|type|string|true|none|Resource type|
|attributes|object|true|none|none|
|» id|string|true|none|Internal reference to the liability|
|» rate|number|true|none|Annual interest rate. Up to two decimals. Decimals must be separated by a dot. Eg. 2.25|
|» rateType|string|false|none|Fixed or variable interest rate|
|» repaymentStart|string|false|none|Repayment start|
|» customRepaymentStartDate|string|false|none|First repayment date. YYYY-MM-DD. Ignored unless `repaymentStart` is *custom_date*.|
|» amountAtRepaymentStart|number|false|none|Loan balance on the repayment start date. Defaults to initialAmount. Up to two decimals. Decimals must be separated by a dot. Eg. 200000.55,|
|» periodicity|string|false|none|Periodicity of the principal and/or interest payment.|
|» periodsDuration|integer|false|none|Number of repayment periods. Ignored if `repaymentType` has no end date (no_end_pay_interest or no_end_capitalized_interest)|
|» prepaid|boolean|false|none|Has the loan been prepaid? (or is it expected to be prepaid at some future date?)|
|» prepaymentDate|string|false|none|Prepayment date. Defaults to current date if prepaid is set to true, otherwise ignored. *'YYYY-MM-DD'*|

#### Enumerated Values

|Property|Value|
|---|---|
|type|estateLiability|
|rateType|fixed|
|rateType|variable|
|repaymentStart|one_period_after_contract_date|
|repaymentStart|first_day_of_next_period|
|repaymentStart|last_day_of_current_period|
|repaymentStart|custom_date|
|periodicity|monthly|
|periodicity|quarterly|
|periodicity|semi_annual|
|periodicity|annual|

<h2 id="tocSrefreshvaluesinsurance">RefreshValuesInsurance</h2>

<a id="schemarefreshvaluesinsurance"></a>

```json
{
  "id": "123dfer",
  "type": "insurance",
  "attributes": {
    "id": "123dfer",
    "acquiredReserve": 2344,
    "acquiredLifeValue": 7386,
    "deathValue": 936842
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|true|none|Internal reference to the insurance|
|type|string|true|none|Resource type|
|attributes|object|true|none|none|
|» id|string|true|none|Internal reference to the insurance|
|» acquiredReserve|number|false|none|Acquired reserve / current contract value. Decimals must be separated by a dot. Eg. 200000.55|
|» acquiredLifeValue|number|false|none|Acquired value in case of life at term (assuming no additional premiums are paid).|
|» deathValue|number|false|none|Death cover amount.|
|» situationDate|string|false|none|Date at which the amounts where calculated. Must be in the past. Defaults to the begining of the current year. *YYYY-MM-DD*.|

#### Enumerated Values

|Property|Value|
|---|---|
|type|insurance|

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
|apiOnly|boolean|false|none|Filter for *'api_only'* *true* or not.|
|type|string|true|none|Filter for estate object type to search for.|
|groupIds|[string]|false|none|Group IDs to filter for.|

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
|» groupId|string|false|none|Internal ID of a group|
|» type|string|false|none|Resource type|
|» ids|[string]|false|none|Internal IDs of estate objects (`estateAsset`, `estateLiability`, `insurance`)|

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
|groupId|string|true|none|Internal ID of a group|
|type|string|true|none|Type of estate objects to be deleted|
|ids|[string]|true|none|Estate objects ids to be deleted|

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
      "locale": "nl",
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
|type|string|true|none|Resource type, not the same as `group` to not confuse with that one, this includes `group`, `groupMembership` and `dummyUser` as a whole|
|attributes|object|true|none|none|
|» dummyUsers|[[DummyUser/properties/attributes](#schemadummyuser/properties/attributes)]|true|none|DummyUser objects that represent the `familyHead` and optionally, the `partner`|
|» group|[Group/properties/attributes](#schemagroup/properties/attributes)|true|none|Attributes for the Group|
|» groupMembership|[GroupMembership/properties/attributes](#schemagroupmembership/properties/attributes)|false|none|GroupMembership of the `familyHead` current spouse|

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
|» id|string|true|none|Internal ID of the resource to be updated.|
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
  "self": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=3&page%5Bsize%5D=50",
  "first": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=1&page%5Bsize%5D=50",
  "prev": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=2&page%5Bsize%5D=50",
  "next": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=4&page%5Bsize%5D=50",
  "last": "https://subdomain.paxfamilia.com/api/v1/company-units?page%5Bnumber%5D=5&page%5Bsize%5D=50"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|self|string|true|none|Link to the current page of the collection.|
|first|string|true|none|Link to the first page of the collection.|
|prev|string|true|none|Link to the previous page of the collection.|
|next|string|true|none|Link to the next page of the collection.|
|last|string|true|none|Link to the last page of the collection.|

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
  "description": "This is the first version of the **PaxFamilia API**. You can find out more about **PaxFamilia** at our [website](https://www.paxfamilia.com/).",
  "documentation": "https://www.paxfamilia.com/",
  "termsOfService": "https://www.paxfamilia.com/hubfs/Conditions%20g%C3%A9n%C3%A9rales/CGU_PaxFamilia_B2B_V3_clean%2026112018.pdf?hsLang=fr-fr",

  "name": "Falcon Alpha Phoenix"
}
</script>

