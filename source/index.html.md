---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:

search: true
---

# Introduction

This page contains the documentation for the <a href='https://midwaylondon.com'>MidWay London</a> API.

With this API, you can create a MidWay event and use our algorithms to find the midpoint of up to 20 locations to enhance your service.

Code examples can be viewed in the area to the right.

# Authentication

> To authorise, use this code:

```javascript
  ...

  client = new MidWayClient(<API_Key>, <API_Token>);
```

> Make sure to replace `<API_Key>` with your API key and `<API_Token>` with your API token.



<aside class="notice">
You must replace <code>&ltAPI_Key&gt</code> with your personal API key.
</aside>

# MidWay Now

## Now

```javascript
  ...

  client = new MidWayClient(<API_Key>, <API_Token>);

  const body = {
    "form-TOTAL_FORMS": 2,
    "form-INITIAL_FORMS": 0,
    "form-0-lat": 51.5347488,
    "form-0-lng": -0.1245845,
    "form-0-name": "Kings Cross",
    "form-1-lat": 51.41833889999999,
    "form-1-lng": -0.2206288,
    "form-1-name": "Wimbledon",
  }

  client.CreateNowEvent(body);
```

This endpoint creates an event with MidWay Now, our event planning tool.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/now`

### Query Parameters

Parameter | Description
--------- | -----------
form-TOTAL_FORMS | Number of locations
form-INITIAL_FORMS | Should be 0 for a now event
form-\<n\>-lat | Latitude of location
form-\<n\>-lng | Longitude of location
form-\<n\>-name | User-provided name for the location

<aside class="notice">
Replace <code>&ltn&gt</code> in the parameter name with the number of the location form (0, 1, ..., n)
</aside>
<aside class="warning">
<code>form-TOTAL_FORMS</code> must be at least 2, and must equal the number of forms submitted
</aside>

## Resolve

```javascript

```

This endpoint submits a choice of venue for a given event.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/resolve`

### URL Parameters

Parameter | Description
--------- | -----------
Event | The ID of the event to be resolved
Venue | The ID of the venue to submit for the event

## Suggestions

```javascript

```

This endpoint gets venue suggestions for a given event.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/suggestions`

### URL Parameters

Parameter | Description
--------- | -----------

## Details

```javascript

```

This endpoint gets details about a given venue.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/details`

### URL Parameters

Parameter | Description
--------- | -----------

## Login

```javascript

```

This endpoint provides a way to login to a MidWay London account.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/login`

### URL Parameters

Parameter | Description
--------- | -----------

## Events

```javascript

```

This endpoint gets a list of all events for the logged in user.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/events`

### URL Parameters

Parameter | Description
--------- | -----------
