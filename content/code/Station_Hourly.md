---
title: "Station Hourly Code"
date: 2022-11-28T06:27:23-06:00
draft: false
description: "Count the total number of plays by station and hour"
---

```sql
with raw as (select 
station , 
substring(p.play_ts, 1, 13) as hourly,
play_ts
from public.plays p 
where p.play_ts  like '2022%'
--and station = 'kool108'

order by p.play_ts 
)
select station, hourly, count(distinct(play_ts)) as play_count
from raw 
group by station , hourly
order by station, hourly
```

|station|hourly|play_count|
|-------|------|----------|
|kost1035|2022-11-22T21|6|
|kost1035|2022-11-22T22|9|
|kost1035|2022-11-22T23|3|
|kost1035|2022-11-23T00|10|
|kost1035|2022-11-23T01|12|
|kost1035|2022-11-23T02|10|
|kost1035|2022-11-23T03|8|
|kost1035|2022-11-23T04|12|
