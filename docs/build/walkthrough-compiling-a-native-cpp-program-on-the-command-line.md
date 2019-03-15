---
title: 'Procédure pas à pas : Compilation d’un programme C++ natif sur la ligne de commande'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: d7b5bc88966f7edbb7179c36398b1dd95afb971f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814343"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Procédure pas à pas : Compilation d’un programme C++ natif sur la ligne de commande

Visual C++ inclut un compilateur C++ en ligne de commande que vous pouvez utiliser pour créer toutes sortes d’applications de console de base pour les applications de plateforme Windows universelle, les applications de bureau, les pilotes de périphériques et les composants .NET.

Dans cette procédure pas à pas, vous allez créer une base « Hello, World »-du style programme C++ à l’aide d’un texte de l’éditeur et puis le compiler sur la ligne de commande. Si vous souhaitez essayer de l’IDE de Visual Studio au lieu d’utiliser la ligne de commande, consultez [procédure pas à pas : Utilisation de projets et Solutions (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [à l’aide de l’IDE Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

Dans cette procédure pas à pas, vous pouvez utiliser votre propre programme Visual C++ au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code Visual C++ provenant d'un autre article d'aide.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio et la propriété facultative **développement Desktop en C++** charge de travail, ou les outils de ligne de commande de génération pour Visual Studio.

Visual Studio est un environnement puissant de développement intégré (IDE) qui prend en charge d’un éditeur complet, les gestionnaires de ressources, les débogueurs et les compilateurs pour plusieurs langages et plateformes. Pour plus d’informations sur la façon de télécharger et installer Visual Studio, y compris l’édition de Visual Studio Community gratuite et pour inclure la prise en charge pour le développement C/C++, consultez [prise en charge de l’installation de C++ dans Visual Studio](vscpp-step-0-installation.md).

Les outils de génération pour Visual Studio installe uniquement les compilateurs de ligne de commande, les outils et les bibliothèques que nécessaires pour générer des programmes C et C++. Il est idéal pour les laboratoires de conception ou de la classe teste et installe relativement rapidement. Pour installer uniquement les outils de ligne de commande, téléchargez [Build Tools pour Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Avant de pouvoir créer un programme C ou C++ sur la ligne de commande, vous devez vérifier que les outils sont installés, et que vous pouvez y accéder à partir de la ligne de commande. Visual C++ a des exigences complexes pour l’environnement de ligne de commande Rechercher les outils, les en-têtes et les bibliothèques qu’elle utilise. **Vous ne pouvez pas utiliser Visual C++ dans une fenêtre d’invite de commandes standard** sans effectuer certaines tâches de préparation. Heureusement, Visual C++ installe des raccourcis pour lancer une invite de commandes développeur qui a l’environnement configuré pour les builds de ligne de commande. Malheureusement, les noms des raccourcis d’invite de commandes de développeur et où ils se trouvent sont différents dans presque toutes les versions de Visual C++ et sur différentes versions de Windows. Votre première tâche de la procédure pas à pas consiste à trouver celui qui convient à utiliser.

> [!NOTE]
> Un raccourci d’invite de commandes développeur définit automatiquement les chemins d’accès corrects pour le compilateur et les outils et pour des en-têtes obligatoires et des bibliothèques. Vous devez définir ces valeurs d’environnement vous-même si vous utilisez une expression régulière **invite de commandes** fenêtre. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md). Nous vous recommandons de qu'utiliser un raccourci d’invite de commandes développeur au lieu de créer votre propre.

### <a name="open-a-developer-command-prompt"></a>Ouvrez une invite de commandes développeur

1. Si vous avez installé Visual Studio 2017 sur Windows 10, ouvrez le menu Démarrer et choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le **Visual Studio 2017** dossier (et pas l’application de Visual Studio 2017). Choisissez **invite de commandes développeur pour VS 2017** pour ouvrir la fenêtre d’invite de commandes.

   Si vous avez installé Microsoft Visual C++ Build Tools 2015 sur Windows 10, ouvrez le **Démarrer** menu et choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le **Visual C++ Build Tools** dossier. Choisissez **invite de commandes outils natifs Visual C++ 2015 x86** pour ouvrir la fenêtre d’invite de commandes.

   Si vous utilisez une autre version de Visual Studio ou exécutez une version différente de Windows, recherchez dans votre menu Démarrer ou page pour un dossier d’outils de Visual Studio qui contient un raccourci d’invite de commandes développeur de démarrage. Vous pouvez également utiliser la fonction de recherche de Windows pour rechercher « invite de commande développeur » et choisissez celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

1. Ensuite, vérifiez que l’invite de commandes développeur Visual C++ est correctement configuré. Dans la fenêtre d’invite de commandes, entrez `cl` et vérifiez que la sortie ressemble à ceci :

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Il peut exister des différences dans le répertoire actif ou les numéros de version, selon la version de Visual C++ et les mises à jour installées. Si la sortie ci-dessus est similaire à celle que vous voyez, vous êtes prêt à générer des programmes C ou C++ sur la ligne de commande.

   > [!NOTE]
   > Si vous obtenez une erreur, tels que « le « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104 lorsque vous exécutez le **cl** commande, soit vous n’utilisez pas d’une invite de commandes développeur, ou a un problème avec votre installation de Visual C++. Vous devez corriger ce problème avant de continuer.

   Si vous ne trouvez pas le développeur raccourci d’invite de commande, ou si vous obtenez un message d’erreur lorsque vous entrez `cl`, puis votre installation de Visual C++ peut rencontrer un problème. Essayez de réinstaller le composant Visual C++ dans Visual Studio, ou réinstallez Microsoft Visual C++ Build Tools. Ne passez à la section suivante jusqu'à ce que cela fonctionne. Pour plus d’informations sur l’installation et la résolution des problèmes de Visual C++, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Selon la version de Windows sur l’ordinateur et la configuration de sécurité du système, vous devrez peut-être avec le bouton droit pour ouvrir le menu contextuel pour le raccourci d’invite de commandes développeur, puis choisissez **exécuter en tant qu’administrateur** à avec succès, générez et exécutez le programme que vous créez en suivant cette procédure pas à pas.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Créer un fichier source Visual C++ et le compiler sur la ligne de commande

1. Dans la fenêtre d’invite de commandes développeur, entrez `md c:\hello` pour créer un répertoire, puis entrez `cd c:\hello` pour accéder à ce répertoire. Ce répertoire est où votre fichier source et le programme compilé sont créés dans.

1. Entrez `notepad hello.cpp` dans la fenêtre d’invite de commandes.

   Choisissez **Oui** lorsque le bloc-notes vous invite à créer un fichier. Cette étape ouvre une fenêtre du bloc-notes vide, prête à entrer votre code dans un fichier nommé hello.cpp.

1. Dans le bloc-notes, entrez les lignes de code suivantes :

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ce code est un programme simple qui écrit une seule ligne de texte sur l’écran et puis quitter. Pour minimiser les risques d’erreurs, copiez le code et collez-le dans le Bloc-notes.

1. Enregistrez votre travail. Dans le Bloc-notes, dans le menu **Fichier** , choisissez **Enregistrer**.

   Félicitations, vous avez créé un fichier source Visual C++, hello.cpp, qui est prêt pour la compilation.

1. Revenez à la fenêtre d’invite de commandes développeur. Entrez `dir` à l’invite de commande pour répertorier le contenu du répertoire c:\hello. Vous devez voir le hello.cpp du fichier source dans la liste des répertoires, qui ressemble à quelque chose comme :

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

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, hello.cpp, assurez-vous que vous avez modifié dans le répertoire c:\hello que vous avez créé et dans le bloc-notes, vérifiez que vous avez enregistré votre fichier source dans ce répertoire. Assurez-vous également que vous avez enregistré le code source avec une extension de nom de fichier .cpp, pas une extension .txt.

1. À l’invite de commandes développeur, entrez `cl /EHsc hello.cpp` pour compiler votre programme.

   Le compilateur cl.exe génère un fichier .obj qui contient le code compilé, puis exécute l’éditeur de liens pour créer un programme exécutable nommé hello.exe. Ce nom apparaît dans les lignes des informations de sortie affichées par le compilateur. La sortie du compilateur doit ressembler à :

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
   > Si vous obtenez une erreur, tels que « le « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104, votre invite de commandes développeur n’est pas configuré correctement. Pour plus d’informations sur la façon de résoudre ce problème, revenez à la **ouvrir une invite de commandes développeur** section.

   > [!NOTE]
   > Si vous obtenez une erreur de l’éditeur de liens ou du compilateur différents ou un avertissement, passez en revue votre code source pour corriger les erreurs éventuelles, puis enregistrez-le et réexécutez le compilateur. Pour plus d’informations sur les erreurs spécifiques, utilisez la zone de recherche sur cette page MSDN pour rechercher le numéro d’erreur.

1. Pour exécuter le programme hello.exe, à l’invite de commandes, entrez `hello`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   Hello, world, from Visual C++!
   ```

   Félicitations, vous avez compilé et exécuter un programme C++ en utilisant les outils de ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple « Hello, World » est environ simple comme un programme C++ peut obtenir. Programmes réels ont des fichiers d’en-tête et d’autres fichiers sources, liaison dans bibliothèques, et effectuer un travail utile.

Vous pouvez utiliser les étapes décrites dans cette procédure pas à pas pour générer votre propre code C++ au lieu de taper l’exemple de code indiqué. Vous pouvez créer également de nombreux programmes d’exemple de code C++ que vous trouvez ailleurs. Vous pouvez placer votre code source et créez vos applications dans n’importe quel répertoire accessible en écriture. Par défaut, l’IDE Visual Studio crée des projets dans votre dossier Documents, dans un sous-dossier de projets d’un dossier de Visual Studio nommé pour votre version de Visual Studio.

Pour compiler un programme qui a des fichiers de code source supplémentaires, entrez-les sur la ligne de commande, telles que :

`cl /EHsc file1.cpp file2.cpp file3.cpp`

L’option de ligne de commande `/EHsc` indique au compilateur d’activer la gestion des exceptions C++. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](reference/eh-exception-handling-model.md).

Lorsque vous fournissez des fichiers sources supplémentaires, le compilateur utilise le premier fichier d’entrée pour créer le nom du programme. Dans ce cas, il génère un programme appelé file1.exe. Pour modifier le nom à program1.exe, ajoutez un [/out](reference/out-output-file-name.md) option de l’éditeur de liens :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Et pour intercepter les erreurs de programmation plus automatiquement, nous vous recommandons de vous compilez en utilisant soit le [w3](reference/compiler-option-warning-level.md) ou [/W4](reference/compiler-option-warning-level.md) choix du niveau d’avertissement :

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Le compilateur, cl.exe, dispose de nombreuses options plus, vous pouvez appliquer pour générer, optimiser, déboguer et analyser votre code. Pour une liste rapide, entrez `cl /?` à l’invite de commandes développeur. Vous pouvez également compiler et lier séparément s’appliquent aux options de l’éditeur de liens dans les scénarios de génération plus complexes. Pour plus d’informations sur les options de l’éditeur de liens et du compilateur et l’utilisation, consultez [référence à la génération C/C++](reference/c-cpp-building-reference.md).

Vous pouvez utiliser NMAKE et makefiles ou MSBuild et les fichiers projet pour configurer et générer des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, consultez [Référence NMAKE](reference/nmake-reference.md) et [MSBuild](msbuild-visual-cpp.md).

Les langages C et C++ sont similaires, mais pas dans le même. Le compilateur MSVC utilise une règle simple pour déterminer la langue à utiliser lors de la compilation de votre code. Par défaut, le compilateur MSVC traite tous les fichiers se terminant par .c comme code source C et tous les fichiers se terminant par .cpp comme code source C++. Pour forcer le compilateur doit traiter tous les fichiers en tant que C++ non dépendante sur l’extension de nom de fichier, utilisez le [TP](reference/tc-tp-tc-tp-specify-source-file-type.md) option du compilateur.

Le compilateur MSVC inclut une bibliothèque de Runtime C (CRT) qui est compatible avec la norme ISO C99, mais pas strictement conformes. Dans la plupart des cas, code portable compilera et s’exécuter comme prévu. Visual C++ ne prend en charge certaines modifications CRT dans ISO C11. Certaines fonctions de bibliothèque et les noms de fonction POSIX sont déconseillées par le compilateur MSVC. Les fonctions sont prises en charge, mais les noms par défaut ont changé. Pour plus d’informations, consultez [des fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et des systèmes de génération](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
