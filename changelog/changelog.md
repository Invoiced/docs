# Release Notes

This page contains release notes for Invoiced. Each week we will share what is new on Invoiced. The API changelog can be found [here](https://github.com/Invoiced/api/blob/master/CHANGELOG.md).

## Mar 12, 2021
**New features**
- The payment pages in the customer portal have an updated look. No functionality was changed in this update.
- Creating a Promise-to-Pay through the customer portal has an added **Payment Reference #** field.

## Mar 5, 2021
**New features**
- QuickBooks Online initial import tool has a transaction date range option. Previously all transactions were imported.

**Bug Fixes**
- Fixed a missing draft invoices setting in the QuickBooks Online integration settings.

## Feb 26, 2021
**New features**
- <span class="label label-success">Major</span> QuickBooks Online integration update. See details below.
- <span class="label label-success">Major</span> Intacct integration syncs payments at payment level instead of line item level. Voiding payments on Invoiced will reverse the corresponding payment on Intacct.
- <span class="label label-success">Major</span> Sub-customer transactions are included in Balance Forward and Open Item statements.
- <span class="label label-success">Major</span> Credit notes can be applied in the customer portal if the *Select Invoices to Pay* setting is enabled. This setting is off by default and can be enabled in the customer portal settings.
- Added a CSV export option to the Payments page.
- The limit on the number of recipients in an email has been removed.
- There is a new failed charge event in the activity log when payments are declined. You can turn on notifications for failed payments in the notification settings.
- Estimate deposits can be paid using PayPal.
- Partial refunds are no longer permitted on the same day that a credit card payment is processed. This is because most payment gateways will void the full amount instead of a partial refund. Instead a full refund can be issued or a partial refund can be issued on the following day.
- The QuickBooks Desktop integration reads all invoices, paid or open.
- Pending line items can be created using items that do not have a default price.

**Bug fixes**
- Fixed a bug where QuickBooks Online custom fields had an inaccurate name.
- Labels are now consistent on customer portal and PDF statement views.
- Fixed a bug where the data type of object properties in webhook events was not consistent.
- Fixed a bug that prevented approving estimates when AutoPay was enabled and the estimate had a deposit amount.
- Subscription MRR value is now accurate when tax inclusive pricing is used.
- When a subscription that has the same plan used for 3 or more subscription addons was modified it could produce an incorrect proration.
- The Pay Now button is no longer shown in the customer portal if the amount owed will be collected by AutoPay.
- Fixed a bug where payments applied to multiple invoices would sometimes sync to Intacct as multiple payments.
- Early pay discounts on estimates would not be transferred to invoices generated from that estimate.
- Fixed a bug where reconciliation report would not include some prior period payments in the opening balance.
- Fixed a bug where transactions with the same date could have an out of order running balance value on account statements.
- In the QuickBooks Desktop integration reading a payment would fail if it was applied to an invoice belonging to a job and an invoice belonging to the parent customer.
- Fixed an object not found error in the QuickBooks Desktop integration when multiple A/R accounts are used.
- Fixed the line item price sent to Xero when tax inclusive pricing is used.
- Clicking the sort button in a table view now returns to the first page.
- Filtering with boolean custom fields was not memorized correctly.
- Fixed a bug that prevented some chasing legacy schedules from being edited.
- Sign up pages that were created from the customer page did not appear in the settings unless refreshing the page.
- Improved the error message shown when payments are declined using the Braintree payment gateway.

**QuickBooks Online integration new features**
- QuickBooks Online integration supports reading credit notes. This must be enabled in the integration settings.
- Data is read from QuickBooks Online hourly. Data is written to QuickBooks Online instantly.
- With the new continuous syncing the list of recent syncs on the Accounting Sync page has been replaced with a list of current sync failures.
- QuickBooks Online sync errors can be retried individually instead of re-syncing your entire account.
- Convenience fees are synced to QuickBooks Online by creating an invoice with a single line item called "Convenience Fee".
- The sub-customer/job hierarchy on QuickBooks Online is synced to Invoiced instead of creating a flat hierarchy.
- The QuickBooks Online import tools have been consolidated into a single tool that allows customers, invoices, payments, and credit memos to be imported with one click.
- Paid invoices can be imported from QuickBooks Online using the initial data import tool. Previously only open invoices could be imported.
- Transactions voided on QuickBooks Online (invoices, payments, credit memos) now void the corresponding transaction on Invoiced.
- Customer updates from QuickBooks Online are now synced to Invoiced even when there are no new invoices for that customer.
