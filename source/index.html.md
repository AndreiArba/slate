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
      "phone": "0753174800",
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

### POST Parameters

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
      "role": "",
      "image": null,
      "user_type": null,
      "gender": null,
      "phone": "0753174800",
      "mobile": null,
      "facebook_username": null,
      "linkedin_username": null,
      "facebook_token": null,
      "facebook_id": null,
      "language": null,
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

### POST Parameters

Parameter | Optional |Description
--------- | --------- | ------------
username | false | username
password | false | password
remember | true | true or false, if true authToken will be available for 3 years otherwise 24 hours

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

This endpoint is used to logout current user.

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
    "status": "success"
  },
  "status": "success"
}
```

This endpoint is used to generate the reset password link. The link will be the url of the consumer ended by /reset-link?token=some_token
The token needs to be added in the following reset request.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/remind`

### POST Parameters

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
    "status": "success"
  },
  "status": "success"
}
```

This endpoint is used to reset a user password.

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/reset`

### POST Parameters

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
      "authToken": "11974e7892313ad0dd7f084ee5969087d9e61f43",
      "user": {
        "id": 227,
        "username": "testandrei3",
        "firstname": "Andrei",
        "lastname": "Arba",
        "email": "andrei.arba@bitstone.eu",
        "role": "",
        "image": null,
        "user_type": null,
        "gender": null,
        "phone": "0753174800",
        "mobile": null,
        "facebook_username": null,
        "linkedin_username": null,
        "facebook_token": null,
        "facebook_id": null,
        "language": null
      }
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

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
firstname | true | used to have detailed informations about the user
lastname | true | used to have detailed informations about the user
email | false | must be a valid email address, will be used to send notifications
phone | false | must be a valid phone number, will be used to send notifications
gender | true | used to have detailed informations about the user
image | true | image path

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
      "authToken": "11974e7892313ad0dd7f084ee5969087d9e61f43",
      "user": {
        "id": 227,
        "username": "testandrei3",
        "firstname": "Andrei",
        "lastname": "Arba",
        "email": "andrei.arba@bitstone.eu",
        "role": "",
        "image": null,
        "user_type": null,
        "gender": null,
        "phone": "0753174800",
        "mobile": null,
        "facebook_username": null,
        "linkedin_username": null,
        "facebook_token": null,
        "facebook_id": null,
        "language": null
      }
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
      "authToken": "11974e7892313ad0dd7f084ee5969087d9e61f43",
      "user": {
        "id": 227,
        "username": "testandrei3",
        "firstname": "Andrei",
        "lastname": "Arba",
        "email": "andrei.arba@bitstone.eu",
        "role": "",
        "image": null,
        "user_type": null,
        "gender": null,
        "phone": "0753174800",
        "mobile": null,
        "facebook_username": null,
        "linkedin_username": null,
        "facebook_token": null,
        "facebook_id": null,
        "language": null
      }
    },
    "status": "success"
}
```

This endpoint is used to change user password

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/change-password`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### POST Parameters

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
      "apply_allowed" : true,
      "supervisor": 0
    },
    {
      "id": 11,
      "client": "Amsterdam",
      "time": "2016-01-21 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : false,
      "supervisor": 0
    },
    {
      "id": 14,
      "client": "Amsterdam",
      "time": "2016-01-26 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : true,
      "supervisor": 0
    },
    {
      "id": 17,
      "client": "Amsterdam",
      "time": "2016-01-29 00:00:00",
      "fillial_location": "Arena Boulevard 155,Amsterdam",
      "log_work_allowed": true,
      "apply_allowed" : true,
      "supervisor": 1
    },
    {
      "id": 4,
      "client": "Reserve / Stand by",
      "time": "2016-04-14 00:00:00",
      "fillial_location": "",
      "log_work_allowed": true,
      "apply_allowed" : true,
    }
  ],
  "status": "success"
}
```

This endpoint is used to display the jobs tables: my future jobs, my jobs and jobs completed but without the hours filled.

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
startdate | true | start date filter for the jobs (EX: YYYY-MM-DD)
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
      "client": "Blokker",
      "job_type": "Bediening",
      "start_time": "2016-02-14 11:00:00",
      "end_time": "2016-02-14 21:00:00",
      "pickup_place": "Badhuispleon 7, Zandvoort",
      "invite_id": 1047,
      "supervisor": 0,
      "shift_id": 23,
      "client_rating": 0,
      "job_type_rating": 0,
      "colleagues_rating": 0,
      "pickup_time": "2016-01-31 12:30:00",
      "subject": "Landgoed Huize Glory",
      "description": "Shooble description",
      "agenda_id": 37,
      "log_work_allowed": true,
      "apply_allowed": false,
      "time_logged": "",
      "fillial_address": "Westerblokker 80,Blokker",
      "address": "Badhuispleon 7, Zandvoort, 2042 JB",
      "briefing_name": "Briefing Meijer aan Zee",
      "briefing": "<strong>Van de website:</strong><br />\r\n&lsquo;Strandrestaurant Meijer aan Zee heet u .."
    },
    "colleagues": [
        {
          "id": 236,
          "firstname": "Andreiiii",
          "lastname": "Arbaaa",
          "email": "andrei.arba@bitstone.eu",
          "phone": "123456789",
          "image": null
        },
        {
          "id": 248,
          "firstname": "Bitstone11",
          "lastname": "Test11",
          "email": "andrei.arba@bitstone.eu",
          "phone": "123456789",
          "image": null
        }
    ],
    "checkpoints": [
    {
        "subject": "Shooble2 25",
        "start_time": "2016-06-09 18:55:30",
        "checkpoint_id": 5,
        "employee_id": 1339,
        "timestamp": "2016-04-28 14:42:55",
        "address": "Badhuispleon 7, Zandvoort, 2042 JB",
        "checked": false,
        "read_only": true
      },
      {
        "subject": "Shooble2 25",
        "start_time": "2016-06-09 18:55:30",
        "checkpoint_id": 6,
        "employee_id": 1339,
        "timestamp": "2016-04-28 14:42:55",
        "address": "Badhuispleon 7, Zandvoort, 2042 JB",
        "checked": false,
        "read_only": true
      }
    ],
    "questions": [
      {
        "id": 31,
        "options": [
          {
            "label": "dolorem",
            "name": "consectetur",
            "type": "signature",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "qui",
            "name": "totam",
            "type": "textarea",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "illo",
            "name": "laudantium",
            "type": "signature",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "delectus",
            "name": "esse",
            "type": "upload",
            "validation": {
              "is_required": true
            }
          }
        ],
        "shift_id": 23,
        "all_colleagues": 0,
        "answered": 0,
        "supervisor_only": 0,
        "created_at": "2016-05-09 17:14:34",
        "updated_at": "2016-05-09 17:14:34",
        "description": "vero nihil autem nostrum quo architecto minima velit neque fugit non quis est quia voluptas",
        "is_read_only": false,
        "answers": []
      },
      {
        "id": 49,
        "options": [
          {
            "label": "omnis",
            "name": "saepe",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 2,
              "max": 26
            }
          },
          {
            "label": "rerum",
            "name": "incidunt",
            "type": "upload",
            "validation": {
              "is_required": false
            }
          },
          {
            "label": "aut",
            "name": "adipisci",
            "type": "textarea",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "eligendi",
            "name": "cumque",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 5,
              "max": 26
            }
          },
          {
            "label": "voluptatem",
            "name": "itaque",
            "type": "signature",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "omnis",
            "name": "labore",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 3,
              "max": 28
            }
          },
          {
            "label": "inventore",
            "name": "est",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 2,
              "max": 30
            }
          }
        ],
        "shift_id": 23,
        "all_colleagues": 0,
        "answered": 1,
        "supervisor_only": 0,
        "created_at": "2016-05-09 17:14:34",
        "updated_at": "2016-05-09 17:14:34",
        "description": "est placeat iste quo quia explicabo placeat tempore sit culpa et et eos doloribus consequuntur",
        "is_read_only": true,
        "answers": [
          {
            "id": 10,
            "question_id": 49,
            "employee_id": 202,
            "answer": {
              "omnis": "vel",
              "rerum": "totam",
              "aut": "dignissimos",
              "eligendi": "saepe",
              "voluptatem": "aliquam",
              "inventore": "quam"
            },
            "created_at": "2016-05-09 17:14:35",
            "updated_at": "2016-05-09 17:14:35"
          }
        ]
      },
      {
        "id": 53,
        "options": [
          {
            "label": "reprehenderit",
            "name": "consectetur",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 1,
              "max": 28
            }
          },
          {
            "label": "facere",
            "name": "amet",
            "type": "signature",
            "validation": {
              "is_required": true
            }
          },
          {
            "label": "minus",
            "name": "quos",
            "type": "slider",
            "validation": {
              "is_required": true,
              "min": 5,
              "max": 11
            }
          },
          {
            "label": "blanditiis",
            "name": "et",
            "type": "text",
            "validation": {
              "is_required": false
            }
          }
        ],
        "shift_id": 23,
        "all_colleagues": 0,
        "answered": 1,
        "supervisor_only": 0,
        "created_at": "2016-05-09 17:14:35",
        "updated_at": "2016-05-09 17:14:35",
        "description": "repudiandae sit dolores eligendi rerum odit nemo provident consequuntur voluptates est nobis ut sed dolor",
        "is_read_only": true,
        "answers": [
          {
            "id": 12,
            "question_id": 53,
            "employee_id": 185,
            "answer": {
              "reprehenderit": "temporibus",
              "facere": "voluptatum",
              "minus": "velit",
              "blanditiis": "aut"
            },
            "created_at": "2016-05-09 17:14:35",
            "updated_at": "2016-05-09 17:14:35"
          }
        ]
      }
    ]
  },
  "status": "success"
}
```

