## Project Submission Dicoding - Data_Processing_Fundamental

- **Nama**        : Bimasakti Faturrahman Soetedjo, M.Sc, MBA, Ph.D
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
├── main.py                      # Main script for orchestrating data processing workflow
├── products.csv                 # Example CSV file containing product data
├── project-pemrosesan-data1-7480cae... # (Potentially a service account key file or similar; consider renaming for clarity if safe)
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


