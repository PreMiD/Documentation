---
title: Solução de problemas
description: Tudo para resolver o seu problema
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Certifique-se de ter a extensão **e** o aplicativo instalado! 
> 
> {.is-warning}

Incluído nesta página:
1. [Solução de problemas gerais](https://docs.premid.app/troubleshooting#general)
2. [Solução de problemas no Linux](https://docs.premid.app/troubleshooting#linux)
3. [Solução de problemas no MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Solução de problemas gerais
> Você pode usar [esta](https://qkeleq10.github.io/PreMiD-Troubleshooting/) ferramenta para identificar seu problema com mais facilidade. 
> 
> {.is-info}
### Recarregue a página
Você pode pressionar <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) ou <kbd>CMD+R</kbd> (MacOS) no seu teclado também, em vez de procurar pelo botão de recarregar.

### Você está usando o aplicativo do Discord?
O PreMiD **não** funciona na versão de navegador do Discord, você precisa baixar o aplicativo [aqui](https://discord.com/download).

### Certifique-se de que você ativou o Status de atividade do Discord nas configurações
**Configurações de Atividade** > **Status de atividade**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Certifique-se de que o Discord NÃO está sendo executado como administrador
Muito importante. O RPC do Discord não irá funcionar se executar o Discord como administrador.

### Você está usando uma presence com configurações?
Muitas presences (incluindo `Twitch` e `SoundCloud`) são afetadas por um problema na extensão. Esse problema faz com que a extensão não pegue corretamente os valores padrões das configurações.

Para resolver isso, tudo que você precisa fazer é desativar e reativar a configuração superior:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Reinicie o seu navegador
Usar <kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) ou <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) também serve. (Você tem que iniciar seu navegador em seguida, obviamente.)

### Reinicie o PreMiD (Aplicativo)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Recarregue/Reinicie o Discord
Pressione <kbd>CTRL+R</kbd> (Windows) ou <kbd>CMD+R</kbd> (MacOS) em seu teclado ou reinicie o Discord manualmente.

### Verifique se você tem antivírus ou firewall em execução no seu computador
Às vezes, programas de antivírus e firewalls irão bloquear aplicativos que estão criando/hospedando servidores ou apenas se conectando à internet. Usamos um servidor local para receber e transferir dados entre nosso app e a extensão, então, se você for bloquear o app de transferir dados, provavelmente não irá conseguir usar o PreMiD.

### Desative os seus complementos
Desative todas as suas extensões e addons e veja se funciona. Se sim, tente reativa-las uma a uma e nos informe qual é a que conflita com o PreMiD.

### Reinicie o seu computador
Espero que você saiba como reiniciar um computador.

### Reinstale o PreMiD
Às vezes, há algo de errado com os arquivos... Tutoriais de instalação podem ser encontrados [aqui](/install).

### Remoção manual
Windows: Digite `%appdata%` no explorador de arquivos e delete a pasta do `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` e delete a pasta do `PreMiD`.

### McAfee detectou PreMiD como vírus (Windows)
Este é um falso positivo da McAfee e relatamos o problema a eles, por enquanto, você pode excluir PreMiD da varredura, executando as seguintes etapas:

> Se você não se sentir seguro para seguir essas etapas, sinta-se à vontade para fazer um ticket em [#support](https://discord.premid.app/) (em inglês) e um de nossos Agentes de Suporte poderá ajudá-lo! 
> 
> {.is-warning}

1. Abra o aplicativo McAfee e clique no ícone de configurações no canto superior direito. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Clique em "Itens em quarentena" (segundo do topo).
3. Expanda, e clique no ícone `>` antes de um item com o nome "settings.dat".
4. Tenha certeza de que o caminho inclui "AppData\Local\Temp\PreMiD", se for o caso selecione e pressione restaurar.<img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Depois de restaurado, você pode fechar a janela "Itens em quarentena", depois pressione novamente o ícone de configurações no canto superior direito.
6. Clique em "Verificação em tempo real" (Terceira do topo).
7. Expanda-o e clique em "Adicionar arquivo".
8. Digite "%appdata%" na barra de endereço do gerenciador de arquivos e pressione Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Abra a pasta "PreMiD" e selecione o arquivo "PreMiD.exe" e clique em abrir. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee agora deve ignorar nosso arquivo, apenas inicie nosso aplicativo e você deve estar pronto para começar.

### Status do PreMiD com problema no Discord
Não se preocupe. Pressione as teclas <kbd>CTRL+R</kbd> (Windows) ou <kbd>CMD+R</kbd> (MacOS) enquanto a janela do seu Discord estiver em primeiro plano para recarregá-lo.

<a name="linux"></a>

# Solução de problemas no Linux
### Para distros baseadas em Ubuntu/Debian
Se você tiver baixado o Discord pelo Snapcraft, o RPC não funcionará. Você tem que desinstalar a versão do Snapcraft executando `sudo snap remove discord` no terminal, baixe a **[build pro Linux do Discord ](https://discordapp.com/api/download?platform=linux)** (**[ou o Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), então navegando para a pasta aonde baixou o Discord (usualmente em `$HOME/Downloads`), em seguida instale o pacote usando `sudo dpkg -i discord-*.deb`. Se o AppImage não funcionar, você deve considerar conferir nossos outros pacotes **[neste link](https://packagecloud.io/premid/linux)**.

### Para distros baseadas em Arch Linux
As distros baseadas no Arch Linux devem usar o pacote AUR (Arch User Repository/Repositório de usuários do Arch) chamado de <code>premid</code> ou <code>premid-git</code> (<em x-id="3">ATENÇÃO: Este repositório cria a build do premid a partir de nosso código-fonte.</em>). Se você não quiser instalar um gerenciador AUR (yay etc.), você pode checar nosso AppImage que pode ser baixado de nosso <strong x-id="1"><a href="https://github.com/premid/linux/releases">repositório Linux</a></strong>.
<em x-id="3">Atenção: o pacote no repositório <strong x-id="1">AUR</strong> não é mantido por nós (como organização PreMiD), mas por outras pessoas.</em>

### Vínculo de porta
Você deve saber que o <strong x-id="1">PreMiD</strong> se liga à porta <strong x-id="1">3020</strong>. Isso é necessário para que a Extensão e o Aplicativo se comuniquem. Se o <strong x-id="1">PreMiD</strong> mostrar um erro sobre esta porta, você deve checar se algo já está vinculado à porta 3020 executando <code>sudo lsof -i:3020</code> ou <code>sudo netstat -tnlp | grep:3020</code> em seu terminal. Se algum processo estiver vinculado a ela, certifique-se de liberar a porta e tentar executar o <code>PreMiD</code> novamente.

### AppImage do PreMiD não inicia no login
Como afirmamos em nosso **repositório Linux**, O AppImage não pode ser iniciado no login. Você pode adicionar na inicialização automática manualmente, executando estas etapas:
1. Crie um arquivo nomeado <strong x-id="1">rc.local</strong> na pasta <code>/etc</code>.
2. Abra este arquivo em seu editor favorito e cole o código fornecido com a alteração de algumas coisas:
```bash
#!/bin/bash
# Necessário para executar como /bin/bash (se você usar zsh etc. você pode alterá-lo.)

# Exemplo: /home/PreMiD/PreMiD*.AppImage
<caminho para o appimage>/PreMiD*.AppImage

exit 0
```
3. Salve o arquivo e execute um chmod nele como executável `sudo chmod a+x /etc/rc.local`.
4. Reinicie seu PC e o PreMiD AppImage deve iniciar no login.

<a name="macos"></a>

# Solução de problemas no MacOS
### Erro na criação de pasta
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

Se você receber esse erro, significa que sua conta não tem permissões de administrador e que é preciso criar a pasta manualmente seguindo estas etapas:
1. Abra o Finder e abra a pasta **Aplicativos**.
2. Clique com o botão direito em algum espaço em branco e clique em **Criar pasta**.
3. Para esta pasta, dê o nome de `PreMiD` (lembre-se das letras maiúsculas).
4. Abra o instalador novamente.

# Isso não resolveu o meu problema
Por favor, abra um ticket em [#support](https://discord.premid.app/).
