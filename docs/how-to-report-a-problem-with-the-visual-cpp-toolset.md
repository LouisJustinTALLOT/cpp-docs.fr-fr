---
title: Guide pratique pour signaler un problème avec l’ensemble d’outils Visual C++
ms.date: 06/21/2018
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 50b1005c7734b62941cbda087161d5ec41a0d026
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57808038"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Guide pratique pour signaler un problème avec la documentation ou l’ensemble d’outils Visual C++

Si vous rencontrez des problèmes avec le compilateur Microsoft Visual C++, l’éditeur de liens ou autres outils et bibliothèques, nous aimerions les connaître. Si le problème se trouve dans notre documentation, nous aimerions aussi le savoir.

## <a name="how-to-report-a-c-toolset-issue"></a>Comment signaler un problème avec l’ensemble d’outils C++

La meilleure façon de nous informer d’un problème consiste à nous envoyer un rapport qui inclut une description du problème que vous avez rencontré, des informations sur la façon dont vous générez votre programme et une *reproduction* qui nous servira à reproduire le problème sur nos propres ordinateurs. Ces informations nous permettent de vérifier rapidement que le problème existe dans notre code et qu’il n’est pas propre à votre environnement, de déterminer s’il affecte d’autres versions du compilateur et de diagnostiquer sa cause.

Dans les sections ci-dessous, vous allez découvrir ce qui constitue un bon rapport, comment générer une reproduction pour le type de problème que vous avez trouvé et comment envoyer votre rapport à l’équipe produit. Vos rapports sont importants pour nous ainsi que pour d’autres développeurs comme vous. Merci de nous aider à améliorer Visual C++ !

## <a name="how-to-prepare-your-report"></a>Comment préparer votre rapport

Il est important de créer un rapport de qualité, car il est très difficile de reproduire le problème rencontré sur nos propres ordinateurs sans informations complètes. Plus votre rapport est exhaustif, plus nous serons en mesure de recréer et diagnostiquer le problème efficacement.

Au minimum, votre rapport doit contenir les éléments suivants :

- Informations sur la version complète de l’ensemble d’outils que vous utilisez.

- Ligne de commande cl.exe complète utilisée pour générer votre code.

- Description détaillée du problème rencontré.

- Une reproduction est un exemple de code source simplifié et autonome qui illustre le problème.

Poursuivez votre lecture pour en savoir plus sur les informations spécifiques dont nous avons besoin, l’endroit où vous pouvez les trouver et la façon de créer une bonne reproduction.

### <a name="the-toolset-version"></a>Version de l’ensemble d’outils

