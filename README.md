# ProductManagement

เว็บแอปพลิเคชันระบบจัดการสินค้า เป็น Mini project ในรายวิชา Software Innovation Development and Application (ปีการศึกษา 1/2567) พัฒนาด้วย React (Frontend) และ Django (Backend) เชื่อมต่อฐานข้อมูล MongoDB ผู้ใช้งานสามารถดู เพิ่ม แก้ไข และลบสินค้าได้ผ่านหน้าเว็บ

## โครงสร้างโปรเจกต์

```text
ProductManagement/
│
├── backend/   → Django REST API (เชื่อมต่อ MongoDB)
├── frontend/  → React (Vite)
├── .gitignore
└── README.md
```

## เทคโนโลยีที่ใช้

- **Frontend:** React, Vite, React Router DOM, Axios, SweetAlert2, React Icons, React Hook Form
- **Backend:** Django, Django REST Framework, django-cors-headers, pymongo
- **Database:** MongoDB

## สิ่งที่ต้องติดตั้งในเครื่องก่อน (Prerequisites)

- [Python](https://www.python.org/downloads/) 3.10+
- [Node.js](https://nodejs.org) 18+ (LTS)
- [MongoDB Community Server](https://www.mongodb.com/try/download/community)

## วิธี Clone และรันโปรเจกต์

### 1. Clone repo นี้

```cmd
git clone https://github.com/nantiwan47/ProductManagement.git
cd ProductManagement
```

### 2. เปิด MongoDB ให้ทำงานอยู่

ตรวจสอบว่า MongoDB รันอยู่ที่ `localhost:27017`

### 3. ติดตั้งและรัน Backend สำหรับ windows

```cmd
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Backend จะรันที่ `http://localhost:8000`

### 4. ติดตั้งและรัน Frontend (เปิด Terminal อีกหน้าต่างแยกกัน)

```cmd
cd frontend
npm install
npm run dev
```

Frontend จะรันที่ `http://localhost:5173`

### 5. เปิดเบราว์เซอร์

ไปที่ `http://localhost:5173`


รายละเอียดเพิ่มเติมของแต่ละส่วนสามารถดูได้ที่

- 📂  [`backend/README.md`](./backend/README.md)
- 📂  [`frontend/README.md`](./frontend/README.md)

เอกสารทั้งสองไฟล์อธิบายรายละเอียดการติดตั้ง โครงสร้างโปรเจกต์ และการพัฒนาในแต่ละฝั่ง
