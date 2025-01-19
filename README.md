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

These examples demonstrate how to use each method in various scenarios, making it easy to interact with the database effectively.
