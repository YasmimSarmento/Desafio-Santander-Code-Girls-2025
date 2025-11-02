\# Anotações Técnicas e Conceitos Consolidados



Este documento contém um resumo dos conceitos e comandos técnicos utilizados durante o Desafio EC2 do Santander Code Girls 2025.



=======================================================

1\. Amazon EC2 (Elastic Compute Cloud)

=======================================================



\- Conceito: Instância

  Resumo: Servidor virtual na nuvem.



\- Conceito: AMI (Amazon Machine Image)

  Resumo: Template para criação de instâncias. Inclui OS e software.



\- Conceito: Security Group

  Resumo: Firewall virtual que controla o tráfego de entrada e saída (Inbound/Outbound) da Instância.



\- Conceito: Tipos de Instância

  Resumo: Ex: T (burstável/econômica), M (propósito geral), C (otimizado para computação).



\- Conceito: Ciclo de Vida

  Resumo: \*\*Stop:\*\* Desliga, mantém dados no EBS, mantém IP Privado (pode mudar o IP Público). \*\*Terminate:\*\* Encerra a instância e exclui o Volume EBS.



=======================================================

2\. EBS (Elastic Block Store) e Snapshots

=======================================================



\- Conceito: Volume EBS

  Resumo: Armazenamento em bloco persistente, como um disco rígido. Deve estar na mesma Zona de Disponibilidade (AZ) da instância.



\- Conceito: Snapshot

  Resumo: Backup pontual e incremental do Volume EBS. Armazenado no S3.



\- Conceito: Incremental

  Resumo: Apenas os blocos de dados que foram alterados desde o último snapshot são salvos. Otimiza tempo e custo.



\- Conceito: Restauração

  Resumo: Um Snapshot é usado para criar um novo Volume EBS ou uma nova AMI.



=======================================================

3\. Comandos Utilizados (Exemplo com Linux)

=======================================================



Estes comandos foram usados para configurar o ambiente de teste na instância EC2:



Comandos (Insira no Bloco de Notas exatamente como está, sem os números de linha):

1\.  # Conectar via SSH:

    ssh -i "sua-chave.pem" ec2-user@ip-publico



2\.  # Atualizar o sistema:

    sudo yum update -y



3\.  # Instalar o Apache (Amazon Linux 2):

    sudo yum install httpd -y



4\.  # Iniciar o serviço Apache:

    sudo systemctl start httpd



5\.  # Habilitar o Apache para iniciar no boot:

    sudo systemctl enable httpd



6\.  # Criar um arquivo de teste para a AMI (Ex: uma página "Hello World"):

    echo "<h1>AMI Criada com Sucesso - Santander Code Girls</h1>" | sudo tee /var/www/html/index.html

