Here's a comprehensive set of examples for each method in the `Prop2` class:

### 1. `IS`
```python
# Check if a specific value exists in the 'users' table
exists = prop2_instance.IS("users", "email", "user@example.com")
print("Record exists:", exists)
```

### 2. `fetchall`
```python
# Fetch all records from the 'products' table where 'category' is 'Electronics'
records = prop2_instance.fetchall("products", category="Electronics")
for record in records:
    print(record)
```

### 3. `fetchall_with`
```python
# Fetch specific columns with sorting and filtering from the 'employees' table
options = {
    "columns": ["id", "name", "position"],
    "order_by": "name ASC",
    "limit": 5
}
records = prop2_instance.fetchall_with("employees", options=options, department="HR")
for record in records:
    print(record)
```

### 4. `count`
```python
# Count the number of 'Active' users in the 'users' table
user_count = prop2_instance.count("users", status="Active")
print("Active users count:", user_count)
```

### 5. `insert`
```python
# Insert a new record into the 'orders' table
order_id = prop2_instance.insert("orders", customer_id=123, amount=250.75, status="Pending")
print("Inserted Order ID:", order_id)
```

### 6. `delete`
```python
# Delete records from the 'logs' table where 'created_at' is older than a specific date
prop2_instance.delete("logs", "created_at < '2023-01-01'")
print("Old logs deleted.")
```

### 7. `update`
```python
# Update the status of a record in the 'tasks' table
success = prop2_instance.update("tasks", {"status": "Completed"}, "id=5")
print("Update successful:", success)
```

### 8. `databases`
```python
# Retrieve a list of all databases
databases = prop2_instance.databases()
print("Databases:", databases)
```

### 9. `mysql_users`
```python
# Retrieve a list of MySQL users
users = prop2_instance.mysql_users()
print("MySQL Users:", users)
```

### 10. `query`
```python
# Execute a custom query on the 'inventory' table
result = prop2_instance.query("inventory", "stock > 50", "category='Books'")
print("Query result:", result)
```

### 11. `queryData`
```python
# Execute a custom query and fetch matching records from the 'sales' table
sales_data = prop2_instance.queryData("sales", "amount > 100", "region='North'")
for sale in sales_data:
    print(sale)
```

### 12. `countData`
```python
# Count the number of records in the 'feedback' table matching certain criteria
feedback_count = prop2_instance.countData("feedback", "rating > 4", "status='Reviewed'")
print("High-rated feedback count:", feedback_count)
```

### 13. `fromData`
```python
# Fetch records from the 'students' table based on a simple condition
students = prop2_instance.fromData("students", "grade", "A")
for student in students:
    print(student)
```

Here are multiple examples demonstrating different use cases for the `fetchall_with` method:

### Example 1: Basic Filtering
```python
# Fetch records from 'products' table where 'category' is 'Electronics'
records = prop2_instance.fetchall_with("products", category="Electronics")
for record in records:
    print(record)
```

### Example 2: Custom Column Selection
```python
# Fetch only the 'id' and 'name' columns from the 'employees' table
options = {"columns": ["id", "name"]}
records = prop2_instance.fetchall_with("employees", options=options)
for record in records:
    print(record)
```

### Example 3: Sorting Results
```python
# Fetch all records from 'orders' table, ordered by 'created_at' in descending order
options = {"order_by": "created_at DESC"}
records = prop2_instance.fetchall_with("orders", options=options)
for record in records:
    print(record)
```

### Example 4: Limiting Number of Results
```python
# Fetch top 10 records from 'sales' table where 'amount' is greater than 100
options = {"limit": 10}
records = prop2_instance.fetchall_with("sales", options=options, amount=">100")
for record in records:
    print(record)
```

### Example 5: Combined Filtering and Sorting
```python
# Fetch records from 'customers' table where 'region' is 'North' and order by 'last_purchase'
options = {"columns": ["id", "name", "last_purchase"], "order_by": "last_purchase DESC"}
records = prop2_instance.fetchall_with("customers", options=options, region="North")
for record in records:
    print(record)
```

### Example 6: Advanced Filtering with Multiple Conditions
```python
# Fetch records from 'transactions' table where 'status' is 'Completed' and 'amount' > 1000
records = prop2_instance.fetchall_with("transactions", status="Completed", amount=">1000")
for record in records:
    print(record)
```

### Example 7: Using `LIKE` for Pattern Matching
```python
# Fetch records from 'users' table where 'email' contains 'example.com'
records = prop2_instance.fetchall_with("users", email="LIKE %example.com%")
for record in records:
    print(record)
```

### Example 8: Using `IN` for Multiple Values
```python
# Fetch records from 'inventory' table where 'category' is either 'Books' or 'Electronics'
records = prop2_instance.fetchall_with("inventory", category="IN ('Books', 'Electronics')")
for record in records:
    print(record)
```

These examples illustrate how versatile the `fetchall_with` method is for fetching data with various combinations of filtering, sorting, and limiting options.
