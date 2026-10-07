# Índice

* [Itens necessários](#itens-necessários)
* [Identificar dados corrompidos](#identificar-dados-corrompidos)
* [Como remover dados corrompidos](#como-remover-dados-corrompidos)
* ["A correção usual"](#a-correção-usual)
* [Prevenir a corrupção de dados](#prevenir-a-corrupção-de-dados)
* [Mais recursos](#mais-recursos)

> **Faça um backup completo dos seus arquivos de save antes de tentar qualquer uma destas etapas!**

---

# Itens necessários

## Pasta de Mods do Steam Workshop (Mods do Workshop)

* Pode ser acessada clicando no ícone de pasta de um mod do Steam Workshop no menu de Mods do Paralives.
* Navegando até:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Pasta do Paralives (Mods locais)

* Pode ser acessada clicando no ícone de pasta de um mod local no menu de Mods do Paralives.
* Navegando até:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Pode ser lido com qualquer software de leitura de arquivos de texto, como o Notepad ou Notepad++.
* Localizado na pasta Paralives\Paralives.
* Fornece registros da sessão atual ou da última sessão do Paralives.

## Pasta Paralives\MySavedGames.mod

* Pasta que contém todos os saves atuais e autosaves.
* Localizada na pasta Paralives\Paralives.
* Esta pasta é mais importante do que qualquer outra.
* Faça regularmente uma cópia completa desta pasta e mantenha-a em um local seguro fora dos arquivos do jogo!

## Pasta Paralives\MyPremadeHouseholds.mod

* Famílias salvas na biblioteca.

## Pasta Paralives\MyPremadeLot.mod

* Lotes salvos na biblioteca.

## Pasta Paralives\MyPremadeOutfits.mod

* Roupas salvas na biblioteca.

## Pastas Paralives\Local.mod e 0.mod

* Armazenam configurações do jogo, como paletas de cores personalizadas.

---

# Identificar dados corrompidos

Dados corrompidos são constituídos por arquivos que foram alterados e já não estão no formato ou na sequência que o jogo espera encontrar.

## Arquivos desatualizados

* O jogo foi atualizado e esses arquivos já não estão de acordo com a sintaxe atual.
* Embora isso possa acontecer ocasionalmente com mods, quase todos os plugins de injeção de código do BepInEx ficam desatualizados após uma atualização do jogo.
* Se um plugin BepInEx estiver instalado, mas os mods ainda não estiverem funcionando, o plugin pode estar causando mais problemas do que ajudando.

## Arquivos modificados incorretamente

* Estes arquivos foram modificados por um jogador, modder ou até mesmo pelo mecanismo do jogo e agora estão incorretos.
* Isso ocorre quando mods ou plugins são usados e depois removidos.

Por exemplo, um mod usado para adicionar uma roupa personalizada é removido, mas a roupa continua sendo identificada nos arquivos do jogo.

Pode ser impossível remover alguns mods sem corromper um arquivo de save.

## Arquivos movidos incorretamente

* Os arquivos são frequentemente movidos pelo jogador, pelo mecanismo do jogo ou pelo Steam, e algumas partes do arquivo acabam sendo deixadas para trás ou excluídas.

## Como o jogo me informará quais arquivos estão corrompidos?

O mecanismo do jogo tentará informar ao usuário quando houver um erro por meio de notificações diretas e indiretas.

### Diretas:

* Pop-ups na tela
* Notificações no console
* Eventos no player.log

### Indiretas:

* Cintilação
* Piscadas
* Travamentos momentâneos
* Lag
* Crashes
* Operações sendo canceladas

## Lendo o Console de Erros e o Player.Log

Os relatórios do console de erros e do player.log se sobrepõem apenas parcialmente, portanto é importante verificar ambos ao tentar identificar um erro.

É importante identificar o erro inicial e ignorar os erros adicionais causados pelo primeiro erro. Ao ler o log de erros, tente corrigir os erros de cima para baixo, em ordem sequencial.

Se vários erros forem introduzidos ao mesmo tempo, pode ser muito difícil diagnosticar o problema. É importante fazer apenas um pequeno número de alterações entre os testes.

Se o jogo estiver funcionando normalmente, anote os erros no log para que eles possam ser descartados posteriormente caso algo apresente problemas.

### CONSOLE DE ERROS

* O console de erros pode ser acessado dentro do jogo como uma aba no menu de cheats.
* Ele não pode ser usado se o jogo não carregar.

1. Pressione Ctrl+Shift+C para abrir o menu de cheats.
2. Pressione a seta para alternar para a aba do console.
3. O console é dividido em três categorias de importância.
4. Apenas os erros vermelhos são importantes para os fins deste tutorial.

### PLAYER.LOG & PLAYER-PREV.LOG

* Este arquivo registra as ações realizadas pelo mecanismo de jogo Unity que executa o Paralives.
* O Player.log é sobrescrito cada vez que o jogo é iniciado e movido para Player-prev.log.
* Ele está localizado na pasta de mods locais Paralives\Paralives.
* Mais informações podem ser adicionadas ao log ativando opções no painel de controle. Muitas opções podem rapidamente fazer com que o log fique muito grande.
* Se algo no log for importante, faça uma cópia!

### Erros bons (ou pelo menos não ruins):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Erros ruins:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Nota: Na versão 1.7, há três novos erros vermelhos no console e no player.log que não parecem afetar negativamente o desempenho do jogo.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Nota: Na versão 1.8A, o importador de .fbx não funcionava corretamente e ficava travado na tela de importação de assets.

---

# Tipos de erros

Os tipos de problemas que estão ocorrendo em nível técnico.

## Referência nula

* Às vezes chamada de referência de ponteiro nulo.
* Qualquer erro indicando que uma configuração, item, malha ou valor não pôde ser encontrado.
* O jogo faz referência a um objeto que não consegue encontrar ou não conseguiu interpretar.

> Nota: O jogo consegue lidar com algumas referências nulas, e várias delas fazem parte da versão de acesso antecipado do jogo.

## Fora dos limites

* O jogo recebeu um valor fora do intervalo esperado.
* Se o jogo espera um valor entre 0 e 10, mas recebe 10842, isso pode causar um erro.

## Tradução

* O jogo tentou corrigir um arquivo que foi determinado como corrompido, mas o resultado estava incorreto.

Por exemplo, um problema envolvendo arquivos .tmp, .mod.meta e .tmp.

## Sintaxe

* O jogo foi atualizado e o mod não está mais de acordo com os padrões definidos pelo jogo. Isso é mais comum com plugins de injeção de código BepInEx.
* Alguns mods criados quando o jogo foi lançado estão sem dois-pontos nos arquivos de texto.

---

# Categorias de sintomas

Quando a causa do erro é desconhecida, o objetivo é correlacionar os sintomas a uma causa específica. Depois que cada erro for corrigido, o jogo funcionará. Estas são categorias arbitrárias para ajudar a agrupar erros semelhantes em conjuntos.

É importante identificar o erro inicial e ignorar os erros adicionais causados pelo primeiro erro.

## Cat A — Iniciar o jogo

### Sintomas

* O jogo não consegue chegar ao menu principal do Paralives
* A tela fica preta
* O jogo fecha ao iniciar pelo Steam
* Um erro aparece ao iniciar o jogo pelo Steam
* O jogo fica travado em uma imagem de nuvens.

### Possíveis soluções

* Verifique se o hardware atende aos requisitos mínimos para jogar Paralives.
* Um arquivo crítico usado durante a inicialização do jogo está corrompido, ilegível ou inacessível.
* Comece verificando os arquivos do jogo.
* Crie uma exceção para o Paralives no antivírus.
* Verifique o player.log em busca de erros na pasta de mods locais paralives/paralives.

## Cat B — Importar assets

### Sintomas

* Travado na importação de assets

### Possível causa

Um arquivo de mod não pode ser lido.

### Possíveis soluções

* Remova os mods mais recentes da pasta de mods locais paralives/paralives ou das pastas do Steam Workshop até que o problema seja resolvido.
* Verifique os arquivos do jogo.

## Cat C — Selecionar um save

### Sintomas

* O jogo retorna ao menu principal ao tentar carregar um save
* O arquivo de save aparece em branco

### Possível causa

O arquivo de save possui nomes de arquivos incorretos, está com arquivos faltando ou não pode ser lido.

### Possível solução

Comece verificando se o nome do save corresponde aos arquivos meta dentro dele e se o save contém todos os componentes necessários.

## Cat D — Carregar um save

### Sintomas

* O jogo trava durante o carregamento do save
* O jogo permanece na tela de carregamento indefinidamente

### Possível causa

Mod corrompido, mod removido incorretamente ou corrupção do arquivo de save, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de save.

### Possível solução

Teste se os erros continuam ocorrendo em um novo save.

## Cat E — Modo de jogo

### Sintomas

* O jogo trava ou congela ao abrir um menu no modo de jogo
* O jogo trava ou congela ao realizar uma ação específica no modo de jogo

### Possível causa

Mod corrompido, mod removido incorretamente ou corrupção do arquivo de save, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de save.

### Possível solução

Teste se os erros continuam ocorrendo em um novo save.

## Cat F — Menus

### Sintomas

* O menu do jogo não abre ao clicar
* O menu do jogo aparece em branco ao clicar
* O menu do jogo não fecha

### Possível causa

Mod corrompido, mod removido incorretamente ou corrupção do arquivo de save, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de save.

### Possível solução

Teste se os erros continuam ocorrendo em um novo save.

## Cat G — Instalar mods

### Sintomas

* Os mods não são instalados

### Possíveis soluções

* Verifique as pastas de mods do Steam e Local em busca de arquivos parciais.
* Exclua os arquivos de mods corrompidos que estejam impedindo o download.

## Cat H — Mods ausentes

### Sintomas

* Os mods instalados não aparecem no menu de mods
* Os mods instalados aparecem no menu de mods, mas não aparecem no jogo

### Possíveis soluções

* Verifique se há mods corrompidos.
* Verifique se existem arquivos de mods duplicados.

## Cat I — Validar mods

### Sintomas

* Os itens de mods instalados não aparecem quando equipados no personagem
* Os itens de mods instalados desapareceram
* O personagem com itens de mods desapareceu
* Os itens de mods parecem estranhos
* Os itens de mods interagem de maneira inesperada
* Os itens de mods apresentam a cor, forma ou tamanho incorretos

### Possível solução

Verifique se há mods corrompidos.

---

> **Faça um backup completo dos seus arquivos de save antes de tentar qualquer uma destas etapas!**

---

# Como remover dados corrompidos

Ordenado por nível de dificuldade e complexidade.

## Fácil

### Desativar e ativar mods

* Às vezes, os mods não são inicializados corretamente, o que pode ser corrigido desativando e ativando novamente apenas um mod usando o menu de mods dentro do jogo.

### Reiniciar o Paralives

* O jogo possui proteções contra dados corrompidos que são ativadas quando o jogo é iniciado.
* Isso pode parecer bobo, mas reiniciar o jogo várias vezes pode ser eficaz em alguns casos.

### Iniciar um novo save

* Se os erros forem muito complicados ou não puderem ser corrigidos, iniciar um novo save pode ser a melhor opção.

### Verificar os arquivos do jogo ou reinstalar o jogo usando o Steam

* No cliente Steam, com o jogo fechado:

  * Steam > Paralives > Propriedades > Verificar integridade dos arquivos do jogo

### Assinar novamente todos os mods para limpar quaisquer arquivos corrompidos

1. Adicione todos os mods assinados a uma coleção personalizada.
2. Cancele a assinatura de todos os mods.
3. Assine novamente todos os mods da coleção.

### Remover mods até que o mod corrompido seja removido

* Remova um mod por vez ou use o método 50/50 para remover metade dos mods até que o mod corrompido seja identificado.
* Os mods ainda podem causar bugs mesmo quando desativados. Eles precisam ser completamente removidos movendo, cancelando a assinatura ou excluindo os arquivos do mod.
* O jogo pode precisar ser reiniciado entre cada teste para garantir que os arquivos armazenados em cache sejam eliminados.
* Documente suas descobertas e anote quais mods funcionam!

### Assinar novamente os mods lentamente para garantir que sejam instalados corretamente

* A teoria é que instalar muitos mods de uma vez causa erros, então instale os mods lentamente.
* O jogo foi projetado para instalar mods rapidamente, mas talvez haja algo nisso.

---

## Intermediário

### Mover os mods do Steam Workshop para a pasta de mods locais Paralives\Paralives

* Os mods instalados localmente são interpretados de maneira diferente pelo mecanismo do jogo, o que pode corrigir o erro.
* Enquanto o jogo não estiver em execução, abra o explorador de arquivos e volte para a pasta de Mods do Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Digite ".mod" na barra de pesquisa. Se nenhum resultado aparecer, tente "*.mod".
* Isso retornará as pastas que contêm mods dentro da pasta de Mods do Steam.
* Selecione, recorte e cole todas as pastas .mod na pasta de mods locais Paralives\Paralives.
* Todas as pastas devem ser movidas de uma vez.
* Em seguida, cancele a assinatura dos mods para impedir que o Steam os copie novamente.
* Certifique-se de que a cópia na pasta do Steam Workshop tenha sido realmente excluída, pois ter duas cópias do mesmo mod pode causar erros.

### Excluir quaisquer arquivos restantes nas pastas de mods do Steam Workshop

* Volte para workshop\content\1118520\ e remova quaisquer arquivos que não tenham sido devidamente eliminados.
* Preste atenção aos detalhes, pois pequenos erros serão difíceis de encontrar posteriormente.
* Arquivos remanescentes têm grande probabilidade de causar erros quando o jogo não os espera.

### Usar comandos do console para reparar um arquivo de save corrompido removendo dados corrompidos

* `CLEARALLOCCUPATIONS` excluirá todos os empregos e o histórico de empregos do para selecionado e não poderá ser desfeito.
* `CLEARCHARACTEROUTFITS` excluirá todas as roupas do para selecionado e não poderá ser desfeito.
* `CLEARINVENTORY` esvaziará o inventário do para selecionado e não poderá ser desfeito.
* O tutorial abaixo explica os comandos de cheat disponíveis.

Tutorial para comandos de cheat ⁠Console e Cheat Commands

### Instalar um plugin de injeção de código para gerenciar erros de mods

* Esses plugins funcionam dando ao mecanismo do jogo mais tempo para processar cada arquivo de mod e ajudando o mecanismo do jogo a diagnosticar erros.
* Plugins também podem causar corrupção adicional de dados se não forem mantidos e atualizados corretamente.
* Espera-se que os plugins se tornem desnecessários à medida que os desenvolvedores do Paralives adicionarem mais código de correção de erros ao jogo.

Plugin do Paralines Launcher ⁠Paraline Launcher [Help | Bug R…

---

## Avançado

### Limpar a pasta de mods locais

* Isso é necessário para obter um início realmente limpo.
* Pode ser necessário desativar o Steam Cloud para impedir que arquivos corrompidos sejam restaurados durante os testes.

1. Recorte e cole a pasta de mods locais em um local seguro fora dos arquivos do jogo, como a área de trabalho.
2. Verifique os arquivos do jogo usando o Steam.
3. Reinicie o jogo. Quando o jogo for iniciado, o Paralives regenerará toda a pasta de mods locais do zero.
4. Verifique se uma nova pasta de mods locais foi gerada.
5. Verifique se o problema foi resolvido.

   * Sim: Reintroduza os arquivos importantes da cópia criada na etapa 1.
   * Não: Tente outros métodos de correção antes de reintroduzir os arquivos antigos.
6. Adicione à nova pasta Paralives somente arquivos considerados seguros para reduzir as chances de copiar arquivos de dados corrompidos.

### Editar arquivos de save diretamente para remover dados corrompidos

* Os arquivos de save são arquivos de texto e podem ser modificados diretamente.
* Qualquer editor de texto pode ser usado, mas o Notepad++ com um plugin para formatação de arquivos JSON é preferível.
* O tutorial abaixo explica como os arquivos de save são formatados.

Explicação da pasta de mods locais ⁠Mod Folder/Save Folder

### Mover partes seguras de um save para um novo arquivo de save

* Quando o problema com o save não pode ser identificado, mova pequenas partes para um novo save.
* Este método pode ser útil ao tentar identificar arquivos corrompidos.
* Por exemplo, pastas de famílias podem ser arrastadas entre saves com uma perda de dados relativamente pequena.
* O tutorial abaixo explica como os arquivos de save são formatados.

Explicação da pasta de mods locais ⁠Mod Folder/Save Folder

### Usar comandos do console para reconstruir personagens em um novo save

* Quando tudo estiver perdido, talvez seja melhor começar novamente em um novo save, mas com uma pequena vantagem inicial.
* Comandos como `SETMONEY` podem ser usados para adicionar dinheiro.
* Os comandos podem ser usados para restaurar habilidades, receitas e muito mais.
* O tutorial abaixo explica os comandos de cheat disponíveis.

Tutorial para comandos de cheat ⁠Console e Cheat Commands

---

> **Faça um backup completo dos seus arquivos de save antes de tentar qualquer uma destas etapas!**

# "A correção usual"

O método de destruir e reconstruir usado para corrigir a maioria dos problemas, excluindo todos os arquivos associados ao jogo para proporcionar o início mais limpo possível. Não recomendo esta solução para todos os problemas, pois isso pode tornar saves antigos com mods impossíveis de jogar sem os mods dos quais dependem para funcionar corretamente.

## Limpar todos os arquivos do jogo para um início limpo

1. Limpe os arquivos do jogo recortando e colando toda a pasta de mods locais paralives/paralives na área de trabalho.
2. Cancele a assinatura de todos os mods do Steam Workshop e exclua quaisquer arquivos de mods restantes.
3. Verifique os arquivos do jogo usando o Steam ou reinstale o jogo.
4. Reinicie o Paralives.
5. Inicie um novo save.
6. Se o jogo funcionar agora, reverta lentamente as alterações até que o problema retorne e você saberá qual é a causa do problema.

---

# Prevenir a corrupção de dados

## Faça cópias de TUDO e COM FREQUÊNCIA

* Faça uma cópia física dos arquivos importantes em um local seguro, como a área de trabalho, fora dos arquivos do jogo.
* Arquivos acessíveis pelo mecanismo do jogo Paralives sempre podem ser corrompidos.

> Nota: O comando ZIPSAVEFILE fará uma cópia do save atual na área de trabalho. Ele pode substituir a cópia antiga se o comando for usado duas vezes.

Tutorial para comandos de cheat ⁠Console e Cheat Commands

`ZIPSAVEFILE` cria um arquivo zip do save atual na área de trabalho.

## Leia as avaliações dos mods

* E deixe avaliações também!
* Os comentários nos mods são a forma como o modder e outros usuários compartilham informações sobre os mods.
* Se o mod parecer estar com problemas, informe o modder para que ele possa corrigi-lo!

## Desative o Steam Cloud

* O Steam Cloud é excelente para proteger arquivos importantes, mas às vezes causa problemas difíceis de encontrar.
* O Steam Cloud gosta de trazer de volta arquivos expirados sem avisar ninguém e simplesmente colocá-los lá para você encontrá-los depois.

## Remova os mods corretamente

* Os mods adicionam referências de itens ao jogo.
* Cada instância desses itens precisa ser removida manualmente do save do jogo ANTES de remover o mod.
* É muito mais fácil remover itens de mods dentro do jogo do que modificando um arquivo de save.
* Remova aquele sofá sofisticado e aquele suéter divertido antes de remover o mod!

## Atualize os drivers

* Para este tutorial, o driver mais importante é o da placa de vídeo (GPU).
* No Windows, baixe o aplicativo da Nvidia ou AMD e instale o novo driver a cada poucos meses.

## Atualize o sistema operacional

* É, eu sei, chato, mas é importante!
* Execute regularmente softwares de atualização integrados, como o Windows Update.

## Instale os mods lentamente e verifique os mods instalados individualmente ou em pequenos grupos

* Isso pode ajudar o jogo a processar cada arquivo sem cometer erros.

## Manutenção preventiva do hardware

* Cuide do computador e ele cuidará de você.
* Instale e execute um software antimalware obtido de forma segura.
* Inspecione o computador em busca de danos físicos e limpe a poeira.
* Execute programas integrados para verificar a saúde e a estabilidade dos componentes.
