# Project 9 - Honeypot Deployment

Time spent: 4 hours spent in total

> Objective: To setup and deploy a honeypot in the cloud and report back the findings.

## Setup Details

The cloud provider used was Google Cloud Platform Free Tier. In the cloud, two virtual machines were created. Bother were f1-micro (1 vCPU, 0.6 GB memory) using the Intel Haswell CPU platform. Both has Ubunto 14.04 (trusty) installed. On one, I installed the Modern Honey Network (MHN) administration application. On the other, I deployed the Dionaea honeypot that MHN supports. I then ran an attack against the honeypot using nmap to make sure it is working correctly. Once I confirmed this, I left it up so that it could collect information for me.

## Results

The honeypot collected a total of 7940 attacks, with the session.json [here](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-9/session.json) in this branch containing information of each. It did not capture any malware. Included is a .gif with a small look at the results.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-9/honeypot.gif "Honeypot Walkthrough")


## Issues

Several issues were encountered, but none were too hard to fix. Initially, the admin VM would not allow me to access it via a browser. To fix this, I had to edit the firewall rule to allow traffic on TCP port 80. The firewall rule was also difficult to create. APIs had to be activated in the GCP settings via my browser in order to create the firewall rules. Lastly, exporting the .json did not work exactly as described. For me, I had to ssh into the admin vm and run this command: mongoexport --db mnemosyne --collection session > session.json
then exit the SSH, and run this command via my local command prompt: gcloud compute scp mhn-admin:session.json ./session.json
Within that .json, I removed my IP address and replaced it with my school's Computer Science department's IP address to help protect my confidentiality. I wish this had been warned about in the instructions.

## Unresolved Questions

None really. I wish that I had some better way to attract malware to the honeypot, as I believe it would be interesting to reverse engineer it. Perhaps in the future I will post the external IP of the honeypot in places that would bait attackers.
