---
layout: default
title: ดาวน์โหลดและติดตั้ง
---

# ดาวน์โหลดและติดตั้ง

ดาวน์โหลดรุ่นล่าสุดได้ที่หน้า **[Releases](https://github.com/mamankub/asdreader-help/releases/latest)**
แต่ละรุ่นมีไฟล์ต่อไปนี้

| ไฟล์ | ใช้กับ |
|---|---|
| `asdreader-<รุ่น>-windows-x64.msi` | **ตัวติดตั้ง Windows** (แนะนำ) |
| `ASDReader-<รุ่น>-windows-x64-portable.zip` | Windows แบบพกพา ไม่ต้องติดตั้ง |
| `ASDReader-<รุ่น>-linux-x86_64.tar.gz` | Linux |
| `SHA256SUMS.txt` | ค่าตรวจสอบความถูกต้องของไฟล์ |

## ติดตั้งบน Windows

1. ดับเบิลคลิกไฟล์ `.msi`
2. หน้า **Install ASDReader** เลือกได้ว่าจะ
   - สร้างทางลัดบนเดสก์ท็อป
   - เพิ่มเมนู "Edit with ASDReader" เมื่อคลิกขวาที่ไฟล์ PDF

   แล้วกด **Next**
3. หน้า **Choose the install folder** แสดงโฟลเดอร์ติดตั้ง ค่าเริ่มต้นคือ `C:\Program Files\ASDReader`
   ถ้าต้องการติดตั้งที่อื่น กด **Browse...** เลือกโฟลเดอร์ (สร้างโฟลเดอร์ใหม่ได้ด้วยปุ่ม **New**) แล้วกด **OK**
4. กด **Install** และยืนยันสิทธิ์ผู้ดูแลระบบเมื่อ Windows ถาม
5. เมื่อเสร็จกด **Finish** แล้วเปิด ASDReader จากเมนู Start

<p class="note">ไฟล์ติดตั้งยังไม่มีลายเซ็นดิจิทัล Windows SmartScreen อาจขึ้นว่า "Windows protected your PC"
ให้กด <strong>More info</strong> แล้ว <strong>Run anyway</strong> เฉพาะไฟล์ที่ดาวน์โหลดจากหน้านี้และตรวจค่า SHA-256 แล้วเท่านั้น</p>

### ติดตั้งแบบไม่มีหน้าจอ (สำหรับผู้ดูแลระบบ)

```
msiexec /i asdreader-<รุ่น>-windows-x64.msi /qn INSTALLFOLDER="D:\Apps\ASDReader"
```

ตัวเลือกเพิ่มเติม: `INSTALLDESKTOPSHORTCUT=0` ไม่สร้างทางลัดบนเดสก์ท็อป, `INSTALLPDFCONTEXTMENU=0` ไม่เพิ่มเมนูคลิกขวา

### อัปเดตและถอนการติดตั้ง

- รุ่นใหม่ติดตั้งทับรุ่นเดิมได้เลย การตั้งค่าของคุณยังอยู่
- ในโปรแกรม เลือก **วิธีใช้ ▸ ตรวจหาการอัปเดต** เพื่อดูว่ามีรุ่นใหม่หรือไม่
- ถอนการติดตั้งได้ที่ **Settings ▸ Apps ▸ Installed apps ▸ ASDReader ▸ Uninstall**

## รุ่นพกพา (Windows)

แตกไฟล์ `.zip` ไว้ที่ใดก็ได้ (เช่น แฟลชไดรฟ์) แล้วเปิด `ASDReader.exe`
รุ่นพกพาเก็บการตั้งค่าและไฟล์บันทึกไว้ในโฟลเดอร์ `ASDReaderData` ข้างตัวโปรแกรม ไม่เขียนลงเครื่อง

## Linux

```
tar xzf ASDReader-<รุ่น>-linux-x86_64.tar.gz
./ASDReader-<รุ่น>-linux-x86_64/bin/asdreader --language th
```

## ตรวจความถูกต้องของไฟล์

บน Windows เปิด PowerShell ในโฟลเดอร์ที่ดาวน์โหลด แล้วเทียบผลกับบรรทัดเดียวกันใน `SHA256SUMS.txt`

```
Get-FileHash .\asdreader-<รุ่น>-windows-x64.msi -Algorithm SHA256
```

บน Linux: `sha256sum -c SHA256SUMS.txt`
