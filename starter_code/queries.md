![Ironhack Logo](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

### 1. All the companies whose name match 'Babelgum'. Retrieve only their `name` field.

<!-- Your Code Goes Here -->

//Query

{
"name": "Babelgum"
}

//Options

{
"project": {
"name": 1
}
}

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

<!-- Your Code Goes Here -->

//Query

{
"number_of_employees":{
\$gt: 5000
},
}

//Options

{
"sort" : {
"number_of_employees": 1
},

"limit": 20
}

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fields.

<!-- Your Code Goes Here -->

//Query

{
"founded_year":{
$gte: 2000,
$lte:2005
}
}

//Options

{
"project": {
"name": 1,
"founded_year": 1
}
}

### 4. All the companies that had a Valuation Amount of more than 100.000.000, and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

<!-- Your Code Goes Here -->

//Query

{
"ipo.valuation_amount":{
$gt:100000000
}, 
"founded_year":{
$lt: 2010
}
}

//Options

{
"project": {
"name": 1,
"ipo":1
}  
}

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

<!-- Your Code Goes Here -->

//Query

{
"number_of_employees": {
$lt: 1000
},
"founded_year":{
$lt:2005
}
}

//Options

{
"sort": {
"number_of_employees":1
},

"limit": 10
}

### 6. All the companies that don't include the `partners` field.

<!-- Your Code Goes Here -->

//Query

{
"partners" : {
\$exists: "false"
}
}

### 7. All the companies that have a null value on the `category_code` field.

<!-- Your Code Goes Here -->

//Query

{
"category_code": null
}

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

<!-- Your Code Goes Here -->

//Query

{
"number_of_employees": {
$gte: 100, 
$lt:1000
}
}

//Options

{
"project" : {
"name":1,
"number_of_employees":1
}
}

### 9. All the companies ordered by their IPO price in a descending manner.

<!-- Your Code Goes Here -->

//Query

{
"ipo": {
\$exists: "true"
}
}

//Options

{
"sort" :{
"ipo": -1
}
}

### 10. The 10 companies with the highest amount of employees, order by the `number of employees`.

<!-- Your Code Goes Here -->

{
"sort": {
"number_of_employees": -1
},
"limit": 10
}

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

<!-- Your Code Goes Here -->

//Query

{
"founded_month": {
$exists: "true",
$gt:6
}
}

//Options

{
"limit" : 1000
}

### 12. All the companies founded before 2000 that have an acquisition amount of more than 10.000.000.

<!-- Your Code Goes Here -->

{
"founded_year": {
$lt: 2000
}, 
"acquisition.price_amount": {
$exists: "true",
\$gt:10000000
}
}

### 13. All the companies that have been acquired after 2010, ordered by the acquisition amount, retrieving only their `name` and `acquisition` fields.

<!-- Your Code Goes Here -->

//Query

{
"acquisition.acquired_year": {
$gt: 2010
},
"acquisition.price_amount": {
$ne: null
}
}

//Options

{
"project": {
"name":1,
"acquisition": 1
}
"sort" : {
"acquisition.price_amount": 1
}
}

### 14. All companies ordered by their `founded year`, retrieving only their `name` and `founded year`.

<!-- Your Code Goes Here -->

//Query

{
"founded_year": {
\$ne: null
}
}

//Options
{
"project": {
"name":1,
"founded_year":1
}
"sort": {
"founded_year": 1
}
}

### 15. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `acquisition price` in a descending order. Limit the search to 10 documents.

<!-- Your Code Goes Here -->

//Query

{
"founded_day":{
$exists:"true",
$lte: 7
},
"acquisition.price_amount": {
\$ne:null
}
}

//Options

{
"project": {
"acquisition":1,
"founded_day":1
}
"sort" : {
"acquisition.price_amount": -1
}
"limit": 10
}

### 16. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascending order.

<!-- Your Code Goes Here -->

//Query

{
"category_code": "web",
"number_of_employees": {
\$gt: 4000
}
}

//Options
{
"sort": {
"number_of_employees": 1
}
}

### 17. All the companies whose acquisition amount was more than 10.000.000, and in which the acquisition currency is 'EUR'.

<!-- Your Code Goes Here -->

//Query

{
"acquisition.price_amount": {
\$gt: 10000000
},
"acquisition.price_currency_code": "EUR"

}

### 18. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

<!-- Your Code Goes Here -->

//Query

{
"acquisition.acquired_month": {
$exists: "true",
$lte: 4
}
}

//Options

{
"project": {
"name":1,
"acquisition": 1
}
}

### 19. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

<!-- Your Code Goes Here -->

//Query

{
"founded_year": {
$lt: 2010,
    $gt: 2000
},
"acquisition.acquired_year": {
\$gt: 2011
}
}
