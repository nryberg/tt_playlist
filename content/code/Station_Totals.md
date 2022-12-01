---
title: "Station Totals Code"
date: 2022-11-28T06:27:23-06:00
draft: false
description: "Count the total number of plays overall"
---

```sql
SELECT 
station,
COUNT(DISTINCT(play_ts)) as play_count
FROM public.plays
GROUP BY station
ORDER BY COUNT(DISTINCT(play_ts)) DESC
```

|station    |play_count|
|-----------|----------:|
|kool108    |2015      |
|star1021   |1954      |
|litefm     |1914      |
|kost1035   |1906      |
|987theriver|1868      |
|957bigfm   |1864      |
|kg95       |1837      |
|magic107   |1766      |
