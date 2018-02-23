When you start the X-CTU software, you will see the following screen:

![](/img/x-ctu-startupscreen.png)

## Selecting the radio {#selectradio}

Click on the `Add devices` button in the upper left corner to add a new device. You will get the following dialog:

![](/img/x-ctu-add-radio-module.png)

> Note: you have to have your coordinator board with an XBee on top connected to your computer right now! If you plug it in when the dialog is already open, click on the button `Refresh ports`.


From the top half, select the Serial/USB port you want to use. On Linux, this should be something like `/dev/ttyUSB0`, on OSX something like `/dev/tty.usbserialAACC123`, on Windows something like `COM3`.

In the lower half of the dialog, you may want to change the baudrate. If the XBee has not been configured before (i.e. if you did **not** buy it together with a MiniBee), select `9600`. If the XBee has been used with the Sense/Stage MiniBee before (or bought with a Sense/Stage MiniBee), then select `57600`.

![](/img/x-ctu-choose-baudrate.png)

After selecting the USB port and checking the baudrate setting, click on the `Finish` button in the lower right corner. You will now get the following screen:

![](/img/x-ctu-discovering-radios.png)

In rare occasions, it cannot find the radio and asks you to reset the radio:

![](/img/x-ctu-action-required.png)

If this dialog shows up, push the button on the coordinator board that is at the edge under the XBee radio.

Once the radio has been found, you will see the following screen:

![](/img/x-ctu-select-radio-to-configure.png)

Click on the radio to see its configuration. You will get a popup screen telling you that it is updating the user interface and reading the radio settings:

![](/img/x-ctu-reading-radio-settings.png)

After that, it will show a list of settings in the right half of the screen.