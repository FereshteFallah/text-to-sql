## 🎯 Main Goal:
The main goal is to create a **Text-to-SQL system** that can convert natural language questions (in English or Persian) into SQL queries and retrieve results from a real database.

---

## 🔄 Implementation Steps:

### 1️⃣ Create SQLite Database
We created a simple database called `students.db` with a table named `students`. This table includes the following information:

- `id`: Student ID  
- `name`: Student Name  
- `age`: Student Age  
- `grade`: Student Grade  

#### 📌 Why SQLite?
SQLite is lightweight and simple; it does not require a separate server installation and is perfect for prototyping.

---

### 2️⃣ Convert Question to SQL
The main idea of the project is that when the user asks a question, we convert that question into SQL. For example:

- **Question:** What is the age of Alice?  
- **Generated SQL Query:**  
    ```sql
    SELECT age FROM students WHERE name = 'Alice';
    ```

#### 📌 How does it work?
First, we analyze the keywords in the question:
- If the question includes `name` and `id`, it means we want to query the student's name by a specific ID.
- If it includes `age` and `of`, we are asking for the age of a specific student by name.
- If it includes `grade`, we are querying the student's grade.
- If the question is like "Show all students," the entire table is returned.

---

### 3️⃣ Process Question and Extract Parameters
To extract the necessary values from the question, we used `split` and `lower` methods.  
**Example:**
- **Question:** What is the age of Alice?  
    - We find the phrase `"of Alice"` and extract `"Alice"` as a parameter to send to SQL.  
- **Question:** What is the name of the student with ID 5?  
    - We extract the value `5` and send it to SQL.

---

### 4️⃣ Execute Query and Display Results
After generating the SQL query, it is executed on the SQLite database.

We use the `sqlite3` library to run the query and fetch the results.

---
