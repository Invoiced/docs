# Custom Fields

With custom fields you can store arbitrary business data on customer accounts and invoices. That data can then be displayed on the invoice presented to your customer.

Custom fields have many uses. Here's just a few scenarios where custom fields can help:

- Keeping track of the sales representative for customer accounts
- Segmenting receivables by department
- Adding purchase order numbers to invoices
- Internal tracking purposes

## Usage

### Creating a custom field

You can add a new custom field by going to **Settings** &rarr; **Custom Fields** &rarr; **New Custom Field**.

#### Supported Object Types

These object types support custom fields:
- Credit Note
- Customer
- Estimate
- Invoice
- Item
- Line Item
- Payment
- Plan
- Subscription
- Transaction

#### Limitations

- The custom field ID must be unique per object type and cannot be changed later.
- Only 10 custom fields can be created per object type.
- Custom field titles are limited to **40 characters**.
- Values set on customer accounts and invoices are limited to **255 characters**.

### Using custom fields

Once you have created a custom field you can begin using it immediately. When creating or editing data (i.e. customers and invoices) in the application you will see form elements for the custom fields you have added.

If you have enabled customer visibility on your custom field, then customers will see it in the customer portal and on documents. Not every object supports displaying custom field values to a customer. This feature is primarily reserved for custom fields on customers, invoices and line items.  Any non-empty, customer-visible custom field will be displayed on the invoice presented to your customer. If the custom field is empty on the invoice then it will inherit its value from the customer account.

These object types can display a custom field to customers when enabled:
- Customer
- Invoice
- Estimate
- Credit Note
- Line Item
- Subscription

[![Custom Field Invoice](/docs/img/custom-field-invoice.png)](/docs/img/custom-field-invoice.png)

### Filtering

When browsing customers, invoices, estimates, subscriptions, and payments inside of the dashboard you can filter the results by custom field values. This setting is available within the **Filter** menu. Any results return will exactly match the filter you have built.

### Reporting

Custom fields enhance your reporting by making additional filtering and grouping options available.

#### Report Filtering

You can filter reports to only include invoices that exactly match a custom field value. Want to see how a specific region or department is performing?

#### Report Grouping

Any of the invoice reports can be grouped by custom field values using the **Group By** option. The custom field must have been set up with a pre-defined list of choices in order to support grouping. This might be useful for building a sales by rep report.

The resulting report will look like this:

[![Custom Field Report Group By](/docs/img/custom-field-grouped-report-sales.png)](/docs/img/custom-field-grouped-report-sales.png)

### Importing

Custom field values can be set when [importing](/resources/docs/guides/importing-data) customers and invoices.

### Field Inheritance

In certain circumstances custom field values will be inherited from related objects. For example, you could have a "Sales Rep" field that is used across customers, invoices, and payments. This section documents all scenarios where custom fields can be inherited. Custom fields are matched across object types, such as from a customer to an invoice, using the custom field ID and not the name.

1. When an invoice, credit note, or estimate PDF is generated, each custom field without a value will inherit its value from the customer.
2. Invoices will inherit matching custom field values on creation from the subscription.
3. Line items will inherit ALL custom field values from the associated plan. Matching custom fields are not required in this scenario.
4. Transactions will inherit matching custom field values on creation from the associated invoice.

### Deleting Custom Fields

If a custom field is deleted then the previously entered values will NOT be deleted. The underlying data will be maintained in the object metadata regardless of whether the custom field exists.