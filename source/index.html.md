---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript
  - clojure
  - c++
  - c
  - java
  - php
  - lua
  - C#
  - rust
  - perl
  - haskell
  - PowerShell
  - swift
  - scala
  - go

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Ltd API! You can use our API to access Ltd API endpoints, which can get information on various entities, reports, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'ltd'

api = Ltd::APIClient.authorize!('subscription_api_token')
```

```python
import ltd

api = ltd.authorize('subscription_api_token')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: subscription_api_token"
```

```javascript
const ltd = require('ltd');

let api = ltd.authorize('subscription_api_token');
```

> Make sure to replace `subscription_api_token` with your API key.

Ltd uses API keys to allow access to the API. You can register a new Ltd API key at our [developer portal](https://ltdapi.com/developers).

Ltd expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: subscription_api_token`

<aside class="notice">
You must replace <code>subscription_api_token</code> with your personal API key.
</aside>

# Reports

## Get All Reports

```ruby
require 'ltd'

api = Ltd::APIClient.authorize!('subscription_api_token')
api.reports.get
```

```python
import ltd

api = ltd.authorize('subscription_api_token')
api.reports.get()
```

```shell
curl "http://example.com/api/reports"
  -H "Authorization: subscription_api_token"
```

```javascript
const ltd = require('ltd');

let api = ltd.authorize('subscription_api_token');
let reports = api.reports.get();
```

> The above command returns JSON structured like this:

```json
[
{
  "id": 1,
  "name": "total-filing-amount",
  "registrant": 682,
  "date_range_start": 20150101,
  "date_range_end": 20180101,
}
{
  "id": 2,
  "name": "clients-per-issue",
  "registrant": 682,
  "date_range_start": 20150101,
  "date_range_end": 20180101,
}
]
```

This endpoint retrieves all reports.

### HTTP Request

`GET http://example.com/api/reports`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_entities | false | If set to true, the result will also include entities.
available | true | If set to false, the result will include reports that have already been adopted.

<aside class="success">
Remember — a happy report is an authenticated report!
</aside>

## Get a Specific Report

```ruby
require 'ltd'

api = Ltd::APIClient.authorize!('subscription_api_token')
api.reports.get(2)
```

```python
import ltd

api = ltd.authorize('subscription_api_token')
api.reports.get(2)
```

```shell
curl "http://example.com/api/reports/2"
  -H "Authorization: subscription_api_token"
```

```javascript
const ltd = require('ltd');

let api = ltd.authorize('subscription_api_token');
let max = api.reports.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "clients-per-issue",
  "registrant": "unknown",
  "date_range_start": 20150101,
  "date_range_end": 20180101,
}
```

This endpoint retrieves a specific report.
### HTTP Request

`GET http://example.com/reports/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the report to retrieve

