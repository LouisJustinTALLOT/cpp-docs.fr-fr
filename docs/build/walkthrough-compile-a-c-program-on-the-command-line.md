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

Visual CMD comprend un compilateur C que vous pouvez utiliser pour créer tout, des programmes de console de base aux applications Windows Desktop complètes, aux applications mobiles, et plus encore.

Ce pas-fort montre comment créer un programme C de base, "Bonjour, Monde" en utilisant un éditeur de texte, puis le compiler sur la ligne de commande. Si vous préférez travailler en C sur la ligne de commandement, consultez [Walkthrough: Compiling a Native CMD Program on the Command Line](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si vous souhaitez essayer l’IDE Visual Studio au lieu d’utiliser la ligne de commande, voir [Procédure Pasthrough: Working with Projects and Solutions (C)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [En utilisant l’IDE Visual Studio pour le développement de bureau C .](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)

## <a name="prerequisites"></a>Prérequis

Pour compléter cette procédure pas à pas, vous devez avoir installé soit Visual Studio et les composants Visual CMD en option, soit les outils build Tools for Visual Studio.

Visual Studio est un puissant environnement de développement intégré qui prend en charge un éditeur, des gestionnaires de ressources, des débrilleurs et des compilateurs complets pour de nombreuses langues et plates-formes. Pour plus d’informations sur ces fonctionnalités et comment télécharger et installer Visual Studio, y compris l’édition gratuite Visual Studio Community, voir [Install Visual Studio](/visualstudio/install/install-visual-studio).

La version Build Tools for Visual Studio de Visual Studio n’installe que l’outil de la ligne de commande, les compilateurs, les outils et les bibliothèques dont vous avez besoin pour construire des programmes C et CM. Il est parfait pour construire des laboratoires ou des exercices en classe et s’installe relativement rapidement. Pour installer uniquement l’toolset de ligne de commande, téléchargez Build Tools for Visual Studio à partir de la page [de téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) et exécutez l’installateur. Dans l’installateur Visual Studio, sélectionnez la charge de travail **des outils de construction CMD** et choisissez **Install**.

Avant de pouvoir construire un programme C ou C sur la ligne de commande, vous devez vérifier que les outils sont installés et que vous pouvez y accéder à partir de la ligne de commande. Visual CMMD a des exigences complexes pour l’environnement de la ligne de commande pour trouver les outils, les en-têtes et les bibliothèques qu’il utilise. **Vous ne pouvez pas utiliser Visual CMMD dans une fenêtre rapide de commande simple** sans une certaine préparation. Vous avez besoin d’une fenêtre *d’invitation de commande de développeur,* qui est une fenêtre rapide de commande régulière qui a toutes les variables d’environnement requises définies. Heureusement, Visual CMMD installe des raccourcis pour vous permettre de lancer des invites de commande de développeur qui ont l’environnement mis en place pour la ligne de commande construit. Malheureusement, les noms de la commande du développeur rapide raccourcis et où ils sont situés sont différents dans presque toutes les versions de Visual C et sur différentes versions de Windows. Votre première tâche pas à pas est de trouver le bon raccourci à utiliser.

> [!NOTE]
> Un raccourci d’invite de commande de développeur définit automatiquement les chemins corrects pour le compilateur et les outils, et pour tous les en-têtes et bibliothèques requis. Certaines de ces valeurs sont différentes pour chaque configuration de construction. Vous devez définir ces valeurs de l’environnement vous-même si vous n’utilisez pas l’un des raccourcis. Pour plus d’informations, consultez [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md). Parce que l’environnement de construction est complexe, nous vous recommandons fortement d’utiliser un raccourci rapide commande développeur au lieu de construire votre propre.

Ces instructions varient selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Ouvrez une invite de commande de développeur dans Visual Studio 2019

Si vous avez installé Visual Studio 2019 sur Windows 10, ouvrez le menu Démarrer, puis faites défiler vers le bas et ouvrez le dossier **Visual Studio 2019** (pas l’application Visual Studio 2019). Choisissez **Developer Command Prompt pour VS 2019** pour ouvrir la fenêtre d’invite de commande.

Si vous utilisez une version différente de Windows, regardez dans votre menu Démarrer ou démarrer la page pour un dossier d’outils Visual Studio qui contient un raccourci rapide de commande développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher "développeur de commande rapide" et choisir celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commande.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Ouvrez une invite de commande de développeur dans Visual Studio 2017

Si vous avez installé Visual Studio 2017 sur Windows 10, ouvrez le menu Démarrer, puis faites défiler vers le bas et ouvrez le dossier **Visual Studio 2017** (pas l’application Visual Studio 2017). Choisissez **Developer Command Prompt pour VS 2017** pour ouvrir la fenêtre d’invite de commande.

Si vous exécutez une version différente de Windows, regardez dans votre menu Démarrer ou démarrer la page pour un dossier d’outils Visual Studio qui contient un raccourci rapide de commande de développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher "développeur de commande rapide" et choisir celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commande.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Ouvrez une invite de commande de développeur dans Visual Studio 2015

Si vous avez installé Microsoft Visual CMD Build Tools 2015 sur Windows 10, ouvrez le menu **Démarrer,** puis faites défiler vers le bas et ouvrez le dossier **Visual CMD Build Tools.** Choisissez **Visual CMMD 2015 x86 Native Tools Command Prompt** pour ouvrir la fenêtre d’invite de commande.

Si vous exécutez une version différente de Windows, regardez dans votre menu Démarrer ou démarrer la page pour un dossier d’outils Visual Studio qui contient un raccourci rapide de commande de développeur. Vous pouvez également utiliser la fonction de recherche Windows pour rechercher "développeur de commande rapide" et choisir celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commande.

::: moniker-end

Ensuite, vérifiez que l’invite de commande visualCMD est configuré correctement. Dans la fenêtre d’invite de commande, entrez `cl` et vérifiez que la sortie ressemble à ceci :

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Il peut y avoir des différences dans les numéros actuels d’annuaire ou de version, selon la version de Visual C et toutes les mises à jour installées. Si la sortie ci-dessus est similaire à ce que vous voyez, alors vous êtes prêt à construire des programmes C ou C à la ligne de commande.

> [!NOTE]
> Si vous obtenez une erreur telle que «cl» n’est pas reconnu comme une commande interne ou externe, programme opérable ou fichier par lots», erreur C1034, ou erreur LNK1104 lorsque vous exécutez la commande **cl,** alors soit vous n’utilisez pas une invite de commande développeur, ou quelque chose ne va pas avec votre installation de Visual C . Vous devez résoudre ce problème avant de pouvoir continuer.

Si vous ne trouvez pas le raccourci rapide de commande du développeur, ou si vous obtenez un message d’erreur lorsque vous entrez, `cl`votre installation Visual CMD peut avoir un problème. Si vous utilisez Visual Studio 2017 ou plus tard, essayez de réinstaller le développement de bureau avec la charge de travail **de CMD** dans l’installateur Visual Studio. Pour plus de détails, voir [Le support Install CMD dans Visual Studio](vscpp-step-0-installation.md). Ou, réinstaller les outils build de la page [visual Studio téléchargements.](https://visualstudio.microsoft.com/downloads/) Ne pas aller à la section suivante jusqu’à ce que cela fonctionne. Pour plus d’informations sur l’installation et le dépannage Visual Studio, voir [Installer Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Selon la version de Windows sur l’ordinateur et la configuration de sécurité du système, vous devrez peut-être cliquer à droite pour ouvrir le menu raccourci pour le raccourci rapide de commande du développeur, puis choisir **Run en tant qu’administrateur** pour construire et exécuter avec succès le programme que vous créez en suivant cette procédure pas à pas.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Créez un fichier source C et compilez-le sur la ligne de commande

1. Dans la fenêtre d’invite de commande de développeur, entrez `cd c:\` pour changer l’annuaire de travail actuel à la racine de votre C : conduisez. Ensuite, `md c:\simple` entrez pour créer un `cd c:\simple` répertoire, puis entrez pour changer à ce répertoire. Ce répertoire tiendra votre fichier source et le programme compilé.

1. Entrez `notepad simple.c` à l’invite de commande du développeur. Dans le dialogue d’alerte Notepad qui apparaît, choisissez **Oui** pour créer un nouveau fichier simple.c dans votre répertoire de travail.

1. Dans Notepad, entrez les lignes de code suivantes :

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Sur la barre de menu Notepad, choisissez **File** > **Save** pour enregistrer simple.c dans votre répertoire de travail.

1. Retournez à la fenêtre d’invitation de commande du développeur. Entrez `dir` à l’invite de commande pour énumérer le contenu de l’annuaire c:'simple. Vous devriez voir le fichier source simple.c dans la liste d’annuaire, qui ressemble à:

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

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, simple.c, assurez-vous que vous avez changé pour l’annuaire c : simple que vous avez créé, et dans Notepad, assurez-vous que vous avez enregistré votre fichier source dans cet annuaire. Assurez-vous également que vous avez enregistré le code source avec une extension de nom de fichier .c, pas une extension .txt.

1. Pour compiler votre `cl simple.c` programme, entrez à l’invite de commande développeur.

   Vous pouvez voir le nom du programme exécutable, simple.exe, dans les lignes d’informations de sortie que le compilateur affiche:

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
   > Si vous obtenez une erreur telle que «cl» n’est pas reconnu comme une commande interne ou externe, programme opérable ou fichier de lot, erreur C1034, ou erreur LNK1104, votre invite de commande développeur n’est pas configuré correctement. Pour obtenir de l’information sur la façon de résoudre ce problème, retournez à la section **Open a developer command prompt.**

   > [!NOTE]
   > Si vous obtenez une erreur ou un avertissement de compilateur ou de lien différent, examinez votre code source pour corriger les erreurs, puis enregistrez-le et exécutez le compilateur à nouveau. Pour plus d’informations sur des erreurs spécifiques, utilisez la boîte de recherche en haut de cette page pour rechercher le numéro d’erreur.

1. Pour exécuter votre `simple` programme, entrez à l’invite de commande.

   Le programme affiche ce texte puis se ferme :

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Félicitations, vous avez compilé et exécuté un programme C en utilisant la ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple "Bonjour, monde" est à peu près aussi simple qu’un programme C peut obtenir. Les programmes du monde réel ont des fichiers d’en-tête et plus de fichiers source, lien dans les bibliothèques, et faire un travail utile.

Vous pouvez utiliser les étapes de cette procédure pas à pas pour construire votre propre code C au lieu de taper le code de l’échantillon montré. Vous pouvez également créer de nombreux programmes d’échantillons de code C que vous trouverez ailleurs. Pour compiler un programme qui dispose de fichiers de code source supplémentaires, entrez-les tous sur la ligne de commande, comme :

`cl file1.c file2.c file3.c`

Le compilateur produit un programme appelé file1.exe. Pour changer le nom en program1.exe, ajoutez une option [/out](reference/out-output-file-name.md) linker:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Et pour attraper plus d’erreurs de programmation automatiquement, nous vous recommandons de compiler en utilisant soit l’option de niveau d’avertissement [/W3](reference/compiler-option-warning-level.md) ou [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Le compilateur, cl.exe, a beaucoup plus d’options que vous pouvez appliquer pour construire, optimiser, déboiser, et analyser votre code. Pour une liste `cl /?` rapide, entrez à l’invite de commande développeur. Vous pouvez également compiler et lier séparément et appliquer des options de liaison dans des scénarios de construction plus complexes. Pour plus d’informations sur les options et l’utilisation des compilateurs et des liaisons, consultez [la référence du bâtiment C/C.](reference/c-cpp-building-reference.md)

Vous pouvez utiliser NMAKE et makefiles, ou MSBuild et les fichiers de projet pour configurer et construire des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, voir [NMAKE Reference](reference/nmake-reference.md) et [MSBuild](msbuild-visual-cpp.md).

Les langues C et CMD sont similaires, mais pas les mêmes. Le compilateur Microsoft C/CMD (MSVC) utilise une règle simple pour déterminer la langue à utiliser lorsqu’il compile votre code. Par défaut, le compilateur MSVC traite tous les fichiers qui se terminent en .c comme code source C, et tous les fichiers qui se terminent en .cpp comme code source C. Pour forcer le compilateur à traiter tous les fichiers comme C non dépendant de l’extension du nom de fichier, utilisez l’option [compilateur /Tc.](reference/tc-tp-tc-tp-specify-source-file-type.md)

MSVC est compatible avec la norme ISO C99, mais pas strictement conforme. Dans la plupart des cas, le code C portable compilera et s’exécute comme prévu. Visual CMD ne prend pas en charge la plupart des changements dans ISO C11. Certaines fonctions de bibliothèque et les noms de fonction POSIX sont dépréciés par MSVC. Les fonctions sont prises en charge, mais les noms préférés ont changé. Pour plus d’informations, voir [caractéristiques de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Compiler Warning (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création d’un programme C++ standard (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C Référence linguistique](../c-language/c-language-reference.md)<br/>
[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Compatibilité](../c-runtime-library/compatibility.md)
