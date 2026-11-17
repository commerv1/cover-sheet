# ใบปะหน้าพัสดุ (PWA) — ฟรี ซิงก์ทุกเครื่อง

ใบปะหน้าขนาด A6 แนวนอน (148×105 มม.) ใช้ GitHub Pages (โฮสต์ฟรี) + Firebase (ฐานข้อมูลฟรี แผน Spark ไม่ต้องใส่บัตรเครดิต)

## ไฟล์ในโฟลเดอร์
index.html, sw.js, manifest.webmanifest, icon-192.png, icon-512.png, firebase-config.js, firestore.rules

## ขั้นตอน

### 1) สร้างโปรเจกต์ Firebase
1. ไปที่ https://console.firebase.google.com → Create a project (ปิด Google Analytics ได้)
2. หน้าโปรเจกต์ กดไอคอน `</>` (Web) → ตั้งชื่อแอป → Register app
3. คัดลอกค่า `firebaseConfig` ไปวางแทนในไฟล์ **firebase-config.js**

### 2) เปิดระบบล็อกอิน
Build → Authentication → Get started → Sign-in method → **Email/Password** → Enable
แท็บ Users → **Add user** ใส่อีเมลและรหัสผ่านของคุณ (ใช้ล็อกอินครั้งเดียวต่อเครื่อง)

### 3) สร้างฐานข้อมูล
Build → Firestore Database → Create database → เลือกที่ตั้ง `asia-southeast1` (สิงคโปร์) → Production mode
แท็บ **Rules** → วางเนื้อหาจากไฟล์ **firestore.rules** โดยเปลี่ยน `you@example.com` เป็นอีเมลในข้อ 2 → Publish
(กฎนี้ทำให้มีแค่บัญชีของคุณที่อ่าน/เขียนข้อมูลได้ ค่า apiKey ที่อยู่ในโค้ดเปิดเผยได้ ไม่เป็นความลับ)

### 4) ขึ้นเว็บฟรีด้วย GitHub Pages
1. สมัคร https://github.com → New repository (ตั้งชื่อ เช่น `label`, เลือก Public)
2. Add file → Upload files → อัปโหลด **ทุกไฟล์** (ยกเว้น firestore.rules และ README.md ไม่จำเป็นก็ได้) → Commit
3. Settings → Pages → Source: Deploy from a branch → Branch `main` / `(root)` → Save
4. รอ 1–2 นาที จะได้ลิงก์ `https://ชื่อผู้ใช้.github.io/label/`
(ทางเลือกอื่นที่ฟรีเช่นกัน: Cloudflare Pages, Netlify — ลากโฟลเดอร์ไปวางได้เลย)

### 5) ติดตั้งบนมือถือ
- **iPhone (Safari):** เปิดลิงก์ → ปุ่มแชร์ → เพิ่มลงหน้าจอโฮม
- **Android (Chrome):** เปิดลิงก์ → เมนู ⋮ → ติดตั้งแอป / เพิ่มลงหน้าจอหลัก
ล็อกอินด้วยอีเมลเดิมในแต่ละเครื่อง ข้อมูลจะซิงก์กัน และใช้ออฟไลน์ได้ (ซิงก์เมื่อกลับมามีเน็ต)

## หมายเหตุ
- ถ้าล็อกอินไม่ได้และขึ้นเรื่องโดเมน: Authentication → Settings → Authorized domains → เพิ่ม `ชื่อผู้ใช้.github.io`
- แก้ไฟล์แล้วอัปโหลดใหม่ แอปจะอัปเดตเมื่อเปิดครั้งถัดไป (อาจต้องเปิดสองครั้ง)
- ข้อมูลจากเวอร์ชันบน Claude ไม่ย้ายมาอัตโนมัติ
- ขนาดฟรีของ Firebase เพียงพอมากสำหรับร้านค้าทั่วไป
