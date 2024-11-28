# Introdução #

Utilizei como base o vídeo abaixo:

How to Install and Configure OCS Inventory Agent on Ubuntu | Debian | LinuxMint

https://www.youtube.com/watch?v=9SXMnrIbWM4&t=84s

Instalação com sucesso nos seguintes OS:

Oracle Linux 8, CentOs 7.9


# 1 - Instalar os pacotes necessários. #

yum install perl-CPAN  && yum install gcc  && yum install perl-XML-Simple && yum install perl-LWP-Protocol-https -y


# 2 - Instalar as dependências perl via CPAN. #

cpan XML::Simple  Compress::Zlib DBI Net::IP LWP::UserAgent Digest::MD5 Net::SSLeay Data::UUID LWP::Protocol::https Net::SNMP XML::SAX::Expat Proc::PID::File Net::Netmask Proc::Daemon Proc::PID::File


**OBS: Caso não funcione, tentar via yum. Basta remover os 2 pontos e escrever assim: yum install perl-XML-Simple.**

# 3 - Baixar o pacote de instalação, descompactar e acessar o diretório. #

"wget  https://github.com/OCSInventory-NG/UnixAgent/releases/download/v2.10.2/Ocsinventory-Unix-Agent-2.10.2.tar.gz"

tar –xvzf Ocsinventory-Unix-Agent-2.10.2.tar.gz (digitar, senão da erro)
cd Ocsinventory-Unix-Agent-2.10.2


# 4 - Iniciar a Instalação guiada. #

perl Makefile.PL

make

make install

Nome do host: http://192.168.10.192/ocsinventory

Caminho da pasta de Log: /var/log/ocs-agent.log

**Marcar n para não importar certificado**

ocsinventory-agent --proxy=192.168.10.18:3128
