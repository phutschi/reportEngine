# Report Engine
## Description
Ruby scripts talk to the API's of each country website. They collect data like amount of appointments or orders and report them to the corresponding department.

## Technology
Scripts run in Ruby on iron.io.

## Scripts
### Appointments vs. orders
Runs **Mondays @ 00:01**. Is sent to **each countries lp department**. Includes **optician number, optician title, number of appointments, number of orders and a difference calculated of both numbers**.

no     | title         | appointments | orders | difference
------ | ------------- | ------------ | ------ | ----------
022001 | Optician Name | 15           | 15     | 0

For the weekly report the previous calendar week is selected by default. Timeframe can be defined by the payload but only when firing the report manually.

**API needed...**
- ...that connects to the collection of opticians and returns an object of all
- ...that connects to the calendar module and returns all Appointments
- ...that connects to the order database and returns all orders

**Returned Objects:**  

_Opticians_

```
{
  optician_no: String,
  optician_name: String
}
```

_Appointments_

```
{
  optician_no: String,
  number_of_appointments: Integer
}
```

_Orders_

```
{
  optician_no: String,
  number_of_orders: Integer
}
```

During the merge process the script iterates over each optician and tries to find a corresponding number of appointments and orders in the other objects. If one is found these numbers are added to the optician. If not a zero is added instead. When the merge process is fnished an object including all opticians and numbers gets returned and stored in a .csv file. This file gets sent to the lp department.

The script is located at <kbd>[iron.io][ee31e1dd]</kbd>. The API's are located at admin level of each countries website location.

[ee31e1dd]: http://www.iron.io "iron.io"
