I made a Digital Forensics CTF task named Micro:\
![challenge](images/image_2023-06-25_122238238.png)
It is a .raw memory dump file so we will be analyzing it using volatility: \
![profile](images/image_2023-06-25_122651391.png)
The profile we will be using is Win7SP1x64 \
We will first be proceeding with a filescan and see what the desktop holds for us:\
We have two files that seemed to be interesting:\
![desktop filescan](images/image_2023-06-25_123012529.png)
![filescan2](images/image_2023-06-25_123154888.png)
Let's first download the two files and see what we have: \
![img](images/image_2023-06-25_123317980.png)
![img](images/image_2023-06-25_123535668.png)
We first unrar the confidential.rar file and we get this confidential.txt:\
![img](images/image_2023-06-25_123727203.png)
This does not do us much right now, so let's go ahead and take a look at doc.docm file, which judging by the extension is a macro-enabled word document: \
![img](images/image_2023-06-25_123855033.png)
But since this is a macro-enabled file, let's take a look at the macros:\
![img](images/image_2023-06-25_124008759.png)
![img](images/image_2023-06-25_124051394.png)
We can see that we have some python code running inside the macro, so let's clean it up and see what this is:\
