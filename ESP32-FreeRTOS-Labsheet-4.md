# การทดลอง ESP32 FreeRTOS 
##  ฟังก์ชัน vTaskDelete()

1. แก่ไข Code จากโปรแกรมที่แล้ว โดยการเพิ่ม task เข้าไปอีก 1 task

```c
...

void My_First_Task(void * arg)
{
	uint16_t i = 0;
	while(1)
	{
		printf("Hello My First Task %d\n",i);
		vTaskDelay(1000/portTICK_PERIOD_MS);
		i++;

		if(i == 5)
		{
			vTaskDelete(MySecondTaskHandle);
			printf("Second Task deleted\n");
		}
	}
}

...
```

จากโปรแกรมด้านบน เมื่อมีการนับจน i == 5 จะทำให้เงื่อนไขในประโยค if เป็นจริง

คำสั่ง `vTaskDelete(MySecondTaskHandle);` จะลบ `MySecondTaskHandle` ออกจาก list ของ task ที่จะทำงาน


4. รันและบันทึกผลจากโปรแกรมข้างบน วิเคราะห์ผลที่ได้ว่าเป็นอย่างไร
## ![Freertos-Lab4 4](https://github.com/user-attachments/assets/4a6dc3d0-6974-4965-9c57-1afcc781749a)
### vTaskDelete ในโค้ดนี้ช่วยให้สามารถลบ Task ที่ไม่ต้องการ  Handle ของ Task จะถูกตั้งค่าเป็น NULL หลังจาก Task ถูกลบออกแล้ว
## [>> ต่อไป >>](./ESP32-FreeRTOS-Labsheet-5.md) 
