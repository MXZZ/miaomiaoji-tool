# 蓝牙机Bluetooth API By ihciah

### Dependency

`pybluez` Bluetooth API needs (the Raspberry Pi toss this thing and stepped on a lot of pits

`twisted, pyopenssl` WeChat interface script needs

`cv2, numpy` image conversion tool needed

### establish connection

The `BtManager()` parameter is left blank to search for available downtime and connect

`BtManager("69:68:63:69:61:68")` Additional specified MAC will skip the search process and connect directly to the device, saving time

### Print image

From the API, the machine can only input binary images for printing, so the text-to-picture is done on the client side.

The printed image format is binary data, and each bit represents black (1) or white (0) with 384 points per line.

```python
Mmj = BtManager()
mmj.sendImageToBt(img)
Mmj.disconnect()
```

### Other miscellaneous

`registerCrcKeyToBt(key=123456)` Change the communication CRC32 KEY (not very acquainted with this is to swear, it is reasonable to listen to this package to get the key)

`sendPaperTypeToBt(paperType=0)` Change the paper type (crazy paper)

`sendPowerOffTimeToBt(poweroff_time=0)` Change the automatic shutdown time

`sendSelfTestToBt()` print self-test page

`sendDensityToBt(density)` Set print density

`sendFeedLineToBt(length)` controls the padding after printing

`queryBatteryStatus()` Query the remaining battery power

`queryDensity()` query print density

`sendFeedToHeadLineToBt(length)` doesn't quite understand the difference with `sendFeedLineToBt`, but it seems to be called after printing.

`queryPowerOffTime()` Query auto shutdown time

`querySNFromBt()` Query device SN

In fact, there are quite a lot of operations, interested in watching `const.py` guess guess.

### Image Tools

`ImageConverter.image2bmp(path)` Any image to binary data for printing
 
`TextConverter.text2bmp(text)` specifies the text to be converted to binary data for printing

### WeChat public platform tool

Two small scripts are used to automatically print the image after sending it to the WeChat public account.

`wechat.php` is used by VPS to receive Tencent data. By default, only specified users are allowed to print.

`printer_server.py` is placed on a Bluetooth-equipped machine that is close to the downtime, such as the Raspberry Pi. You can use `tinc` to create a VPN for direct access by the VPS.

### Make complaints

Can't this add a multi-print function? It is possible to print a grayscale image by printing multiple times at a lower temperature and then feeding the paper.

The firmware that has been reversed for a long time has not come out to pick up something. It is really a dish. I hope that I can tell me a little about my life experience.

By the way, two chip models are lost: `NUC123LD4BN0`, `STM32F071CBU6`, which seems to be Cortex-M0.

PS: This code is for non-profit use only. For commercial use, please also use Gaoming.
