1.What is the name of the HTTP server software running on port 80?
I did a scan, this is a version of software running on port 80: nostromo, i've never see this before also in this lab i will learn something new, this drop me also on my terminal some HTML.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/ee54967a-c58d-40e8-9b08-f027872b51c0)

2.As which user you can get code execution through Nostromo?
I first what i did is check on metasploit is there can be something intresting about this version, and i found some exploit.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/db3f89d3-31b7-46ba-a6c7-62fd1ff95860)

I insert LHOST and RHOST and run this exploit and i got a shell, now i need to do some recon to find user that can get code execution. After when i got a shell write in terminal id and here is the results:
![obraz](https://github.com/Anogota/Traverxec/assets/143951834/45b8473b-7796-4f16-b939-63d6ac612b07)
The answer is www-data 
