EngageBay Webhooks
==================

[EngageBay](https://www.engagebay.com/) is a simple, affordable all-in-one marketing and sales software built for growing businesses. Get the power of an enterprise software at a fraction of the cost.

### Overview

A webhook lets an app pass information to other apps in near real-time. This could mean notifying a information from EngageBay to another web application, or a way to notify another 3rd party application that accepts POST requests.

In EngageBay, webhooks are used to send data from your account into another system or database that has an API that can listen for webhooks (eg, Zapier). They are event driven and allow you to update 3rd party applications with contact activity as they happen.

There are a variety of uses for webhooks, such as sending data and pushing notifications.

- Posting EngageBay contacts data to another system, such as a CRM, when that contact fills out a particular form on your site.
- Sending deal data to an external shipment-handling system to create a purchase order.
- Sending company data to another system, such as a CRM, when that contact fills out a particular form on your site.

NOTE: 
```
EngageBay does not accept incoming webhooks. Instead, you will need to use our API to send information into your account from a 3rd party application.
```

### Getting Started

* [1 How to create a webhook](#1-how-to-create-a-webhook)
* [2 How webhook data is received](#2-how-webhook-data-is-received)
* [Sample data (json formatted)](#3-sample-data-json-formatted)

### 1 How to create a webhook: 

With every webhook you create, you can choose when it should fire. For example, you may only want to receive data when a contact is created or you may want to only receive data when a contact tag is updated/deleted.

In this section, you'll learn how to create a webhook from the Account Settings -> Webhooks settings page.

1. Click “Add Webhook” to create a webhook.
2. Type the name of your webhook in the Name field
3. Select which event webhook will be associated with by clicking the dropdown
4. Type the URL from your integration or application where you want to send information to. This URL will need to come from your 3rd party application or integration.

![alt text](https://lh3.googleusercontent.com/8dgqi18u48TXkl2ReEn5wCXqe16LsLbeJK1Hl4EOMQ-qZaVr3gEce09Xuv5v6HmWmkczpi9pDJaFIb3L09xsW8HK9T2BZJTQgvEsssa4N7R3YXRfCR0S-H3M6_8Hbha1o4MsVjPS)

5. Click the boxes next to any action/event that will trigger your webhook:

- Contact created
-  Contact updated
- Contact deleted
- Company created
- Company updated
- Company deleted
- Deal created
- Deal updated
- Deal deleted

![alt text](https://lh5.googleusercontent.com/Rym1pSCa7Pl6GaNP1fVt2J-Vcqs44K65_hZ-dowCLdfHqShEYKmoMW6NWgiKo30YobaZkH-ujz4lS_DywEe9my0PNDOn7srhjX9Z-dcvMUn3GaSxeWJ4btB3cXv72AIGTI0Vizlo)

6. When finished, click “Add Webhook” on the lower right of opened modal.

### 2 How webhook data is received: 

The data you receive will be sent as a POST parameter to your URL. 

The easiest way to test the output of your webhooks is to use a service such as [RequestBin] (https://requestbin.com/). This service will give you a URL that will collect requests made to it and let you inspect them in a human-friendly way.


### 3 Sample data (json formatted): 

Request type - Contact Created
###### Example 1
```javascript
{
    "event": "contact.created",
    "entity": {
        "id": 5667649732233534,
        "created_time": 1455855737,
        "properties": [
            {
                "name": "name",
                "value": "Peter"
            },
            {
                "name": "lastname",
                "value": "Ross"
            },
            {
                "name": "email",
                "value": "peter@gmail.com"
            }
        ]
    }
}
```

Request type - Contact Updated

###### Example 2
```javascript
{
    "event": "contact.updated",
    "entity": {
        "id": 5667649732233534,
        "created_time": 1455855737,
        "updated_time": 1455856605,
        "properties": [
            {
                "name": "name",
                "value": "Peter"
            },
            {
                "name": "lastname",
                "value": "Ross"
            },
            {
                "name": "email",
                "value": "peter@yahoo.com"
            }
        ]
    }
}
```

Request type - Deal Created

###### Example 3
```javascript
{
    "event": "deal.created",
    "entity": {
        "id": 5802786220408832
		"unique_id": 1594305685795
		"name": "Test Deal"
		"description": "Test Deal"
		"amount": 200
		"track_id": 5634472569470976,
		"milestoneLabelName": "New",
		"owner_id": 5358693205934080
    }
}
```

Request type - Deal Updated
###### Example 3
```javascript
{
    "event": "deal.updated",
    "entity": {
        "id": 5802786220408832
		"unique_id": 1594305685795
		"name": "Test Deal"
		"description": "Test Deal"
		"amount": 200
		"track_id": 5634472569470976,
		"milestoneLabelName": "New",
		"owner_id": 5358693205934080
    }
}
```
