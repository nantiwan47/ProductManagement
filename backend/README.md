# Backend — Django + MongoDB

ขั้นตอนการสร้างโปรเจกต์นี้ตั้งแต่เริ่มต้น

---

## สิ่งที่ต้องมีก่อนเริ่ม

- Python 3.10+
- **MongoDB Community Server ติดตั้งแล้ว และต้องเปิดทำงานอยู่ตลอด** (รันที่ `localhost:27017`) — เช็คให้แน่ใจว่าเปิดอยู่ก่อนเริ่มขั้นตอนด้านล่าง โดยเฉพาะก่อนถึงขั้น 8

---

## ขั้นตอนการสร้างโปรเจกต์

### ขั้น 1 — สร้าง Virtual Environment

```cmd
python -m venv venv
venv\Scripts\activate
```
ผลลัพธ์: เห็น `(venv)` ขึ้นหน้า prompt

---

### ขั้น 2 — ติดตั้ง Django และสร้างโปรเจกต์

```cmd
pip install django
django-admin startproject ProjectSIDev .
```
ผลลัพธ์: ได้ไฟล์ `manage.py` และโฟลเดอร์ `ProjectSIDev/`

---

### ขั้น 3 — สร้าง App สำหรับจัดการสินค้า

```cmd
python manage.py startapp products
```
ผลลัพธ์: ได้โฟลเดอร์ `products/`

---

### ขั้น 4 — ติดตั้ง Package เสริม

```cmd
pip install pymongo djangorestframework django-cors-headers
```

| Package | ใช้ทำอะไร |
|---|---|
| `pymongo` | เชื่อมต่อ Django กับ MongoDB |
| `djangorestframework` | สร้าง REST API ให้ React เรียกใช้ |
| `django-cors-headers` | อนุญาตให้ React เรียก API ข้าม origin ได้ |

---

### ขั้น 5 — แก้ไขไฟล์ `ProjectSIDev/settings.py`

⚠️ ไม่มีคำสั่งพิมพ์ ต้องเปิดไฟล์แล้วแก้เอง 3 จุด:

**จุดที่ 1** เพิ่มใน `INSTALLED_APPS`:
```python
"rest_framework",
"corsheaders",
"products",
```

**จุดที่ 2** เพิ่มใน `MIDDLEWARE` (บรรทัดบนสุด):
```python
"corsheaders.middleware.CorsMiddleware",
```

**จุดที่ 3** เพิ่มบรรทัดใหม่ท้ายไฟล์:
```python
CORS_ALLOWED_ORIGINS = ["http://localhost:5173"]
```

---

### ขั้น 6 — สร้างไฟล์ `db_connection.py`

database ชื่อ `projectSIDev` collection ชื่อ `products`

---

### ขั้น 7 — เขียน views.py และ urls.py ในโฟลเดอร์ products

เขียนโค้ดเองเพื่อกำหนด endpoint `/products/` รองรับ create, list, retrieve, update, delete

---

### ขั้น 8 — ตรวจ MongoDB แล้วรันเซิร์ฟเวอร์

**ก่อนรันคำสั่งนี้ ต้องเปิด MongoDB ให้ทำงานอยู่ก่อนเสมอ** ไม่งั้น backend จะเชื่อมต่อฐานข้อมูลไม่ได้

```cmd
python manage.py migrate
python manage.py runserver
```
ผลลัพธ์: เปิด `http://localhost:8000/products/` แล้วเห็นข้อมูล JSON (หรือ `[]` ถ้ายังไม่มีสินค้า)

---

### ขั้น 9 — บันทึกรายการ dependency ทั้งหมด

```cmd
pip freeze > requirements.txt
```
ผลลัพธ์: ได้ไฟล์ `requirements.txt` ไว้ให้คนอื่น `pip install -r requirements.txt` ตอน clone แทนที่จะทำขั้น 1–8 ใหม่ทั้งหมด

---

## ดูข้อมูลด้วย MongoDB Compass

ส่วนนี้**ไม่ใช่ขั้นตอนที่ต้องทำ** เป็นแค่โปรแกรมช่วยดูข้อมูลใน MongoDB แบบเห็นภาพ (GUI) แทนการดูผ่านโค้ด 

### ติดตั้งและเชื่อมต่อ

1. ดาวน์โหลดที่ [mongodb.com/try/download/compass](https://www.mongodb.com/try/download/compass)
2. เปิด Compass → กด **New Connection**
3. ช่อง **URI** : `mongodb://localhost:27017`
4. ช่อง **Name** : ใส่ชื่ออะไรก็ได้ (ไม่มีผลต่อการเชื่อมต่อ)
5. กด **Save & Connect**

### ดูข้อมูลสินค้า

หลังเชื่อมต่อสำเร็จ มองหา database ชื่อ **`projectSIDev`** และ collection ชื่อ **`products`**

> ไม่ต้องสร้างเองก็ได้ — MongoDB จะสร้างให้อัตโนมัติทันทีที่มีการเพิ่มสินค้าครั้งแรกผ่านหน้าเว็บ ถ้ายังไม่เคยเพิ่มสินค้า จะยังไม่เห็น database นี้ เป็นเรื่องปกติ

### (ถ้าอยากสร้างล่วงหน้าเอง)

1. คลิก **Create Database**
2. **Database Name:** `projectSIDev`
3. **Collection Name:** `products`
4. ปล่อย Time-Series และ Additional preferences ว่างไว้
5. กด **Create Database**

⚠️ ต้องสะกดตรงตัวพิมพ์ใหญ่-เล็ก (`projectSIDev` ไม่ใช่ `projectsidev`) ไม่งั้น backend จะเขียนข้อมูลไปคนละ database

---