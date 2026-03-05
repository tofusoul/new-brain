- [Great Tute](https://www.youtube.com/watch?v=CvQ7e6yUtnw) from Ajran Codes

- Nice talk from Bruce Eckles about [Using data classes as immutable types](https://www.youtube.com/watch?v=w77Kjs5dEko).

- nice dataclasses overview from TDS <https://towardsdatascience.com/9-reasons-why-you-should-start-using-python-dataclasses-98271adadc66>

- <https://stackoverflow.com/questions/47955263/what-are-data-classes-and-how-are-they-different-from-common-classes>

- Example from my code

``` python
@dataclass(kw_only=True, frozen=True)
class Collection:
    name: str
    id: str
    url: str
    client: Client = field(repr=False)

    @property
    def access(self) -> Spread:
        print(f"connecting to ")
        return Spread(self.name, client=self.client)

    @property
    def tables_access(self) -> list[Worksheet]:
        return self.access.sheets

    @property
    def table_names(self) -> list[str]:
        return [item.title for item in self.tables_access]

    @property
    def dfs(self) -> dict[pd.DataFrame]:
        dfs = 
        for i in self.table_names:
            self.access.open_sheet(i)
            dfs[i] = self.access.sheet_to_df()
            print(f"loaded dataframe ")
        return dfs


```

- Dataclass supports export to dictionary

- **[chris-b1](https://github.com/chris-b1) ** commented   [on 16 Jul 2018](https://github.com/pandas-dev/pandas/issues/21910#issuecomment-405109225)

The  `dataclasses`  module has  `is_dataclass`  and  `fields`  introspection functions, so that part shouldn\'t be an issue.That said I\'m not sure we should quickly commit to any specific API/support here. For now the the  `asdict`  helper from the dataclasses module can help with the ingest usecase.

``` python
In [18]: from dataclasses import asdict

In [19]: pd.DataFrame([asdict(x) for x in [dataclass_object1, dataclass_object2]])
Out[19]:
   field_a field_b
0        1       a
1        2       b
```

\*
