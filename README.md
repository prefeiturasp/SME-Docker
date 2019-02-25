

# Docker

O Docker permite a verdadeira independência entre aplicativo e infraestrutura, desenvolvedores e operações de TI para que possam desbloquear seu potencial e criar um modelo para melhor colaboração e inovação. O Docker possibilita o empacotamento de uma aplicação ou ambiente inteiro dentro de um container, e a partir desse momento o ambiente inteiro torna-se portável para qualquer outro Host que contenha o Docker instalado. Veja mais informações [aqui](https://www.docker.com/what-docker) e [aqui](https://www.mundodocker.com.br/o-que-e-docker/).

### Porque começar usar docker nas aplicações da SME?

A Secretaria Municipal de Educação de São Paulo possui dezenas de sistemas sob sua tutela, seja para uso dos professores quanto para uso administrativo. Cada um com suas peculiaridades e requisitos de sistema diferentes, produzidos e mantidos por diferentes empresas, em diferentes sistemas operacionais. Cada dia que passa fica mais complicado manter tudo em ordem e não criar dependências entre equipes. A utilização de containers vem para ser o primeiro passo de muitos que irão facilitar o gerenciamento desses sistemas e iniciar um processo de padronização para que futuramente seja mais fácil replicar ambientes e compartilhar arquivos.

### Primeiros Passos

* 64-bit CentOS 7
* Acesso como usuário administrador 
   
###  Instalação Docker

Atualizar os pacotes do SO 

`sudo yum check-update`

Fazer o download da última versão e instalar o docker

`curl -fsSL https://get.docker.com/ | sh`

Iniciar o docker daemon

`sudo systemctl start docker`

Teste se está funcionando como deveria

`sudo systemctl status docker`

Por fim certifique-se ele é iniciado quando o servidor reinicia

`sudo systemctl enable docker`

Pronto, agora já é possível utilizar docker nas suas aplicações. Enjoy!


### Instalação docker-compose

Faça instalação da última versão do docker-compose

` sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose `

Aplique as permissões

` sudo chmod +x /usr/local/bin/docker-compose `

Teste a instalação

` docker-compose --version `

### Troubleshooting

#### Conflito de rede

Por padrão o Docker utiliza a rede 172.16.0.0/12. Caso este range já esteja em uso, será necessário alterar.

Alterando a rede docker0

` sudo vi /etc/docker/daemon.json `

Adicione:

` {
  "bip": "10.0.0.1/24"
} `

Criando uma rede

` docker network create app --driver bridge --subnet 10.0.1.0/24 `

# Roadmap
https://docs.docker.com/docker-hub/builds/

https://docs.docker.com/registry/

https://docs.docker.com/engine/swarm/

https://codefresh.io/docker-tutorial/not-ignore-dockerignore/


Para saber quais sistemas estão utilizando docker e como isso foi feito, visite a nossa wiki: 

[Processo de adoção e instalação do docker na SME](https://github.com/prefeiturasp/SME-Docker/wiki/Processo-de-ado%C3%A7%C3%A3o-do-Docker-na-SME)

