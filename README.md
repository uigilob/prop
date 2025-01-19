# Prop2 Class Documentation

The `Prop2` class provides a set of methods to interact with a MySQL database. These methods allow for querying, inserting, updating, and deleting data, as well as fetching metadata about the database. Below is the detailed documentation for each method in the `Prop2` class.

## Methods

### `IS(self, table, w, find)`

Checks if a record exists in the specified table based on a single condition.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `w` (str): The column name to check.
  - `find` (str): The value to match in the column.

- **Returns:**
  - `True` if a matching record is found, `False` otherwise.

- **Example:**
  ```python
  result = _pro.IS("users", "username", "'john_doe'")
  ```

### `fetchall(self, table, **conditions)`

Fetches all records from the specified table, optionally filtered by conditions.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `**conditions` (dict): Optional conditions to filter the results.

- **Returns:**
  - A list of dictionaries representing the fetched records.

- **Example:**
  ```python
  results = _pro.fetchall("ssh_keys", id=3)
  ```

### `fetchall_with(self, table, options=None, **conditions)`

Fetches records from the specified table with advanced filtering and sorting options.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `options` (dict, optional): Additional options for filtering and sorting.
  - `**conditions` (dict): Conditions to filter the results.

- **Returns:**
  - A list of dictionaries representing the fetched records.

- **Example:**
  ```python
  results = _pro.fetchall_with("ssh_keys", options={"colms": "id,key"}, id=3)
  ```

### `count(self, table, **conditions)`

Counts the number of records in the specified table, optionally filtered by conditions.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `**conditions` (dict): Optional conditions to filter the results.

- **Returns:**
  - The count of matching records.

- **Example:**
  ```python
  count = _pro.count("ssh_keys", id=3)
  ```

### `insert(self, table, **kwargs)`

Inserts a new record into the specified table.

- **Parameters:**
  - `table` (str): The name of the table to insert into.
  - `**kwargs` (dict): Column-value pairs to insert.

- **Returns:**
  - The ID of the inserted record.

- **Example:**
  ```python
  new_id = _pro.insert("ftp", username="demo2", password="hello")
  ```

### `delete(self, table, where_condition)`

Deletes records from the specified table based on a condition.

- **Parameters:**
  - `table` (str): The name of the table to delete from.
  - `where_condition` (str): The condition to match for deletion.

- **Returns:**
  - `True` if the deletion was successful.

- **Example:**
  ```python
  result = _pro.delete("ftp", "id = 1 AND password = 'pun'")
  ```

### `update(self, table, update_data, where_condition=None)`

Updates records in the specified table based on a condition.

- **Parameters:**
  - `table` (str): The name of the table to update.
  - `update_data` (dict): Column-value pairs to update.
  - `where_condition` (str, optional): The condition to match for updating.

- **Returns:**
  - `True` if the update was successful.

- **Example:**
  ```python
  result = _pro.update("ftp", {"username": "ilike"}, "id = 1")
  ```

### `databases(self)`

Fetches a list of all databases.

- **Returns:**
  - A list of database names.

- **Example:**
  ```python
  databases = _pro.databases()
  ```

### `mysql_users(self)`

Fetches a list of all MySQL users.

- **Returns:**
  - A list of user names.

- **Example:**
  ```python
  users = _pro.mysql_users()
  ```

### `query(self, table, *arg)`

Executes a query to check if a record exists based on multiple conditions.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `*arg` (tuple): Conditions to filter the results.

- **Returns:**
  - `True` if a matching record is found, `False` otherwise.

- **Example:**
  ```python
  result = _pro.query("emails", "email", "'rahul@gmail.com'", "otp", "123456")
  ```

### `queryData(self, table, *arg)`

Executes a query to fetch records based on multiple conditions.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `*arg` (tuple): Conditions to filter the results.

- **Returns:**
  - A list of dictionaries representing the fetched records.

- **Example:**
  ```python
  results = _pro.queryData("emails", "email", "'rahul@gmail.com'", "otp", "123456")
  ```

### `countData(self, table, *arg)`

Counts the number of records in the specified table based on multiple conditions.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `*arg` (tuple): Conditions to filter the results.

- **Returns:**
  - The count of matching records.

- **Example:**
  ```python
  count = _pro.countData("emails", "email", "'rahul@gmail.com'", "otp", "123456")
  ```

