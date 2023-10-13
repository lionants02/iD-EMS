# Er

```mermaid
erDiagram
erDiagram
    event["เหตุการณ์"]

    call["สายการแจ้งเหตุ"] {
        gen call_id PK "รหัสอ้างอิง ระบบ Gen"
        gen event_plan_id FK "Link สถานที่เกิดเหตุ"
        gen event_person_id FK "Link ผู้แจ้ง"
    }
    call_plan["สถานที่เกิดเหตุ"]{
        gen event_plan_id PK "รหัสสถานที่ ระบบ Gen"
        varchar2(200) E_Place_Detail"สถานที่รายละเอียด"
        varchar2(50) E_Mooban"หมู่บ้าน/หมู่ที่"
        varchar2(50) E_Tambol"ตำบล"
        varchar2(50) E_Amphur"อำเภอ"
        varchar2(50) E_Province"จังหวัด"
        varchar2(50) E_Latitude
        varchar2(50) E_Longitude
        timestamp create
        timestamp update
    }
    call_person["ผู้แจ้ง"]{
        gen event_person_id PK "รหัสผู้แจ้ง ระบบ Gen"
        varchar2(200) E_Caller_Name"ชื่อ-นามสกุล"
        varchar2(50) E_Call_Channel_Code"ช่องทางการแจ้งเหตุ"
        varchar2(50) E_Caller_Number
        varchar2(200) E_Place_Detail"สถานที่รายละเอียด"
        varchar2(50) E_Mooban"หมู่บ้าน/หมู่ที่"
        varchar2(50) E_Tambol"ตำบล"
        varchar2(50) E_Amphur"อำเภอ"
        varchar2(50) E_Province"จังหวัด"
        varchar2(50) E_Latitude
        varchar2(50) E_Longitude
        timestamp create
        timestamp update
    }
    call_patient["ข้อมูลผู้ประสบเหตุตอนรับแจ้ง"]{
        gen event_patient_id PK "ระบบ Gen"
        gen call_id FK "Link สายการแจ้งเหตุ"
        varchar2(200) E_Idc_Code
        varchar2(200) E_Event_Detail
        timestamp create
        timestamp update
    }

    event 1--many call : "มี"
    call 1--1 call_plan : "มี"
    call  1--1 call_person : "มี"
    call 1--many call_patient : "มี"


```
