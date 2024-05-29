# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).
```
Assumptions for my ERD:
Employee. Each employee is uniquely identified by an employee_id. Employees have unique email addresses.
Customer. Each customer is uniquely identified by a customer_id. Customers have unique email addresses. Basic contact information (e.g., phone number, address) is stored for each customer.
Book. Each book is uniquely identified by a book_id. Books are uniquely identified by their title (title), author (author), and publisher (publisher). Books have a price (price) and stock quantity (stock_quantity) to track availability.
Order. Each order is uniquely identified by an order_id. An order is placed by a customer (customer_id) and processed by an employee (employee_id). Each order includes a reference to the date it was placed (order_date), which links to the Date table. An order can consist of multiple sales transactions.
Sales. Each sales transaction is uniquely identified by a sales_id. Each sales transaction is associated with a specific order (order_id), book (book_id), and employee (employee_id). The quantity of books sold and the price per unit at the time of sale are recorded. The date of the sale (sales_date) is recorded and links to the Date table.
Date. Dates are managed in a separate Date table, uniquely identified by date_id. The Date table includes detailed date components like year, month, day, and weekday for easy querying and reporting.
```

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.
```
Assumptions for my ERD (shifts):
Shift. Each shift worked by an employee is recorded in the Employee_Shift table, uniquely identified by shift_id. The shift_date is recorded and links to the Date table. Shifts are classified as either 'Morning' or 'Evening'.
```

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Type 1 is a table that will overwrite changed. It's simpler and involves overwriting the address fields directly whenever the customer's address changes. This approach is simple, but doesn't save historical data. It's suitable when historical address information is not required and data storage needs to be minimized.
Type 2 is a table that will retain changes. It creates new records for each change, with each record indicating the period it was valid. This approach save customer address history, which can be useful for tracking customer movements and performing historical analysis. However, it requires more memory and a more complex implementation to process these additional records.

And yes, there are privacy implications to this, as retaining historical address data may raise privacy concerns for customers. Previous addresses are retained, but customers may no longer need them or they may no longer be relevant. This data must be protected.
```

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Differences:
1. The AdventureWorks Schema uses higher levels of normalization. The data is broken into many detailed tables. My ERD has few tables and is not so detailed.
2. The AdventureWorks Schema includes complex relationships and additional tables for detailed transactions and history. My ERD has simple relationships.
3. Zoning ERD by blocks.
4. The AdventureWorks Schema doesn't include the date table.

I would zone my ERD.
```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
