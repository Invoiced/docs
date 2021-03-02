# QuickBooks Online

Invoiced integrates with QuickBooks Online out of the box to extend the billing capabilities of QuickBooks. This document describes how to set up the integration and how it works in detail.

## Overview

The QuickBooks Online integration ships with the following capabilities:

- Bi-directional sync with QuickBooks Online
- New data from QuickBooks Online is synced once per hour
- Transactions generated on Invoiced post to QuickBooks Online in real-time
- Import tool to bring customers and historical transactions from QuickBooks Online

[![QuickBooks Online Data Flow](/docs/img/qbo-object-mapping.png)](/docs/img/qbo-object-mapping.png)

## Setup

1. In order to begin syncing with QuickBooks Online first go to **Settings** &rarr; **Integrations**.  

2. Click on **Connect to QuickBooks**. You will be redirected to QuickBooks. You will need to sign in to QuickBooks, if you are not already signed in.

   [![QuickBooks Online Login](/docs/img/qbo-login.png)](/docs/img/qbo-login.png)

3. Next you will be prompted to authorize Invoiced access to your QuickBooks Online organization.  Click on **Authorize**.

   [![QuickBooks Online Authorize](/docs/img/qbo-connect-authorize.png)](/docs/img/qbo-connect-authorize.png)

4. You will be redirected back to Invoiced. QuickBooks Online is now connected! Now you can configure the accounting sync in order to tell Invoiced how to map the data into your general ledger.

5. Configure the data flows you wish to enable and any account mappings. Click **Save**.

## Usage

Once the QuickBooks Online integration is enabled it will sync data automatically on a going forward basis per the data flows that you have enabled.

Writing data from Invoiced to QuickBooks Online will sync instantly.

Reading data from QuickBooks Online to Invoiced, such as when a new invoice is available, will sync once per hour. You can see when the last sync happened on the **Accounting Sync** page. If you wish to run a one-off sync you can click the **Sync Now** button.

### Handling Errors

On the **Accounting Sync** page you will see a *Reconciliation Errors* table which contains any sync errors that the integration encountered. Each error listed belongs to individual record that could not be synced. The error message is listed next to each failed record. When a record fails to sync it will not be re-attempted unless there is a new operation (i.e. updating the record) that triggers a new sync. You can retry syncing any failed record by clicking the **Retry** button or you can ignore the error by clicking the **Ignore** button. Errors will not go away until they are successful or ignored. 

### Field Mapping

We support setting several optional fields on QuickBooks Online that do not have a standard Invoiced field. This can be useful if you are first creating invoices on Invoiced and posting to QuickBooks Online.
 
These additional field mappings work when a record on Invoiced has a custom field with a specific ID that corresponds to a specific field on QuickBooks Online. This gives you granular control of the data sent to QuickBooks Online.

Object Type | Invoiced Custom Field ID    | QuickBooks Field
------------|-----------------------------|------------------
Invoice     | `qbo_location`              | Location
Line Item   | `qbo_class`                 | Class

#### Income Account Mapping

The *Income Account* for any line item in QuickBooks Online is derived from the associated Product or Service on QuickBooks. Our integration will match the Product or Service on QuickBooks based on the line item name.

When creating an invoice, if a Product or Service with a matching name cannot be found on QuickBooks, then our integration will create a new Product or Service. The name of the Product or Service will be the line item name. The *Income Account* for the newly created Product or Service will be the default income account you have selected in the integration settings.

You can change the *Income Account* for any line item in the **Products and Services** page on QuickBooks. This will work for any Product or Service, regardless of whether it was created by the Invoiced integration. If you find that a line item created by the Invoiced integration does not have the correct *Income Account* then it can still be changed through the **Products and Services** page.

Please consult the QuickBooks documentation for more details on how to configure Products and Services.

#### Deposit Account Mapping

You can map the accounts in which payments are deposited into. By default, payments are put into *Undeposited Funds*. You can create rules to choose the deposit account for each payment method and currency combination. The deposit account can be any bank or current liability account.

### Import Historical Data

You can import data from QuickBooks Online into Invoiced for the time period before the Invoiced integration was installed. This data can be imported:

- Customers
- Open and/or paid invoices
- Credit memos
- Payments

Instructions:

1. Go to the **Customers** or **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

2. Select **QuickBooks**.

3. Configure the data you wish to import, date range, and any other settings.

4. Click **Start**.

5. The import tool will begin processing your request. You are free to leave the page once the import starts. You will get an email afterwards with the result.

6. Once the import is finished you will see the newly imported data on Invoiced. The import detail screen has a list of all records that were imported.

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the QuickBooks Online integration.

- Any changes to data on the system other than where it originated will be ignored, and potentially overwritten. For example, if an invoice was created on QuickBooks by the Invoiced integration then subsequent modifications to that invoice on QuickBooks would not sync to Invoiced. It is possible that those changes on QuickBooks would be overwritten by a future sync.

- Customers on Invoiced are mapped to customers on QuickBooks by the name. Please keep in mind that QuickBooks does not allow multiple customers with the same name, but Invoiced does allow duplicates.

- Customer names are truncated to 100 characters due to a character limitation in QuickBooks.

- Only issued invoices (not a draft) on Invoiced will be synced.

- The sync will match each line item to a product or service in QuickBooks based on the line item name. If the product or service does not exist then it will create an item in QuickBooks. If the line item name is blank then a generic Invoiced item will be created.

- Line item descriptions over 4,000 characters are truncated due to a character limit in QuickBooks.

- If a line item on Invoiced has an item attached, then the product created on QuickBooks will have its SKU set to the Invoiced item ID.

- Credit balances from Invoiced do not sync to Quickbooks Online.

- Transactions created in Invoiced (invoices, payments, credit notes) will not post to Quickbooks Online if the transaction has a date that is in a closed accounting period.

- Voiding a credit note on Invoiced will not void the credit memo on QuickBooks. This is due to a technical limitation in the QuickBooks API.

## Troubleshooting

When a sync fails you will be able to see the error message in the *Recent Syncs* section in **Settings** &rarr; **Accounting Sync**. Normally the error message will include the invoice # that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your books synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Account period has closed

> The account period has closed and the account books cannot be updated through the QBO Services API. Please use the QBO website to make these changes.

When you see this error message then it means that Invoiced is trying to sync an invoice or payment during a time period that you have already closed. One way you can fix this is by re-opening your books for that time period and running the sync once more. When the sync finishes you can close the books again.

Another solution is to change the date range that Invoiced will sync to QuickBooks. You can tell Invoiced to not sync any invoices before the time period when you closed the books. The sync date range can be set up in the QuickBooks settings at **Settings** &rarr; **Integrations** &rarr; **Configure** (in the *QuickBooks Online* section).

### You can only add or edit one name at a time

> Business Validation Error: You can only add or edit one name at a time. Please try again.

Often this error means that an accounting sync was running while someone was working in the books. This can be fixed by signing out of the QuickBooks Online interface and re-trying the sync.

### QuickBooks Online could not authenticate

> QuickBooks Online could not authenticate.

If you see this error message then our access token to your QuickBooks account has expired. You need to go to **Settings** &rarr; **Integrations** in order to reconnect QuickBooks.

### Subscription period has ended

> Subscription period has ended or canceled or there was a billing problem : You can't add data to QuickBooks Online Plus because your trial or subscription period ended, you cancelled your subscription, or there was a billing problem. To update your subscription, click the gear icon and view your account information.

Your QuickBooks subscription has expired. Please sign into QuickBooks in order to address the issue.