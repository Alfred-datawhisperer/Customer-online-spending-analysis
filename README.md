# Customer-online-spending-analysis



Let's look at the orders, items sold, revenue, and profit as key performance indicators for each country.

select 
    country,
    count(id) as total_orders,
    sum(quantity) as items_sold,
    sum(total_revenue)::money as revenue,
    sum(total_profit)::money as profit
from online_sales
group by country
order by items_sold desc;

-- Let's look at the basic demographic breakdown for customers in each country.

select
    country,
    gender,
    round(avg(age), 1) as age,
    round(avg(quantity), 1) as items_purchased,
    round(avg(total_cost), 2) as amount_spent
from online_sales
group by country, gender
order by country, gender;

-- Our customers who spend the most amount on an average order are 35-year-old females in Germany and 35-year-old males in France.
-- Our customers who spend the least amount on an average order are in the United States.

-- Let's look at the product categories with the most sales.

select
    category,
    count(id) as orders
from online_sales
group by category
order by orders desc;

-- Our accessories account 64.6% of all our online sales.

-- Let's look at a similar breakdown for the subcategories within accessories.

select 
    subcategory,
    count(id) as orders
from online_sales
where category = 'Accessories'
group by subcategory
order by orders desc;

-- Tires and tubes account for 49.3% of all our accessories sales.
