```sql
-----------------------Удаление дубликатов----------------------------
delete from scheme.table t1
where concat(ctid, gp_segment_id) in (
select ctid from
(SELECT
concat(ctid, gp_segment_id) as ctid,
row_number() over(partition by tt.
) as n
FROM scheme.table tt) t
where n > 1);
------------------------Удаление дубликатов----------------------------
```