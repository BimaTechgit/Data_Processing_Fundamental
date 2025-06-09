## Project Submission Dicoding - Data_Processing_Fundamental

- **Nama**        : Bimasakti Faturrahman Soetedjo, M.Sc, MBA, Ph.D
- **Email**       : riqjuniorbimasakti@gmail.com
- **DicodingID**  : Bimatech

#### **Deskripsi:**

Repositori ini dibuat sebagai bagian dari penyelesaian submission kelas Fundamental Pemrosesan Data. Aplikasi ini menjalankan proses ETL (Extract, Transform, Load) untuk mengolah data produk fashion dari situs Fashion Studio Dicoding, mencakup pengambilan data, pembersihan, dan penyimpanan ke beberapa tempat seperti CSV, Googlesheet dan Postgresql.

#### **Tautan Website yang digunakan:**
https://fashion-studio.dicoding.dev/


#### **Struktur file dan folder: **
```python
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
