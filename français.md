# Index

* [Éléments requis](#éléments-requis)
* [Identifier les données corrompues](#identifier-les-données-corrompues)
* [Comment supprimer les données corrompues](#comment-supprimer-les-données-corrompues)
* [« La solution habituelle »](#la-solution-habituelle)
* [Prévenir la corruption des données](#prévenir-la-corruption-des-données)
* [Ressources supplémentaires](#ressources-supplémentaires)

> **Faites une sauvegarde complète de vos fichiers de sauvegarde avant de tenter l'une de ces étapes !**

---

# Éléments requis

## Dossier des mods Steam Workshop (Mods Workshop)

* Peut être ouvert en cliquant sur l'icône de dossier d'un mod Steam Workshop dans le menu des mods de Paralives.
* En naviguant vers :

**Windows :**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac :**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Dossier Paralives (Mods locaux)

* Peut être ouvert en cliquant sur l'icône de dossier d'un mod local dans le menu des mods de Paralives.
* En naviguant vers :

**Windows :**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac :**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Peut être lu avec n'importe quel logiciel de lecture de fichiers texte tel que Notepad ou Notepad++.
* Situé dans le dossier Paralives\Paralives.
* Fournit les journaux de la session actuelle ou de la dernière session jouée de Paralives.

## Dossier Paralives\MySavedGames.mod

* Dossier contenant toutes les sauvegardes actuelles et les sauvegardes automatiques.
* Situé dans le dossier Paralives\Paralives.
* Ce dossier est plus important que tout autre.
* Veuillez régulièrement faire une copie complète de ce dossier dans un emplacement sûr en dehors des fichiers du jeu !

## Dossier Paralives\MyPremadeHouseholds.mod

* Foyers enregistrés dans la bibliothèque.

## Dossier Paralives\MyPremadeLot.mod

* Terrains enregistrés dans la bibliothèque.

## Dossier Paralives\MyPremadeOutfits.mod

* Tenues enregistrées dans la bibliothèque.

## Dossiers Paralives\Local.mod et 0.mod

* Stockent les paramètres du jeu tels que les palettes personnalisées.

---

# Identifier les données corrompues

Les données corrompues sont constituées de fichiers qui ont été modifiés de manière à ne plus correspondre à la forme ou à la séquence que le jeu s'attend à trouver.

## Fichiers obsolètes

* Le jeu a été mis à jour et ces fichiers ne sont plus conformes à la syntaxe actuelle.
* Bien que cela puisse arriver occasionnellement avec les mods, presque tous les plugins d'injection de code BepInEx deviennent obsolètes après une mise à jour du jeu.
* Si un plugin BepInEx est installé mais que les mods ne fonctionnent toujours pas, le plugin peut faire plus de mal que de bien.

## Fichiers modifiés incorrectement

* Ceux-ci ont été modifiés par un joueur, un moddeur ou même le moteur du jeu et sont désormais incorrects.
* Il peut s'agir de mods ou de plugins qui ont été utilisés puis supprimés.

Par exemple, un mod utilisé pour ajouter une tenue personnalisée est supprimé, mais la tenue est toujours identifiée dans les fichiers du jeu.

Il peut être impossible de supprimer certains mods sans endommager un fichier de sauvegarde.

## Fichiers déplacés incorrectement

* Les fichiers sont souvent déplacés par le joueur, le moteur du jeu ou Steam, et certaines parties du fichier sont laissées derrière ou supprimées.

## Comment le jeu va-t-il m'indiquer quels fichiers sont corrompus ?

Le moteur du jeu tentera d'informer l'utilisateur lorsqu'une erreur survient par le biais de notifications directes et indirectes.

### Direct :

* Fenêtres contextuelles à l'écran
* Notifications dans la console
* Événements dans le player.log

### Indirect :

* Scintillement
* Clignotement
* Saccades
* Lag
* Crash
* Annulation d'opérations

## Lire la console d'erreurs et le Player.Log

Les rapports de la console d'erreurs et du player.log ne se chevauchent que partiellement ; il est donc important de vérifier les deux lors de la recherche d'une erreur.

Il est important d'identifier l'erreur initiale et d'ignorer les erreurs supplémentaires causées par la première erreur. Lors de la lecture du journal d'erreurs, essayez de corriger les erreurs de haut en bas, dans l'ordre.

Si plusieurs erreurs sont introduites en même temps, le diagnostic peut être très difficile. Il est important de ne faire qu'un petit nombre de changements entre les tests.

Si le jeu fonctionne correctement, notez les erreurs présentes dans le journal afin de pouvoir les écarter plus tard lorsqu'un problème survient.

### CONSOLE D'ERREURS

* La console d'erreurs est accessible dans le jeu sous forme d'onglet dans le menu des triches.
* Elle ne peut pas être utilisée si le jeu ne se charge pas.

1. Appuyez sur Ctrl+Shift+C pour ouvrir le menu des triches.
2. Appuyez sur le chevron pour passer à l'onglet de la console.
3. La console est classée en trois catégories d'importance.
4. Seules les erreurs rouges sont importantes dans le cadre de ce tutoriel.

### PLAYER.LOG & PLAYER-PREV.LOG

* Ce fichier enregistre les actions effectuées par le moteur de jeu Unity exécutant Paralives.
* Player.log est remplacé à chaque démarrage du jeu et déplacé vers Player-prev.log.
* Il se trouve dans le dossier de mods locaux Paralives\Paralives.
* Davantage d'informations peuvent être ajoutées au journal en activant des options dans le panneau de configuration. Trop d'options peuvent rapidement rendre le journal très volumineux.
* Si quelque chose dans le journal est important, faites-en une copie !

### Bonnes erreurs (du moins pas mauvaises) :

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Mauvaises erreurs :

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Remarque : Dans la version 1.7, trois nouvelles erreurs rouges apparaissent dans la console et le player.log et ne semblent pas affecter négativement les performances du jeu.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Remarque : Dans la version 1.8A, l'importateur .fbx ne fonctionnait pas correctement et restait bloqué sur l'écran d'importation des ressources.

---

# Types d'erreurs

Les types de problèmes qui se produisent au niveau technique.

## Référence nulle

* Parfois appelée référence de pointeur nul.
* Toute erreur indiquant qu'un paramètre, élément, maillage ou valeur n'a pas pu être trouvé.
* Le jeu fait référence à un objet qu'il ne peut pas trouver ou n'a pas compris ce qu'il a trouvé.

> Remarque : Le jeu est capable de gérer certaines références nulles et plusieurs d'entre elles font partie de la version en accès anticipé du jeu.

## Hors limites

* Une valeur en dehors de la plage attendue a été fournie au jeu.
* Si le jeu attend une valeur comprise entre 0 et 10 mais reçoit 10842, cela peut provoquer une erreur.

## Traduction

* Le jeu a tenté de corriger un fichier considéré comme endommagé et le résultat était incorrect.

Par exemple, un problème avec les fichiers .tmp, ⁠.mod.meta et .tmp.

## Syntaxe

* Le jeu a été mis à jour et le mod n'est plus conforme aux normes définies par le jeu. Cela est particulièrement fréquent avec les plugins d'injection de code BepInEx.
* Certains mods créés lors du lancement du jeu ont des deux-points manquants dans le fichier texte.

---

# Catégories de symptômes

Lorsque la cause de l'erreur est inconnue, l'objectif est de corréler les symptômes à une cause spécifique. Une fois chaque erreur corrigée, le jeu devrait fonctionner. Voici des catégories arbitraires permettant de regrouper des erreurs similaires en groupes.

Il est important d'identifier l'erreur initiale et d'ignorer les erreurs supplémentaires causées par la première erreur.

## Cat A — Lancer le jeu

### Symptômes

* Le jeu n'arrive pas à atteindre le menu principal de Paralives
* L'écran est noir
* Le jeu plante lors du lancement depuis Steam
* Une erreur apparaît lors du lancement du jeu depuis Steam
* Le jeu reste bloqué sur une image de nuages.

### Solutions possibles

* Vérifiez que le matériel répond aux exigences minimales pour jouer à Paralives.
* Un fichier critique utilisé lors du lancement du jeu est corrompu, illisible ou inaccessible.
* Commencez par vérifier l'intégrité des fichiers du jeu.
* Ajoutez une exception pour Paralives dans l'antivirus.
* Vérifiez le player.log pour rechercher des erreurs dans le dossier de mods locaux paralives/paralives.

## Cat B — Importation des ressources

### Symptômes

* Bloqué sur l'importation des ressources

### Cause possible

Un fichier de mod est illisible.

### Solutions possibles

* Supprimez les mods les plus récents du dossier de mods locaux paralives/paralives ou des dossiers Steam Workshop jusqu'à ce que le problème soit résolu.
* Vérifiez l'intégrité des fichiers du jeu.

## Cat C — Sélectionner une sauvegarde

### Symptômes

* Le jeu revient au menu principal lorsqu'une sauvegarde est chargée
* Le fichier de sauvegarde est blanc

### Cause possible

Le fichier de sauvegarde contient des noms de fichiers incorrects, des fichiers manquants ou est illisible.

### Solution possible

Commencez par vérifier que le nom de la sauvegarde correspond aux fichiers meta qu'elle contient et que la sauvegarde contient tous les composants requis.

## Cat D — Charger une sauvegarde

### Symptômes

* Le jeu reste bloqué pendant le chargement de la sauvegarde
* Le jeu reste indéfiniment sur l'écran de chargement

### Cause possible

Mod corrompu, mod supprimé incorrectement ou corruption du fichier de sauvegarde telle qu'une erreur de référence nulle.

Il peut être impossible de supprimer certains mods sans endommager un fichier de sauvegarde.

### Solution possible

Vérifiez si les erreurs persistent dans une nouvelle sauvegarde.

## Cat E — Mode Vie

### Symptômes

* Le jeu reste bloqué ou se fige lors de l'ouverture d'un menu en mode Vie
* Le jeu reste bloqué ou se fige lors de l'exécution d'une action spécifique en mode Vie

### Cause possible

Mod corrompu, mod supprimé incorrectement ou corruption du fichier de sauvegarde telle qu'une erreur de référence nulle.

Il peut être impossible de supprimer certains mods sans endommager un fichier de sauvegarde.

### Solution possible

Vérifiez si les erreurs persistent dans une nouvelle sauvegarde.

## Cat F — Menus

### Symptômes

* Le menu du jeu ne s'ouvre pas lorsqu'on clique dessus
* Le menu du jeu est vide lorsqu'on clique dessus
* Le menu du jeu ne se ferme pas

### Cause possible

Mod corrompu, mod supprimé incorrectement ou corruption du fichier de sauvegarde telle qu'une erreur de référence nulle.

Il peut être impossible de supprimer certains mods sans endommager un fichier de sauvegarde.

### Solution possible

Vérifiez si les erreurs persistent dans une nouvelle sauvegarde.

## Cat G — Installation des mods

### Symptômes

* Les mods ne s'installent pas

### Solutions possibles

* Vérifiez les dossiers de mods Steam et locaux pour rechercher des fichiers partiels.
* Supprimez les fichiers de mod corrompus empêchant le téléchargement.

## Cat H — Mods manquants

### Symptômes

* Les mods installés n'apparaissent pas dans le menu des mods
* Les mods installés apparaissent dans le menu des mods mais pas dans le jeu

### Solutions possibles

* Vérifiez la présence de mods corrompus.
* Vérifiez la présence de fichiers de mods en double.

## Cat I — Vérification des mods

### Symptômes

* Les éléments des mods installés n'apparaissent pas lorsqu'ils sont équipés sur un personnage
* Les éléments des mods installés ont disparu
* Le personnage utilisant des éléments de mod a disparu
* Les éléments des mods ont un aspect étrange
* Les éléments des mods interagissent de manière inattendue
* Les éléments des mods ont la mauvaise couleur, forme ou taille

### Solution possible

Vérifiez la présence de mods corrompus.

---

> **Faites une sauvegarde complète de vos fichiers de sauvegarde avant de tenter l'une de ces étapes !**

---

# Comment supprimer les données corrompues

Classé par niveau de difficulté et de complexité.

## Facile

### Désactiver et réactiver les mods

* Parfois, les mods ne s'initialisent pas correctement, ce qui peut être corrigé en désactivant puis en réactivant un seul mod à l'aide du menu des mods en jeu.

### Redémarrer Paralives

* Le jeu dispose de protections contre les données corrompues qui s'activent lorsque le jeu est démarré.
* Cela peut sembler ridicule, mais redémarrer le jeu plusieurs fois peut être efficace dans certains cas.

### Commencer une nouvelle sauvegarde

* Si les erreurs sont trop complexes ou ne peuvent pas être corrigées, commencer une nouvelle sauvegarde peut être la meilleure option.

### Vérifier les fichiers du jeu ou réinstaller le jeu avec Steam

* Dans le client Steam, avec le jeu fermé :

  * Steam > Paralives > Propriétés > Vérifier l'intégrité des fichiers du jeu

### Se réabonner à tous les mods pour supprimer les fichiers corrompus

1. Ajoutez tous les mods auxquels vous êtes abonné à une collection personnalisée
2. Désabonnez-vous de tous les mods
3. Abonnez-vous à tous les mods de la collection

### Supprimer les mods jusqu'à ce que le mod corrompu soit supprimé

* Supprimez un mod à la fois ou utilisez la méthode 50/50 pour supprimer la moitié des mods jusqu'à identifier le mod corrompu.
* Les mods peuvent toujours provoquer des bugs même lorsqu'ils sont désactivés. Ils doivent être complètement supprimés en déplaçant, en se désabonnant ou en supprimant les fichiers du mod.
* Le jeu peut devoir être redémarré entre chaque test afin de s'assurer que les fichiers mis en cache sont purgés.
* Documentez vos résultats et notez quels mods fonctionnent !

### Se réabonner lentement aux mods pour s'assurer qu'ils s'installent correctement

* La théorie est que l'installation de trop nombreux mods à la fois provoque des erreurs ; installez donc les mods progressivement.
* Le jeu est conçu pour installer rapidement les mods, mais il y a peut-être quelque chose à cela.

---

## Intermédiaire

### Déplacer les mods Steam Workshop vers le dossier de mods locaux Paralives\Paralives

* Les mods installés localement sont interprétés différemment par le moteur du jeu, ce qui peut corriger l'erreur.

* Pendant que le jeu n'est pas en cours d'exécution, ouvrez l'explorateur de fichiers et retournez dans le dossier des mods Steam Workshop :

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```

* Tapez ".mod" dans la barre de recherche. Si aucun résultat n'est trouvé, essayez "*.mod".

* Cela affichera les dossiers contenant les mods dans le dossier Steam Mods.

* Sélectionnez, coupez et collez tous les dossiers .mod dans le dossier de mods locaux Paralives\Paralives.

* Tous les dossiers doivent être déplacés en même temps.

* Désabonnez-vous ensuite des mods afin d'empêcher Steam de les recopier.

* Assurez-vous que la copie présente dans le dossier des mods Steam Workshop a bien été supprimée, car avoir deux copies d'un même mod peut provoquer des erreurs.

### Supprimer les fichiers restants dans les dossiers de mods Steam Workshop

* Retournez dans workshop\content\1118520\ et supprimez tous les fichiers qui n'ont pas été correctement supprimés.
* Faites particulièrement attention aux détails, car les petites erreurs seront difficiles à trouver plus tard.
* Les fichiers persistants sont très susceptibles de provoquer des erreurs lorsque le jeu ne s'attend pas à les trouver.

### Utiliser les commandes de console pour réparer un fichier de sauvegarde corrompu en supprimant les données corrompues

* `CLEARALLOCCUPATIONS` supprimera tous les emplois et l'historique des emplois du para sélectionné et cette action ne peut pas être annulée.
* `CLEARCHARACTEROUTFITS` supprimera toutes les tenues du para sélectionné et cette action ne peut pas être annulée.
* `CLEARINVENTORY` vide l'inventaire du para sélectionné et cette action ne peut pas être annulée.
* Le tutoriel lié ci-dessous explique les commandes de triche disponibles.

Tutoriel sur les commandes de triche ⁠Console and Cheat Commands

### Installer un plugin d'injection de code pour gérer les erreurs des mods

* Ces plugins fonctionnent en donnant au moteur du jeu davantage de temps pour traiter chaque fichier de mod et en aidant le moteur du jeu à diagnostiquer les erreurs.
* Les plugins peuvent également provoquer une corruption supplémentaire des données s'ils ne sont pas maintenus et mis à jour correctement.
* Les plugins deviendront, espérons-le, inutiles lorsque les développeurs de Paralives ajouteront davantage de code de correction des erreurs au jeu.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Avancé

### Purger le dossier de mods locaux

* Cela est nécessaire afin de repartir correctement de zéro.
* Steam Cloud peut devoir être désactivé afin d'empêcher la restauration de fichiers corrompus pendant les tests.

1. Coupez et collez le dossier de mods locaux dans un emplacement sûr en dehors des fichiers du jeu, tel que le bureau.
2. Vérifiez l'intégrité des fichiers du jeu avec Steam.
3. Redémarrez le jeu. Lorsque le jeu est démarré, Paralives régénérera entièrement le dossier de mods locaux à partir de zéro.
4. Vérifiez qu'un nouveau dossier de mods locaux a été généré.
5. Vérifiez si le problème est résolu.

   * Oui : réintroduisez les fichiers importants à partir de la copie créée à l'étape 1.
   * Non : essayez d'autres méthodes pour résoudre le problème avant de réintroduire les anciens fichiers.
6. Ajoutez uniquement au nouveau dossier Paralives les fichiers considérés comme sûrs afin de réduire les risques de recopier les fichiers de données corrompus.

### Modifier directement les fichiers de sauvegarde pour supprimer les données corrompues

* Les fichiers de sauvegarde sont des fichiers texte et peuvent être modifiés directement.
* N'importe quel éditeur de texte peut être utilisé, mais Notepad++ avec un plugin permettant de formater les fichiers json est recommandé.
* Le tutoriel lié ci-dessous explique comment les fichiers de sauvegarde sont structurés.

Explication du dossier de mods locaux ⁠Mod Folder/Save Folder

### Déplacer les parties sûres d'une sauvegarde vers un nouveau fichier de sauvegarde

* Lorsque le problème de la sauvegarde ne peut pas être identifié, déplacez de petites parties vers une nouvelle sauvegarde.
* Cette méthode peut être utile pour tenter d'identifier les fichiers corrompus.
* Par exemple, les dossiers de foyers peuvent être glissés entre les sauvegardes avec une perte de données relativement minime.
* Le tutoriel lié ci-dessous explique comment les fichiers de sauvegarde sont structurés.

Explication du dossier de mods locaux ⁠Mod Folder/Save Folder

### Utiliser les commandes de console pour reconstruire les personnages dans une nouvelle sauvegarde

* Lorsque tout est perdu, il est peut-être préférable de recommencer sur une nouvelle sauvegarde, mais avec un peu d'avance.
* Des commandes telles que `SETMONEY` peuvent être utilisées pour ajouter de l'argent.
* Les commandes peuvent être utilisées pour restaurer les compétences, les recettes et bien plus encore.
* Le tutoriel lié ci-dessous explique les commandes de triche disponibles.

Tutoriel sur les commandes de triche ⁠Console and Cheat Commands

---

> **Faites une sauvegarde complète de vos fichiers de sauvegarde avant de tenter l'une de ces étapes !**

# « La solution habituelle »

La méthode radicale pour résoudre la plupart des problèmes en supprimant chaque fichier associé au jeu afin d'obtenir le meilleur nouveau départ possible. Je ne recommande pas cette solution pour tous les problèmes, car elle peut rendre d'anciennes sauvegardes modifiées injouables sans les mods dont elles dépendent pour fonctionner correctement.

## Purger tous les fichiers du jeu pour repartir de zéro

1. Purgez les fichiers du jeu en coupant et collant l'intégralité du dossier de mods locaux paralives/paralives sur le bureau.
2. Désabonnez-vous de tous les mods Steam Workshop et supprimez tous les fichiers de mods restants.
3. Vérifiez l'intégrité des fichiers du jeu avec Steam ou réinstallez le jeu.
4. Redémarrez Paralives.
5. Commencez une nouvelle sauvegarde.
6. Si le jeu fonctionne maintenant, annulez progressivement les modifications jusqu'à ce que le problème réapparaisse ; vous connaîtrez alors la cause du problème.

---

# Prévenir la corruption des données

## Faites des copies de TOUT et SOUVENT

* Faites une copie physique des fichiers importants dans un emplacement sûr tel que le bureau, en dehors des fichiers du jeu.
* Les fichiers accessibles par le moteur du jeu Paralives peuvent toujours être corrompus.

> Remarque : La commande ZIPSAVEFILE créera une copie de votre sauvegarde actuelle sur le bureau. Elle peut écraser l'ancienne copie si la commande est utilisée deux fois.

Tutoriel sur les commandes de triche ⁠Console and Cheat Commands

`ZIPSAVEFILE` crée un zip du fichier de sauvegarde actuel sur le bureau

## Lisez les avis sur les mods

* Et laissez également des avis !
* Les commentaires sur les mods permettent au moddeur et aux autres utilisateurs de partager des informations sur les mods.
* Si le mod semble défectueux, informez-en le moddeur afin qu'il puisse le corriger !

## Désactiver Steam Cloud

* Steam Cloud est formidable pour protéger les fichiers importants, mais il provoque parfois des problèmes difficiles à trouver.
* Steam Cloud aime restaurer des fichiers obsolètes sans prévenir et simplement les déposer là pour que vous les découvriez plus tard.

## Supprimer correctement les mods

* Les mods ajoutent des références d'éléments au jeu.
* Chaque instance de ces éléments doit être supprimée manuellement de la sauvegarde du jeu AVANT de supprimer le mod.
* Il est beaucoup plus facile de supprimer les éléments d'un mod dans le jeu plutôt qu'en modifiant un fichier de sauvegarde.
* Supprimez ce canapé élégant et ce joli pull avant de supprimer le mod !

## Mettre à jour les pilotes

* Pour ce tutoriel, le pilote à privilégier est celui de la carte graphique (GPU).
* Pour Windows, téléchargez l'application Nvidia ou AMD et installez le nouveau pilote tous les quelques mois.

## Mettre à jour le système d'exploitation

* Oui, c'est pénible, mais c'est important !
* Exécutez régulièrement les logiciels de mise à jour intégrés tels que Windows Update.

## Installez les mods progressivement et vérifiez les mods installés individuellement ou en petits lots

* Cela peut aider le jeu à traiter chaque fichier sans faire d'erreurs.

## Maintenance préventive du matériel

* Prenez soin de l'ordinateur et il prendra soin de vous.
* Installez et exécutez un logiciel anti-malware obtenu de manière sûre.
* Inspectez les dommages physiques et nettoyez la poussière.
* Exécutez les programmes intégrés permettant de vérifier l'état et la stabilité des composants.

---

# Ressources supplémentaires

## Discussions traitant des problèmes de mods (où je trouve mes sujets de test)

* Recommandations de corrections des développeurs
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Méga-fil sur les mods manquants
  https://discord.com/channels/595045400805769238/1517352862395404499
* Mods qui ne se chargent pas
  https://discord.com/channels/595045400805769238/1517449529174130779
* Erreurs de référence nulle
  https://discord.com/channels/595045400805769238/1517532031662424154
* Erreurs de référence nulle
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* Fichiers de mods corrompus
  https://discord.com/channels/595045400805769238/1517266950944981062
* Wiki de Paralives
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Journal des modifications de Paralives
  https://www.paralives.com/news
* Développement de Paralives
  https://www.paralives.com/development
* Feuille de route de Paralives
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Bugs connus
  https://discord.com/channels/595045400805769238/1508927230154244216
* Feuille de route de Paralives
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Bugs connus
  known-issues-and-bugs
