```sql
--------------------------------------------TOXIC------------------------------------------------
SELECT pg_cancel_backend(0);

SELECT pg_terminate_backend(0);

SELECT pid from pg_catalog.pg_stat_activity
WHERE usename ='0'
AND state = 'active'
AND query NOT LIKE '%pg_catalog.pg_stat_activity%';
-------------------------------------------TOXIC------------------------------------------------
```
