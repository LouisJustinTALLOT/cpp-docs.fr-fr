---
title: 'Procédure pas à pas : Compilation d’un programme C sur la ligne de commande | Microsoft Docs'
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f1390259838302a56e58397afa79fa8c458b939
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710331"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Procédure pas à pas : Compilation d’un programme C sur la ligne de commande

Visual C++ inclut un compilateur C que vous pouvez utiliser pour créer toutes sortes de programmes de console de base pour les applications Windows Desktop complètes, des applications mobiles et bien plus encore.

Cette procédure pas à pas montre comment créer une base « Hello, World »-programme C de style à l’aide d’un texte de l’éditeur, puis le compiler sur la ligne de commande. Si vous préférez travailler en C++ sur la ligne de commande, consultez [procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si vous souhaitez essayer de l’IDE de Visual Studio au lieu d’utiliser la ligne de commande, consultez [procédure pas à pas : utilisation de projets et Solutions (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [à l’aide de l’IDE Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio et les composants facultatifs de Visual C++ ou les outils de génération pour Visual Studio.

Visual Studio est un environnement de développement puissant et intégré qui prend en charge d’un éditeur complet, les gestionnaires de ressources, les débogueurs et les compilateurs pour plusieurs langages et plateformes. Pour plus d’informations sur ces fonctionnalités et comment télécharger et installer Visual Studio, y compris l’édition de Visual Studio Community gratuite, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

Les outils de génération pour Visual Studio version de Visual Studio installe uniquement l’ensemble d’outils de ligne de commande, les compilateurs, outils et bibliothèques que vous avez besoin pour générer des programmes C et C++. Il est idéal pour les laboratoires de conception ou de la classe teste et installe relativement rapidement. Pour installer uniquement l’ensemble d’outils de ligne de commande, téléchargez [Build Tools pour Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721) et exécutez le programme d’installation.

Avant de pouvoir créer un programme C ou C++ sur la ligne de commande, vous devez vérifier que les outils sont installés, et que vous pouvez y accéder à partir de la ligne de commande. Visual C++ a des exigences complexes pour l’environnement de ligne de commande afin de trouver les outils, les en-têtes et les bibliothèques qu’elle utilise. **Vous ne pouvez pas utiliser Visual C++ dans une fenêtre d’invite de commandes standard** sans certaines tâches de préparation. Vous devez un *invite de commandes développeur* fenêtre, qui est une fenêtre d’invite de commandes standard qui a toutes les variables d’environnement nécessaires à définir. Heureusement, Visual C++ installe des raccourcis pour lancer des invites de commandes développeur qui ont l’environnement configuré pour les builds de ligne de commande. Malheureusement, les noms des raccourcis d’invite de commandes développeur et où ils se trouvent sont différents dans presque toutes les versions de Visual C++ et sur différentes versions de Windows. Votre première tâche de procédure pas à pas consiste à trouver le bon raccourci à utiliser.

> [!NOTE]
> Un raccourci d’invite de commandes développeur définit automatiquement les chemins d’accès corrects pour le compilateur et les outils et pour des en-têtes obligatoires et des bibliothèques. Certaines de ces valeurs sont différentes pour chaque configuration de build. Vous devez définir ces valeurs d’environnement vous-même si vous n’utilisez pas l’un des raccourcis. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Étant donné que l’environnement de génération est complexe, nous vous recommandons vivement de qu'utiliser d’un raccourci d’invite de commandes développeur au lieu de créer votre propre.

## <a name="open-a-developer-command-prompt"></a>Ouvrez une invite de commandes développeur

1. Si vous avez installé Visual Studio 2017 sur Windows 10, ouvrez le menu Démarrer, puis faites défiler vers le bas et ouvrez le **Visual Studio 2017** dossier (et pas l’application de Visual Studio 2017). Choisissez **invite de commandes développeur pour VS 2017** pour ouvrir la fenêtre d’invite de commandes.

   Si vous avez installé Microsoft Visual C++ Build Tools 2015 sur Windows 10, ouvrez le **Démarrer** menu, puis faites défiler vers le bas et ouvrir le **Visual C++ Build Tools** dossier. Choisissez **invite de commandes outils natifs Visual C++ 2015 x86** pour ouvrir la fenêtre d’invite de commandes.

   Si vous utilisez une autre version de Visual Studio ou exécutez une version différente de Windows, recherchez dans votre menu Démarrer ou page pour un dossier d’outils de Visual Studio qui contient un raccourci d’invite de commandes développeur de démarrage. Vous pouvez également utiliser la fonction de recherche de Windows pour rechercher « invite de commande développeur » et choisissez celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

2. Ensuite, vérifiez que l’invite de commandes développeur Visual C++ est correctement configuré. Dans la fenêtre d’invite de commandes, entrez `cl` et vérifiez que la sortie ressemble à ceci :

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]

   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>
   ```

   Il peut exister des différences dans le répertoire actif ou les numéros de version, selon la version de Visual C++ et les mises à jour installées. Si cela est similaire à celle que vous voyez, vous êtes prêt à générer des programmes C ou C++ sur la ligne de commande.

   > [!NOTE]
   > Si vous obtenez une erreur, tels que « le « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104 lorsque vous exécutez le **cl** commande, soit vous n’utilisez pas d’une invite de commandes développeur, ou a un problème avec votre installation de Visual C++. Vous devez corriger ce problème avant de continuer.

   Si vous ne trouvez pas le développeur raccourci d’invite de commande, ou si vous obtenez un message d’erreur lorsque vous entrez `cl`, puis votre installation de Visual C++ peut rencontrer un problème. Si vous utilisez Visual Studio 2017, essayez de réinstaller le **développement Desktop en C++** charge de travail dans le programme d’installation de Visual Studio. Pour plus d’informations, consultez [prise en charge de l’installation de C++ dans Visual Studio](../build/vscpp-step-0-installation.md). Ou, réinstallez le [Build Tools pour Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721). Ne passez à la section suivante jusqu'à ce que cela fonctionne. Pour plus d’informations sur l’installation et la résolution des problèmes de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Selon la version de Windows sur l’ordinateur et la configuration de sécurité du système, vous devrez peut-être avec le bouton droit pour ouvrir le menu contextuel pour le raccourci d’invite de commandes développeur, puis choisissez **exécuter en tant qu’administrateur** à avec succès, générez et exécutez le programme que vous créez en suivant cette procédure pas à pas.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Créer un fichier source C et le compiler sur la ligne de commande

1. Dans la fenêtre d’invite de commandes développeur, entrez **cd c:\\**  pour modifier le répertoire de travail actuel à la racine de votre lecteur C:. Ensuite, entrez **md c:\simple** pour créer un répertoire, puis entrez **cd c:\simple** pour accéder à ce répertoire. Il s’agit du répertoire qui contient votre fichier source et le programme compilé.

2. Entrez **notepad simple.c** à l’invite de commandes développeur. Dans le bloc-notes alerte boîte de dialogue qui s’affiche, choisissez **Oui** pour créer un nouveau fichier simple.c dans votre répertoire de travail.

3. Dans le bloc-notes, entrez les lignes de code suivantes :

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

4. Dans la barre de menus le bloc-notes, choisissez **fichier**, **enregistrer** pour enregistrer simple.c dans votre répertoire de travail.

5. Revenez à la fenêtre d’invite de commandes développeur. Entrez **dir** à l’invite de commande pour répertorier le contenu du répertoire de c:\simple. Vous devez voir le simple.c du fichier source dans la liste de répertoires, qui ressemble à ceci :

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

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, simple.c, assurez-vous que vous avez modifié dans le répertoire de c:\simple que vous avez créé et dans le bloc-notes, vérifiez que vous avez enregistré votre fichier source dans ce répertoire. Assurez-vous également que vous avez enregistré le code source avec une extension de nom de fichier .c, pas une extension .txt.

6. Pour compiler votre programme, entrez **cl simple.c** à l’invite de commandes développeur.

   Vous pouvez voir le nom du programme exécutable, simple.exe, dans les lignes d’informations de sortie affichées par le compilateur :

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
   > Si vous obtenez une erreur, tels que « le « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104, votre invite de commandes développeur n’est pas configuré correctement. Pour plus d’informations sur la façon de résoudre ce problème, revenez à la **ouvrir une invite de commandes développeur** section.

   > [!NOTE]
   > Si vous obtenez une erreur de l’éditeur de liens ou du compilateur différents ou un avertissement, passez en revue votre code source pour corriger les erreurs éventuelles, puis enregistrez-le et réexécutez le compilateur. Pour plus d’informations sur les erreurs spécifiques, utilisez la zone de recherche en haut de cette page pour rechercher le numéro d’erreur.

7. Pour exécuter votre programme, entrez **simple** à l’invite de commandes.

   Le programme affiche ce texte puis se ferme :

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Félicitations, vous avez simplement compilé et exécuté un programme C à l’aide de la ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple « Hello, World » est environ aussi simple qu’un programme C peut obtenir. Programmes réels ont des fichiers d’en-tête et d’autres fichiers sources, liaison dans bibliothèques, et effectuer un travail utile.

Vous pouvez utiliser les étapes décrites dans cette procédure pas à pas pour générer votre propre code C au lieu de taper l’exemple de code indiqué. Vous pouvez également créer des nombreux exemples de programmes C que vous trouvez ailleurs. Pour compiler un programme qui a plusieurs fichiers de code source, les entrer sur la ligne de commande, comme suit :

`cl file1.c file2.c file3.c`

Le compilateur génère un programme appelé file1.exe. Pour modifier le nom à program1.exe, ajoutez un [/out](../build/reference/out-output-file-name.md) option de l’éditeur de liens :

`cl file1.c file2.c file3.c /link /out:program1.exe`

Et pour intercepter les erreurs de programmation plus automatiquement, nous vous recommandons de vous compilez en utilisant soit le [w3](../build/reference/compiler-option-warning-level.md) ou [/W4](../build/reference/compiler-option-warning-level.md) choix du niveau d’avertissement :

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Le compilateur, cl.exe, dispose de nombreuses options plus, vous pouvez appliquer pour générer, optimiser, déboguer et analyser votre code. Pour une liste rapide, entrez **cl / ?** à l’invite de commandes développeur. Vous pouvez également compiler et lier séparément s’appliquent aux options de l’éditeur de liens dans les scénarios de génération plus complexes. Pour plus d’informations sur les options de l’éditeur de liens et du compilateur et l’utilisation, consultez [référence à la génération C/C++](../build/reference/c-cpp-building-reference.md).

Vous pouvez utiliser NMAKE et makefiles ou MSBuild et les fichiers projet pour configurer et générer des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, consultez [Référence NMAKE](../build/nmake-reference.md) et [MSBuild](../build/msbuild-visual-cpp.md).

Les langages C et C++ sont similaires, mais pas dans le même. Le compilateur Visual C++ utilise une règle simple pour déterminer la langue à utiliser lors de la compilation de votre code. Par défaut, le compilateur Visual C++ traite tous les fichiers se terminant par .c comme code source C et tous les fichiers se terminant par .cpp comme code source C++. Pour forcer le compilateur doit traiter tous les fichiers en tant que C, quel que soit l’extension de nom de fichier, utilisez le [TP](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) option du compilateur.

Le compilateur Visual C++ C est généralement compatible avec la norme ISO C99, mais pas strictement conformes. Dans la plupart des cas, le code C portable compilera et s’exécuter comme prévu. Visual C++ ne prend pas en charge la plupart des modifications dans ISO C11. Certaines fonctions de bibliothèque et les noms de fonction POSIX sont déconseillées par le compilateur Visual C++. Les fonctions sont prises en charge, mais les noms par défaut ont changé. Pour plus d’informations, consultez [des fonctionnalités de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Création d’un programme C++ Standard (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)
[référence du langage C](../c-language/c-language-reference.md)<br/>
[Génération de programmes C/C++](../build/building-c-cpp-programs.md)<br/>
[Compatibilité](../c-runtime-library/compatibility.md)
