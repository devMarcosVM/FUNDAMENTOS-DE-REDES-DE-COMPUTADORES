# Criar VLANs

Conecte 2 computadores na FastEthernet 1 e 2 , e outros 2 computadores nas portas 11 e 12. Abra o CLI do Switch e entao:
```bash
    enable
    configure terminal
    do show vlan brief
    vlan 2 # começamos na vlan2 pois a 1 é reservada
    name vendas # nomeia o vlan2 como vendas
    exit
    vlan 3
    name ti # nomeia o vlan3 como ti
    exit 
    show vlan brief # verificar se as vlans foram configuradas corretamente
    interface range fa0/1-10 #configura o range do primeiro vlan
    switchport access vlan3 # atribui o range configurado na interface a vlan3
    exit
    interface range fa0/11-20 # configura o range do segundo vlan
    switchport access vlan2  # atribui o range configurado na interface a vlan2
    exit
    do show vlan brief
    do wr 
```

Após fechar a configuração do switch, vamos configurar as máquinas, entrando nas máquina 1 e 2, vamos configurar o IP:
    - Ipv4 address: 
        - Máquina1: 192.168.10.2 
        - Máquina2: 192.168.10.3
    - Deafault Gateway: 192.168.10.1

Agora configurando as máquina 3 e 4, com outra rede colocamos a seguinte configuração:
    - Ipv4 address: 
        - Máquina1: 192.168.20.2 
        - Máquina2: 192.168.20.3
    - Deafault Gateway: 192.168.20.1