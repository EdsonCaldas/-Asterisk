# -Asterisk
Como habilitar videochamadas no Asterisk

Esses codecs não precisam ser instalados, eles já estão incluídos no Asterisk por padrão, no entanto, se você não fizer isso, siga as instruções abaixo com as alterações necessárias.

1- Instale o software Asterisk PABX

2- Se a opção de videochamada não estiver habilitada na GUI, a área de opções exibe um dos padrões de compressão de vídeo h261, h263, h263p, h264 ou mpeg4, você precisará fazer alterações ou adicionar um arquivo à pasta. .conf e mais um em extension.conf

3- Fazendo alterações no arquivo .conf

3.1 - abra o terminal e insira o caminho raiz vi /etc/asterisk/sip.conf, se o vi não funcionar, tente o vim, este comando irá abrir esta pasta no modo de visualização e pressione Enter para acessar a pasta

3.2- digite i para habilitar a inserção, se não houver arquivo, adicione o texto abaixo no final da documentação clicando na seta para baixo

context = default
bindaddr = 0.0.0.0
allow = ulaw
allow = alaw
allow = ilbc
allow = h263
allow = h263
allow = h263p
allow = h264
allow = mpeg4
videosupport = yes
textupport = yes
McCallbitrate = 384

[1000]
type = friend
callerid = "test" <1000>
username = 1000
secret = 1000
host = dynamic
nat = yes
canreinvite = no
context = internal
qualify = yes
allow = all
videosupport = yes

[1001]
type = friend
callerid = "test" <1001>
username = 1001
secret = 1001
host = dynamic
nat = yes
canreinvite = no
context = internal
qualify = yes
allow = all
videosupport = yes

Em seguida, digite esc e digite: qw para sair e salvar as alterações: w para salvar: q! para sair sem salvar as alterações e apenas: q para sair

3.3- depois de entrar em vi /etc/asterisk/extensions.conf para acessar

3.4- Seta para baixo ou tecla de página para baixo para adicionar o arquivo abaixo no final do código.

[interior]
exten => 1000.1, dial (SIP / 1000.25)
exten => 1000.2, Hang

[interior]
exten => 1002.1, dial (SIP / 1002.25)
exten => 1002.2, Hang

4. Após digitar serviço asterisco reiniciar e reiniciar, os programas de configuração serão adicionados à interface.
