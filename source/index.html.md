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
      "image": "uploads/users/242/0gqbu1.jpg",
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
image | true | must be type png,jpg,jpeg,gif,JPG,JPEG,GIF,PDF,PNG

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
image | true | must be type png,jpg,jpeg,gif,JPG,JPEG,GIF,PDF,PNG

<aside class="warning">
Invalid token — a 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — a test user is registered!
</aside>

## Profile details

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

This endpoint is used to return the user details, here we can return more fields once we define them.

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/profile`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### Query Parameters

No parameters for this endpoint

<aside class="warning">
Invalid token — a 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — user details!
</aside>

## Change password

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

This endpoint is used to change user password

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/change-password`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
old_password | true | must match with the password saved in DB
new_password | true | must have minimum 6 characters
confirm_password | false | must match with new_password

<aside class="warning">
Invalid token — a 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — user details!
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
      "fillial_location": "",
      "log_work_allowed": true
       "-- true if employee can log hours, only for my jobs and jobs completed but without the hours filled",
       "apply_allowed" : true
       "--true if employee can apply to the job",
       "supervisor": 0 "-- 1 if user is a supervisor"
    },
    {
      "id": 2,
      "client": "AHBC",
      "time": "2016-01-01 00:00:00",
      "fillial_location": "Nieuwe Kalfjeslaan  19,Amstelveen",
      "log_work_allowed": true,
      "apply_allowed" : true
      "supervisor": 0
    },
    {
      "id": 11,
      "client": "Amsterdam",
      "time": "2016-01-21 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : false
      "supervisor": 0
    },
    {
      "id": 14,
      "client": "Amsterdam",
      "time": "2016-01-26 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : true
      "supervisor": 0
    },
    {
      "id": 17,
      "client": "Amsterdam",
      "time": "2016-01-29 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : true
      "supervisor": 1
    },
    {
      "id": 4,
      "client": "Reserve / Stand by",
      "time": "2016-04-14 00:00:00",
      "fillial_location": "",
      "log_work_allowed": true,
      "apply_allowed" : true
    }
  ],
  "status": "success"
}
```

This endpoint is used to display the jobs tables, my future jobs, my jobs and jobs completed but without the hours filled.

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
device | true | must be type mobile or desktop

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
      "fillial_address": "Avenue Ceramique 221,Maastricht",
      "address": "Cluj, Zorilor, 435241",
      "log_work_allowed": true,
      "apply_allowed": false,
      "invite_id" : 1234,
      "shift_id": 12,
      "client_rating" : 3,
      "job_type_rating" : 2,
      "colleagues_rating" : 5,
      "start_time": "2016-06-09 18:55:30",
      "end_time": "2016-06-09 21:55:30",
      "pickup_place": "Cluj-Napoca, Caraiman nr 1",
      "pickup_time" : "2016-02-21 0:00:00",
      "subject" : "Shooble",
      "description" : "Test test test",
      "supervisor": 0 "-- 1 if user is a supervisor",
      "agenda_id" : 99123
    },
    "colleagues": [
      {
        "id": 177,
        "firstname": "Maarten",
        "lastname": "Mannaerts",
        "email": "andrei.arba@bitstone.eu",
        "phone": "+31653572956",
        "image" : ""
      },
      {
        "id": 196,
        "firstname": "Bobby",
        "lastname": "Grobben",
        "email": "andrei.arba@bitstone.eu",
        "phone": "0297272703",
        "image" : ""
      }
    ],
    "checkpoints": [
      {
        "subject": "Shooble2 23",
        "start_time": "2016-04-25 00:00:00",
        "klant": 1518,
        "location_street": null,
        "location_postal_code": null,
        "location_place": null,
        "checkpoint_id": 52,
        "template_id": 52,
        "type": "0",
        "checkpoint_timeframe_id": 52,
        "agenda_invite_id": 1311,
        "timestamp": "2016-05-03 12:35:31"
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

Parameter | Optional | Description
--------- | ------- | -----------
device | true | must be type mobile or desktop

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the job details
</aside>

## Evaluation on job details

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success   --we can remove this if it's not used"
  },
  "status": "success"
}
```

This endpoint is used by supervisor to evaluate client/job type/colleagues
ONLY supervisor can evaluate

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/work-evaluation`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | shift_id from job details
rating | false | specific rating
type | false | should be a value from: client/job_type/colleagues

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the job details
</aside>

## Checkin

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success   --we can remove this if it's not used"
  },
  "status": "success"
}
```

This endpoint is used to checkin on a checkpoint in a specific job

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/checkin`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
employee_id | false | array of employee ids
checkpoint_id | false | checkpoint id
unchecked | false | true if user wants to remove checkpoint, false otherwise

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success
</aside>

## My availability dates

> The command returns JSON structured like this:

```json
{
  "data": [
      {
        "id": 24,
        "plan_time": "2016-01-02 00:00:00",
        "employee": 115,
        "available": [
          "a",
          "e"
        ],
        "comment": "",
        "transport": {
          "type": "",
          "seats": 0
        }
      },
      {
        "id": 36,
        "plan_time": "2016-01-07 00:00:00",
        "employee": 115,
        "available": [
          "a",
          "e"
        ],
        "comment": "",
        "transport": {
          "type": "",
          "seats": 0
        }
      }
    ],
  "status": "success"
}
```

This endpoint is used to display availability dates for user.

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/availability`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
startdate | false | start date filter for the availability dates
period | false | filter for period, possible values: week/month/year - default is week

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the availability dates
</aside>

## Update/Create availability dates

> The command returns JSON structured like this:

```json
{
  "data": {
      "status": "success   --we can remove this if it's not used"
    },
    "status": "success"
}
```

This endpoint is used to display availability dates for user.
Make the request both on pagination and on submit

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/availability`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
array of availability dates | false | array of availability dates

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the availability dates will be created or updated!
</aside>

## Log work

> The command returns JSON structured like this:

```json
{
  "data": {
      "status": "success   --we can remove this if it's not used"
    },
    "status": "success"
}
```

This endpoint is used to log hours.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/log-work`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | id of the job(agenda id)
start_time | false | start time of the job (ex: HH:mm:ss)
end_time | false | end time of the job (ex: HH:mm:ss)
break | true | an integer with number of minutes
employee_id | false | array of employee ids

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success
</aside>

## Set supervisor

> The command returns JSON structured like this:

```json
{
  "data": {
      "status": "success   --we can remove this if it's not used"
    },
    "status": "success"
}
```

This endpoint is used to set current user as supervisor on specific job.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/supervisor`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | id of the job(agenda id)

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success
</aside>


