# Tools
Pentest tools used in industry that i didn't knew about

## 1. Flask-Unsign: A tool to forge flask session cookies

  ![forge](https://user-images.githubusercontent.com/79413473/148261669-55f80735-64e6-4d56-b1a2-43e62d2e8a8a.jpeg)


Tool Github Link:         https://github.com/Paradoxis/Flask-Unsign  

Author's official blog:   https://blog.paradoxis.nl/defeating-flasks-session-management-65706ba9d3ce

+ While reading [this blog](https://adithyanak.medium.com/how-i-cracked-secarmys-oscp-challenge-5a96e429e105), i had a callback that while solving a HTB box
  i have seen this before but never tried it. So here it is.
+ This tool can be used to manipulate stateless cookies, like FLask's session management and JWTs are not encrypted rather they are signed which means they are
  are easily readable and manipulable as long as secret is **somehow known**. 
+ Server accepts the data hash it with a secret and verify the signature it recevied against the signature it produced by hashing.If they match server allows the 
  user to perform action, else not.
+ flask-unsign one such tool which can get the cookie and try to guess the secret which have been used to sign the cookie using a wordlist.
+ You can use either your own wordlist or creator's common secret keys used scrapped from github and stackoverflow.


### Installation
+ `pip3 install flask-unsign`
    or 
+ `pip3 install flask-unsign[wordlist]` to install default wordlist along with tool.

 Rest refer to official github link or run `flask-unsin -h` for it's usage synatx.
 
 *A google search `flask-unsign ctf` will give you lot of writeups how this have been used in ctfs to forge cookies.*
 
 
## 2. Faster hashe cracking using Google colab(GPUs):

  ![image](https://user-images.githubusercontent.com/79413473/150385576-127beaa4-35ce-4d6b-a031-ffbb61664f6b.png)

while browsing youtube today i found this great video by **superhero1** about using Google Colab for cracking hashes and i was like wow that's awesome why didn't i 
think about utilising colab's GPU for cracking hashes, as my laptop is not that strong so i always struggle with cracking paswords during CTFs.

Video with great explaination by legend himself : https://www.youtube.com/watch?v=5pd9n4BTYp0

+ Notebook Link: https://colab.research.google.com/github/mxrch/penglab/blob/master/penglab.ipynb

### Explaination:

Notebook Github: https://github.com/mxrch/penglab

+ In Google colab basically you can create notebooks, which is nothing but blocks of code which you can also share with others and other people can directly use 
  that code by simply just clicking Run it.
+ This notebook install **JOhn-The_Ripper, Hashcat, and Hydra** and fetch **Rockyou.txt** wordlist and you can use those tools easily in your workflow.
+ It has many more functionalities check it out.

## 3. MongoDump Tool

 + While watching this video of ippsec https://www.youtube.com/watch?v=ahzOprfN--Y . He used a tool called **mongodump**. It's an offical tool created by mongodb creators to export data in binary format from database.
  *mongodump is a utility for creating a binary export of the contents of a database. mongodump can export data from either mongod or mongos instances; i.e. can   export data from standalone, replica set, and sharded cluster deployments*
 + It can save time in reading passwords from databse if password is unknown.
 + Tool url : https://docs.mongodb.com/database-tools/mongodump/ . You can run it from your terminal directly. 
 + `mongodump`  command will by default assume localhost and default mongodb port & no authentication is required.

## 4. DNS rebinding(not a tool but technique):

  ![image](https://user-images.githubusercontent.com/79413473/151499582-c607cde4-2b8f-49cb-87bd-fc34b1bd0455.png)

  
   **Tool Url:** https://lock.cmpxchg8b.com/rebinder.html
   **Blog:**     https://blog.compass-security.com/2021/02/the-good-old-dns-rebinding/
    
+ While reading about bypassing ssrf [blog](https://sirleeroyjenkins.medium.com/bypassing-ssrf-protection-to-exfiltrate-aws-metadata-from-larksuite-bf99a3599462) 
   this mentioned about **DNS rebinding** technique. 
+ DNS rebinding is used to bypass filter which check where a url is resolving to. So using DNS rebinding when victim make a DNS request to attcker server,already configured to use attacker's DNS server, we give it a harmless IP to connect to and connection is resolved but ttl(time to live) of this response was very short so next time it will query our dns server it respond back with internal IP which was not allowed initially.

+ Official singulairyt tool to setup using VPS: https://0x1.gitlab.io/web-security/Singularity/ 

## 5. Gopherus
*Gopher payload generator*

**Tool:** https://github.com/tarunkant/Gopherus   

**Blog:** https://spyclub.tech/2018/08/14/2018-08-14-blog-on-gopherus/

+ If we get a ssrf with gopher protocl enabled we can use this to access services like mysql,redis,smtp etc on server.
+ This tool helps to generate Payloads for different services to interact with these services and gain persistence.
+ While reading this [blog](9https://sirleeroyjenkins.medium.com/just-gopher-it-escalating-a-blind-ssrf-to-rce-for-15k-f5329a974530)  found about this tool. Itws awesome how he chained gopher and 302 redirect together.
+ There is also a tool for 302 redirecter, i knew about it but never use i write my own 302 redirect using php file `header("Location: http://internal-service.com)` with apache or ngrok. But this tool looks promising too.

## 6. faketime
*linux tool which can be used to change time for a particular command, so instead of screwing your whole system time you can use this.*

[0xdf tweet:](https://twitter.com/0xdf_/status/1487098702779097100)
![image](https://user-images.githubusercontent.com/79413473/151674674-516d9fe3-6bb4-48fc-949d-990e09871a4c.png)


## 7. pyftpdlib : Python FTP server

While Playing HackTheBox Timing machine, i needed to spawn a temporray ftp server but only option i had was to setup vsftpd on my ubuntu machine, but then **pyftpdlib** came to rescue. This library will help you on spwaning instant ftp server also can be easily used for file transfers with anonymous login. SUper useful tool.

+ Library: [here](https://pypi.org/project/pyftpdlib/).
+ `pip install pyftpdlib` then `python3 -m pyftpdlib -h`. 

More on it on [this](https://github.com/giampaolo/pyftpdlib) repository. 

## 8. awslocal: an alternative for aws for local instances

Tool: https://github.com/localstack/awscli-local

`pip3 install awscli-local`

It saves time for typing --endopoint-url again and again.

## 9. WADComs (A resource for window AD hacking tools):

[WADcoms](https://wadcoms.github.io/) is developed by John Woodman, it like GTFOBins for AD hacking. It lists different tools you can use to enumerate, attack and gain persistence in ADenvironment. It also list syntax to use these services. You can search tools by services name or by exploit technique.

![Screenshot from 2022-05-13 14-21-29](https://user-images.githubusercontent.com/79413473/168247739-72794700-9654-49c4-b927-4f95108906d3.png)

## 10. SerializationDumper

I discovered this tool while doing Fingerprint machine from HTB and it had java deserilization vulnerability. This tool can help in decoding java serilizaed objects and recreate serializaed objects.

Check out Github Link: https://github.com/NickstaDB/SerializationDumper for usage guide.

it supports multiple formats and is essentially a helpful tool for CTFs.

## 11. Dive: Interactive Docker layer inspection tool

Tool: https://github.com/wagoodman/dive


