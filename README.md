# micro_photocell
## کنترل LED با سنسور فوتوسل و آردوینو
## هدف
هدف این آزمایش بررسی نحوه استفاده از ورودی آنالوگ برای کنترل روشن و خاموش شدن یکLED است. در این پروژه از سنسور فوتوسل )حساس به نور( برای خواندن شدت نور محیط استفاده شده و با مقایسه ی مقدار خوانده شده، LED روشن یا خاموش میشود .
## مواد و ابزار لازم
 برد آردوینو
 ال ای دی
 سنسور فوتوسل (Photocell)  سیمهای اتصال
 مقاومت مناسب )برای اتصال فوتوسل(
## نحوه بستن آزمایش
در این مدار، LED به پین دیجیتال ۱۳ آردوینو متصل شده و فوتوسل به پین A0 متصل است. مراحلاتصال به شرح زیر است : 
۱ . اتصال فوتوسل :  یک پایه سنسور فوتوسل را به پین A0 آردوینو و پایه دیگر را به زمین (GND) وصل کنید .برای سنجش شدت نور، یک مقاومت مناسب نیز به صورت سری بین فوتوسل و VCC وصل کنید تایک تقسیم ولتاژ مناسب ایجاد شود . 2 . اتصال :LED پایه مثبت LED را به پین دیجیتال ۱۳ و پایه منفی آن را به زمین (GND) آردوینو وصل کنید . با این اتصالات، مقدار سنسور فوتوسل که نشاندهنده شدت نور محیط است، توسط آردوینو خوانده میشود و با توجه به آن، وضعیت روشن یا خاموش بودن LED تنظیم میگردد .



## کد
```
int sensor;
int led=13;

void setup() {
  Serial.begin(9600);
  pinMode(led,OUTPUT);
  
}

void loop() {
  sensor=analogRead(A0);
  Serial.print("sensor value=");
  Serial.println(sensor);
  delay(300);
   if(sensor>120){
    digitalWrite(led,LOW);
   }
   else{
    digitalWrite(led,HIGH);
   }
 

}

```
## توضیحات کد
۱ . تنظیمات اولیه : در تابع setup ، پورت سریال برای نمایش مقدار سنسور راهاندازی میشود و پینLED به عنوان خروجی تنظیم میشود .
```
{ ()setup void
;)9600(beginSerial.
} ;OUTPUT) (led,pinMode
```
2 . خواندن مقدار فوتوسل و کنترل :LED در حلقهی اصلی برنامه، مقدار فوتوسل از پین 0A خوانده
شده و از طریق پورت سریال نمایش داده میشود. سپس این مقدار با عدد ۱20 مقایسه میشود.
اگر مقدار خواندهشده از فوتوسل بیش از ۱20 باشد )نشاندهنده نور زیاد(، LED خاموش و اگر کمتر
باشد )نشاندهنده نور کم(، LED روشن میشود .
```
{ ()loop void
;(A0)analogRead = sensor
;)value=" "sensor(printSerial.
;(sensor)printlnSerial.
;)300(delay
{ )120 > (sensor if
} ;LOW) (led,digitalWrite
{ else
} } ;HIGH) (led,digitalWrite
```
## نتیجه
در این پروژه، LED با توجه به مقدار خوانده شده از فوتوسل که نشاندهندهی شدت نور محیط
است، روشن یا خاموش میشود. این پروژه نحوهی استفاده از ورودی آنالوگ فوتوسل برای کنترل
دستگاههای مختلف را نشان میدهد .
