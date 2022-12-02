# Advance-Recon
This information use for performing advance recon about your target.

### USE 3-4 TOOLS FOR FINDING SUBDOMAIN IT WILL HELP YOU FOR UNIQNESS.

First tool for subdomain finding is "subfinder" is available on git hub.
 	[ subfinder -d example.com -t 100 -o /root/subfinder.txt ].

Second tool is "assetfinder".
 	[ assetfinder example.com -subs-only > /root/assetfinder.txt ].

Third tools is "amass" before use amass make sure that maximum api keys are available is .config file of amass.
 	[ amass enum -ip -brute -d example.com -o /root/amass.txt ].

Fourth tool is "crt.sh" is also available on git hub.
	[ ./crt.sh example.com > /root/Desktop/crt.txt ].
	

### AFTER ALL SUBDOMAIN ENUMERATION THEN SORT ALL FILE FOR COLLECT UNIQ SUBDOMAIN.
	[ sort assetfinder.txt subfinder.txt amass.txt crt.txt | uniq -u > /root/sort.txt ].
	

### AFETR THAT USE HTTPROBE FOR CHECK REAL DOMAIN FROM sort.txt FILE.
	[ cat sort.txt | httprobe > httprobe.txt ] 
	

### AFTER THAT USE HTTPX TOOL FOR CHECK 80 AND 443 PORT USE  'sort.txt' FILE.
	[ cat sort.txt | httpx threads 200 > /root/httpx.txt ].
	

### THEN USE WAYBACKURLS TOOLS FOR FETCH URL'S FROM WAYBACK MACHINE USING 'httpx.txt' FILE.
	[ cat httpx.txt | waybackurls | tee -a /root/wayback.txt ]


### FOR JS FILE ENUMERATE USE 'grep' COMMAND.
	[ cat wayback.txt | grep js | tee -a /root/js.txt ]


### THEN USE EYEWITNESS FOR TAKING SCREENSHOTS OF DOMAIN USE sort.txt FILE.
	[ eyewitness --web -f /root/sort.txt -d /root/eyewitness.txt ]
	

### AFTER THAT FOR HIDDEN DIRECTORY FIND USE BREACHER TOOL.
	[ python3 breacher.py -u example.com ] 


### THEN CHECK FOR SUBDOMAIN TAKEOVER USE SUBZY TOOL USE httpx.txt FILE.
	[ subzy -targets httpx.txt  -concurrency 50 | tee -a /root/subzy.txt ]
	

### USE DOMAIN-PROFILER TOOLS FOR OBTAIN INFORMATION ABOUT WEB,DNS,MAIL HOSTING AND DOMAIN REGISTER



### USE PHOTON FOR RETRIVE SENSITIVE FILE, SUBDOMAIN AND JS FILES.


### USE LINKFINDER TOOL FOR JAVASCRIPT FILES.


### USE ARJUN TOOL FOR BRUTEFORCING THE PARAMETERS.


### AFTER THAT USE NUCLEI AND NUCLEI-TEMPLATES FOR SCANNING VULNERABILITY.
