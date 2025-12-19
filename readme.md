# PostgreSQL Learning Progress 📚

## **All Slide Links**

🔗 4.15 DBMS besics: https://drive.google.com/file/d/1FC31pHU_TKCTMF8ctfhnzrMC9bWYGryS/view 


🔗 4.15 Annomalies, normalization & dependency: https://drive.google.com/file/d/1yjvJm6Vauk3-SvXil4qHUL9gdmijHy7i/view


🔗 4.17 postgres datatypes & management: https://drive.google.com/file/d/1zPLUb2mSC4w2cT7YIV8jGYi5RWK__-q-/view

### **1. Data Types** ✅
#### **Most Used:**
- **Boolean**: `true`, `false`, `null` (when field is empty)
- **Numbers**:
  - `SMALLINT` (2 bytes, -32768 to +32767)
  - `INTEGER` (4 bytes, -2B to +2B)
  - `BIGINT` (8 bytes, -9Q to +9Q)
  - `REAL` (4 bytes, ~6 decimal precision)
  - `DOUBLE PRECISION` (8 bytes, ~15 decimal precision)
  - `NUMERIC/DECIMAL` (variable, exact precision, e.g., `NUMERIC(10,2)`)
  - `SERIAL` (4 bytes, auto-increment 1 to 2.1B)
- **Character**:
  - `CHAR(n)` (fixed n length)
  - `VARCHAR(n)` (up to n characters)
  - `TEXT` (unlimited length)
- **Date/Time**:
  - `DATE` (various formats: '1980-12-20', '12-Dec-1980', etc.)
  - `TIME` ('14:30:00')
  - `TIMETZ` (time with timezone)
  - `TIMESTAMP` (date + time)
  - `TIMESTAMPTZ` (timestamp with timezone)
  - `INTERVAL` ('3 days 4 hours')
- **UUID** (Universally Unique Identifier)

#### **Rarely Used:**
- Binary, JSON, Array, XML

### **2. Database Operations** ✅
- **Create database**: `CREATE DATABASE school;`
- **Delete database**: `DROP DATABASE school;`

### **3. Table Operations** ✅
#### **Basic Table Creation:**
```sql
CREATE TABLE students (
    id SERIAL,
    name VARCHAR(50),
    age SMALLINT,
    isActive BOOLEAN,
    dob DATE
);
```

#### **Table Deletion:**
```sql
DROP TABLE IF EXISTS students;  -- Handles "table doesn't exist" error
```

### **4. Constraints** ✅
#### **Column-level constraints:**
```sql
CREATE TABLE students(
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    age SMALLINT CHECK (age >= 18),
    isActive VARCHAR(10) DEFAULT 'active'
);
```

#### **Table-level constraints:**
```sql
CREATE TABLE students(
    id SERIAL,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    age SMALLINT,
    isActive VARCHAR(10) DEFAULT 'active',
    PRIMARY KEY (id),
    UNIQUE(email, name),  -- Composite unique constraint
    CHECK (age >= 18)
);
```

#### **Constraint Types Learned:**
1. **NOT NULL** - Column must have a value
2. **UNIQUE** - Column values must be unique
3. **PRIMARY KEY** - Unique + NOT NULL (identifies each row)
4. **REFERENCES** - Foreign key constraint
5. **DEFAULT** - Sets default value if none provided
6. **CHECK** - Validates data against a condition

### **5. Inserting Data** ✅
#### **Single row insert (all fields):**
```sql
INSERT INTO students (id, name, email, age, isActive) 
VALUES (1, 'sajid', 'sajid4@gmail.com', 20, 'inactive');
```

#### **Multi-row insert:**
```sql
INSERT INTO students (name, email, age) 
VALUES 
    ('maruf', 'maruf@gmail.com', 20),
    ('maruf', 'maruf2@gmail.com', 20);
```

#### **Without column list (must follow table order):**
```sql
INSERT INTO students VALUES (10, 'tanvir', 'tanvir@gmail.com', 20, 'inactive');
```

#### **Best practice (auto-increment handled automatically):**
```sql
INSERT INTO students (name, email, age) 
VALUES ('ratul', 'ratul@gmail.com', 20);
```

---


*Last Updated: PostgreSQL Data Types, Table Creation & Constraints, Insert Operations*