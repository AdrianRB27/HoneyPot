# HoneyPot

<h1>Honeypot Assignment</h1>
<h2>Time spent: 13 hours spent in total</h2>

<p>I went ahead and created a honeypot in order to protect my MHN Admin VM. I configured the VM with the follwowing firewall rules:</p>

<dl>
  <dt>gcloud compute firewall-rules create http \</dt>
  <dd>--allow tcp:80 \</dd>
  <dd>--description="Allow HTTP from Anywhere" \</dd>
  <dd>--direction ingress \</dd>
  <dd>--target-tags="mhn-admin"</dd>
</dl>

<dl>
  <dt>
gcloud compute firewall-rules create honeymap \</dt>
  <dd>--allow tcp:3000 \</dd>
  <dd>--description="Allow HoneyMap Feature from Anywhere" \</dd>
  <dd>--direction ingress \</dd>
  <dd>--target-tags="mhn-admin"</dd>
</dl>

<dl>
  <dt>gcloud compute firewall-rules create hpfeeds \</dt>
  <dd>--allow tcp:10000 \</dd>
  <dd>--description="Allow HPFeeds from Anywhere" \</dd>
  <dd>--direction ingress \</dd>
  <dd>--target-tags="mhn-admin"</dd>
</dl>

<p> With these set of rules, not only did we created a HoneyMap which would lead are attackers to the Honeyspots, which is our main objective. In order to create this honey spot, we SSH into our admin console and created the honey pot. Once SSH'd, we deployed 2 scripts called elastichonet & dionaea.<p>
<img src="https://user-images.githubusercontent.com/33438018/116504427-1a3c6780-a86d-11eb-81e6-936044e514b9.PNG">
  <p> In this image we see that the dionaea honeypot has been recieving multiple attacks. This could mean that this is an effective honeypot as many attackers are falling for it. It will be good to try to deploy multiple more though, as this honeypot can become more well know between hackers since everyone is attacking it.</p>
<img src="https://user-images.githubusercontent.com/33438018/116504435-1e688500-a86d-11eb-9fab-dd212edcf259.PNG">
<p>Here we have the results of how many attackers have attempted to attack our honeypot-2-dionaea
  
  
 <h3>Week 11 </h3>
 <br>
 <p>This week we needed to export the json file containing information that all of the honeypots contained and scan to see if they had viruses. In my personal case, I ran a clamscan and did not find any viruses. I went ahead and exported the json file and stored it in the local machine for examination. </p>
 <p> To do this, I went ahead and perfomed the following commands on whie being SSH'ed to the MHN Admin Machine while having the honeypots running </p>
 <dl>
  <dd>mongoexport --db mnemosyne --collection session > session.json</dd>
  <dd>truncate --size="<5M" session.json</dd>
  <dd>gcloud compute scp mhn-admin:~/session.json ./session.json</dd>
</dl>
 
 

