ในหัวข้อก่อนหน้า คุณเห็นวิธีที่ฟีด Twitter ของคุณถูกขับเคลื่อนโดยรายการ SharePoint ด้วยวิธีง่าย ๆ ในหัวข้อนี้ คุณจะได้เรียนรู้วิธีสร้างสถานการณ์ที่เป็นมิตรกับธุรกิจมากขึ้น โดยใช้การอนุมัติ ด้วยวิธีนี้ ทุกคนที่มีสิทธิ์เข้าถึงไปยังรายการ SharePoint สามารถมีส่วนร่วมทวีต และทีมโซเชียลมีเดียสามารถอนุมัติ หรือปฏิเสธทวีตเหล่านั้น ทีมยังคงรักษาการควบคุมของบัญชีและเนื้อหาที่ออกไปยังลูกค้า 

## <a name="create-an-approval-request-flow"></a>สร้างโฟลว์ร้องขอการอนุมัติ
1. บนโฮมเพจ **Microsoft Flow** เลือก**การอนุมัติ** และเลือก**สร้างโฟลว์การอนุมัติ** จากนั้น เลื่อนลงแล้วเลือกเทมเพลต**โพสต์ข้อมูลในรายการไปยัง Twitter หลังจากการอนุมัติ** 
   
    ![เลือกเทมเพลต](./media/learning-approval-center/create-approval.png)
2. ตรวจสอบข้อมูลประจำตัวของบัญชีผู้ใช้สำหรับ **SharePoint**, **การอนุมัติ** และ **Twitter** และเลือก**ดำเนินการต่อ** 
   
    ![ตรวจสอบข้อมูลประจำตัว](./media/learning-approval-center/verify-credentials.png)

ตามค่าเริ่มต้น เทมเพลตนี้จะเริ่มต้นกระบวนการอนุมัติเมื่อใดก็ตามที่รายการใหม่ถูกสร้างขึ้นในรายการที่กำหนด และถ้าได้รับการอนุมัติก็จะโพสต์ทวีตไปยัง Twitter ในหัวข้อนี้ คุณจะปรับเปลี่ยนขั้นตอนนี้ โดยเพิ่มขั้นตอนการอัปเดตรายการ SharePoint พร้อมกับการตอบกลับการอนุมัติ ว่าได้รับอนุมัติหรือไม่ และเพิ่มข้อคิดเห็นที่ผู้อนุมัติอาจเพิ่มลงในคำขอทวีต 

1. ในรายการ SharePoint **ContosoTweets** ที่คุณสร้างขึ้นก่อนหน้านี้ เพิ่มสองคอลัมน์ใหม่:
   
   1. เลือกเครื่องหมายบวก "**+**" และเลือก**ใช่/ไม่ใช่**
   2. ป้อน **ApprovalStatus** และเลือก**สร้าง**
   3. เลือกเครื่องหมายบวก "**+**" และเลือก**ข้อความบรรทัดเดียว**
   4. ป้อน **ApproverComments** และเลือก**บันทึก**
      
      ![เพิ่มคอลัมน์](./media/learning-approval-center/new-columns.png)
2. กลับไปที่ **Microsoft Flow** ในการดำเนินการ**เมื่อมีการสร้างรายการใหม่** ใส่ค่าต่อไปนี้:
   
   * **ที่อยู่ไซต์**: URL ของ SharePoint ของทีมคุณ
   * **ชื่อรายการ**: ContosoTweets
     
     ![ไซต์และรายการ](./media/learning-approval-center/site-address.png)
3. ในการดำเนินการ**เริ่มกระบวนการอนุมัติ** เลือก**แก้ไข**เพื่อแสดงฟิลด์ทั้งหมด 
   
    ![แก้ไขฟิลด์](./media/learning-approval-center/edit-all-fields.png)
4. ใน**ชื่อเรื่อง** ใส่ **New tweet for** แล้วเลือก **Title** จากรายการเนื้อหาแบบไดนามิก 
   
    ![ชื่อเรื่อง](./media/learning-approval-center/tweet-title.png)
5. ใน**กำหนดให้** พิมพ์และเลือกชื่อของคุณ หรือชื่อของผู้ใช้ทดสอบ 
   
    ![กำหนดให้](./media/learning-approval-center/tweet-assigned-to.png)
6. ใน**รายละเอียด** เอารายการเริ่มต้นออก และเพิ่ม **TweetContent**, **TweetDate** และ **Created by DisplayName**จากเนื้อหารายการแบบไดนามิก เชื่อมต่อด้วยคำว่า **on** และ **by** 
   
    ![รายละเอียด](./media/learning-approval-center/tweet-details.png)
7. ใน**ลิงก์รายการ** คัดลอกและวาง URL ของรายการ SharePoint ของคุณ และใน**คำอธิบายของลิงก์รายการ** ใส่ **Contoso Tweet List** 
   
    ![ลิงก์รายการ](./media/learning-approval-center/tweet-item-link.png)
8. ในการดำเนินการ**เงื่อนไข** โฮเวอร์เหนือกล่อง**ถ้าใช่** เลือกเครื่องหมายบวก "**+**" และเลือก**เพิ่มการดำเนินการ** 
   
    ![เพิ่มการดำเนินการ](./media/learning-approval-center/add-an-action.png)
9. ค้นหา**อัปเดตรายการ** เลือกตัวเชื่อมต่อ **SharePoint** และเลือกการดำเนินการ **SharePoint – อัปเดตรายการ**
   
    ![อัปเดตรายการ SharePoint](./media/learning-approval-center/update-item.png)
10. ใน**ที่อยู่ไซต์**และ**ชื่อรายการ** ใส่ URL ของไซต์ของคุณและรายการ **ContosoTweets** อีกครั้ง และใน **ID** ใส่ **ID** จากรายการเนื้อหาแบบไดนามิก 
    
     ![ไซต์, รายการ และ ID](./media/learning-approval-center/address-list-id.png)
11. เลือกฟิลด์**ชื่อเรื่อง** และในรายการเนื้อหาแบบไดนามิก ค้นหา**ชื่อเรื่อง** เพิ่มรายการ**ชื่อเรื่อง** จากการดำเนินการ**เมื่อมีการสร้างรายการใหม่** 
    
     ![ชื่อเรื่องใหม่](./media/learning-approval-center/add-title.png)
12. เลือก **ApprovalStatus** และตั้งค่าเป็น**ใช่** แล้วเลือก **ApproverComments** และตั้งค่าเป็น**ข้อคิดเห็น** จากรายการเนื้อหาแบบไดนามิก 
    
     ![สถานะและข้อคิดเห็น](./media/learning-approval-center/approver-status.png)
13. ใกล้กับด้านล่างของกล่อง**ถ้าไม่ ไม่ต้องทำอะไร** เลือก**เพิ่มการดำเนินการ**
    
     ![เพิ่มการดำเนินการกรณีถ้าไม่](./media/learning-approval-center/add-a-no-action.png)
14. ใช้ขั้นตอนเดียวกันกับที่คุณใช้สำหรับกำหนดค่า**ถ้าใช่** สร้างการดำเนินการ **SharePoint – อัปเดตรายการ** และกำหนดค่าฟิลด์ที่มีค่าเดียวกัน ยกเว้นการตั้งค่า **ApprovalStatus** เป็น**ไม่ใช่** 
    
     ![Status = no](./media/learning-approval-center/status-no.png)
15. เลือกการดำเนินการ**โพสต์ทวีต** เลือก**แก้ไข** และตั้งค่า**ข้อความทวีต**เป็น **TweetContent** จากรายการเนื้อหาแบบไดนามิก  ที่ด้านบนของหน้า เลือก**สร้างโฟลว์**เพื่อบันทึกงานของคุณ 
    
     ![โพสต์ และบันทึก](./media/learning-approval-center/post-tweet.png)

นี่เป็นเพียงวิธีหนึ่งที่ Microsoft Flow สามารถเพิ่มประสิทธิภาพการทำงานสำหรับทีมของคุณ ทีมของคุณสามารถมีส่วนร่วมในแนวคิด, ข่าวสารที่เกี่ยวข้อง หรือคำแนะนำผลิตภัณฑ์ และคุณยังคงควบคุมได้ว่า อะไรจะทวีตออกไปยังลูกค้า

ในหัวข้อถัดไป เราจะได้เห็นว่าเป็นอย่างไร เมื่อผู้อนุมัติได้รับคำขอทวีตใหม่ 
