# Git e Github
Durante o meu aprendizado no curso fiz anatações e teste prático para entender o máximo das funcionalidades do Git. Aprendi desde comandos básicos e até formas de utilizar o programa em equipe, deixarei registrado esse README com os testes com as anotações.
</br>
*Curso ministrado pela plataforma Alura*
</br>
## Indice 
- Comandos básicos para iniciar Git
- Branch
- Merge
- Rebase
- Log
- Checkout
- Reset
- Revert
- Stash
- Diff
- Tag
</br>
### Comandos básicos para iniciar Git
O Git é um sistema de controle de versão utilizado para gerenciar projetos de software. Ele permite que várias pessoas trabalhem em um mesmo projeto ao mesmo tempo, sem que haja conflitos de versões. O GitHub é uma plataforma que utiliza o Git para hospedar repositórios de código-fonte.
</br>
### Comandos Básicos:
- `git init`: inicializa um novo repositório Git.
- `git add <arquivo>`: adiciona um arquivo ao stage (área de preparação).
- `git commit -m "<mensagem de commit>"`: salva as mudanças no repositório com uma mensagem de commit.
- `git status`: mostra o status atual do repositório.
- `git log`: mostra o histórico de commits do repositório.
- `git push`: envia mudanças locais para o repositório remoto.
- `git pull`: baixa mudanças do repositório remoto para o repositório local.
</br>
#### Branch 
    Uma branch no Git é uma ramificação do código-fonte que permite que diferentes versões do mesmo projeto sejam desenvolvidas simultaneamente. Ela permite que um grupo de desenvolvedores trabalhe em uma funcionalidade específica sem interferir no trabalho de outros desenvolvedores e, posteriormente, mesclar as alterações das diferentes branches em uma única versão final. Além disso, as branches podem ser usadas para criar versões de correção de bugs ou para testar novas funcionalidades sem afetar a versão principal do projeto. O Git permite criar, renomear, visualizar e mesclar branches de forma simples e intuitiva.
    
    Para criar uma nova branch, podemos utilizar o seguinte comando:
    
    ```
    git branch nome_da_branch
    
    ```
    
    Para mudar para a nova branch criada, utilizamos o comando:
    
    ```
    git checkout nome_da_branch
    
    ```
    
    Para criar e mudar para a nova branch de uma vez, podemos utilizar o comando:
    
    ```
    git checkout -b nome_da_branch
    
    ```
    
    Lembre-se de sempre fazer o *commit* das alterações antes de mudar de branch.
    
</br>
#### Merge
    
    O *merge* é uma operação no Git que combina alterações de várias branches em uma única branch. Isso é útil quando diferentes desenvolvedores trabalham em diferentes partes do mesmo projeto ou quando uma nova funcionalidade é desenvolvida em uma branch separada. O *merge* é usado para combinar as alterações de uma branch com outra, geralmente com a branch principal do projeto. Quando um *merge* é realizado, as alterações são mescladas e os conflitos são resolvidos, criando uma nova versão do projeto que contém as alterações de ambas as branches. O Git possui várias ferramentas para ajudar a resolver conflitos de mesclagem e, em geral, o processo de *merge* é bastante simples e intuitivo.
    
    O comando básico para realizar um merge no Git é:
    
    ```
    git merge nome_da_branch
    
    ```
    
    Esse comando realiza a mesclagem da branch atual com a branch especificada no argumento `nome_da_branch`. É importante lembrar que é necessário estar na branch que receberá as alterações antes de executar o comando.
    
    Caso ocorram conflitos durante o merge, é necessário resolvê-los manualmente antes de realizar o commit. Para isso, o Git oferece algumas ferramentas para auxiliar na resolução de conflitos, como o `git mergetool`.
    
    Para resolver conflitos de merge no Git, é necessário seguir os seguintes passos:
    
    1. Identificar os conflitos: após realizar o merge, o Git irá informar quais arquivos estão em conflito. Esses arquivos terão marcações especiais que indicam as diferenças entre as versões.
    2. Editar os arquivos conflitantes: abra os arquivos conflitantes em um editor de texto e resolva as diferenças manualmente. O Git irá destacar as diferenças e permitir que você escolha qual versão deseja manter.
    3. Salvar as alterações: após editar os arquivos conflitantes, salve as alterações.
    4. Adicionar os arquivos ao stage: use o comando `git add` para adicionar os arquivos conflitantes ao stage.
    5. Completar o merge: use o comando `git merge --continue` para completar o merge. O Git irá criar um novo commit com as alterações mescladas.
    
    É importante lembrar que conflitos de merge podem ocorrer quando duas ou mais alterações diferentes são feitas no mesmo arquivo e na mesma linha. Para evitar conflitos, é recomendado que os desenvolvedores trabalhem em diferentes branches e que as alterações sejam mescladas apenas quando estiverem prontas. Além disso, é importante que os desenvolvedores se comuniquem e coordenem suas atividades para evitar conflitos desnecessários.
    
