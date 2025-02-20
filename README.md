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
โครงงานนี้มีวัตถุประสงค์เพื่อวิเคราะห์ข้อมูลคุณภาพอากาศในกรุงเทพฯ โดยเน้นที่ PM2.5 และ PM10  โดยใช้ข้อมูลตั้งแต่ปี 2016-2024  การวิเคราะห์จะใช้ภาษา Python และ libraries เช่น pandas, numpy, matplotlib, และ seaborn

เกณฑ์ระดับฝุ่น PM 2.5 ที่ใช้อ้างอิงในการวิเคราะห์

![image](https://github.com/user-attachments/assets/b660bd2b-f39b-4c63-9750-0f6037298749)
Credit : https://aqicn.org/data-platform/register/

แนวโน้มโดยรวม (Trend)

กราฟ: Trends of PM2.5 and PM10 over Time in Bangkok

![image](https://github.com/user-attachments/assets/beda8325-0aa9-41b9-b3f6-fb8dcff7f187)

•	แนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล: ค่ามลพิษมีความผันผวนตามช่วงเวลา มีบางช่วงที่พุ่งสูงขึ้นชัดเจน 

•	ค่า PM2.5 ยังเกินมาตรฐาน: ถึงแม้จะมีแนวโน้มเพิ่มขึ้น-ลดลงตามฤดูกาล แต่ค่า PM2.5 ในบางช่วงเวลายังคงเกินค่ามาตรฐานที่องค์การอนามัยโลกกำหนด โดยเฉพาะในช่วงต้นปี (มกราคม-มีนาคม) และปลายปี (ตุลาคม-ธันวาคม) ซึ่งอาจเกิดจากปัจจัยตามฤดูกาล เช่น การเผาไหม้ในที่โล่ง การจราจรที่หนาแน่น และสภาพอากาศ

•	PM2.5 มีค่าสูงกว่า PM10โดนรวม: ค่าเฉลี่ยของ PM2.5 มีค่าสูงกว่า PM10 อย่างเห็นได้ชัด แต่ PM10 ก็มีแนวโน้มพุ่งขึ้นมาใกล้เคียงกันในบางช่วง

กราฟ: Daily Average PM2.5 Levels

![image](https://github.com/user-attachments/assets/b7dd5ab0-1986-4d3a-b66b-46676380eaf8)

•	ค่าระดับ PM2.5 รายวันทั้งหมด 4062 วัน

กราฟ: High-Risk Days with PM2.5 > 100

![image](https://github.com/user-attachments/assets/17493791-b8e4-471d-bc6c-69e6a867ec19)

•	ค่า PM2.5 ที่เกิน 100 มีอยู่ทั้งหมด 756 วัน ซึ่งเป็นช่วงต้นปีและปลายปีส่วนใหญ่

กราฟ: High-Risk Days with PM2.5 > 150

![image](https://github.com/user-attachments/assets/bc1c3916-f2d2-40b6-8ec1-a182f6cfa600)

•	ค่า PM2.5 ที่เกิน 150 มีอยู่ทั้มหมด 121 วัน ซึ่งเป็นช่วง ต้นปีและปลายปี

กราฟ: PM2.5 Calendar Heatmap (2016 - 2025)

![image](https://github.com/user-attachments/assets/dbd04ce6-8886-45b6-b3b2-ecd6738c98e9)

•	ภาพรวมรายปี: Calendar Heatmap ช่วยให้เห็นภาพรวมของค่า PM2.5 เฉลี่ยในแต่ละวันของปี โดยใช้โทนสีเพื่อแสดงระดับความรุนแรงของมลพิษ

•	ยืนยันแนวโน้ม: Heatmap ยืนยันแนวโน้มที่เห็นในกราฟก่อนหน้า โดยช่วงต้นปีและปลายปีมักมีค่า PM2.5 สูงกว่าช่วงอื่นๆ

•	เปรียบเทียบระหว่างปี: Heatmap ช่วยให้เปรียบเทียบค่า PM2.5 ระหว่างปีต่างๆ ได้ง่าย เช่น ปี 2020 มีค่า PM2.5 ต่ำกว่าปีอื่นๆ ซึ่งอาจเป็นผลมาจากมาตรการ Lockdown ในช่วงการระบาดของ COVID-19

ความสัมพันธ์ (Correlation)

กราฟ: Correlation Matrix of Pollutants

![image](https://github.com/user-attachments/assets/81b58a9b-53d2-4ad7-8fe5-eb191982d8f9)

•	PM2.5 กับ PM10 มีความสัมพันธ์ระดับปานกลาง (0.55): หมายความว่า PM2.5 มักจะเพิ่มขึ้นพร้อมกับ PM10 แต่ไม่ได้สัมพันธ์กัน 100% ซึ่งอาจเกิดจากแหล่งกำเนิดมลพิษที่คล้ายกัน เช่น การเผาไหม้ การจราจร และฝุ่นละออง

•	PM2.5 กับ O3 (โอโซน) ก็มีความสัมพันธ์ปานกลาง (0.51): อาจเกิดจากกระบวนการทางเคมีในอากาศที่ทำให้ทั้งสองเพิ่มขึ้นพร้อมกัน

• PM2.5 กับ NO2 (ไนโตรเจนไดออกไซด์) มีความสัมพันธ์ระดับเล็กน้อย (0.42): แสดงว่า NO2 อาจมีผลต่อ PM2.5 แต่ไม่ชัดเจนมาก

• PM2.5 กับ CO (คาร์บอนมอนอกไซด์) มีความสัมพันธ์ต่ำ (0.23): อาจเกิดจากแหล่งกำเนิดที่ต่างกัน เช่น CO มาจากการเผาไหม้ของเครื่องยนต์มากกว่า

• PM2.5 กับ SO2 (ซัลเฟอร์ไดออกไซด์) ไม่มีความสัมพันธ์ (-0.13): แสดงว่าการเพิ่มขึ้นของ PM2.5 ไม่ได้สัมพันธ์กับการปล่อย SO2

กราฟ: Statistical Analysis

![image](https://github.com/user-attachments/assets/b2e7de65-d754-408d-b212-79e395af5355)

• PM10 มีค่าต่ำสุด-สูงสุดห่างกันมากที่สุด – แสดงว่ามีช่วงที่ PM10 สูงผิดปกติ (เช่น ช่วงที่เกิดมลพิษหนัก)

• PM2.5 และ PM10 มีค่าเฉลี่ยสูงกว่าสารมลพิษอื่น ๆ – เป็นตัวชี้วัดที่สำคัญของคุณภาพอากาศ

• ค่า Standard Deviation ของ PM2.5 และ PM10 สูงกว่าตัวอื่น – แสดงว่ามีความแปรปรวนสูง (อาจมีบางช่วงที่ค่ามลพิษพุ่งสูงมาก)

• O3 และ NO2 มีค่าต่ำสุดใกล้ศูนย์ แต่ค่าสูงสุดอยู่ในระดับปานกลาง – แสดงว่ามีช่วงที่อากาศดีและช่วงที่มีมลพิษมาก

• SO2 และ CO มีค่าเฉลี่ยต่ำ และมีค่าต่ำสุด-สูงสุดที่ไม่แตกต่างกันมาก – อาจเป็นตัวที่ไม่ส่งผลกระทบต่อคุณภาพอากาศมากเท่าตัวอื่น

กราฟ: Average Concentration of Pollutants

![image](https://github.com/user-attachments/assets/95a6228f-22dc-4cf6-b6c2-d9dbb4e7e939)

•	ค่า PM2.5 มีค่าเฉลี่ยอยู่ที่ 82.22 ซึ่งถือว่าเป็นค่าที่เริ่มมีผลต่อสุขภาพ โดยเฉพาะผู้เป็นโรคทางเดินหายใจ

การคาดการณ์ (Prediction)

กราฟ: PM2.5 Prediction using Linear Regression

![image](https://github.com/user-attachments/assets/89c73b33-7b74-4635-86f4-e171f2a73e9d)

กราฟ: PM2.5 Prediction using Linear Regression (per month)

![image](https://github.com/user-attachments/assets/647b7820-96d4-4159-863b-b4983c1bb2b5)

กราฟ: PM2.5 Prediction using Linear Regression (Y2020 - Y2024)

![image](https://github.com/user-attachments/assets/c4f748cd-f403-4429-a077-1c80f5060c44)

•	ทำนายแนวโน้ม: โมเดล Linear Regression สามารถทำนายแนวโน้มของ PM2.5 ได้ในระดับหนึ่ง โดยใช้ค่า PM2.5 ในวันก่อนหน้า (Lagged Feature) เป็นตัวแปรทำนาย

•	ยังมีความคลาดเคลื่อน: โมเดลยังมีความคลาดเคลื่อนในการทำนายอยู่บ้าง ซึ่งอาจเกิดจากปัจจัยอื่นๆ ที่ไม่ได้นำมาพิจารณาในโมเดล เช่น สภาพอากาศ กิจกรรมต่างๆ และนโยบายของรัฐ

## Summary
จากการวิเคราะห์ข้อมูลและกราฟต่างๆ พบว่าคุณภาพอากาศในกรุงเทพฯ มีแนวโน้มดีขึ้น แต่ค่า PM2.5 ในบางช่วงเวลายังคงเกินค่ามาตรฐาน PM2.5 และ PM10 มีความสัมพันธ์กันอย่างมาก โมเดล Linear Regression สามารถใช้ในการคาดการณ์แนวโน้ม PM2.5 ซึ่งข้อมูล insight เหล่านี้สามารถนำไปใช้ในการวางแผนและดำเนินนโยบายเพื่อลดมลพิษทางอากาศ และปรับปรุงคุณภาพชีวิตของประชาชนต่อไป
