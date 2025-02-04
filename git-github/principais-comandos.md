# Principais comandos de navegação em diretórios
- **ls**: visualizar diretórios
- **cd [*nome-pasta*]**: entrar em uma pasta
- **cd ..**: subir um nível de pasta
- **mkdir [*nome-pasta*]**: criar uma pasta
- **rmdir [*nome-pasta*]**: deletar uma pasta

# Principais comandos Git
- **git config** 
    - **--global user.name "[*nome-usuário*]"**: conecta a máquina local ao usuário do github por meio do nome de usuário
    - **--global user.email "[*email-usuário*]"**: conecta a máquina local ao usuário do github por meio do email
    - **--list**: lista as configurações atuais
- **git init**: inicializa o rastreamento do diretório selecionado pelo git
- **git status**: visualiza o status de atualização dos arquivos
- **git remote** 
    - **--v**: verificar se há origem remota do repositório
    - **add origin**: criar uma origem remota do repositório
- **git clone [*endereço https ou ssh*]**: clona um repositório do remoto para a máquina local
- **git add**
    - **[*nome-arquivo*]**: adiciona alterações de um arquivo local específico ao índice ou staging area do Git
    - **.** : adiciona alterações de todos os arquivos locais de uma pasta específica ao índice ou staging area do Git
- **git commit**
    - **-m "[*mensagem-descritiva*]"**: insere uma mensagem ao commitar os arquivos de um repositório (enviar as alterações do repositório local para o repositório Git)
- **git push**: insere os arquivos e atualizações do repositório no github
    - **--set-upstream origin [*nome-branch*]**: conecta o repositório local à branch no github
- **git checkout**
    - **-b [*nome-branch*]**: cria e migra para uma nova branch
    - **[*nome-branch*]**: migra para a branch desejada
- **git branch**: lista as branches existentes
- **git merge [*nome-branch*]**: incorpora os arquivos da branch desejada na branch atual, unindo-as em uma só branch

# Anotações extras
- **git init x git remote add origin**: o comando git init cria um novo repositório Git, enquanto o comando git remote add origin adiciona um repositório remoto no GitHub;
- **git add x git commit**: o git add é similar ao comando commit, mas não commita as mudanças. O commit confirma os arquivos adicionados e cria uma nova revisão;
- **arquivos .git em diretórios**: caso faça git init em um diretório do repositório, esta pasta não poderá ser acessada no github. Por isso, certifique-se de inicializar o git no caminho do repositório, não em uma de suas pastas;
- **git merge e commits**: para garantir a efetividade da junção de duas branches, recomenda-se commitar todas as alterações de cada uma separadamente antes de utilizar o comando git merge. Além disso, fazer um merge também é considerado uma alteração a ser commitada em ambas as branches.

