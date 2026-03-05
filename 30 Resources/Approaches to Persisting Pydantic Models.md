
To persist a [[Pydantic]] model, you generally need to take these approaches because Pydantic itself focuses on data validation and serialization but does not natively include a persistence layer:

1. Serialize the Pydantic Model:
   - Convert the model to a JSON string or dictionary using `.json()` or `.dict()` methods.
   - This serialization is the first step before saving the model data to a file, database, or any other store.

2. Save the Serialized Data:
   - Save the JSON or dictionary data to a persistent store such as a file (e.g., JSON file), a relational database (e.g., Postgres, [[Sqlite]]), or a NoSQL database.
   - For file persistence, you can simply write the JSON string to a disk file.
   - For databases, insert or update records after converting the Pydantic model data. This aligns with approaches in [[SQLModel]], which uses Pydantic models for database schemas.

3. Load and Recreate the Model:
   - To retrieve the model, read the serialized data from the persistent store.
   - Use the Pydantic model constructor with parsed data (`Model.parse_raw()` or `Model.parse_obj()`) to recreate the validated model instance.

More structured approaches with Pydantic-related libraries:

- Using pydantic-graph:
  - Implement state persistence by subclassing the abstract base class `BaseStatePersistence`.
  - You can use built-in persistence like `FileStatePersistence` for JSON file snapshots or implement your own to persist in databases.
  - This manages storage and retrieval of graph states and node snapshots, ideal for workflows or stateful processes.

- Using pydantic-factories:
  - Define sync or async persistence handlers conforming to `SyncPersistenceProtocol` or `AsyncPersistenceProtocol`.
  - Override save/save_many methods to implement your custom persistence logic for single or batch model saves.
  - This approach integrates persistence within factory methods for creating instances, useful for testing or data creation workflows. This could be relevant for projects like [[Sesame_Bento]], where Pydantic models are used alongside [[DuckDB]] for persistence.

Example for file-based persistence using pydantic-graph:

```python
from pathlib import Path
from pydantic_graph.persistence.file import FileStatePersistence

# Create file persistence for a run
persistence = FileStatePersistence(Path('model_state.json'))

# Save snapshots are automatically handled during graph execution

# Later load or iterate from the saved state
async with graph.iter_from_persistence(persistence) as run:
    node_or_end = await run.next()
```

Example for custom persistence handler in pydantic-factories:

```python
from pydantic_factories import ModelFactory, SyncPersistenceProtocol
from typing import TypeVar, List
from pydantic import BaseModel

T = TypeVar("T", bound=BaseModel)

class SyncPersistenceHandler(SyncPersistenceProtocol[T]):
    def save(self, data: T) -> T:
        # Custom logic to save data to a database or file
        return data

    def save_many(self, data: List[T]) -> List[T]):
        # Custom logic to save multiple instances
        return data

class MyModelFactory(ModelFactory):
    __sync_persistence__ = SyncPersistenceHandler
```

In summary, to persist a Pydantic model:
- Serialize the model to JSON or dict.
- Save the serialized data to your persistent storage (e.g., integrating with [[DuckDB]] or [[Polars]] as in [[How I like to build Python Apps]]).
- Recreate the model instance by parsing the stored data.
- Alternatively, use libraries like pydantic-graph or pydantic-factories that provide persistence interface implementations or protocols you can extend for custom persistence logic.

This keeps it alongside other Python notes like [[Pydantic]] and [[SQLModel]]. If you're using the manual curation protocol from [[restructure_notes_plan]], follow these steps:

If this relates to a specific project like [[Sesame_Bento]], consider linking it there too for cross-referencing. Let me know if you need further tweaks!

#### Sources:

[^1]: [[FastAPI]]
[^2]: [[restructure_notes_plan]]
[^3]: [[How I like to build Python Apps]]
[^4]: [[SQLModel]]
[^5]: [[Pydantic]]
[^6]: [[Sesame_Bento]]
[^7]: [[Final Vault Structure Plan]]
[^8]: [[restructure_solution_summary]]
[^9]: [[AGENTS]]
[^10]: [[2022-09-14]]
[^11]: [[2022-11-22]]
[^12]: [[Notes_Discussed_With_Jasper]]
[^13]: [[2022-11-16]]
[^14]: [[QWEN]]