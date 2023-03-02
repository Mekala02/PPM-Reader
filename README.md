# PPM-Reader
 Simple PPM reader for arduino (Interrupt)

```
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
