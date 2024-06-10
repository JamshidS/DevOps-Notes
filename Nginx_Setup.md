## Setting Up Reverse Proxy with Nginx

To begin, let's explore why a reverse proxy is necessary.

Consider a scenario where you have an application running on port `9090`. When deploying this application on an EC2 instance, accessing it requires specifying the port number alongside the public IP or Public DNS. Without a reverse proxy or load balancer, accessing your application directly through your domain becomes impractical. This is because the default ports for HTTP and HTTPS requests are 80 and 443 respectively, whereas your application is running on port 9090. Thus, accessing your application using your domain becomes impossible without proper routing.

We'll address this challenge shortly.