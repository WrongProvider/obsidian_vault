SQLi

blind SQL

`CAST((SELECT example_column FROM example_table) AS int)` essa func muda o tipo do dado int para str ou outros

`TrackingId=' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--`