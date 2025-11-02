# Desafio de Projeto: Gerenciamento de Instâncias EC2 na AWS

## Bootcamp
Santander Code Girls 2025 - AWS Cloud Foundations (DIO)

---

## Descrição do Desafio

Este laboratório teve como objetivo **consolidar conhecimentos em gerenciamento de instâncias EC2 na AWS**. O entregável é um repositório organizado contendo anotações e *insights* adquiridos durante a prática, servindo como material de apoio para estudos e futuras implementações.

## Objetivos de Aprendizagem

Ao concluir este desafio, foi possível:
* Aplicar os conceitos de Amazon Machine Image (AMI), Snapshots do Elastic Block Store (EBS) e gerenciamento do ciclo de vida de instâncias EC2.
* Documentar processos técnicos de forma clara e estruturada.
* Utilizar o GitHub como ferramenta para versionamento e compartilhamento.

---

## Passos Executados e Documentação

O projeto foi dividido em três partes principais, cobrindo os tópicos essenciais de gerenciamento de EC2.

### 1. Criação e Uso de Imagens AMI (Amazon Machine Image)

A AMI é um modelo (template) que contém a configuração de software, incluindo o sistema operacional, servidor de aplicativos e qualquer outra aplicação, necessária para iniciar uma instância EC2.

#### Processo:
1.  **Criação da Instância Base:**
    * Foi lançada uma instância EC2 com um Volume EBS de 8GB.
    * Conectei-me à instância via SSH e instalei um pacote simples para servir como "aplicação" de demonstração.
2.  **Criação da Imagem AMI:**
    * No Console EC2, selecionei a instância base.
    * Acesse: **Ações > Imagem e modelos > Criar imagem**.
    * Defini o nome da AMI.
    * A AWS criou a AMI, incluindo o template do SO e as configurações que fiz.
3.  **Teste da AMI Personalizada:**
    * Lancei uma **nova instância EC2** utilizando a recém-criada.
    * Após a inicialização, a nova instância já continha o servidor web pré-instalado, validando o processo de replicação do ambiente.

### 2. Snapshots EBS (Elastic Block Store)

Snapshots são backups incrementais dos Volumes EBS. Eles são armazenados no Amazon S3 e são essenciais para a resiliência e recuperação de desastres.

#### Processo:
1.  **Identificação do Volume:**
    * Localizei o Volume EBS (disco rígido virtual) da minha instância de teste no console.
2.  **Criação do Snapshot:**
    * Selecionei o Volume e escolhi **Ações > Criar Snapshot**.
    * Defini uma tag para identificação.
3.  **Simulação de Recuperação (Restauração):**
    * Para validar o backup, o Snapshot foi usado para **criar um novo Volume EBS**.
    * Este novo volume, contendo os dados do momento do backup, pode ser anexado a qualquer outra instância na mesma Zona de Disponibilidade, simulando a recuperação de dados após uma falha no volume original.

### 3. Gerenciamento de Instâncias EC2

O gerenciamento eficiente do ciclo de vida das instâncias é crucial para segurança, performance e, principalmente, **otimização de custos**.

#### Processo:
1.  **Controle do Ciclo de Vida:**
    * **STOP:** A instância é desligada. O Volume EBS e o IP Privado são mantidos (custo de armazenamento persiste), mas o custo da computação (a instância) é interrompido.
    * **START:** A instância é ligada novamente, mantendo a mesma configuração (mas podendo receber um novo IP Público).
    * **TERMINATE:** A instância e o Volume EBS principal são apagados (se a opção de exclusão for marcada). Este é o método final para **evitar custos** de computação e armazenamento indesejados.

2.  **Configuração de Segurança (Security Groups):**
    * Verifiquei que o **Security Group** anexado às instâncias permitia apenas o tráfego essencial:
        * Porta 22 (SSH) ou 3389 (RDP) – Apenas para meu IP.
        * Porta 80 (HTTP) – Liberada para o mundo (0.0.0.0/0) para testar o servidor web.

---

## Entrega Final

O projeto demonstra a aplicação prática dos principais conceitos de gerenciamento de computação e armazenamento na AWS, conforme proposto no desafio.
