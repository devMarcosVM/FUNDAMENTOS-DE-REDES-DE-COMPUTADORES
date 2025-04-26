# Comandos essenciais FUNDAMENTO DE REDES DE COMPUTADORES

## Comandos de Administração

### Acessando Níveis de Administração
- Para acessar o nível intermediário de administração:
    ```bash
    enable
    ```
- Para acessar o nível mais alto de administração:
    ```bash
    configure terminal
    ```

## Desativar Tradução de Nomes no Cisco Packet Tracer
- Use o comando abaixo para evitar que o dispositivo tente traduzir nomes incorretos:
    ```bash
    no ip domain lookup
    ```

## Configuração do Endereço do Gateway (Roteador)
- Para configurar o endereço IP do gateway:
    ```bash
    ip address 192.168.10.254 255.255.255.0
    ```
- Caso tenha configurado o IP incorretamente, utilize o comando com `no` para corrigir:
    ```bash
    no ip address 192.168.10.254 255.255.255.0
    ```

## Primeiras Configurações do Switch e Router
- Certifique-se de estar no nível mais alto de administração antes de executar os comandos abaixo:
    ```bash
    hostname NOME
    banner motd #ACESSO RESTRITO#
    line console 0
    password SUA_SENHA
    login
    exit #volta para o nível anterior
    do copy running-config startup-config
    reload
    ```

## Configuração de IP no Roteador
- Lembre-se de configurar o IP em todas as máquinas e ajustar o switch para a nova conexão. No terminal do roteador, siga os passos abaixo:
    1. Acesse o modo privilegiado:
         ```bash
         enable
         ```
    2. Entre no modo de configuração global:
         ```bash
         configure terminal
         ```
    3. Exiba um resumo das interfaces e seus endereços IP:
         ```bash
         show ip interface brief
         ```
    4. Selecione a interface para configuração:
         ```bash
         interface gigabitEthernet 0/1
         ```
    5. Configure o endereço IP e a máscara de sub-rede:
         ```bash
         ip address 192.168.5.254 255.255.255.0
         ```
    6. Ative a interface, caso esteja desativada:
         ```bash
         no shutdown
         ```
    7. Salve as configurações realizadas:
         ```bash
         do wr
         ```

## Configurar o Gateway de cada computador

- Passos 
    1. Abra o computador
    2. Selecione ip
    3. Coloque o ip do switch em `Default Gateway`. ex: 192.168.5.254

Faça isso para todos os computadores para conectar a outra redes

## Configuração de RIP no Roteador
- Para configurar o protocolo RIP no roteador:
    1. Abra o roteador e vá para a aba `Config`.
    2. Em `RIP`, adicione as redes necessárias no campo `Network` com o final `.0` e clique em `ADD`.
    3. Repita o processo para todas as redes que forem necessárias.