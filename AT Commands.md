![](https://i.imgur.com/cZ0uokP.png)

```shell 
# Sim related
AT+QUIMSlOT?  	# -> Check sim slot
AT+QUIMSLOT=1	# -> Swtich Sim Slot to 1

# Changing network modes
AT+QNWPREFCFG="mode_pref",NR5G		# -> Force to 5G standalone, meaning no fall back to 4G
AT+QNWPREFCFG="mode_pref",AUTO		# -> Switches networks based on signal quality and service availability, meaning can fall back to 4G etc
AT+QNWPREFCFG="nr5g_disable_mode",0	# -> Enable for 5G SA and NSA
AT+QNWPREFCFG="nr5g_disable_mode",2	# -> Disable 5G NSA Mode

# Checking network status
AT+QENG="servingcell"

# Switching USB network interface mode 
AT+QCFG="usbnet",1	# -> Switches to ECM mode uses USB interface
AT+QCFG="usbnet",2 	# -> Switches to MBIM mode uses wwan interface

# Save and reboot
AT+CFUN=1,1		# -> CFUN=1 full functionality, ,1 indicates reboot after saving

# Query IP address 
AT+CGPADDR=1	# -> Only gives IP
AT+CGCONTRDP	# -> Gives IP + More information

# Query Network Info
AT+QNWINFO 

# Set up 5G Frequency bands
AT+QNWPREFCFG="nr5g_band",77:78

# Check current network operator status
AT+COPS?

# Check Signal Strength (dBm) and bit error rate
AT+CSQ	# -> dBm range is 0 - 31 (strongest) and bit error is (no error) 0 -> 99 (error rate is unknown)
```

>[!note]
><h3>What is MBIM (Mobile Broadband Interface Model)?</h3>
>Used for faster data connections and broader compatibility, especially with Windows systems.

>[!note]
><h3>What is ECM (Ethernet Control Model)</h3>
>It emulates an Ethernet connection over a USB connection, making the modem appear as a network interface to the OpenWRT device. ECM is limited in functionality compared to MBIM and QMI and typically only provides basic internet connectivity without additional features like SMS or signal monitoring. While ECM may work with a wider range of modems due to its simplicity, it lacks the advanced capabilities of MBIM and QMI.

>[!note]
><h3>What is QMI (Qualcomm MSM Interface)</h3>
>QMI is a protocol developed by Qualcomm primarily for their cellular chipsets. It is often used in devices that have Qualcomm-based modems, such as certain smartphones, routers, and embedded systems. QMI offers a comprehensive set of standardised messages for controlling and configuring the modem, including data, voice, and GPS services. It provides more advanced features and better performance compared to ECM, especially on Qualcomm-based devices.

