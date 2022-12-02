---
title: "Track Code"
date: 2022-11-28T06:27:23-06:00
draft: false
description: "Plays by Track"
---

```sql
WITH titles
AS (
    select 
	t.track_name, 
	play_ts 
	FROM PUBLIC.plays p
	JOIN PUBLIC.track t ON p.track_id = t.track_id
	
	)
	,tots
AS (
	SELECT count(DISTINCT (play_ts)) AS count_plays
		,max(play_ts) AS last_play
		,track_name
	FROM titles
	GROUP BY track_name
	ORDER BY count_plays DESC
	)
SELECT *
FROM tots
WHERE count_plays > 1
ORDER BY count_plays desc 
```

|count_plays|last_play|track_name|
|-----------|---------|----------|
|154|2022-12-01T20:02:11|Run Run Rudolph|
|2|2022-11-26T13:36:09|Run To You|
|16|2022-12-01T02:57:10|Santa Baby|
|14|2022-11-30T01:56:18|Santa, Can’t You Hear Me|
|160|2022-12-01T13:45:19|Santa Claus Is Coming to Town|
|24|2022-11-30T14:54:18|Santa Claus Is Coming To Town|
|59|2022-12-01T07:21:19|Santa Claus Is Comin' to Town|
