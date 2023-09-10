
1. How many TCP ports are open on the remote host?
First what we need to do is some recon, to know what's running on the server, for CTF it's enough use: nmap -sV <IP> with this i got everything what i want to know

![obraz](https://github.com/Anogota/Paper/assets/143951834/ed8782ef-0e6d-4aeb-b162-e4a69788636d)

We can see some SSH on port 22, HTTP on port 80 and also HTTPS on port 443, this scan looks intresting especially port 443 i don't see many times this port in CTF

2.What is the domain for the Wordpress blog?
First what i did is go to the webiste and check the source code, the experience told me to always check this out. But in source code is nothing intresting i intercept the traffic with burp and i found the Wordpress blog

![obraz](https://github.com/Anogota/Paper/assets/143951834/df1e5ee6-991e-4bd1-bf65-a4a4d3416c57)
