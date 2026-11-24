# Testcase Design — GradeCalculator

## 1. Document Information

| รายการ | รายละเอียด |
|---|---|
| System Under Test | GradeCalculator – แปลงคะแนนเป็นเกรด |
| Author | วันเดียวพอ |
| Date Written | 24/11/2569 |
| Document Version | 0.1 |
| Programming Language | Java |
| Test Framework | JUnit 4.13.2 |
| Java Version | Java 17+ |

---

## 2. Requirements from the Exercise

| Req ID | Requirement |
|---|---|
| R1 | รับค่าคะแนนตั้งแต่ 0–100 |
| R2 | คำนวณเกรด A ถึง F |
| R3 | รองรับเกรด B+, C+, D+ |
| R4 | ตรวจสอบคะแนนที่น้อยกว่า 0 หรือมากกว่า 100 |

---

## 3. Grading Scale

| คะแนน | เกรด |
|---|---|
| 80–100 | A |
| 75–79 | B+ |
| 70–74 | B |
| 65–69 | C+ |
| 60–64 | C |
| 55–59 | D+ |
| 50–54 | D |
| 0–49 | F |

### Design Assumptions

- รับคะแนนเป็นจำนวนเต็มชนิด `int` เท่านั้น
- คะแนนต้องอยู่ในช่วง 0–100
- หากคะแนนน้อยกว่า 0 หรือมากกว่า 100 ต้องโยน `IllegalArgumentException`
- ผลลัพธ์ที่ได้ต้องเป็น String
- คะแนนที่อยู่ในช่วงเดียวกันต้องได้เกรดเดียวกัน

---

## 4. Test Design Techniques

| Technique | Description |
|---|---|
| EP (Equivalence Partitioning) | แบ่งคะแนนออกเป็นกลุ่มตามช่วงเกรด และเลือกค่าตัวแทน |
| BVA (Boundary Value Analysis) | ทดสอบค่าขอบเขตของแต่ละช่วงคะแนน |
| Robustness Testing | ทดสอบค่าผิดปกติและค่าที่อยู่นอกช่วงที่กำหนด |

---

## 5. Test Cases

| TC ID | Req ID | Type | Technique | Priority | Test Data | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|---|
| TC01 | R2 | ปกติ | EP | H | 90 | A | - | Not Run |
| TC02 | R3 | ปกติ | EP | H | 77 | B+ | - | Not Run |
| TC03 | R2 | ปกติ | EP | H | 72 | B | - | Not Run |
| TC04 | R3 | ปกติ | EP | H | 67 | C+ | - | Not Run |
| TC05 | R2 | ปกติ | EP | M | 62 | C | - | Not Run |
| TC06 | R3 | ปกติ | EP | M | 57 | D+ | - | Not Run |
| TC07 | R2 | ปกติ | EP | M | 52 | D | - | Not Run |
| TC08 | R2 | ปกติ | EP | H | 25 | F | - | Not Run |
| TC09 | R1, R2 | ขอบเขต | BVA | H | 100 | A | - | Not Run |
| TC10 | R1, R2 | ขอบเขต | BVA | H | 80 | A | - | Not Run |
| TC11 | R2, R3 | ขอบเขต | BVA | H | 79 | B+ | - | Not Run |
| TC12 | R2, R3 | ขอบเขต | BVA | M | 75 | B+ | - | Not Run |
| TC13 | R2 | ขอบเขต | BVA | M | 74 | B | - | Not Run |
| TC14 | R2 | ขอบเขต | BVA | M | 70 | B | - | Not Run |
| TC15 | R2, R3 | ขอบเขต | BVA | M | 69 | C+ | - | Not Run |
| TC16 | R2, R3 | ขอบเขต | BVA | M | 65 | C+ | - | Not Run |
| TC17 | R2 | ขอบเขต | BVA | M | 64 | C | - | Not Run |
| TC18 | R2 | ขอบเขต | BVA | M | 60 | C | - | Not Run |
| TC19 | R2, R3 | ขอบเขต | BVA | M | 59 | D+ | - | Not Run |
| TC20 | R2, R3 | ขอบเขต | BVA | M | 55 | D+ | - | Not Run |
| TC21 | R2 | ขอบเขต | BVA | M | 54 | D | - | Not Run |
| TC22 | R2 | ขอบเขต | BVA | M | 50 | D | - | Not Run |
| TC23 | R2 | ขอบเขต | BVA | H | 49 | F | - | Not Run |
| TC24 | R1, R2 | ขอบเขต | BVA | H | 0 | F | - | Not Run |
| TC25 | R4 | ผิดปกติ | BVA | H | -1 | Throw IllegalArgumentException | - | Not Run |
| TC26 | R4 | ผิดปกติ | BVA | H | 101 | Throw IllegalArgumentException | - | Not Run |
| TC27 | R4 | ผิดปกติ | EP | M | -50 | Throw IllegalArgumentException | - | Not Run |
| TC28 | R4 | ผิดปกติ | EP | M | 150 | Throw IllegalArgumentException | - | Not Run |
| TC29 | R4 | ผิดปกติ | Robustness | L | Integer.MIN_VALUE | Throw IllegalArgumentException | - | Not Run |
| TC30 | R4 | ผิดปกติ | Robustness | L | Integer.MAX_VALUE | Throw IllegalArgumentException | - | Not Run |

---

## 6. TDD Process (Red → Green → Refactor)

| Round | Red | Green | Refactor |
|---|---|---|---|
| 1 | เขียน Test คะแนน 100 และ 80 คาดหวังเกรด A แล้วทดสอบกับโค้ดเริ่มต้นที่ยังไม่รองรับ | เขียนโค้ดให้คะแนนตั้งแต่ 80 ขึ้นไปคืนค่า A | ตรวจสอบโค้ดให้เรียบง่ายและอ่านเข้าใจ |
| 2 | เพิ่ม Test คะแนน 79, 75, 74 และ 70 เพื่อทดสอบ B+ และ B | เพิ่มเงื่อนไขเกรด B+ และ B ให้ผ่าน Test | ปรับเงื่อนไขให้เรียงลำดับจากคะแนนสูงไปต่ำ |
| 3 | เพิ่ม Test เกรด C+, C, D+ และ D | เพิ่มเงื่อนไขการคำนวณเกรดที่เหลือ | ลดความซ้ำซ้อนและจัดรูปแบบโค้ด |
| 4 | เพิ่ม Test คะแนน 49 และ 0 เพื่อทดสอบเกรด F | เพิ่มเงื่อนไขคืนค่า F | ตรวจสอบโครงสร้าง if-else |
| 5 | เพิ่ม Test คะแนน -1, 101 และค่าผิดปกติ | เพิ่มการโยน IllegalArgumentException เมื่อคะแนนอยู่นอกช่วง | ตรวจสอบความถูกต้องและรัน Test ทั้งหมดอีกครั้ง |

---

## 7. Traceability Matrix

| Req ID | Requirement | Test Cases | Total |
|---|---|---|---:|
| R1 | รับค่าคะแนน 0–100 | TC01–TC24 | 24 |
| R2 | คำนวณเกรด A ถึง F | TC01–TC24 | 24 |
| R3 | รองรับเกรด B+, C+, D+ | TC02, TC04, TC06, TC11, TC12, TC15, TC16, TC19, TC20 | 9 |
| R4 | ตรวจสอบคะแนนนอกช่วง | TC25–TC30 | 6 |
| Total | | 30 Test Cases | 30 |
