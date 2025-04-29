EC2 Web Server Setup – Amazon Linux

- Launch an Amazon EC2 instance using *Amazon Linux*
- SSH into the instance
- Install a web server (Apache)
- Create and host a basic HTML page
- Provide the public IP or private link to access the web page

 1. Launch EC2 Instance
- Go to [AWS EC2 Console](https://console.aws.amazon.com/ec2/)
- Click Launch Instance
- Select*Amazon Linux 2 AMI (Free tier eligible)
- Choose instance type: t2.micro
- Create or select an existing key pair
- Configure security group:
- Allow SSH (port 22)from your IP
- Allow HTTP (port 80)from anywhere (0.0.0.0/0)
- Launch the instance

2. Connect via SSH

Make sure your key file has proper permissions:
chmod 400 server.pem
Then connect:
ssh -i "server.pem" ec2-user@<your-ec2-public-ip>
3. Install Apache Web Server
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
4. Create a Simple HTML Page

echo "<html><body><h1>Hello world i am sandhya from EC2 Web Server!</h1></body></html>" | sudo tee /var/www/html/index.html
If you get event not found error, run:
set +H
5. Access Your Web Page
Open a browser and go to:
http://<your-ec2-public-ip>
You should see your HTML page displaying:
Hello world i am sandhya from EC2 Web Server!
Example
Public IP: http://18.233.160.198
(Replace with your actual IP)
