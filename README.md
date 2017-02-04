# GreenToGo

This project contains both the GreenToGo subscription site and API for use by the mobile app.

The files are laid out in accordance with recommendations from Two Scoops of Django.

Development Setup

1. pip install -r requirements.txt
2. createdb -E UTF-8 greentogo

## Assumptions to question

- One subscription has one email address
- One email address has one subscription

## Things that can happen

- Customers can buy a subscription
- Customers can renew a subscription
- Customers can upgrade a subscription
- Customers can downgrade a subscription
- Customers can cancel a subscription

- Companies can buy a subscription for their employees
- Employees will not be able to upgrade, downgrade, cancel, or renew their subscription

## Models

### Customer

* name
* password
* stripe_id?
* subscriptions -- many to many

### Email

* customer
* email

### Company

* admin -- Customer

### Subscription

* admin -- Customer
* user -- Customer -- many to many
* plan
* started_on
* expires_on
* stripe_id
* parent_subscription? -- this is to handle corporate subscriptions
    * maybe corporate subscriptions work differently, with a separate table for them and each of the sub-subscriptions are in this table