# aggregation

there are four types
- metrics
  - these are aggregation over a se of documents
  - single or multiple value result
  - filter documents and then calculate result for filtered set
- bucketing
  - logically group data

## metric

used for performing simple statistic calculation
  - sum
  - avg
  - count

### unbound

this query aggregates the age field across the entire data set for the index

```bash
/<index>/_search
{
  "size": 0,
  "aggs": {
    "avg_age": {
      "avg": {
        "field": "age"
      }
    }
  }
}
```

### bound

performs the aggregateion on the dataset that is bound by the query

```bash
/<index>/_search
{
  "size": 0,
  "query": {

  },
  "aggs": {
    "avg_age": {
      "avg": {
        "field": "age"
      }
    }
  }
}
```
