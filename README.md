EngageBay Webhooks
==================

[EngageBay](https://www.engagebay.com/) is a simple, affordable, integrated all-in-one marketing, sales, and support software with free CRM built for growing businesses. Get the power of an enterprise software at a fraction of the cost.

### Overview

A webhook (also called a web callback or HTTP push API) allows one application to provide real-time information to other applications. A webhook delivers data to other applications as it happens so you get immediate access to data. 

Therefore, information from EngageBay may be passed on to another app instantly, or any 3rd party application that accepts POST requests may be notified in real-time. 

Webhooks, in EngageBay, are used to transmit data from your account into another system or database that has an API and can identify and receive webhooks (eg, Zapier). These are driven by occurring events and they allow you to update 3rd party apps with contact activity as they occur.


Webhooks have a number of uses such as pushing notifications and sending data.

- Posts EngageBay contacts data to another system, e.g. to a CRM. 
- In order to create a purchase order, webhooks pass on deal data to an external shipment-handling system. 
- When a contact fills out a particular form on your site, webhooks send contact data to another system, e.g. to a CRM.

NOTE: 
```
EngageBay does not accept incoming webhooks. You are required to use our API to send information to your 
account from a 3rd party application.
```

### Getting Started

* [1 How to create a webhook](#1-how-to-create-a-webhook)
* [2 How webhook data is received](#2-how-webhook-data-is-received)
* [3 Sample data (json formatted)](#3-sample-data-json-formatted)

### 1. How to create a webhook: 

Whenever you create a webhook, you can choose when to trigger it. For example, you may choose to receive data only when a contact is created or when a contact tag is updated/deleted.

Here’s how to create a webhook from the Account Settings -> Webhooks settings page.

1. Click “Add Webhook” to create a webhook.
2. Enter the webhook name of your choice in the field ‘Name’ 
3. Select the webhook associated event by clicking the dropdown
4. Enter the destination URL from your integration/app where you want the information to be sent. This URL should be from your 3rd party app/integration.

NOTE: 
```
The destination URL supports personlization with muscahe compiler format. It behaves like dynamic URL with personalize values. Ex: https://xxx.yourdomain.com?id={{entity.id}}
```


![alt text](https://lh3.googleusercontent.com/8dgqi18u48TXkl2ReEn5wCXqe16LsLbeJK1Hl4EOMQ-qZaVr3gEce09Xuv5v6HmWmkczpi9pDJaFIb3L09xsW8HK9T2BZJTQgvEsssa4N7R3YXRfCR0S-H3M6_8Hbha1o4MsVjPS)

5. Click the boxes next to any action/event that will trigger your webhook:

- Contact created
- Contact updated
- Contact deleted
- Company created
- Company updated
- Company deleted
- Deal created
- Deal updated
- Deal deleted

![alt text](https://lh5.googleusercontent.com/Rym1pSCa7Pl6GaNP1fVt2J-Vcqs44K65_hZ-dowCLdfHqShEYKmoMW6NWgiKo30YobaZkH-ujz4lS_DywEe9my0PNDOn7srhjX9Z-dcvMUn3GaSxeWJ4btB3cXv72AIGTI0Vizlo)

6. When finished, click “Add Webhook” on the lower right of opened modal.

### 2. How webhook data is received: 

The data you receive will be passed as a POST parameter to your URL.

A quick and easy way to test the output of your webhooks is to use [RequestBin] (https://requestbin.com/). This service gives you a URL that collects requests made to it and lets you inspect them easily.


### 3. Sample data (json formatted): 

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
