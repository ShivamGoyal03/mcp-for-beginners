<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a0acf3093691b1cfcc008a8c6648ea26",
  "translation_date": "2025-06-13T06:46:13+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "th"
}
-->
ในโค้ดก่อนหน้านี้ เราได้ทำสิ่งต่อไปนี้:

- นำเข้าไลบรารี
- สร้างอินสแตนซ์ของ client และเชื่อมต่อโดยใช้ stdio เป็นวิธีการขนส่ง
- แสดงรายการ prompts, resources และ tools แล้วเรียกใช้งานทั้งหมด

นั่นแหละ คือ client ที่สามารถสื่อสารกับ MCP Server ได้

ตอนนี้เรามาใช้เวลาทำความเข้าใจในส่วนถัดไป โดยจะแยกโค้ดแต่ละส่วนและอธิบายว่าเกิดอะไรขึ้น

## แบบฝึกหัด: การเขียน client

อย่างที่กล่าวไปแล้ว ให้เราใช้เวลาทำความเข้าใจโค้ด และถ้าต้องการก็สามารถเขียนโค้ดตามไปด้วยได้

### -1- การนำเข้าไลบรารี

เราจะนำเข้าไลบรารีที่จำเป็น ซึ่งเราต้องการอ้างอิงถึง client และโปรโตคอลขนส่งที่เราเลือกใช้คือ stdio stdio เป็นโปรโตคอลสำหรับงานที่รันบนเครื่องของคุณเอง ส่วน SSE เป็นอีกโปรโตคอลหนึ่งที่จะแสดงในบทถัดไป แต่ตอนนี้เราจะใช้ stdio ต่อไป

มาเริ่มที่การสร้างอินสแตนซ์กัน

### -2- การสร้างอินสแตนซ์ของ client และ transport

เราจะต้องสร้างอินสแตนซ์ของ transport และของ client ดังนี้

### -3- การแสดงรายการฟีเจอร์ของเซิร์ฟเวอร์

ตอนนี้เรามี client ที่สามารถเชื่อมต่อได้เมื่อโปรแกรมถูกรันแล้ว แต่ยังไม่ได้แสดงรายการฟีเจอร์ของเซิร์ฟเวอร์ ดังนั้นเรามาทำตรงนี้กันต่อ

ดีมาก ตอนนี้เราได้เก็บข้อมูลฟีเจอร์ทั้งหมดแล้ว คำถามคือเราจะใช้ฟีเจอร์เหล่านี้เมื่อไหร่? client ตัวนี้ค่อนข้างเรียบง่าย หมายความว่าเราต้องเรียกใช้งานฟีเจอร์เหล่านี้อย่างชัดเจนเมื่อเราต้องการ ในบทถัดไป เราจะสร้าง client ที่ซับซ้อนขึ้นซึ่งมีการเข้าถึงโมเดลภาษาขนาดใหญ่ของตัวเอง (LLM) แต่ตอนนี้มาดูวิธีเรียกใช้ฟีเจอร์บนเซิร์ฟเวอร์กันก่อน:

### -4- การเรียกใช้ฟีเจอร์

เพื่อเรียกใช้ฟีเจอร์ เราต้องแน่ใจว่าได้ระบุอาร์กิวเมนต์ที่ถูกต้อง และในบางกรณีต้องระบุชื่อของสิ่งที่เราต้องการเรียกใช้งานด้วย

### -5- การรัน client

เพื่อรัน client ให้พิมพ์คำสั่งต่อไปนี้ในเทอร์มินัล:

## งานที่ได้รับมอบหมาย

ในงานนี้ คุณจะใช้ความรู้ที่ได้เรียนรู้ในการสร้าง client แต่ให้สร้าง client ของคุณเอง

นี่คือเซิร์ฟเวอร์ที่คุณสามารถใช้ได้ ซึ่งคุณต้องเรียกผ่านโค้ด client ของคุณ ลองดูว่าคุณสามารถเพิ่มฟีเจอร์ให้กับเซิร์ฟเวอร์เพื่อทำให้มันน่าสนใจขึ้นได้ไหม

## วิธีแก้ปัญหา

[Solution](./solution/README.md)

## ข้อสรุปสำคัญ

ข้อสรุปสำคัญของบทนี้เกี่ยวกับ client คือ:

- สามารถใช้ค้นหาและเรียกใช้ฟีเจอร์บนเซิร์ฟเวอร์ได้
- สามารถเริ่มเซิร์ฟเวอร์พร้อมกับตัว client เองได้ (เหมือนในบทนี้) แต่ client ก็สามารถเชื่อมต่อกับเซิร์ฟเวอร์ที่กำลังรันอยู่ได้เช่นกัน
- เป็นวิธีที่ดีในการทดสอบความสามารถของเซิร์ฟเวอร์ควบคู่ไปกับทางเลือกอื่น ๆ เช่น Inspector ตามที่อธิบายไว้ในบทก่อนหน้า

## แหล่งข้อมูลเพิ่มเติม

- [การสร้าง client ใน MCP](https://modelcontextprotocol.io/quickstart/client)

## ตัวอย่าง

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## ต่อไปคืออะไร

- ถัดไป: [การสร้าง client ที่มี LLM](/03-GettingStarted/03-llm-client/README.md)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารฉบับนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้ความถูกต้องสูงสุด แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความคลาดเคลื่อนได้ เอกสารต้นฉบับในภาษาดั้งเดิมถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่มีความสำคัญ ควรใช้บริการแปลโดยผู้เชี่ยวชาญที่เป็นมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดที่เกิดขึ้นจากการใช้การแปลนี้