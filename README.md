# Tools
Pentest tools used in industry

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

### Explaination:

Notebook Github: https://github.com/mxrch/penglab

+ In Google colab basically you can create notebooks, which is nothing but blocks of code which you can also share with others and other people can directly use 
  that code by simply just clicking Run it.
+ This notebook install **JOhn-The_Ripper, Hashcat, and Hydra** and fetch **Rockyou.txt** wordlist and you can use those tools easily in your workflow.
+ It has many more functionalities check it out.


