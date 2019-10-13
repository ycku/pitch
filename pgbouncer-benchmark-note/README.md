## PgBouncer
1. https://pgbouncer.github.io/
2. PostgreSQL 的 connection pool，在資料庫前面緩衝大量連線。
3. 確保只有能夠穩定執行的查詢數量在資料庫中。

## 範例情境
1. PostgreSQL port=5432, max_connection=100
2. PgBouncer port=6432, pool_size=1000
3. 資料庫可接受 500 個連線，以輪替的方式讓 100 個連線同時在資料庫中執行查詢。
4. Client端能感受到資料庫連線數量增加，建立連線速度變快；資料庫實際負載固定，有利於整體資源規劃。

## 實驗環境
1. PgBouncer 1.11.0
2. PostgreSQL 11.5
3. Ubuntu Server 18.04

## 測試指令 

```
$ pgbench -p 6432 -c 100 -j 100 pgbench
```

## 參考資訊
- [PgBouncer - lightweight connection pooler for PostgreSQL](https://pgbouncer.github.io/)
- [PGBOUNCER AUTHENTICATION MADE EASY](https://www.cybertec-postgresql.com/en/pgbouncer-authentication-made-easy/)
