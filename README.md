# Projetos

Este tutorial foi feito porque executo a o meu Home Assistant em uma maquina virtual no Proxmox e as formas padrões de obter dados da maquina atraves do Home Assistant só obtem os dados da maquina virtual e não do Host, por isso fiz esse tutorial. Com esse metodo você vai ser capaz de obter os dados de temperatura, uso de cpu e uso de ram diretamente do servidor Proxmox.

Os comandos a seguir são executados no complemento Terminal & SSH do Home Assistant

Este comando é usado para gerar a chave SSH na maquina virtual do Home Assistant
ssh-keygen

Este comando envia a chave ssh para o servidor Proxmox
ssh-copy-id root@ip_do_proxmox
**após esse comando será solicitado a sua senha de root do proxmox, preencha como solicitado

Cria um diretorio com o nome .ssh na pasta config do Home Asistant
mkdir -p /config/.ssh

Copia o arquivo id_rsa do diretorio /root do Proxmox para o diretorio que acabamos de criar na pasta config do Home Assistant
cp /root/.ssh/id_rsa /config/.ssh/id_rsa

Comando para testar se está OK, importante usar o argumento -i para o proxmo não pedir a senha root
ssh -i /config/.ssh/id_rsa root@ip_do_proxmox

Sair da conexão
exit
