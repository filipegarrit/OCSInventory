# 0 - Requisitos Prévios #

- Oracle Linux 8 (x86_64) 

- Apache 2.4 

- MariaDB 

- PHP 7.4 

- Perl 5.26 (já vem instalado no OL 8) 

 

# 1 - Instalar dependências # 

Pacotes Adicionais para Enterprise Linux (ou EPEL) é um grupo especial do Fedora com interesse em criar, manter e gerenciar um conjunto de pacotes adicionais com alta qualidade para o Enterprise Linux, incluindo, mas não se limitando a, Red Hat Enterprise Linux (RHEL), CentOS e Scientific Linux (SL), o Oracle Linux (OL). 

Pacotes EPEL são geralmente baseados em suas contrapartes do Fedora e nunca entrarão em conflito ou substituirão os pacotes da base de distribuições Enterprise Linux. EPEL usa muito da mesma infraestrutura do Fedora, incluindo buildsystem, bugzilla, gerenciador de atualizações, gerenciador de sites espelhos (mirrors) e muito mais. 

Instalar gcc: yum install gcc 

Instalar CPAN: yum install perl-CPAN 

cpan XML::Simple  Compress::Zlib DBI Net::IP LWP::UserAgent Digest::MD5 Net::SSLeay Data::UUID LWP::Protocol::https Net::SNMP XML::SAX::Expat Proc::PID::File Net::Netmask Proc::Daemon Proc::PID::File

Instalar Epel: yum install -y epel-release 

Instalar PHP : yum install php-mysqlnd &&dnf install @php:8.2 

Instalar apache: sudo yum install httpd -y 

Iniciar serviço apache: systemctl start httpd 

Habilitar apache no boot: systemctl enable httpd.service 

Instalar MariaDB: sudo yum install mariadb-server 

Iniciar serviço MariaDB: sudo systemctl start mariadb 

Habilitar apache no boot: sudo systemctl enable mariadb.service 


# 2 - Criar banco de dados e usuário # 

mysql_secure_installation 
 

Login como root no mysql. 

mysql -u root -p 

CREATE DATABASE ocsweb; 

GRANT ALL PRIVILEGES ON ocsweb.* TO 'host'@'localhost'  IDENTIFIED BY 'senha'; 

FLUSH PRIVILEGES; 

 
# 3 - Baixar e instalar o OCS Inventory # 

wget https://github.com/OCSInventory-NG/OCSInventory-ocsreports/releases/download/2.12.3/OCSNG_UNIX_SERVER-2.12.3.tar.gz  

tar -xvzf OCSNG_UNIX_SERVER-2.12.3.tar.gz 

cd OCSNG_UNIX_SERVER-2.12.3/ 

perl Makefile.PL 

make 

make install 
 
# 4 - Configurar o OCS Inventory e inicializar o serviço #

ocsinventory-setup --database-driver DBI::mysql --database-host localhost --database-name ocs --database-user ocs --database-password senha 

systemctl start ocsinventory-server && sudo systemctl enable ocsinventory-server 


# 5 -  Acessar o painel #
 
- URL: http://<ip-do-servidor>/ocsreports 

- Usuário: admin 

- Senha: admin 

Lembre-se de substituir <ip-do-servidor> pelo IP do seu servidor. 

 

Erros: 

 




