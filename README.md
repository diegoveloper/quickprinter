# Quick Printer
## Android POS Printer (ESC/POS)
> Created for the purpose of serving as a channel among other applications that require printing data on receipt printers using ESC/POS commands.

## Introduction
Quick printer is an Android application that allows you to add and configure receipt printers (POS printers) through different connection types:
- Red Wifi
- Bluetooth
- USB (OTG)

The most important thing is that it allows you to print the text you share from any application, so you can print your favorite texts.

And if you're a developer, you can integrate your application in a super simple way so you can print tickets, receipts, etc.

> The application supports many types of thermal and matrix printers such as EPSON, BIXOLON, STAR MICRONICS, CITIZEN, etc.


## Usage
The steps for using the application will be detailed below:

###__1. Download Quick Printer from the playstore [here](https://play.google.com/store/apps/details?id=pe.diegoveloper.printerserverapp "Quick Printer")__
    
  <center><img src="http://www.qr-code-generator.com/phpqrcode/getCode.php?cht=qr&chl=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dpe.diegoveloper.printerserverapp&chs=180x180&choe=UTF-8&chld=L|0" width="200"></center>     
    Configure your printers using the Tutorial inside de app.
  
###__2. Share Text from any application installed__  
    When the application selection dialog appears, select 'Quick Printer'.  
    The selected text will be printed on your previously configured printer.


## Developers

If you are a developer and want to integrate your Android application with 'Quick Printer', read the following instructions.:

* ###Using Sharing Intents 

  You can share plain text using shared Intents with the appropriate commands, below the simplest example.  
```java
        String textToPrint = "Your text here";
        Intent intent = new Intent();  
        intent.setAction(android.content.Intent.ACTION_SEND);  
        intent.setType("text/plain");  
        intent.putExtra(android.content.Intent.EXTRA_TEXT,textToPrint);  
        startActivity(intent);  
```
     When the selection dialog appears, select 'Quick Printer'.  
 
  
  
  
  






