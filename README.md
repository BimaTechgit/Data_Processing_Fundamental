## Project Submission Dicoding - Data_Processing_Fundamental

- **Nama**        : Bimasakti Faturrahman Soetedjo
- **Email**       : riqjuniorbimasakti@gmail.com
- **DicodingID**  : Bimatech

### **Deskripsi:**

Repositori ini dibuat sebagai bagian dari penyelesaian submission kelas Fundamental Pemrosesan Data. Aplikasi ini menjalankan proses ETL (Extract, Transform, Load) untuk mengolah data produk fashion dari situs Fashion Studio Dicoding, mencakup pengambilan data, pembersihan, dan penyimpanan ke beberapa tempat seperti CSV, Googlesheet dan Postgresql.

### **Tautan Website yang digunakan:**
https://fashion-studio.dicoding.dev/


### **Struktur file dan folder:**
```python
htmlcov/
|   ├── .gitignore                   # Specifies intentionally untracked files to ignore by Git
|   ├── class_index.html             # HTML report file, likely showing coverage by class
|   ├── coverage_html_cb_497bf287.js # JavaScript file for interactive coverage reports
|   ├── favicon_32_cb_58284776.png   # Favicon for the HTML coverage reports
|   ├── function_index.html          # HTML report file, likely showing coverage by function
|   ├── index.html                   # Main HTML entry point for the code coverage report
|   ├── keybd_closed_cb_ce680311.png # Image file, possibly for keyboard shortcuts in the report
|   ├── status.json                  # JSON file containing status data for the coverage report
|   ├── style_cb_718ce007.css        # CSS stylesheet for the HTML coverage reports
|   ├── z_c810615cce0f7acb___init__py.html  # HTML coverage report for __init__.py
|   ├── z_c810615cce0f7acb_extract_py.html   # HTML coverage report for extract.py
|   ├── z_c810615cce0f7acb_load_gsheet_...  # HTML coverage report for load_gsheet.py (truncated name)
|   ├── z_c810615cce0f7acb_load_postgres... # HTML coverage report for load_postgres.py (truncated name)
|   ├── z_c810615cce0f7acb_load_py.html      # HTML coverage report for load.py
|   └── z_c810615cce0f7acb_transform_py.html # HTML coverage report for transform.py
├── tests/
│   ├── __pycache__/             # Cache folder for Python compiled bytecode
│   ├── test_extract.py          # Unit tests for data extraction functionalities
│   ├── test_load.py             # Unit tests for data loading functionalities
│   └── test_transform.py        # Unit tests for data transformation functionalities
├── utils/
│   ├── __pycache__/             # Cache folder for Python compiled bytecode
│   ├── __init__.py              # Initializes the utils directory as a Python package
│   ├── extract.py               # Module for data extraction operations
│   ├── load_gsheet.py           # Module for loading data from Google Sheets
│   ├── load_postgres.py         # Module for loading data into PostgreSQL database
│   ├── load.py                  # General module for data loading operations
│   ├── tempCodeRunnerFile.py    # Temporary file, often created by code runners/IDEs (can be ignored or removed)
│   └── transform.py             # Module for data transformation operations
├── .coverage                    # Coverage report file from code testing
├── .env                         # database credensial from lokal user  
├── main.py                      # Main script for orchestrating data processing workflow
├── products.csv                 # Example CSV file containing product data
├── project-pemrosesan-data1-7480caee9e37 # (Potentially a service account key file or similar; consider renaming for clarity if safe)
└── requirements.txt             # Lists all Python dependencies required for the project
```

### **Feature & Storage:**
- **Extract:** Mengambil data produk dari situs menggunakan requests dan BeautifulSoup.
- **Transform:** Membersihkan, manipulasi dan memformat data menggunakan pandas kedalam bentuk dataframe.
- Load: Menyimpan data hasil pada file **main.py** scraping ke dalam bentuk:
  - File CSV: (products.csv)
  - Google Sheets: https://docs.google.com/spreadsheets/d/1dUQtnSseh1j4xHRjNbPBAwfwAXN6N6I1RKLh6Q5Y9Sk/edit?usp=sharing
  - PostgreSQL Database:
 
