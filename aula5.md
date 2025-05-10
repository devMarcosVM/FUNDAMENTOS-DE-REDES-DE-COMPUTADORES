# Interligar Redes Diferentes

## Primeiro Passo - Configurar as Redes
Configure duas redes separadas, uma da outra com IP's diferentes

 - **Roteador 1:** 3 máquinas, um servidor, um roteador e um switch
 - **Roteador 2:** 1 Roteador, um switch e 3 máquinas

Na aula foi configurado a primeira rede como `192.168.5.0` para primeira rede e para a segunda `192.168.10.0`

Para consultar como configurar um roteador acesse o arquivo `comandos.md` no tópico `Configuração do Terminal` onde temos a configuração geral e a configuração do Gateway do roteador

Os roteadores foram configurados no endereço `.1`. E o servidor da rede 1 foi configurado no `.2`.
Configure as maquinas da rede1 com DHCP após configurar o servidor, o tutorial de como configurar o servidor está em `comandoaula4.md` nos tópicos `Configurar Servidor` e `Configurar Serviços do Servidor`, e configure de forma estática os ips da rede 2, assim como foi feito na aula.

Configure o link `www.unb.br` no DNS em Servidor->Services->DNS, adicione o nome como `www.unb.br` para o ip do servidor que no nosso caso é `192.168.5.2`.

## Segundo Passo - Conexão Entre Roteadores
Configuração:

1. Desligue os roteadores, e adicione a peça NIM-2T neles e depois religue eles.

2. Interligue os dois roteadores pelo cabo `Serial DCE` através da porta `Serial 0/1/0`

3. Para conectar duas redes através do roteador é preciso iniciar uma nova rede que irá conectar as duas, acesse o roteador da rede `192.168.5.1` e execute os comandos:

    ```bash
         enable
         configure terminal
         do show ip interface brief
         interface Serial0/1/0
         ip address 192.168.15.1 255.255.255.0
         no shutdown
         do wr
         exit
    ```

    E faça a mesma coisa no outro roteador trocando o ip do Serial para `192.168.15.2`

4. Vá nas máquina da segunda rede e altere o DNS do IPconfig para o ip do DNS do servidor da primeira rede que é o `192.168.5.2`
5. Abra o roteador da rede 1, Roteador->Config->RIP, e adicione as redes `192.168.15.0` e `192.168.10.0`, opcionalmente adicionando a própria rede do roteador mas não é obrigatório.
6. Abra o roteador da rede 2, Roteador->Config->RIP, e adicione as redes `192.168.15.0` e `192.168.5.0`, opcionalmente adicionando a própria rede do roteador mas não é obrigatório.
7. Mande pacotes entre os roteadores e máquinas, as primeiras vezes vai falhar mas acredite no seu potencial.

# Passo 3 - Adicionar Uma Nova Rede Triangulada
Inicialmente configure uma nova rede com roteador, switch e as máquinas no ip `192.168.30.0`, então:

1. Desligue o roteador e Adicone o adaptador `NIM-2T` e ligue o roteador novamente
2. Conecte o novo roteador aos outros da rede 1 e rede 2 com o cabo `Serial DCE`, para não se perder adicione documentação nas conexões com o número das redes e cada roteador pois cada conexão serial é um novo ip a ser trabalhado o que é muito fácil de se perder.
3. Agora você vai precisar entrar em cada um dos roteadores e configurar os IP's dos Seriais:
    Configuração do roteador `192.168.5.1`, roteador da primeira rede:

    ```bash
         do show ip interface brief
         interface Serial0/1/1
         ip address 192.168.40.1 255.255.255.0
         no shutdown
         do wr
         exit
    ```

    Configuração do roteador `192.168.10.1`, roteador da segunda rede:

    ```bash
         enable
         configure terminal
         do show ip interface brief
         interface Serial0/1/1
         ip address 192.168.25.1 255.255.255.0
         no shutdown
         do wr
         exit
    ```
    Configuração do roteador `192.168.30.1`, roteador da rede que acabou de ser criada:

    ```bash
         enable
         configure terminal
         do show ip interface brief
         interface Serial0/1/0
         ip address 192.168.40.2 255.255.255.0
         no shutdown
         exit
         interface Serial0/1/1
         ip address 192.168.25.2 255.255.255.0
         no shutdown
         do wr
         exit
    ```
4. Configuração do RIP, agora temos que configurar o RIP dos 3 roteadores para que eles saibam como se achar:
    - Roteador 1 (`192.168.5.1`) e Roteador 2 (`192.168.10.0`): Adicione os ips `192.168.40.0` e `192.168.25.2` no RIP desse roteador
    - Roteador 3 (`192.168.30.1`): Adicione os seguintes ips:
        - `192.168.5.0`
        - `192.168.10.0`
        - `192.168.15.0`
        - `192.168.25.0`
        - `192.168.30.0`
        - `192.168.40.0`
