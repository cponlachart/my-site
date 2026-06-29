# EnviPSU Website — Deploy package (แนวทาง A: เดโม)

ไฟล์ในโฟลเดอร์นี้เป็นไฟล์ **self-contained** (ฝังรูป/โลโก้/ฟอนต์/ข้อมูลครบในไฟล์เดียว) เปิดได้ทันทีและอัปขึ้นโฮสต์สแตติกได้เลย

- `index.html` — เว็บไซต์คณะ (สาธารณะ)
- `admin.html` — ระบบจัดการเนื้อหา (สำหรับเจ้าหน้าที่) เข้าได้จากลิงก์ "สำหรับเจ้าหน้าที่ · เข้าสู่ระบบผู้ดูแล" ที่ท้ายเว็บ

> ⚠️ โหมดเดโม: ข้อมูลที่แก้ใน admin ถูกเก็บใน **localStorage ของเบราว์เซอร์เครื่องนั้น** เท่านั้น
> ใช้พรีวิว/แก้คนเดียวได้ แต่ยังไม่ซิงก์ข้ามเครื่องและผู้เข้าชมทั่วไปไม่เห็นการแก้ของคุณ
> หากต้องการให้เนื้อหาแชร์ถึงทุกคน ให้ใช้แนวทาง B (เก็บข้อมูลเป็นไฟล์ JSON ใน repo หรือเชื่อม backend)

## วิธี deploy บน GitHub Pages

1. สร้าง repository ใหม่บน GitHub (เช่น `envipsu-web`)
2. อัปโหลดไฟล์ `index.html`, `admin.html` (และ `README.md`) เข้า repo — ลากวางผ่านหน้าเว็บ GitHub ได้เลย หรือใช้ git:
   ```bash
   git init
   git add index.html admin.html README.md
   git commit -m "EnviPSU website"
   git branch -M main
   git remote add origin https://github.com/<username>/envipsu-web.git
   git push -u origin main
   ```
3. ไปที่ repo → **Settings → Pages**
4. ที่ **Source** เลือก **Deploy from a branch** → Branch: **main** / **/ (root)** → **Save**
5. รอสักครู่ เว็บจะอยู่ที่ `https://<username>.github.io/envipsu-web/`
   - หน้าเว็บ: `https://<username>.github.io/envipsu-web/`
   - หน้า admin: `https://<username>.github.io/envipsu-web/admin.html`

## หมายเหตุความปลอดภัย
หน้า `admin.html` ในแพ็กเกจนี้เป็นต้นแบบ ไม่มีระบบยืนยันตัวตนจริง (กรอกอะไรก็เข้าได้)
ก่อนใช้งานจริงควรเพิ่มการล็อกอินจริงและที่เก็บข้อมูลกลาง (แนวทาง B)
