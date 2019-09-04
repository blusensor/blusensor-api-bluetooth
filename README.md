# bluSensor® Bluetooth Low Energy API

## Introduction

You can use any Bluetooth Low Energy API to access sensor data, download logged data, configure alarms, and much more on our bluSensor® devices. 

For more information how to use Bluetooth Low Energy on your platform we refer to the platform’s API documents.

### Bluetooth Low Energy SDKs
* iOS: https://developer.apple.com/bluetooth/
* Android: https://developer.android.com/guide/topics/connectivity/bluetooth-le 
* Xamarin: https://developer.xamarin.com/api/namespace/Android.Bluetooth.LE/ 
* Xamarin: https://developer.xamarin.com/api/namespace/CoreBluetooth/
* Web: https://github.com/WebBluetoothCG/web-bluetooth/blob/gh-pages/implementation-status.md


### Official Bluetooth SIG ID
```
Almendo Technologies GmbH (0x06E8)
```
Please find our official ID here: [Bluetooth - Company ID](https://www.bluetooth.com/specifications/assigned-numbers/company-identifiers/)


# Advertisements

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
01           | Bluetooth Low Energy (BLE)
02           | WiFi and BLE (IoT Sensor)
03           | WiFi and BLE (MQTT Sensor)


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

#### Advertisement Alarm Codes

bluSensor® devices

alarm code   | description
------------ | ------------- 
00           | no alarm
01           | alarm active



#### Advertisement Sensor Data

##### Humidity & Temperature 

The sensor data is 4 bytes and can be converted using the following mechanism and formular.

```c++
int hum = (data[2] & 0xff) | ((data[3] << 8) & 0xff00); 
float relHum = -6.0f + 125.0f * (float) hum / (float) 65536;
```


```c++
int temp = (data[0] & 0xff) | ((data[1] << 8) & 0xff00);
float tempC = -46.85f + 175.72f * (float) temp / (float) 65536;
```

Example:
```
0100ac667a63 => 42.5% and 23.5°C
```

#### Other Sensors

Will be added soon...

# Services

## Device Information Service
```
180a
```

Please find official specification here: [Bluetooth - Device Information Service](https://www.bluetooth.com/specifications/gatt/viewer?attributeXmlFile=org.bluetooth.service.device_information.xml)

## Battery Service
```
180f
```
Please find official specification here: [Bluetooth - Battery Service](https://www.bluetooth.com/specifications/gatt/viewer?attributeXmlFile=org.bluetooth.service.battery_service.xml)

## bluSensor® Service
```
 a8a82630-10a4-11e3-ab8c-f23c91aec05e
```

All bluSensor® devices implement the following characteristics. The logger functionality needs some configurations to be opertional. See details below.

#### Sensor Data

#### LED

#### MAC Address

#### Logger Time Reference

#### Logger Interval

#### Logger On/Off

#### Logger Control

#### Logger Data

#### Logger Flash Size

#### Logger Usage

# Development Tools

There are many tools available for iOS and Android that you can use for testing and development.

Here are some of the tools available:
* BLExplr (iOS)
* LightBlue Explorer (iOS and Android)
* nRF Connect (iOS and Android)
* Blue Gecko (iOS and Android)


# Purchase Sensors

You can buy sensors and development kits in our online shop at https://www.blusensor.com/shop/

# Support

Having trouble with bluSensor® API or need development support? 

You will get direct support from our **core development team** (free of charge)!

You can contact us anytime at support@blusensor.com

You need a sensor type that is not listed yet?

Just drop us an email!


