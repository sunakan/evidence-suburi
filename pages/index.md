---
title: Evidenceの素振り
---

<Details title='ページの更新方法'>

- このページはプロジェクト内の `/pages/index.md` にある。
- マークダウンファイルに変更を加えて保存すると、ブラウザ上で変更が反映される。

</Details>

ソースとして `sources/needful_things/` を読み込んでいる

<Details title="tree sources/needful_things の結果">

```markdown
sources/needful_things
├── connection.yaml
├── needful_things.duckdb
└── orders.sql
```

</Details>


↓はneedful_things.ordersのカテゴリをgroup byしたSQL(SQLを記載すると、結果まで載せてくれる👍)

```sql categories
  select
      category
  from needful_things.orders
  group by category
```

<Dropdown data={categories} name=category value=category>
    <DropdownOption value="%" valueLabel="全てのcategory"/>
</Dropdown>

<Dropdown name=year>
    <DropdownOption value=% valueLabel="全ての年"/>
    <DropdownOption value=2019/>
    <DropdownOption value=2020/>
    <DropdownOption value=2021/>
</Dropdown>

sqlで `${inputs.〇〇.value}` を利用すると、↓のSQLの内容を動的にできる(結果も即時反映されるし超便利👍)

```sql orders_by_category
  select 
      date_trunc('month', order_datetime) as month,
      sum(sales) as sales_usd,
      category
  from needful_things.orders
  where category like '${inputs.category.value}'
  and date_part('year', order_datetime) like '${inputs.year.value}'
  group by all
  order by sales_usd desc
```

`BarChartタグ` で、棒グラフも表示可能(data=〇〇で、ソースを指定する(この例ではorders_by_categoryを指定してる))

<BarChart
    data={orders_by_category}
    title="月毎のセールス, {inputs.category.label}"
    x=month
    y=sales_usd
    series=category
/>
