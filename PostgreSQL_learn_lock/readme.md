lock

解 lock

查詢

https://dba.stackexchange.com/questions/58271/how-to-view-the-query-of-another-session-in-pg-stat-activity-without-being-super

pg_stat_active_allusers 給一般 user 查詢
```
CREATE FUNCTION get_sa() RETURNS SETOF pg_stat_activity AS
$$ SELECT * FROM pg_catalog.pg_stat_activity; $$
LANGUAGE sql
VOLATILE
SECURITY DEFINER;
CREATE VIEW pg_stat_activity_allusers AS SELECT * FROM get_sa();
GRANT SELECT ON pg_stat_activity_allusers TO public;
```
解 lock 程序
```
CREATE OR REPLACE FUNCTION public.pg_kill_connection(bigint)
 RETURNS boolean
 LANGUAGE sql
 SECURITY DEFINER NOT FENCED NOT SHIPPABLE
AS $function$select pg_terminate_backend($1);$function$;
```
