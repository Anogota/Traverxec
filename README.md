1.What is the name of the HTTP server software running on port 80?
I did a scan, this is a version of software running on port 80: nostromo, i've never see this before also in this lab i will learn something new, this drop me also on my terminal some HTML.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/ee54967a-c58d-40e8-9b08-f027872b51c0)

2.As which user you can get code execution through Nostromo?
I first what i did is check on metasploit is there can be something intresting about this version, and i found some exploit.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/db3f89d3-31b7-46ba-a6c7-62fd1ff95860)

I insert LHOST and RHOST and run this exploit and i got a shell, now i need to do some recon to find user that can get code execution. After when i got a shell write in terminal id and here is the results:
![obraz](https://github.com/Anogota/Traverxec/assets/143951834/45b8473b-7796-4f16-b939-63d6ac612b07)
The answer is www-data.

I use python better shell, to get a better shell :P This shell is mutch clear
python -c 'import pty; pty.spawn("/bin/bash")'

3.What is full path to the backup archive that contains an SSH key for the david user?
I foud intresting directory /var/nostromo/conf and here is the file nhttpd.conf, i cat this file and i saw intressting path 

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/f8313a2a-9096-4776-80f7-c8a577c3f59c)

i try to use this on david because when i try acces or ls david directory i see "Permission denied" maybe with this path we can bypass this. And i was right i bypass this Permission denied.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/5bc89aa7-bc0c-404d-891d-05ec52cdf840)

When we know full path for SSH key, now we need to figure out how to download this i found something intresting in /var/nostromo/conf there is .htpasswd and we cen see there this:

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/ed0c8af2-b734-439d-b714-00c9466464fe)

After quick recon i know this hash is md5crypt hash, i use hashcat to crack this hash, here is the resoult:Nowonly4me
