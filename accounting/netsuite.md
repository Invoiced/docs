# NetSuite

Invoiced integrates with NetSuite out of the box, a cloud-based ERP system. This document outlines how to setup and use the NetSuite integration.

## Overview

The NetSuite integration ships with the following capabilities:

- Importing outstanding invoices from NetSuite
- Importing customers from NetSuite
- Writing invoices generated on Invoiced to NetSuite
- Reconciling payments received on Invoiced to NetSuite
- Syncing payments recorded on NetSuite to Invoiced

[![NetSuite Data Flow](../img/netsuite-object-mapping.png)](../img/netsuite-object-mapping.png)

## Setup

In order to set up the NetSuite integration you first need these pieces of information:
- NetSuite Account ID
- OAuth Access Token

Below we will show you how to connect NetSuite with Invoiced, step-by-step.

### Setting Up an OAuth Access Token

The next step is to create an OAuth Access Token for Invoiced on NetSuite.

Coming Soon!

### Connecting NetSuite on Invoiced

1. Go to **Settings** > **Integrations** in the Invoiced dashboard.

   [![Integration Settings](../img/integration-settings.png)](../img/integration-settings.png)

2. Click on **Connect** on the NetSuite integration.

   [![Connect NetSuite](../img/connect-netsuite.png)](../img/connect-netsuite.png)

3. Enter in the NetSuite account ID, consumer secret, consumer key, token, and token secret for the Invoiced integration created earlier.

4. Click **Save**. NetSuite is now connected! Next you will likely want to configure the integration before using it.

   [![NetSuite Connected](../img/netsuite-connected.png)](../img/netsuite-connected.png)

### Configuring the Accounting Sync

Now you can configure the accounting sync in order to tell Invoiced how to map the data into your general ledger.

1. Click on **Configure** on the NetSuite integration from the integrations page.

   [![NetSuite Integration Settings](../img/netsuite-integration-settings.png)](../img/netsuite-integration-settings.png)

2. Select the item account from your G/L on NetSuite. This is the default account where new line items are mapped.

3. Select the undeposited funds account label from your G/L on NetSuite. This is where payments received through Invoiced will be mapped.

4. Click **Save**.

## Usage

In this section you will learn how to use the NetSuite integration.

### Enabling Auto-Sync

Auto-sync will run accounting syncs automatically for you on an ongoing basis. Once auto-sync is enabled, accounting syncs will happen approximately once per hour. Here's how you can enable auto-sync:

1. Go to **Settings** > **Accounting Sync**. Select **NetSuite** as your accounting system, if not already selected.

   [![NetSuite Accounting Sync](../img/netsuite-accounting-sync-connected.png)](../img/netsuite-accounting-sync-connected.png)

2. Click **Enable Auto-Sync** next to the NetSuite integration. You can periodically check back here to see activity in the *Recent Syncs* table.

   [![NetSuite Accounting Sync](../img/netsuite-accounting-sync.png)](../img/netsuite-accounting-sync.png)

### Running Syncs Manually

If you want control over when your books are synced then you can manually trigger accounting syncs. You can run an accounting sync by following these steps:

1. Go to **Settings** > **Accounting Sync**. Select **NetSuite** as your accounting system, if not already selected.

   [![NetSuite Accounting Sync](../img/netsuite-accounting-sync-connected.png)](../img/netsuite-accounting-sync-connected.png)

2. Click **Sync Now** underneath *NetSuite* any time you want to run an accounting sync. When the job is finished you will see it in the *Recent Syncs* table.

   [![NetSuite Accounting Sync](../img/netsuite-accounting-sync.png)](../img/netsuite-accounting-sync.png)

### Manual Invoice Imports

You can import outstanding invoices from NetSuite using the invoice importer. With the NetSuite invoice importer you have the option to pull in invoices from the **Accounts Receivable** or **Order Entry** module, depending on where you create your invoices. If you are using the Order Entry module then it is recommended to import invoices from there as the invoices will have more detail, such as the line item quantity.

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Invoices Page](../img/invoices-header.png)](../img/invoices-header.png)

2. Select **NetSuite**.

   [![Invoice Importer](../img/invoice-importer.png)](../img/invoice-importer.png)

3. When ready to import, click **Start**.

   [![Start NetSuite Invoice Import](../img/netsuite-invoice-importer-options.png)](../img/netsuite-invoice-importer-options.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Invoice Import Started](../img/netsuite-invoice-importer-pending.png)](../img/netsuite-invoice-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

   [![NetSuite Invoice Import Finished](../img/netsuite-invoice-importer-finished.png)](../img/netsuite-invoice-importer-finished.png)

### Manual Customer Imports

You can import customers from NetSuite into Invoiced as a one-time import. Why might you use this? The accounting sync will only import customers that have invoices, whereas a manual import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Customers Page](../img/customers-header.png)](../img/customers-header.png)

2. Select **NetSuite**.

   [![Customer Importer](../img/customer-importer.png)](../img/customer-importer.png)

3. Click **Start**.

   [![Start NetSuite Customer Import](../img/netsuite-customer-importer.png)](../img/netsuite-customer-importer.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Customer Import Started](../img/netsuite-customer-importer-pending.png)](../img/netsuite-customer-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

   [![NetSuite Customer Import Finished](../img/netsuite-customer-importer-finished.png)](../img/netsuite-customer-importer-finished.png)

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the NetSuite integration.

- Customers on Invoiced are mapped to customers on NetSuite by the customer name.

- Only non-draft invoices on Invoiced that have been updated since the last sync will be synced. On your first sync this means that all non-draft invoices will be synced.

- Any changes to invoices imported from NetSuite that are later modified on Invoiced will not be synced to NetSuite. Payments processed through Invoiced for imported invoices will still be synced.

## Troubleshooting

When a sync fails you will be able to see the error message in the *Recent Syncs* section in **Settings** > **Accounting Sync**. Normally the error message will include the invoice # that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your books synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Finding Your NetSuite Account ID

Your NetSuite account ID is required in order to connect the integration. You can obtain your account ID from NetSuite with these steps:

1. Within the NetSuite application, hover over the **Setup** tab and click **Company** > **Company Information**.

2. You should see an *Account ID* field. This is the account ID that you will use in the connection steps.