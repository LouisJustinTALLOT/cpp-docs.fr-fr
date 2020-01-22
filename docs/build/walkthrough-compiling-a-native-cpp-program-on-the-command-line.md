---
title: "Procédure pas à pas : compilation d'un programme C++ natif sur la ligne de commande"
description: Utilisez le compilateur C++ Microsoft à partir d’une invite de commandes.
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: d002fd4c4edc99775e62023dda7998fba2c6a44f
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518169"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++ natif sur la ligne de commande

Visual Studio inclut un compilateur de ligne C++ de commande que vous pouvez utiliser pour créer tout depuis les applications console de base vers des applications plateforme Windows universelle, des applications de bureau, des pilotes de périphériques et des composants .net.

Dans cette procédure pas à pas, vous créez un programme de type C++ « Hello, World » de base à l’aide d’un éditeur de texte, puis vous le compilez sur la ligne de commande. Si vous souhaitez essayer l’IDE Visual Studio au lieu d’utiliser la ligne de commande, consultez [procédure pas à pas : utilisation de projetsC++et de solutions ()](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [utilisation de C++ l’IDE de Visual Studio pour le développement bureautique](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

Dans cette procédure pas à pas, vous pouvez utiliser votre propre programme Visual C++ au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code Visual C++ provenant d'un autre article d'aide.

## <a name="prerequisites"></a>Prerequisites

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio et le **développement Desktop C++ facultatif avec** une charge de travail, ou les outils de génération en ligne de commande pour Visual Studio.

Visual Studio est un puissant environnement de développement intégré (IDE) qui prend en charge un éditeur complet, les gestionnaires de ressources, les débogueurs et les compilateurs pour de nombreux langages et plateformes. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio, y compris la version gratuite de Visual Studio Community Edition, etC++ pour inclure la prise en charge de C/Development, consultez [installation C++ de la prise en charge dans Visual Studio](vscpp-step-0-installation.md).

Les outils de génération pour Visual Studio installent uniquement les compilateurs de ligne de commande, les outils et les bibliothèques dont vous avez besoin C++ pour générer des C et des programmes. Il est parfait pour les ateliers de génération ou les exercices de la classe et s’installe relativement rapidement. Pour installer uniquement les outils en ligne de commande, recherchez outils de génération pour Visual Studio dans la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) .

Avant de pouvoir créer un C ou C++ un programme sur la ligne de commande, vous devez vérifier que les outils sont installés et que vous pouvez y accéder à partir de la ligne de commande. Visual C++ requiert des exigences complexes pour que l’environnement de ligne de commande recherche les outils, les en-têtes et les bibliothèques qu’il utilise. **Vous ne pouvez pas C++ utiliser Visual dans une fenêtre d’invite de commandes ordinaire** sans effectuer de préparation. Heureusement, Visual C++ installe des raccourcis vous permettant de lancer une invite de commandes développeur pour laquelle l’environnement est configuré pour les builds de ligne de commande. Malheureusement, les noms des raccourcis de l’invite de commandes développeur et de leur emplacement sont différents dans presque toutes les versions C++ de Visual et sur les différentes versions de Windows. Votre première tâche de procédure pas à pas consiste à trouver le bon à utiliser.

> [!NOTE]
> Un raccourci d’invite de commandes développeur définit automatiquement les chemins d’accès corrects pour le compilateur et les outils, ainsi que pour les en-têtes et les bibliothèques nécessaires. Vous devez définir ces valeurs d’environnement vous-même si vous utilisez une fenêtre d' **invite de commandes** normale. Pour plus d’informations, consultez [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md). Nous vous recommandons d’utiliser un raccourci d’invite de commandes développeur au lieu de créer le vôtre.

### <a name="open-a-developer-command-prompt"></a>Ouvrir une invite de commandes développeur

1. Si vous avez installé Visual Studio 2017 ou version ultérieure sur Windows 10, ouvrez le menu Démarrer et choisissez **toutes les applications**. Faites défiler vers le dessous et ouvrez le dossier **Visual Studio** (et non l’application Visual Studio). Choisissez **invite de commandes développeur pour Visual Studio** pour ouvrir la fenêtre d’invite de commandes.

   Si vous avez installé Microsoft Visual C++ Build Tools 2015 sur Windows 10, ouvrez le menu **Démarrer** et choisissez **toutes les applications**. Faites défiler vers le dessous et ouvrez le dossier  **C++ Visual Build Tools** . Choisissez **Visual C++ 2015 invite de commandes des outils natifs x86** pour ouvrir la fenêtre d’invite de commandes.

   Vous pouvez également utiliser la fonction de recherche Windows pour rechercher « invite de commandes développeur » et en choisir une qui correspond à la version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

1. Ensuite, vérifiez que l’invite C++ de commandes Visual Developer est correctement configurée. Dans la fenêtre d’invite de commandes, entrez `cl` et vérifiez que la sortie ressemble à ceci :

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Il peut y avoir des différences au niveau du répertoire actuel ou des numéros de version, en fonction C++ de la version de Visual et des mises à jour installées. Si la sortie ci-dessus est similaire à ce que vous voyez, vous êtes prêt à générer C++ C ou des programmes sur la ligne de commande.

   > [!NOTE]
   > Si vous recevez une erreur telle que « Cl » n’est pas reconnu en tant que commande interne ou externe, programme exécutable ou fichier de commandes, «erreur C1034 ou LNK1104 d’erreur lors de l’exécution de la commande **CL** , vous n’utilisez pas une invite de commandes développeur ou un problème avec votre installation de C++Visual. Vous devez corriger ce problème avant de pouvoir continuer.

   Si vous ne trouvez pas le raccourci de l’invite de commandes développeur ou si vous recevez un message d’erreur lorsque vous entrez `cl`C++ , votre installation visuelle peut avoir un problème. Essayez de réinstaller le composant visuel C++ dans Visual Studio, ou réinstallez les outils de C++ génération Microsoft Visual. N’passez pas à la section suivante jusqu’à ce que cela fonctionne. Pour plus d’informations sur l’installation et C++la résolution des problèmes visuels, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Selon la version de Windows sur l’ordinateur et la configuration de la sécurité du système, vous devrez peut-être cliquer avec le bouton droit pour ouvrir le menu contextuel du raccourci d’invite de commandes développeur, puis choisir **exécuter en tant qu’administrateur** pour générer et exécuter correctement le programme que vous créez en suivant cette procédure pas à pas.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Créer un fichier C++ source visuel et le compiler sur la ligne de commande

1. Dans la fenêtre d’invite de commandes développeur, entrez `md c:\hello` pour créer un répertoire, puis entrez `cd c:\hello` pour accéder à ce répertoire. Ce répertoire est l’emplacement où votre fichier source et le programme compilé sont créés.

1. Entrez `notepad hello.cpp` dans la fenêtre d’invite de commandes.

   Choisissez **Oui** lorsque le bloc-notes vous invite à créer un fichier. Cette étape ouvre une fenêtre de bloc-notes vide, qui vous permet d’entrer votre code dans un fichier nommé hello. cpp.

1. Dans le bloc-notes, entrez les lignes de code suivantes :

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ce code est un programme simple qui écrit une ligne de texte à l’écran, puis s’arrête. Pour minimiser les risques d’erreurs, copiez le code et collez-le dans le Bloc-notes.

1. Enregistrez votre travail. Dans le Bloc-notes, dans le menu **Fichier** , choisissez **Enregistrer**.

   Félicitations, vous avez créé un C++ fichier source, Hello. cpp, qui est prêt pour la compilation.

1. Revenez à la fenêtre d’invite de commandes développeur. Entrez `dir` à l’invite de commandes pour répertorier le contenu du répertoire c:\hello. Vous devez voir le fichier source Hello. cpp dans la liste des répertoires, qui ressemble à ceci :

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, Bonjour. cpp, assurez-vous que vous avez remplacé le répertoire c:\hello que vous avez créé, et dans le bloc-notes, vérifiez que vous avez enregistré votre fichier source dans ce répertoire. Assurez-vous également que vous avez enregistré le code source avec une extension de nom de fichier. cpp, et non une extension. txt.

1. À l’invite de commandes développeur, entrez `cl /EHsc hello.cpp` pour compiler votre programme.

   Le compilateur cl.exe génère un fichier .obj qui contient le code compilé, puis exécute l’éditeur de liens pour créer un programme exécutable nommé hello.exe. Ce nom apparaît dans les lignes des informations de sortie affichées par le compilateur. La sortie du compilateur doit ressembler à ceci :

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Si vous recevez une erreur telle que « Cl » n’est pas reconnu en tant que commande interne ou externe, programme exécutable ou fichier de commandes, «erreur C1034 ou LNK1104 d’erreur, l’invite de commandes développeur n’est pas configurée correctement. Pour plus d’informations sur la résolution de ce problème, revenez à la section **ouvrir une invite de commandes développeur** .

   > [!NOTE]
   > Si vous recevez une erreur ou un avertissement du compilateur ou de l’éditeur de liens différent, examinez votre code source pour corriger les erreurs éventuelles, puis enregistrez-le et réexécutez le compilateur. Pour plus d’informations sur des erreurs spécifiques, utilisez la zone de recherche sur cette page MSDN pour rechercher le numéro d’erreur.

1. Pour exécuter le programme hello.exe, à l’invite de commandes, entrez `hello`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   Hello, world, from Visual C++!
   ```

   Félicitations, vous avez compilé et exécuté un C++ programme à l’aide des outils en ligne de commande.

## <a name="next-steps"></a>Étapes suivantes :

Cet exemple « Hello, World » est le plus simple qu’un C++ programme peut obtenir. Les programmes réels contiennent des fichiers d’en-tête et d’autres fichiers sources, des liens dans les bibliothèques et un travail utile.

Vous pouvez utiliser les étapes de cette procédure pas à pas pour C++ générer votre propre code au lieu de taper l’exemple de code indiqué. Vous pouvez également générer de C++ nombreux exemples de code que vous trouverez ailleurs. Vous pouvez placer votre code source et générer vos applications dans n’importe quel répertoire accessible en écriture. Par défaut, l’IDE de Visual Studio crée des projets dans le dossier documents, dans un sous-dossier projets d’un dossier Visual Studio nommé pour votre version de Visual Studio.

Pour compiler un programme qui contient des fichiers de code source supplémentaires, entrez-les tous sur la ligne de commande, par exemple :

`cl /EHsc file1.cpp file2.cpp file3.cpp`

L’option de ligne de commande `/EHsc` indique au compilateur d’activer la gestion des exceptions C++. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](reference/eh-exception-handling-model.md).

Lorsque vous fournissez des fichiers sources supplémentaires, le compilateur utilise le premier fichier d’entrée pour créer le nom du programme. Dans ce cas, elle génère un programme nommé fichier1. exe. Pour modifier le nom en Program1. exe, ajoutez une option [/out](reference/out-output-file-name.md) de l’éditeur de liens :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Et pour intercepter automatiquement d’autres erreurs de programmation, nous vous recommandons de compiler à l’aide de l’option de niveau d’avertissement [/W3](reference/compiler-option-warning-level.md) ou [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Le compilateur, cl. exe, offre de nombreuses autres options que vous pouvez appliquer pour générer, optimiser, déboguer et analyser votre code. Pour obtenir une liste rapide, entrez `cl /?` à l’invite de commandes développeur. Vous pouvez également compiler et lier séparément et appliquer des options de l’éditeur de liens dans des scénarios de génération plus complexes. Pour plus d’informations sur les options du compilateur et de l’éditeur de liens et sur son utilisation, consultez [C/C++ Building Reference](reference/c-cpp-building-reference.md).

Vous pouvez utiliser NMAKE et les Makefiles, ou les fichiers projet et MSBuild pour configurer et générer des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, consultez la [Référence NMAKE](reference/nmake-reference.md) et [MSBuild](msbuild-visual-cpp.md).

Le C et C++ les langages sont similaires, mais pas les mêmes. Le compilateur MSVC utilise une règle simple pour déterminer le langage à utiliser lors de la compilation de votre code. Par défaut, le compilateur MSVC traite tous les fichiers qui se terminent par. c en tant que code source C, et tous les fichiers C++ se terminant par. cpp comme code source. Pour forcer le compilateur à traiter tous les fichiers C++ comme non dépendants de l’extension de nom de fichier, utilisez l’option de compilateur [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) .

Le compilateur MSVC comprend une bibliothèque Runtime C (CRT) qui est compatible avec la norme ISO C99, mais qui n’est pas strictement conforme. Dans la plupart des cas, le code portable se compile et s’exécute comme prévu. Visual C++ ne prend pas en charge certaines modifications du CRT dans ISO C11. Certaines fonctions de bibliothèque et certains noms de fonction POSIX sont déconseillés par le compilateur MSVC. Les fonctions sont prises en charge, mais les noms préférés ont changé. Pour plus d’informations, consultez [fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
