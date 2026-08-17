# Task 2: SQL Schema and Sensor Agent Support

I extended the pipeline so inference results can be stored in SQLite and queried through natural language.

## Key Work

- Added configurable SQL schema support.
- Stored image, sensor, and fused inference results in SQLite.
- Connected SQLCoder-based natural-language querying.
- Added support for sensor-related metadata in queryable outputs.

## Result

Users can ask natural-language questions about structured inference results, and the system can generate SQL queries over the configured SQLite schema.
