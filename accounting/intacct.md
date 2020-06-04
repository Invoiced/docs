# Sage Intacct

Invoiced integrates with Sage Intacct out of the box, a best-in-class cloud ERP. This document outlines how to setup and use the Intacct integration.

## Overview

The Intacct integration ships with the following capabilities:

- Reading customers, open invoices, and payments from Intacct
- Reconciling payments received on Invoiced to Intacct
- Writing invoices generated on Invoiced to Intacct
- Most data flows happen in real-time

[![Intacct Data Flow](/docs/img/intacct-object-mapping.png)](/docs/img/intacct-object-mapping.png)

## Setup

In order to set up the Intacct integration you first need these pieces of information:
- Intacct Company ID
- Web services user

Below we will show you how to connect Intacct with Invoiced, step-by-step.

### Setting Up a Web Services User

The next step is to set up a web services user for Invoiced on Intacct. It is recommended that you use a dedicated web services user for Invoiced in order to ensure it has the correct permissions. We also recommend against using a non-web services user because any password changes would break the integration.

1. You need to ensure that your company has web services enabled on Intacct in **Company** &rarr; **Subscriptions**.

2. Within the Intacct application, hover over the **Company** tab and click the **+** button next to *Web Services Users*.

3. You will want to set up a user similar to the screenshot below with the following settings:

   - User ID: "invoiced"
   - First Name / Last Name: "Invoiced"
   - Email address: your shared accounting team email
   - User type: "Business"
   - Admin privileges: "Full"
   - Status: "Active"
   - Keep password until admin resets it: check this box
   - Restrict user access to web services only: check this box
   
   [![Intacct Web Services User Setup](/docs/img/intacct-web-services-user.png)](/docs/img/intacct-web-services-user.png)

4. Next you need to configure permissions for the Invoiced user. On the subscriptions page check the **Accounts Receivable**, **General Ledger**, and **Order Entry** modules.

   [![Intacct Subscriptions Setup](/docs/img/intacct-web-services-user-subscriptions.png)](/docs/img/intacct-web-services-user-subscriptions.png)

5. Click on the **Permissions** button next to the Accounts Receivable module. Select the **All** radio in the top right. Click **Save**.

   [![Intacct Permissions Setup](/docs/img/intacct-web-services-user-permissions.png)](/docs/img/intacct-web-services-user-permissions.png)

6. Click on the **Permissions** button next to the General Ledger module. Select the **Read only** radio in the top right. Click **Save**.

7. Click on the **Permissions** button next to the Order Entry module. Select the **Read only** radio in the top right. Click **Save**.

8. Click **Save** on the subscriptions page. You should have received an email with the company ID, username, and password information.

### Adding a Web Services authorization

1. Go to the **Company Info** page. Click **Edit**.

2. In the Web Services authorizations section, click the + icon above the top-right corner of the table.

3. Enter in *Invoiced* as the **Sender ID**. *Please note the sender id is case sensitive and starts with a capital I*. Click **Save**.

   [![Intacct Web Services Authorization](/docs/img/intacct-web-services-authorization.png)](/docs/img/intacct-web-services-authorization.png)

### Connecting Intacct on Invoiced

1. Go to **Settings** &rarr; **Integrations** in the Invoiced dashboard.

   [![Integration Settings](/docs/img/integration-settings.png)](/docs/img/integration-settings.png)

2. Click on **Connect** on the Intacct integration.

   [![Connect Intacct](/docs/img/connect-intacct.png)](/docs/img/connect-intacct.png)

3. Enter in the Intacct company ID, username, and password for your Invoiced web services user created earlier. If you are using a shared multi-entity account then you can also enter in the entity ID you would like the connection to use.

4. Click **Save**. Intacct is now connected! Next you will want to configure the integration before using it.

   [![Intacct Integration Settings](/docs/img/intacct-integration-settings.png)](/docs/img/intacct-integration-settings.png)

5. You can customize the integration, including the data you want to sync to/from Intacct, account mappings, and other integration behaviors.

6. Click **Save & Download Customization** to save your settings and download the customization package needed in the next step.

### Install the Invoiced Customization Package

The Invoiced Customization Package generated in the previous step can be installed on Intacct to add new custom fields needed by the integration and instantly import transactions from Intacct.

1. Find the `invoiced.xml` file generated in the previous section. This file is tied to your Invoiced account. Do not share it with anyone! Install the Invoiced package on Intacct in the **Customization Services** section.

   [![Intacct Customization Package Install](/docs/img/intacct-customization-package-install.png)](/docs/img/intacct-customization-package-install.png)

## Usage

Once the integration is configured and the customization package is installed, new transactions will begin to sync with Intacct automatically. If you wish to import existing customers or invoices please continue reading.

### Import Existing Invoices

You can import outstanding invoices from the Intacct Order Entry module using our Intacct invoice import tool. This is useful after setting up the integration to pull in invoices that were created before the integration was installed.

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Invoices Page](/docs/img/invoices-header.png)](/docs/img/invoices-header.png)

2. Select **Intacct**.

   [![Invoice Import Tool](/docs/img/invoice-importer.png)](/docs/img/invoice-importer.png)

3. Select the sales document type you would like to import, and when ready, click **Start**.

   [![Start Intacct Invoice Import](/docs/img/intacct-invoice-importer-options.png)](/docs/img/intacct-invoice-importer-options.png)

