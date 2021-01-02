Challenge :
``` 
My friend sent me this zip file... He is a prankster and compressed the file a LOT of times... 

I don't know how to make this go quickly and I don't have the time... At least he told me the password is "pass".

Can you please help? 
```
And they provide a zip file named 50.zip. As the challenge prompt says that it has been compressed a lot of times and the file named 50.zip that means it is zipped 50 times.
So I used a python script found online and modified it according to the challenge 

Script:
```
#!/usr/bin/env python3
import zipfile
import sys

secret = "pass"

for i in range(50, 0, -1):
  if i < 10:
    i = "0" + str(i)
  filename = str(i) + ".zip"
  sys.stdout.write("\rGetting Flag " + filename)

  with zipfile.ZipFile(filename) as file:
    file.extractall(pwd = bytes(secret, 'utf-8'))


with open("flag.txt", "r") as f:
  print("\n" + f.read())
```
Running this gave me the flag

flag:
```flag{cf97382071cb149aac8d6ab8baeaa3ee}```
