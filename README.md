# elasticsearch-workshop

### Connexion à votre instance linux

- Installer [mobaXterm](https://download.mobatek.net/2022020030522248/MobaXterm_Portable_v20.2.zip) si vous êtes sur Windows
- Vos Credentials et IP respectives vous seront envoyés sur le chat
- Une clé SSH .pem vous sera transmise sur le chat
- si elle fournie au format .pem : 
	Convertissez-la en .ppk(voir mini [tuto](https://stackoverflow.com/questions/3190667/convert-pem-to-ppk-file-format))
- username : centos
- adresse ip : votre adresse
- options de connection : clé ssh ppk
	
### Production Tools

- Installer les outils suivants : 
	- [VS Code](https://code.visualstudio.com/download)
	- [GitHub Desktop](https://help.github.com/en/desktop/getting-started-with-github-desktop/installing-github-desktop)
	- [ElasticSearch - The Definitive Guide ](https://drive.google.com/open?id=1dtJhgRiVfaTrqpDqi4MA4HRK5K2iWSr6)
- IMPORTANT : L'ouvrage vous est fourni à titre de démo, merci de penser aux auteurs et de l'acheter légalement

### Installation de Java & wget
```
sudo yum install -y java
sudo yum install -y wget
```

### Installation ElasticSearch

- Centos/RHEL/AMZN
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.2-x86_64.rpm
sudo rpm -i elasticsearch-7.6.2-x86_64.rpm
```
- Debian
```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.2-amd64.deb 
sudo dpkg -i elasticsearch-7.6.2-amd64.deb
```

### Démarrage Service ElasticSearch
```
sudo service elasticsearch start
```

### Installation Logstash
- Centos/RHEL/AMZN
```
wget https://artifacts.elastic.co/downloads/logstash/logstash-7.6.2.rpm
sudo rpm -i logstash-7.6.2.rpm
```
- Debian
```
wget https://artifacts.elastic.co/downloads/logstash/logstash-7.6.2.deb
sudo dpkg -i logstash-7.6.2.deb
```

### Installation Kibana
- Centos/RHEL
```
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.6.2-x86_64.rpm
sudo rpm -i kibana-7.6.2-x86_64.rpm
```
- Debian
```
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.6.2-amd64.deb
sudo dpkg -i kibana-7.6.2-amd64.deb
```

#### Configuration accès distant (remplacer localhost / 127.0.0.1 par 0.0.0.0) 

- Editer le fichier de conf
```
sudo vi /etc/kibana/kibana.yml
``` 
```
# Kibana is served by a back end server. This setting specifies the port to use.

server.port: 5601 <<<<<< ⚠⚠⚠ VERIFIER ÇA ⚠⚠⚠

# Specifies the address to which the Kibana server will bind. IP addresses and host names are both valid values.
# The default is 'localhost', which usually means remote machines will not be able to connect.
# To allow connections from remote users, set this parameter to a non-loopback address.

server.host: 0.0.0.0 <<<<<< ⚠⚠⚠ CHANGER ÇA ⚠⚠⚠
```

- Sauvegarder

### Démarrage Service Kibana
```
sudo service kibana start
```

### Vérification de votre accès Web

- http://votre.adresse.IP:5601
