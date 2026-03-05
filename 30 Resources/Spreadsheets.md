\*

- Google Sheets Query Function

- <https://www.benlcollins.com/spreadsheets/google-sheets-query-sql/>

:LOGBOOK: CLOCK: \[2022-01-06 Thu 23:17:32\]--\[2022-01-06 Thu 23:17:34\] => 00:00:02 :END:

- Index Match look up values

``` 
INDEX(ReturnValue; MATCH(LookupCell; ColumnToMatch; 0))
```

- `~` 

- Check for Unique values in data validation

``` 
=COUNTIF($C:$C,"="&C2) < 2 
- when used in conditional formatting wrapp it in Not 
=NOT(COUNTIF($C:$C,"="&C2) < 2)
```

- Remove the first Word

``` 
=RIGHT(C2,LEN(C2)-FIND(" ",C2))
```

\*

- INDEX(ReturnValues; MATCH(LookupCell; ColumnToMatch; 0)

- 2D lookups

- INDEX(ReturnValues, MATCH(LookupCell1, ColumnRangeToMatch, 0), MATCH(LookupCell2, RowRangeToMatch, 0 )

- Settings
