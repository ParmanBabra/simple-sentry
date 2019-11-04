//Install Docker
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

//Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose


//Install Git
sudo apt-get install git

//Clone code
git clone https://github.com/ParmanBabra/simple-sentry.git sentry
git clone https://github.com/tesseract-shadow/tesseract-ocr-re.git tesseract
cd sentry


//Install sentry
sudo docker-compose up -d
sudo docker-compose exec sentry sentry upgrade
sudo docker-compose restart sentry
