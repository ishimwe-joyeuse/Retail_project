# 🧠 VENDOR PERFORMANCE ANALYSIS PROJECT  
**Sector:** Retail  

---

## 📌 Project Overview  
This project evaluates vendor performance based on key procurement metrics such as delivery quality, order quantity, and return rates. A clustering model is used to categorize vendors, and final insights are visualized in Power BI dashboards.

---

## ❗ Problem Statement  
The project aims to identify and address inefficiencies in vendor performance using data analysis to support better decision-making.

---

## 🔄 Project Workflow  
![Project Workflow]<img width="1246" height="806" alt="image" src="https://github.com/user-attachments/assets/3aa546e4-cb8a-4bb8-9f46-f3eb2c0065e5" />


---

## 🧰 Tools & Technologies  
- **Python** (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)  
- **MySQL** (Data storage via XAMPP)  
- **Power BI** (Dashboard visualization)  
- **Jupyter Notebook (VSCode)**  
- **GitHub** (Project hosting & submission)  

---

## 🗃️ Database Schema & SQL Tables  

### ✅ Database Creation in XAMPP 

![Database Screenshot]<img width="1360" height="669" alt="database" src="https://github.com/user-attachments/assets/11a0e6ad-69ae-4a4c-b71f-66d68a1dfd3b" />

📃 Database Schema

```sql
CREATE TABLE vendors (
 vendor_id INT PRIMARY KEY,
 name VARCHAR(100),
 category VARCHAR(50),
 country VARCHAR(50)
);

CREATE TABLE orders (
 order_id INT PRIMARY KEY,
 vendor_id INT,
 product_id INT,
 order_date DATE,
 quantity INT,
 expected_delivery DATE,
 FOREIGN KEY (vendor_id) REFERENCES vendors(vendor_id)
);

CREATE TABLE deliveries (
 delivery_id INT PRIMARY KEY,
 order_id INT,
 delivery_date DATE,
 quality_score INT CHECK (quality_score BETWEEN 1 AND 10),
 FOREIGN KEY (order_id) REFERENCES orders(order_id)
);

CREATE TABLE returns (
 return_id INT PRIMARY KEY,
 order_id INT,
 return_reason TEXT,
 return_date DATE,
 FOREIGN KEY (order_id) REFERENCES orders(order_id)
);

```
<img width="1342" height="669" alt="tables" src="https://github.com/user-attachments/assets/f1d00f7c-2bd5-40f9-9008-d22a53f0a42e" />

```

2. 💾 Import CSVs into MySQL

**Step 1: Open phpMyAdmin or MySQL CLI**  
**Step 2: Run the SQL table creation scripts above**  
**Step 3: Import CSVs into corresponding tables using phpMyAdmin OR with a query like:**


LOAD DATA INFILE '/path/to/vendors.csv'
INTO TABLE vendors
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;

```

<img width="1341" height="681" alt="import" src="https://github.com/user-attachments/assets/0ccf8809-67e7-420e-a055-e15a4da375fa" />

---

3. 📊 Running the Analysis (Python)

1. Open `Vendors_analysis.ipynb` in **VSCode (Jupyter Notebook view)**
2. Ensure MySQL is running on port 3307
3. Install required libraries:
   
---   

```bash
pip install mysql-connector-python pandas matplotlib seaborn scikit-learn

```

---
4. Run all notebook cells to:
   - Load and clean data
   -  Exploratory Data Analysis (EDA) 
   - Perform clustering
   - Export cleaned files for Power BI

```



## 📈 Power BI Dashboard

- Load the `clustered_vendors.csv` and `vendors_cleaned.csv` into Power BI
- Create visuals such as:
  1.VENDOR QUALITY SCORE DISTRIBUTION
  
    1.1 <img width="1364" height="719" alt="screenshoot1" src="https://github.com/user-attachments/assets/4bf68cdc-3b81-4c30-8249-075e9cc40476" />   
  2. CLUSTERING INSHIGHT 
    2.1<img width="1357" height="717" alt="screenshoot2" src="https://github.com/user-attachments/assets/75841603-fd44-467b-be87-abd6100e474d" />
    2.2<img width="1365" height="717" alt="screenshoot2 1" src="https://github.com/user-attachments/assets/ae95e8b3-ba1a-47fb-ad1c-fedb7a248669" />
    2.3<img width="1353" height="695" alt="screenshoot2 2" src="https://github.com/user-attachments/assets/1cdf160e-2c45-43a1-ba80-a79bb8614eee" />
    2.4<img width="1364" height="720" alt="screenshoot2 3" src="https://github.com/user-attachments/assets/20cb96f5-e4cb-4348-905c-e143cf7407e7" />
    
  4. RETURNS ANALYSIS
    3.1<img width="1361" height="718" alt="screenshoot3" src="https://github.com/user-attachments/assets/de74b967-afe2-4bd0-bd77-4c798d77c193" />
    3.2<img width="1349" height="713" alt="screenshoot3 1" src="https://github.com/user-attachments/assets/43f074d2-45eb-4feb-b29e-ba1b4f049bfd" />
    3.3<img width="1343" height="696" alt="screenshoot3 2" src="https://github.com/user-attachments/assets/db91f13b-9a20-4838-89eb-9c0fbc0131ac" />


## ✅ Final Submission Checklist

- [x] GitHub repo with all folders and files
- [x] README.md file
- [x] Jupyter Notebook (`Vendors_analysis.ipynb`)
- [x] Power BI file (`clustered_dashboard.pbix`)


---

© 2025 Joyeuse Ishimwe | INSY 8413 Capstone

