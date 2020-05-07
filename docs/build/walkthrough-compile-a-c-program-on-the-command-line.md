---
title: 'Procédure pas à pas : compiler un programme C sur la ligne de commande'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335264"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Procédure pas à pas : compiler un programme C sur la ligne de commande

Visual C++ inclut un compilateur C que vous pouvez utiliser pour créer toutes sortes de programmes, des programmes de console de base aux applications de bureau Windows complètes, aux applications mobiles, etc.

Cette procédure pas à pas montre comment créer un programme de style C de base, « Hello, World », à l’aide d’un éditeur de texte, puis le compiler sur la ligne de commande. Si vous préférez travailler en C++ sur la ligne de commande, consultez [procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si vous souhaitez tester l’IDE de Visual Studio au lieu d’utiliser la ligne de commande, consultez [procédure pas à pas : utilisation de projets et de solutions (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [utilisation de l’IDE Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio et les composants Visual C++ facultatifs, ou les outils de génération pour Visual Studio.

Visual Studio est un environnement de développement intégré puissant qui prend en charge un éditeur complet, les gestionnaires de ressources, les débogueurs et les compilateurs pour de nombreux langages et plateformes. Pour plus d’informations sur ces fonctionnalités et sur le téléchargement et l’installation de Visual Studio, y compris l’édition Visual Studio Community gratuite, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

La version des outils de génération pour Visual Studio de Visual Studio installe uniquement l’ensemble d’outils de ligne de commande, les compilateurs, les outils et les bibliothèques dont vous avez besoin pour générer des programmes C et C++. Il est parfait pour les ateliers de génération ou les exercices de la classe et s’installe relativement rapidement. Pour installer uniquement l’ensemble d’outils de ligne de commande, téléchargez Build Tools pour Visual Studio à partir de la page de [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) et exécutez le programme d’installation. Dans le programme d’installation de Visual Studio, sélectionnez la charge de travail **outils de génération C++** , puis choisissez **installer**.

Avant de pouvoir générer un programme C ou C++ sur la ligne de commande, vous devez vérifier que les outils sont installés et que vous pouvez y accéder à partir de la ligne de commande. Visual C++ a des exigences complexes pour que l’environnement de ligne de commande recherche les outils, les en-têtes et les bibliothèques qu’il utilise. **Vous ne pouvez pas utiliser Visual C++ dans une fenêtre d’invite de commandes simple** sans préparation. Vous avez besoin d’une fenêtre d' *invite de commandes développeur* , qui est une fenêtre d’invite de commandes standard avec toutes les variables d’environnement définies. Heureusement, Visual C++ installe des raccourcis pour lancer des invites de commandes développeur pour lesquelles l’environnement est configuré pour les builds de ligne de commande. Malheureusement, les noms des raccourcis de l’invite de commandes développeur et de leur emplacement sont différents dans presque toutes les versions de Visual C++ et sur différentes versions de Windows. Votre première tâche de procédure pas à pas consiste à trouver le bon raccourci à utiliser.

> [!NOTE]
> Un raccourci d’invite de commandes développeur définit automatiquement les chemins d’accès corrects pour le compilateur et les outils, ainsi que pour les en-têtes et les bibliothèques nécessaires. Certaines de ces valeurs sont différentes pour chaque configuration de Build. Vous devez définir ces valeurs d’environnement vous-même si vous n’utilisez pas l’un des raccourcis. Pour plus d’informations, consultez [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md). Étant donné que l’environnement de génération est complexe, nous vous recommandons vivement d’utiliser un raccourci d’invite de commandes développeur au lieu de créer le vôtre.

Ces instructions varient en fonction de la version de Visual Studio que vous utilisez. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Ouvrir une invite de commandes développeur dans Visual Studio 2019

Si vous avez installé Visual Studio 2019 sur Windows 10, ouvrez le menu Démarrer, puis faites défiler et ouvrez le dossier **Visual studio 2019** (et non l’application visual studio 2019). Choisissez **invite de commandes développeur pour Visual studio 2019** pour ouvrir la fenêtre d’invite de commandes.

Si vous utilisez une autre version de Windows, recherchez dans le menu Démarrer ou la page de démarrage un dossier Visual Studio Tools contenant un raccourci d’invite de commandes développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher « invite de commandes développeur » et en choisir une qui correspond à la version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Ouvrir une invite de commandes développeur dans Visual Studio 2017

Si vous avez installé Visual Studio 2017 sur Windows 10, ouvrez le menu Démarrer, puis faites défiler et ouvrez le dossier **Visual studio 2017** (et non l’application visual studio 2017). Choisissez **invite de commandes développeur pour Visual studio 2017** pour ouvrir la fenêtre d’invite de commandes.

Si vous utilisez une autre version de Windows, recherchez dans le menu Démarrer ou la page de démarrage un dossier Visual Studio Tools contenant un raccourci d’invite de commandes développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher « invite de commandes développeur » et en choisir une qui correspond à la version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Ouvrir une invite de commandes développeur dans Visual Studio 2015

Si vous avez installé Microsoft Visual C++ Build Tools 2015 sur Windows 10, ouvrez le menu **Démarrer** , puis faites défiler et ouvrez le dossier **Visual C++ Build Tools** . Choisissez **Visual C++ Invite de commandes des outils natifs x86 2015** pour ouvrir la fenêtre d’invite de commandes.

Si vous utilisez une autre version de Windows, recherchez dans le menu Démarrer ou la page de démarrage un dossier Visual Studio Tools contenant un raccourci d’invite de commandes développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher « invite de commandes développeur » et en choisir une qui correspond à la version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

::: moniker-end

Ensuite, vérifiez que l’invite de commandes développeur Visual C++ est correctement configurée. Dans la fenêtre d’invite de commandes `cl` , entrez et vérifiez que la sortie ressemble à ceci :

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Il peut y avoir des différences au niveau du répertoire actuel ou des numéros de version, en fonction de la version de Visual C++ et des mises à jour installées. Si la sortie ci-dessus est similaire à ce que vous voyez, vous êtes prêt à générer des programmes C ou C++ sur la ligne de commande.

> [!NOTE]
> Si vous recevez une erreur telle que « Cl » n’est pas reconnu en tant que commande interne ou externe, programme exécutable ou fichier de commandes, «erreur C1034 ou LNK1104 d’erreur lors de l’exécution de la commande **CL** , vous n’utilisez pas d’invite de commandes développeur ou un problème avec votre installation de Visual C++. Vous devez corriger ce problème avant de pouvoir continuer.

Si vous ne trouvez pas le raccourci d’invite de commandes développeur ou si vous recevez un message d’erreur `cl`lorsque vous entrez, votre installation de Visual C++ peut avoir un problème. Si vous utilisez Visual Studio 2017 ou une version ultérieure, essayez de réinstaller la charge de travail **développement Desktop en C++** dans le programme d’installation de Visual Studio. Pour plus d’informations, consultez [installer la prise en charge de C++ dans Visual Studio](vscpp-step-0-installation.md). Ou réinstallez les outils de génération à partir de la page de [téléchargements de Visual Studio](https://visualstudio.microsoft.com/downloads/) . N’passez pas à la section suivante jusqu’à ce que cela fonctionne. Pour plus d’informations sur l’installation et le dépannage de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Selon la version de Windows sur l’ordinateur et la configuration de la sécurité du système, vous devrez peut-être cliquer avec le bouton droit pour ouvrir le menu contextuel du raccourci d’invite de commandes développeur, puis choisir **exécuter en tant qu’administrateur** pour générer et exécuter correctement le programme que vous créez en suivant cette procédure pas à pas.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Créer un fichier source C et le compiler sur la ligne de commande

1. Dans la fenêtre d’invite de commandes développeur `cd c:\` , entrez pour modifier le répertoire de travail actuel à la racine de votre lecteur C :. Ensuite, entrez `md c:\simple` pour créer un répertoire, puis entrez `cd c:\simple` pour passer à ce répertoire. Ce répertoire contiendra votre fichier source et le programme compilé.

1. Entrez `notepad simple.c` à l’invite de commandes développeur. Dans la boîte de dialogue d’alerte du bloc-notes qui s’affiche, choisissez **Oui** pour créer un nouveau fichier simple. c dans votre répertoire de travail.

1. Dans le bloc-notes, entrez les lignes de code suivantes :

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Dans la barre de menus du bloc-notes, choisissez **fichier** > **Enregistrer** pour enregistrer simple. c dans votre répertoire de travail.

1. Revenez à la fenêtre d’invite de commandes développeur. Entrez `dir` à l’invite de commandes pour répertorier le contenu du répertoire c:\simple. Vous devez voir le fichier source simple. c dans la liste des répertoires, qui ressemble à ceci :

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, simple. c, vérifiez que vous avez modifié le répertoire c:\simple que vous avez créé et, dans le bloc-notes, vérifiez que vous avez enregistré votre fichier source dans ce répertoire. Assurez-vous également que vous avez enregistré le code source avec une extension de nom de fichier. c, et non une extension. txt.

1. Pour compiler votre programme, entrez `cl simple.c` à l’invite de commandes développeur.

   Vous pouvez voir le nom du programme exécutable, simple. exe, dans les lignes d’informations de sortie affichées par le compilateur :

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > Si vous recevez une erreur telle que « Cl » n’est pas reconnu en tant que commande interne ou externe, programme exécutable ou fichier de commandes, «erreur C1034 ou LNK1104 d’erreur, l’invite de commandes développeur n’est pas configurée correctement. Pour plus d’informations sur la résolution de ce problème, revenez à la section **ouvrir une invite de commandes développeur** .

   > [!NOTE]
   > Si vous recevez une erreur ou un avertissement du compilateur ou de l’éditeur de liens différent, examinez votre code source pour corriger les erreurs éventuelles, puis enregistrez-le et réexécutez le compilateur. Pour plus d’informations sur des erreurs spécifiques, utilisez la zone de recherche en haut de cette page pour rechercher le numéro d’erreur.

1. Pour exécuter votre programme, entrez `simple` à l’invite de commandes.

   Le programme affiche ce texte puis se ferme :

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Félicitations, vous avez compilé et exécuté un programme C à l’aide de la ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple « Hello, World » est le plus simple qu’un programme C peut obtenir. Les programmes réels contiennent des fichiers d’en-tête et d’autres fichiers sources, des liens dans les bibliothèques et un travail utile.

Vous pouvez utiliser les étapes de cette procédure pas à pas pour générer votre propre code C au lieu de taper l’exemple de code indiqué. Vous pouvez également créer un grand nombre de programmes d’exemples de code C que vous trouverez ailleurs. Pour compiler un programme qui contient des fichiers de code source supplémentaires, entrez-les tous sur la ligne de commande, par exemple :

`cl file1.c file2.c file3.c`

Le compilateur génère un programme appelé fichier1. exe. Pour modifier le nom en Program1. exe, ajoutez une option [/out](reference/out-output-file-name.md) de l’éditeur de liens :

`cl file1.c file2.c file3.c /link /out:program1.exe`

Et pour intercepter automatiquement d’autres erreurs de programmation, nous vous recommandons de compiler à l’aide de l’option de niveau d’avertissement [/W3](reference/compiler-option-warning-level.md) ou [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Le compilateur, cl. exe, offre de nombreuses autres options que vous pouvez appliquer pour générer, optimiser, déboguer et analyser votre code. Pour obtenir une liste rapide, `cl /?` entrez à l’invite de commandes développeur. Vous pouvez également compiler et lier séparément et appliquer des options de l’éditeur de liens dans des scénarios de génération plus complexes. Pour plus d’informations sur les options du compilateur et de l’éditeur de liens et sur son utilisation, consultez Référence de la [génération C/C++](reference/c-cpp-building-reference.md).

Vous pouvez utiliser NMAKE et les Makefiles, ou les fichiers projet et MSBuild pour configurer et générer des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, consultez la [Référence NMAKE](reference/nmake-reference.md) et [MSBuild](msbuild-visual-cpp.md).

Les langages C et C++ sont similaires, mais pas identiques. Le compilateur Microsoft C/C++ (MSVC) utilise une règle simple pour déterminer le langage à utiliser lors de la compilation de votre code. Par défaut, le compilateur MSVC traite tous les fichiers qui se terminent par. c en tant que code source C, et tous les fichiers se terminant par. cpp comme code source C++. Pour forcer le compilateur à traiter tous les fichiers comme étant non tributaires de l’extension de nom de fichier, utilisez l’option du compilateur [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) .

MSVC est compatible avec la norme ISO C99, mais n’est pas strictement conforme. Dans la plupart des cas, le code C portable se compile et s’exécute comme prévu. Visual C++ ne prend pas en charge la plupart des modifications apportées à ISO C11. Certaines fonctions de bibliothèque et certains noms de fonction POSIX sont déconseillés par MSVC. Les fonctions sont prises en charge, mais les noms préférés ont changé. Pour plus d’informations, consultez [fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création d’un programme C++ standard (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Référence du langage C](../c-language/c-language-reference.md)<br/>
[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Compatibilité](../c-runtime-library/compatibility.md)
