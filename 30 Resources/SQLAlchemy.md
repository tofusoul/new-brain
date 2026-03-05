- [Official Documentation](https://www.sqlalchemy.org/library.html)

- [sql alchemy todolist tutorial](https://hackernoon.com/building-a-to-do-list-app-with-python-data-access-layer-with-sqlalchemy)

- [The Architecture Article on SQL Alchemy](https://aosabook.org/en/sqlalchemy.html)

- [DuckDB SQLAlchemy Connection](https://pypi.org/project/duckdb-engine/)

- [Mapping to Dataclasses](https://docs.sqlalchemy.org/en/14/orm/dataclasses.html)

- Declarative Mapping with metadata

- #+BEGIN~SRC~ python

from [[future]] import annotations

from dataclasses import dataclass, field from typing import List

from sqlalchemy import Column, ForeignKey, Integer, String from sqlalchemy.orm import registry, relationship

mapper~registry~ = registry()

@mapper_registry.mapped @dataclass class User: [[tablename]] = \"user\"

[[sa~dataclassmetadatakey~]] = \"sa\" id: int = field(init=False, metadata=) name: str = field(default=None, metadata=) fullname: str = field(default=None, metadata=) nickname: str = field(default=None, metadata=) addresses: List\[Address\] = field( default~factory~=list, metadata= )

@mapper_registry.mapped @dataclass class Address: [[tablename]] = \"address\" [[sa~dataclassmetadatakey~]] = \"sa\" id: int = field(init=False, metadata=) user~id~: int = field(init=False, metadata=) email~address~: str = field(default=None, metadata=)

```
#+END_SRC
```
