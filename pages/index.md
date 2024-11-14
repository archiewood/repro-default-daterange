<DateRange
    name=date_picker
    start='2021-01-01'
    end='2021-10-21'
    dates=readable_date
    defaultValue='Last 7 Days'
/>

```sql dates
select 
'${inputs.date_picker.start}' as start, 
'${inputs.date_picker.end}' as end
```

<DataTable data={dates}/>

```sql orders_per_day
select 
date_trunc('day', order_datetime) as date,
count(*) as orders
from orders
where order_datetime between '${inputs.date_picker.start}' and '${inputs.date_picker.end}'
group by 1
```

<LineChart
    data={orders_per_day}
    x=date
    y=orders
/>

