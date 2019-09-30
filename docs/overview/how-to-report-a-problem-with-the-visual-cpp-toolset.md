---
title: Guide pratique pour signaler un problème avec l’ensemble d’outils Microsoft C++
description: Comment créer un rapport de problème et des informations de reproduction corrects C++ pour l’ensemble d’outils Microsoft.
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685701"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Guide pratique pour signaler un problème avec la documentation ou l’ensemble d’outils Microsoft C++

Si vous rencontrez des problèmes avec le compilateur Microsoft C++ (MSVC), l’éditeur de liens ou autres outils et bibliothèques, nous aimerions les connaître. Si le problème se trouve dans notre documentation, nous aimerions aussi le savoir.

## <a name="how-to-report-a-c-toolset-issue"></a>Comment signaler un problème avec l’ensemble d’outils C++

La meilleure façon de nous informer d’un problème consiste à nous envoyer un rapport qui inclut une description du problème que vous avez rencontré. Le rapport doit inclure tous les détails sur la façon dont vous générez votre programme. Il doit aussi inclure une *reproduction*, un cas de test terminé que nous pouvons utiliser pour reproduire le problème sur nos propres machines. Ces informations nous permettent de vérifier rapidement que le problème existe dans notre code et qu’il n’est pas propre à votre environnement. Elles nous permettent de déterminer s’il affecte d’autres versions du compilateur, et nous aident à diagnostiquer sa cause.

Dans les sections ci-dessous, vous allez découvrir ce qui constitue un bon rapport. Nous décrivons comment générer une reproduction pour le type de problème que vous avez trouvé et comment envoyer votre rapport à l’équipe produit. Vos rapports sont importants pour nous ainsi que pour d’autres développeurs comme vous. Merci de nous aider à améliorer Microsoft C++ !

## <a name="how-to-prepare-your-report"></a>Comment préparer votre rapport

Il est important de créer un rapport de haute qualité, car il est difficile pour nous de reproduire le problème que vous avez rencontré sans informations complètes. Plus votre rapport est exhaustif, plus nous pourrons recréer et diagnostiquer le problème efficacement.

Au minimum, votre rapport doit contenir les éléments suivants :

- Informations sur la version complète de l’ensemble d’outils que vous utilisez.

- Ligne de commande cl.exe complète utilisée pour générer votre code.

- Description détaillée du problème rencontré.

- Une reproduction est un exemple de code source simplifié et autonome qui illustre le problème.

Poursuivez votre lecture pour en savoir plus sur les informations spécifiques dont nous avons besoin, l’endroit où vous pouvez les trouver et la façon de créer une bonne reproduction.

### <a name="the-toolset-version"></a>Version de l’ensemble d’outils

Nous avons besoin des informations complètes sur la version et de l’architecture cible de l’ensemble d’outils qui provoque le problème. Cela nous permettra de tester votre reproduction avec le même ensemble d’outils sur nos machines. Si nous pouvons reproduire le problème, ces informations nous donnent également un point de départ pour rechercher si d’autres versions de l’ensemble d’outils présentent le même problème.

