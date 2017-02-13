
# Using GPS on a Raspberry Pi

# Goals
- Install a GPS (gpsd) on a Raspberry Pi 3
- Succesfully test and capture GPS data
<br/><br/>
<div class="paragraphs">
  <div class="row">
    <div class="col-md-4">
      <div class="content-heading clearfix media">
           <img class="pull-left" src="http://res.cloudinary.com/bizicloud/image/upload/c_scale,h_250/a_0/v1479058388/sf-life/globalsat-bu-353-s4.jpg"/>
      </div>
    </div>
  </div>
</div>

# Details GPS device
- Brand is USGlobalSat
- Model name is "BU-353S4 USB GPS Receiver"
- <a href="http://usglobalsat.com/p-688-bu-353-s4.aspx#images/product/large/688.jpg" target = "_blank">Company's product link</a>

# Which Raspberry Pi can I use?
- I've succesfully installed and used the BU-353S4 GPS receiver on both the Pi 2 and Pi 3
- The image I'm currently using is Raspbian Jessie released on 9/23/2016, which is kernal version is 4.4

# Before getting started
- Make sure to be in a location that has lots of open visibility to the sky and close to a window. Otherwise you might not be able to lock in coordinates with satelites. 
- I'm assuming you already know the basics of using the Raspberry Pi, including being comfortable with navigation on command line (at least the basics)
- All necessary updates on the Raspian image have been performed
- Accessories like a keyboard, mouse, monitor, and/or running Raspbian on a virtual environment are already taken care of

# Step 1
- Before powering on the Raspberry Pi, plug in the GPS receiver into one of the USB ports. It doesn't matter which port.  
<br/>
<div class="paragraphs">
  <div class="row">
    <div class="col-md-4">
      <div class="content-heading clearfix media">
           <img class="pull-left" src="http://res.cloudinary.com/bizicloud/image/upload/c_scale,h_250/v1479060212/sf-life/plug-gps-into-usb.jpg"/>
      </div>
    </div>
  </div>
</div>

# Step 2
- Power on the Raspberry Pi

# Step 3
- Open up the terminal
- Type in "sudo apt-get update" and hit ENTER
- Let's now double check to make sure the GPS receiver is being recognized on one of the ports.  
    - Type in "sudo lsusb"
    - You should hopefully see the USB adapter (Prolific Technology, Inc. PL2303)

# Step 4
- Type in "sudo nano /etc/default/gpsd" and hit ENTER
- Once the file is displayed make sure all details match EXACTLY with the lines shown below.
<br/><br/>
START_DAEMON="true"
<br/>
GPSD_OPTIONS="n"
<br/>
DEVICES="/dev/ttyUSB0"
<br/>
USBAUTO="false"
<br/>
GPSD_SOCET="/var/run/gpsd.sock"
<br/><br/>
- Save it, then type in "sudo /etc/init.d/gpsd restart"

# Step 5
- Now that the installation and setup are complete, let's take a look at the little red light on the GPS receiver.
- Do you see the red light blinking? 
    - If so, that means you have succesfully locked in coordinates. 
    - Please move on to Step 6.  If not, continue with Step 5.
- Why is the red light not blinking? 
    - That means coordinates have not yet been locked in with Satellites. If this is your first time using the GPS receiver, it could take several minutes. Then, going forward it's usually pretty fast. 
    - If after several minutes the red light is not blinking I would recommend moving to another spot that has lots of visibility to the sky, possibly even outside.  

# Step 6
- If you've made it this far you're close!!  
- Type in "cgps -s" and hit ENTER
- Within a few seconds you should see some numbers popping up and changing. If so, you're now ready to capture GPS coordinates on the Raspberry Pi!


```python

```
