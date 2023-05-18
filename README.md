# apache
#How to host multiple websites on the same machine

### 1 - first of all you need to launch your instance and make sure that the securty group is configured correctly you can do the same thing on your local machine:

### 2 - install apache on your centos machine using the following command :
        sudo yum -y install httpd
### 3 - you should start the service using the following command :
        sudo systemctl enable httpd.service
### 4 - Adjust the Firewall
        sudo firewall-cmd --permanent --add-service=http
### 5 - to apply changes of the firewall
        sudo firewall-cmd --reload
### 5  try to make sure that the apache server working correctly by hitting your local or private ip 
### such as (127.0.0.1)

### 6 - configure the virtual host file using this pass /etc/httpd/canf.d you can name the file any name you want but you should end the file with this extension (.conf) to allow the globel file reads your virtual Host file
      sudo etc/httpd/conf.d/01-VirtualHost.conf
      
### 7 - Virtual Host configuration
      check the Virtual host configuration file
      
### 8 - create you project dir, if you will create your project directory under /var/www it will work without any problem but if you want to change the path of the dir and not under /var/www the SElinux will prevent you so if you wanna avoid this problem you can give the same context of apache to the path of your project directory using the following command 
      sudo chcon -R --reference=/var/www/html /path/to/new_directory
      
### 9 - change your local DNS and add the name of your website along with the ip of your machine,
     sudo vim /etc/hosts
     
### 10 - restert the services (apache - network-manager)
     sudo systemctl restart httpd.service
     sudo systemctl restart network-manager

