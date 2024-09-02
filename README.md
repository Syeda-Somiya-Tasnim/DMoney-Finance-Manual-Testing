# DMoney-Finance-Manual-Testing
# EasyPay MFS Mobile App

This repository contains the documentation and test cases for the EasyPay MFS mobile app, covering the implementation and testing of two key features: Merchant and Utility Bill Payment with cashback rules, and the Loan Facility. Additionally, bug/improvement reports for the admin functionalities on the `dmoney-web` site are included.

## Features

### Feature 1: Merchant and Utility Bill Payment with Cashback & Service Charge
- **Service Charge:** A 1% service charge will be deducted for each merchant payment, with a minimum fee of 5 TK.
- **Cashback Rules for Merchant Payments:** 
  - Transactions over 5000 TK: 10% cashback.
  - Transactions over 10,000 TK: 20% cashback, capped at 3000 TK.
  - **No cashback for utility bill payments.**

### Feature 2: Loan Facility
- **Loan Eligibility:** Customers with a balance of less than 100 TK can apply for a loan of up to 20,000 TK.
- **Interest-Free Repayment:** No interest if the loan is repaid within 30 days.
- **Interest on Late Repayment:** 1.8% daily compound interest on the remaining amount after the 30-day period.
- **Additional Loan Eligibility:** Customers who have repaid 50% of their remaining loan balance are eligible for another loan.

## Acceptance Criteria

### Feature 1: Merchant and Utility Bill Payment
- **AC1:** The system should deduct a 1% service charge from each merchant payment, with a minimum fee of 5 TK.
- **AC2:** For merchant transactions above 5000 TK, the customer should receive a 10% cashback.
- **AC3:** For merchant transactions above 10,000 TK, the customer should receive a 20% cashback, capped at 3000 TK.
- **AC4:** No cashback should be applied for utility bill payments.

### Feature 2: Loan Facility
- **AC1:** The system should allow customers with a balance of less than 100 TK to apply for a loan of up to 20,000 TK.
- **AC2:** No interest should be applied if the loan is repaid within 30 days.
- **AC3:** A daily interest of 1.8% should be applied in a compound manner on the remaining loan balance after the 30-day period.
- **AC4:** The system should allow customers who have repaid 50% of their remaining loan balance to apply for another loan.

## Test Cases

### Feature 1: Merchant and Utility Bill Payment

| Test Case ID | Test Case Description | Pre-Conditions | Steps | Expected Result | Actual Result | Status (Pass/Fail) |
| ------------ | --------------------- | -------------- | ----- | --------------- | ------------- | ------------------ |
| TC1          | Verify service charge deduction for merchant payment | User is logged in with a sufficient balance | 1. Make a merchant payment of 1000 TK | A 1% service charge (10 TK) is deducted | | |
| TC2          | Verify minimum service charge of 5 TK is applied | User is logged in with a sufficient balance | 1. Make a merchant payment of 400 TK | A minimum service charge of 5 TK is deducted | | |
| TC3          | Verify cashback of 10% for transactions over 5000 TK | User is logged in with a sufficient balance | 1. Make a merchant payment of 6000 TK | A cashback of 600 TK is received | | |
| TC4          | Verify cashback of 20% for transactions over 10,000 TK | User is logged in with a sufficient balance | 1. Make a merchant payment of 11,000 TK | A cashback of 2200 TK is received, capped at 3000 TK | | |
| TC5          | Verify no cashback for utility bill payments | User is logged in with a sufficient balance | 1. Make a utility bill payment of 7000 TK | No cashback is received | | |

### Feature 2: Loan Facility

| Test Case ID | Test Case Description | Pre-Conditions | Steps | Expected Result | Actual Result | Status (Pass/Fail) |
| ------------ | --------------------- | -------------- | ----- | --------------- | ------------- | ------------------ |
| TC6          | Verify loan application for balance below 100 TK | User balance is below 100 TK | 1. Apply for a loan of 10,000 TK | Loan application is successful | | |
| TC7          | Verify no interest is charged for repayment within 30 days | Loan has been taken | 1. Repay the loan within 30 days | No interest is charged on the loan | | |
| TC8          | Verify interest is charged for late repayment | Loan has been taken | 1. Repay the loan after 30 days | A daily compound interest of 1.8% is applied on the remaining balance | | |
| TC9          | Verify eligibility for another loan after repaying 50% of the current loan | Customer has repaid 50% of the remaining loan | 1. Apply for another loan | Loan application is successful | | |
| TC10         | Verify loan application rejection for balance over 100 TK | User balance is over 100 TK | 1. Apply for a loan | Loan application is rejected | | |

## Bug/Improvement Reporting

### URL: https://dmoney-web.vercel.app/

1. **Bug ID:** 001
   - **Title:** Inconsistent deposit amounts for agents.
   - **Severity:** High
   - **Priority:** Medium
   - **Steps to Reproduce:** 
     1. Login as admin.
     2. Create an agent.
     3. Deposit to the agent multiple times.
   - **Expected Result:** Deposited amounts should be accurate.
   - **Actual Result:** Inconsistent amounts are reflected in the agent's balance.

2. **Bug ID:** 002
   - **Title:** Missing validation on customer withdrawal form.
   - **Severity:** Medium
   - **Priority:** High
   - **Steps to Reproduce:** 
     1. Login as a customer.
     2. Attempt to withdraw without entering an amount.
   - **Expected Result:** Validation should prevent submission.
   - **Actual Result:** Form is submitted without entering an amount.

... [Add more bugs/improvements with appropriate severity and priority]

## Feature Prioritization
Please refer to the [Google Doc](https://docs.google.com/document) for the full feature prioritization, which includes a priority table and explanations for how the features were prioritized based on the needs of the app and potential user impact.
