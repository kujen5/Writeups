I made a Digital Forensics CTF task named Micro:\
![challenge](images/image_2023-06-25_122238238.png)\
<br />
<br />
It is a .raw memory dump file so we will be analyzing it using volatility: \
![profile](images/image_2023-06-25_122651391.png)\
<br />
<br />
The profile we will be using is Win7SP1x64 \
We will first be proceeding with a filescan and see what the desktop holds for us:\
We have two files that seemed to be interesting:\
![desktop filescan](images/image_2023-06-25_123012529.png)\
<br />
<br />
![filescan2](images/image_2023-06-25_123154888.png)\
<br />
<br />
Let's first download the two files and see what we have: \
![img](images/image_2023-06-25_123317980.png)\
<br />
<br />
![img](images/image_2023-06-25_123535668.png)\
<br />
<br />
We first unrar the confidential.rar file and we get this confidential.txt:\
![img](images/image_2023-06-25_123727203.png)\
<br />
<br />
This does not do us much right now, so let's go ahead and take a look at doc.docm file, which judging by the extension is a macro-enabled word document: \
![img](images/image_2023-06-25_123855033.png)\
<br />
<br />
But since this is a macro-enabled file, let's take a look at the macros:\
![img](images/image_2023-06-25_124008759.png)\
<br />
<br />
![img](images/image_2023-06-25_124051394.png)\
<br />
<br />
We can see that we have some python code running inside the macro, so let's clean it up and see what this is:\
![img](images/image_2023-06-25_124615276.png)\
<br />
<br />
After analyzing the code, we can see that this is basically a ransomware, it is using an AES algorithm, generate a random 16 byte key which we use for encryption, then stores the key in the Software hive under the name secret-key, so let's get that key:\
![img](images/image_2023-06-25_125346199.png)\
<br />
<br />
And now we have the key and the confidential file, all we need to do now is to decrypt it, I prefer to write a decryptor script and not use tools but you may use Cyberchef: \
![img](images/image_2023-06-25_130120983.png)\
<br />
<br />
And we get our flag: \ 
Hackfest{macros_g0t_Noth1n9_on_mEEEE}