## **Cara Menjalankan Proyek:**

### **Jalankan Proses ETL (Extract-Transform-load):**

```python
python main.py
```

### **Jalankan Unit Testing**
```python
python -m pytest tests
```

### **Jalankan Coverage Testing**

**Cara 1:**

```python
coverage run -m pytest tests 
```

**Cara 2:**
```python
pytest --cov=tests --cov-report=term-missing
```

**Cara 3: Via HTML**
- pastikan anda sudah menginstall live server (jika belum silahkan install live server pada enviroment VS Code terlebih dahulu)
- buka folder **htmlcov/** dan cari **index.html**
- klik kanan dan pilih **"Open with Live Server"**
- setelah itu anda akan diarahkan ke halaman web coverage dan bisa melihat hasil report dari fitur fitur yang ada dalam web

### **Jalankan Database Testing:**

kemudian pada kode ini:

```python
import os
import pandas as pd
from sqlalchemy import create_engine

def save_to_postgresql(data, db_name=None, user=None, password=None, host=None, port=None, table_name="fashion_products"):
    try:
        # Gunakan environment variable, kalau tidak ada pakai default
        db_name = db_name or os.getenv("DB_NAME", "fashion_dicoding")
        user = user or os.getenv("DB_USER", "bimatech")
        password = password or os.getenv("DB_PASS", "bimadev")
        host = host or os.getenv("DB_HOST", "localhost")
        port = port or int(os.getenv("DB_PORT", 5432))

        # Buat koneksi engine ke PostgreSQL
        engine = create_engine(f"postgresql://{user}:{password}@{host}:{port}/{db_name}")

        # Konversi ke DataFrame (jika belum)
        df = pd.DataFrame(data)

        # Simpan ke table (replace = hapus dulu jika sudah ada)
        df.to_sql(table_name, engine, if_exists="replace", index=False)

        print(f"[INFO] Data berhasil disimpan ke PostgreSQL table: {table_name} ({len(df)} baris)")
    except Exception as e:
        print(f"[ERROR] Gagal menyimpan ke PostgreSQL: {e}")
```

Secara default, database akan tersambung menggunakan credential berikut:

- DB_NAME: fashion_dicoding
- DB_USER: bimatech
- DB_PASS: bimadev
- DB_HOST: localhost
- DB_PORT: 5432

Agar program dapat terhubung dengan database PostgreSQL milik Anda, silakan ikuti langkah berikut:

### Opsi 1: Menggunakan File `.env` **(Sangat Disarankan)**
1. Buat file `.env` di root project.
2. Masukkan kredensial PostgreSQL Anda seperti berikut:
    ```
    DB_NAME=nama_database_anda
    DB_USER=username_postgres_anda
    DB_PASS=password_postgres_anda
    DB_HOST=localhost
    DB_PORT=5432
    ```
3. Jalankan program seperti biasa:
    ```bash
    python main.py
    ```
    
### Opsi 2: Menggunakan Environment Variable di Terminal
Jika tidak ingin menggunakan file `.env`, Anda dapat langsung memasukkan credential di terminal:
- **Git Bash  enviroment VS Code:**
    ```bash
    DB_NAME=nama_database DB_USER=username DB_PASS=password python main.py
    ```
- **PowerShell enviroment VS Code:**
    ```powershell
    $env:DB_NAME="nama_database"; $env:DB_USER="username"; $env:DB_PASS="password"; python main.py
    ```
- **CMD  enviroment VS Code:**
    ```cmd
    set DB_NAME=nama_database && set DB_USER=username && set DB_PASS=password && python main.py
    ```
 Anda bebas menggunakan database dengan konfigurasi Anda sendiri. Program ini tidak bergantung pada database lokal peserta.




