////กดเลือกEEPROM
////ถ้าเขียนscriptเสร็จแล้วกดRunแล้วเลือก Tools และ SerialMonitor
////เลขserialmonitor สีขาว=เลขด้านหน้าต้้องมากกว่าเลขด้านหลัง สีดำ=เลขด้านหลังต้องมากกว่าเลขด้านหน้า ,,,,ถ้าเลขไม่ตรงให้ไปที่bot08แล้วเช็คใหม่
////วิธีถ่ายคลิป ถ่ายคลิปรถอยู่ืที่สีขาวและตัวเลขที่อยู่serialMOnitor กับ สีดำกับเลขserialmonitor และถ่าย เลขBot

int ref[] = {0,0,0,0,0};
int refSize = sizeof(ref) / sizeof(int); ///สูตรคำนวณหาขนาด
int sencor[] = {A0,A1,A2,A3,A4};
void setup() {
  Serial.begin(9600);
  for(int i = 0; i < refSize; i++){
    ref[i] = EEPROM.read(i) * 10 + EEPROM.read(i + refSize);
  }
}

void loop() {
  Serial.print("Read A0 : [");
  Serial.print(analogRead(sencor[0]));
  Serial.print(",");
  Serial.print(ref[0]);
  Serial.print("] A1 : [");
  Serial.print(analogRead(sencor[1]));
  Serial.print(",");
  Serial.print(ref[1]);
  Serial.print("] A2 : [");
  Serial.print(analogRead(sencor[2]));
  Serial.print(",");
  Serial.print(ref[2]);
  Serial.print("] A3 : [");
  Serial.print(analogRead(sencor[3]));
  Serial.print(",");
  Serial.print(ref[3]);
  Serial.print("] A4 : [");
  Serial.print(analogRead(sencor[4]));
  Serial.print(",");
  Serial.print(ref[4]);
  Serial.println("]")'



  delay(1000);
}
