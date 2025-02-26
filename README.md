# PM2.5-DATA-ANALYTICS
# Data Analysis of PM2.5 in Bangkok(Y2016-Y2025)
## DADS5001 Mini-Project
## Name : Sutthipong Sawang  /  Student ID : 6710412001
## Source of Data 
ข้อมูลคุณภาพอากาศจากแพลตฟอร์มข้อมูลประวัติคุณภาพอากาศ World Air Quality Index (WAQI) project team กรกฎาคม 2016 - กุมภาพันธ์ 2025
- File : https://aqicn.org/data-platform/register/
- รายละเอียด : ข้อมูลฝุ่นละอองขนาดไม่เกิน 2.5 ไมครอน (PM2.5) รายวัน 
- หน่วยวัด : ความเข้มข้นของ PM2.5 ในบรรยากาศโดยทั่วไป (µg/m3)
## Research Question
1.แนวโน้ม PM 2.5 เป็นอย่างไรในช่วงที่ผ่านมา

2.ความสัมพันธ์ระหว่าง PM2.5 กับก๊าซต่างๆ

3.การคาดการณ์ PM2.5 จาก Linear Regression

## Data Journey
โครงงานนี้มีวัตถุประสงค์เพื่อวิเคราะห์ข้อมูลคุณภาพอากาศในกรุงเทพฯ โดยเน้นที่ PM2.5 และ PM10  โดยใช้ข้อมูลตั้งแต่ปี 2016-2025  การวิเคราะห์จะใช้ภาษา Python และ libraries เช่น pandas, numpy, matplotlib, และ seaborn

เกณฑ์ระดับฝุ่น PM 2.5 ที่ใช้อ้างอิงในการวิเคราะห์

