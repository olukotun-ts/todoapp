ctx:
    - create AMI using Packer (https://learn.hashicorp.com/tutorials/packer/aws-get-started-build-image?in=packer/aws-get-started)
    - config.yml

Compress folder
tar -czvf name-of-archive.tar.gz /path/to/directory-or-file
tar -czvf build.tar.gz build

Copy file to instance
scp -i /path/key-pair-name.pem /path/my-file.txt ec2-user@instance-public-dns-name:path/
scp -i ~/.ssh/olukotun-us-west-1.pem ./build.tar.gz ec2-user@54.193.56.83:build.tar.gz

Uncompress folder
tar -xzvf build.tar.gz

Install Apache server
sudo yum install httpd -y

Start service
sudo service httpd start

Configure to restart if stopped
sudo chkconfig httpd on

Default config
cat /etc/httpd/conf/httpd.conf

Create default httpd DocumentRoot dir if not exists
mkdir -p /var/www/html

[? Didn't work] Create symlink to build folder
ln -s existing_source_file optional_symbolic_link
sudo ln -s ~/build/index.html /var/www/html/index.html

Copy build folder to default httpd dir
sudo cp -a ~/build/. /var/www/html