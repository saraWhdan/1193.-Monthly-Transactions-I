# 1193. Monthly Transactions I
### Problem Description :[ Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/description/?envType=study-plan-v2&envId=top-sql-50)
## Solution 
```sql
/* Write your T-SQL query statement below */
SELECT 
    CAST(YEAR(trans_date ) AS VARCHAR(4)) + '-' + RIGHT('00' + CAST(MONTH(trans_date ) AS VARCHAR(2)), 2) AS month
    ,country
    ,count(*) trans_count,
    sum(case when state='approved' then 1 else 0 end) approved_count
   , sum(amount) trans_total_amount
   ,isnull(sum(case when state='approved' then amount else 0 end),0)approved_total_amount
FROM Transactions
group by YEAR(trans_date ),MONTH(trans_date ),country
order by  YEAR(trans_date ),MONTH(trans_date ),country desc
