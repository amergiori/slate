---
title: Seller API

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - php
  - python
  - javascript

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Gigsberg API! You can use our API to access API endpoints, which can get information on various events, listings, categories, orders & addresses.

We have language bindings in Php, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

<!-- ```python
import kittn

api = kittn.authorize('meowmeowmeow')
``` -->


<!-- ```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key. -->

Gigsberg API uses secret key to allow access to the API. A secret key must be provided to you by our team.
Gigsberg API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`x-api-key: TOKEN`

<aside class="notice">
You must replace <code>TOKEN</code> with secret key.
</aside>

# Events

## Get All Events

```php
  $url = `http://integration.gigsberg.com/v1/event/search`;
  $header[] = "Accept: application/json";
  $post_data = json_encode([
            'id'            => int,
            'name'          => string,
            'city'          => string,
            'date'          => [
                'from'      => 'dd/mm/yyyy',
                'to'        => 'dd/mm/yyyy'
            ],
            'venue'         => string,
            'performer1'    => string,
            'performer2'    => string
  ]);

  $ch = curl_init();
  curl_setopt($ch, CURLOPT_URL, $url);
  curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BEARER);
  curl_setopt($ch, CURLOPT_POST, 1);
  curl_setopt($ch, CURLOPT_POSTFIELDS, $post_data);

  curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
  curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);

  $error = curl_error($ch);
  $result = curl_exec($ch);
  $output = json_decode($result, true);
```

```python
```

```javascript
```

> The above command returns JSON structured like this:

```json
{
    "id": 111111,
    "name": "Test Event",
    "subType_id": 111,
    "subType": null,
    "date": "2024-05-31",
    "time": "19:30:00",
    "venue_id": 121212,
    "performer1_id": 222222,
    "performer2_id": 3333333,
    "performer1": "Gigsberg",
    "performer2": "Gigsberg 2",
    "country": "United States",
    "city": "New York",
    "venue": "The Rooftop at Pier 17",
    "tour": "",
    "categories": {
        "42": {
            "General Admission": [
                "General Admission"
            ]
        },
        "363": {
            "Silver": [
                "Heineken Zone"
            ]
        }
    }
}
```

This endpoint retrieves all events.

Parameter | value | Description
--------- | ------- | -----------
id | string | listing id
name | string | event's name
city | string | city's name
date[from] | string | date from dd/mm/yyyyy
date[to] | string | date
venue | string | venue's name
performer1 | string | performer's name
performer2 | string | performer's name


# Listings

## Get All Listings

```php
  $url = `http://integration.gigsberg.com/v1/listing/search`;
  $header[] = "Accept: application/json";
  $post_data = json_encode([
            'id'            => int,
            'block'         => string,
            'category'      => string,
            'currency'      => string,
            'split_type'    => string,
            'event'         => string,
            'event_id'      => int,
            'event_date'    => [
                'from'      => 'dd/mm/yyyy',
                'to'        => 'dd/mm/yyyy'
            ],
            'venue'        => string
  ]);

  $ch = curl_init();
  curl_setopt($ch, CURLOPT_URL, $url);
  curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BEARER);
  curl_setopt($ch, CURLOPT_POST, 1);
  curl_setopt($ch, CURLOPT_POSTFIELDS, $post_data);

  curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
  curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);

  $error = curl_error($ch);
  $result = curl_exec($ch);
  $output = json_decode($result, true);
```

<!-- ```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

> The above command returns JSON structured like this:

```json
{
    "items": [
        {
            "id": 111111,
            "event_id": 11111,
            "block": null,
            "row": "C",
            "quantity": 1,
            "ticket_type": "Mobile Ticket",
            "uploaded": 1,
            "listing_split_type": "dont_leave_one",
            "seat_start": 44,
            "seat_end": 46,
            "currency": "Pound Sterling",
            "checkout_url": "https://gigsberg.com/checkout...",
            "category_name": "Stalls Seating",
            "restrictions": [
                "Children under 15 must be accompanied by an Adult"
            ],
            "price": {
                "POUND_STERLING": 117.26,
                "EURO": 136.51,
                "US_DOLLARS": 149.62,
                "AUSTRALIAN_DOLLAR": 222.78,
                "PLOLISH_ZLOTY": 591.36,
                "CZECH_KORUNA": 3345.45,
                "NEW_ISRAELY_SHEKEL": 554.64,
                "SWISS_FRANC": 126.82
            },
            "fees": {
                "POUND_STERLING": 42.11,
                "EURO": 49.02,
                "US_DOLLARS": 53.72,
                "AUSTRALIAN_DOLLAR": 79.99,
                "PLOLISH_ZLOTY": 212.32,
                "CZECH_KORUNA": 1201.14,
                "NEW_ISRAELY_SHEKEL": 199.14,
                "SWISS_FRANC": 45.53
            },
            "event": "Test Event",
            "category": {
                "Stalls Seating": [
                    "Stalls Seating"
                ]
            }
        },
    ]
}
```

This endpoint retrieves all events.

Parameter | value | Description
--------- | ------- | -----------
id | string | listing id
block | string | block name
category | string | category name
currency | string | currency name: Pound Sterling, Euro, US Dollars, Australian Dollar, Plolish Zloty, Czech koruna, New Israely Shekel, Swiss Franc
split_type | string | split type:  any, none, pairs, two_per_order, dont_leave_one
event | string | block name
event_id | int | event id
event_date[from] | string | inquery start date
event_date[to] | string | inquery end date
venue | string | block name

# Affiliate Orders

## Get Affiliate Order

```php
  $url = `http://integration.gigsberg.com/v1/affiliate-order/search`;
  $header[] = "Accept: application/json";
  $post_data = json_encode([
            'order_id'            => int,
            'time'    => [
                'from'      => 'dd/mm/yyyy',
                'to'        => 'dd/mm/yyyy'
            ],
  ]);

  $ch = curl_init();
  curl_setopt($ch, CURLOPT_URL, $url);
  curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BEARER);
  curl_setopt($ch, CURLOPT_POST, 1);
  curl_setopt($ch, CURLOPT_POSTFIELDS, $post_data);

  curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
  curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);

  $error = curl_error($ch);
  $result = curl_exec($ch);
  $output = json_decode($result, true);
```

<!-- ```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

> The above command returns JSON structured like this:

```json
{
    "items": [
        {
            "id": 111111,
            "order_id": 111111,
            "currency": "Pound Sterling",
            "total_price": "352.000",
            "timestamp": "2024-02-13 05:38:20",
            "url": "url",
            "status": "Stripe Waiting",
            "domain": "seatpick.com"
        },
    ]
}
```

This endpoint retrieves all events.

Parameter | value | Description
--------- | ------- | -----------
order_id | string | order id
time[from] | string | inquery start date
time[to] | string | inquery end date
