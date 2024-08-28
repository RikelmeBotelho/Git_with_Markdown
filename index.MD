# Ajuda com o Git

A documentação a seguir foi desenvolvida para auxiliar na utilização de alguns comandos no Git e GitHub, abordando os seguintes tópicos:

* Como realizar o upload de arquivos para um repositório no Git.

* Como atualizar arquivos já existentes no Git.

* Como criar uma nova branch e como renomear uma branch existente.

* Como apagar uma branch no Git.

* Entendimento sobre o comando git force e suas aplicações.


## Como realizar o upload de arquivos para um repositório no Git ?

Se você ainda não configurou o Git em seu sistema, siga estas etapas para preparar sua instalação. A configuração inicial é importante para identificar quem está alterando o código e garantir que seus commits sejam atribuídos corretamente.

1. Abra o Terminal ou Linha de Comando

* No Windows, você pode usar o Prompt de Comando ou o Git Bash.

* No macOS ou Linux, use o Terminal.

2. Configure seu Nome e E-mail

* O Git usa seu nome e e-mail para registrar quem fez cada commit. Então comece com:

``` 
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
```
> Substitua o que está entre parênteses pelas suas informações.

> Usar --global configura as informações para todos os repositórios Git no seu sistema. É útil se você deseja usar o mesmo nome e e-mail em todos os projetos

Agora, o segundo passo é criar um repositório Git. Você pode fazer isso através do GitHub ou localmente, utilizando os seguintes comandos no seu terminal:


``` 
mkdir nome-do-repositorio
cd nome-do-repositorio
git init
```

Agora adicione todos os arquivos na pasta:

``` 
git add .
```
> Você pode adicionar separadamente utilizando "cp /caminho/para/seus/arquivos ."

Você pode ver se os arquivos foram adicionados utilizando o comando

``` 
Git status
```

Depois de adicionar os arquivos, você precisa fazer um commit para salvar as mudanças:

``` 
git commit -m "Mensagem de commit descrevendo as alterações"
```

Para conectar seu projeto a plataformas como GitHub, GitLab ou Bitbucket, crie um novo repositório na plataforma de sua escolha e copie o URL fornecido. Em seguida, utilize este URL para vincular seu projeto local ao repositório online, permitindo que você sincronize suas alterações e colabore com outros desenvolvedores.

``` 
git remote add origin https://github.com/usuario/nome-do-repositorio.git
```

Agora, envie suas mudanças para o repositório remoto:

``` 
git push -u origin main
```

## Como atualizar arquivos já existentes no Git ?

O Git é a ferramenta essencial para desenvolvedores que trabalham em equipe. Para manter seu projeto sempre atualizado e sincronizado com o repositório remoto, siga estas etapas:

1. Faça as alterações nos arquivos locais

* Abra os arquivos que você deseja modificar e faça as alterações necessárias.

2. Verifique o status do repositório

``` 
git status
```
> Isso mostrará quais arquivos foram modificados, adicionados ou deletados.

3. Adicione as alterações

* Para adicionar todos os arquivos modificados:

``` 
git add .
```

* Se você deseja adicionar apenas arquivos específicos:

``` 
git add nome_do_arquivo
```

4. Faça o commit das alterações

``` 
git commit -m "Mensagem descritiva sobre o que foi alterado"
```

5. Envie as alterações para o repositório remoto

* Para enviar as alterações para o repositório remoto (como GitHub, GitLab, etc.), use:

``` 
git push origin nome_da_branch
```
> Substitua nome_da_branch pelo nome da branch em que você está trabalhando (por exemplo, main ou master).

## Como criar uma nova branch e como renomear uma branch existente ?

Criar e renomear branches são ações fundamentais no dia a dia com Git, especialmente em equipes. Dominar esses comandos é crucial para um controle eficiente do código.

<u>Criando uma Branch</u>

1. Descubra em qual branch você está trabalhando: Antes de criar uma nova branch, utilize o comando:

``` 
git branch
```
> Isso listará todas as branches locais

2. Crie uma nova branch, use o seguinte comando:

``` 
git checkout -b nome-da-branch
```
> Substitua o "nome-da-branch" pelo nome da nova branch

> O parâmetro -b serve para criar uma nova branch e, ao mesmo tempo, passar a trabalhar nela. Se preferir criar a branch sem trocar para ela, omita o -b.

<u>Renomeando uma Branch</u>

1. Para renomear uma branch específica, é fundamental estar posicionado nela. Verifique sua branch atual com o comando:

``` 
git checkout nome-da-branch
```

2. Para mudar o nome da branch atual, use o comando:

``` 
git branch -m novo-nome
```
>Substitua novo-nome-da-branc pelo nome que você deseja. O -m significa "mover" ou "renomear" a branch.

3. Atualize o repositório remoto

>Antes de excluir a branch remota, garanta que todas as alterações relevantes foram mescladas ou que você possui um backup completo.

* Caso a branch já tenha sido enviada para um repositório remoto, é preciso atualizar o remoto. Comece removendo a branch antiga:

``` 
git push origin --delete nome-da-branch-antiga
```

* Em seguida, coloque a nova branch:

``` 
git push origin nome-da-branch-nova
```

* Agora, sincronize a nova branch com:

``` 
git push --set-upstream origin nome-da-branch-nova
```
>É essencial atualizar o rastreamento da branch após renomeá-la no Git para manter a sincronia com o repositório remoto.

## Como apagar uma branch no Git ?

Ao finalizar uma tarefa no Git, é comum excluir a branch para manter o repositório organizado.

<u>Apagando uma Branch Local</u>

1. Verifique a branch que você está:

``` 
git branch
```

2. Troque para outra branch:

``` 
git checkout nome-da-outra-branch
```

3. Apague a branch:

``` 
git branch -D nome-da-branch
```

<u>Apagando uma Branch Remota</u>

``` 
git push origin --delete nome-da-branch
```

>  Se o nome do seu repositório remoto for diferente de "origin", substitua-o no comando.

## Entendimento sobre o comando git force e suas aplicações.

O comando "git force" não existe como um comando separado. Quando as pessoas dizem "git force", geralmente estão falando sobre o uso de flags como --force em comandos como git push, git fetch ou git merge. Esses flags permitem executar ações que evitam conflitos ou diferenças entre versões locais e remotas.

No entanto, é importante enfatizar que o simples uso do --force pode levar à perda de dados e problemas de compatibilidade. Portanto, é importante entender os efeitos de cada comando e saber quando utilizá-lo.


<u>Quando usar?</u>

*  Reescrever o Histórico Local

* Corrigir Erros

* Manter o Repositório Limpo

<u>Cuidados a serem tomados:</u>

* Evite Usar em Branches Compartilhadas: Forçar o push em um branch compartilhado pode apagar as alterações de outros desenvolvedores, causando sérios conflitos

* Comunique a Equipe: Para evitar surpresas e possíveis perda de trabalho.