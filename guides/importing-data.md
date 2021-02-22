# Importing Data

It's easy to import customers, invoices, payments, and items into Invoiced. This guide shows you how to import data into Invoiced using our importer.

## Usage

The import tool works by letting you build a spreadsheet where each line contains a record that you want to import. Once you have your spreadsheet ready to go, you simple copy the contents and paste it into the textbox on the new import page. In the next step we will help you match each column to a field in Invoiced. Finally, just click the button to start the import and we will notify you when it's finished.

We recommend using the first line to specify which field on Invoiced the line matches up with. It's not required, however, it makes the import process quicker. You can get the field names from the sample import templates below for the type of record you are trying to import. Invoiced will automatically match the columns after the first step. 

A few notes:

- All dates must be entered using this format: `Aug-06-2015`
- Any unused, optional fields can be removed or left blank
- If there's a failure in your import we will show you each line that failed with the reason on the import page.
- All importers support setting metadata on imported objects for any columns with a title following the pattern: `metadata.key` where `key` is the name of the metadata property. For example, you could add a `sales-rep` metadata value by adding a `metadata.sales-rep` column.

### Customers

Steps to import Customers:

1. Go to the **Customers** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/customers-import-template.xlsx) a sample customers import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The only required field is the customer's name.
- Customers are identified by their account number first, and if that's not given then customers are identified by their name. If a customer with the same account number (or name if account # was not given) has already been created in Invoiced then a new customer will not be created.
- You can supply an account # or if left empty we will generate one for you.
- The *Type* field can only be one of `person`, `company`, or blank.

### Invoices

Steps to import Invoices:

1. Go to the **Invoices** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/invoices-import-template.xlsx) a sample invoices import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The only required field is one of *Customer Name*, *Customer ID*, or *Account #*.
- Each line represents an invoice AND a corresponding line item.
If an invoice has multiple line items then you would have multiple lines for the same invoice. Only the first line needs to include the invoice's information. Subsequent lines must have the same invoice #, however only need to have the line item fields filled in (*Item*, *Description*, *Quantity*, *Unit Cost*, *Tax*, and *Discounts*).
- You can supply an invoice # or leave it blank. If left blank we will generate one for you.
- Customers are identified by their account number first, and if that's not given then customers are identified by their name. If a customer with the same account number (or name if account # was not given) has already been created in Invoiced then the existing customer will be used. Otherwise, we will create a new customer.
- The *Currency* field should use an [ISO-4217](https://en.wikipedia.org/wiki/ISO_4217) currency code. Otherwise, we will use your default currency.
- The *Type* field can be one of `product`, `service`, `expense`, `hours`, `days`, `month`, `year`, `shipping`, or blank

### Payments

Steps to import Payments:

1. Go to the **Payments** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/payments-import-template.xlsx) a sample payments import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *Amount* and one of *Invoice #*, *Invoice ID*, *Customer Name*, *Customer ID*, or *Account #*.
- The payment method can be one of `credit_card`, `ach`, `paypal`, `check`, `wire_transfer`, `cash`, `other`
- When the payment method is `check` you can pass in a check # with the *Transaction ID* field
- The *Gateway* field should only be used when tracking electionic payments

### Items

1. Go to **Settings** &rarr; **Items**

2. Click **Import**

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/items-import-template.xlsx) a sample items import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *ID* and *Name*
- The *ID* field must be at least 2 characters long and can only be alphanumeric, dashes, or underscores
- The *Type* field can be one of `product`, `service`, `expense`, `hours`, `days`, `month`, `year`, `shipping`, or blank

### Plans

1. Go to **Settings** &rarr; **Plans**

2. Click **Import**

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/plans-import-template.xlsx) a sample plans import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *ID*, *Name*, *Interval*, *Interval Count*, and *Amount*
- The *ID* field must be at least 2 characters long and can only be alphanumeric, dashes, or underscores
- The *Interval* field can be one of `day`, `week`, `month`, `year`
- The *Interval Count* field must be 1 or greater, i.e. interval count of 3 with an interval of `month` is billed qaurterly.

### Coupons

1. Go to **Settings** &rarr; **Coupons**

2. Click **Import**

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/coupons-import-template.xlsx) a sample coupons import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *ID*, *Name*, and *Value*
- The *ID* field must be at least 2 characters long and can only be alphanumeric, dashes, or underscores

### Tax Rates

1. Go to **Settings** &rarr; **Tax Rates**

2. Click **Import**

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://app.invoiced.com/files/tax-rates-import-template.xlsx) a sample tax rates import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *ID*, *Name*, and *Value*
- The *ID* field must be at least 2 characters long and can only be alphanumeric, dashes, or underscores

### Rolling back imports

Did your import not turn out the way you expected? Not a problem! You can rollback any import with the click of a button provided it happened within the last 3 days. Simply open the import in the dashboard and click the red **Rollback Import** button.

There is a limit on the size of imports that can be rolled back. If your import has more than a few thousand records then you might not be able to rollback. The exact limit depends on the complexity of your records (i.e. number of line items).