Nous avons besoin d’informations complètes sur la version et l’architecture cible de l’ensemble d’outils qui entraînent le problème pour pouvoir tester votre reproduction avec le même ensemble d’outils sur nos ordinateurs. Si nous pouvons reproduire le problème, ces informations nous donnent également un point de départ pour rechercher si d’autres versions de l’ensemble d’outils présentent le même problème.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Pour indiquer la version complète du compilateur que vous utilisez

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet. Par exemple, si vous générez vos projets en utilisant Visual Studio 2017 sur x64 pour des cibles x64, choisissez **Invite de commandes des outils natifs x64 pour VS 2017**. Pour plus d’informations, consultez [Raccourcis de l’invite de commandes développeur](build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /Bv**.

La sortie doit ressembler à ceci :

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

Copiez et collez l’intégralité de la sortie dans votre rapport.

### <a name="the-command-line"></a>Ligne de commande

Nous avons besoin de la ligne de commande exacte (cl.exe et tous ses arguments) utilisée pour générer votre code afin de pouvoir le générer exactement de la même façon sur nos ordinateurs. Ce point est important, car le problème que vous avez rencontré peut uniquement se produire lors de la génération avec un certain argument ou une certaine combinaison d’arguments.

L’endroit le plus approprié pour trouver ces informations se situe dans le journal de génération immédiatement après avoir rencontré le problème. Cela permet de garantir que la ligne de commande contient exactement les mêmes arguments pouvant contribuer au problème.

#### <a name="to-report-the-contents-of-the-command-line"></a>Pour signaler le contenu de la ligne de commande

1. Recherchez le fichier **CL.command.1.tlog** et ouvrez-le. Par défaut, ce fichier se trouve dans votre dossier Documents dans \\Visual Studio *version*\\Projets\\*NomSolution*\\*NomProjet*\\*Configuration*\\*NomProjet*.tlog\\CL.command.1.tlog ou dans votre dossier Utilisateur sous \\Source\\Référentiels\\*NomSolution*\\*NomProjet*\\*Configuration*\\*NomProjet*.tlog\\CL.command.1.tlog. Il peut se trouver dans un autre emplacement si vous utilisez un autre système de build ou si vous avez changé l’emplacement par défaut de votre projet.

   Dans ce fichier, vous trouverez les noms des fichiers de code source suivis des arguments de ligne de commande utilisés pour les compiler, chacun sur une ligne distincte.

1. Recherchez la ligne qui contient le nom du fichier de code source dans lequel le problème se produit ; la ligne en dessous contient les arguments de la commande cl.exe correspondants.

Copiez et collez l’intégralité de la ligne de commande dans votre rapport.

### <a name="a-description-of-the-problem"></a>Description du problème

Nous avons besoin d’une description détaillée du problème que vous avez rencontré pour pouvoir vérifier que nous constatons le même effet sur nos ordinateurs ; il nous est également parfois utile de savoir ce que vous tentiez d’effectuer et ce à quoi vous vous attendiez.

Fournissez les **messages d’erreur exacts** que vous recevez de l’ensemble d’outils ou le comportement d’exécution exact que vous voyez. Nous avons besoin de ces informations pour vérifier que nous avons correctement reproduit le problème. Incluez **l’intégralité** de la sortie du compilateur, pas juste le dernier message d’erreur. Nous devons voir tout ce qui a conduit au problème que vous signalez. Si vous pouvez dupliquer le problème avec le compilateur de ligne de commande, cette sortie du compilateur est préférable. En effet, l’IDE et autres systèmes de build peuvent filtrer les messages d’erreur que vous voyez ou capturer uniquement la première ligne d’un message d’erreur.

Si le problème vient du compilateur qui accepte du code non valide et ne génère pas de diagnostic, notez ce point dans votre rapport.

Pour signaler un problème de comportement d’exécution, ajoutez une **copie exacte** de ce que le programme envoie et de ce que vous vous attendez à voir. Dans l’idéal, c’est incorporé dans l’instruction de sortie elle-même, par exemple, `printf("This should be 5: %d\n", actual_result);`. Si votre programme plante ou se bloque, mentionnez-le également.

Ajoutez tout autre détail susceptible de nous aider à diagnostiquer le problème que vous rencontrez, comme des solutions de contournement éventuellement trouvées. Évitez de répéter des informations qui figurent ailleurs dans votre rapport.

### <a name="the-repro"></a>Reproduction

Une reproduction est un exemple de code source complet et autonome qui reproduit le problème que vous avez rencontré (d’où son nom). Nous avons besoin d’une reproduction pour pouvoir reproduire l’erreur sur nos ordinateurs. Le code doit être suffisant en lui-même pour créer un exécutable simple qui se compile et s’exécute, ou qui aurait dû se compiler et s’exécuter si vous n’aviez pas rencontré de problème. Une reproduction n’est pas un extrait de code ; elle doit avoir des classes et des fonctions complètes et contenir toutes les directives #include, même pour les en-têtes standard.

#### <a name="what-makes-a-good-repro"></a>Ce qui constitue une bonne reproduction

Une bonne reproduction est :

- **Est minimale.** Les reproductions doivent être aussi courtes que possible tout en montrant exactement le problème rencontré. Les reproductions n’ont pas besoin d’être complexes ou réalistes. Il faut juste qu’elles affichent le code qui est conforme au standard ou à l’implémentation documentée du compilateur, ou dans le cas d’absence de diagnostic, le code qui n’est pas conforme. Les reproductions simples et directes qui contiennent juste assez de code pour illustrer le problème sont les meilleures. Si vous pouvez enlever ou simplifier du code tout en restant conforme et sans modifier le problème, n’hésitez pas. Vous n’avez pas besoin d’ajouter de contre-exemples de code qui fonctionnent.

- **Est autonome.** Les reproductions doivent éviter les dépendances inutiles. Si vous pouvez reproduire le problème sans bibliothèques tierces, faites-le. Si vous pouvez reproduire le problème sans code de bibliothèque avec des instructions de sortie simples (par exemple, `puts("this shouldn't compile");`, `std::cout << value;` et `printf("%d\n", value);` sont OK), n’hésitez pas. Si l’exemple peut être condensé dans un seul fichier de code source, sans référence à aucun en-tête utilisateur, c’est parfait. Vous nous aiderez considérablement en réduisant la quantité de code que nous devons examiner comme facteur possible du problème.

- **Utilise la dernière version du compilateur.** Les reproductions doivent utiliser la dernière mise à jour vers la dernière version de l’ensemble d’outils ou la préversion la plus récente de la prochaine mise à jour ou de la prochaine version majeure, si possible. Les problèmes que vous pouvez rencontrer dans des versions antérieures de l’ensemble d’outils ont très souvent été résolus dans les versions plus récentes. Les correctifs ne sont reportés que très rarement sur des versions antérieures.

- **Comparée à d’autres compilateurs**, le cas échéant. Les reproductions qui impliquent du code C++ portable doivent vérifier le comportement par rapport à d’autres compilateurs si possible. Le standard finit toujours par déterminer si le programme est correct. Aucun compilateur n’est parfait, mais si Clang et GCC acceptent votre code sans diagnostic alors que MSVC non, vous voyez probablement un bogue dans notre compilateur. (Autres possibilités : des différences de comportement entre Unix et Windows ou différents niveaux d’implémentation de standards C++, etc.) En revanche, si tous les compilateurs rejettent votre code, c’est probablement que votre code est incorrect. Voir différents messages d’erreur peut vous aider à diagnostiquer le problème vous-même.

   Vous pouvez trouver des listes de compilateurs en ligne pour tester votre code avec des [compilateurs C++ en ligne](https://isocpp.org/blog/2013/01/online-c-compilers) sur le site web C++ ISO ou cette [liste de compilateurs C++ en ligne](https://arnemertz.github.io/online-compilers/) organisée sur GitHub. Voici quelques exemples spécifiques : [Wandbox](https://wandbox.org/), [Compiler Explorer](https://godbolt.org/) et [Coliru](http://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Les sites web de compilateurs en ligne ne sont pas affiliés à Microsoft. De nombreux sites web de compilateurs en ligne sont gérés en tant que projets personnels et certains de ces sites ne seront peut-être pas disponibles lorsque vous lirez ceci, mais vous devriez en trouver d’autres que vous pourrez utiliser.

Les problèmes dans le compilateur, l’éditeur de liens et les bibliothèques ont tendance à apparaître de manière spécifique. Le type de problème que vous rencontrez détermine le type de reproduction à inclure dans votre rapport. Sans une reproduction appropriée, nous n’avons rien à examiner. Voici quelques-uns des types de problèmes que vous pouvez voir et les instructions permettant de générer les types de reproductions que vous devez utiliser pour signaler chaque type de problème.

#### <a name="frontend-parser-crash"></a>Blocage de serveur frontal (analyseur)

Les blocages de serveur frontal se produisent pendant la phase d’analyse du compilateur. En règle générale, le compilateur indique [Erreur irrécupérable C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) et fait référence au fichier de code source et au numéro de ligne où l’erreur s’est produite ; il mentionne souvent un fichier msc1.cpp, mais vous pouvez ignorer ce détail.

Pour ce type de blocage, fournissez une [reproduction prétraitée](#preprocessed-repros).

Voici un exemple de sortie du compilateur pour ce type de blocage :

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>Blocage du backend (génération de code)

Les blocages de serveur principal se produisent pendant la phase de génération de code du compilateur. En règle générale, le compilateur indique [Erreur irrécupérable C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) et peut ne pas référencer le fichier de code source ni le numéro de ligne associés au problème ; il mentionne souvent le compilateur de fichiers\\utc\\src\\p2\\main.c, mais vous pouvez ignorer ce détail.

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros) si vous utilisez la génération de code durant l’édition de liens (LTCG), activée par l’argument de ligne de commande **/GL** dans cl.exe. Sinon, fournissez une [reproduction prétraitée](#preprocessed-repros) à la place.

Voici un exemple de sortie du compilateur pour un blocage de backend quand la génération LTCG n’est pas utilisée. Si la sortie du compilateur ressemble à ceci, vous devez fournir une [reproduction prétraitée](#preprocessed-repros).

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Si la ligne qui commence par **ERREUR INTERNE DU COMPILATEUR** mentionne link.exe plutôt que cl.exe, la génération LTCG a été activée et vous devez fournir une [reproduction de lien](#link-repros). Si le message d’erreur du compilateur n’indique pas clairement si la génération LTCG a été activée, vous devez peut-être examiner les arguments de ligne de commande que vous avez copiés à partir du journal de génération dans une étape précédente pour l’argument de ligne de commande **/GL**.

#### <a name="linker-crash"></a>Blocage d’éditeur de liens

Les blocages d’éditeur de liens se produisent pendant la phase d’édition des liens, après l’exécution du compilateur. En règle générale, l’éditeur de liens indique [Erreur des outils Éditeur de liens LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Si la sortie mentionne C1001 ou implique la génération de code durant l’édition de liens, reportez-vous plutôt à [Blocage de serveur principal (génération de code)](#backend-code-generation-crash) pour plus d’informations.

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros).

Voici un exemple de sortie du compilateur pour ce type de blocage.

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Si l’édition des liens incrémentielle est activée et que le blocage se produit seulement après une édition initiale réussie des liens (autrement dit, seulement après la première édition complète des liens sur laquelle l’édition des liens incrémentielle suivante est basée), fournissez également une copie des fichiers objet (.obj) et bibliothèque (.lib) correspondant aux fichiers sources qui ont été modifiés une fois l’édition initiale des liens terminée.

#### <a name="bad-code-generation"></a>Génération de code incorrect

La génération de code incorrect est rare, mais se produit quand le compilateur génère par inadvertance du code incorrect qui entraîne le blocage de votre application au moment de l’exécution au lieu de détecter ce problème au moment de la compilation. Si vous pensez que le problème que vous rencontrez occasionne une génération de code incorrect, traitez votre rapport comme dans [Blocage de serveur principal (génération de code)](#backend-code-generation-crash).

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros) si vous utilisez la génération de code durant l’édition de liens (LTCG), activée par l’argument de ligne de commande **/GL** dans cl.exe. Sinon, fournissez une [reproduction prétraitée](#preprocessed-repros).

## <a name="how-to-generate-a-repro"></a>Comment générer une reproduction

Pour nous aider à trouver la source du problème, une [bonne reproduction](#what-makes-a-good-repro) est indispensable. Avant de suivre les étapes décrites ci-dessous pour certains types de reproductions, essayez de condenser le code qui illustre le problème autant que possible. Essayez d’éliminer ou de minimiser les dépendances, les en-têtes nécessaires et les bibliothèques, et de limiter les options du compilateur et les définitions de préprocesseur utilisées, si possible.

Vous trouverez ci-dessous des instructions pour générer les différents types de reproductions que vous utiliserez pour signaler différents types de problèmes.

### <a name="preprocessed-repros"></a>Reproductions prétraitées

Une *reproduction prétraitée* est un seul fichier source qui illustre un problème, généré à partir de la sortie du préprocesseur C en utilisant l’option du compilateur **/P** du fichier source de reproduction d’origine. Cela intègre les en-têtes inclus pour supprimer les dépendances sur d’autres fichiers sources et d’en-tête, et résout également des macros, des valeurs #ifdef et d’autres commandes de préprocesseur qui pourraient dépendre de votre environnement local.

> [!NOTE]
> Les reproductions prétraitées ne sont pas aussi utiles pour les problèmes qui peuvent être le résultat de bogues dans notre implémentation de bibliothèque standard, car nous voulons souvent substituer notre dernière implémentation en cours pour voir si nous avons déjà résolu le problème. Dans ce cas, ne prétraitez pas la reproduction et, si vous ne pouvez pas réduire le problème à un seul fichier source, empaquetez votre code dans un fichier .zip ou similaire, ou utilisez une reproduction de projet IDE. Pour plus d’informations, consultez [Autres reproductions](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Pour prétraiter un fichier de code source

1. Capturez les arguments de ligne de commande utilisés pour générer votre reproduction, comme décrit dans [Pour signaler le contenu de la ligne de commande](#to-report-the-contents-of-the-command-line).

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet.

1. Accédez au répertoire qui contient votre projet de reproduction.

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *filename.cpp*, où *arguments* est la liste des arguments capturés ci-dessus et *filename.cpp* est le nom du fichier source de votre reproduction. Cette commande réplique la ligne de commande utilisée pour la reproduction, mais arrête la compilation après le passage du préprocesseur, et génère en sortie le code source prétraité dans *filename*.i.

Si vous prétraitez un fichier de code source C++/CX ou utilisez la fonctionnalité Modules C++, vous devez effectuer des étapes supplémentaires. Pour plus d’informations, consultez les sections ci-dessous.

Une fois que vous avez généré le fichier prétraité, il est judicieux de vérifier que le problème se reproduit toujours avec le fichier prétraité.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Pour confirmer que l’erreur se reproduit toujours avec le fichier prétraité

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl** *arguments* **/TP** *filename*.i pour indiquer à cl.exe de compiler le fichier prétraité en fichier source C++, où *arguments* est la liste des arguments capturés ci-dessus, mais avec les arguments **/D** et **/I** supprimés (car ils ont déjà été inclus dans le fichier prétraité) ; et où *filename*.i est le nom de votre fichier prétraité.

1. Confirmez que le problème est reproduit.

Enfin, attachez la reproduction prétraitée *filename*.i à votre rapport.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Reproductions de code C++/CX WinRT/UWP prétraitées

Si vous utilisez C++/CX pour générer votre exécutable, vous devez effectuer quelques étapes supplémentaires pour créer et valider une reproduction prétraitée.

#### <a name="to-preprocess-ccx-source-code"></a>Pour prétraiter du code source C++/CX

1. Créez un fichier source prétraité comme décrit dans [Pour prétraiter un fichier de code source](#to-preprocess-a-source-code-file).

1. Recherchez dans le fichier_filename_.i les directives **#using**.

1. Faites la liste de tous les fichiers référencés. Omettez tous les fichiers Windows\*.winmd, platform.winmd et mscorlib.dll.

Pour vérifier que le fichier prétraité reproduit toujours le problème, effectuez la préparation suivante :

1. Créez un répertoire et copiez le fichier prétraité dans le nouveau répertoire.

1. Copiez les fichiers .winmd figurant dans votre liste **#using** dans le nouveau répertoire.

1. Créez un fichier vccorlib.h vide dans le nouveau répertoire.

1. Modifiez le fichier prétraité de façon à supprimer toute directive **#using** pour mscorlib.dll.

1. Modifiez le fichier prétraité de façon à remplacer les chemins absolus par les simples noms des fichiers .winmd copiés.

Confirmez que le fichier prétraité reproduit toujours le problème, comme décrit ci-dessus.

### <a name="preprocessed-c-modules-repros"></a>Reproductions prétraitées utilisant des modules C++

Si vous utilisez la fonctionnalité Modules du compilateur C++, vous devez suivre une procédure différente pour créer et valider une reproduction prétraitée.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Pour prétraiter un fichier de code source qui utilise un module

1. Capturez les arguments de ligne de commande utilisés pour générer votre reproduction, comme décrit dans [Pour signaler le contenu de la ligne de commande](#to-report-the-contents-of-the-command-line).

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet.

1. Accédez au répertoire qui contient votre projet de reproduction.

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *filename.cpp*, où *arguments* est la liste des arguments capturés ci-dessus et *filename.cpp* le nom du fichier source qui consomme le module.

1. Passez au répertoire contenant le projet de reproduction qui a généré l’interface du module (sortie .ifc).

1. Capturez les arguments de ligne de commande utilisés pour générer votre interface de module.

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *modulename.ixx*, où *arguments* est la liste des arguments capturés ci-dessus et *modulename.ixx* le nom du fichier qui crée l’interface du module.

Une fois que vous avez généré les fichiers prétraités, il est judicieux de vérifier que le problème se reproduit toujours avec le fichier prétraité.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Pour confirmer que l’erreur se reproduit toujours avec le fichier prétraité

1. Dans la fenêtre de console développeur, repassez au répertoire contenant votre projet de reproduction.

1. Entrez la commande **cl** *arguments* **/TP** *filename*.i, comme indiqué ci-dessus, pour compiler le fichier prétraité comme s’il s’agissait d’un fichier source C++.

1. Confirmez que le problème est toujours reproduit par le fichier prétraité.

Enfin, attachez à votre rapport les fichiers de reproduction prétraités (*filename*.i et *modulename*.i), ainsi que la sortie .ifc.

### <a name="link-repros"></a>Reproductions de liens

Une *reproduction de lien* est le contenu généré par l’éditeur de liens d’un répertoire spécifié par la variable d’environnement **link\_repro**. Elle contient les artefacts de build qui montrent collectivement un problème qui se produit au moment de la liaison, par exemple un blocage de backend qui implique la génération de code d’édition de liens (LTCG), ou un blocage de l’éditeur de liens. Ces artefacts de build sont ceux nécessaires comme entrée de l’éditeur de liens pour que le problème puisse être reproduit. Une reproduction de lien peut être créée facilement à l’aide de cette variable d’environnement pour activer la fonctionnalité de génération de reproduction intégrée de l’éditeur de liens.

#### <a name="to-generate-a-link-repro"></a>Pour générer une reproduction de lien

1. Capturez les arguments de ligne de commande utilisés pour générer votre reproduction, comme décrit dans [Pour signaler le contenu de la ligne de commande](#to-report-the-contents-of-the-command-line).

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet.

1. Dans la fenêtre de console de l’invite de commandes développeur, accédez au répertoire qui contient votre projet de reproduction.

1. Entrez **mkdir linkrepro** pour créer un répertoire dédié à la reproduction de lien.

1. Entrez la commande **set link\_repro=linkrepro** pour définir la variable d’environnement **link\_repro** sur le répertoire que vous venez de créer. Si votre build s’exécute à partir d’un autre répertoire, comme cela est souvent le cas pour les projets plus complexes, affectez plutôt le chemin complet du répertoire linkrepro à **link\_repro**.

1. Pour générer le projet de reproduction dans Visual Studio, dans la fenêtre de la console de l’invite de commandes développeur, entrez la commande **devenv**. Cela garantit que la valeur de la variable d’environnement **link\_repro** est visible dans Visual Studio. Pour générer le projet sur la ligne de commande, utilisez les arguments de ligne de commande capturés au-dessus pour dupliquer la build de reproduction.

1. Générez votre projet de reproduction et confirmez que le problème attendu s’est produit.

1. Fermez Visual Studio si vous l’avez utilisé pour effectuer la build.

1. Dans la fenêtre de la console de l’invite de commandes développeur, entrez la commande **set link\_repro=** pour effacer la variable d’environnement **link\_repro**.

Enfin, empaquetez la reproduction en compressant l’ensemble du répertoire linkrepro dans un fichier .zip ou similaire et attachez-la à votre rapport.

### <a name="other-repros"></a>Autres reproductions

Si vous ne pouvez pas réduire le problème à un seul fichier source ou une reproduction prétraitée et que le problème ne nécessite pas une reproduction de lien, nous pouvons examiner un projet IDE. Toutes les instructions sur la création d’une bonne reproduction s’appliquent aussi : le code doit être minime et autonome, le problème doit se produire dans nos outils plus récent, et le cas échéant, le problème ne doit pas apparaître dans d’autres compilateurs.

Créez votre reproduction comme un projet IDE minimal, puis empaquetez-la en compressant l’intégralité de la structure de répertoire dans un fichier .zip ou similaire et attachez-la à votre rapport.

## <a name="ways-to-send-your-report"></a>Modes d’envoi de votre rapport

Pour nous faire parvenir votre rapport, deux options s’offrent à vous. Vous pouvez utiliser les pages intégrées de Visual Studio [Outil Signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ou [Communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/). Vous pouvez également accéder directement aux pages de la communauté de développeurs en choisissant le bouton **Commentaires sur le produit** en bas de cette page. Votre choix dépend de ce que vous voulez faire : soit utiliser les outils intégrés à l’IDE pour capturer des écrans et organiser votre rapport en vue de sa publication sur les pages de la communauté des développeurs, soit utiliser le site web directement.

> [!NOTE]
> Quelle que soit la manière dont vous envoyez votre rapport, Microsoft respecte votre vie privée. Microsoft s’engage à respecter toutes les lois et réglementations relatives à la confidentialité des données. Pour plus d’informations sur la façon dont nous utilisons les données que vous nous envoyez, consultez la [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Utiliser l’outil Signaler un problème

L’outil **Signaler un problème** dans Visual Studio est un moyen pour les utilisateurs de Visual Studio de signaler différents problèmes en quelques clics. Il fournit un formulaire simple qui vous permet de spécifier des informations détaillées sur le problème que vous avez rencontré et d’envoyer ensuite votre rapport sans jamais quitter l’IDE.

L’outil **Signaler un problème** est facile et pratique à utiliser à partir de l’IDE. Vous pouvez y accéder à partir de la barre de titre en choisissant l’icône **Envoyer des commentaires** à côté de la zone de recherche **Lancement rapide**, ou vous pouvez le trouver sur la barre de menus dans **Aide** >  **Envoyer des commentaires** > **Signaler un problème**.

Quand vous choisissez de signaler un problème, cherchez d’abord s’il en existe de similaires dans la Communauté des développeurs. Si votre problème a déjà été signalé, votez pour la rubrique et ajoutez des commentaires qui ajoutent de nouveaux éléments. Si vous ne voyez pas de problème similaire, choisissez le bouton **Signaler un nouveau problème** dans le bas de la boîte de dialogue Commentaires sur Visual Studio et suivez les étapes pour signaler votre problème.

### <a name="use-the-visual-studio-developer-community-pages"></a>Utiliser les pages de la Communauté des développeurs Visual Studio

Les pages de la Communauté des développeurs Visual Studio sont un autre moyen pratique de signaler des problèmes et de trouver des solutions pour Visual Studio, le compilateur C++, les outils et les bibliothèques. Il existe des pages de Communauté des développeurs propres à [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html), [Visual Studio pour Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [Azure DevOps](https://developercommunity.visualstudio.com/spaces/21/index.html) et [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html). Sous ces onglets, en haut de chaque page, se trouve une zone de recherche que vous pouvez utiliser pour rechercher des publications ou des rubriques qui signalent des problèmes similaires aux vôtres. Il est possible qu’une solution ou d’autres informations utiles relatives à votre problème soient déjà disponibles. Si quelqu’un a signalé le même problème, votez pour cette rubrique et ajoutez-y des commentaires au lieu de signaler un nouveau problème. Pour commenter, voter ou signaler un nouveau problème, vous pouvez être invité à vous connecter à votre compte Visual Studio et à accepter de donner à l’application Communauté des développeurs un accès à votre profil.

Pour les problèmes relatifs au compilateur, à l’éditeur de liens, et aux autres outils et bibliothèques C++, utilisez la page [C++](https://developercommunity.visualstudio.com/spaces/62/index.html). Si vous recherchez votre problème et qu’il n’a pas encore été signalé, choisissez le bouton **Signaler un problème** en regard de la zone de recherche en haut de la page. Vous pouvez inclure le code et la ligne de commande de votre reproduction, des captures d’écran, des liens vers des discussions qui s’y rapportent, et toute autre information que vous pensez pertinente et utile.

> [!TIP]
> Pour d’autres types de problèmes que vous pouvez rencontrer dans Visual Studio et qui ne sont pas liés à l’ensemble d’outils C++ (par exemple, des problèmes d’interface utilisateur, une fonctionnalité de l’IDE rompue ou des plantages généraux), utilisez l’outil **Signaler un problème** dans l’IDE. Il s’agit du meilleur choix, en raison de ses fonctionnalités de capture d’écran et de sa capacité à enregistrer des actions d’interface utilisateur qui mènent à un problème que vous avez rencontré. Ces types d’erreurs peuvent également être recherchés sur le site [Communauté des développeurs](https://developercommunity.visualstudio.com/). Pour plus d’informations, consultez [Guide pratique pour signaler un problème avec Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Rapports et confidentialité

Par défaut, **toutes les informations contenues dans les rapports, ainsi que les commentaires et les réponses qui peuvent y figurer, sont visibles publiquement**. Il s’agit en général d’un avantage dans la mesure où toute la communauté a accès aux problèmes, solutions et solutions de contournement identifiés par d’autres utilisateurs. Toutefois, si le fait de présenter au public vos données ou votre identité vous préoccupe, que ce soit pour des raisons de confidentialité ou de propriété intellectuelle, vous avez plusieurs options.

Si vous ne souhaitez pas révéler votre identité, [créez un compte Microsoft](https://signup.live.com/) qui ne divulgue aucun détail vous concernant. Utilisez ce compte pour créer votre rapport.

**Ne placez pas d’informations privées dans le titre ou le contenu du rapport initial, qui est public.** Au lieu de cela, envoyez des détails en privé dans un commentaire séparé. Pour garantir que votre rapport s’adresse aux bonnes personnes, ajoutez **cppcompiler** dans la liste des rubriques de votre rapport de problème. Une fois le rapport de problème créé, vous pouvez désormais spécifier qui peut voir vos réponses et pièces jointes.

#### <a name="to-create-a-problem-report-for-private-information"></a>Pour créer un rapport de problème avec des informations privées

1. Dans le rapport que vous avez créé, choisissez **Ajouter un commentaire** pour créer une description privée du problème.

1. Dans l’éditeur de réponse, utilisez le contrôle de liste déroulante sous **Envoyer** et **Annuler** pour spécifier l’audience de votre réponse. Seules les personnes que vous spécifiez peuvent voir ces réponses privées et les images, liens ou extraits de code inclus. Choisissez **Viewable by moderators and the original poster** (Consultable par les modérateurs et l’auteur à l’origine de la publication) pour limiter la visibilité aux employés de Microsoft et à vous-même.

1. Ajoutez la description et les autres informations, images et pièces jointes de fichier nécessaires à la reproduction. Choisissez le bouton **Envoyer** pour envoyer ces informations en privé.

   Notez que les fichiers joints sont limités à 10 et qu’ils ne doivent pas dépasser 2 Go. Pour les chargements plus volumineux, demandez une URL de chargement dans votre commentaire privé.

Toutes les réponses figurant sous ce commentaire ont la même visibilité restreinte. Cela est vrai même si le contrôle de liste déroulante sur les réponses n’affiche pas correctement l’état de visibilité.

Pour assurer votre confidentialité et ne pas dévoiler d’informations sensibles au public, veillez à limiter toutes les interactions avec Microsoft aux réponses sous ce commentaire restreint. Le fait de répondre à d’autres commentaires peut vous amener à divulguer accidentellement des informations sensibles.

## <a name="how-to-report-a-c-documentation-issue"></a>Comment signaler un problème dans la documentation C++

Nous utilisons les problèmes GitHub pour faire le suivi des problèmes liés à notre documentation. Vous pouvez désormais créer des problèmes GitHub directement à partir d’une page de contenu, ce qui permet d’améliorer considérablement l’interaction avec les rédacteurs et les équipes produit. Si vous constatez un problème lié à un document, un exemple de code incorrect, une explication confuse, une omission critique ou simplement une faute d’orthographe, vous pouvez facilement nous en faire part. Faites défiler la page jusqu’en bas et sélectionnez **Se connecter pour fournir des commentaires sur la documentation**. Si ce n’est pas déjà fait, créez un compte GitHub. Une fois que vous disposez d’un compte, vous pouvez voir tous les problèmes liés à notre documentation, noter leur état et recevoir des notifications quand des modifications sont apportées au problème que vous avez signalé. Pour plus d’informations, consultez [A New Feedback System Is Coming to docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Quand vous créez sur GitHub un problème lié à la documentation à l’aide du bouton de commentaires sur la documentation, le problème est automatiquement accompagné d’informations sur la page concernée pour que nous puissions le trouver. Ne modifiez pas ces informations. Ajoutez simplement les détails relatifs au problème rencontré et, si vous le souhaitez, une suggestion de correction. [Notre documentation étant open source](https://github.com/MicrosoftDocs/cpp-docs/), vous pouvez mettre au point un correctif et le proposer vous-même. Pour plus d’informations sur la façon dont vous pouvez contribuer à notre documentation, consultez notre [guide consacré aux contributions](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) sur GitHub.
