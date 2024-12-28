## 産業別 実在者賃金（情報通信業）


- [TOKYO OPEN DATA/組織/東京都産業労働局/中小企業の賃金・退職金事情(令和6年版)/第4表 産業別実在者賃金(情報通信業)](https://catalog.data.metro.tokyo.lg.jp/dataset/t000012d0000000067/resource/4500299e-2ee1-41fb-be55-26319fafd218)

```shell
duckdb db.duckdb "create table chingin as select * from 'r6chincho_4_04.csv';"
duckdb --csv db.duckdb "select * from chingin limit 3;"
```

```csv
"学歴・年齢区分","男性／集計人員数（人）","男性／平均勤続年数（年）","男性／７月の所定時間内賃金（円）","男性／令和5年年間給与支払額（円）","女性／集計人員数（人）","女性／平均勤続年数（年）","女性／７月の所定時間内賃金（円）","女性／令和5年年間給与支払額（円）"
"学歴計／～17歳",-,-,-,-,-,-,-,-
"学歴計／18～19歳",-,-,-,-,-,-,-,-
"学歴計／20～21歳",4,x,x,x,-,-,-,-
```

- CSV: 4.2KB
- db.duckdb: 524KB
