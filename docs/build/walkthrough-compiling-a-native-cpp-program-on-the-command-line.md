---
title: "Procédure pas à pas : compilation d'un programme C++ natif sur la ligne de commande"
description: Utilisez le compilateur Microsoft CMD à partir d’une invite de commande.
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335229"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++ natif sur la ligne de commande

Visual Studio comprend un compilateur de la ligne de commande C et C. Vous pouvez l’utiliser pour créer de tout, des applications consoles de base aux applications Universal Windows Platform, aux applications de bureau, aux pilotes d’appareils et aux composants .NET.

Dans cette procédure pas à pas, vous créez un programme de base, "Bonjour, Monde" de style C en utilisant un éditeur de texte, puis le compiler sur la ligne de commande. Si vous souhaitez essayer l’IDE Visual Studio au lieu d’utiliser la ligne de commande, voir [Procédure Pasthrough: Working with Projects and Solutions (C)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [En utilisant l’IDE Visual Studio pour le développement de bureau C .](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)

Dans cette procédure pas à pas, vous pouvez utiliser votre propre programme C au lieu de taper celui qui est montré. Ou, vous pouvez utiliser un échantillon de code CMD d’un autre article d’aide.

## <a name="prerequisites"></a>Prérequis

Pour compléter cette procédure pas à pas, vous devez avoir installé soit Visual Studio et le développement de bureau en option avec la charge de travail **de C,** ou la ligne de commande Build Tools pour Visual Studio.

Visual Studio est un *environnement de développement intégré* (IDE). Il prend en charge un éditeur, des gestionnaires de ressources, des débrilleurs et des compilateurs complets pour de nombreuses langues et plates-formes. Les versions disponibles comprennent l’édition gratuite Visual Studio Community, et toutes peuvent soutenir le développement C et CMD. Pour plus d’informations sur la façon de télécharger et d’installer Visual Studio, voir [Le support Install CMD dans Visual Studio](vscpp-step-0-installation.md).

Les outils de construction pour studio visuel n’installent que les compilateurs de lignes de commande, les outils et les bibliothèques dont vous avez besoin pour construire des programmes C et CM. Il est parfait pour construire des laboratoires ou des exercices en classe et s’installe relativement rapidement. Pour installer uniquement les outils de la ligne de commande, recherchez build Tools for Visual Studio sur la page [Visual Studio Downloads.](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)

Avant de pouvoir construire un programme C ou C sur la ligne de commande, vérifiez que les outils sont installés et que vous pouvez y accéder depuis la ligne de commande. Visual CMMD a des exigences complexes pour l’environnement de la ligne de commande pour trouver les outils, les en-têtes et les bibliothèques qu’il utilise. **Vous ne pouvez pas utiliser Visual CMMD dans une fenêtre rapide de commande simple** sans faire une certaine préparation. Heureusement, Visual CMMD installe des raccourcis pour que vous lancez une invite de commande de développeur qui a l’environnement mis en place pour la ligne de commande construit. Malheureusement, les noms de la commande du développeur rapide raccourcis et où ils sont situés sont différents dans presque toutes les versions de Visual C et sur différentes versions de Windows. Votre première tâche pas à pas est de trouver la bonne tâche à utiliser.

> [!NOTE]
> Un raccourci d’invite de commande de développeur définit automatiquement les chemins corrects pour le compilateur et les outils, et pour tous les en-têtes et bibliothèques requis. Vous devez définir ces valeurs d’environnement vous-même si vous utilisez une fenêtre **régulière De commande Prompt.** Pour plus d’informations, consultez [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md). Nous vous recommandons d’utiliser un raccourci rapide de commande de développeur au lieu de construire votre propre.

### <a name="open-a-developer-command-prompt"></a>Ouvrez une invite de commande de développeur

1. Si vous avez installé Visual Studio 2017 ou plus tard sur Windows 10, ouvrez le menu Démarrer et choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le dossier **Visual Studio** (pas l’application Visual Studio). Choisissez **Developer Command Prompt pour VS** pour ouvrir la fenêtre d’invite de commande.

   Si vous avez installé Microsoft Visual CMD Build Tools 2015 sur Windows 10, ouvrez le menu **Démarrer** et choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le dossier **Visual CMMD Build Tools.** Choisissez **Visual CMMD 2015 x86 Native Tools Command Prompt** pour ouvrir la fenêtre d’invite de commande.

   Vous pouvez également utiliser la fonction de recherche Windows pour rechercher "développeur de commande rapide" et choisir celui qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commande.

1. Ensuite, vérifiez que l’invite de commande visualCMD est configuré correctement. Dans la fenêtre d’invite de commande, entrez `cl` et vérifiez que la sortie ressemble à ceci :

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Il peut y avoir des différences dans les numéros actuels d’annuaire ou de version. Ces valeurs dépendent de la version de Visual CM et de toutes les mises à jour installées. Si la sortie ci-dessus est similaire à ce que vous voyez, alors vous êtes prêt à construire des programmes C ou C à la ligne de commande.

   > [!NOTE]
   > Si vous obtenez une erreur telle que «cl» n’est pas reconnu comme une commande interne ou externe, programme opérable ou fichier **`cl`** par lots», erreur C1034, ou erreur LNK1104 lorsque vous exécutez la commande, alors soit vous n’utilisez pas une invite de commande développeur, ou quelque chose ne va pas avec votre installation de Visual C . Vous devez résoudre ce problème avant de pouvoir continuer.

   Si vous ne trouvez pas le raccourci rapide de commande du développeur, ou si vous obtenez un message d’erreur lorsque vous entrez, `cl`votre installation Visual CMD peut avoir un problème. Essayez de réinstaller le composant Visual CMMD dans Visual Studio ou réinstallez les outils de construction Microsoft Visual CMD. Ne pas aller à la section **`cl`** suivante jusqu’à ce que la commande fonctionne. Pour plus d’informations sur l’installation et le dépannage visual C, voir [Install Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Selon la version de Windows sur l’ordinateur et la configuration de sécurité du système, vous pourriez avoir à cliquer à droite pour ouvrir le menu raccourci pour le raccourci rapide commande développeur, puis choisir **Run comme administrateur** pour construire et exécuter avec succès le programme que vous créez en suivant cette procédure pas à pas.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Créez un fichier source Visual CMD et compilez-le sur la ligne de commande

1. Dans la fenêtre d’invite de commande de développeur, entrez `md c:\hello` pour créer un répertoire, puis entrez `cd c:\hello` pour changer à ce répertoire. Ce répertoire est l’endroit où votre fichier source et le programme compilé sont créés.

1. Entrez `notepad hello.cpp` dans la fenêtre d’invite de commande.

   Choisissez **Oui** lorsque Notepad vous invite à créer un fichier. Cette étape ouvre une fenêtre Notepad vierge, prêt pour vous d’entrer votre code dans un fichier nommé hello.cpp.

1. Dans Notepad, entrez les lignes de code suivantes :

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ce code est un programme simple qui va écrire une ligne de texte sur l’écran, puis sortir. Pour minimiser les risques d’erreurs, copiez le code et collez-le dans le Bloc-notes.

1. Enregistrez votre travail. Dans le Bloc-notes, dans le menu **Fichier** , choisissez **Enregistrer**.

   Félicitations, vous avez créé un fichier source C, hello.cpp, qui est prêt à compiler.

1. Retournez à la fenêtre d’invitation de commande du développeur. Entrez `dir` à l’invite de commande pour énumérer le contenu de l’annuaire c:-bonjour. Vous devriez voir le fichier source hello.cpp dans la liste d’annuaire, qui ressemble à:

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

   Les dates et autres détails seront différents sur votre ordinateur. Si vous ne voyez pas votre fichier de code source, *hello.cpp*, assurez-vous que vous avez changé pour le *\\c: bonjour* répertoire que vous avez créé. Dans Notepad, assurez-vous d’avoir enregistré votre fichier source dans cet annuaire. Assurez-vous également que vous avez *`.cpp`* enregistré le code *`.txt`* source avec une extension de nom de fichier, pas une extension.

1. À l’invite de `cl /EHsc hello.cpp` commande du développeur, entrez pour compiler votre programme.

   Le compilateur cl.exe génère un fichier .obj qui contient le code compilé, puis exécute l’éditeur de liens pour créer un programme exécutable nommé hello.exe. Ce nom apparaît dans les lignes des informations de sortie affichées par le compilateur. La sortie du compilateur devrait ressembler à quelque chose comme:

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
   > Si vous obtenez une erreur telle que «cl» n’est pas reconnu comme une commande interne ou externe, programme opérable ou fichier de lot, erreur C1034, ou erreur LNK1104, votre invite de commande développeur n’est pas configuré correctement. Pour obtenir de l’information sur la façon de résoudre ce problème, retournez à la section **Open a developer command prompt.**

   > [!NOTE]
   > Si vous obtenez une erreur ou un avertissement de compilateur ou de lien différent, examinez votre code source pour corriger les erreurs, puis enregistrez-le et exécutez le compilateur à nouveau. Pour plus d’informations sur des erreurs spécifiques, utilisez la boîte de recherche sur cette page MSDN pour rechercher le numéro d’erreur.

1. Pour exécuter le programme hello.exe, à l’invite de commandes, entrez `hello`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   Hello, world, from Visual C++!
   ```

   Félicitations, vous avez compilé et exécuté un programme CMD en utilisant les outils de la ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple de " Bonjour, monde est à peu près aussi simple qu’un programme de CMD peut l’obtenir. Les programmes du monde réel ont généralement des fichiers d’en-tête, plus de fichiers source, et un lien vers les bibliothèques.

Vous pouvez utiliser les étapes de cette procédure pas à pas pour construire votre propre code C au lieu de taper le code de l’échantillon indiqué. Ces étapes vous permettent également de créer de nombreux programmes d’échantillons de code CMD que vous trouvez ailleurs. Vous pouvez mettre votre code source et créer vos applications dans n’importe quel répertoire récaltable. Par défaut, l’IDE Visual Studio crée des projets dans votre dossier utilisateur, dans un sous-pli de *repos source.\\* Les versions plus anciennes peuvent mettre des projets dans une *version Documents\\Visual Studio \<>\\ *dossier ProjectsMD.

Pour compiler un programme qui dispose de fichiers de code source supplémentaires, entrez-les tous sur la ligne de commande, comme :

`cl /EHsc file1.cpp file2.cpp file3.cpp`

L’option `/EHsc` de ligne de commande demande au compilateur d’activer le comportement standard de manipulation des exceptions CMD. Sans elle, les exceptions jetées peuvent entraîner des objets non consommés et des fuites de ressources. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](reference/eh-exception-handling-model.md).

Lorsque vous fournissez des fichiers source supplémentaires, le compilateur utilise le premier fichier d’entrée pour créer le nom du programme. Dans ce cas, il produit un programme appelé file1.exe. Pour changer le nom en program1.exe, ajoutez une option [/out](reference/out-output-file-name.md) linker:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Et pour attraper plus d’erreurs de programmation automatiquement, nous vous recommandons de compiler en utilisant soit l’option de niveau d’avertissement [/W3](reference/compiler-option-warning-level.md) ou [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Le compilateur, cl.exe, a beaucoup plus d’options. Vous pouvez les appliquer pour construire, optimiser, déboquer et analyser votre code. Pour une liste `cl /?` rapide, entrez à l’invite de commande développeur. Vous pouvez également compiler et lier séparément et appliquer des options de liaison dans des scénarios de construction plus complexes. Pour plus d’informations sur les options et l’utilisation des compilateurs et des liaisons, consultez [la référence du bâtiment C/C.](reference/c-cpp-building-reference.md)

Vous pouvez utiliser NMAKE et faire des fichiers, des fichiers MSBuild et projet, ou CMake, pour configurer et construire des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, voir [NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md), et [CMake projets dans Visual Studio](cmake-projects-in-visual-studio.md).

Les langues C et CMD sont similaires, mais pas les mêmes. Le compilateur MSVC utilise une règle simple pour déterminer la langue à utiliser lorsqu’il compile votre code. Par défaut, le compilateur MSVC traite *`.c`* les fichiers qui se terminent sous forme de code source C, et les fichiers qui se terminent sous *`.cpp`* forme de code source C. Pour forcer le compilateur à traiter tous les fichiers comme C 'indépendamment de l’extension du nom de fichier, utilisez l’option [compilateur /TP.](reference/tc-tp-tc-tp-specify-source-file-type.md)

Le compilateur MSVC comprend une bibliothèque C Runtime (CRT) qui est conforme à la norme ISO C99, à quelques exceptions près. Le code portable compile généralement et fonctionne comme prévu. Certaines fonctions obsolètes de la bibliothèque, ainsi que plusieurs noms de fonction POSIX, sont dépréciées par le compilateur MSVC. Les fonctions sont prises en charge, mais les noms préférés ont changé. Pour plus d’informations, voir [caractéristiques de sécurité dans le CRT](../c-runtime-library/security-features-in-the-crt.md) et [Compiler Warning (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
