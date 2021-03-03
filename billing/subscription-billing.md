# Subscription Billing

Subscriptions allow businesses to automate the billing for customers on a recurring basis. With subscription billing on Invoiced, you can charge customers automatically each billing cycle, or issue an invoice that can be paid with payment methods accepted on the account.

If you find yourself sending the same invoices each month, then subscription billing is the solution . Not only will subscription billing save you time, but your customers will likely appreciate the predictability and convenience of subscriptions.

## Introduction

Invoiced has designed a subscription billing system to offer power and flexibility, while remaining simple to understand and to use. There are a few key concepts you might want to become familiar with before starting:

### Plans

A plan describes how much and how frequently your customer will be billed. An example plan might be one for website hosting that is $100 per month. Plans are reusable templates for building subscriptions. You can setup and manage your plans in **Settings** &rarr; **Plans**.

### Subscriptions

A subscription bills a customer for a fixed amount on a systematic basis, according to the plan the customer is subscribed to. Subscription pricing is flexible on Invoiced and allows for quantities, addons, discounts, and taxes to be combined. Subscriptions also support many options to customize the billing intervals.

Although we use traditional defaults, we also support many advanced subscription billing features that you might want to become familiar with. The advanced features include: 

#### Trial Period

Subscriptions support a free trial period at the beginning of the subscription where the customer is not charged. For example, a subscription might have a 30-day trial period where the customer is given service for free until the first bill is issued. After the trial period, the customers subscription will begin to bill. 

#### Billing Date

The billing date is the date when the next bill for the subscription is going to be generated. Essentially when a subscription renews, the next invoice in the cycle is formed and issued. Billing dates are controlled by you and dependent on whether anniversary or calendar billing is used.

#### Anniversary Billing

As stated in the billing date section, *Anniversary Billing* renews a subscription on the anniversary of the start date.
For example, if your customer purchased a monthly subscription on the 9th then they would be billed each month on the 9th. In Invoiced, subscriptions use anniversary billing by default.

#### Calendar Billing

Another option to Anniversary Billing is *Calendar Billing, *which renews subscriptions on a specific day of the month chosen, instead of the start date. Calendar billing also has the ability, on the first invoice, to prorate partial months*.

For example, let's consider a scenario where your customer purchased a monthly subscription on the 9th with calendar billing set to the 1st of the month. The first bill would be prorated for the time remaining until the next 1st of the month. Future bills will be generated on the 1st of the month for the full amount.


#### Billing Period

Each subscription keeps track of the current billing period. The billing period represents the time frame that the subscription will cover. The length of the billing period always matches the plan interval. By default, the billing period will be the interval following the billing date. If a monthly subscription renewed on December 1 then the current billing period would be December 1 - December 31.

#### Duration

Subscriptions can be *infinite* or *fixed* duration. An infinite subscription (the default) runs forever until the customer cancels. A finite subscription will run for a fixed number of billing cycles.

#### Quantity

The subscription quantity acts as a multiplier to the base plan price. If your subscription is based on a per-user subscription (i.e. $30/user/month) then the quantity would represent the number of users the customer should be billed for each month.

### Subscription Addons

Subscription addons are meant to give you pricing flexibility on top of the base plan amount. Addons save you from creating a large number of plans for every possible combination of products/services that a customer could subscribe to. An addon is an additional plan added onto a subscription, in addition to the primary plan. Each addon is billed as a separate line item on the generated invoices. 

You can setup and manage your plans in **Settings** &rarr; **Plans**.


### Subscription Invoices

A subscription will generate an invoice each billing cycle for the amount owed in that billing cycle. The invoice contains line items for the plan and any addons.

#### AutoPay

