# Network-Commands and Creating Custom Command

# Linux Network Commands


| Command       | Description                                              | Example |
|---------------|----------------------------------------------------------|-------------------------------------------------|
| ifconfig      | Displays the configuration of all active network interfaces on the system including IP addresses, MAC addresses, and more. | ![carbon (2)](https://github.com/gunduzl/Network-Commands/assets/69585166/4fc12585-2e2f-4c44-a916-367c1bbde1ad) |
| ip            | The ip command is a more comprehensive and modern alternative to ifconfig for network configuration and management in Unix-like systems. It offers extensive functionality including address management, routing, device manipulation, policy routing, and tunnel configuration.  | ![carbon (3)](https://github.com/gunduzl/Network-Commands/assets/69585166/1a8f179a-6f40-4608-bc56-dad6734833ba) |
| ping          | Tests connectivity between two hosts by sending ICMP echo requests and waiting for ICMP echo replies. | ![carbon (4)](https://github.com/gunduzl/Network-Commands/assets/69585166/f22106c1-7967-4901-acfa-f5116b478bcc) |
| traceroute    | Displays the route that packets take to reach a destination by sending packets with increasing TTL values and analyzing the responses. | ![carbon (5)](https://github.com/gunduzl/Network-Commands/assets/69585166/ffcd4094-c86b-4e11-b56f-127c6d19e7bb) |
| netstat       | Displays various network-related information such as active network connections, routing tables, interface statistics, etc. | ![carbon (6)](https://github.com/gunduzl/Network-Commands/assets/69585166/92c0b4ff-28c0-45d2-a428-1d53d187fa36) |
| nslookup      | Performs DNS lookup to retrieve domain name or IP address information from DNS servers. | ![carbon (8)](https://github.com/gunduzl/Network-Commands/assets/69585166/e912026c-58dc-4ea6-ba20-e995890b7e8a) |
| dig           | Another DNS lookup utility that provides more detailed information about DNS records and server responses. | ![carbon (9)](https://github.com/gunduzl/Network-Commands/assets/69585166/db725470-22be-4f90-8e88-0f5c9081f98c) |
| hostname      | Displays or sets the hostname of the system.             | ![carbon (10)](https://github.com/gunduzl/Network-Commands/assets/69585166/b91a1358-0700-466d-9418-a2a7f65e5146) |
| route         | Displays or modifies the IP routing table, including adding or deleting routes.  It allows users to add, delete, or modify routes in the routing table, which determines how network packets are forwarded to their destinations. | ![carbon(11)](https://github.com/gunduzl/Network-Commands/assets/69585166/99dcc440-8165-4cc7-907c-fbbdec43192e) |
| networksetup      | The networksetup command allows you to configure network settings, such as network interfaces, IP addresses, DNS servers, and more. | ![carbon](https://github.com/gunduzl/Network-Commands/assets/69585166/79f9ce03-3a07-4746-8ae0-3eff72ad2ded) |
| arp           | Displays and modifies the ARP cache, which maps IP addresses to MAC addresses. To list IP addresses, MAC addresses, flags, and interfaces associated with each entry in the ARP cache, you can use the arp -a command.| ![carbon (6)](https://github.com/gunduzl/Network-Commands/assets/69585166/c0bc464b-70ab-4c7e-b6cb-c52195a3b4df) |
| sshd          | The SSH daemon responsible for allowing secure remote login and command execution. | <!-- Add any additional notes here if needed --> |
| scp           | Securely copies files between hosts over an SSH connection. | <!-- Add any additional notes here if needed --> |
| ssh-keygen    | Used to generate SSH key pairs for secure authentication without passwords. | ![carbon (1)](https://github.com/gunduzl/Network-Commands/assets/69585166/20c8fe37-5446-4e04-a7a1-da5b9a05ab33) |
| iptables      | A powerful firewall utility for configuring packet filtering, NAT, and other network-related rules. In macOS, the equivalent of iptables in Linux is the pfctl command, which interacts with the Packet Filter firewall, also known as PF. PF is a versatile firewall included with macOS that allows you to define rules for packet filtering, NAT (Network Address Translation), and more. | ![carbon (2)](https://github.com/gunduzl/Network-Commands/assets/69585166/eb10a1d6-b244-4bee-9904-2ebc71a47031) |
| tcpdump       | A packet analyzer that captures and displays network packets in real-time for troubleshooting or analysis. | ![carbon (3)](https://github.com/gunduzl/Network-Commands/assets/69585166/9b9ef189-6189-4a06-9ab0-b50492d29c4e) |
| nc            | Netcat, a networking utility used for reading from and writing to network connections using TCP or UDP. | ![carbon (5)](https://github.com/gunduzl/Network-Commands/assets/69585166/e6e582be-b9ae-4174-93dc-4b69814a0a66) ![carbon (4)](https://github.com/gunduzl/Network-Commands/assets/69585166/c8b7a6f4-a8ad-4568-bb84-f03c4007b7b5) |
| nmap          | A powerful network scanner used for discovering hosts and services on a network. | <!-- Add any additional notes here if needed --> |
| iftop         | A command-line tool that displays bandwidth usage on an interface by host. | <!-- Add any additional notes here if needed --> |
| mtr           | Combines the functionality of ping and traceroute, providing both network latency and path information. | <!-- Add any additional notes here if needed --> |
| curl          | A command-line tool used to transfer data to or from a server, supporting various protocols including HTTP, HTTPS, FTP, etc. | ![carbon (7)](https://github.com/gunduzl/Network-Commands/assets/69585166/e6262f16-6ad4-42cc-8374-9709471d6d4e) |
| wget          | Another command-line tool for downloading files from the internet using HTTP, HTTPS, or FTP protocols. | <!-- Add any additional notes here if needed --> |







## Creating Custom Command 



1. **Create Bash File**:

   Assuming you're in the directory where your updated script is located. Create a bash file. I will create a network.sh file

      ```bash
   nano network.sh
   ```
   In this example. I will combine 3 networking commands `ping` `traceroute` `nslookup`. So I will put that into my network.sh

      ```bash
      #!/bin/bash
   
   # Check if a domain is provided
   if [ -z "$1" ]; then
       echo "Usage: $0 <domain>"
       exit 1
   fi
   
   domain="$1"
   
   # Perform the ping
   echo "Performing ping for $domain"
   ping -c 5 "$domain"
   echo -e "\nPing command completed\n"
   
   # Perform the traceroute
   echo "Performing traceroute for $domain"
   traceroute "$domain"
   echo -e "\nTraceroute command completed\n"
   
   # Perform the nslookup
   echo "Performing nslookup for $domain"
   nslookup "$domain"
   echo -e "\nNslookup command completed\n"

      echo -e "\nAll Commands Have Been Executed\n"
   ```
   

3. **Remove the Old Script (if needed)**:

   If there's already an older version of your script in the `/usr/local/bin` directory, you may want to remove it. Run the following command:

   ```bash
   sudo rm /usr/local/bin/network
   ```

4. **Move the Updated Script**:

   Move your updated script (`network.sh` in this case) to the `/usr/local/bin` directory using the following command:

   ```bash
   sudo mv network.sh /usr/local/bin/network
   ```

5. **Set Execution Permission (if needed)**:

   If the script doesn't have execution permission, grant it using the following command:

   ```bash
   sudo chmod +x /usr/local/bin/network
   ```


Once you've completed these steps, your custom command `network` should be updated and ready to use.


![carbon12](https://github.com/gunduzl/Network-Commands/assets/69585166/da8b8110-b7a9-4ba1-90d5-3ac082203c71)



