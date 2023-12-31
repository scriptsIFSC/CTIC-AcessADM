# Acesso ao CTIC Windows - Requisitos: PCs com Windows e Linux

## Técnicas Utilizadas: Reinicialização com Parâmetros Especiais, Sticky Keys Backdoor

Este documento descreve os passos necessários para acessar o sistema operacional Windows do CTIC utilizando uma combinação de técnicas, como a reinicialização com parâmetros especiais e a exploração da vulnerabilidade conhecida como "Sticky Keys Backdoor".

### Passo 1: Desligamento Completo dos Processos do Windows

Para garantir que todos os processos do Windows sejam desligados completamente:

1. Ao desligar o Windows, segure a tecla "SHIFT" enquanto seleciona a opção de desligar. Isso garante o desligamento completo dos processos.

### Passo 2: Acesso ao GRUB do Linux Ubuntu

1. Após o desligamento completo do Windows, inicie o computador.
2. Na tela de seleção de Sistema Operacional (Windows ou Linux Ubuntu), selecione o Linux Ubuntu, mas não entre no sistema.
3. Pressione a tecla "e" para editar as configurações do GRUB.
4. Localize a linha que começa com "linux" ou "linuxefi" e vá até o final dela.
5. Adicione o parâmetro `init=/bin/bash` ao final da linha.
6. Pressione "Ctrl+X" ou "F10" para iniciar o sistema com as alterações.

Este passo apenas do GRUB pode ser necessário executar duas vezes.

### Passo 3: Sticky Keys Backdoor

1. Após entrar no terminal bash, execute os seguintes comandos:

   ```bash
   fdisk -l # Para listar as partições e identificar a partição do Windows (provavelmente sob "Microsoft data")
   mkdir /mnt/windows # Criar uma pasta para montar a partição do Windows
   mount {caminho_da_partição_windows} /mnt/windows # Substitua {caminho_da_partição_windows} pelo caminho correto
   cd /mnt/windows/Windows/System32 # Acessar o diretório do sistema Windows
   mv sethc.exe sethc1.exe # Renomear arquivos para criação da backdoor
   mv cmd.exe sethc.exe
   ```

2. Reinicie o sistema Windows.

### Passo 4: Alteração da Senha Local do Usuário CTIC

1. Após reiniciar e acessar o Windows:
2. Se estiver logado como usuário "IFSC", pressione as teclas `Windows + L` para bloquear a tela.
3. Pressione a tecla SHIFT cinco vezes para acionar um prompt de comando com privilégios de administrador.
4. Execute o comando:

   ```bash
   control userpasswords2
   ```

5. Na janela de configuração de contas de usuário, acesse a aba "Avançado" e clique no botão correspondente.
6. Selecione o usuário "CTIC" e clique em "Mais ações" e, em seguida, "Redefinir senha". Ou clique com o botão direito no usuário "CTIC" e selecione "Redefinir senha".
7. Insira a nova senha desejada.
8. Faça login com a nova senha no usuário "CTIC".


**Aviso Importante: Responsabilidade pelo Uso das Instruções**

As instruções fornecidas neste documento são fornecidas apenas para fins educacionais e informativos. Qualquer utilização destas instruções é de total responsabilidade do usuário. Não me responsabilizo por quaisquer danos, perdas, alterações indesejadas ou consequências resultantes da aplicação destas instruções em qualquer computador ou sistema operacional.

Ao prosseguir com a execução dessas etapas, você reconhece e concorda que está ciente dos riscos envolvidos na realização de ações que podem afetar o funcionamento normal de um sistema. Recomenda-se que você possua autorização adequada e conhecimento técnico para realizar essas ações, e que você siga todas as leis, regulamentos e políticas de segurança aplicáveis.

Lembre-se de que explorar vulnerabilidades ou realizar modificações não autorizadas em sistemas pode ter implicações legais graves. Certifique-se de obter permissão adequada e de agir de acordo com os regulamentos e diretrizes antes de executar qualquer procedimento mencionado neste documento.
