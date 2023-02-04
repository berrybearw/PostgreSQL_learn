lock

解 lock

查詢

https://dba.stackexchange.com/questions/58271/how-to-view-the-query-of-another-session-in-pg-stat-activity-without-being-super

```
CREATE FUNCTION get_sa() RETURNS SETOF pg_stat_activity AS
$$ SELECT * FROM pg_catalog.pg_stat_activity; $$
LANGUAGE sql
VOLATILE
SECURITY DEFINER;
CREATE VIEW pg_stat_activity_allusers AS SELECT * FROM get_sa();
GRANT SELECT ON pg_stat_activity_allusers TO public;
```