### `fromData(self, table, w, find)`

Fetches records from the specified table based on a single condition.

- **Parameters:**
  - `table` (str): The name of the table to query.
  - `w` (str): The column name to check.
  - `find` (str): The value to match in the column.

- **Returns:**
  - A list of dictionaries representing the fetched records.

- **Example:**
  ```python
  results = _pro.fromData("users", "username", "'john_doe'")
  ```

## Usage

To use the `Prop2` class, create an instance of the class and call the desired methods with the appropriate parameters.

```python
_pro = Prop2()
```

This documentation provides a comprehensive overview of the `Prop2` class and its methods, enabling users to interact with a MySQL database efficiently.


Certainly! Below are examples of how to use the `fetchall_with` method in the `Prop2` class with various options and conditions.

### Example 1: Basic Usage

Fetch all columns from the `users` table where `id` is 1.

```python
results = _pro.fetchall_with("users", id=1)
```

### Example 2: Selecting Specific Columns

Fetch only the `id` and `username` columns from the `users` table where `id` is 1.

```python
results = _pro.fetchall_with("users", options={"colms": "id,username"}, id=1)
```

### Example 3: Excluding Specific Columns

Fetch all columns except `password` from the `users` table where `id` is 1.

```python
results = _pro.fetchall_with("users", options={"not_colms": "password"}, id=1)
```

### Example 4: Using `BETWEEN` Condition

Fetch records from the `orders` table where the `order_date` is between '2023-01-01' and '2023-12-31'.

```python
results = _pro.fetchall_with("orders", order_date=('between', '2023-01-01', '2023-12-31'))
```

### Example 5: Using `IN` Condition

Fetch records from the `users` table where the `id` is in the list [1, 2, 3].

```python
results = _pro.fetchall_with("users", id=('in', [1, 2, 3]))
```

### Example 6: Using `NOT IN` Condition

Fetch records from the `users` table where the `id` is not in the list [1, 2, 3].

```python
results = _pro.fetchall_with("users", id=('not_in', [1, 2, 3]))
```

### Example 7: Using `GREATER THAN` Condition

Fetch records from the `orders` table where the `total_amount` is greater than 100.

```python
results = _pro.fetchall_with("orders", total_amount=('greater_than', 100))
```

### Example 8: Using `LESS THAN` Condition

Fetch records from the `orders` table where the `total_amount` is less than 50.

```python
results = _pro.fetchall_with("orders", total_amount=('less_than', 50))
```

### Example 9: Using `LIKE` Condition

Fetch records from the `users` table where the `username` contains 'john'.

```python
results = _pro.fetchall_with("users", username=('like', 'john'))
```

### Example 10: Using `REGEXP` Condition

Fetch records from the `users` table where the `email` matches a regular expression pattern.

```python
results = _pro.fetchall_with("users", email=('regex', '^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$'))
```

### Example 11: Using `MATCH` Condition

Fetch records from the `articles` table where the `title` or `content` matches the term 'python'.

```python
results = _pro.fetchall_with("articles", options={"match": ["title", "content"], "match_terms": "python"})
```

### Example 12: Sorting Results

Fetch records from the `users` table and sort them by `username` in ascending order.

```python
results = _pro.fetchall_with("users", options={"sort_by": "username", "order": "ASC"})
```

### Example 13: Sorting Results with Multiple Columns

Fetch records from the `orders` table and sort them by `order_date` in descending order and then by `total_amount` in ascending order.

```python
results = _pro.fetchall_with("orders", options={"sort_by": ["order_date", "total_amount"], "order": ["DESC", "ASC"]})
```

### Example 14: Limiting Results

Fetch the first 10 records from the `users` table.

```python
results = _pro.fetchall_with("users", options={"limit": 10})
```

### Example 15: Using Offset

Fetch records from the `users` table starting from the 11th record.

```python
results = _pro.fetchall_with("users", options={"offset": 10})
```

### Example 16: Combining Multiple Options

Fetch records from the `orders` table where the `total_amount` is greater than 100, sort them by `order_date` in descending order, and limit the results to 5.

```python
results = _pro.fetchall_with("orders", options={"sort_by": "order_date", "order": "DESC", "limit": 5}, total_amount=('greater_than', 100))
```

These examples demonstrate the versatility of the `fetchall_with` method, allowing you to perform complex queries with various conditions, sorting, and limiting options.
