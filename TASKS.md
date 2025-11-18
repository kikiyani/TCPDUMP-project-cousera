                                                                   TASK 1: INTRODUCTION AND GETTING STARTED
sudo tcpdump ( to access tcpdump, shows captured network traffic)
tcpdump -c 10 ( limits the capture to only 10 packets, useful to tell if something is up and running )
tcpdump -c 10 -# ( this hash puts a line number infront of each capture to keep a track )
tcpdump -c 10 -#xx (shows content of data packets in heaxadecimal and asci ) 
tcpdump -c 10 -#A ( shows content of data packets in ASCII)
tcpdump -c 10 #tttt ( gives timestamps to our output)

<img width="425" height="151" alt="image" src="https://github.com/user-attachments/assets/1e26da51-b38a-4de6-8e14-53a36093919a" />

                                                                  Task 2: Start Building the Logging Tool Script
sudo tcpdump -D (lists all the network interfaces, amoung which tcpdump only caughts the first one ethernet usually)
sudo tcpdump -c 10 -i lo (this -i options makes us specify which interface we want tcpdump to capture from)
tcpdump -c 10 -#xxtttt port 443 or host cousera.org (so this port and host option helps us classify which specific host or port we want to capture at)
tcpdump -c 10 -#xxtttt src\dest cousera (capturing traffic thats either coming fro cousera only or going to cousera , two different options)
tcpdump -c 10 -#xxtttt host cousera.org and port 443 (this way we can filter on basis of two things)

Creating a script:
<img width="254" height="50" alt="image" src="https://github.com/user-attachments/assets/b52b12ef-7850-464e-b941-626fddb87173" />


Executing the script with proper permissions:
<img width="363" height="98" alt="image" src="https://github.com/user-attachments/assets/9d113240-48d2-4629-af5e-1cddbaab403c" />
