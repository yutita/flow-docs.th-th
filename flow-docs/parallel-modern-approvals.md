---
title: สร้างเวิร์กโฟลว์การอนุมัติทันสมัยแบบขนาน | Microsoft Docs
description: สร้างเวิร์กโฟลว์การอนุมัติทันสมัยแบบขนาน
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: ec3c6725ca6c0b1e03738f50132464b00c1f8695
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690709"
---
# <a name="create-parallel-approval-workflows-with-microsoft-flow"></a>สร้างเวิร์กโฟลว์การอนุมัติแบบขนาน ด้วย Microsoft Flow

ในเวิร์กโฟลว์การอนุมัติแบบขนาน หลายบุคคลจำเป็นในการอนุมัติรายการต่าง ๆ เช่น ใบแจ้งหนี้ ซื้อใบสั่งซื้อ คำขอวันหยุดพักผ่อน เป็นต้น การอนุมัติแต่ละคนเป็นอิสระจากผู้อนุมัติอื่นๆ ทั้งหมด

ใน walkthrough นี้ เราใช้ Microsoft Flow เพื่อสร้างโฟลว์ที่คล้ายเวิร์กโฟลว์การอนุมัติแบบขนาน โฟลว์นี้คล้ายกระบวนการขอวันหยุดพักผ่อนของพนักงาน ที่จำเป็นต้องมีการอนุมัติจากบุคคลทั้งหมด (หรือทีม) ที่พนักงานทำงานให้ พนักงานใช้[รายการ SharePoint](https://support.office.com/article/Introduction-to-lists-0a1c3ace-def0-44af-b225-cfa8d92c52d7)เพื่อร้องขอวันหยุดพักผ่อน การอนุมัติวันหยุดพักผ่อนจำเป็นต้องทำจากผู้จัดการสายตรงของพนักงาน ทีมขาย และทีมทรัพยากรบุคคล คำขอวันหยุดพักผ่อนแต่ละตัวจะถูกส่งไปยังผู้อนุมัติแต่ละคนตัดสินใจ ขั้นตอนการส่งอีเมลที่มีสถานะการเปลี่ยนแปลง และจากนั้น ปรับปรุง SharePoint ด้วยการตัดสินใจ

## <a name="prerequisites"></a>ข้อกำหนดเบื้องต้น

[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

รายการ SharePoint Online ที่คุณสร้างต้องมีคอลัมน์ต่อไปนี้:

   ![คอลัมน์รายการ SharePoint](./media/parallel-modern-approvals/sharepoint-columns.png)

จดบันทึกชื่อและ URL ของรายการ SharePoint Online เราใช้รายการเหล่านี้ในภายหลังเพื่อกำหนดค่าทริกเกอร์ **SharePoint - เมื่อรายการหนึ่งถูกสร้างขึ้น**

## <a name="create-your-flow-from-the-blank-template"></a>สร้างโฟลว์ของคุณจากเทมเพลตว่างเปล่า

[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>เพิ่มทริกเกอร์

[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

   ![ข้อมูล SharePoint](includes/media/parallel-modern-approvals/select-sharepoint-site-info.png)

## <a name="get-the-manager-for-the-person-who-created-the-vacation-request"></a>รับผู้จัดการสำหรับบุคคลที่สร้างคำขอวันลาพักร้อน

[!INCLUDE [add-get-manager-action](includes/add-get-manager-action.md)]

## <a name="name-and-save-your-flow"></a>ตั้งชื่อให้โฟลว์ของคุณและบันทึก

1. ใส่ชื่อสำหรับโฟลว์ของคุณ จากนั้นเลือกไอคอน**บันทึก**เพื่อบันทึกงานที่เราได้ทำไว้

   ![บันทึกโฟลว์](./media/parallel-modern-approvals/save.png)

> [!NOTE]
> เลือกไอคอน**บันทึก**เป็นระยะ ๆ เพื่อบันทึกการเปลี่ยนแปลงไปยังโฟลว์ของคุณ
> 
> 


## <a name="add-an-approval-action-for-immediate-manager"></a>เพิ่มการดำเนินการอนุมัติสำหรับผู้จัดการสายตรง

[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

> [!IMPORTANT]
> การดำเนินการนี้ส่งคำขอวันหยุดพักผ่อนไปยังที่อยู่อีเมลในกล่อง**มอบหมายให้** ดังนั้นให้แทรกโทเค็น**อีเมล**จากรายการ**ผู้จัดการ (v2)**
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-sales-team"></a>แทรกการดำเนินการการอนุมัติสาขาแบบคู่ขนานของทีมงานขาย

1. เลือกลูกศรที่อยู่ระหว่าง**ผู้จัดการ (v2)** และบัตร**เริ่มการอนุมัติ**
2. เลือกเครื่องหมายบวกที่แสดงขึ้นด้านบนของลูกศรหัวลงหลังจากที่คุณเลือก
3. เลือก**เพิ่มสาขาคู่ขนาน**
4. เลือก**เพิ่มแอคชัน**

    ![รับการกำหนดค่าของผู้จัดการ](./media/parallel-modern-approvals/add-parallel-branch.png)
5. ค้นหา เลือก แล้ว กำหนดค่าเป็นดำเนินการ**เริ่มการอนุมัติ**ที่ส่งคำขอวันหยุดพักผ่อนให้กับทีมขาย ดู[ขั้นตอนที่ใช้เมื่อต้องเพิ่มการดำเนินการอนุมัติสำหรับผู้จัดการสายตรง](parallel-modern-approvals.md#add-an-approval-action-for-immediate-manager)ถ้าคุณไม่แน่ใจวิธีการเพิ่มการดำเนินการ**เริ่มการอนุมัติ**

> [!IMPORTANT]
> ใช้ที่อยู่อีเมลของของทีมขายในกล่อง**มอบหมายให้**ของการดำเนินการ**เริ่มการอนุมัติ 2**
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-human-resources-team"></a>แทรกการดำเนินการการอนุมัติสาขาคู่ขนานของทีมทรัพยากรบุคคล

1. ทำซ้ำขั้นตอนเพื่อ[แทรกสาขาคู่ขนานของทีมขาย](parallel-modern-approvals.md#insert-a-parallel-branch-approval-action-for-the-sales-team)เพื่อเพิ่ม และกำหนดค่าดำเนินการ**เริ่มการอนุมัติ**เพื่อส่งคำขอวันหยุดพักผ่อนไปยังฝ่ายทรัพยากรบุคคล

> [!IMPORTANT]
> ใช้ที่อยู่อีเมลของของฝ่ายทรัพยากรบุคคลในกล่อง**มอบหมายให้**ของการดำเนินการ**เริ่มการอนุมัติ 3**
> 
> 

ถ้าคุณได้ติดตามมาตลอด โฟลว์ของคุณควรมีลักษณะเช่นนี้:

   ![โฟลว์พร้อมกับสาขาคู่ขนาน](./media/parallel-modern-approvals/flow-with-parallel-branches.png)

## <a name="options-after-adding-parallel-branches"></a>ตัวเลือกหลังจากเพิ่มสาขาคู่ขนาน

หลังจากคุณได้เพิ่มการกระทำในสาขาคู่ขนาน คุณมีสองตัวเลือกเพื่อเพิ่มขั้นตอนเพิ่มเติมไปยังโฟลว์ของคุณ:

1. ใช้ปุ่ม**แทรกขั้นตอนใหม่**ขนาดเล็ก (ทรงกลมบวกปุ่มที่ปรากฏขึ้นเมื่อคุณเลือกพื้นที่สีขาวบนสาขาหรือพื้นที่ด้านล่างสาขา) ปุ่มนี้เพิ่มขั้นตอนที่**สาขาเฉพาะ** ขั้นตอนที่คุณเพิ่มด้วยปุ่มนี้เรียกใช้หลังจากสาขาเฉพาะนี้่เสร็จสมบูรณ์
1. ใช้ปุ่ม**ขั้นตอนใหม่**ขนาดใหญ่ที่ด้านล่างของเวิร์กโฟลว์ทั้งหมด ขั้นตอนที่คุณเพิ่มด้วยปุ่มนี้เรียกใช้หลังจากที่สาขาทั้งหมดเสร็จสมบูรณ์

ในส่วนต่อไปนี้ เราใช้ปุ่ม**แทรกขั้นตอนใหม่**ขนาดเล็ก เพื่อดำเนินการเหล่านี้ของแต่ละสาขา:

* เพิ่มเงื่อนไขที่ตรวจสอบถ้ามีอนุมัติ หรือปฏิเสธคำขอวันหยุดพักผ่อน
* ส่งอีเมลที่จะแจ้งให้พนักงานผลการตัดสินใจ
* ปรับปรุงคำขอวันหยุดพักผ่อนใน SharePoint ด้วยการผลการอนุมัติ

จากนั้น เราใช้ปุ่ม**ขั้นตอนใหม่**ขนาดใหญเพื่อส่งอีเมลที่สรุปตัดสินใจทั้งหมดของคำขอวันหยุดพักผ่อน

ลองทำต่อไป:

## <a name="add-a-condition-to-each-branch"></a>เพิ่มเงื่อนไขให้แต่ละสาขา

1. เลือกพื้นที่สีขาวบนการ**เริ่มการอนุมัติ**สาขา
2. เลือกปุ่ม**แทรกขั้นตอนใหม่**ขนาดเล็ก (แบบวงกลมบวกปุ่มที่ปรากฏขึ้นหลังจากที่คุณเลือกพื้นที่สีขาวในขั้นตอนก่อนหน้า)
3. เลือก**เพิ่มเงื่อนไข**จากเมนูที่ปรากฏขึ้น
4. เลือกกล่องแรกบนบัตร**เงื่อนไข** จากนั้นเลือกโทเค็น**ตอบสนอง**จากประเภท**เริ่มการอนุมัติ**ในรายการเนื้อหาแบบไดนามิก

    ![โฟลว์พร้อมกับเงื่อนไขสาขาคู่ขนาน](./media/parallel-modern-approvals/configure-approval-condition.png)
5. ยืนยันรายชื่อ(ในตรงกลางของการ**การ์ดเงื่อนไข**) ถูกตั้งค่าให้เป็น**เท่ากับ**
6. ป้อน**อนุมัติ**(ข้อความนี้ตรวจสอบตัวเล็กตัวใหญ่) ลงในกล่องสุดท้าย
7. ตอนนี้บัตรเงื่อนไขของคุณต้องเหมือนกับรูปภาพนี้:

    ![โฟลว์พร้อมกับเงื่อนไขสาขาคู่ขนาน](includes/media/parallel-modern-approvals/condition-card.png)

   > [!NOTE]
   > เงื่อนไขนี้ตรวจสอบการตอบสนองจาก การดำเนินการ**เริ่มการอนุมัติ**ที่จะส่งไปยังผู้จัดการของพนักงาน
   > 
   > 
8. ทำซ้ำขั้นตอนก่อนหน้านี้ที่สาขา**เริ่มการอนุมัติ 2** (คำขออนุมัติไปยังฝ่ายขาย) และ**เริ่มการอนุมัติ 3** (คำขออนุมัติไปยังฝ่ายทรัพยากรบุคคล)

## <a name="add-email-actions-to-each-branch"></a>เพิ่มการดำเนินการอีเมลไปยังแต่ละสาขา

ดำเนินการขั้นตอนต่อไปนี้ **ถ้าใช่**ด้านข้างของ**เงื่อนไข**สาขา

   หมายเหตุ: โฟลว์ของคุณใช้ขั้นตอนเหล่านี้เพื่อส่งอีเมลเมื่อมีการอนุมัติคำขอ:

[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![กำหนดค่าเทมเพลตอีเมลการอนุมัติล่วงหน้า](includes/media/parallel-modern-approvals/yes-email-config.png)

เพื่อส่งอีเมลเมื่อคำขอถูกปฏิเสธ ให้ใช้**ถ้าไม่ใช่** ที่ด้านข้างของ**เงื่อนไข**สาขา จากนั้นทำซ้ำขั้นตอนก่อนหน้าเมื่อต้องเพิ่มเทมเพลสำหรับอีเมลการปฏิเสธ

ทำซ้ำขั้นตอนก่อนหน้านี้ที่สาขา**เริ่มการอนุมัติ 2** (คำขออนุมัติไปยังฝ่ายขาย) และ**เริ่มการอนุมัติ 3** (คำขออนุมัติไปยังฝ่ายทรัพยากรบุคคล)

## <a name="update-the-vacation-request-with-the-decision"></a>ปรับปรุงคำขอวันหยุดพักผ่อนด้วยการตัดสินใจ

ทำตามขั้นตอนต่อไปนี้เพื่อปรับปรุง SharePoint เมื่อตัดสินใจ

   หมายเหตุ: ให้แน่ใจว่าทำตามขั้นตอนเหล่านี้ในทั้งสองด้าน**ถ้าใช่**และ**ถ้าไม่ใช่**ของสาขา

[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

   ![กำหนดไอเท็มการอัปเดต](./media/parallel-modern-approvals/configure-update-item.png)

ทำซ้ำขั้นตอนก่อนหน้านี้ที่สาขา**เริ่มการอนุมัติ 2**และ**เริ่มการอนุมัติ 3**

## <a name="complete-the-flow"></a>ทำโฟลว์ให้เสร็จ

1. เลือก **ขั้นตอนใหม่** > **เพิ่มการดำเนินการ**

    ![กำหนดไอเท็มการอัปเดต](includes/media/parallel-modern-approvals/add-an-action-2-step.png)
1. ใช้ขั้นตอนที่ระบุไว้ก่อนหน้านีเพื่อส่งอีเมลที่สรุปผลลัพธ์ของแต่ละการอนุมัติ ส่งอีเมลนี้ไปยังพนักงานที่ร้องขอวันหยุดพักผ่อน บัตรของคุณอาจมีลักษณะเช่นนี้:

   ![กำหนดไอเท็มการอัปเดต](./media/parallel-modern-approvals/final-email-card.png)

## <a name="learn-more-about-modern-approvals"></a>เรียนรู้เพิ่มเติมเกี่ยวกับการอนุมัติที่ทันสมัย

[บทนำสู่การอนุมัติที่ทันสมัย](modern-approvals.md)

