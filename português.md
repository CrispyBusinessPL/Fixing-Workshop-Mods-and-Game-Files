# Índice

* [Itens necessários](#itens-necessários)
* [Identificar dados corrompidos](#identificar-dados-corrompidos)
* [Como remover dados corrompidos](#como-remover-dados-corrompidos)
* ["A solução habitual"](#a-solução-habitual)
* [Prevenir corrupção de dados](#prevenir-corrupção-de-dados)
* [Mais recursos](#mais-recursos)

> **Faça um backup completo dos seus arquivos de salvamento antes de tentar qualquer uma destas etapas!**

---

# Itens necessários

## Pasta de Mods do Steam Workshop (Mods do Workshop)

* Pode ser acessada clicando no ícone de pasta em um mod do Steam Workshop no Menu de Mods do Paralives.
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

* Pode ser acessada clicando no ícone de pasta em um mod local no Menu de Mods do Paralives.
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

* Pode ser lido com qualquer software de leitura de arquivos de texto, como Notepad ou Notepad++.
* Localizado na pasta Paralives\Paralives.
* Fornece registros da sessão atual ou da última sessão jogada do Paralives.

## Pasta Paralives\MySavedGames.mod

* Pasta que contém todos os jogos salvos atuais e salvamentos automáticos.
* Localizada na pasta Paralives\Paralives.
* Esta pasta é mais importante do que qualquer outra.
* Faça regularmente uma cópia completa desta pasta em um local seguro fora dos arquivos do jogo!

## Pasta Paralives\MyPremadeHouseholds.mod

* Famílias salvas na biblioteca.

## Pasta Paralives\MyPremadeLot.mod

* Lotes salvos na biblioteca.

## Pasta Paralives\MyPremadeOutfits.mod

* Roupas salvas na biblioteca.

## Pasta Paralives\Local.mod e 0.mod

* Armazena configurações do jogo, como amostras de cores personalizadas.

---

# Identificar dados corrompidos

Dados corrompidos são compostos por arquivos que foram alterados e já não estão no formato ou na sequência que o jogo espera encontrar.

## Arquivos desatualizados

* O jogo foi atualizado e esses arquivos já não estão em conformidade com a sintaxe atual.
* Embora isso possa acontecer ocasionalmente com mods, quase todos os plugins de injeção de código do bepinex ficam desatualizados após uma atualização do jogo.
* Se um plugin bepinex estiver instalado, mas os mods ainda não estiverem funcionando, o plugin pode estar causando mais problemas do que resolvendo.

## Arquivos modificados incorretamente

* Estes foram modificados por um jogador, modder ou até mesmo pelo mecanismo do jogo e agora estão incorretos.
* Isso acontece quando mods ou plugins são usados e depois removidos.

Por exemplo, um mod usado para adicionar uma roupa personalizada é removido, mas a roupa continua identificada nos arquivos do jogo.

Pode ser impossível remover alguns mods sem corromper um arquivo de salvamento.

## Arquivos movidos incorretamente

* Os arquivos são frequentemente movidos pelo jogador, pelo mecanismo do jogo ou pelo Steam, e algumas partes do arquivo acabam sendo deixadas para trás ou excluídas.

## Como o jogo vai me informar quais arquivos estão corrompidos?

O mecanismo do jogo tentará informar o usuário quando houver um erro por meio de notificações diretas e indiretas.

### Diretas:

* Janelas pop-up na tela
* Notificações no console
* Eventos no player.log

### Indiretas:

* Piscadas
* Flashes
* Travamentos momentâneos
* Lag
* Crashes
* Cancelamento de operações

## Lendo o Error Console e o Player.Log

Os registros do error console e do player.log se sobrepõem apenas parcialmente, portanto é importante verificar ambos ao tentar identificar um erro.

É importante identificar o erro inicial e ignorar os erros adicionais causados pelo primeiro erro. Ao ler o registro de erros, tente corrigir os erros de cima para baixo, em ordem sequencial.

Se vários erros forem introduzidos ao mesmo tempo, pode ser muito difícil diagnosticar o problema. É importante fazer apenas um pequeno número de alterações entre os testes.

Se o jogo estiver funcionando normalmente, anote os erros no registro para que possam ser descartados posteriormente quando algo apresentar problemas.

### ERROR CONSOLE

* O error console é acessado no jogo como uma aba no menu de cheats.
* Ele não pode ser usado se o jogo não carregar.

1. Pressione Ctrl+Shift+C para abrir o menu de cheats.
2. Pressione a seta para mudar para a aba do console.
3. O console é organizado em três categorias de importância.
4. Apenas os erros vermelhos são importantes para este tutorial.

### PLAYER.LOG & PLAYER-PREV.LOG

* Este arquivo registra as ações realizadas pelo mecanismo de jogo Unity que executa o Paralives.
* Player.log é sobrescrito sempre que o jogo é iniciado e movido para Player-prev.log.
* Ele está localizado na pasta de mods locais Paralives\Paralives.
* Mais informações podem ser adicionadas ao registro ativando opções no painel de controle. Muitas opções podem rapidamente fazer o registro ficar muito grande.
* Se algo no registro for importante, faça uma cópia!

### Bons erros (pelo menos não ruins):

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

> Observação: Na versão 1.7, há três novos erros vermelhos no console e no player.log que não parecem afetar negativamente o desempenho do jogo.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Observação: Na versão 1.8A, o .fbx importer não funcionava corretamente e ficava preso na tela de importação de assets.

---

# Tipos de erros

Os tipos de problemas que estão ocorrendo em nível técnico.

## Null Reference

* Às vezes chamado de referência de ponteiro nulo.
* Qualquer erro indicando que uma configuração, item, mesh ou valor não pôde ser encontrado.
* O jogo faz referência a um objeto que não consegue encontrar ou não conseguiu entender o que encontrou.

> Observação: O jogo consegue lidar com algumas referências nulas e várias delas fazem parte da versão de acesso antecipado do jogo.

## Out of Bounds

* O jogo recebeu um valor fora do intervalo esperado.
* Se o jogo espera um valor entre 0 e 10, mas recebe 10842, isso pode causar um erro.

## Translation

* O jogo tentou corrigir um arquivo determinado como corrompido e o resultado estava incorreto.

Por exemplo, um problema com arquivos .tmp ⁠.mod.meta e .tmp

## Syntax

* O jogo foi atualizado e o mod já não está em conformidade com os padrões definidos pelo jogo. Mais comum com plugins de injeção de código Bepinex.
* Alguns mods criados quando o jogo foi lançado estão sem dois-pontos no arquivo de texto.

---

# Categorias de sintomas

Quando a causa do erro é desconhecida, o objetivo é correlacionar os sintomas a uma causa específica. Depois que cada erro for corrigido, o jogo funcionará. Estas são categorias arbitrárias para ajudar a agrupar erros semelhantes em conjuntos.

É importante identificar o erro inicial e ignorar os erros adicionais causados pelo primeiro erro.

## Cat A — Iniciar o jogo

### Sintomas

* O jogo não consegue chegar ao menu principal do Paralives
* A tela fica preta
* O jogo trava ao iniciar o jogo pelo Steam
* Um erro aparece ao iniciar o jogo pelo Steam
* O jogo fica preso em uma imagem de nuvens.

### Possíveis soluções

* Verifique se o hardware atende aos requisitos mínimos para jogar Paralives.
* Um arquivo crítico usado durante a inicialização do jogo está corrompido, ilegível ou inacessível.
* Comece verificando os arquivos do jogo.
* Crie uma exceção para o Paralives no antivírus.
* Verifique o player.log em busca de erros na pasta de mods locais paralives/paralives.

## Cat B — Importando assets

### Sintomas

* Preso na importação de assets

### Possível causa

Um arquivo de mod está ilegível.

### Possíveis soluções

* Remova os mods mais recentes da pasta de mods locais paralives/paralives ou das pastas do Steam Workshop até que o problema seja resolvido.
* Verifique os arquivos do jogo.

## Cat C — Selecionar um salvamento

### Sintomas

* O jogo retorna ao menu principal ao tentar carregar um salvamento
* O arquivo de salvamento está branco

### Possível causa

O arquivo de salvamento possui nomes de arquivos incorretos, está sem arquivos ou está ilegível.

### Possível solução

Comece verificando se o nome do salvamento corresponde aos arquivos meta dentro dele e se o salvamento contém todos os componentes necessários.

## Cat D — Carregar um salvamento

### Sintomas

* O jogo trava durante o carregamento do salvamento
* O jogo permanece na tela de carregamento para sempre

### Possível causa

Mod corrompido, um mod foi removido incorretamente ou corrupção do arquivo de salvamento, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de salvamento.

### Possível solução

Teste se os erros persistem em um novo jogo salvo.

## Cat E — Modo Live

### Sintomas

* O jogo trava ou congela ao abrir um menu no modo Live
* O jogo trava ou congela ao realizar uma ação específica no modo Live

### Possível causa

Mod corrompido, um mod foi removido incorretamente ou corrupção do arquivo de salvamento, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de salvamento.

### Possível solução

Teste se os erros persistem em um novo jogo salvo.

## Cat F — Menus

### Sintomas

* O menu do jogo não abre quando clicado
* O menu do jogo fica em branco quando clicado
* O menu do jogo não fecha

### Possível causa

Mod corrompido, um mod foi removido incorretamente ou corrupção do arquivo de salvamento, como um erro de referência nula.

Pode ser impossível remover alguns mods sem corromper um arquivo de salvamento.

### Possível solução

Teste se os erros persistem em um novo jogo salvo.

## Cat G — Instalando mods

### Sintomas

* Os mods não são instalados

### Possíveis soluções

* Verifique as pastas de mods do Steam e locais em busca de arquivos parciais.
* Exclua arquivos de mods corrompidos que estejam impedindo o download.

## Cat H — Mods ausentes

### Sintomas

* Os mods instalados não aparecem no menu de mods
* Os mods instalados aparecem no menu de mods, mas não aparecem no jogo

### Possíveis soluções

* Verifique se há mods corrompidos.
* Verifique se há arquivos de mods duplicados.

## Cat I — Validando mods

### Sintomas

* Os itens de mods instalados não aparecem quando equipados no personagem
* Os itens de mods instalados desapareceram
* O personagem com itens de mods desapareceu
* Os itens de mods parecem estranhos
* Os itens de mods interagem de maneira inesperada
* Os itens de mods têm a cor, forma ou tamanho incorretos

### Possível solução

Verifique se há mods corrompidos.

---

> **Faça um backup completo dos seus arquivos de salvamento antes de tentar qualquer uma destas etapas!**

---

# Como remover dados corrompidos

Organizado por nível de dificuldade e complexidade.

## Fácil

### Desative e ative os mods

* Às vezes os mods não são inicializados corretamente, o que pode ser corrigido desativando e ativando novamente apenas um mod usando o menu de mods dentro do jogo.

### Reinicie o Paralives

* O jogo possui proteções contra dados corrompidos que são ativadas quando o jogo é iniciado.
* Pode parecer bobo, mas reiniciar o jogo várias vezes pode ser eficaz em alguns cenários.

### Inicie um novo jogo salvo

* Se os erros forem muito complicados ou não puderem ser corrigidos, iniciar um novo salvamento pode ser a melhor opção.

### Verifique os arquivos do jogo ou reinstale o jogo usando o Steam

* No cliente Steam, com o jogo encerrado:

  * Steam > Paralives > Properties > Verify integrity of games files

### Cancele a inscrição de todos os mods para limpar arquivos corrompidos

1. Adicione todos os mods inscritos a uma coleção personalizada
2. Cancele a inscrição de todos os mods
3. Inscreva-se em todos os mods da coleção

### Remova mods até que o mod corrompido seja removido

* Remova um mod por vez ou use o método 50/50 para remover metade dos mods até que o mod corrompido seja identificado.
* Os mods ainda podem causar bugs mesmo quando desativados. Eles precisam ser completamente removidos movendo, cancelando a inscrição ou excluindo os arquivos do mod.
* O jogo pode precisar ser reiniciado entre cada teste para garantir que os arquivos em cache sejam eliminados.
* Documente suas descobertas e anote quais mods funcionam!

### Inscreva-se novamente nos mods lentamente para garantir que sejam instalados corretamente

* A teoria é que instalar muitos mods de uma vez causa erros, então instale os mods lentamente.
* O jogo foi projetado para instalar mods rapidamente, mas talvez haja algo nisso.

---

## Intermediário

### Mova os mods do Steam Workshop para a pasta de mods locais Paralives\Paralives

* Mods instalados localmente são interpretados de maneira diferente pelo mecanismo do jogo, o que pode corrigir o erro.
* Com o jogo fechado, abra o explorador de arquivos e retorne à pasta de Mods do Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Digite ".mod" na barra de pesquisa. Se não houver resultados, tente "*.mod".
* Isso retornará as pastas que contêm mods dentro da pasta de Mods do Steam.
* Selecione, recorte e cole todas as pastas .mod na pasta de mods locais Paralives\Paralives.
* Todas as pastas devem ser movidas de uma vez.
* Depois, cancele a inscrição nos mods para impedir que o Steam os copie de volta.
* Certifique-se de que a cópia na pasta de mods do Steam Workshop seja devidamente excluída, pois ter duas cópias do mesmo mod pode causar erros.

### Exclua quaisquer arquivos restantes nas pastas de mods do Steam Workshop

* Retorne a workshop\content\1118520\ e remova quaisquer arquivos que não tenham sido devidamente descartados.
* Preste atenção aos detalhes, pois pequenos erros serão difíceis de encontrar posteriormente.
* Arquivos remanescentes têm grande probabilidade de causar erros quando o jogo não espera encontrá-los.

### Use comandos do console para reparar um arquivo de salvamento corrompido removendo dados corrompidos

* `CLEARALLOCCUPATIONS` excluirá todos os empregos e o histórico de empregos do para selecionado e não poderá ser desfeito.
* `CLEARCHARACTEROUTFITS` excluirá todas as roupas do para selecionado e não poderá ser desfeito.
* `CLEARINVENTORY` esvazia o inventário do para selecionado e não poderá ser desfeito.
* O tutorial abaixo explica os comandos de cheat disponíveis.

Tutorial for cheat commands ⁠Console and Cheat Commands

### Instale um plugin de injeção de código para gerenciar erros de mods

* Esses plugins funcionam dando ao mecanismo do jogo mais tempo para processar cada arquivo de mod e ajudando o mecanismo do jogo a diagnosticar erros.
* Plugins também podem causar corrupção adicional de dados se não forem mantidos e atualizados corretamente.
* Espera-se que os plugins se tornem desnecessários à medida que os desenvolvedores do Paralives adicionarem mais código de correção de erros ao jogo.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Avançado

### Limpe a pasta de mods locais

* Isso é necessário para obter um novo início adequado.
* O Steam Cloud pode precisar ser desativado para impedir que arquivos corrompidos sejam restaurados durante os testes.

1. Recorte e cole a pasta de mods locais em um local seguro fora dos arquivos do jogo, como a área de trabalho
2. Verifique os arquivos do jogo usando o Steam
3. Reinicie o jogo. Quando o jogo for iniciado, o Paralives regenerará toda a pasta de mods locais do zero.
4. Verifique se uma nova pasta de mods locais foi gerada.
5. Verifique se o problema foi resolvido.

   * Sim: Reintroduza os arquivos importantes da cópia feita na etapa 1.
   * Não: Tente outros métodos de correção do problema antes de reintroduzir arquivos antigos.
6. Adicione apenas arquivos à pasta Paralives recém-gerada que sejam considerados seguros para reduzir as chances de copiar arquivos de dados corrompidos.

### Edite os arquivos de salvamento diretamente para remover dados corrompidos

* Os arquivos de salvamento são arquivos de texto e podem ser modificados diretamente.
* Qualquer editor de texto pode ser usado, mas é preferível usar o Notepad++ com um plugin para formatar arquivos json.
* O tutorial abaixo explica como os arquivos de salvamento são formatados.

Explanation of the local mods folder ⁠Mod Folder/Save Folder

### Mova partes seguras de um salvamento para um novo arquivo de salvamento

* Quando o problema com o salvamento não puder ser identificado, mova pequenas partes para um novo salvamento.
* Este método pode ser útil ao tentar identificar arquivos corrompidos.
* Por exemplo, pastas de famílias podem ser arrastadas entre salvamentos com perda de dados relativamente pequena.
* O tutorial abaixo explica como os arquivos de salvamento são formatados.

Explanation of the local mods folder ⁠Mod Folder/Save Folder

### Use comandos do console para reconstruir personagens em um novo salvamento

* Quando tudo estiver perdido, talvez seja melhor começar novamente em um novo salvamento, mas com um pouco de vantagem inicial.
* Comandos como `SETMONEY` podem ser usados para adicionar dinheiro.
* Comandos podem ser usados para restaurar habilidades, receitas e muito mais.
* O tutorial abaixo explica os comandos de cheat disponíveis.

Tutorial for cheat commands ⁠Console and Cheat Commands

---

> **Faça um backup completo dos seus arquivos de salvamento antes de tentar qualquer uma destas etapas!**

# "A solução habitual"

O método de terra arrasada para corrigir a maioria dos problemas, excluindo todos os arquivos associados ao jogo para proporcionar o melhor início possível. Não recomendo esta solução para todos os problemas, pois isso pode tornar salvamentos antigos com mods impossíveis de jogar sem os mods dos quais dependem para funcionar corretamente.

## Limpe todos os arquivos do jogo para um novo início

1. Limpe os arquivos do jogo recortando e colando toda a pasta de mods locais paralives/paralives na área de trabalho.
2. Cancele a inscrição em todos os mods do Steam Workshop e exclua quaisquer arquivos de mods remanescentes.
3. Verifique os arquivos do jogo usando o Steam ou reinstale o jogo.
4. Reinicie o Paralives.
5. Inicie um novo jogo salvo.
6. Se o jogo funcionar agora, reverta lentamente as alterações até que o problema retorne e você saberá a causa do problema.

---

# Prevenir corrupção de dados

## Faça cópias de TUDO e COM FREQUÊNCIA

* Faça uma cópia física dos arquivos importantes em um local seguro, como a área de trabalho, fora dos arquivos do jogo.
* Arquivos acessíveis pelo mecanismo do jogo Paralives sempre podem ser corrompidos.

> Observação: O comando ZIPSAVEFILE fará uma cópia do seu salvamento atual na área de trabalho. Ele pode sobrescrever a cópia antiga se o comando for usado duas vezes.

Tutorial for cheat commands ⁠Console and Cheat Commands

`ZIPSAVEFILE` cria um zip do arquivo de salvamento atual na área de trabalho

## Leia as avaliações dos mods

* E deixe avaliações também!
* Os comentários nos mods são como o modder e outros usuários compartilham informações sobre os mods.
* Se o mod parecer estar quebrado, avise o modder para que ele possa corrigi-lo!

## Desative o Steam Cloud

* O Steam Cloud é excelente para proteger arquivos importantes, mas às vezes causa problemas difíceis de encontrar.
* O Steam Cloud gosta de trazer de volta arquivos expirados sem avisar ninguém e simplesmente colocá-los lá para que você os encontre mais tarde.

## Remova os mods corretamente

* Mods adicionam referências de itens ao jogo.
* Cada instância desses itens precisa ser removida manualmente do salvamento do jogo ANTES de remover o mod.
* É muito mais fácil remover itens de mods dentro do jogo do que modificando um arquivo de salvamento.
* Exclua aquele sofá sofisticado e aquele suéter divertido antes de remover o mod!

## Atualize os drivers

* Para este tutorial, o driver no qual você deve se concentrar é o da placa gráfica (GPU).
* No Windows, baixe o aplicativo da Nvidia ou AMD e instale o novo driver a cada poucos meses.

## Atualize o sistema operacional

* Sim, é chato, mas é importante!
* Execute regularmente softwares de atualização integrados, como o Windows Update.

## Instale mods lentamente e verifique os mods instalados individualmente ou em pequenos grupos

* Isso pode ajudar o jogo a processar cada arquivo sem cometer erros.

## Manutenção preventiva do hardware

* Cuide do computador e ele cuidará de você.
* Instale e execute softwares antimalware obtidos de fontes seguras.
* Inspecione o computador em busca de danos físicos e limpe a poeira.
* Execute programas integrados para verificar a integridade e estabilidade dos componentes.

---

# Mais recursos

## Tópicos discutindo problemas com mods (onde obtenho minhas cobaias)

* Recomendações de correções dos desenvolvedores
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Mega tópico de mods ausentes
  https://discord.com/channels/595045400805769238/1517352862395404499
* Mods não carregando
  https://discord.com/channels/595045400805769238/1517449529174130779
* Erros de referência nula
  https://discord.com/channels/595045400805769238/1517532031662424154
* Erros de referência nula
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* Arquivos de mods corrompidos
  https://discord.com/channels/595045400805769238/1517266950944981062
* Wiki do Paralives
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Registro de alterações do Paralives
  https://www.paralives.com/news
* Desenvolvimento do Paralives
  https://www.paralives.com/development
* Roadmap do Paralives
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Bugs conhecidos
  https://discord.com/channels/595045400805769238/1508927230154244216
* Roadmap do Paralives
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Bugs conhecidos

The contents of this repository, source code, documentation, and associated files, may not be used for AI model training, dataset creation, or other machine-learning purposes. known-issues-and-bugs
  known-issues-and-bugs
