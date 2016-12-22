# Quick Printer
## Android POS Printer (ESC/POS)
> Created for the purpose of serving as a channel among other applications that require printing data on receipt printers using ESC/POS commands.

## __Introduction__
Quick printer is an Android application that allows you to add and configure receipt printers (POS printers) through different connection types:
- Wifi local network
- Bluetooth
- USB (OTG)

The most important thing is that it allows you to print the text you share from any application, so you can print your favorite texts.

And if you're a developer, you can integrate your application in a super simple way so you can print tickets, receipts, etc.

> The application supports many types of thermal and matrix printers such as EPSON, BIXOLON, STAR MICRONICS, CITIZEN, etc.


## __Usage__
The steps for using the application will be detailed below:

###__1. Download Quick Printer from the playstore [here](https://play.google.com/store/apps/details?id=pe.diegoveloper.printerserverapp "Quick Printer")__
    
  <center><img src="http://www.qr-code-generator.com/phpqrcode/getCode.php?cht=qr&chl=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dpe.diegoveloper.printerserverapp&chs=180x180&choe=UTF-8&chld=L|0" width="200"></center>     
    Configure your printers using the Tutorial inside de app.
  
###__2. Share Text from any application installed__  
    When the application selection dialog appears, select 'Quick Printer'.  
    The selected text will be printed on your previously configured printer.


## __Developers__
If you are a developer and want to integrate your Android application with 'Quick Printer', read the following instructions:

* ### Using Sharing Intents
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

* ### Using Sharing Intents with commands
You can specify different printer commands in your sharing text to take advantage of your printer. This is an example of how to use the commands. 
 ```java  

        String textToPrint = "<BIG>Text Title<BR>Testing <BIG>BIG<BR><BIG><BOLD>" +
                "string <SMALL> text<BR><LEFT>Left aligned<BR><CENTER>" +
                "Center aligned<BR><UNDERLINE>underline text<BR><QR>12345678<BR>" +
                "<CENTER>QR: 12345678<BR>Line<BR><LINE><BR>Double Line<BR><DLINE><BR><CUT>";  
        Intent intent = new Intent();  
        intent.setAction(android.content.Intent.ACTION_SEND);  
        intent.setType("text/plain");  
        intent.putExtra(android.content.Intent.EXTRA_TEXT,textToPrint);  
        startActivity(intent);  
 ```  
 These commands generate this ticket    
 <img src="https://raw.githubusercontent.com/diegoveloper/quickprinter/master/receipt_ticket.jpg" width="300"/> 
 ### __Commands supported__
 
 | Command  | Description|
 | ------------ |------------------------------------| 
 |`<BR>`       |  breakline|
 |`<SMALL>`       |  normal text size|
 |`<BIG>`       | big text size
 |`<BOLD>` | bold text
 |`<LEFT>`| text aligned to the left
 |`<CENTER>`| text aligned to center
 |`<UNDERLINE>` | text with underline
 |`<NORMAL>` | turn off bold and underline
 |`<LINE>`| A single line of text
 |`<DLINE>`| Double line of text
 |`<CUT>`| Cut the paper
 |`<LOGO>`| Print the logo configured on your printer
 |`<INVERSE>`| Turn on white/black reverse mode
 |`<DRAWER>` | Open the cash drawer connected to the printer
 |`<QR>your text` | Print a QR code of your text(premium feature)
 
* ### Getting the print result
If you want to get the printing result you should use  startActivityForResult instead of startActivity, below is the sample code
 ```java  
        Intent intent = new Intent();
        intent.setAction(android.content.Intent.ACTION_SEND);
        intent.setType("text/plain");
        intent.putExtra(android.content.Intent.EXTRA_TEXT,"your text to print here");
        startActivityForResult(intent,YOUR_REQUEST_CODE);  
        
           @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
       // super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == YOUR_REQUEST_CODE){
            if (resultCode == RESULT_OK){
                //Printing is ok
            } else {
                if (data != null) {
                    String errorMessage = data.getStringExtra("errorMessage");  
                    //Printing with error
                }
            }
        }
    }
 ``` 
  
* ### Printing on a specific printer by alias
If you want to send the data to a specific printer (replacing printer selection), You can do following the snippet code 
 ```java  
        String data = "<PRINTER alias='your_printer_alias'> YOUR CUSTOM DATA <BR><CUT>"; 
        Intent intent = new Intent();
        intent.setAction(android.content.Intent.ACTION_SEND);
        intent.setType("text/plain");
        intent.putExtra(android.content.Intent.EXTRA_TEXT,data);
        startActivityForResult(intent,YOUR_REQUEST_CODE);  
  ``` 
 
* ### Advance options (Premium features)
If you are suscribed to the 'Quick Printer' application, you can use this advanced options
 ```java  
        Intent intent = new Intent();
        intent.setAction(android.content.Intent.ACTION_SEND);
        intent.setType("text/plain");
        intent.putExtra(android.content.Intent.EXTRA_TEXT,etPrinterText.getText().toString());
        //premium features
        intent.putExtra("config_error_dialog",false); 
        intent.putExtra("config_color_background_dialog","#0000ff");
        intent.putExtra("config_color_text_dialog","#00ff00");
        intent.putExtra("config_text_dialog","Loading...");
        startActivityForResult(intent,YOUR_REQUEST_CODE);
 ```
 | Option  | Value|Description|
 | ------------ |------------------------------------|------------------------------------|
 |config_error_dialog       |  (true/false)| Default value is 'true', you can send 'false' if you don't want the 'Quick Printer' app handle the error if exists|
 |config_color_background_dialog       |  Color in hexadecimal| Background color of the Printing dialog|
 |config_color_text_dialog       | Color in hexadecimal| Text color of the Printing dialog|
 |config_text_dialog | Text | Text of the Printing dialog| 
 
 __NOTE__: 'QR' command and these options are only availables for Premium Version. Free version print a message at the end of the ticket. 

* ### Integrate Printer Driver directly in your code
 'Quick Printer' is an app that is using a library developed by me. If you want integrate the library directly in your project, please [contact me](mailto:diegoveloper@gmail.com). 
 
## __Contact me__
 __Diego Velásquez López__ 
 
 Mobile Developer expert from Peru, author of the 'Quick Printer' and the library used by the app.   
 [diegoveloper@gmail.com](mailto:diegoveloper@gmail.com)  
  
 
  






