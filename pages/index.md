<Dropdown name=date_picker defaultValue='2021-01-08'>
    <DropdownOption value='2021-01-01'/>
    <DropdownOption value='2021-01-02'/>
    <DropdownOption value='2021-01-03'/>
    <DropdownOption value='2021-01-04'/>
    <DropdownOption value='2021-01-05'/>
    <DropdownOption value='2021-01-06'/>
    <DropdownOption value='2021-01-07'/>
    <DropdownOption value='2021-01-08'/>
    <DropdownOption value='2021-01-09'/>
    <DropdownOption value='2021-01-10'/>
</Dropdown>




```sql dates
select 
'${inputs.date_picker.value}' as start
```

<DataTable data={dates}/>

```sql orders_per_day
select 
date_trunc('day', order_datetime) as date,
count(*) as orders
from orders
where order_datetime > '${inputs.date_picker.value}'
group by 1
```

<LineChart
    data={orders_per_day}
    x=date
    y=orders
/>