</br>

#### Rebase
    
    O *rebase* é uma operação no Git que permite alterar o histórico de commits de uma branch. Ele é usado para integrar as alterações de uma branch com outra, geralmente com a branch principal do projeto, mas de forma que o histórico de commits pareça linear e mais fácil de entender. O *rebase* é útil quando várias branches são criadas a partir da mesma branch principal e se deseja manter o histórico de commits mais organizado.
    
    O comando básico para realizar um rebase no Git é:
    
    ```
    git rebase nome_da_branch
    
    ```
    
    Esse comando aplica as alterações da branch especificada no argumento `nome_da_branch` à branch atual, modificando o histórico de commits da branch atual. É importante lembrar que o rebase pode causar conflitos de mesclagem e, nesse caso, é necessário resolvê-los manualmente antes de realizar o commit.
    
    O *rebase* também pode ser usado para reordenar os commits de uma branch, permitindo que eles sejam apresentados em uma ordem mais lógica e fácil de entender.
    
    Para corrigir conflitos de rebase no Git, siga os seguintes passos:
    
    1. Execute o comando `git rebase nome_da_branch`. Se houver conflitos, o Git irá parar o rebase e informar quais arquivos estão em conflito.
    2. Abra os arquivos conflitantes em um editor de texto e resolva as diferenças manualmente. O Git irá destacar as diferenças e permitir que você escolha qual versão deseja manter.
    3. Adicione os arquivos conflitantes ao stage usando o comando `git add`.
    4. Continue o rebase usando o comando `git rebase --continue`. O Git irá aplicar as alterações e continuar o rebase até a conclusão ou até encontrar outro conflito.
    5. Repita os passos 2 a 4 para cada conflito encontrado.
    6. Verifique se o rebase foi concluído com sucesso usando o comando `git log` ou `git reflog`.
    
    Lembre-se de que o rebase pode alterar o histórico de commits de uma branch e pode causar conflitos de mesclagem. Por isso, é importante utilizá-lo com cuidado e sempre verificar se o resultado final é o esperado.
    
</br>

#### Log
    
    O comando `git log` é usado para visualizar o histórico de commits de um repositório Git. Ele mostra a lista de commits em ordem cronológica reversa, ou seja, do mais recente para o mais antigo. Cada commit contém informações como o autor, a data, a mensagem de commit e um hash que identifica exclusivamente aquele commit.
    
    Algumas opções úteis para o comando `git log` são:
    
    - `-oneline`: mostra cada commit em uma única linha, com o hash e a mensagem de commit
    - `-graph`: mostra o histórico de commits em forma de grafo, com as branches e as junções entre elas
    - `-author=nome`: filtra os commits pelo autor especificado
    - `-since=data`: filtra os commits a partir da data especificada
    
    Exemplos de uso do comando `git log`:
    
    ```
    git log --oneline
    git log --graph
    git log --author="João da Silva"
    git log --since="2022-01-01"
    
    ```
    
    Para sair do log, basta pressionar a tecla `q`.
    
</br>

