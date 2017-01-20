# Dell S4048 - Initial Configuration {#dell-s4048-initial-configuration}

1. Connect with Serial Connection \(Serial Cord and Putty\) and the following settings
   1. 115200 Baud Rate
   2. No Parity
   3. 8 data bits
   4. 1 stop bit
   5. No flow control
2. Type A for “abort BMP now.”
3. Press Enter for Shell Prompt which will say
   **Dell**
   **&gt;**
4. Elevate privilege level type
   _enable_
   and press Enter twice
5. You will now see a prompt that looks like
   **Dell\#**
6. Enter CONFIGURATION mode. Type
   _configure_
   and press Enter
7. You will now see a prompt that says
   **Dell\(conf\)\#**
8. Change the hostname, if it was to be s4048-1b type:
   _hostname s4048-1b_
9. Your prompt will now say something like
   **s4048-1b\(conf\)\#**
10. Configure the Management Port IP Address
    1. Enter Interface mode for the Management Port, type:
       _interface Managementethernet 1/1_
    2. The prompt will now say something like
       **s4048-1b\(conf-if-ma-1/1\)\#**
    3. Assign an IP Address to the interface, for example type:
       _ip address 10.130.143.132/25_
    4. Enable the interface, type:
       _no shutdown_
11. Configure a Management Route
    1. Enter CONFIGURATION mode from Interface Mode, type:
       _exit_
    2. Configure the Route, for example type:
       _management route 0.0.0.0/0 10.130.143.129_
12. Configure a Username and Password
    1. Stay in CONFIGURATION mode from last step.
    2. For example type:
       _username joeadmin password joeadminpassword_
       press Enter twice.
13. Configure the Enable Password for EXEC Privilege Mode
    1. For example type:
       _enable secret joeadminssecretpassword_
14. Enable SSH and Disable Telnet
    1. Stay in CONFIGURATION mode
    2. Type:
       _ip ssh server enable_
       and press Enter twice
    3. Confirm SSH server is enabled, type:
       _do show ip ssh_
    4. Exit CONFIGURATION mode, type:
       _exit_
       and press Enter twice.
    5. Make the configurations survive a reboot, type:
       _copy running-config startup-config_
    6. Test that SSH works before disabling Telnet
    7. Enter CONFIGURATION mode, type:
       _configure_
    8. Turn off Telnet, type:
       _no ip telnet server enable_
    9. Exit CONFIGURATION mode, type:
       _exit_
       and press Enter twice.
    10. Make the configurations survive a reboot, type:
        _copy running-config startup-config_
    11. Confirm to overwrite, type:
        _yes_
    12. Exit Session, type:
        _exit_