4. The import tool will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![Intacct Invoice Import Started](/docs/img/intacct-invoice-importer-pending.png)](/docs/img/intacct-invoice-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

   [![Intacct Invoice Import Finished](/docs/img/intacct-invoice-importer-finished.png)](/docs/img/intacct-invoice-importer-finished.png)

### Import Entire Customer List

You can import your entire customer list from Intacct into Invoiced as a one-time import. Why might you use this? The integration will only import customers that have new invoices, whereas a customer import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Customers Page](/docs/img/customers-header.png)](/docs/img/customers-header.png)

2. Select **Intacct**.

   [![Customer Import Tool](/docs/img/customer-importer.png)](/docs/img/customer-importer.png)

3. Click **Start**.

   [![Start Intacct Customer Import](/docs/img/intacct-customer-importer.png)](/docs/img/intacct-customer-importer.png)

4. The import tool will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![Intacct Customer Import Started](/docs/img/intacct-customer-importer-pending.png)](/docs/img/intacct-customer-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

   [![Intacct Customer Import Finished](/docs/img/intacct-customer-importer-finished.png)](/docs/img/intacct-customer-importer-finished.png)

### Dimension Mapping

We support setting line item dimensions and other fields on Intacct that do not have a standard Invoiced field. This can be useful if you are first creating invoices on Invoiced and posting to Intacct.
 
The mappings happen automatically when a line item on Invoiced has a custom field with a specific ID that corresponds to a specific field on Intacct. This gives you granular control of the data sent to Intacct and enables you to take advantage of dimensions.

Invoiced Custom Field ID | Intacct Field
-------------------------|--------------------
`intacct_glaccountno`    | GL Account Number
`intacct_allocation`     | Allocation ID
`intacct_location`       | Location ID
`intacct_department`     | Department ID
`intacct_project`        | Project ID
`intacct_vendor`         | Vendor ID
`intacct_employee`       | Employee ID
`intacct_item`           | Item ID
`intacct_class`          | Class ID
`intacct_contract`       | Contract ID
`intacct_warehouse`      | Warehouse ID

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the Intacct integration.

- Customers on Invoiced are mapped to customers on Intacct by the customer name and/or account number.

- Only customers with a status of *Active* and invoices belonging to customers with an *Active* status will be imported into Invoiced.

- Only non-draft invoices on Invoiced will be posted to Intacct. Currently updates to invoices are not posted to Intacct, unless the invoice was voided.

- Any modifications to invoices on Invoiced that originated from Intacct will not be posted to Intacct.

- When importing bill to contacts instead of customers, the customer on Invoiced will use the information from the bill to contact instead of the Intacct customer. This means the name and details will match the bill to contact, and will result in multiple Invoiced customers for a single Intacct customer. The customer number on Invoiced will be auto-generated and will not match the one on Intacct because there are multiple Invoiced customers that could have the same account number.

- Partial refunds are not supported by the integration and must be reconciled manually.

- A/R adjustments posted to Intacct and applied to an invoice will not be picked up by our integration and will require a manual reconciliation on Invoiced using a credit note.

## Troubleshooting

When a record fails to sync you will be able to see the error message in the *Reconciliation Errors* section in **Settings** &rarr; **Accounting Sync**. Normally the error message will include the record identifier that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end. Once that is resolved you can either ignore or retry the record.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your data synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

[![Intacct Reconciliation Errors](/docs/img/intacct-reconciliation-errors.png)](/docs/img/intacct-reconciliation-errors.png)

### Finding Your Intacct Company ID

Your Intacct company ID is required in order to connect the integration. You can obtain your company ID from Intacct with these steps:

1. Within the Intacct application, hover over the **Company** tab and click **Company Info**.

2. You should see an *ID* field. This is the company ID that you will use in the connection steps.

### 401 Error

> non-200 status code: 401

We could not connect to Intacct using the credentials you provided. Please make sure the Intacct company ID, username, and password are correct.

### Numbering collision

> A transaction with the number 'XXX' already exists.

If you see this error message then there is already a different invoice with the same number on Intacct. It is recommended that you choose a unique invoice # for the invoice that is being synced.

### Please provide a payment batch key

> Please provide a payment batch key.

Change the Payments Summary frequency to either Daily or Monthly. To do so, complete the following steps in Intacct:

1. Hover over the Accounts Receivable tab
2. Click Configure Accounts Receivable
3. Scroll down to Summary Frequency in the Accounting Settings section
4. Change the Payments field to either Daily or Monthly and Save the changes
5. Retry the record

### DL02000001 error

When an import fails with a `DL02000001` error code then that means the importer was trying to retrieve a field that did not exist on an Intacct object. This could happen if you have modified an object definition to remove or modify a standard field that our importer requests, or if you have configured the importer to pull in a custom field that does not exist on Intacct.

### Undeposited funds error with multi-currency

> You cannot make payment for foreign currency invoice for payment method "XXX" using Undeposited Fund Account.

If you are in a multi-currency environment then you might see a `BL02000051` error code. You can only post a payment to an undeposited funds account if the payment is in your base currency. When you see this error the solution is to use a bank account (instead of an undeposited funds G/L account) for that currency/payment method combination in order for the payment to post to Intacct.
