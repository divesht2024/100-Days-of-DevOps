
. Connected to Application Server 3

ssh banner@stapp03

        

        
      

2. Navigated to Docker Directory

cd /opt/docker/

        

        
      

Checked available files:

ls

        

        
      

Output:

Dockerfile  certs  html

        

        
      

👉 This confirmed:

    Dockerfile is present
    SSL certificates are available
    HTML application files are available

3. Inspected the Existing Dockerfile

Command used:

cat Dockerfile

        

        
      

Observed Dockerfile content:

IMAGE httpd:2.4.43

ADD sed -i "s/Listen 80/Listen 8080/g" /usr/local/apache2/conf/httpd.conf

ADD sed -i '/LoadModule\ ssl_module modules\/mod_ssl.so/s/^#//g' conf/httpd.conf

ADD sed -i '/LoadModule\ socache_shmcb_module modules\/mod_socache_shmcb.so/s/^#//g' conf/httpd.conf

ADD sed -i '/Include\ conf\/extra\/httpd-ssl.conf/s/^#//g' conf/httpd.conf

COPY certs/server.crt /usr/local/apache2/conf/server.crt

COPY certs/server.key /usr/local/apache2/conf/server.key

COPY html/index.html /usr/local/apache2/htdocs/

        

        
      

🔹 Problem Observed

Tried building the image:

docker build .
    

Docker returned error:

ERROR: failed to solve: dockerfile parse error on line 1: unknown instruction: IMAGE

