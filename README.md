# bluSensor® Bluetooth Low Energy API

## Introduction

You can use any Bluetooth Low Energy API to access sensor data on bluSensor® devices. For more information we refer to the platform’s API documents.

### Bluetooth Low Energy SDKs
* iOS: https://developer.apple.com/bluetooth/
* Android: https://developer.android.com/guide/topics/connectivity/bluetooth-le 
* Xamarin: https://developer.xamarin.com/api/namespace/Android.Bluetooth.LE/ 
* Xamarin: https://developer.xamarin.com/api/namespace/CoreBluetooth/

### Official Bluetooth SIG ID
```
Almendo Technologies GmbH (0x06E8)
```
Reference: https://www.bluetooth.com/specifications/assigned-numbers/company-identifiers/


### Service UUIDs

bluSensor® devices are using the following unique service UUIDs
```
a8a82630-10a4-11e3-ab8c-f23c91aec05e
```

### Advertisement Scan Record

All our sensors are broadcasting sensor data using manufacturer specific data.

To filter for bluSensor® devices during discovery you can use the service UUID that is part of the Scan Record. Please note that using scan filters on Android is buggy and it is better to implement your own filter mechanism using the provided UUID from the Scan Record.

#### Service UUID (Scan Record)
```
 a8a82630-10a4-11e3-ab8c-f23c91aec05e
 ```

#### Manufacturer Specific Data (Scan Record)

bluSensor® devices (**1st generation**) 

sensor type  | alarm code    | sensor data
------------ | ------------- | -------------
1 byte       | 1 byte        | variable bytes


bluSensor® devices (**2nd generation**)

company ID   | company ID    | device type  | sensor type  | alarm code   | sensor data |
------------ | ------------- | -------------| -------------| -------------| -------------
0x06         | 0xE8          | 1 byte       | 1 byte       |  1 byte      | variable bytes

#### Device Types

device type  | description            
------------ | ------------- 



#### Sensor Types

sensor type  | description             
------------ | -------------           
01           | Humidity & Temperature  
02           | Accelerometer           
03           | 3D Fusion (Euler)       
04           | Air Flow                
05           | Ambient Light           
06           | Accelerometer, Magnetometer, Gyroscope 
07           | Accelerometer (Low Energy)  
08           | ShakeIt Sports Tracker 
09           | Air Quality (Industrial)
10           | Air Quality 
11           | Usage Counter  
12           | Temperature Probe (PTC) 
13           | Temperature Probe (NTC) 
14           | Infrared Array Camera  
15           | Particulate Matter 
16           | Distance 
17           | Ambient Light  
18           | Highspeed Magnetometer  
19           | People Presence Detector  
20           | People Counter
21           | Distance Counter

#### Alarm Codes





