### Default template Laravel 8 
<br/>
<br/>

#### Services
* php:7.4-fpm
* nginx latest
* mysql latest
<br/>
#### How start
* docker composer up -d --build
* expose port 80
* default route /

<br/>
<br/>

# Desafio

Seu desafio será criar um simulador de caixa eletrônico, com as seguintes funções:

* Acesso por número de conta e senha
* Deposito de valores
* Saque de valores
* Extrato de valores dos últimos trinta dias
* tela de cadastro de contas
* envio de email com boas vindas do novo usuário

#### Opcionais

* Transferência entre contas
* envio de email para informar as seguintes transações (Saque, depósito de valores, transferência)


## Documentação de consulta de

[Laravel](https://laravel.com/docs/8.x)<br/>
[MailTrap](https://blog.especializati.com.br/utilizando-o-mailtrapio-testes-de-envio-de-e-mail/) Para captura do envio de emails <br/>
[Bootstrap](https://getbootstrap.com/docs/5.1/getting-started/introduction/) Já existe um template em backend/resources/views/layouts/app.blade.php
<br/>

## Ajudas

### Docker

Essa aplicação roda no docker, por isso será necessário instalar o docker e o docker composer em sua última versão. Para subir a aplicação basta rodar docker-compose up --build. Toda vez que aplicação roda as migrations e dependências do composer e npm são atualizadas.

#### Dica de ouro

Como a aplicação roda em container do docker para ter acesso será necessário executar a seguinte ação:<br/>

docker exec -it [nome do container] bash

#### Banco de dados
Você deverá criar a estrutura do banco de dados, caso queria uma ferramenta para gerência o banco de dados recomendo dbeaver.<br/>
Para o acesso ao banco de dados utilize as credências:<br/>
Usuário e senha <b>root</b>
Endereço do servidor: localhost:3006

#### Acesso aplicação

Para acessar a aplicação basta acessar localhost, ela já roda na porta 80