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

                                                              Task 3: Save the capture packets in a dump file

 When saving our results we use the -w option with filename.pcap, here pcap is the standard extension, although you can use any. Also the directory where we are using tcpdump and making the file needs to have the write access by everyone.    

 <img width="365" height="66" alt="image" src="https://github.com/user-attachments/assets/a1566170-0350-4a15-b9b9-68389b3ff169" />

 <img width="373" height="105" alt="image" src="https://github.com/user-attachments/assets/efa95199-7a50-4240-af71-2dcf6b6d5875" />

 we can use the -r option of tcpdump to read the file and add other options to the captured data as well, as here we did of time:


 <img width="377" height="36" alt="image" src="https://github.com/user-attachments/assets/f66a2cf1-8512-451a-af69-8d27d3d12db5" />

We can open the same file in wireshark for better readable content that we captured:

<img width="468" height="262" alt="image" src="https://github.com/user-attachments/assets/226d0e35-e1c4-46be-ae08-fb81f3605170" />

                                                                       Task 4: Create Sequenced Dump Files

We use the -G option to ensure that content after every 15 seconds here is wiped out of our pcap (reate a new capture file every X seconds. This prevents one giant .pcap file and instead splits the capture into smaller, manageable chunks):

<img width="512" height="140" alt="image" src="https://github.com/user-attachments/assets/7f09cbd2-e149-463a-9e85-4393583e7b7f" />


we can also limit the size of the file so -C limits the size to 1 megabyte or whatever number we write and then make a new one:

<img width="354" height="106" alt="image" src="https://github.com/user-attachments/assets/2ea5b541-c704-4968-9a01-48fba5d93ceb" />

or we can set both options but in that case if one one is fullfilled then it moves to next file chunk:
<img width="384" height="80" alt="image" src="https://github.com/user-attachments/assets/26c23eaf-018a-4ab2-ac2e-868c4b84dbb2" />

                                                                      Task 5: Decrypt and Analyze Captured Traffic
Script for network traffic capture and to get the private and public keys:

<img width="369" height="98" alt="image" src="https://github.com/user-attachments/assets/b1fed93d-e0e3-46c4-955d-be7f7b02ecbd" />


Files made after running the script:
<img width="255" height="67" alt="image" src="https://github.com/user-attachments/assets/21da35cc-5e36-4723-88fd-524364a26a66" />
                                                                      

To tell wireshark where keys are as we open the capture file and see encryted data, we go to edit-preference-protocols-TLS and then at the last option add the full path to the keys file, so then we see that the HTTP data is decrypted as it turns green, so we can also apply the http filter to easily analyse:



