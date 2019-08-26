# Zabbix + Telegram com Graficos

É muito simples monitorar com Zabbix, melhor ainda se você recebe os alertas em seu celular/computador via telegram!

Para que isto ocorra, basta inserir o script "zabbix-telegram.sh" dentro do seu diretório de alertscripts, exemplo "/usr/lib/zabbix/alertscripts"

##### Não esqueça de colocar a permissão de execução para o script (chmod 777 zabbix-telegram.sh)

Com o script dentro do diretório correto, abra-o e edite as linhas:
    
    ZBX_URL=""     URL DE LOGIN AO SEU ZABBIX
    USARNAME=""    USUARIO QUE ENVIA AS NOTIFICAÇÕES
    PASSWORD=""    SENHA O DO USUARIO
    BOT_TOKEN=""   TOKEN DO BOT TELEGRAM (Pode-se conseguir esta informação, falando com o "botfather" dentro do telegram)

##### IMPORTANTE COLOCAR EM "1" O "ENVIAR_GRAFICO" (Por padrão já deixei o valor 1 na variavel)

Agora vamos ensinar para o Zabbix enviar mensagens pelo Telegram:

Dentro de Administração > Tipos de Midias, adicione uma nova mídia

![zabbix-telegram0](https://user-images.githubusercontent.com/33628133/63696402-05364800-c7f1-11e9-8459-e537c5c0e8b3.png)

##### Dentro da Criação de Midia, coloque os campos "NOME", "NOME SCRIPT" e Adicione parametros como na imagem a baixo:

![zabbix-telegram2](https://user-images.githubusercontent.com/33628133/63696506-462e5c80-c7f1-11e9-9cd4-284f1f831923.png)

##### Agora o zabbix sabe que existe o telegram para enviar alertas 

![zabbix-telegram1](https://user-images.githubusercontent.com/33628133/63696588-6e1dc000-c7f1-11e9-9182-75b2964d96ff.png)

##### Agora vamos ensinar o usuario que enviará os alertas a ter os o telegram configurado:

    Dentro de Administração > Usuários
    Clique no usuario que deseja configurar > Midia: 

![zabbix-telegram-4](https://user-images.githubusercontent.com/33628133/63697055-7b877a00-c7f2-11e9-8fe5-a29b6374ca52.png)

##### Na tela de Midia, dentro do usuario, clique em "adicionar" no campo de midia
##### Agora precisa configurar o tipo, que no caso é o TELEGRAM que configuramos
##### no campo de "enviar para", coloque o ID de seu grupo/usuario no Telegram

![zabbix-telegram-5](https://user-images.githubusercontent.com/33628133/63697319-11bba000-c7f3-11e9-8e1a-af340b88eb5a.png)

Feito isto, salve e agora vamos para a parte Final que é dizer como o Zabbix deve enviar os alertas para o Telegram.

##### Agora vamos para Configuração > Ações
##### Dentro deste cara vamos configurar para que o zabbix mande para alertas de um numero X de hosts ou um numero X de grupos.

##### Clique em Criar ação

Você quiser que o zabbix mande informação de qualquer coisa, a parte de "nova condição" não precisa ser mexida, se não, coloque conforme sua necessidade.

Vamos para a Aba de "Operações e Operações de recuperação"

Estas abas elas simplismente são a mensagem de alerta caso tenha falha e recuperação.
Coloque no campo Operações, conforme a baixo:

##### Assunto padrão:
    
    Instabilidade: {EVENT.NAME}
    
##### Mensagem padrão:
    
    Indicente inicio {EVENT.TIME} no {EVENT.DATE}
    Instabilidade: {EVENT.NAME}
    Host: {HOST.NAME}
    Gravidade: {EVENT.SEVERITY}
    ID original da instabilidade: {EVENT.ID}
    Item Graphic: [{ITEM.ID1}}


Coloque no campo de Operações de recuperação, conforme a baixo


##### Assunto padrão:
    
    Resolvido: {EVENTO.NAME}

##### Mensagem padrão:

    Instabilidade resolvida as {EVENT.RECOVERY.TIME} no {EVENT.RECOVERY.DATE}
    Instabilidade: {EVENT.NAME}
    Host: {HOST.NAME}
    Gravidade: {EVENT.SEVERITY}
    ID da instabilidade: {EVENT.ID}
    Item Graphic: [{ITEM.ID1}}
    
    
Após isto, o zabbix está configurado para enviar mensagems para o telegram:




FIM
