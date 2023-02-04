
回收 高水位 資料表

--查看高水位 table

`SELECT table_schema , table_name AS table_full_name, pg_size_pretty(pg_total_relation_size('"' || table_schema || '"."' || table_name || '"')) AS size`
`FROM information_schema.tables`
`where table_schema ='dsdemo'`
`and table_name ='psaa_t'`
`ORDER BY`
`pg_total_relation_size('"' || table_schema || '"."' || table_name || '"') desc`

--收縮 vacuum 語法

`SELECT 'VACUUM '||n.nspname||'.'||t.relname||';'`
`FROM pg_class t`
`JOIN pg_namespace n ON n.oid = t.relnamespace`
`WHERE t.relkind = 'r' and n.nspname in ('dsdemo','dsdata')`
`and t.relname like 'psaa%'`
`order by n.nspname,t.relname;`
