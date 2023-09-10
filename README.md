
1. How many TCP ports are open on the remote host?
First what we need to do is some recon, to know what's running on the server, for CTF it's enough use: nmap -sV <IP> with this i got everything what i want to know

![obraz](https://github.com/Anogota/Paper/assets/143951834/ed8782ef-0e6d-4aeb-b162-e4a69788636d)

We can see some SSH on port 22, HTTP on port 80 and also HTTPS on port 443, this scan looks intresting especially port 443 i don't see many times this port in CTF

2.What is the domain for the Wordpress blog?
First what i did is go to the webiste and check the source code, the experience told me always to check this out. But in source code is nothing intresting i intercept the traffic with burp and i found the Wordpress blog

![obraz](https://github.com/Anogota/Paper/assets/143951834/df1e5ee6-991e-4bd1-bf65-a4a4d3416c57)

3.Which 2019 CVE is the wordpress version vulnerable to?
We need to know the version Wodpress, we can check this with help extension wapalyzer, heres the results:

![obraz](https://github.com/Anogota/Paper/assets/143951834/5c9051bc-8a54-46d7-a60b-fc1f55fc6198)

That how you can see the version of wordpres is 5.2.3, now with this information we nned to find some CVE
I found this exploit on exploit-db

![obraz](https://github.com/Anogota/Paper/assets/143951834/27b47b7c-82b4-4d76-a4ab-80184ac70f0a)

Descryption exploit:
So far we know that adding `?static=1` to a wordpress URL should leak its secret content

Here are a few ways to manipulate the returned entries:

- `order` with `asc` or `desc`
- `orderby`
- `m` with `m=YYYY`, `m=YYYYMM` or `m=YYYYMMDD` date format


In this case, simply reversing the order of the returned elements suffices and `http://wordpress.local/?static=1&order=asc` will show the secret content:
