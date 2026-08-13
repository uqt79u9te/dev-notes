# Airflow DAG Retry Notes

- Default retries: 3, retry_delay: 5 min
- For external API calls, use exponential backoff (multiplier=2)
- Set `retry_exponential_backoff=True` in task defaults
- Avoid retrying on permanent failures — catch and fail fast
- Use `trigger_rule='all_failed'` only when necessary

Example:
```python
default_args = {
    'retries': 3,
    'retry_delay': timedelta(minutes=5),
    'retry_exponential_backoff': True,
}
```