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
<p align="center"> Credit : https://aqicn.org/data-platform/register/</p><br>

แนวโน้ม PM 2.5 (Trend)

![image](https://github.com/user-attachments/assets/0d14e8ac-4b66-44de-b64f-85b835c48dff)

<p align="center"> กราฟ 1: Daily Average PM2.5 Levels</p><br>

•	ค่าระดับ PM2.5 รายวันทั้งหมด 3117 วัน

![image](https://github.com/user-attachments/assets/40123307-c486-4394-91c3-e957dcbc35d9)

<p align="center"> กราฟ 2: Daily and Monthly Average PM2.5 Levels</p><br>

• มีแนวโน้มเป็น คาบฤดูกาล (Seasonality) โดยค่า PM2.5 จะสูงขึ้นในช่วงปลายปีถึงต้นปีถัดไป (ประมาณ พ.ย. - มี.ค.) และลดลงช่วงกลางปี

• ค่าฝุ่นสูงขึ้นเป็นรอบ ๆ คล้ายกับปรากฏการณ์หมอกควันในช่วงฤดูหนาว

![image](https://github.com/user-attachments/assets/25ab37c0-9512-412d-97dc-d82b2c821f2f)

<p align="center"> กราฟ 3: High-Risk Days with PM2.5 > 100</p><br>

•	ค่า PM2.5 ที่เกิน 100 มีอยู่ทั้งหมด 756 วัน 

• มีจำนวนวันที่ค่าฝุ่นสูงเกิน 100 มากในช่วงฤดูหนาวของทุกปี

• สังเกตได้ว่าบางช่วงที่มีช่วงเว้นว่าง เกิดจากการที่ค่า PM ในช่วงนั้นไม่เกิน 100 ซึ่งจะเป้นช่วงประมาณ (พ.ค.-ก.ย.)

![image](https://github.com/user-attachments/assets/0eef25b9-a0b7-438c-919c-2e0fccc85d3a)

<p align="center"> กราฟ 4: High-Risk Days with PM2.5 > 150</p><br>

•	ค่า PM2.5 ที่เกิน 150 มีอยู่ทั้มหมด 121 วัน ซึ่งเป็นช่วง ต้นปีและปลายปี

•	ยังคงพบแนวโน้มเป็นรอบฤดูกาล เช่นเดียวกับกราฟก่อนหน้า

![image](https://github.com/user-attachments/assets/dbd04ce6-8886-45b6-b3b2-ecd6738c98e9)

<p align="center">กราฟ 5: PM2.5 Calendar Heatmap (2016 - 2025)</p><br>

•	ภาพรวมรายปี: Calendar Heatmap ช่วยให้เห็นภาพรวมของค่า PM2.5 เฉลี่ยในแต่ละวันของปี โดยใช้โทนสีเพื่อแสดงระดับความรุนแรงของมลพิษ

•	ยืนยันแนวโน้ม: Heatmap ยืนยันแนวโน้มที่เห็นในกราฟก่อนหน้า โดยช่วงต้นปีและปลายปี มักมีค่า PM2.5 สูงกว่าช่วงอื่นๆ 

• PM2.5 สูงสุดในช่วงต้นปี (มกราคม - มีนาคม)

• PM2.5 ลดลงชัดเจนในช่วงกลางปี (เมษายน - กันยายน)

• แนวโน้มฝุ่นสะสมมากขึ้นช่วงปลายปี (ตุลาคม - ธันวาคม)

•	เปรียบเทียบระหว่างปี: Heatmap ช่วยให้เปรียบเทียบค่า PM2.5 ระหว่างปีต่างๆ ได้ง่าย เช่น ปี 2022 มีค่า PM2.5 ต่ำกว่าปีอื่นๆ ซึ่งอาจเป็นผลมาจากมาตรการ Lockdown ในช่วงการระบาดของ COVID-19 

ความสัมพันธ์ (Correlation)

![image](https://github.com/user-attachments/assets/81b58a9b-53d2-4ad7-8fe5-eb191982d8f9)

<p align="center">กราฟ 6: Correlation Matrix of Pollutants</p><br>

•	PM2.5 กับ PM10 มีความสัมพันธ์ระดับปานกลาง (0.55): หมายความว่า PM2.5 มักจะเพิ่มขึ้นพร้อมกับ PM10 แต่ไม่ได้สัมพันธ์กัน 100% ซึ่งอาจเกิดจากแหล่งกำเนิดมลพิษที่คล้ายกัน เช่น การเผาไหม้ การจราจร และฝุ่นละออง

•	PM2.5 กับ O3 (โอโซน) ก็มีความสัมพันธ์ปานกลาง (0.51): อาจเกิดจากกระบวนการทางเคมีในอากาศที่ทำให้ทั้งสองเพิ่มขึ้นพร้อมกัน

• PM2.5 กับ NO2 (ไนโตรเจนไดออกไซด์) มีความสัมพันธ์ระดับเล็กน้อย (0.42): แสดงว่า NO2 อาจมีผลต่อ PM2.5 แต่ไม่ชัดเจนมาก

• PM2.5 กับ CO (คาร์บอนมอนอกไซด์) มีความสัมพันธ์ต่ำ (0.23): อาจเกิดจากแหล่งกำเนิดที่ต่างกัน เช่น CO มาจากการเผาไหม้ของเครื่องยนต์มากกว่า

• PM2.5 กับ SO2 (ซัลเฟอร์ไดออกไซด์) ไม่มีความสัมพันธ์ (-0.13): แสดงว่าการเพิ่มขึ้นของ PM2.5 ไม่ได้สัมพันธ์กับการปล่อย SO2

![image](https://github.com/user-attachments/assets/f0aff07d-71d5-49db-ab7f-a0af6907dae3)

<p align="center">กราฟ 7: Trends of PM2.5 and PM10 over Time in Bangkok</p><br>

•	แนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล: ค่ามลพิษมีความผันผวนตามช่วงเวลา มีบางช่วงที่พุ่งสูงขึ้นชัดเจน 

•	ค่า PM2.5 ยังเกินมาตรฐาน: ถึงแม้จะมีแนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล แต่ค่า PM2.5 ในบางช่วงเวลายังคงเกินค่ามาตรฐานที่องค์การอนามัยโลกกำหนด โดยเฉพาะในช่วงต้นปี (มกราคม-มีนาคม) และปลายปี (ตุลาคม-ธันวาคม) ซึ่งอาจเกิดจากปัจจัยตามฤดูกาล เช่น การเผาไหม้ในที่โล่ง การจราจรที่หนาแน่น และสภาพอากาศ

•	PM2.5 มีค่าสูงกว่า PM10 โดนรวม: ค่าเฉลี่ยของ PM2.5 มีค่าสูงกว่า PM10 อย่างเห็นได้ชัด แต่ PM10 ก็มีแนวโน้มพุ่งขึ้นมาใกล้เคียงกันในบางช่วง

![image](https://github.com/user-attachments/assets/b2e7de65-d754-408d-b212-79e395af5355)

<p align="center">กราฟ 8: Statistical Analysis</p><br>

• PM10 มีค่าต่ำสุด-สูงสุดห่างกันมากที่สุด – แสดงว่ามีช่วงที่ PM10 สูงผิดปกติ (เช่น ช่วงที่เกิดมลพิษหนัก)

• PM2.5 และ PM10 มีค่าเฉลี่ยสูงกว่าสารมลพิษอื่น ๆ – เป็นตัวชี้วัดที่สำคัญของคุณภาพอากาศ

• ค่า Standard Deviation ของ PM2.5 และ PM10 สูงกว่าตัวอื่น – แสดงว่ามีความแปรปรวนสูง (อาจมีบางช่วงที่ค่ามลพิษพุ่งสูงมาก)

• O3 และ NO2 มีค่าต่ำสุดใกล้ศูนย์ แต่ค่าสูงสุดอยู่ในระดับปานกลาง – แสดงว่ามีช่วงที่อากาศดีและช่วงที่มีมลพิษมาก

• SO2 และ CO มีค่าเฉลี่ยต่ำ และมีค่าต่ำสุด-สูงสุดที่ไม่แตกต่างกันมาก – อาจเป็นตัวที่ไม่ส่งผลกระทบต่อคุณภาพอากาศมากเท่าตัวอื่น

![image](https://github.com/user-attachments/assets/94beed92-d694-494d-be03-dc23471b8771)

<p align="center">กราฟ 9: Average Concentration of Pollutants</p><br>

•	PM2.5 สูงที่สุด (82.22 µg/m³)  เป็นมลพิษหลักที่ส่งผลต่อคุณภาพอากาศและสุขภาพมีค่ามากกว่า PM10 ถึง 2 เท่า

• PM10 (39.62 µg/m³) อยู่ในระดับสูงรองลงมา ส่วนใหญ่มาจากฝุ่นละอองขนาดใหญ่ เช่น การเผาไหม้และการก่อสร้าง

• O3 (โอโซน) มีค่าเฉลี่ย 18.27 µg/m³ อาจเกิดจากปฏิกิริยาเคมีของมลพิษในชั้นบรรยากาศ

• NO2 (12.02 µg/m³): มักมาจากการจราจรและอุตสาหกรรม

• SO2 (3.55 µg/m³): ส่วนใหญ่มาจากการเผาไหม้เชื้อเพลิงฟอสซิล

• CO (9.29 µg/m³): มาจากการเผาไหม้ไม่สมบูรณ์

การคาดการณ์ (Prediction)

![image](https://github.com/user-attachments/assets/ecb441a1-accd-4dd9-928b-72c5ca45aceb)

<p align="center">กราฟ 10: PM2.5 Prediction using Linear Regression</p><br>

• แนวโน้มของ PM2.5 มีลักษณะเป็นช่วง ๆ มีค่าสูงในช่วงฤดูหนาว-ต้นปี (ม.ค.-มี.ค.) และลดลงช่วงกลางปี มีลักษณะเป็นวัฏจักรซ้ำ ๆ ทุกปี 

• โมเดล Linear Regression สามารถจับแนวโน้มได้ดี เส้น Predicted PM2.5 (เส้นประสีแดง) ค่อนข้างตรงกับ Actual PM2.5 (เส้นสีน้ำเงิน) แสดงให้เห็นว่า Linear Regression จับรูปแบบของข้อมูลได้ดี 

• ความผิดพลาดอาจเกิดขึ้นในค่าที่ผันผวนสูง บางจุดที่ค่า PM2.5 สูงมาก (เช่นช่วง peak) โมเดลอาจพยากรณ์ต่ำกว่าค่าจริง อาจเกิดจากข้อจำกัดของ Linear Regression ที่ไม่สามารถจับความไม่เป็นเชิงเส้น (non-linearity) ได้ดี

![image](https://github.com/user-attachments/assets/c1849171-34ee-40a5-81be-ec33d33d96e7)

<p align="center">กราฟ 11: PM2.5 Prediction using Linear Regression (per month)</p><br>

• แนวโน้มชัดเจนขึ้นเมื่อใช้ค่าเฉลี่ยรายเดือน ค่า PM2.5 มีแนวโน้มเป็นรูปแบบซ้ำ ๆ ทุกปี มีค่าสูงช่วงต้นปี (ธ.ค.-มี.ค.) และลดลงช่วงกลางปี

• โมเดล Linear Regression ทำงานได้ดีขึ้นเมื่อใช้ค่าเฉลี่ยรายเดือน เส้นสีน้ำเงิน (Actual PM2.5) และ เส้นประสีแดง (Predicted PM2.5) เกือบตรงกัน การใช้ค่าเฉลี่ยรายเดือนช่วยลด Noise ในข้อมูล ทำให้การพยากรณ์แม่นยำขึ้น

• ช่วงที่โมเดลอาจมีข้อผิดพลาด ช่วงที่ค่า PM2.5 เพิ่มขึ้นหรือลดลงอย่างรวดเร็ว โมเดลอาจพยากรณ์ได้ช้ากว่าค่าจริง อาจเกิดจากความล่าช้าในโมเดล Linear Regression ที่ไม่สามารถจับความเปลี่ยนแปลงฉับพลันได้ดี

![image](https://github.com/user-attachments/assets/d92a006c-7d5d-4ac6-9e5a-10c5a9e351e9)

<p align="center">กราฟ 12: PM2.5 Prediction using Linear Regression (Y2020 - Y2024)</p><br>

• การตัดช่วงปีให้โฟกัสที่ 2020-2024 กราฟนี้แสดงการพยากรณ์ที่ละเอียดขึ้นโดยเน้นช่วง 5 ปีล่าสุด เห็นรูปแบบฤดูกาลของค่า PM2.5 ได้ชัดเจน (เพิ่มขึ้นช่วงปลายปี - ต้นปี และลดลงกลางปี)

• ความแม่นยำของการพยากรณ์ยังอยู่ในระดับที่ดี เส้นน้ำเงิน (Actual PM2.5) และ เส้นประแดง (Predicted PM2.5) ยังคงใกล้เคียงกัน มีบางช่วงที่โมเดลพยากรณ์ค่า PM2.5 ต่ำกว่าค่าจริง โดยเฉพาะช่วงที่มีการเพิ่มขึ้นอย่างรวดเร็ว

• จุดอ่อนของ Linear Regression โมเดลนี้อาจไม่สามารถจับความผันผวนระยะสั้นหรือเหตุการณ์ที่ไม่เป็นไปตามแนวโน้มปกติได้ดีท เห็นได้ว่าช่วงที่ค่า PM2.5 เพิ่มสูงมากในบางปี (เช่น 2021, 2023) โมเดลคาดการณ์ค่าต่ำกว่าจริงเล็กน้อย

![image](https://github.com/user-attachments/assets/54e2d802-1bdd-402e-adda-912dd21206ab)

<p align="center">กราฟ 13: PM2.5 Prediction with Monthly Average (Y2020 - Y2024)</p><br>

• เพิ่มกราฟแท่งเพื่อให้เห็นรายเดือน

## Summary
1️. แนวโน้มของ PM2.5 

• ค่า PM2.5 มี ความผันผวนเป็นช่วงฤดูกาล โดยมักจะสูงขึ้นในช่วงปลายปีถึงต้นปี (ฤดูหนาว) และลดลงช่วงกลางปี 

• ค่า PM2.5 มีแนวโน้มเพิ่มขึ้นในบางปี และลดลงในบางช่วง ซึ่งอาจเกี่ยวข้องกับมาตรการควบคุมมลพิษ หรือสภาพอากาศ 

• มีหลายจุดที่ค่าฝุ่นพุ่งสูงมาก (peak) ซึ่งอาจเกิดจากเหตุการณ์เฉพาะ เช่น ไฟป่า หรือสภาวะอากาศปิด 

2. ข้อค้นพบจาก EDA

• พบว่า จำนวนวันที่มีค่า PM2.5 เกินมาตรฐาน (100 และ 150 µg/m³) มีแนวโน้มสูงขึ้นในบางปี

• Heatmap รายปี แสดงให้เห็นว่า ช่วงปลายปี - ต้นปีเป็นช่วงที่ค่าฝุ่นสูงที่สุด และมักเกิดขึ้นต่อเนื่องกันหลายวัน

• ค่าฝุ่นในปี 2022 มีค่าน้อยกว่าปีอื่นๆ อาจเป็นผลมาจาก Covid-19 

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

2. ลดแหล่งกำเนิดมลพิษ เช่น คุมเข้มไอเสียจากยานพาหนะ คุมการปล่อยก๊าซพิษจากโรงงานอุตสาหกรรม

![image](https://github.com/user-attachments/assets/0a6fa64b-b9a5-4c7a-9142-b7f2d943c994)

<p align="center"> Credit : https://www.thairath.co.th/scoop/infographic/2619583</p><br>

3. ส่งเสริมเมืองสีเขียวและขนส่งสาธารณะ เพื่อช่วยลดปริมาณ PM2.5 ในระยะยาว
