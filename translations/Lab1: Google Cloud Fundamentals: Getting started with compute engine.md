## Lab1 Translation Code
Lab1: Google Cloud Fundamentals: Getting started with compute engine.
##Objectives: Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

Create a Compute Engine virtual machine using the gcloud command-line interface.

Connect between the two instances.

#Tasks: Step 1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default" --tags http
Step 2. Create a Compute Engine virtual machine using the gcloud command-line interface.

gcloud config set compute/zone us-central1-b
gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default"
Step 3. Connect between the two instances.

#Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network.

#Connect to my-vm-2 using ssh

gcloud compute ssh my-vm-2
#run ping to test connection to my-vm-1

 ping -c 3 my-vm-1
#Use the ssh command to open a command prompt on my-vm-1

 ssh my-vm-1
#install the Nginx web server

 sudo apt-get install nginx-light -y
#Use the nano text editor to add a custom message to the home page of the web server:

 sudo nano /var/www/html/index.nginx-debian.html
#Add text like this, and replace YOUR_NAME with your name:

 Hi from YOUR_NAME
#Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:

curl http://localhost/
#To exit the command prompt on my-vm-1, execute this command.

exit
#To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:

 curl http://my-vm-1/
#Get external IP for my-vm-1

 gcloud compute instances list
#copy and paste my-vm-1 external IP to a web browser address bar #you will see your web server's home page, including your custom text.