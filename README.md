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
And i found this, here we need this credentials

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/dfb12c91-83ff-40b1-b97c-1fb4124f0171)

also on this website we can find SSH key

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/9c968a47-04f1-43e7-b7a1-ebf2326f777b)

i download this key.
To extract or untar the file to the current directory, type the following, (Making sure to replace file_name.tar with the actual filename) tar -xvf file_name.tar.
![obraz](https://github.com/Anogota/Traverxec/assets/143951834/e4b38713-899e-4c39-813a-e90079de2d02)

How we must to crack this key i recomend to use johntheripper, this tool is simply and fast

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/2057e5b6-cbee-46b0-ab23-f94b151f3f7f)

With ssh2john u will replace this key into the hash, and now you can crak it.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/e8be65bf-4af9-4543-8b82-20898d11dd1d)

When i try use john i encountered weird problem, if u will have the same, how i have you will be know how to solve this problem

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/2c02968f-efc6-4180-b539-b25741d05568)

first u must login as root, and write in terminal: rm /home/kali/.john/john.rec  And the problem solved, now u can normaly use ur johntheripper.
Now we need log in to SSH
But before this i got again some error

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/ff3f5260-0864-491d-8a98-4ef24bf87d60)

If u can't connect to SSH try this command: sudo ifconfig tun0 mtu 1200  This help and now i can connect to SSH.

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/17257760-051b-4911-b5d2-206884ca0171)
![obraz](https://github.com/Anogota/Traverxec/assets/143951834/640fd00a-1b43-4d02-b5aa-4a9af3ecdc99)

4.What is the name of the binary that david can run as root without a password?
i can't use command sudo -l to check it but i look around i found this

![obraz](https://github.com/Anogota/Traverxec/assets/143951834/dbe67134-f05d-4fe5-9d75-4bd3394bc8aa)

5.What is the default pager that gets invoked when journalctl has more lines of output than will fit on the current terminal?

