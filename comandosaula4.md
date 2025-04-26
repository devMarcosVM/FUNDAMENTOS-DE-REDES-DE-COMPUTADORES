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

## Primeiras Configurações do Switch
- Certifique-se de estar no nível mais alto de administração antes de executar os comandos abaixo:
    ```bash
    hostname NOME
    banner motd #ACESSO RESTRITO#
    line console 0
    password SUA_SENHA
    login
    exit
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

## Configurar o Servidor
A configuração do servidor serve para utilizar os serviços do servidor, o que fizemos em aula foi o serviço de automatização dos ips das máquinas através do DHCP.
 - Passos
   1. Desligar servidor
   2. Retirar a peça Ethernet e no lugar colocar a peça PT-HOST-NM-1CGE
   3. Religar o servidor e colocar um cabo Copper Straight-Through entre o servidor e o Switch
   4. Abra o Ip configuration do Servidor e coloque o ip `192.168.1.2` (ip do servidor) e `192.168.1.1` (ip do roteador) na entrada de gateway
   5. Coloque o DNS como endereco ip do servidor

## Configurar o Serviços do Servidor
 - Passos
   1. Abra o servidor na aba serviço 
   2. Vá em DHCP e coloque o service em ON
   3. As vezes a interface não está correta então verifique se está no GigabitEthernet0
   4. Configure o Gateway (ip do roteador) e DNS (ip do servidor)
   5. Coloque o Start IP Adress a partir de onde você quer que o id das máquinas comece, como o id 1 esta no roteador e id 2 no servidor colocaremos o start ip adress em `192.168.1.3`
   6.Agora vá em todos os PCs em Desktop -> IP Configuration e selecione DHCP, os ipa serão preenchidos automaticamente.




## Anotações para prova

 - Quando o 0 está no final do ip 192.168.1.0 você está mostrando o endereço de uma rede inteira não de um dispositivo

