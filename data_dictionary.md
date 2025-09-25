# Data Dictionary – Sales Financial Dataset

This document describes the fields used in the `sales_financial.csv` dataset.

| Column       | Description                                                                 | Example Value      |
|--------------|-----------------------------------------------------------------------------|--------------------|
| OrderID      | Unique identifier for each sales order                                      | 1001               |
| OrderDate    | Date when the order was placed                                              | 2024-01-05         |
| Region       | Broad geographical region of the customer                                   | East               |
| State        | State where the order was placed                                            | New York           |
| City         | City where the order was placed                                             | New York           |
| Category     | High-level product category                                                 | Furniture          |
| SubCategory  | More detailed category under the main category                              | Chairs             |
| Product      | Specific product name                                                       | Office Chair       |
| Quantity     | Number of units ordered                                                     | 3                  |
| Sales        | Total sales value (post-discount, before cost)                              | 450.00             |
| Cost         | Cost of goods sold                                                          | 300.00             |
| Profit       | Sales – Cost (net profit)                                                   | 150.00             |
| Discount     | Discount amount applied on the sale                                         | 20.00              |
