# online-retail-revenue-leakage
Power BI dashboards and report on UK online retail sales (2009 to 2011), checking revenue leakage, invoice completion and stock loss with Power Query, DAX and Excel.

I built these dashboards to find out how much revenue the business loses between gross sales and net revenue, and how well its invoices are completed. While checking my own numbers, I found that some headline figures looked worse than the real situation. The report explains why.

## Dashboard previews
### Dashboard 1: Revenue Leakage
<img width="1160" height="656" alt="Screenshot 2026-10-05 at 7 56 27 AM" src="https://github.com/user-attachments/assets/0f6372b7-a6bf-4681-9e5f-5674494250e3" />

### Dashboard 2: Performance and Operational Risk
<img width="1160" height="656" alt="Screenshot 2026-10-05 at 7 57 08 AM" src="https://github.com/user-attachments/assets/bcdd7cf1-a2a3-45f2-b8bf-62260cbfccf4" />

## About the data
- Dataset: Online Retail II, UCI Machine Learning Repository
- Link: https://archive.ics.uci.edu/dataset/502/online+retail+ii
- Licence: CC BY 4.0
- Credit: Chen, Daqing (2019). Online Retail II.
- A UK-based online shop that mainly sells gift-ware. Many of its customers are wholesalers.
- 1,067,371 rows in the original data. After removing duplicates in Power Query, 1,033,036 rows were used.
- The data ends on 9 December 2011, so December 2011 is not a full month.

The raw data file is not in this repository because it is large. Please download it from the link above.
  
## What I did
1. Combined the two yearly sheets and cleaned the data in Power Query.
2. Marked every row as Completed, Cancelled or Inventory Adjustment (I/A), and as Product or Non-Product.
3. Calculated RFM scores for customers in Excel.
4. Built the measures in DAX and the two dashboards in Power BI.
5. Checked the dashboard numbers against the data and wrote the report.

Tools: Power Query, DAX, Power BI, Excel.

## Main findings
- The leakage rate is 7.14% (£1.46M on £20.48M of gross sales). Two orders that were bought and cancelled on the same day (£168K and £77K) lift it. Without them the rate is 6.02%.
- 51% of the leakage is fees and adjustments (mostly the codes M and AMAZONFEE), not customers cancelling products.
- Product cancellations are 3.65% of product sales, or 2.43% without the two same-day orders.
- After removing those two orders, the leakage rate did not rise from 2010 (6.28%) to 2011 (5.99%).
- The invoice completion rate is 74.74%, but about 10% of invoices are stock adjustments, not orders. Counting only customer orders, it is 82.9%.
- The stock loss card shows 805K units, but it counts added stock as loss too. The net removal is 333K units.
- The UK has 86.6% of the leakage, but its rate (7.27%) is close to the other countries (6.41%). Very high rates appear only in small markets such as Singapore and Hong Kong, with few invoices.
- 36% of customers (Strong and Champion segments) bring about 76% of net spending.
  
## Problems I found in my own dashboards
I listed 14 problems with suggested fixes in the report. The main ones are:
- Fees and adjustments are mixed with cancellations in the leakage rate.
- The inventory loss measure uses absolute values.
- Some stock codes are repeated in the product summary table.
- The trend chart leaves out December 2009.

## Repository structure
online-retail-revenue-leakage/
├── README.md
├── report/        Word report and PDF copy
├── dashboards/    Power BI file (.pbix) and page screenshots
├── data/          E_Commerce.xlsx (Power Query output and RFM tables)
└── images/        Screenshots used in this README

## Limitations
- Only one retailer and about two years of data.
- There is no cost or margin data, so I can measure lost sales value but not lost profit.
- The data does not say why an invoice was cancelled.
- A cancellation is not linked to its original invoice, so I matched same-day orders by customer, product and quantity.
- My reading of codes such as M, D and S, and of the stock adjustment descriptions, should be confirmed with the business.

## Author
Mayakrishnan Perumal (MK) MSc in Data Analytics, Dublin, Ireland.  
LinkedIn:https://www.linkedin.com/in/mayakrishnan-p/?isSelfProfile=true
