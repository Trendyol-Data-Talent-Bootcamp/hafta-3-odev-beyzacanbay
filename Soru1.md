# Soru1) ​ Beklenen dsmbootcamp.sample.semi_structured_hw tablosunu kullanarak dsmbootcamp.sample.semi_structured_hw_expected tablosundaki veriyi oluşturmaktır.

```sql
select name, car.id as car_id, car.model as car_model, manufacture.year as manufacture_year,
array(select as struct purchase.id, (timestamp_add(purchase.date, INTERVAL 3 hour)) as date from unnest(purchase) as purchase) as purchase
from `beyza_canbay.semi_structured_hw`
cross join unnest(car) as car
cross join unnest(manufacture) as manufacture 
on car.id = manufacture.id
```