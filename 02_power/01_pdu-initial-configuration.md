# TrippLite PDU Initial Configuration

## Preparation

*   Installed four TrippLite PDUMNV30HV PDU's, two each in the "A"
    and "B" enclosures, and cross-wired them to the "A" and "B"
    UPS's, e.g.:
    
        PDU-1A-A = PDU in enclosure 1A, connected to UPS-1A
        PDU-1A-B = PDU in enclosure 1A, connected to UPS-1B
        
        PDU-1B-A = PDU in enclosure 1B, connected to UPS-1A
        PDU-1B-B = PDU in enclosure 1B, connected to UPS-1B
        
    The goal was to establish "A" and "B" PDUs on each side of
    the LCU, so all equipment installed in an enclosure could
    be connected to both "A" and "B" UPS's.
    
*   Verified that we could connect via serial cable from a laptop
    serial port to the PDU's serial management ports, using appropriate 
    terminal software (e.g., Putty), with the following settings:
    
        Bits Per Second:  **9600**
        Data Bits:        **8**
        Parity:           **None**
        Stop Bits:        **1**
        Flow Control:     **None**

*   Connected ethernet cables from the PDU network management ports
    to the out-of-band management switch.

## Procedure

The following procedure was performed on the PDU-1A-A PDU, and then
duplicated on the other three devices (PDU-1A-B, PDU-1B-A, PDU-1B-B),
with appropriate adjustments (e.g. to IP address, device name, etc.).

### Initial configuration via serial port.

*   Rebooted the interface by pushing the reset pin on the PDU.

*   Once the initialization page appeared in the console window, 
    pressed any key to interrupt the initialization sequence.

*   Pressed "M" to modify settings.

*   When prompted, entered the default root password ("TrippLite").

*   Answered prompts as follows:

        Reset configuration and root password to default values? **N**
        Obtain IPv4 settings automatically using DHCP for Ethernet interface? **N**
        IP Address? **10.130.143.135**
        Subnet mask? **255.255.255.128**
        Gateway Address? **10.130.143.129**
        Enable DHCPv6 for the Ethernet interface? **N**
        Enable static IPv6 for the Ethernet interface? **N**
        DNS Server? **150.135.238.4**
        This card’s host name? **PDU-1A-A**
        This card’s domain? **library.arizona.edu**
        Enable SNTP? **Y**
        Enable FTP? **N**
        Port number? **21**
        Enable HTTP? **N**
        Port number? **80**
        Enable HTTPS? **N**
        Port number? **443**
        Enable Telnet Menu? **N**
        Port number? **23**
        Enable Telnet Programs? **N**
        Port number? **5214**
        Enable SSH Menu? **Y**
        Port number? **22**
        Enable SSH Programs? **N**
        Port Number? **2112**
        Enable SNMP? **Y**
        Port number? **161**
        Enable SNMPv1? **Y**
        Enable SNMPv2c? **Y**
        Enable SNMPv3? **Y**
        Do you wish to modify the network watchdog configuration? **N**
        Would you like to update the RTC date/time in GMT? **N**
        Time Zone in 30 minute intervals, +/-HH:MM: **-07:00**
        Do you wish to configure the advanced settings? **N**
        Would you like to update the Root Password? **Y**
        
            *(set and confirmed the new root password)*
        
        Do you wish to modify the users? **N**
        Do you wish to modify the auth and accounting method? **N**
        Do you wish to modify the radius hosts table? **N**
        Erase the server private key passphrase? **Y**
        
            *(set and confirmed the server private key passphrase)*
            
        Erase the client private key passphrase? **Y**
        
            *(set and confirmed the client private key passphrase)*
            
        How long (in seconds) should CPU delay before starting up? **5**

*   Disconnected from the serial port.

### Secondary configuration via management port.

*   Confirmed that it was possible to connect via SSH and the out-of-band
    management subnet to the newly-set IP using the default username and
    password:
    
        Username: **localadmin**
        Password: **localadmin**
        
*   Navigated the menu prompts to set the following information:

    *   Devices -> Identification ->

            Device Name:  **PDU-1A-A**
            Location:     **LCU1**
            Region:       **UA LIBRARIES**
        
    *   System Configuration -> Address Book -> Email Contacts
    
            Name:   **Library Ops LCU Distribution List**
            Email:  **LBRY-OPS-LCU@distribution.arizona.edu**
            
    *   System Configuration -> Security -> Local Users
    
            (set new passwords and auth passwords for each of the five default users)

    *   System Configuration -> Date/Time -> Time Settings
    
            Timezone Offset:              **-07:00**
            Using Daylight Savings Time:  **No**
            
    *   System Configuration -> Date/Time -> NTP Settings

            Update Interval:    **360**
            Primary Address:    **0.pool.ntp.arizona.edu**
            Primary Port:       **123**
            Secondary Address:  **1.pool.ntp.arizona.edu**
            Secondary Port:     **123**
    
    *   System Configuration -> Date/Time -> Time Source -> Switch To NTP

    *   (Note: session terminated upon applying the above changes and
         re-syncing; logged back in and verified settings and system time.)

### End procedure.
