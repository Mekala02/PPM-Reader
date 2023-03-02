# PPM-Reader
 Simple PPM reader for arduino (Interrupt)

```cpp
void Read_Channels(){
    t = micros();
    d = t - pt;
    if (d > 3000)
        c = 0;
    ch[c] = d;
    c ++;
    pt = t;
}
```

Example:

```cpp
#define PPM_PIN 3
#define PPM_CHANNELS 8

// current time, previous time
unsigned long int t, pt = 0;
// channel no, time differance
int c, d = 0;
int ch[15];

void Read_Channels();

void setup() {
    pinMode(PPM_PIN, INPUT_PULLUP);
    attachInterrupt(digitalPinToInterrupt(PPM_PIN), Read_Channels, FALLING);
}

void loop() {
  for (int i = 0; i < PPM_CHANNELS; i++){
    Serial.print(channel[i]);
    Serial.print("\t");
  }
  Serial.println();
  delay(10);
}

// Reading ppm signal
void Read_Channels(){
    t = micros();
    d = t - pt;
    if (d > 3000)
        c = 0;
    ch[c] = d;
    c ++;
    pt = t;
}
```
