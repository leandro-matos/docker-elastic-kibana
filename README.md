# Elastic Stack on Docker
* **Criado por:** Leandro de Matos Pereira<br>
* **Última atualização:** 29.03.2020

Nesse repositório estarão dispostos os arquivos necessários para configuração do ambiente, lembrando que utilizei esse ambiente usando um EC2 da AWS, no entanto é possível replicar em qualquer um dos Cloud Providers ou até mesmo por meio do VirtualBox utilizando o Vagrant para provisionar as máquinas.

Nesse tutorial, vamos fazer uma instalação usando Docker, o que deixa o processo muito mais rápido e como nosso foco será mais na utilização do que na configuração da infra, acredito ser a melhor opção.

## Configuração do servidor:

A criação de uma máquina com a seguinte configuração é mais que suficiente para testes no ambiente. Uma máquina Linux com 2VCPU, 08GB de RAM e 2GB de disco, equivalente ao tipo t2.large

## Overview:

*	3 Node Elasticsearch para a formação do Cluster
*	Kibana version
*	Audit Beat version
*	MetricBeat version
*	HeartBeat version
*	Packet Beat version
*	APM Server version
*	APM Search
*	NGINX

## Instalando e configurando os Pré requisitos:

```
sudo yum update -y
sudo yum install docker git -y
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```