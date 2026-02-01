# workflow-orchestration

## Workflow orquestration

### Question 1 - What is the uncompressed file size of file yellow_tripdata_2020-12.csv

```
It's 134.5 MB
```

Equivalent to

```
128.2692 MiB
```

### Question 2 - What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?

Based on
```
file: "{{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv" 
```

The value is 
```
green_tripdata_2020-04.csv
```

### Question 3 - How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?

```sql
SELECT
  count(1)
FROM
  `kestra-sandbox-486105.zoomcamp.yellow_tripdata` yt
WHERE 
  yt.filename like '%2020%'
```

```
24648499
```

### Question 4 - How many rows are there for the Green Taxi data for all CSV files in the year 2020?

```sql
SELECT
  count(1)
FROM
  `kestra-sandbox-486105.zoomcamp.green_tripdata` gt
WHERE 
  gt.filename like '%2020%'
```

```
1734051
```

### Question 5 - How many rows are there for the Yellow Taxi data for the March 2021 CSV file?

```sql
SELECT
  count(1)
FROM
  `kestra-sandbox-486105.zoomcamp.yellow_tripdata` yt
WHERE 
  yt.filename = 'yellow_tripdata_2021-03.csv'
```

```
1925152
```

### Question 6 - How would to configure the timezone to New York in a Schedule trigger?

In both here
```
triggers:
- id: green_schedule
type: io.kestra.plugin.core.trigger.Schedule
cron: "0 9 1 * *"
inputs:
    taxi: green

- id: yellow_schedule
type: io.kestra.plugin.core.trigger.Schedule
cron: "0 10 1 * *"
inputs:
    taxi: yellow
```

it should be added a new parameter

```
timezone: America/New_York
```