![image](https://github.com/user-attachments/assets/b660bd2b-f39b-4c63-9750-0f6037298749)
Credit : https://aqicn.org/data-platform/register/

แนวโน้ม PM 2.5 (Trend)

กราฟ: Daily Average PM2.5 Levels

![image](https://github.com/user-attachments/assets/ddc0ab30-9eab-4e1d-85ec-9aa719cb9eb3)

•	ค่าระดับ PM2.5 รายวันทั้งหมด 3117 วัน

• มีแนวโน้มเป็น คาบฤดูกาล (Seasonality) โดยค่า PM2.5 จะสูงขึ้นในช่วงปลายปีถึงต้นปีถัดไป (ประมาณ พ.ย. - มี.ค.) และลดลงช่วงกลางปี

• ค่าฝุ่นสูงขึ้นเป็นรอบ ๆ คล้ายกับปรากฏการณ์หมอกควันในช่วงฤดูหนาว

กราฟ: High-Risk Days with PM2.5 > 100

![image](https://github.com/user-attachments/assets/06d9cdcb-1778-4637-a8bb-e5fcb3a8b43a)

•	ค่า PM2.5 ที่เกิน 100 มีอยู่ทั้งหมด 756 วัน 

• มีจำนวนวันที่ค่าฝุ่นสูงเกิน 100 มากในช่วงฤดูหนาวของทุกปี

• สังเกตได้ว่าบางช่วงที่มีช่วงเว้นว่าง เกิดจากการที่ค่า PM ในช่วงนั้นไม่เกิน 100 ซึ่งจะเป้นช่วงประมาณ (พ.ค.-ก.ย.)

กราฟ: High-Risk Days with PM2.5 > 150

![image](https://github.com/user-attachments/assets/6173f907-7265-40be-acec-cee7e2c84638)

•	ค่า PM2.5 ที่เกิน 150 มีอยู่ทั้มหมด 121 วัน ซึ่งเป็นช่วง ต้นปีและปลายปี

•	ยังคงพบแนวโน้มเป็นรอบฤดูกาล เช่นเดียวกับกราฟก่อนหน้า

กราฟ: PM2.5 Calendar Heatmap (2016 - 2025)

![image](https://github.com/user-attachments/assets/dbd04ce6-8886-45b6-b3b2-ecd6738c98e9)

•	ภาพรวมรายปี: Calendar Heatmap ช่วยให้เห็นภาพรวมของค่า PM2.5 เฉลี่ยในแต่ละวันของปี โดยใช้โทนสีเพื่อแสดงระดับความรุนแรงของมลพิษ

•	ยืนยันแนวโน้ม: Heatmap ยืนยันแนวโน้มที่เห็นในกราฟก่อนหน้า โดยช่วงต้นปีและปลายปี มักมีค่า PM2.5 สูงกว่าช่วงอื่นๆ 

• PM2.5 สูงสุดในช่วงต้นปี (มกราคม - มีนาคม)

• PM2.5 ลดลงชัดเจนในช่วงกลางปี (เมษายน - กันยายน)

• แนวโน้มฝุ่นสะสมมากขึ้นช่วงปลายปี (ตุลาคม - ธันวาคม)

•	เปรียบเทียบระหว่างปี: Heatmap ช่วยให้เปรียบเทียบค่า PM2.5 ระหว่างปีต่างๆ ได้ง่าย เช่น ปี 2022 มีค่า PM2.5 ต่ำกว่าปีอื่นๆ ซึ่งอาจเป็นผลมาจากมาตรการ Lockdown ในช่วงการระบาดของ COVID-19 

ความสัมพันธ์ (Correlation)

กราฟ: Correlation Matrix of Pollutants

![image](https://github.com/user-attachments/assets/81b58a9b-53d2-4ad7-8fe5-eb191982d8f9)

•	PM2.5 กับ PM10 มีความสัมพันธ์ระดับปานกลาง (0.55): หมายความว่า PM2.5 มักจะเพิ่มขึ้นพร้อมกับ PM10 แต่ไม่ได้สัมพันธ์กัน 100% ซึ่งอาจเกิดจากแหล่งกำเนิดมลพิษที่คล้ายกัน เช่น การเผาไหม้ การจราจร และฝุ่นละออง

•	PM2.5 กับ O3 (โอโซน) ก็มีความสัมพันธ์ปานกลาง (0.51): อาจเกิดจากกระบวนการทางเคมีในอากาศที่ทำให้ทั้งสองเพิ่มขึ้นพร้อมกัน

• PM2.5 กับ NO2 (ไนโตรเจนไดออกไซด์) มีความสัมพันธ์ระดับเล็กน้อย (0.42): แสดงว่า NO2 อาจมีผลต่อ PM2.5 แต่ไม่ชัดเจนมาก

• PM2.5 กับ CO (คาร์บอนมอนอกไซด์) มีความสัมพันธ์ต่ำ (0.23): อาจเกิดจากแหล่งกำเนิดที่ต่างกัน เช่น CO มาจากการเผาไหม้ของเครื่องยนต์มากกว่า

• PM2.5 กับ SO2 (ซัลเฟอร์ไดออกไซด์) ไม่มีความสัมพันธ์ (-0.13): แสดงว่าการเพิ่มขึ้นของ PM2.5 ไม่ได้สัมพันธ์กับการปล่อย SO2

กราฟ: Trends of PM2.5 and PM10 over Time in Bangkok

![image](https://github.com/user-attachments/assets/beda8325-0aa9-41b9-b3f6-fb8dcff7f187)

•	แนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล: ค่ามลพิษมีความผันผวนตามช่วงเวลา มีบางช่วงที่พุ่งสูงขึ้นชัดเจน 

•	ค่า PM2.5 ยังเกินมาตรฐาน: ถึงแม้จะมีแนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล แต่ค่า PM2.5 ในบางช่วงเวลายังคงเกินค่ามาตรฐานที่องค์การอนามัยโลกกำหนด โดยเฉพาะในช่วงต้นปี (มกราคม-มีนาคม) และปลายปี (ตุลาคม-ธันวาคม) ซึ่งอาจเกิดจากปัจจัยตามฤดูกาล เช่น การเผาไหม้ในที่โล่ง การจราจรที่หนาแน่น และสภาพอากาศ

•	PM2.5 มีค่าสูงกว่า PM10 โดนรวม: ค่าเฉลี่ยของ PM2.5 มีค่าสูงกว่า PM10 อย่างเห็นได้ชัด แต่ PM10 ก็มีแนวโน้มพุ่งขึ้นมาใกล้เคียงกันในบางช่วง

กราฟ: Statistical Analysis

![image](https://github.com/user-attachments/assets/b2e7de65-d754-408d-b212-79e395af5355)

• PM10 มีค่าต่ำสุด-สูงสุดห่างกันมากที่สุด – แสดงว่ามีช่วงที่ PM10 สูงผิดปกติ (เช่น ช่วงที่เกิดมลพิษหนัก)

• PM2.5 และ PM10 มีค่าเฉลี่ยสูงกว่าสารมลพิษอื่น ๆ – เป็นตัวชี้วัดที่สำคัญของคุณภาพอากาศ

• ค่า Standard Deviation ของ PM2.5 และ PM10 สูงกว่าตัวอื่น – แสดงว่ามีความแปรปรวนสูง (อาจมีบางช่วงที่ค่ามลพิษพุ่งสูงมาก)

• O3 และ NO2 มีค่าต่ำสุดใกล้ศูนย์ แต่ค่าสูงสุดอยู่ในระดับปานกลาง – แสดงว่ามีช่วงที่อากาศดีและช่วงที่มีมลพิษมาก

• SO2 และ CO มีค่าเฉลี่ยต่ำ และมีค่าต่ำสุด-สูงสุดที่ไม่แตกต่างกันมาก – อาจเป็นตัวที่ไม่ส่งผลกระทบต่อคุณภาพอากาศมากเท่าตัวอื่น

กราฟ: Average Concentration of Pollutants

![image](https://github.com/user-attachments/assets/95a6228f-22dc-4cf6-b6c2-d9dbb4e7e939)

•	PM2.5 สูงที่สุด (82.22 µg/m³)  เป็นมลพิษหลักที่ส่งผลต่อคุณภาพอากาศและสุขภาพมีค่ามากกว่า PM10 ถึง 2 เท่า

• PM10 (39.62 µg/m³) อยู่ในระดับสูงรองลงมา ส่วนใหญ่มาจากฝุ่นละอองขนาดใหญ่ เช่น การเผาไหม้และการก่อสร้าง

• O3 (โอโซน) มีค่าเฉลี่ย 18.27 µg/m³ อาจเกิดจากปฏิกิริยาเคมีของมลพิษในชั้นบรรยากาศ

• NO2 (12.02 µg/m³): มักมาจากการจราจรและอุตสาหกรรม

• SO2 (3.55 µg/m³): ส่วนใหญ่มาจากการเผาไหม้เชื้อเพลิงฟอสซิล

• CO (9.29 µg/m³): มาจากการเผาไหม้ไม่สมบูรณ์

การคาดการณ์ (Prediction)

กราฟ: PM2.5 Prediction using Linear Regression

![image](https://github.com/user-attachments/assets/89c73b33-7b74-4635-86f4-e171f2a73e9d)

• แนวโน้มของ PM2.5 มีลักษณะเป็นช่วง ๆ มีค่าสูงในช่วงฤดูหนาว-ต้นปี (ม.ค.-มี.ค.) และลดลงช่วงกลางปี มีลักษณะเป็นวัฏจักรซ้ำ ๆ ทุกปี 

• โมเดล Linear Regression สามารถจับแนวโน้มได้ดี เส้น Predicted PM2.5 (เส้นประสีแดง) ค่อนข้างตรงกับ Actual PM2.5 (เส้นสีน้ำเงิน) แสดงให้เห็นว่า Linear Regression จับรูปแบบของข้อมูลได้ดี 

• ความผิดพลาดอาจเกิดขึ้นในค่าที่ผันผวนสูง บางจุดที่ค่า PM2.5 สูงมาก (เช่นช่วง peak) โมเดลอาจพยากรณ์ต่ำกว่าค่าจริง อาจเกิดจากข้อจำกัดของ Linear Regression ที่ไม่สามารถจับความไม่เป็นเชิงเส้น (non-linearity) ได้ดี

กราฟ: PM2.5 Prediction using Linear Regression (per month)

![image](https://github.com/user-attachments/assets/b8e6fdea-a35f-46c4-9e96-12db4ffb52c0)

• แนวโน้มชัดเจนขึ้นเมื่อใช้ค่าเฉลี่ยรายเดือน ค่า PM2.5 มีแนวโน้มเป็นรูปแบบซ้ำ ๆ ทุกปี มีค่าสูงช่วงต้นปี (ธ.ค.-มี.ค.) และลดลงช่วงกลางปี

• โมเดล Linear Regression ทำงานได้ดีขึ้นเมื่อใช้ค่าเฉลี่ยรายเดือน เส้นสีน้ำเงิน (Actual PM2.5) และ เส้นประสีแดง (Predicted PM2.5) เกือบตรงกัน การใช้ค่าเฉลี่ยรายเดือนช่วยลด Noise ในข้อมูล ทำให้การพยากรณ์แม่นยำขึ้น

• ช่วงที่โมเดลอาจมีข้อผิดพลาด ช่วงที่ค่า PM2.5 เพิ่มขึ้นหรือลดลงอย่างรวดเร็ว โมเดลอาจพยากรณ์ได้ช้ากว่าค่าจริง อาจเกิดจากความล่าช้าในโมเดล Linear Regression ที่ไม่สามารถจับความเปลี่ยนแปลงฉับพลันได้ดี

กราฟ: PM2.5 Prediction using Linear Regression (Y2020 - Y2024)

![image](https://github.com/user-attachments/assets/379642da-724d-45c1-b7e8-1beddfa921ed)

• การตัดช่วงปีให้โฟกัสที่ 2020-2024 กราฟนี้แสดงการพยากรณ์ที่ละเอียดขึ้นโดยเน้นช่วง 5 ปีล่าสุด เห็นรูปแบบฤดูกาลของค่า PM2.5 ได้ชัดเจน (เพิ่มขึ้นช่วงปลายปี - ต้นปี และลดลงกลางปี)

• ความแม่นยำของการพยากรณ์ยังอยู่ในระดับที่ดี เส้นน้ำเงิน (Actual PM2.5) และ เส้นประแดง (Predicted PM2.5) ยังคงใกล้เคียงกัน มีบางช่วงที่โมเดลพยากรณ์ค่า PM2.5 ต่ำกว่าค่าจริง โดยเฉพาะช่วงที่มีการเพิ่มขึ้นอย่างรวดเร็ว

• จุดอ่อนของ Linear Regression โมเดลนี้อาจไม่สามารถจับความผันผวนระยะสั้นหรือเหตุการณ์ที่ไม่เป็นไปตามแนวโน้มปกติได้ดีท เห็นได้ว่าช่วงที่ค่า PM2.5 เพิ่มสูงมากในบางปี (เช่น 2021, 2023) โมเดลคาดการณ์ค่าต่ำกว่าจริงเล็กน้อย

## Summary
1️. แนวโน้มของ PM2.5 

• ค่า PM2.5 มี ความผันผวนเป็นช่วงฤดูกาล โดยมักจะสูงขึ้นในช่วงปลายปีถึงต้นปี (ฤดูหนาว) และลดลงช่วงกลางปี 

• ค่า PM2.5 มีแนวโน้มเพิ่มขึ้นในบางปี และลดลงในบางช่วง ซึ่งอาจเกี่ยวข้องกับมาตรการควบคุมมลพิษ หรือสภาพอากาศ 

• มีหลายจุดที่ค่าฝุ่นพุ่งสูงมาก (peak) ซึ่งอาจเกิดจากเหตุการณ์เฉพาะ เช่น ไฟป่า หรือสภาวะอากาศปิด 

2. ข้อค้นพบจาก EDA

• พบว่า จำนวนวันที่มีค่า PM2.5 เกินมาตรฐาน (100 และ 150 µg/m³) มีแนวโน้มสูงขึ้นในบางปี

• Heatmap รายปี แสดงให้เห็นว่า ช่วงปลายปี - ต้นปีเป็นช่วงที่ค่าฝุ่นสูงที่สุด และมักเกิดขึ้นต่อเนื่องกันหลายวัน

• ค่าฝุ่นในวันทำงานและวันหยุดมีความใกล้เคียงกัน อาจแสดงถึงแหล่งกำเนิดมลพิษที่ไม่ได้เกิดจากแค่กิจกรรมของมนุษย์ เช่น โรงงาน หรือยานพาหนะ แต่ยังอาจมาจากสภาพอากาศ 

3️. ความสัมพันธ์ระหว่าง PM2.5 กับก๊าซมลพิษ 

• ค่า PM2.5 มีความสัมพันธ์เชิงบวกกับ PM10, O3, NO2 และ CO ซึ่งหมายความว่าเมื่อค่าของมลพิษเหล่านี้สูงขึ้น ค่า PM2.5 ก็มักจะสูงขึ้นตาม

• ความสัมพันธ์ระหว่าง PM2.5 กับ SO2 เป็นไปในเชิงลบในบางช่วงเวลา อาจเป็นเพราะกระบวนการเคมีในอากาศ หรือแหล่งกำเนิดของ SO2 อาจแตกต่างจาก PM2.5 ในขณะที่ PM2.5 มักสูงช่วงอากาศปิดหรือมีหมอกควัน

• CO และ NO2 เป็นตัวชี้วัดที่ดีของ PM2.5 เพราะทั้งสองมักมาจากการเผาไหม้เชื้อเพลิง เช่น การจราจรและโรงงานอุตสาหกรรม

4️. การคาดการณ์ PM2.5 ด้วย Linear Regression

• ใช้ Linear Regression เพื่อคาดการณ์ค่า PM2.5 โดยใช้ก๊าซมลพิษอื่น ๆ เป็นตัวแปรอิสระ

• ผลลัพธ์แสดงให้เห็นว่าโมเดลสามารถ คาดการณ์ค่า PM2.5 ได้ใกล้เคียงกับค่าจริงในระดับแนวโน้ม โดยเฉพาะเมื่อใช้ค่าเฉลี่ยรายเดือน

• อย่างไรก็ตาม โมเดลยังมีข้อจำกัดในการพยากรณ์ค่าฝุ่นที่พุ่งสูงมาก (peak values) ซึ่งอาจต้องใช้โมเดลที่ซับซ้อนขึ้น เช่น Time Series หรือ Machine Learning ขั้นสูง

5️. ผลลัพธ์สำคัญ

• ค่า PM2.5 มีแนวโน้มเป็น รูปแบบฤดูกาล โดยสูงขึ้นช่วงปลายปี - ต้นปี

• การวิเคราะห์ EDA พบว่า มลพิษในอากาศมีความเชื่อมโยงกับ PM2.5 โดยเฉพาะ PM10, O3 และ NO2

• Linear Regression สามารถคาดการณ์แนวโน้มของ PM2.5 ได้ดี แต่ยังมีข้อจำกัดในกรณีค่าฝุ่นที่พุ่งสูงมาก

• ข้อมูลที่ได้สามารถนำไปใช้เป็นแนวทางในการ เฝ้าระวังคุณภาพอากาศและวางแผนมาตรการป้องกันมลพิษ ได้

## ข้อเสนอแนะ

1️. ใช้โมเดลคาดการณ์ PM2.5 เพื่อแจ้งเตือนประชาชนล่วงหน้า

2. ลดแหล่งกำเนิดมลพิษ เช่น คุมเข้มไอเสียจากยานพาหนะ ลดการเผาในที่โล่ง

3. ส่งเสริมเมืองสีเขียวและขนส่งสาธารณะ เพื่อช่วยลดปริมาณ PM2.5 ในระยะยาว