This endpoint is used to display the job details based on shift_id.

### HTTP Request

`GET http://shooble-api.bitstoneint.com/api/v1/work/<shift_id>`

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
    "status": "success"
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

### POST Parameters

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
    "status": "success"
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

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
employee_id | false | array of employee ids
checkpoint_id | false | checkpoint id
timestamp | true | checkin hour and date (EX: YYYY-MM-DD HH:MM:SS)

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success
</aside>

## Questionnaire

> The command returns JSON structured like this:

```json
{
  "data": {
    "status": "success"
  },
  "status": "success"
}
```

This endpoint is used to post the answers for a questionnaire, using the fields received on job details form

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/work/<shift_id>/questionnaire/<questionnaire_id>`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
option name | true | Here we will have a list of all options provided for this questions, use the name from option level to name the input field (the same for signature and upload as the upload will be done in a previous call)

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
startdate | false | start date filter for the availability dates (EX: YYYY-MM-DD)
period | false | filter for period, possible values: week/month/year - default is week

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — the availability dates
</aside>

## Update/Create availability dates

> The post parameters should be structured like this:

```json
[
    {
        "id":0,
        "plan_time": "2016-04-20 10:00:00",
        "employee": 247,
        "available": ["a", "e"],
        "comment": "works",
        "transport": {
            "type": "car",
            "seats": 3
        }
    },
    {
        "id":1146,
        "plan_time": "2016-04-20 20:00:00",
        "employee": 247,
        "available": ["m","a", "e"],
        "comment": "works update",
        "transport": {
          "type": "car",
          "seats": 1
        }
    }
]
```

> The command returns JSON structured like this:

```json
{
  "data": {
      "status": "success"
    },
    "status": "success"
}
```

This endpoint is used to create/update availability dates for user.
Make the request both on pagination and on submit

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/availability`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken | a valid login token

