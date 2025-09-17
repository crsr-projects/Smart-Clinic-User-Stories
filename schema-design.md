## MySQL Database Design

### Table: patients
- patient_id: INT, Primary Key, AUTO_INCREMENT  
- first_name: VARCHAR(50), NOT NULL  
- last_name: VARCHAR(50), NOT NULL  
- email: VARCHAR(100), UNIQUE, NOT NULL  
- phone: VARCHAR(15), NOT NULL  
- date_of_birth: DATE, NULL  
- created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP  

### Table: doctors
- doctor_id: INT, Primary Key, AUTO_INCREMENT  
- first_name: VARCHAR(50), NOT NULL  
- last_name: VARCHAR(50), NOT NULL  
- specialization: VARCHAR(100), NOT NULL  
- email: VARCHAR(100), UNIQUE, NOT NULL  
- phone: VARCHAR(15), NOT NULL  
- created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP  

### Table: appointments
- appointment_id: INT, Primary Key, AUTO_INCREMENT  
- patient_id: INT, Foreign Key → patients(patient_id)  
- doctor_id: INT, Foreign Key → doctors(doctor_id)  
- appointment_time: DATETIME, NOT NULL  
- status: TINYINT DEFAULT 0  -- 0=Scheduled, 1=Completed, 2=Cancelled  
- created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP  

### Table: admin
- admin_id: INT, Primary Key, AUTO_INCREMENT  
- username: VARCHAR(50), UNIQUE, NOT NULL  
- password_hash: VARCHAR(255), NOT NULL  
- role: ENUM('superadmin','staff') DEFAULT 'staff'  
- created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP  
