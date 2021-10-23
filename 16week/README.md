## Week 16 Homework Submission File: Penetration Testing 1

#### Step 1: Google Dorking


- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is: 
<br>

`The Chief Executive Officer of Altoro Mutual is Karl Fitzgeral.`

- How can this information be helpful to an attacker: <br>

`This information is helpful to the attacker because they can use a whaling attack to get access to the CEO's information.`

![picture](\images\01.PNG)


#### Step 2: DNS and Domain Discovery

Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results: <br>

![picture](.\images\02.PNG)

![picture](.\images\03.PNG)

  1. Where is the company located: 
  
         Sunnyvale, CA 
  

  ![picture](.\images\04.PNG) <br>


  2. What is the NetRange IP address: 
   
          65.61.137.64 - 65.61.137.127 

![picture](.\images\05.PNG) 



  3. What is the company they use to store their infrastructure:

          The company being used is called Rackspace Technology

  https://www.rackspace.com/


  4. What is the IP address of the DNS server: 

        	65.61.137.117

![picture](.\images\06.PNG) 

#### Step 3: Shodan

- What open ports and running services did Shodan find:

      port 80, 443, 8080 

![picture](.\images\07.PNG) 



#### Step 4: Recon-ng

- Install the Recon module `xssed`. 

![picture](.\images\08.PNG) 


- Set the source to `demo.testfire.net`. 

![picture](.\images\09.PNG) 


- Run the module. 

![picture](.\images\10.PNG) 

Is Altoro Mutual vulnerable to XSS: Yes

![picture](.\images\11.PNG) 

### Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

- Command for Zenmap to run a service scan against the Metasploitable machine: 
<br>

      -A = Aggressive
      -O = Operating System detection
      -sV = enables services and version detection
      -v = Verbose
      -192.168.0.10 = metasploitable IP

 
- Bonus command to output results into a new text file named `zenmapscan.txt`:


      -nmap -sV -O -T3 -A -v -oN zenmapscan.txt 192.168.0.10 


- Zenmap vulnerability script command: 

![picture](.\images\13.PNG) 

- Once you have identified this vulnerability, answer the following questions for your client:
  1. What is the vulnerability:

        - 192.168.0.10 is vulnerable to FTP attacks
        - this server is vulnerable to ftp-vsftpd-backdoor 
        - tmp fileshare allows anyone to read and write access


  2. Why is it dangerous: <br>


            This is dangerous because the hacker can gain access to the server and install malicious codes. 

  3. What mitigation strategies can you recommendations for the client to protect their server: <br>

      -update software 
      -install firewall
      -install antivirus
      -secure network
      -have 2 step authentication 

![picture](.\images\12.PNG) 


---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  

