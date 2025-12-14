# Pivot Table Setup + Key Queries

## 1. Monthly Inquiry Trend
Pivot Table:
- Rows → Inquiry Date (Group by Month)
- Values → Count of Inquiry_ID
- Filter → Project 

## 2. Monthly Sales Trend
Pivot Table:
- Rows → Sales Date (Group by Month)
- Values → SUM of Units_Sold
- Filter → Project

## 3. Lead Source Performance
Pivot Table:
- Rows → Source
- Values → Count of Inquiry_ID

## 4. Status Pipeline
Pivot Table:
- Rows → Status
- Values → Count of Inquiry_ID

## 5. Lead vs Sales Combined
Using QUERY:

=QUERY(
  {Inquiry_Data!B2:G, ARRAYFORMULA(IF(ROW(Inquiry_Data!A2:A)="",,0))};
  "SELECT Col1, COUNT(Col1) GROUP BY Col1";
  0
)

=QUERY(
  {Sales_Data!B2:E};
  "SELECT Col1, SUM(Col3), SUM(Col4) GROUP BY Col1";
  0
)
