# Frontend — React + Vite

ขั้นตอนการสร้างโปรเจกต์นี้ตั้งแต่เริ่มต้น

## Prerequisites

- Node.js 18+

## Setup

**1. สร้างโปรเจกต์ React ด้วย Vite**

```cmd
npm create vite@latest
```

เลือก Framework: **React**, Variant: **JavaScript**

**2. เข้าไปที่โฟลเดอร์โปรเจกต์และติดตั้ง dependency พื้นฐาน**

```cmd
cd products
npm install
```

**3. ติดตั้ง Library เพิ่มเติมที่ใช้ในโปรเจกต์**

จัดการฟอร์ม:

```cmd
npm install react-hook-form
```

เรียก HTTP request ไปยัง backend:

```cmd
npm install axios
```

แสดง popup แจ้งเตือน:

```cmd
npm install sweetalert2
```

ไอคอนต่างๆ:

```cmd
npm install react-icons
```

การนำทางระหว่างหน้า (routing):

```cmd
npm install react-router-dom
```

**4. สร้างโครงสร้าง Component**

สร้างโฟลเดอร์ `src/Components/` แล้วสร้างไฟล์ต่างๆ:

<div align="center">

| ไฟล์ | หน้าที่ |
|---|---|
| `AppHeader.jsx` / `AppFooter.jsx` | ส่วนหัว-ท้ายเว็บ |
| `ProductList.jsx` | แสดงรายการสินค้า (ดึงจาก backend `/products/`) |
| `AddProduct.jsx` | ฟอร์มเพิ่มสินค้า |
| `EditProduct.jsx` | ฟอร์มแก้ไขสินค้า |
| `ImageUploader.jsx` / `ImageUploaderEdit.jsx` | อัปโหลดรูปสินค้า |

</div>

**5. ตั้งค่า Routing ใน `main.jsx` และ `App.jsx`**

ใช้ `BrowserRouter` ครอบ App ใน `main.jsx` แล้วกำหนดเส้นทางใน `App.jsx`:

- `/` → ProductList
- `/add` → AddProduct
- `/edit/:id` → EditProduct

**6. รันโปรเจกต์ตอนพัฒนา**

```cmd
npm run dev
```

⚠️ ต้องรัน backend คู่กันที่ `http://localhost:8000` ด้วย ไม่งั้นดึงข้อมูลสินค้าไม่ได้
