## Hello, This is my Writeup for Emdee Five For Life Challenge From HackTheBox

There is many writeups about this challenge have already publiched but i tried to solve it with another way

### Challenge Description

this challenge needs you to md5 the text which generated with each request fast enough so you can get the flag
so we have no way to do it without a script 

while all people solving it with requests and re modules in python  
i decided to just solve it with just a grep and curl in a 3 line bash script :laughing: 

### Code
```
X=$(curl docker.hackthebox.eu:34890 --cookie "PHPSESSID=77pm7sh9047jrfo78nqo2bun46" --silent | grep -oP ">+.*?</h3>" | cut -d ">" -f 4 | cut -d "<" -f 1 )  
Y=$(echo -n $X |md5sum | cut -d " " -f 1)  
curl -d "hash=$Y" -X POST docker.hackthebox.eu:34890 --cookie "PHPSESSID=77pm7sh9047jrfo78nqo2bun46" --silent | grep -oP ">+.*?</p>"| cut -d ">" -f 6 | cut -d "<" -f 1  
```
> Don't Forget to modify the port number and the cookie ;)  

![flag](https://raw.githubusercontent.com/MoSalah20/HackTheBox/master/Emdee%20Five%20For%20Life/flag.png)
