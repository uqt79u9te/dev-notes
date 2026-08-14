# Airflow DAG Pitfalls

- **Don't put `@dag` decorator on a function that returns a task group** — it silently breaks scheduling.
- **Use `catchup=False`** unless you really want backfill on a schedule change.
- **`retries` on the DAG level vs task level** — task level overrides.
- **Sensor timeouts**: always set `timeout` and `poke_interval`, otherwise stuck tasks.
- **`execution_date` is deprecated** — use `logical_date` in Airflow 2.4+.
- **Test DAGs with `dag.test()`** locally before pushing to prod.

Source: personal experience, Aug 2026.