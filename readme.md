# LAB 01 - Cloud Computing
-------------------------------
###  Samuel Darcey - Zharkova Anastasia
-------------------------------
#### TASK 1:  SET UP
**Deliverable 1 :**  *List the available regions in the report. Which region is closest to you?  :*  
```USA Est (Virginie du Nord)```
```USA Est (Ohio)```
```USA Ouest (Californie du Nord)```
```USA Ouest( Oregon)```
```Canada (Centre)```
```UE (Irlande)```
``` UE (Francfort)```
```UE (Londres )```
```Asie Pacifique (Singapour)```
```Asie Pacifique (Sydney)```
```Asie Pacifique (Séoul)```
```Asie Pacifique (Tokyo)```
```Asie Pacifique (Mumbai)```
```Amerique du Sud (San Paulo)```

La region la proche de nous est UE ( n'importe lequel, Irlande était choisi automatiquement).  

**Deliverable 2:**
*From the EC2 Management Console copy the public DNS name of the instance into the report.*
```ec2-34-248-203-122.eu-west-1.compute.amazonaws.com```

*Once you have successfully logged into your EC2 instance, run the hostname and uname -a commands and paste their outputs into the report.* 
#HOSTNAME
```ubuntu@ip-172-31-29-214:/$ hostname```
```ip-172-31-29-214```

#UNAME
```ubuntu@ip-172-31-29-214:/$ uname -a```
```Linux ip-172-31-29-214 3.13.0-107-generic #154-Ubuntu SMP Tue Dec 20 09:57:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux```

*Try to ping the instance from your local machine. What do you see? Explain. Change the configuration to make it work. Ping the instance, record 5 round-trip times and plot them on a line graph using a spreadsheet.*

```Envoi d’une requête 'Ping'  34.249.162.52 avec 32 octets de données :```
```Délai d’attente de la demande dépassé.```
```Délai d’attente de la demande dépassé.```
```Délai d’attente de la demande dépassé.```

```Le port n'est pas ouvert dans le groupe de sécurité, il faut accepter les requête ICMP```

```C:\Users\samy->ping 34.249.162.52 -n 5```

```Envoi d’une requête 'Ping'  34.249.162.52 avec 32 octets de données :```
```Réponse de 34.249.162.52 : octets=32 temps=37 ms TTL=40```
```Réponse de 34.249.162.52 : octets=32 temps=36 ms TTL=40```
```Réponse de 34.249.162.52 : octets=32 temps=39 ms TTL=40```
```Réponse de 34.249.162.52 : octets=32 temps=36 ms TTL=40```
```Réponse de 34.249.162.52 : octets=32 temps=37 ms TTL=40```

```Statistiques Ping pour 34.249.162.52:```
  ```  Paquets : envoyés = 5, reçus = 5, perdus = 0 (perte 0%),```
```Durée approximative des boucles en millisecondes :```
   ``` Minimum = 36ms, Maximum = 39ms, Moyenne = 37ms```

*Determine the IP address seen by the operating system in the EC2 instance by running the ifconfig command. What type of address is it? Compare it to the address displayed by the ping command earlier. How do you explain that you can successfully communicate with the machine?.* On utilise la commande* ```history``` 
```ubuntu@ip-172-31-29-214:~$ ifconfig```
```eth0      Link encap:Ethernet  HWaddr 06:eb:ca:c2:2a:df
          inet addr:172.31.29.214  Bcast:172.31.31.255  Mask:255.255.240.0
          inet6 addr: fe80::4eb:caff:fec2:2adf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:32545 (32.5 KB)  TX bytes:32882 (32.8 KB)
```
IPV6 adresse: **fe80::4eb:caff:fec2:2adf**     (/64)
IPV4 adresse : **172.31.29.214**
En se loggant sur le port eth0 (la machine se trouve dans le cloud privé) on rentre l'adresse IPv4 public qui est traduit par le protocole interne en IPv6, il n'est pas necessaire de connaitre IPv6 pour se connecter à ce port. 

#### TASK 3: INSTALL A WEB APPLICATION

```--DRUPAL7
Password: 123soleil
--DRUPAL7 Installation
Password: 123soleil
```
**Deliverable 3:**

Add a screenshot of the page you created in Drupal to the report.
[Screenshot]: (Drupal_Front_Page.PNG) 

Add the elastic IP Address you created to the report.
```http://34.248.10.103/```

Why is it a good idea to create an Elastic IP Address for a web site (our web application)? Why is it not sufficient to hand out as URL for the web site the public DNS name of the instance?

Adresse IP Elastic est une adresse IPv4 qui est relié à notre compte AWS Amazon. Il permets de masquer la failure d'une instance ou software pour remapper à une autre instance qui est lié à notre compte. Puisque l'adresse elastique est attegnable depuis internet , il est possible, en cas d'absence adresse IPv4 public, de mapper l'adresse elastique à l'instance pour communiquer à l'exterieur. 
Les adresses elastiques ont ses limites aussi, il est possible d 'avoir uniquement 5 adresses par compte par region, voici pourquoi il est conseillé d'utiliser ces adresses pour maper l'adresse d'une autre inscance en cas de coupure et utiliser les DNS hostnames pour les autres inter-node communication. 







