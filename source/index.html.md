---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:

search: true
---

# Introduction

This page contains the documentation for the <a href='https://www.midwaylondon.com'>MidWay London</a> API.

With this API, you can create a MidWay event and use our algorithms to find the midpoint of up to 20 locations to enhance your service.

Code examples can be viewed in the area to the right.

# Authentication

> To install, run the following in your terminal:

```javascript
  npm install midway-js
```

```python
  pip install midwayPy
```

> To authorise, use this code:

```javascript
  import MidwayClient from 'midway-js';

  client = new MidwayClient(<API_Key>, <API_Token>);
```

```python
  import MidwayClient from midwayPy

  client = MidwayClient(<API_Key>, <API_Token>)
```

> Make sure to replace `<API_Key>` with your API key and `<API_Token>` with your API token.

Follow <a href="#">this link</a> to sign up for an API key.

Install the MidWay Client for JavaScript or Python and include it in your source.

<aside class="notice">
You must replace <code>&ltAPI_Key&gt</code> with your personal API key.
</aside>

# Interfaces

## MidwayEvent

Information about a MidWay Event

Property | Type | Description
-------- | ---- | -----------
`id` | `string` | The unique id of the event
`name` | `string` | The given name of the event
`date` | `string` | The date on which the event takes place
`endtime` | `string` |
`description` | `string` | The given description of the event
`is_open` | `boolean` | Flag to indicate whether the event is accepting responses
`created` | `string` |
`venue` | <code>string &verbar; null</code> | Chosen venue for the event, null if venue not yet chosen

<aside class="notice">
See <a href="#now">now</a> documentation for default MidWay Now values
</aside>

## PlaceDetails


Property | Type | Description
-------- | ---- | -----------
`id` | `string` | The unique id of the place
`name` | `string` | The given name of the place
`formatted_address` | `string` |
`place_id` | `string` |
`reference` | `string` |
`geometry` | `Object` | Information about the location of the place

### geometry

Property | Type | Description
-------- | ---- | -----------
`location` | `LatLng` | Latitude and Longitude of the location
`viewport` | `Object` |

### LatLng

Property | Type | Description
-------- | ---- | -----------
`lat` | `number` | Latitude of the Object
`lng` | `number` | Longitude of the Object

# MidWay Now

## Now

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

  // in this example we create an array of two PlaceDetails objects: Kings Cross and Wimbledon
  const locations = [
    {
      id: 1,
      name: "Kings Cross",
      formatted_address: "",
      place_id: "",
      reference: "",
      geometry: {
        location: {
          lat: 51.5347488,
          lng: -0.1245845,
        },
        viewport: {

        },
      },
    },
    {
      id: 2,
      name: "Wimbledon",
      formatted_address: "",
      place_id: "",
      reference: "",
      geometry: {
        location: {
          lat: 51.41833889999999,
          lng: -0.2206288,
        },
        viewport: {

        },
      },
    },
  ];

  client.CreateNowEvent(locations);
```

This endpoint creates an event with MidWay Now, our event planning tool.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/now`

### URL Parameters

Parameter | Description
--------- | -----------
`form-TOTAL_FORMS` | Number of locations
`form-INITIAL_FORMS` | Should be 0 for a now event
`form-<n>-lat` | Latitude of location
`form-<n>-lng` | Longitude of location
`form-<n>-name` | User-provided name for the location

<aside class="notice">
Replace <code>&ltn&gt</code> in the parameter name with the number of the location form (0, 1, ..., n)
</aside>
<aside class="warning">
<code>form-TOTAL_FORMS</code> must be at least 2, and must equal the number of forms submitted
</aside>

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
`locations` | `PlaceDetails[]` | The starting locations for the event

<aside class="warning">
<code>locations</code> must be an array with length of at least 2
</aside>

### Returns
A <a href="#midwayevent">MidWay Event</a> with the following default values:

Property | Default
-------- | -------
`name` | "Quick event"
`date` | Date of event creation
`is_open` | false

## Suggestions

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

  const locations = [...];
  const event = client.CreateNowEvent(locations);

  client.GetSuggestions(event.id);

```

This endpoint gets venue suggestions for a given event.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/suggestions`

### Query Parameters

Parameter | Description
--------- | -----------
`eventId` | Unique id of the event to get suggestions for

## Details

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

  const locations = [...];
  const event = client.CreateNowEvent(locations);
  const venue = client.GetSuggestions(event.id).venues[0];

  client.GetDetails(venue);
```

This endpoint gets details about a given venue.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/details`

### Query Parameters

Parameter | Description
--------- | -----------
`place_id` | Unique id of the venue to get details for

## Resolve

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

  const locations = [...];
  const event = client.CreateNowEvent(locations);
  const venue = client.GetSuggestions(event.id).venues[0];

  client.Resolve(event.id, venue.id);
```

This endpoint submits a choice of venue for a given event.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/resolve`

### Query Parameters

Parameter | Description
--------- | -----------
`event` | The ID of the event to be resolved
`venue` | The ID of the venue to submit for the event

## Login

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

```

This endpoint provides a way to login to a MidWay London account.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/login`

### Query Parameters

Parameter | Description
--------- | -----------

## Events

```javascript
  ...

  client = new MidwayClient(<API_Key>, <API_Token>);

```

This endpoint gets a list of all events for the logged in user.

### HTTP Request

`GET https://www.midwaylondon.com/api/v1/events`

### Query Parameters

Parameter | Description
--------- | -----------
