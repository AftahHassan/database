# 📌 Base de Donnée - Manage Surf

## 🗄️ Création et configuration de la base de données

```sql
-- 1️⃣ Créer la base de données
CREATE DATABASE manage_surf;

-- 2️⃣ Utiliser la base de données
USE manage_surf;

-- 3️⃣ Création des tables

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100),
    password VARCHAR(255),
    role ENUM('admin','client'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    country VARCHAR(100),
    level ENUM('beginner','intermediate','advanced'),
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE lessons (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100),
    coach VARCHAR(100),
    description TEXT,
    price DECIMAL(10,2),
    level ENUM('beginner','intermediate','advanced'),
    date DATETIME
);

CREATE TABLE enrollments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    lesson_id INT,
    payment_status ENUM('paid','pending'),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (lesson_id) REFERENCES lessons(id)
);
