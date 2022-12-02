---
title: "Sleigh Ride"
date: 2022-12-01T09:03:20-08:00
draft: false
description: The most popular song of ... the year
---

`Sleigh Ride` is _the_ quintessential Chistmas Song.  It's fun, upbeat, and you can jingle your car keys to it in this blatantly overdubbed "live" [show](https://youtu.be/sSazgH6CT7o) with Amy Grant. 

The Ronnettes kill it with plays and managing to cram a live, slightly terrified horse into a recording studio.  It's sweet, has great chord changes, and keeps those toes a tapping.  

{{< youtube YgJtnEEJf8I >}}

Johnny Mathis clips along at a slightly faster pace, and really hits those giddyups hard:

{{< youtube 6b9BKK27HuQ>}}

## Code

```sql
SELECT a.artist_name
	,a2.album_name
	,count(DISTINCT (p.play_ts)) AS play_count
FROM plays p
JOIN track t ON p.track_id = t.track_id
JOIN artist a ON p.artist_id = a.artist_id
JOIN album a2 ON p.album_id = a2.album_id
WHERE t.track_name = 'Sleigh Ride'
GROUP BY a.artist_name
	,a2.album_name
```

|artist_name|album_name|play_count|
|-----------|----------|----------:|
|The Ronettes|A Christmas Gift For You From Phil Spector|275|
|Johnny Mathis|Merry Christmas|233|
|The A-Strings|Home For Christmas|153|
|Amy Grant|A Christmas Album|142|
|Andy Williams|Merry Christmas|84|
|Boston Pops Orchestra|White Christmas - A Christmas Festival|40|
|Air Supply|The Christmas Album|39|
|Harry Connick, Jr.|When My Heart Finds Christmas|5|
|Ray Conniff|Christmas Carolling|5|