#### <a name="to-report-the-full-version-of-your-compiler"></a>Pour indiquer la version complète de votre compilateur

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet. Par exemple, si vous générez vos projets en utilisant Visual Studio 2017 sur x64 pour des cibles x64, choisissez **Invite de commandes des outils natifs x64 pour VS 2017**. Pour plus d’informations, consultez [Raccourcis de l’invite de commandes développeur](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /Bv**.

La sortie doit ressembler à :

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

Nous avons besoin de la ligne de commande exacte (cl.exe et tous ses arguments) que vous utilisez pour générer votre code. Cela nous permettra de compiler exactement de la même façon sur nos machines. Ce point est important, car le problème que vous avez rencontré peut uniquement se produire lors de la génération avec un certain argument ou une certaine combinaison d’arguments.

L’endroit le plus approprié pour trouver ces informations se situe dans le journal de génération immédiatement après avoir rencontré le problème. Cela permet de garantir que la ligne de commande contient exactement les mêmes arguments pouvant contribuer au problème.

#### <a name="to-report-the-contents-of-the-command-line"></a>Pour signaler le contenu de la ligne de commande

1. Recherchez le fichier **CL.command.1.tlog** et ouvrez-le. Par défaut, ce fichier se trouve dans votre dossier Documents dans \\Visual Studio *version*\\Projets\\*NomSolution*\\*NomProjet*\\*Configuration*\\*NomProjet*.tlog\\CL.command.1.tlog ou dans votre dossier Utilisateur sous \\Source\\Référentiels\\*NomSolution*\\*NomProjet*\\*Configuration*\\*NomProjet*.tlog\\CL.command.1.tlog. Il peut se trouver dans un autre emplacement si vous utilisez un autre système de build ou si vous avez changé l’emplacement par défaut de votre projet.

   Dans ce fichier, vous trouverez les noms de vos fichiers de code source suivis des arguments de ligne de commande utilisés pour les compiler, chacun sur une ligne distincte.

1. Recherchez la ligne qui contient le nom du fichier de code source dans lequel le problème se produit. La ligne ci-dessous contient les arguments de commande cl.exe correspondants.

Copiez et collez l’intégralité de la ligne de commande dans votre rapport.

### <a name="a-description-of-the-problem"></a>Description du problème

Nous avons besoin d’une description détaillée du problème que vous avez rencontré. Cela nous permet de vérifier que nous observons le même effet sur nos machines. Il est parfois utile de savoir ce que vous tentiez d’effectuer et ce à quoi vous vous attendiez.

Une bonne description fournit les **messages d’erreur exacts** que vous recevez de l’ensemble d’outils ou le comportement d’exécution exact que vous voyez. Nous avons besoin de ces informations pour vérifier que nous avons correctement reproduit le problème. Incluez **toute** la sortie du compilateur, pas juste le dernier message d’erreur. Nous devons voir tout ce qui a conduit au problème que vous signalez. Si vous pouvez dupliquer le problème avec le compilateur en ligne de commande, cette sortie de compilateur est préférable. L’IDE et les autres systèmes de compilation peuvent filtrer les messages d’erreur que vous voyez ou capturer uniquement la première ligne d’un message d’erreur.

Si le problème vient du compilateur qui accepte du code non valide et ne génère pas de diagnostic, notez cela dans votre rapport.

Pour signaler un problème de comportement d’exécution, ajoutez une **copie exacte** de ce que le programme envoie et de ce que vous vous attendez à voir. Dans l’idéal, incorporerez-les dans l’instruction de sortie elle-même, par exemple, `printf("This should be 5: %d\n", actual_result);`. Si votre programme plante ou se bloque, mentionnez-le également.

Ajoutez tout autre détail susceptible de nous aider à diagnostiquer le problème que vous rencontrez, comme des solutions de contournement éventuellement trouvées. Essayez de ne pas répéter les informations qui se trouvent ailleurs dans votre rapport.

### <a name="the-repro"></a>Reproduction

Une *reproduction* est un exemple de code source complet et autonome. Il reproduit le problème que vous avez rencontré, d’où le nom. Nous avons besoin d’une reproduction pour pouvoir reproduire l’erreur sur nos ordinateurs. Le code doit être suffisant en lui-même pour créer un exécutable de base qui se compile et s’exécute. Ou qui *pourrait* compiler et exécuter sans le problème que vous avez rencontré. Une reproduction n’est pas un extrait de code. Elle doit avoir des classes et des fonctions complètes et contenir toutes les directives #include, même pour les en-têtes standard.

#### <a name="what-makes-a-good-repro"></a>Ce qui constitue une bonne reproduction

Une bonne reproduction est :

- **Est minimale.** Les reproductions doivent être aussi courtes que possible tout en montrant exactement le problème rencontré. Les reproductions n’ont pas à être complexes ou réalistes. Il suffit qu’elles présentent un code qui est conforme à la norme ou à l’implémentation documentée du compilateur. Pour un diagnostic manquant, votre reproduction doit afficher le code qui n’est pas conforme. Les reproductions simples et directes qui contiennent juste assez de code pour illustrer le problème sont les meilleures. Si vous pouvez enlever ou simplifier du code tout en restant conforme et sans modifier le problème, n’hésitez pas. Vous n’avez pas besoin d’ajouter de contre-exemples de code qui fonctionnent.

- **Est autonome.** Les reproductions doivent éviter les dépendances inutiles. Si vous pouvez reproduire le problème sans bibliothèques tierces, faites-le. Si vous pouvez reproduire le problème sans code de bibliothèque avec des instructions de sortie simples (par exemple, `puts("this shouldn't compile");`, `std::cout << value;` et `printf("%d\n", value);`), n’hésitez pas. Si l’exemple peut être condensé dans un seul fichier de code source, sans référence à aucun en-tête utilisateur, c’est parfait. Vous nous aiderez considérablement en réduisant la quantité de code que nous devons examiner comme facteur possible du problème.

- **Utilise la dernière version du compilateur.** Les reproductions doivent utiliser la dernière mise à jour de la dernière version de l’ensemble d’outils dès que possible. Ou utilisez la version préliminaire la plus récente de la prochaine mise à jour ou version majeure. Les problèmes que vous pouvez rencontrer dans des versions antérieures de l’ensemble d’outils ont souvent été résolus dans les versions plus récentes. Les correctifs ne sont reportés que très rarement sur des versions antérieures.

- **Comparée à d’autres compilateurs**, le cas échéant. Les reproductions qui impliquent du code C++ portable doivent vérifier le comportement par rapport à d’autres compilateurs si possible. La norme C++ détermine l’exactitude du programme, et aucun compilateur n’est parfait. Toutefois, lorsque Clang et GCC acceptent votre code sans diagnostic et que MSVC ne le fait pas, vous avez probablement trouvé un bogue dans notre compilateur. (Autres possibilités : des différences de comportement entre Unix et Windows ou différents niveaux d’implémentation de standards C++, etc.) Si tous les compilateurs rejettent votre code, c’est probablement que votre code est incorrect. Voir différents messages d’erreur peut vous aider à diagnostiquer le problème vous-même.

   Vous pouvez trouver des listes de compilateurs en ligne pour tester votre code avec des [compilateurs C++ en ligne](https://isocpp.org/blog/2013/01/online-c-compilers) sur le site web C++ ISO ou cette [liste de compilateurs C++ en ligne](https://arnemertz.github.io/online-compilers/) organisée sur GitHub. Voici quelques exemples spécifiques : [Wandbox](https://wandbox.org/), [Compiler Explorer](https://godbolt.org/) et [Coliru](https://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Les sites web de compilateurs en ligne ne sont pas affiliés à Microsoft. De nombreux sites web de compilateurs en ligne sont proposés en tant que projets personnels. Certains de ces sites peuvent être indisponibles lorsque vous lirez ceci, mais vous devriez en trouver d’autres personnes que vous pourrez utiliser.

Les problèmes dans le compilateur, l’éditeur de liens et les bibliothèques ont tendance à apparaître de manière spécifique. Le type de problème que vous rencontrez détermine le type de reproduction à inclure dans votre rapport. Sans une reproduction appropriée, nous n’avons rien à examiner. Voici quelques-uns des types de problèmes que vous pouvez rencontrer. Nous incluons des instructions sur la façon de générer le type de reproduction que vous devez utiliser pour signaler chaque type de problème.

#### <a name="frontend-parser-crash"></a>Blocage de serveur frontal (analyseur)

Les blocages de serveur frontal se produisent pendant la phase d’analyse du compilateur. En règle générale, le compilateur émet une [Erreur irrécupérable C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md), et les références du fichier de code source avec la le numéro de la ligne à laquelle l’erreur s’est produite. Il mentionne souvent un fichier nommé msc1.cpp, mais vous pouvez ignorer ce détail.

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

Les blocages de serveur principal se produisent pendant la phase de génération de code du compilateur. En règle générale, le compilateur émet une [Erreur irrécupérable C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md) et il peut ne pas faire référence au fichier de code source et au numéro de la ligne associée au problème. Il mentionne souvent le fichier compiler\\utc\\src\\p2\\main.c, mais vous pouvez ignorer ce détail.

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros) si vous utilisez la génération de code durant l’édition de liens (LTCG), activée par l’argument de ligne de commande **/GL** dans cl.exe. Sinon, fournissez une [reproduction prétraitée](#preprocessed-repros) à la place.

Voici un exemple de sortie du compilateur pour un blocage de backend quand la génération LTCG n’est pas utilisée. Si la sortie du compilateur ressemble à ce qui suit, vous devez fournir une [reproduction prétraitée](#preprocessed-repros).

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

Si la ligne qui commence par **ERREUR INTERNE DU COMPILATEUR** mentionne link.exe plutôt que cl.exe, la génération LTCG a été activée. Fournissez une [reproduction de lien](#link-repros) dans ce cas. S’il n’est pas clair si la génération LTCG a été activée ou non à partir du message d’erreur du compilateur, examinez les arguments de ligne de commande. Vous les avez copiés partir de votre journal de génération à l’étape précédente pour l’argument de ligne de commande **/GL**.

#### <a name="linker-crash"></a>Blocage d’éditeur de liens

Les blocages d’éditeur de liens se produisent pendant la phase d’édition des liens, après l’exécution du compilateur. En règle générale, l’éditeur de liens indique [Erreur des outils Éditeur de liens LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Si la sortie mentionne C1001 ou implique la génération de code durant l’édition de liens, reportez-vous plutôt à [Blocage de serveur principal (génération de code)](#backend-code-generation-crash).

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros).

Voici un exemple de sortie du compilateur pour ce type de blocage :

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

La génération de code incorrect est rare. Cela se produit lorsque le compilateur génère par inadvertance du code incorrect qui incite votre application à se bloquer lors de l’exécution. Au lieu de cela, il doit générer du code correct ou détecter un problème au moment de la compilation. Si vous pensez que le problème que vous rencontrez occasionne une génération de code incorrect, traitez votre rapport comme dans [Blocage de serveur principal (génération de code)](#backend-code-generation-crash).

Pour ce type de blocage, fournissez une [reproduction de lien](#link-repros) si vous utilisez l’argument de ligne de commande **/GL** dans cl.exe. Fournissez une [reproduction prétraitée](#preprocessed-repros) si non.

## <a name="how-to-generate-a-repro"></a>Comment générer une reproduction

Pour nous aider à trouver la source du problème, une [bonne reproduction](#what-makes-a-good-repro) est indispensable. Avant de suivre les étapes décrites ci-dessous pour certains types de reproductions, essayez de condenser le code qui illustre le problème autant que possible. Essayez d’éliminer ou de minimiser les dépendances, les en-têtes requis et les bibliothèques. Limitez les options du compilateur et les définitions de préprocesseur utilisées, si possible.

Vous trouverez ci-dessous des instructions pour générer les différents types de reproductions que vous utiliserez pour signaler différents types de problèmes.

### <a name="preprocessed-repros"></a>Reproductions prétraitées

Une *reproduction prétraitée* est un fichier source unique qui illustre un problème. Il est généré à partir de la sortie du préprocesseur C. Pour en créer un, utilisez l’option **/P** du compilateur sur le fichier source de reproduction d’origine. Cette option intègre les en-têtes inclus pour supprimer des dépendances sur les fichiers sources et d’en-tête supplémentaires. L’option résout aussi les macros, les instructions conditionnelles #ifdef et les autres commandes de préprocesseur qui pourraient dépendre de votre environnement local.

> [!NOTE]
> Les reproductions prétraitées ne sont pas aussi utiles pour les problèmes qui peuvent être le résultat de bogues dans notre implémentation de bibliothèque standard, car nous voulons souvent substituer notre dernière implémentation en cours pour voir si nous avons déjà résolu le problème. Dans ce cas, ne prétraitez pas la reproduction et, si vous ne pouvez pas réduire le problème à un seul fichier source, empaquetez votre code dans un fichier .zip ou similaire, ou utilisez une reproduction de projet IDE. Pour plus d’informations, consultez [Autres reproductions](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Pour prétraiter un fichier de code source

1. Capturez les arguments de ligne de commande utilisés pour générer votre reproduction, comme décrit dans [Pour signaler le contenu de la ligne de commande](#to-report-the-contents-of-the-command-line).

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet.

1. Accédez au répertoire qui contient votre projet de reproduction.

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *filename.cpp*. Pour *arguments*, utilisez la liste d’arguments que vous avez capturée ci-dessus. *filename.cpp* est le nom de votre fichier source de reproduction. Cette commande réplique la ligne de commande que vous avez utilisée pour la reproduction, mais arrête la compilation après le passage du préprocesseur. Elle écrit ensuite le code source prétraité dans *filename*.i.

Si vous prétraitez un fichier de code source C++/CX ou utilisez la fonctionnalité Modules C++, vous devez effectuer des étapes supplémentaires. Pour plus d’informations, consultez les sections ci-dessous.

Une fois que vous avez généré le fichier prétraité, il est judicieux de vérifier que le problème se reproduit lorsque vous compilez le fichier prétraité.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Pour vérifier que le fichier prétraité reproduit toujours l’erreur

1. Dans la fenêtre de console d’invite de commandes pour développeurs, entrez la commande **cl** *arguments* **/TP** *filename.i* pour indiquer à cl.exe de compiler le fichier prétraité comme un fichier source C++. Les *arguments* sont les mêmes arguments que ceux capturés ci-dessus, mais avec les arguments **/D** et **/I** supprimés. C’est parce qu’ils ont déjà été inclus dans le fichier prétraité. *filename.i* est le nom de votre fichier prétraité.

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

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *filename.cpp*. Les *arguments* sont les arguments capturés ci-dessus et *filename.cpp* est le nom du fichier source qui utilise le module.

1. Passez au répertoire contenant le projet de reproduction qui a généré l’interface du module (sortie .ifc).

1. Capturez les arguments de ligne de commande utilisés pour générer votre interface de module.

1. Dans la fenêtre de console de l’invite de commandes développeur, entrez la commande **cl /P** *arguments* *modulename.ixx*. Les *arguments* sont les arguments capturés ci-dessus et *modulename.ixx* est le nom du fichier qui crée l’interface du module.

Une fois que vous avez généré les fichiers prétraités, il est judicieux de vérifier que le problème se reproduit toujours avec le fichier prétraité.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Pour vérifier que le fichier prétraité reproduit toujours l’erreur

1. Dans la fenêtre de console développeur, repassez au répertoire contenant votre projet de reproduction.

1. Entrez la commande **cl** *arguments* **/TP** *filename*.i, comme indiqué ci-dessus, pour compiler le fichier prétraité comme s’il s’agissait d’un fichier source C++.

1. Confirmez que le problème est toujours reproduit par le fichier prétraité.

Enfin, attachez à votre rapport les fichiers de reproduction prétraités (*filename*.i et *modulename*.i), ainsi que la sortie .ifc.

### <a name="link-repros"></a>Reproductions de liens

Une *reproduction de lien* est le contenu généré par l’éditeur de liens d’un répertoire, spécifié par la variable d’environnement **Link @ no__t-2repro** ou en tant qu’argument de l’option de l’éditeur de liens [/LINKREPRO](../build/reference/linkrepro.md) . Il contient des artefacts de build qui illustrent collectivement un problème qui se produit au moment de la liaison. Les exemples incluent un blocage de serveur principal impliquant la génération de code durant l’édition de liens (LTCG) ou un blocage de l’éditeur de liens. Ces artefacts de build sont ceux qui sont nécessaires comme entrée de l’éditeur de liens pour que le problème puisse être reproduit. Une reproduction de lien peut être facilement créée à l’aide de cette variable d’environnement. Elle active la fonctionnalité de génération de reproduction intégrée de l’éditeur de liens.

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>Pour générer une reproduction de lien à l’aide de la variable d’environnement LINK_REPRO

1. Capturez les arguments de ligne de commande utilisés pour générer votre reproduction, comme décrit dans [Pour signaler le contenu de la ligne de commande](#to-report-the-contents-of-the-command-line).

1. Ouvrez l’**invite de commandes développeur** qui correspond à l’architecture de configuration et à la version de Visual Studio utilisées pour générer votre projet.

1. Dans la fenêtre de console de l’invite de commandes développeur, accédez au répertoire qui contient votre projet de reproduction.

1. Entrez **mkdir linkrepro** pour créer un répertoire nommé *linkrepro* pour la reproduction de lien. Vous pouvez utiliser un autre nom pour capturer une autre reproduction de lien.

1. Entrez la commande **set link\_repro=linkrepro** pour définir la variable d’environnement **link\_repro** sur le répertoire que vous avez créé. Si votre Build est exécutée à partir d’un autre répertoire, comme c’est souvent le cas pour des projets plus complexes, définissez plutôt **Link @ no__t-1repro** sur le chemin d’accès complet à votre répertoire de reproduction de lien.

1. Pour générer le projet de reproduction dans Visual Studio, dans la fenêtre de la console de l’invite de commandes développeur, entrez la commande **devenv**. Cela garantit que la valeur de la variable d’environnement **link\_repro** est visible dans Visual Studio. Pour générer le projet sur la ligne de commande, utilisez les arguments de ligne de commande capturés au-dessus pour dupliquer la build de reproduction.

1. Générez votre projet de reproduction et confirmez que le problème attendu s’est produit.

1. Fermez Visual Studio si vous l’avez utilisé pour effectuer la build.

1. Dans la fenêtre de la console de l’invite de commandes développeur, entrez la commande **set link\_repro=** pour effacer la variable d’environnement **link\_repro**.

Enfin, empaquetez la reproduction en compressant l’intégralité du répertoire linkrepro dans un fichier. zip ou similaire, et joignez-le à votre rapport.

L’option de l’éditeur de liens **/LINKREPRO** a le même effet que la variable d’environnement **Link @ no__t-2repro** . Vous pouvez utiliser l’option [/LINKREPROTARGET](../build/reference/linkreprotarget.md) pour spécifier le nom du filtre pour la reproduction de lien générée. Pour utiliser **/LINKREPROTARGET**, vous devez également spécifier l’option **/out** de l’éditeur de liens.

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>Pour générer une reproduction de lien à l’aide de l’option/LINKREPRO

1. Créez un répertoire pour contenir la reproduction de lien. Nous allons faire référence au chemin d’accès complet au répertoire que vous créez en tant que _chemin d’accès au répertoire_. Utilisez des guillemets doubles autour du chemin d’accès s’il contient des espaces.

1. Ajoutez la commande **/LINKREPRO :** _Directory-Path_ à la ligne de commande de l’éditeur de liens. Dans Visual Studio, ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Sélectionnez les **Propriétés de Configuration** > **éditeur de liens**@no__t page de propriétés ligne de**commande** -3. Ensuite, entrez l’option **/LINKREPRO :** _Directory-Path_ dans la zone **options supplémentaires** . Choisissez **OK** pour enregistrer vos modifications.

1. Générez votre projet de reproduction et confirmez que le problème attendu s’est produit.

Enfin, empaquetez la reproduction en compressant l’intégralité du répertoire de reproduction du lien de _chemin d’accès au répertoire_ dans un fichier. zip ou similaire, et joignez-le à votre rapport.

### <a name="other-repros"></a>Autres reproductions

Si vous ne pouvez pas réduire le problème à un fichier source unique ou à une reproduction prétraitée et que le problème ne nécessite pas de reproduction de lien, nous pouvons examiner un projet IDE. Tous les conseils sur la création d’une bonne reproduction s’appliquent toujours : Le code doit être minimaliste et autonome. Le problème doit se produire dans nos outils les plus récents et, le cas échéant, ne doit pas se produire dans d’autres compilateurs.

Créez votre reproduction comme un projet IDE minimal, puis empaquetez-la en compressant l’intégralité de la structure de répertoire dans un fichier .zip ou similaire et attachez-la à votre rapport.

## <a name="ways-to-send-your-report"></a>Modes d’envoi de votre rapport

Pour nous faire parvenir votre rapport, plusieurs options s’offrent à vous. Vous pouvez utiliser les pages intégrées de Visual Studio [Outil Signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ou [Communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/). Vous trouverez aussi un bouton **Commentaires sur les produits** en bas de cette page. Le choix diffère selon que vous souhaitiez ou non utiliser les outils intégrés dans l’IDE pour prendre des captures d’écran et organiser votre rapport. Si vous préférez ne pas le faire, vous pouvez utiliser directement le site web de la communauté de développeurs.

> [!NOTE]
> Quelle que soit la manière dont vous envoyez votre rapport, Microsoft respecte votre vie privée. Microsoft s’engage à respecter toutes les lois et réglementations relatives à la confidentialité des données. Pour plus d’informations sur la façon dont nous utilisons les données que vous nous envoyez, consultez la [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Utiliser l’outil Signaler un problème

L’outil **Signaler un problème** dans Visual Studio est un moyen pour les utilisateurs de Visual Studio des problèmes en quelques clics. Il affiche un formulaire simple pour envoyer des informations détaillées sur le problème que vous avez rencontré. Vous pouvez ensuite envoyer votre rapport sans jamais quitter l’IDE.

L’outil **Signaler un problème** est facile et pratique à utiliser à partir de l’IDE. Vous pouvez y accéder à partir de la barre de titre en choisissant l’icône **Envoyer des commentaires** située à côté de la zone de recherche **Lancement rapide**. Ou vous pouvez le trouver dans la barre de menus dans **Aide** > **Envoyer des commentaires** > **Signaler un problème**.

Quand vous choisissez de signaler un problème, cherchez d’abord s’il en existe de similaires dans la Communauté des développeurs. Si votre problème a déjà été signalé, votez pour le rapport et ajoutez des commentaires qui ajoutent de nouveaux éléments. Si vous ne voyez pas de problème similaire, choisissez le bouton **Signaler un nouveau problème** dans le bas de la boîte de dialogue Commentaires sur Visual Studio et suivez les étapes pour signaler votre problème.

### <a name="use-the-visual-studio-developer-community-pages"></a>Utiliser les pages de la Communauté des développeurs Visual Studio

Les pages de la Communauté des développeurs Visual Studio sont un autre moyen pratique de signaler des problèmes et de trouver des solutions pour Visual Studio, le compilateur C++, les outils et les bibliothèques. Il existe des pages de Communauté des développeurs propres à [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html), [Visual Studio pour Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [Azure DevOps Services](https://developercommunity.visualstudio.com/spaces/21/index.html) et [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html).

Sous les onglets de la communauté, près du haut de chaque page, vous trouverez une zone de recherche. Vous pouvez l’utiliser pour rechercher des publications qui signalent des problèmes semblables au vôtre. Il est possible qu’une solution ou d’autres informations utiles relatives à votre problème soient déjà disponibles. Si quelqu’un a signalé le même problème, votez pour cette rubrique et ajoutez-y des commentaires au lieu de signaler un nouveau problème. Pour commenter, voter pour ou signaler un nouveau problème, vous pourriez avoir à vous connecter à votre compte Visual Studio. La première fois que vous vous connectez, vous devrez accepter de donner à l’application Communauté des développeurs l’accès à votre profil.

Pour les problèmes relatifs au compilateur, à l’éditeur de liens, et aux autres outils et bibliothèques C++, utilisez la page [C++](https://developercommunity.visualstudio.com/spaces/62/index.html). Si vous recherchez votre problème et qu’il n’a pas encore été signalé, choisissez le bouton **Signaler un problème** en regard de la zone de recherche. Vous pouvez inclure le code et la ligne de commande de votre reproduction, des captures d’écran, des liens vers des discussions qui s’y rapportent, et toute autre information que vous pensez pertinente et utile.

> [!TIP]
> Pour d’autres types de problèmes que vous pouvez rencontrer dans Visual Studio et qui ne sont pas liés à l’ensemble d’outils C++ (par exemple, des problèmes d’interface utilisateur, une fonctionnalité de l’IDE rompue ou des plantages généraux), utilisez l’outil **Signaler un problème** dans l’IDE. Il s’agit du meilleur choix, en raison de ses fonctionnalités de capture d’écran et de sa capacité à enregistrer des actions d’interface utilisateur qui mènent à un problème que vous avez rencontré. Ces types d’erreurs peuvent également être recherchés sur le site [Communauté des développeurs](https://developercommunity.visualstudio.com/). Pour plus d’informations, consultez [Guide pratique pour signaler un problème avec Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Rapports et confidentialité

**Toutes les informations contenues dans les rapports, ainsi que les commentaires et les réponses qui peuvent y figurer, sont visibles publiquement par défaut**. Il s’agit en général d’un avantage dans la mesure où toute la communauté a accès aux problèmes, solutions et solutions de contournement identifiés par d’autres utilisateurs. Toutefois, si le fait de présenter au public vos données ou votre identité vous préoccupe, que ce soit pour des raisons de confidentialité ou de propriété intellectuelle, vous avez plusieurs options.

Si vous ne souhaitez pas révéler votre identité, [créez un compte Microsoft](https://signup.live.com/) qui ne divulgue aucun détail vous concernant. Utilisez ce compte pour créer votre rapport.

**Ne placez pas d’informations privées dans le titre ou le contenu du rapport initial, qui est public.** Au lieu de cela, supposons que vous envoyez des détails en privé dans un commentaire séparé. Pour garantir que votre rapport s’adresse aux bonnes personnes, ajoutez **cppcompiler** dans la liste des rubriques de votre rapport de problème. Une fois le rapport de problème créé, vous pouvez désormais spécifier qui peut voir vos réponses et pièces jointes.

#### <a name="to-create-a-problem-report-for-private-information"></a>Pour créer un rapport de problème avec des informations privées

1. Dans le rapport que vous avez créé, choisissez **Ajouter un commentaire** pour créer une description privée du problème.

1. Dans l’éditeur de réponse, utilisez le contrôle de liste déroulante sous **Envoyer** et **Annuler** pour spécifier l’audience de votre réponse. Seules les personnes que vous spécifiez peuvent voir ces réponses privées et les images, liens ou extraits de code inclus. Choisissez **Viewable by moderators and the original poster** (Consultable par les modérateurs et l’auteur à l’origine de la publication) pour limiter la visibilité aux employés de Microsoft et à vous-même.

1. Ajoutez la description et les autres informations, images et pièces jointes de fichier nécessaires à la reproduction. Choisissez le bouton **Envoyer** pour envoyer ces informations en privé.

   Les fichiers joints sont limités à 10 et ils ne doivent pas dépasser 2 Go. Pour les chargements plus volumineux, demandez une URL de chargement dans votre commentaire privé.

Toutes les réponses figurant sous ce commentaire ont la même visibilité restreinte. Cela est vrai même si le contrôle de liste déroulante sur les réponses n’affiche pas correctement l’état de visibilité.

Pour garantir votre confidentialité et maintenir vos informations sensibles hors de la vue publique, faites preuve de prudence. Limitez vos interactions avec Microsoft aux réponses sous le commentaire restreint. Le fait de répondre à d’autres commentaires peut vous amener à divulguer accidentellement des informations sensibles.

## <a name="how-to-report-a-c-documentation-issue"></a>Comment signaler un problème dans la documentation C++

Nous utilisons les problèmes GitHub pour faire le suivi des problèmes liés à notre documentation. Vous pouvez désormais créer des problèmes GitHub directement à partir d’une page de contenu, ce qui permet d’améliorer considérablement l’interaction avec les rédacteurs et les équipes produit. Si vous constatez un problème lié à un document, un exemple de code incorrect, une explication confuse, une omission critique ou simplement une faute d’orthographe, vous pouvez facilement nous en faire part. Faites défiler la page jusqu’en bas et sélectionnez **Se connecter pour fournir des commentaires sur la documentation**. Vous devez créer un compte GitHub si vous n’en avez pas encore un. Lorsque vous avez un compte GitHub, vous pouvez voir tous les problèmes de notre documentation et leur état. Vous recevez également des notifications lorsque des modifications sont apportées pour le problème signalé. Pour plus d’informations, consultez [A New Feedback System Is Coming to docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Vous créez un problème de documentation sur GitHub lorsque vous utilisez le bouton de commentaires sur la documentation. Le problème est automatiquement renseigné avec les informations de la page depuis laquelle vous créez le problème. C’est ainsi que nous savons où le problème se trouve, aussi ne modifiez pas ces informations. Ajoutez simplement les détails relatifs au problème rencontré et, si vous le souhaitez, une suggestion de correction. [Nos documents C++ sont open source](https://github.com/MicrosoftDocs/cpp-docs/), ainsi si vous souhaitez envoyer un correctif vous-même, vous pouvez le faire. Pour plus d’informations sur la façon dont vous pouvez contribuer à notre documentation, consultez notre [guide consacré aux contributions](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) sur GitHub.
