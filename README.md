# pd5356-DATAB-2

**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #1**

    SELECT p.name, t.result, t.test_date
    FROM patients p
    INNER JOIN tests t
    ON p.patient_id = t.patient_id
    WHERE t.test_name = 'Blood Sugar'
    ORDER BY p.name ASC;

| name         | result | test_date  |
| ------------ | ------ | ---------- |
| Bob Johnson  | 120.0  | 2023-10-05 |
| Chris Taylor | 110.0  | 2023-10-09 |
| Emma Wilson  | 98.0   | 2023-10-07 |
| Emma Wilson  | 105.0  | 2023-10-14 |
| Jane Smith   | 95.0   | 2023-10-02 |
| John Doe     | 85.5   | 2023-10-01 |
| Sophia Davis | 92.0   | 2023-10-10 |

---
**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #2**

    SELECT AVG(t.result) AS avg_blood_sugar
    FROM tests t
    WHERE t.test_name = 'Blood Sugar';

| avg_blood_sugar |
| --------------- |
| 100.785714      |

---
**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #3**

    SELECT p.name, t.test_date
    FROM patients p
    INNER JOIN tests t
    ON p.patient_id = t.patient_id
    WHERE t.test_name = 'Cholesterol'
    AND t.result = (
        SELECT MAX(result)
        FROM tests
        WHERE test_name = 'Cholesterol'
    );

| name        | test_date  |
| ----------- | ---------- |
| Emma Wilson | 2023-10-06 |

---
**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #4**

    SELECT p.name, COUNT(t.test_id) AS total_tests
    FROM patients p
    INNER JOIN tests t
    ON p.patient_id = t.patient_id
    GROUP BY p.patient_id, p.name;

| name         | total_tests |
| ------------ | ----------- |
| John Doe     | 3           |
| Jane Smith   | 2           |
| Alice Brown  | 2           |
| Bob Johnson  | 1           |
| Emma Wilson  | 3           |
| Chris Taylor | 2           |
| Sophia Davis | 2           |

---
**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #5**

    SELECT 
        p.name,
        t.test_name,
        t.result,
        CASE
            WHEN t.test_name = 'Blood Sugar' AND t.result < 100 THEN 'Normalny'
            WHEN t.test_name = 'Blood Sugar' AND t.result >= 100 THEN 'Wysoki'
            WHEN t.test_name = 'Cholesterol' AND t.result < 200 THEN 'Normalny'
            WHEN t.test_name = 'Cholesterol' AND t.result >= 200 THEN 'Wysoki'
            ELSE 'Brak klasyfikacji'
        END AS result_status
    FROM patients p
    INNER JOIN tests t
    ON p.patient_id = t.patient_id;

| name         | test_name   | result | result_status     |
| ------------ | ----------- | ------ | ----------------- |
| John Doe     | Blood Sugar | 85.5   | Normalny          |
| John Doe     | Cholesterol | 200.0  | Wysoki            |
| John Doe     | Vitamin D   | 30.0   | Brak klasyfikacji |
| Jane Smith   | Blood Sugar | 95.0   | Normalny          |
| Jane Smith   | Cholesterol | 190.0  | Normalny          |
| Alice Brown  | Cholesterol | 180.0  | Normalny          |
| Alice Brown  | Vitamin D   | 28.0   | Brak klasyfikacji |
| Bob Johnson  | Blood Sugar | 120.0  | Wysoki            |
| Emma Wilson  | Cholesterol | 210.0  | Wysoki            |
| Emma Wilson  | Blood Sugar | 98.0   | Normalny          |
| Emma Wilson  | Blood Sugar | 105.0  | Wysoki            |
| Chris Taylor | Cholesterol | 190.0  | Normalny          |
| Chris Taylor | Blood Sugar | 110.0  | Wysoki            |
| Sophia Davis | Blood Sugar | 92.0   | Normalny          |
| Sophia Davis | Cholesterol | 170.0  | Normalny          |

---
**Schema (MySQL v5.7)**

    CREATE TABLE patients (
        patient_id INT PRIMARY KEY,
        name VARCHAR(255),
        age INT,
        gender CHAR(1)
    );
    
    INSERT INTO patients (patient_id, name, age, gender)
    VALUES
    (1, 'John Doe', 30, 'M'),
    (2, 'Jane Smith', 25, 'F'),
    (3, 'Alice Brown', 35, 'F'),
    (4, 'Bob Johnson', 40, 'M'),
    (5, 'Emma Wilson', 50, 'F'),
    (6, 'Chris Taylor', 45, 'M'),
    (7, 'Sophia Davis', 28, 'F');
    
    CREATE TABLE tests (
        test_id INT PRIMARY KEY,
        patient_id INT,
        test_name VARCHAR(255),
        result DECIMAL(6,2),
        test_date DATE,
        FOREIGN KEY (patient_id) REFERENCES patients(patient_id)
    );
    
    INSERT INTO tests (test_id, patient_id, test_name, result, test_date)
    VALUES
    (1, 1, 'Blood Sugar', 85.50, '2023-10-01'),
    (2, 1, 'Cholesterol', 200.00, '2023-10-03'),
    (3, 2, 'Blood Sugar', 95.00, '2023-10-02'),
    (4, 3, 'Cholesterol', 180.00, '2023-10-04'),
    (5, 4, 'Blood Sugar', 120.00, '2023-10-05'),
    (6, 5, 'Cholesterol', 210.00, '2023-10-06'),
    (7, 5, 'Blood Sugar', 98.00, '2023-10-07'),
    (8, 6, 'Cholesterol', 190.00, '2023-10-08'),
    (9, 6, 'Blood Sugar', 110.00, '2023-10-09'),
    (10, 7, 'Blood Sugar', 92.00, '2023-10-10'),
    (11, 7, 'Cholesterol', 170.00, '2023-10-11'),
    (12, 1, 'Vitamin D', 30.00, '2023-10-12'),
    (13, 3, 'Vitamin D', 28.00, '2023-10-13'),
    (14, 5, 'Blood Sugar', 105.00, '2023-10-14'),
    (15, 2, 'Cholesterol', 190.00, '2023-10-15');

---

**Query #6**

    SELECT p.name
    FROM patients p
    INNER JOIN tests t
    ON p.patient_id = t.patient_id
    WHERE t.test_name IN ('Blood Sugar', 'Vitamin D')
    GROUP BY p.patient_id, p.name
    HAVING COUNT(DISTINCT t.test_name) = 2;

| name     |
| -------- |
| John Doe |

---
