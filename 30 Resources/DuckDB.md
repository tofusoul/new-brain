---
title: DuckDB
url:  https://duckdb.org/
---


- great [intro video](https://www.youtube.com/watch?v=cBWlTLTMwfQ) from one of the founders
- its ACID complient, which is a good way to deal with everything
- based on postgres flavour of [[SQL]]
- duckdb has an online service that is integrated to the db to called [Mother Duck](https://app.motherduck.com/)
    - Mother Duck is free for now but will be charged in the future for compute and storage
## From the Docs
- [DuckDB with Ibis](https://duckdb.org/docs/archive/0.9.2/guides/python/ibis) 
    - has a really nice interface, not sure how much added complexity it rings
- using duckdb with [[Polars]] - [DuckDB with Polars](https://duckdb.org/docs/archive/0.9.2/guides/python/polars)


## Python DuckDB Api

full [api reference](http://duckdb.org/docs/archive/0.9.2/api/python/reference/) at link

example of using named params in duckdb queries
```python
import duckdb

duckdb.execute("""
    SELECT
        $my_param,
        $other_param,
        $also_param
    """,
    {
        'my_param': 5,
        'other_param': 'DuckDB',
        'also_param': [42]
    }
).fetchall()
# [(5, 'DuckDB', [42])]
```

## Types
BIGINT
BIT
BOOLEAN
BLOB
DATE 
DOUBLE
DECIMAL
HUGEINT
INTEGER
INTERVAL
REAL
SMALLINT
TIME
TIMESTAMP
TIMESTAMPTZ
TINYINT
UBIGINT
UINTERGER
USMALLLINT
UTINYINT
UUID
VARCHAR

## Nested Composit Types
LIST
STRUCT
MAP
UNION

