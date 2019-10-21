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

Welcome to the MidWay API. With this API, you can create MidWay events or use our algorithm to find the midpoint of up to 20 locations to enhance your own service.

Code examples can be viewed in the area to the right.

# Authentication

> To authorise, use this code:

```javascript

```

> Make sure to replace `<API_Key>` with your API key and `<API_Token>` with your API token.



<aside class="notice">
You must replace <code>&ltAPI_Key&gt</code> with your personal API key.
</aside>

# MidWay Now

## Now

```javascript

```

This endpoint creates an event with MidWay Now, our event planning tool.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/now`

### Query Parameters

Parameter | Description
--------- | -----------
form-TOTAL_FORMS | Number of locations (>= 2)
form-INITIAL_FORMS | Should be 0 for a now event
form-\<n\>-lat | latitude of location
form-\<n\>-lng | longitude of location
form-\<n\>-name | user-provided name for the location

<aside class="notice">
Replace <code>&ltn&gt</code> in the parameter name with the number of the location form (1, 2, ..., n)
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
Event | The ID of the event to submit a venue for
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
