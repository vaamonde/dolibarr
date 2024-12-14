#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 14/01/2023<br>
#Data de atualização: 12/08/2024<br>
#Versão: 0.18<br>

Conteúdo estudado nesse desafio:<br>
#01_ 

Site Oficial do MySQL: https://www.mysql.com/<br>
Site Oficial do MariaDB: https://mariadb.org/<br>
Site Oficial do Workbench: https://www.mysql.com/products/workbench/

Site Oficial do W3C School MySQL: https://www.w3schools.com/mysql/default.asp

O MySQL é um sistema de gerenciamento de banco de dados, que utiliza a linguagem SQL como interface. É atualmente um dos sistemas de gerenciamento de bancos de dados mais populares da Oracle Corporation, com mais de 10 milhões de instalações pelo mundo. 

[![MySQL Server](http://img.youtube.com/vi//0.jpg)]( "MySQL Server")

Link da vídeo aula: 

Resolver problema de dependências do Mcrypt: https://computingforgeeks.com/install-php-mcrypt-extension-on-ubuntu/

sudo apt install php-mysql php-imagick php-gd php-mbstring php-soap php-curl php-intl php-zip php-xml php-gd

https://wiki.dolibarr.org/index.php?title=Dependencies_and_external_libraries

#01_ Download do Dolibarr ERP/CRM do SourceForge<br>
```bash
#download do arquivo compactado do Dolibarr
wget -O /tmp/dolibarr.tgz https://sourceforge.net/projects/dolibarr/files/Dolibarr%20ERP-CRM/20.0.0/dolibarr-20.0.0.tgz
```

#02_ Descompactar o Arquivo do Dolibarr<br>
```bash
#acessando o diretório temporário
cd /tmp

#descompactando o arquivo do Dolibarr
sudo tar -zxvf /tmp/dolibarr.tgz
```

#03_ Copiando o Diretório do Dolibarr para a Raiz do Apache2<br>
```bash
#acessando o diretório descompactado do Dolibarr
cd dolibarr*/

#copiando e alterando o nome do diretório do Dolibarr
sudo cp -Rv htdocs/ /var/www/html/vaamonde

#copiando o arquivo de configuração do Dolibarr
sudo cp -v /var/www/html/vaamonde/conf/conf.php.example /var/www/html/vaamonde/conf/conf.php

#alterando as permissões do arquivo de configuração do Dolibarr
sudo chmod 666 -v /var/www/html/vaamonde/conf/conf.php

#criando o diretório de documentos do Dolibarr
sudo mkdir -v /var/www/html/vaamonde/documents
sudo chmod -v 777 /var/www/html/vaamonde/documents/

#instalação via Web
https://172.16.1.20/vaamonde/install

#nova instalação do Dolibarr
Instalação/Atualização do Dolibarr
  Verificando pré-requisitos
    Nova instalação <Iniciar>

#iniciando a instalação do Dolibarr
DolibarrSetup - Arquivo de configuração
  Servidor web
    Diretório onde armazenar as páginas web: /var/www/html/vaamonde
    Diretório onde armazenar documentos enviados e/ou gerados: /var/www/html/vaamonde/documents
    URL raiz: https://172.16.1.20
    Forcar conexões seguras https: (ON) (ENABLE)

Base de dados Dolibarr
  Nome da Base de Dados: vaamonde
  Tipo de Controlador: mysqli (MySQL or MariaDB >= 5.03)
  Servidor da Base de Dados: localhost
  Porta: 3306
  Prefixo da tabela de banco de dados: maq_
  Criar uma base de dados: (ON) (ENABLE)
  Iniciar Sessão: vaamonde
  Senha: pti@2018
  Crie uma conta de usuário ou conceda permissão de conta de usuário no banco de dados Dolibarr: (ON) (ENABLE)

Base de dados - Acesso Superuser
  Iniciar Sessão: root
  Senha: pti@2018
<Passo Seguinte>

Instalação/Atualização do Dolibarr - Arquivo de configuração
  Arquivo de configuração
<Passo Seguinte>

Instalação/Atualização do Dolibarr - Criação dos objetos na base de dados...
  Faça um ping anônimo '+1' no servidor de base Dolibarr (feito apenas uma vez após a instalação) 
  para permitir que a base conte o número de instalações do Dolibarr. (ON) (ENABLED)
<Passo Seguinte>

Instalação/Atualização do Dolibarr - Criando login do Administrador
  Sessão Administrador Dolibarr
  Iniciar Sessão: vaamonde
  Senha: vaamonde2024
  Reescreva a sua senha: vaamonde2024
<Passo Seguinte>

Instalação/Atualização do Dolibarr - Fim da Configuração
<Ir para a área de configuração>

#bloqueando a reinstalação do Dolibarr
sudo touch /var/www/html/vaamonde/documents/install.lock

#alterando as permissões do arquivo Conf do Dolibarr
sudo chmod 644 -v /var/www/html/vaamonde/conf/conf.php

https://wiki.dolibarr.org/index.php?title=Backups

mysqldump -u root -ppti@2018 -l --single-transaction -K --add-drop-table=TRUE --tables -c -e --hex-blob --default-character-set=utf8 --result-file=vaamonde-17102024.sql vaamonde

sudo mount -t cifs -o username=vaamonde,password=vaamonde //172.16.1.25/vaamonde /backup/

//172.16.1.25/maqfrio /backup cifs username=vaamonde,password=vaamonde,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

iocharset=utf8