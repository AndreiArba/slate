---
title: API Reference

language_tabs:
  - Api Response

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - statuses
  - errors

search: true
---

# Introduction

Welcome to the Shooble API! You can use our API to access Shooble API endpoints

# Authentication

## Register

> The command returns JSON structured like this:

```json
{
  "data": {
    "authToken": "f5a87aa0917deb621b43d3291d330dc0e5c4a8dc",
    "user": {
      "username": "testandrei3",
      "email": "andrei.arba@bitstone.eu",
      "firstname": "Andrei",
      "lastname": "Arba",
      "phone": "0753174814",
      "updated_at": "2016-04-13 15:30:19",
      "created_at": "2016-04-13 15:30:19",
      "id": 227
    }
  },
  "status": "success"
}
```

This endpoint is used just temporary in order to have some test data.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/register`

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
username | false | must be unique
password | false | must have minimum 6 characters
firstname | true | used to have detailed informations about the user
lastname | true | used to have detailed informations about the user
email | false | must be a valid email address, will be used to send notifications
phone | false | must be a valid phone number, will be used to send notifications
gender | true | used to have detailed informations about the user

<aside class="success">
Success — a test user is registered!
</aside>

## Login

> The above command returns JSON structured like this:

```json
{
  "data": {
    "authToken": "11974e7892313ad0dd7f084ee5969087d9e61f43",
    "user": {
      "id": 227,
      "username": "testandrei3",
      "firstname": "Andrei",
      "lastname": "Arba",
      "email": "andrei.arba@bitstone.eu",
      "active": null,
      "member_of": null,
      "link_id": null,
      "role": "",
      "counter": null,
      "created": null,
      "lastlogin": null,
      "hyvesnaam": null,
      "image": null,
      "user_type": null,
      "gender": null,
      "initials": null,
      "phone": "0753174814",
      "mobile": null,
      "see_holding": null,
      "default_holding": 0,
      "facebook_username": null,
      "linkedin_username": null,
      "facebook_token": null,
      "facebook_id": null,
      "planner_group": null,
      "office_type": null,
      "ext_id": null,
      "language": null,
      "lastsync_master": null,
      "lastsync_slave": null,
      "created_at": "2016-04-13 15:30:19",
      "updated_at": "2016-04-13 15:30:19"
    }
  },
  "status": "success"
}
```

This endpoint is used for authentication. On a successful attempt, a token will be send on response, used for the future api calls.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/login`

### URL Parameters

Parameter | Optional |Description
--------- | --------- | ------------
username | false |
password | false |

<aside class="success">
Success — a user is authenticated and able to make api calls!
</aside>

## Logout

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success"
  },
  "status": "success"
}
```

This endpoint is used just temporary in order to have some test data.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/logout`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

<aside class="success">
Success — a test user is registered!
</aside>

# Reset Password

## Remind

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success   --we can remove this if it's not used"
  },
  "status": "success"
}
```

This endpoint is used to generate the reset password link. The link will be the url of the consumer ended by /reset-link?token=some_token
The token needs to be added in the following reset request.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/remind`

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
email | false | must be a valid email address, will be used to send the reset link

<aside class="success">
Success — an email with password reset link is send to the user!
</aside>

## Reset

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success   --we can remove this if it's not used"
  },
  "status": "success"
}
```

This endpoint is used to reset a user password.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/reset`

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
reset_token | false | must be a valid token received in the reset email
password | false | must have at least 6 characters
password_confirm | false | must be the same as password

<aside class="success">
Success — the password will be reset!
</aside>

# User

## Update profile

> The command returns JSON structured like this:

```json
{
  "data": {
    "id": 225,
    "username": "testandrei",
    "firstname": "Andrei",
    "lastname": "Arba",
    "email": "andrei.arba@bitstone.eu",
    "active": null,
    "member_of": null,
    "link_id": null,
    "role": "",
    "counter": null,
    "created": null,
    "lastlogin": null,
    "hyvesnaam": null,
    "image": null,
    "user_type": "test",
    "gender": "male",
    "initials": null,
    "phone": "0753174814",
    "mobile": "0744444444",
    "see_holding": null,
    "default_holding": 0,
    "facebook_username": null,
    "linkedin_username": null,
    "facebook_token": null,
    "facebook_id": null,
    "planner_group": null,
    "office_type": null,
    "ext_id": null,
    "language": null,
    "lastsync_master": null,
    "lastsync_slave": null,
    "created_at": "2016-04-11 17:19:59",
    "updated_at": "2016-04-13 14:15:23"
  },
  "status": "success"
}
```

This endpoint is used to update the user details, here we can add more fields once we define them.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/profile`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
firstname | true | used to have detailed informations about the user
lastname | true | used to have detailed informations about the user
email | false | must be a valid email address, will be used to send notifications
phone | false | must be a valid phone number, will be used to send notifications
gender | true | used to have detailed informations about the user

<aside class="warning">
Invalid token — a 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — a test user is registered!
</aside>


# Work

## List of jobs

> The command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "client": "Filiaal",
      "time": "2015-12-31 00:00:00",
      "location": ""
    },
    {
      "id": 2,
      "client": "AHBC",
      "time": "2016-01-01 00:00:00",
      "location": "Nieuwe Kalfjeslaan  19,Amstelveen"
    },
    {
      "id": 11,
      "client": "Amsterdam",
      "time": "2016-01-21 00:00:00",
      "location": "Arena Boulevard 155,Amsterdam"
    },
    {
      "id": 14,
      "client": "Amsterdam",
      "time": "2016-01-26 00:00:00",
      "location": "Arena Boulevard 155,Amsterdam"
    },
    {
      "id": 17,
      "client": "Amsterdam",
      "time": "2016-01-29 00:00:00",
      "location": "Arena Boulevard 155,Amsterdam"
    },
    {
      "id": 4,
      "client": "Reserve / Stand by",
      "time": "2016-04-14 00:00:00",
      "location": ""
    }
  ],
  "status": "success"
}
```

This endpoint is used to display the jobs tables, future jobs, my jobs and jobs completed but without the hours filled.

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/work`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
type | true | possible values all/future/unfilled - default is all
startdate | true | start date filter for the jobs
enddate | true | end date filter for the jobs, if startdate and enddate are set this filter type has priority over period
period | true | filter for period, possible values: week/month/year - default is week

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — a list of jobs filtered by the parameters!
</aside>

## Job details

> The command returns JSON structured like this:

```json
{
  "data": {
    "details": {
      "client": "Filiaal",
      "job_type": "",
      "pickup_place": "",
      "time_logged": "",
      "date_time": "",
      "address": "Avenue Ceramique 221,Maastricht"
    },
    "colleagues": [
      {
        "id": 177,
        "firstname": "Maarten",
        "lastname": "Mannaerts",
        "email": "andrei.arba@bitstone.eu",
        "phone": "+31653572956"
      },
      {
        "id": 196,
        "firstname": "Bobby",
        "lastname": "Grobben",
        "email": "andrei.arba@bitstone.eu",
        "phone": "0297272703"
      }
    ]
  },
  "status": "success"
}
```

This endpoint is used to display the job details.

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/work/<ID>`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

No parameters for this endpoint

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the job details
</aside>