#### Checkout
    
    O comando `git checkout --` é usado para descartar as mudanças feitas em um arquivo que ainda não foi adicionado ao stage. Ele reverte o arquivo para a última versão salva no repositório Git, ignorando as mudanças feitas desde a última atualização. É importante lembrar que o comando `git checkout --` é uma ação irreversível, ou seja, as mudanças serão perdidas permanentemente. Por isso, é recomendado usar esse comando apenas em situações em que as mudanças não são necessárias ou estão incorretas. Para descartar as mudanças de um arquivo que já foi adicionado ao stage, use o comando `git reset HEAD nome_do_arquivo`.
    

</br>

#### Reset
    
    O comando `git reset HEAD pasta` é usado para remover a pasta especificada do stage. Isso significa que as mudanças feitas na pasta não serão incluídas no próximo commit. É importante lembrar que o comando `git reset` é uma ação irreversível, ou seja, as mudanças serão perdidas permanentemente, a menos que sejam salvas em um commit anterior. Por isso, é recomendado usar esse comando com cuidado e sempre verificar se as mudanças são realmente desnecessárias antes de executá-lo.
    

</br>

#### Revert
    
    <aside>
    👉 O comando `git revert` é usado para desfazer um commit anterior em um repositório Git. Diferentemente do comando `git reset`, que remove permanentemente um commit e todas as alterações subsequentes, o `git revert` cria um novo commit que desfaz as alterações do commit anterior. Isso é útil quando é necessário desfazer alterações em um commit específico, mas manter o histórico de commits do projeto. Para usar o `git revert`, basta especificar o hash do commit que deseja desfazer:
    
    ```
    git revert <hash_do_commit>
    
    ```
    
    O Git irá abrir o editor de texto padrão para permitir que você adicione uma mensagem de commit para o novo commit que reverte as alterações do commit especificado. Depois de salvar a mensagem de commit, o Git irá criar um novo commit que desfaz as alterações do commit especificado.
    
    </aside>
    
</br>

#### Stash
    
    O comando `git stash` é usado para armazenar temporariamente as mudanças que ainda não foram adicionadas ao stage em uma área de armazenamento temporário chamada stash. Isso permite que você salve as alterações em um estado intermediário sem precisar criar um novo commit. O stash é útil quando você precisa mudar de branch ou fazer outras alterações que não estão prontas para o commit, mas não quer perder as mudanças que já foram feitas.
    
    O comando básico para usar o stash no Git é:
    
    ```
    git stash
    
    ```
    
    Esse comando armazena as mudanças ainda não adicionadas no stash e reverte a pasta de trabalho para a última versão salva no repositório Git. Para recuperar as mudanças armazenadas no stash, use o comando `git stash apply`. Esse comando irá aplicar as mudanças do stash na pasta de trabalho atual. Se houver mais de um stash, você pode especificar o stash que deseja aplicar usando o comando `git stash apply stash@{n}`.
    
    Para listar os stashes existentes, use o comando `git stash list`. Esse comando mostra uma lista dos stashes existentes, com uma mensagem de descrição para cada um. Para excluir um stash específico, use o comando `git stash drop stash@{n}`. Isso remove o stash especificado da lista de stashes e o exclui permanentemente. Se você quiser recuperar as mudanças armazenadas em um stash e excluí-lo ao mesmo tempo, use o comando `git stash pop`.
    
    O stash também pode ser usado para salvar mudanças parciais em um arquivo específico. Para isso, use o comando `git stash save --patch nome_do_arquivo`. Esse comando irá abrir uma interface interativa que permite selecionar as mudanças que deseja armazenar no stash. Você pode selecionar as mudanças que deseja armazenar e ignorar as mudanças que não deseja armazenar.
    
    Para resumir, o stash é uma ferramenta útil para armazenar temporariamente as mudanças que ainda não estão prontas para o commit, permitindo que você mude de branch ou faça outras alterações sem perder as mudanças que já foram feitas.
    
</br>

