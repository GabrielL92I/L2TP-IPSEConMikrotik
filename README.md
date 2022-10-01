# L2TP/IPsec on Mikrotik by Gabriel Lami
Configure L2TP/IPsec on Mikrotik professionally(Site-to-Client)

1- First, we choose and create a network for the VPN clients. In this tutorial I will use `192.168.40.0/24`. Than we will create the bridge and IP Pool.
 - Creation of the bridge where the network addresses will be added. `Bridge->Create new bridge`
![l2tpbridge](https://user-images.githubusercontent.com/44748406/192971144-8406add0-0f8f-4a55-9b3a-b39c7637295a.png)
 - Creation of the network address. `IP->Addresses`
![address](https://user-images.githubusercontent.com/44748406/192971770-d5320a7f-038b-440d-b770-afe521cc6f4a.png)
 - Creation of the IP Pool. You can set a desidered addresses range depending on how many clients will connect to the VPN. `IP->Pool`
![pool](https://user-images.githubusercontent.com/44748406/192972150-329adcf5-f06a-47e4-8c10-a905a8f8ac5b.png)

2- Secondly, we have to create the firewall and NAT rule for the VPN to be able for the clients to communicate with the VPN Server.

- Creation of the firewall filter rule. `IP->Firewall->Filter Rules`
![rule](https://user-images.githubusercontent.com/44748406/192972775-3efd60a8-3daf-4ce0-9536-180262cc6de2.png)
- Creation of the NAT rule(only if you don't have this rule already). `IP->Firewall->NAT`
![NATRULE](https://user-images.githubusercontent.com/44748406/192098130-ac7b040a-7afe-4d5c-94d7-da9df854b818.png)
  
 4- Forth, we will create the L2TP server, profile and secret credentials for the user who will connect to this VPN server.
 
  - Creation of the L2TP server using IPsec pre-shared key. `PPP->Interface->L2TP Server`
![l2tpserver](https://user-images.githubusercontent.com/44748406/192973268-1b25efae-35ee-446c-91b5-f12ed98b8e73.png)

  - Creation of the profile which holds the encryption. `PPP->Profiles`
![profiles](https://user-images.githubusercontent.com/44748406/192974310-71bc6ae5-c73c-45ee-bc34-b57b7a31bb15.png)

  - Creation of the user credentials which will be used to connect to the VPN server. `PPP->Secrets`
![secret](https://user-images.githubusercontent.com/44748406/192974649-e5020074-1fa6-4044-95e1-8b2fcb6902c0.png)

 5- In this last step we will configure L2TP client to be able to connect through VPN
 
    You can do this by going into Settings->Network & internet->VPN->Add a new VPN
    
    Fill the information below:
    
    `Connection name` - Whatever name you want
    `Server name or address` - your public IP address
    `VPN Type` - L2TP/IPsec with pre-shared key
    `Pre-shared key` - Add the key you created on the L2TP Server setup on your Mikrotik
    `Type of sing-in info` - Username and password
    `Username` - Fill the username you created in Secrets
    `Password` - Fill the password you created in Secrets
    
    Click Save.
 [   ![client](https://user-images.githubusercontent.com/44748406/192976313-ddf15e26-a470-4a66-9768-0cc4fdd1ce8f.png)](https://github.com/GabrielL92I/L2TP-IPsec-on-Mikrotik/issues/1#issuecomment-1261917704)
     
     Good job, you should be now connected! If not, check the steps again because you might have done any mistake.
  ![connected](https://user-images.githubusercontent.com/44748406/192976634-7b17902e-d7ae-479d-9cc1-212b612ee9ab.png)
     
     
    - Some pro and cons
    
      Advantages:
      
      1- Secure(no major vulnerabilities)
      2- Compatibility(is widely available to various platforms by default)
      3- Configurations(easy to setup on a computer device or mobile phone)
      4- Stability(very stable and reliable connection)
      
      Disadvantages:
      
      1- Speed(less faster than OpenVPN because of the double encapsulation)
      2- Port Support(limited number of ports makes it easy for the ports to be blocked behind a firewall) 
      3- Trust(L2TP/IPSec was developed by Cisco and Microsoft, which raises questions about trust)
     
      
     Thank you.
