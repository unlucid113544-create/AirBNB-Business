# AirBNB-Business-Data-Analysis (Interactive Dashboard creation using MS Excel, PostgreSQL and MS PowerBI)

## AirBNB Business Data Analysis
An Airbnb business operating across multiple locations in the Philippines, offering a range of accommodations  from cozy studio units to spacious apartments for your vacation or staycation plans. 

## Project Objective
This project aims to create an easy to understand dashboard  to review the track down the trend and growth of the AirBNB business for the year 2024. It’s designed to give clear insights on which areas to focus the business decisions and to continue the growth.

## Dashboard
- <a href="https://github.com/unlucid113544-create/AirBNB-Business/blob/main/Portfolio%201.0%20AIRBNB.pbix">AirBNB Dashboard</a>

<img width="4150" height="2400" alt="Dashboard" src="https://github.com/user-attachments/assets/84320732-8969-4c29-8d72-26810f5c3b40" />

## Business Question 1:
Which property generated the highest revenue of the year 2024?

```sql
SELECT pro.property_name, 
	SUM (b.total_price) AS total_revenues
FROM bookings b
JOIN properties pro ON b.property_id = pro.property_id
WHERE b.booking_status = 'Completed'
GROUP BY pro.property_name
ORDER BY total_revenues;
```

## Business Question 2:
Whats the Average revenue per booking for each property type?

```sql
SELECT pro.property_name, 
	ROUND(AVG(b.total_price),2) AS total_revenues
FROM bookings b
JOIN properties pro ON b.property_id = pro.property_id
WHERE b.booking_status = 'Completed'
GROUP BY pro.property_name
ORDER BY total_revenues;
```

## Business Question 3:
Which location generated the highest earnings? 
```sql
SELECT pro.location, 
	SUM(b.total_price) AS total_revenues
FROM bookings b
JOIN properties pro ON b.property_id = pro.property_id
WHERE b.booking_status = 'Completed'
GROUP BY pro.location
ORDER BY total_revenues DESC;
```

## Business Question 4:
Which nationality books the most nights overall?
```sql
SELECT 
	gu.nationality,
	SUM(b.check_out - b.check_in) AS total_nights
FROM bookings b
JOIN guests gu ON b.guest_id = gu.guest_id
WHERE booking_status = 'Completed'
GROUP BY gu.nationality
ORDER BY total_nights DESC;
```

## Business Question 5:
How many bookings per month?
```sql
SELECT 
	EXTRACT(YEAR FROM check_in) as YEAR,
	EXTRACT(MONTH FROM check_in) as MONTH,
	COUNT (*) AS total_bookings
FROM bookings
GROUP BY year, month
ORDER BY year, month;
```

## Business Question 6:
Top 20 Guests bookings
