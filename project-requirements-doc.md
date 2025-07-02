# **Project Requirements Document: Gym Records & Income Tracker App**

app name: Ben Fitness Gym

The following table outlines the detailed functional requirements of the Gym Records & Income Tracker App.a

| Requirement ID | Description                    | User Story                                                                                            | Expected Behavior/Outcome                                                                                                                           |
| -------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| FR001          | Owner Login                    | As the gym owner, I want to log in securely to access the app.                                        | The system should allow a single owner account to log in using email and password (or PIN/biometric if available).                                  |
| FR002          | Add Customer                   | As the owner, I want to add a new customer with details like name, membership type, and payment info. | The app should provide a form to add a customer’s name, contact (optional), membership type (walk-in/monthly), payment amount, and start/end dates. |
| FR003          | View Customers                 | As the owner, I want to view all customers in a list.                                                 | The system should show a scrollable list of all customers, with filters for active, expired, or walk-in types.                                      |
| FR004          | Edit/Delete Customer           | As the owner, I want to update or remove customer records if needed.                                  | The system should allow editing existing customer info and deleting records with a confirmation prompt.                                             |
| FR005          | Record Walk-In Payment         | As the owner, I want to log a one-time payment from a walk-in customer.                               | The app should let the owner quickly record payment amount and timestamp under walk-in income.                                                      |
| FR006          | Record Monthly Subscription    | As the owner, I want to record subscription payments for monthly members.                             | The system should store the payment amount and auto-calculate expiration date (e.g. +30 days).                                                      |
| FR007          | View Daily/Monthly Income      | As the owner, I want to see total income per day or month.                                            | The dashboard should display total income from walk-ins and subscriptions for selected date ranges.                                                 |
| FR008          | Dashboard Summary              | As the owner, I want a quick overview of stats like active members and income.                        | The dashboard should show: total customers, active/expired members, today’s income, this month’s income, and simple charts.                         |
| FR009          | Subscription Expiry Alerts     | As the owner, I want to know when a customer’s subscription is about to expire.                       | The app should highlight members expiring today or within 3 days with a color tag or banner.                                                        |
| FR010          | Search Customers               | As the owner, I want to quickly search for a customer by name.                                        | The customer list should include a search bar to find users instantly.                                                                              |
| FR011          | Backup/Restore Data (Optional) | As the owner, I want to back up my records or restore them if I change devices.                       | The system should support local backup (to file) or optional Firebase sync for online storage and recovery.                                         |
| FR012          | App Settings                   | As the owner, I want to edit my gym name or logout of the app.                                        | The settings screen should include gym name/logo, change password (if needed), and logout button.                                                   |

---

Let me know if you want to add more modules (like expenses, attendance, or image receipts), or if you want a Firestore structure or mock UI next.
