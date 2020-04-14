# Elastic Stack on Docker
* **Criado por:** Leandro de Matos Pereira<br>
* **Última atualização:** 13.04.2020

Nesse repositório estão dispostos os arquivos necessários para configuração do ambiente, lembrando que utilizei esse ambiente usando um EC2 da AWS, no entanto é possível replicar em qualquer um dos Cloud Providers ou até mesmo por meio do VirtualBox utilizando o Vagrant para provisionar as máquinas.

Nesse tutorial, a instalação é feita usando o Docker, no entanto é possível fazer a instalação individual nas máquinas apenas baixando o binário de instalação, no entanto optei pela opção via containers, o que deixa o processo muito mais rápido.

### Configuração do servidor:

A criação de uma máquina com a seguinte configuração é mais que suficiente para testes no ambiente. Uma máquina Linux com 2VCPU, 08GB de RAM e 20GB de disco, equivalente ao tipo t2.large, também é possível utilizar a t2.medium, o SO fica um pouco mais lento durante o seu uso.

### Overview:

*	3 Node Elasticsearch para a formação do Cluster
*	Kibana version
*	Audit Beat version
*	MetricBeat version
*	HeartBeat version
*	Packet Beat version
*	APM Server version
*	APM Search
*	NGINX

### Instalando e configurando os recursos do SO:

Aumentar a memória Virtual, conforme a documentação oficial da Elastic: https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html

```
Sudo sysctl -w vm.max_map_count=262144 
```
A recomedação é editar o arquivo de configuração /etc/sysctl.conf e incluindo os paramêtros de forma permanente.


Instalação do Docker, conforme a documentação oficial do Docker: https://github.com/docker/docker-install

```
curl -fsSL https://get.docker.com | sh
```

Instalação do Docker-Compose, segundo a documentação oficial da Docker: https://docs.docker.com/compose/install/

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

```

Com tudo instalado validamos o docker e o docker-compose:

```
docker -v
docker-compose -version
```

### Baixando esse repositório via Git:
Para baixar o repositorio com o compose digite o comando abaixo:
```
git clone https://github.com/leandro-matos/docker-elastic-kibana.git
```
Entre dentro do diretório baixado:
```
cd docker-elastic-kibana
```

### Como fazer a execução.
Com o docker e o docker-compose instalados (no meu caso num Linux) basta baixar esse conteudo via ```git clone``` e entrando na pasta baixada rodar o comando abaixo:

```
sudo docker-compose up -d
```

### Como parar a execução.
Para remover os containers, assim como as respectivas configurações, basta executar o comando abaixo:

```
sudo docker-compose up -d
```
  
### Monitorando o start dos serviços:
Podemos acompanhar os logs de inicialização de cada serviço com o comando abaixo:
```
sudo docker-compose logs -f
```

#### Checando o status dos containers
```
docker-compose ps -a
```
![](images/docker-ps.PNG)

### Acesso ao Kibana
```
http://seuhost:5601 ou curl http://localhost:9200/_nodes?pretty=true via linha de comando
```

### Validando se o Kibana está rodando
![](images/kibana.PNG)

### Acessando o Kibana pelo Ngninx
```
http://seuhost:8081
```

### Acessando o ElasticSearch
```
http://seuhost:9200
```
### Validando se o ElasticSearch está rodando
![](images/cluster-elastic.PNG)

Dashboards criados automaticamente pelos Beats, o arquivo de configuração está dentro da pasta /config

##Metricbeat:
![](images/metricbeat.PNG)

##Metricbeat:
![](images/metrics.PNG)

##Packetbeat:
![](images/packetbeat.PNG)

##Heartbeat:
![](images/heartbeat.PNG)

# **Links Úteis**
* [Documentação Oficial](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)
* [Treinamentos Elastic](https://training.elastic.co/)
