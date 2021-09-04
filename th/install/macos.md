---
title: macOS
description: เริ่มต้นการติดตั้ง PreMiD บน macOS
published: true
date: 2020-02-12T22:08:37.439Z
tags:
---

> ก่อนดำเนินการใด ๆ เพิ่มเติมตรวจสอบให้แน่ใจว่าระบบของคุณตรงตาม [เงื่อนไข](/install/requirements) ไหม 
> 
> {.is-info}

การติดตั้งแอปพลิเคชันนั้นสำคัญมากเพราะส่วนขยายไม่สามารถทำอะไรเองได้

# ติดตั้ง
1. ไปที่หน้าดาวน์โหลดของเรา [คลิกที่นี่](https://premid.app/downloads).
2. เลือก **OS X**.
3. แยกไฟล์หากจำเป็น
4. เปิดไฟล์ติดตั้งที่ดาวน์โหลดแล้ว
5. ข้อความ**แจ้งเตือนความปลอดภัย** อาจปรากฏขึ้น หากคุณติดตั้ง PreMiD เป็นครั้งแรก หากเป็นเช่นนั้น ให้ทำตามขั้นตอนในหัวข้อ [อนุญาตแอพจากนักพัฒนาที่ไม่รู้จัก](https://docs.premid.app/install/macos#allow-apps-from-unidentified-developers)
> This is because we do not have a Code Signing Certificate (CSC). [สนับสนุนพวกเรา](https://www.patreon.com/Timeraa){.is-info}
6. Choose open when prompted.
7. Grant access to connections through **Firewall** and control **System Events** when prompted.

แอปพลิเคชันจะเริ่มต้นโดยอัตโนมัติ Check for the symbol in your menu bar.

> อย่าลืม [เพิ่ม**ส่วนขยาย**](/install) 
> 
> {.is-warning}

![](https://img.icons8.com/color/2x/mac-logo.png) {.align-abstopright}

## Allow apps from unidentified developers
ขั้นตอนสำหรับ macOS Big Sur (11.0+):
1. คลิกขวาที่ตัวติดตั้ง
2. คลิกเปิดในเมนูดรอปดาวน์
3. คลิกเปิดในป๊อปอัป

ขั้นตอนสำหรับ macOS เวอร์ชันเก่า:
1. เปิดการตั้งค่าระบบ
2. ไปที่แท็บ ความปลอดภัยและความเป็นส่วนตัว
3. คลิกล็อคและป้อนรหัสผ่านหรือสแกนลายนิ้วมือเพื่อให้คุณสามารถเปลี่ยนแปลงการตั้งค่าได้
4. ปลี่ยนการตั้งค่าสำหรับ 'อนุญาตแอปที่ดาวน์โหลดจาก' จากเดิมที่เป็น 'App Store' ให้เป็น 'App Store และระบุนักพัฒนา'