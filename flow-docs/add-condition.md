---
title: เพิ่มเงื่อนไขให้กับโฟลว์ | Microsoft Docs
description: ระบุให้โฟลว์ดำเนินการงานอย่างน้อยหนึ่งงาน เมื่อเงื่อนไขเป็นจริง
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/17/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: b4407238f9d1782db802b47060b156b8b77c328b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689053"
---
# <a name="add-a-condition-to-a-flow"></a>เพิ่มเงื่อนไขให้กับโฟลว์

ระบุให้โฟลว์ดำเนินการงานอย่างน้อยหนึ่งงาน เมื่อเงื่อนไขเป็นจริง ตัวอย่างเช่น ระบุว่าคุณจะได้รับอีเมล ถ้าทวีตที่มีคำสำคัญถูกรีทวีตอย่างน้อย 10 ครั้ง

## <a name="prerequisites"></a>ข้อกำหนดเบื้องต้น

* [สร้างโฟลว์](get-started-logic-template.md) จากเทมเพลตfrom - บทช่วยสอนนี้[ใช้เทมเพลตนี้](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/)เป็นตัวอย่าง

## <a name="add-a-condition"></a>เพิ่มเงื่อนไข

1. ใน [Microsoft Flow](https://flow.microsoft.com) ให้เลือก **โฟลว์ของฉัน** ในแถบนำทางด้านบน

    คุณอาจต้องลงชื่อเข้าใช้ ถ้าคุณยังไม่ได้ลงชื่อเข้าใช้

1. ในรายการโฟลว์ ให้เลือกหนึ่งในโฟลว์ที่คุณสร้างขึ้น

    บทช่วยสอนนี้ใช้ตัวอย่างที่มีทริกเกอร์ Twitter และการดำเนินการ SharePoint

1. เลือก **แก้ไขโฟลว์**

1. ภายใต้การดำเนินการล่าสุด ให้เลือก **ขั้นตอนใหม่**

1. เลือก **เพิ่มเงื่อนไข**

    ![ปุ่มเงื่อนไข](./media/add-condition/add-condition.png)

1. บนบัตร **เงื่อนไข** ให้เลือกพื้นที่ว่างในกล่องทางด้านซ้าย

    รายการ **เนื้อหาแบบไดนามิก** จะเปิดขึ้น

1. เลือกพารามิเตอร์ **จำนวนการรีทวีต** เพื่อเพิ่มลงในกล่อง

1. ในกล่องตรงกลางของบัตร **เงื่อนไข** ให้เลือก **มากกว่าหรือเท่ากับ**

1. ในกล่องทางด้านขวา ให้ป้อน **10**

    ![กล่อง ชื่อวัตถุ ที่มีพารามิเตอร์อยู่ด้านใน](./media/add-condition/specify-condition.png)

1. เลือกส่วนหัวของการดำเนินการที่คุณต้องการใช้ภายในเงื่อนไข (เช่น **สร้างรายการ**) และลากไปใต้ข้อความที่อ่านว่า **ถ้าใช่**

    เมื่อคุณปล่อยเคอร์เซอร์ การดำเนินการจะย้ายไปยังกล่องนั้น

    ![ลากการดำเนินการ](./media/add-condition/drag-action.png)

1. กำหนดค่าการดำเนินการ ถ้าจำเป็น

1. บันทึกโฟลว์

## <a name="edit-in-advanced-mode"></a>แก้ไขในโหมดขั้นสูง

คุณยังสามารถเลือก **แก้ไขในโหมดขั้นสูง** เพื่อเขียนเงื่อนไขขั้นสูงกว่า คุณสามารถใช้นิพจน์จาก *ภาษานิยามเวิร์กโฟลว์* ในโหมดขั้นสูงได้ เรียนรู้เกี่ยวกับ [นิพจน์](https://msdn.microsoft.com/library/azure/mt643789.aspx) ที่พร้อมใช้งานทั้งหมด

## <a name="next-steps"></a>ขั้นตอนถัดไป

เรียนรู้วิธีการ[ใช้นิพจน์](use-expressions-in-conditions.md)ในเงื่อนไขในโหมดขั้นสูง
