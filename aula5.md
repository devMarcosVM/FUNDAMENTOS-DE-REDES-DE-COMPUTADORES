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