Since subscriptions are a generate invoice monthly, that means [AutoPay](https://www.invoiced.com/resources/docs/payments/autopay) customers are fully supported with subscription billing. AutoPay will automatically charge your customer's payment method for any invoices issued against their account, including subscription invoices.

If a customer with AutoPay enabled is subscribed to a plan, but does not have payment information on file yet, then we will send them the first invoice automatically. Upon paying the invoice, we will capture the customer's payment information for use on future invoices.

#### Payment Terms

When AutoPay is not enabled, then the customer will receive an invoice each billing period that they can pay using any of the payment methods you accept.

Payment terms succinctly tell the customer when an invoice is due. For example, NET 7 means that payment is due within 7 days of the invoice whereas NET 30 means payment is due in 30 days. 

You can read more about the different kinds of payment terms in this [blog post](https://www.invoiced.com/blog/how-to-get-paid-faster-on-your-invoice-part-i).


#### Pending Line Items

If there are any unbilled one-time charges (setup fees or usage charges) that were added to the customer's account during the billing cycle, then those line items will be swept into subscription invoice at the time it is generated.

### Prorations

Invoiced supports prorations on subscriptions when changing a plan, quantity, or addons mid- billing cycle. When a customer downgrades, they will receive a credit, and when they upgrade will be charged.

Prorations are calculated any time a subscription is changed, unless disabled. A proration will generate a credit for the time remaining on the current billing cycle before the subscription update and a charge for the time remaining with the subscription update. If the proration is negative (downgrade) then we will issue the customer a credit. If positive (upgrade) then will add the amount to the next subscription invoice.

When switching to a plan with a different billing cycle, for example, switching from monthly to annual billing, then a new billing cycle will be started at the time of pro-ration. This means an invoice will be generated for the next billing cycle on the plan.

#### Proration Calculation

Prorations are calculated based on the number of seconds left in the billing cycle. Here is the formula we use to calculate prorations. 

The `% time remaining` is calculated with:

`seconds left in period / total seconds in period`

Then a proration credit line item is computed using this formula:

`% time remaining * subscription price before change`

And a proration charge line item is computed using this formula:

`% time remaining * subscription price after change`

### Sign Up Pages

Sign up pages allow customers to purchase a subscription online through a self-serve form hosted by Invoiced. The [Sign Up Pages Guide](sign-up-pages) has more information on this.


###Add a discount code to a plan

Wanting to discount some of the subscription payments but not all? You now have the flexibility to add a duration to a coupon discount. That way, when you apply that discount, it will only be discounted for the X duration applied to on the discount code. To learn more about this functionality, please visit the Coupons documentation. 

## Usage

## Enabling Subscription Billing

The subscription billing addon is disabled by default. Follow these steps to enable subscription billing:

1. Go to **Settings** &rarr; **General** in the Invoiced dashboard. Towards the bottom of the page you will find a *Subscriptions Addon* toggle.

2. Click on the toggle next to *Subscriptions Addon*.

### Creating a Subscription

The following example is based off of a subscription invoice with a NET 14 terms. In this scenario, AutoPay will be disabled. If you wish to use AutoPay, we recommend using the signup pages to subscribe a new customer and capture the payment information on signup. 

Subscriptions are created and accessed in the Subscriptions tab. To begin creating a subscription, you can click the + sign next to the subscription tab or access the Add Subscription button in the Subscriptions tab. 

A dialogue box will now show to select or add a customer. If the customer does not exist, you will add the customers name and Invoiced will create the customer. 

This will allow you to enter the customers contact information, select AutoPay (if applicable), payment terms,  and options for payment methods. This example will use NET 14. Click create when finished.

Once the customer is saved, it is time to create a plan. Click +New Plan to create a new plan. 

Let's say we want to create a plan called *Basic* for *$39/month*. The *ID* field is a unique identifier used to reference your plan through the API. The ID is automatically generated for you, but you are free to rename this to match your own internal SKU or naming scheme. Click save when completed. 

The last step is to customize the duration of the subscription and if you wish to have any addons. To reveal these options, click the *Options *drop down*. 

In this example, we want to start the subscription now. If you wish to start the subscription at a later date or offer a free trial period then you can uncheck the *Starting now *option to select a start date. We are going to leave the *Duration* as Until canceled. The subscription will renew until canceled by you or the customer. The *Quantity* can be left as 1, unless the customer is purchasing multiple quantities of the base price. Let's try adding an addon by clicking *+ Addon*. In our example we are selecting an 1 on 1 session addon and setting the quantity to 4.

For the *Renew On* setting we are going to leave it as Start date anniversary. This will renew the subscription each billing cycle on the same day of the month as the start date, which is today in this example. If you selected Day of month instead then this would bill your customer on a specific day of the month you choose, like the first of the month. The first bill would be prorated for the time remaining until the next billing cycle. Future renewals will be on the date you've specified.

At the bottom of the screen you can see the calculated recurring total. If you click the *Preview* button you can even see a preview of the upcoming billing cycles. Once the subscription looks right you can now click *Create*.

You will now see that your newly created subscription is active. The invoice for the first billing cycle has already been generated.

### Editing a Subscription

What happens when your customer falls in love with your service and wants to purchase more? This common scenario is easily handled with Invoiced. We will even (optionally) calculate and bill the prorated amount when switching a plan, quantity, or addons in the middle of the billing cycle.

You can edit a subscription by opening the subscription in the dashboard and clicking the *Edit* button in the top right corner.

This allows you to change the quantity, add subscription addons, discounts, and taxes.


### Changing the Billing Date

Once your subscription is running you might want to change when it renews next. The reason might be that the customer wants the subscription to renew on a certain day of the month, maybe the wrong start date was chosen, or else you want to issue invoices sooner.

With the subscription in the dashboard you can click **Actions** &rarr; **Change Billing Date** to change when the subscription will renew next.

The billing date cannot be set in the past. Changing the billing date will not produce any prorations.

### Canceling a Subscription

Canceling a subscription is simple. With the subscription open in the dashboard you can click **Actions** &rarr; **Cancel Subscription**.

You can choose whether you want the subscription to be canceled immediately or at the end of the billing period.

When a customer cancels a subscription in the customer portal, the subscription will end at the end of the billing cycle. This also means that the cancellation will not trigger a credit to the customers account. This is because the subscription is pre-paid at the beginning of the billing cycle. 

## Contract Billing

With subscriptions, an automatic billing schedule is based on an infinite number of billing charges. With contract billing, a finite duration of payments for the consumers contract can be created that does not automatically renew, making it beneficial to your enterprise. The interval at which the customer is billed is often more frequent than the length of the contract. Traditional subscription billing allows you to set a subscription billing cycle with no end date, or a billing plan with an ending of X months. Contract billing allows you to set a contract term length. Even if canceled, the contract will continue to bill until the end of the contract term. 

### Usage 

An example of Contract Billing can be an annual contract that is billed monthly and the contract does not renew automatically. When the contract does not renew automatically, the user will have to manually update the contract during the renewal process to determine if the customer intends to renew their contract. This process also allows for renewal increases and what the duration of the renewal might be. 

Please note the renewal length and initial term length are not intrinsically the same. A customer could have a contract that has an initial term of three years and has the option to renew on a yearly basis **after** the inital term. 

If auto-renewal is enabled, there is no need for internal intervention of the contract. With auto-renewal disabled, each time there is a contract renewal, it is important to distinguish if the subscription is being renewed, what the length of the next term will be, and if there will be any pricing or line item changes. 

### Setup

To set-up a contract, simply navigate to:

Subscriptions &rarr; Add Subscription 

Like the process of creating a traditional subscription, find the customer you wish to add the subscription to then select the subscription plan. To add contract billing terms, expand the *Options* section. 

Select how long the initial term of the contract will be.

Next, select whether the contract will :

*Renew Automatically*: It will continue to renew automatically until canceled based on the renewal terms.

*Require Approval to Renew*: It will require the approval from the customer to renew the contract. This allows internal users to change the terms, pricing, and plan items.

*Stop Billing*: This will cancel the contract

Once you select the process of the contract ending, continue the traditional set up of a subscription billing cycle. 

###Approval of Contract Renewal

When a contract is up for renewal, the renewal process is done by the internal Invoiced user, not the customer. It is up to the business and the customer to work on the renewal terms of the contract. 

You can filter your subscriptions by upcoming renewal in your Subscriptions section under the filter : Pending Renewal. 

### Canceling Contract Billing
 
Canceling contract billing is slightly different than canceling a traditional subscription. The customer can still access the cancellation process in the customer portal, however, the option to cancel at the end of the billing cycle should not be available until the length of the contract has completed. In many cases, this option could be a couple of cycles out from the end of the contract billing term. 

## FAQs

### What automated emails does Invoiced send for subscriptions? 

Invoiced can send these emails with subscriptions:

- **Sign up confirmation**
  
  Confirmation that a customer has finished signing up for automatic billing.

- **Renews Soon**

  A reminder sent X days before a subscription renews to let customers know about upcoming charges.

- **New invoice**
  
  Sends any invoices generated from a subscription to your customer.

- **Cancellation**

  Notification when a subscription is canceled.

You can learn more about these emails in the [Emails Guide](/resources/docs/guides/emails).

### When do subscription invoices go out?

Subscriptions are usually renewed very close to the billing timestamp (within a minute). Subscriptions will never renew early but please keep in mind that they might be renewed late. If a subscription does happen to be renewed later than scheduled then our system will not punish the customer for non-payment, as should yours.