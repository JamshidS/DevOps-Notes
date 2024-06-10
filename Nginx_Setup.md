## Setting Up Reverse Proxy with Nginx

To begin, let's explore why a reverse proxy is necessary.

Consider a scenario where you have an application running on port `9090`. When deploying this application on an EC2 instance, accessing it requires specifying the port number alongside the public IP or Public DNS. Without a reverse proxy or load balancer, accessing your application directly through your domain becomes impractical. This is because the default ports for HTTP and HTTPS requests are 80 and 443 respectively, whereas your application is running on port 9090. Thus, accessing your application using your domain becomes impossible without proper routing.

We'll address this challenge shortly.

## Setting Up Hosted Zones with Route 53

Begin by creating a hosted zone and linking it with your domain. Configure it accordingly with your domain name provider.
Afterward, create an A record that routes to your instance's public IP address. Additionally, create a CNAME record for your domain.

## Installing Nginx

To install Nginx on your AWS machine, begin by SSH-ing into your instance. Then, execute the following command:

```
sudo yum install nginx -y
```
- Start Nginx: Once Nginx is installed, start the Nginx service:
```ssh
sudo systemctl start nginx
```
- Verify Installation: Verify that Nginx is installed and running properly:
```
sudo systemctl status nginx
```

Now that Nginx is successfully installed on your machine, the next step is to edit the configuration to route requests to the corresponding port number.

## Editing Configuration File

To edit the configuration file, you can use Vim. Open the config file by executing:

```
sudo vim /etc/nginx/nginx.conf
```

Within the file, navigate to the server section and remove everything. Replace it with the following configuration:

```
server {
    listen 80;
    listen [::]:80;
    server_name your_domain_name_here;

    location / {
        proxy_pass http://localhost:9090; # Replace this port with the one your application is running on
    }
}
```

Ensure to replace `your_domain_name_here` with your actual domain name and adjust the `proxy_pass` directive to reflect the port your application is running on.