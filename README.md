 Test Cases

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