### POST Parameters

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
      "details": {
        "client": "Amsterdam",
        "job_type": "Type 3",
        "start_time": "2016-07-15 00:55:14",
        "end_time": "2016-07-15 03:55:14",
        "pickup_place": "Badhuispleon 7, Zandvoort",
        "invite_id": null,
        "supervisor": null,
        "shift_id": null,
        "client_rating": 0,
        "job_type_rating": 0,
        "colleagues_rating": 0,
        "pickup_time": "2016-01-31 12:30:00",
        "subject": "Shooble2 8",
        "description": "Shooble description",
        "agenda_id": 99195,
        "briefing_name": null,
        "briefing": null,
        "log_work_allowed": false,
        "apply_allowed": false,
        "time_logged": 0,
        "fillial_address": "Europaplein  71,Amsterdam",
        "address": "Badhuispleon 7, Zandvoort, 2042 JB"
      },
      "colleagues": [
        {
          "id": 236,
          "firstname": "Andreiiii",
          "lastname": "Arbaaa",
          "email": "andrei.arba@bitstone.eu",
          "phone": "123456789",
          "image": null
        },
        {
          "id": 248,
          "firstname": "Bitstone11",
          "lastname": "Test11",
          "email": "andrei.arba@bitstone.eu",
          "phone": "123456789",
          "image": null
        }
      ],
      "checkpoints": [],
      "questions": []
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

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | id of the job(shift id)
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
        "status": "success"
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

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | id of the job(invite id)

<aside class="warning">
Invalid token — an 401 unauthorized response will be received!
</aside>

<aside class="success">
Success
</aside>


#Common

## Upload image

> The command returns JSON structured like this:

```json
{
  "data": "http://shooble-api.com/uploads/questionnaire/1/11793332_1020059951360631_1599355863_nTUYKPrO5oDd8YHcp.jpg",
  "status": "success"
}
```

This endpoint is used to upload image on user profile and questionnaire

### HTTP Request

`POST http://shooble-api.bitstoneint.com/api/v1/upload`

### Headers

This request must contain the authToken header with a valid user token in order to be performed

Header | Value |
-------| -------
authToken| a valid login token

### POST Parameters

Parameter | Optional | Description
--------- | ------- | -----------
id | false | id of user or id of questionnaire
type | false | must be profile or questionnaire
image | false | must be type png,jpg,jpeg,gif,JPG,JPEG,GIF,PDF,PNG

<aside class="warning">
Invalid token — a 401 unauthorized response will be received!
</aside>

<aside class="success">
Success — a test user is registered!
</aside>