#### Diff
    O comando `git diff` é usado para mostrar as diferenças entre o conteúdo atual do repositório e um commit anterior, um branch ou um arquivo específico. Ele é útil para verificar as mudanças feitas em um arquivo antes de adicioná-lo ao stage ou para verificar as diferenças entre duas versões do projeto.
    
    Algumas opções úteis para o comando `git diff` são:
    
    - `-cached`: mostra as diferenças entre o conteúdo atual do stage e o último commit
    - `-name-only`: mostra apenas os nomes dos arquivos modificados
    - `-color-words`: mostra as diferenças em palavras em vez de linhas inteiras
    - `-color-moved`: mostra as linhas que foram movidas entre arquivos
    - `HEAD~n`: mostra as diferenças em relação ao commit `n` anterior ao HEAD
    
    Exemplos de uso do comando `git diff`:
    
    ```
    # mostra as diferenças entre o HEAD e o commit anterior
    git diff HEAD^ HEAD
    
    # mostra as diferenças entre o HEAD e o commit anterior ao anterior
    git diff HEAD~2 HEAD
    
    # mostra as diferenças entre o stage e o último commit
    git diff --cached
    
    # mostra as diferenças em um arquivo específico
    git diff nome_do_arquivo
    
    # mostra apenas os nomes dos arquivos modificados
    git diff --name-only
    
    # mostra as diferenças em palavras em vez de linhas inteiras
    git diff --color-words
    
    # mostra as linhas que foram movidas entre arquivos
    git diff --color-moved
    
    ```
    
    O `git diff` é uma ferramenta poderosa e versátil para verificar as diferenças entre versões do projeto e para verificar as mudanças feitas em um arquivo antes de adicioná-lo ao stage. É importante lembrar que o `git diff` mostra apenas as diferenças e não faz alterações no repositório Git. Para salvar as mudanças, é necessário adicioná-las ao stage e fazer um commit.
    
</br>

#### Tag:
    
    O comando `git tag` é usado para criar, listar e deletar tags no Git. As tags são referências estáticas para um commit específico, permitindo que você marque pontos importantes na história do projeto, como versões de lançamento ou pontos de referência para o desenvolvimento. As tags também podem ser usadas para criar releases no GitHub ou em outras plataformas de hospedagem de código.
    
    Para criar uma nova tag no Git, use o comando `git tag nome_da_tag`. Esse comando irá criar uma nova tag com o nome especificado apontando para o commit atual. Se você quiser criar uma tag em um commit específico, use o comando `git tag nome_da_tag hash_do_commit`. Isso irá criar uma nova tag com o nome especificado apontando para o commit com o hash especificado.
    
    Para listar as tags existentes, use o comando `git tag -l`. Isso irá mostrar uma lista das tags existentes em ordem alfabética. Se você quiser listar as tags em ordem cronológica, use o comando `git tag --sort=-creatordate`. Isso irá mostrar uma lista das tags existentes em ordem cronológica reversa.
    
    Para excluir uma tag existente, use o comando `git tag -d nome_da_tag`. Isso irá excluir a tag com o nome especificado. Se você quiser excluir uma tag remota, use o comando `git push --delete origin nome_da_tag`.
    
    Para fazer o checkout de uma tag específica, use o comando `git checkout nome_da_tag`. Isso irá mudar para o commit que a tag especificada aponta, permitindo que você trabalhe com uma versão específica do projeto. É importante lembrar que o checkout de uma tag específica coloca você em um estado "detached HEAD", o que significa que as alterações feitas não serão salvas no branch atual.
    
    Para criar uma tag anotada, que inclui uma mensagem de tag, use o comando `git tag -a nome_da_tag -m "mensagem_da_tag"`. Isso irá criar uma nova tag anotada com o nome e a mensagem especificados.
    
    Para fazer o push de uma tag para um repositório remoto, use o comando `git push origin nome_da_tag`. Isso irá enviar a tag especificada para o repositório remoto, permitindo que outros desenvolvedores acessem a tag. Se você quiser fazer o push de todas as tags existentes para um repositório remoto, use o comando `git push --tags`.
    
    Em resumo, o comando `git tag` é usado para criar, listar e deletar tags no Git. As tags são úteis para marcar pontos importantes na história do projeto e para criar releases para o projeto. Para usar o `git tag`, basta seguir as instruções acima e adaptá-las às suas necessidades específicas.