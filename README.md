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
