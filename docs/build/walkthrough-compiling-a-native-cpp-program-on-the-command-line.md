---
title: 'Procédure pas à pas : Compilation d’un programme C++ natif sur la ligne de commande | Documents Microsoft'
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb0d7aab8000febdf07288370da058f437767387
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322431"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++ natif sur la ligne de commande

Visual C++ inclut un compilateur de ligne de commande C++ que vous pouvez utiliser pour créer toutes sortes d’applications console Visual basic pour applications de plateforme Windows universelle, les applications de bureau, les pilotes de périphérique et les composants .NET.

Dans cette procédure pas à pas, vous créez une base « Hello, World »-style programme C++ à l’aide d’un texte de l’éditeur, puis le compiler sur la ligne de commande. Si vous souhaitez essayer l’IDE de Visual Studio au lieu d’utiliser la ligne de commande, consultez [procédure pas à pas : utilisation de projets et Solutions (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [à l’aide de l’IDE de Visual Studio pour le développement de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

Dans cette procédure pas à pas, vous pouvez utiliser votre propre programme Visual C++ au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code Visual C++ provenant d'un autre article d'aide.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio et le paramètre facultatif **bureau développement avec C++** la charge de travail ou les outils de génération de ligne de commande pour Visual Studio.

Visual Studio est un environnement puissant de développement intégré (IDE) qui prend en charge un éditeur complet, les gestionnaires de ressources, les débogueurs et les compilateurs pour plusieurs langages et les plateformes. Pour plus d’informations sur la façon de télécharger et installer Visual Studio, y compris l’édition gratuite de Visual Studio Community et pour inclure la prise en charge pour le développement C/C++, consultez [prise en charge de l’installation de C++ dans Visual Studio](../build/vscpp-step-0-installation.md).

Les outils de génération pour Visual Studio installe uniquement les compilateurs de ligne de commande, outils et bibliothèques que vous avez besoin pour générer des programmes C et C++. Il est idéal pour les laboratoires de build ou la classe exerce et installe assez rapidement. Pour installer uniquement les outils de ligne de commande, téléchargez [outils de génération pour Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Avant de pouvoir créer un programme C ou C++ sur la ligne de commande, vous devez vérifier que les outils sont installés et que vous pouvez y accéder à partir de la ligne de commande. Visual C++ a des exigences complexes de l’environnement de ligne de commande afin de trouver les outils, les en-têtes et les bibliothèques qu’il utilise. **Vous ne pouvez pas utiliser Visual C++ dans une fenêtre d’invite de commande simple** sans effectuer certaines tâches de préparation. Heureusement, Visual C++ installe des raccourcis pour vous permet de lancer une invite de commandes développeur qui a la configuration d’environnement pour les versions de ligne de commande. Malheureusement, les noms des raccourcis d’invite de commandes développeur et où ils se situent sont différents dans presque chaque version de Visual C++ et sur différentes versions de Windows. La première tâche de la procédure pas à pas est de trouver celui qui convient à utiliser.

> [!NOTE]
> Un raccourci d’invite de commandes développeur définit automatiquement les chemins d’accès corrects pour le compilateur et les outils et pour tous les en-têtes requis et les bibliothèques. Vous devez définir ces valeurs d’environnement vous-même si vous utilisez une fenêtre d’invite de commandes normale. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Nous vous recommandons de qu'utiliser un raccourci d’invite de commandes développeur au lieu de générer votre propre.

### <a name="open-a-developer-command-prompt"></a>Ouvrez une invite de commandes développeur

1. Si vous avez installé Visual Studio 2017 sur Windows 10, ouvrez le menu Démarrer, puis choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le **Visual Studio 2017** dossier (pas l’application Visual Studio 2017). Choisissez **invite de commandes développeur pour VS 2017** pour ouvrir la fenêtre d’invite de commandes.

   Si vous avez installé Microsoft Visual C++ Build Tools 2015 sur Windows 10, ouvrez le **Démarrer** menu et choisissez **toutes les applications**. Faites défiler vers le bas et ouvrez le **outils de génération de Visual C++** dossier. Choisissez **invite de commandes outils natifs Visual C++ 2015 x86** pour ouvrir la fenêtre d’invite de commandes.

   Si vous utilisez une autre version de Visual Studio ou une autre version de Windows sont en cours d’exécution, recherchez dans votre menu Démarrer ou page pour un dossier d’outils de Visual Studio qui contient un raccourci d’invite de commandes développeur de démarrage. Vous pouvez également utiliser la fonction de recherche de Windows pour rechercher « invite de commandes développeur » et sélectionnez celle qui correspond à votre version installée de Visual Studio. Utilisez le raccourci pour ouvrir la fenêtre d’invite de commandes.

2. Ensuite, vérifiez que l’invite de commandes développeur Visual C++ est correctement configuré. Dans la fenêtre d’invite de commandes, entrez `cl` et vérifiez que la sortie ressemble à ceci :

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Il peut y avoir des différences dans le répertoire actuel ou les numéros de version, selon la version de Visual C++ et les mises à jour installées. Si cela est similaire à celle que vous voyez, vous êtes prêt à créer des programmes C ou C++ sur la ligne de commande.

   > [!NOTE]
   > Si vous obtenez une erreur, tels que « « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104 lorsque vous exécutez le **cl** de commandes, puis soit vous n’utilisez pas d’une invite de commandes développeur, ou un problème se pose avec votre installation de Visual C++. Vous devez corriger ce problème avant de continuer.

   Si vous ne trouvez pas le développeur raccourci d’invite de commande, ou si vous obtenez un message d’erreur lorsque vous entrez `cl`, puis votre installation Visual C++ peut rencontrer un problème. Essayez de réinstaller le composant Visual C++ dans Visual Studio, ou réinstallez Microsoft Visual C++ Build Tools. Ne passez à la section suivante jusqu'à ce que cela fonctionne. Pour plus d’informations sur l’installation et la résolution des problèmes de Visual C++, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Selon la version de Windows sur l’ordinateur et la configuration de sécurité du système, vous devrez peut-être avec le bouton droit pour ouvrir le menu contextuel pour le raccourci d’invite de commandes développeur, puis choisissez **exécuter en tant qu’administrateur** à avec succès, générez et exécutez le programme que vous créez en suivant cette procédure pas à pas.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Créer un fichier source Visual C++ et le compiler sur la ligne de commande

1. Dans la fenêtre d’invite de commandes développeur, entrez **md c:\hello** pour créer un répertoire, puis entrez **cd c:\hello** pour accéder à ce répertoire. Il s’agit du répertoire créés dans votre fichier source et le programme compilé.

2. Entrez **notepad hello.cpp** dans la fenêtre d’invite de commandes.

   Choisissez **Oui** lorsque le bloc-notes vous invite à créer un fichier. Une fenêtre du bloc-notes vide, prête à entrer votre code dans un fichier nommé hello.cpp s’ouvre.

3. Dans le bloc-notes, entrez les lignes de code suivantes :

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Il s’agit d’un programme très simple qui écrit une seule ligne de texte sur l’écran, puis s’arrête. Pour minimiser les risques d’erreurs, copiez le code et collez-le dans le Bloc-notes.

4. Enregistrez votre travail. Dans le Bloc-notes, dans le menu **Fichier** , choisissez **Enregistrer**.

   Félicitations, vous avez créé un fichier source Visual C++, hello.cpp, qui est prêt pour la compilation.

5. Revenez à la fenêtre d’invite de commandes développeur. Entrez **dir** à l’invite de commande pour répertorier le contenu du répertoire c:\hello. Vous devez voir le hello.cpp du fichier source dans la liste de répertoires, qui ressemble à ceci :

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

6. À l’invite de commandes développeur, entrez `cl /EHsc hello.cpp` pour compiler votre programme.

   Le compilateur cl.exe génère un fichier .obj qui contient le code compilé, puis exécute l’éditeur de liens pour créer un programme exécutable nommé hello.exe. Ce nom apparaît dans les lignes des informations de sortie affichées par le compilateur. La sortie du compilateur doit ressembler à ceci :

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
   > Si vous obtenez une erreur, tels que « « cl » n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes, » erreur C1034 ou l’erreur LNK1104, votre invite de commandes développeur n’est pas configuré correctement. Pour plus d’informations sur la façon de résoudre ce problème, revenez à la **ouvrir une invite de commandes développeur** section.

   > [!NOTE]
   > Si vous obtenez une erreur de l’éditeur de liens ou compilateur différente ou un avertissement, passez en revue votre code source pour corriger les erreurs éventuelles, puis enregistrez-le et réexécutez le compilateur. Pour plus d’informations sur les erreurs spécifiques, utilisez la zone de recherche sur cette page MSDN pour rechercher le numéro d’erreur.

7. Pour exécuter le programme hello.exe, à l’invite de commandes, entrez `hello`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   Hello, world, from Visual C++!
   ```

   Félicitations, vous avez simplement compilé et exécuté un programme C++ en utilisant les outils de ligne de commande.

## <a name="next-steps"></a>Étapes suivantes

Cet exemple « Hello, World » est environ aussi simple qu’un programme C++ peut obtenir. Programmes réels ont des fichiers d’en-tête et d’autres fichiers sources, la liaison dans les bibliothèques et effectuer des tâches utiles.

Vous pouvez utiliser les étapes dans cette procédure pas à pas pour créer votre propre code C++ au lieu de taper l’exemple de code indiqué. Vous pouvez également générer des nombreux programmes d’exemple de code C++ que vous trouvez ailleurs. Vous pouvez placer votre code source et créer des applications dans un répertoire accessible en écriture. Par défaut, l’IDE Visual Studio crée des projets dans votre dossier Documents, dans un sous-dossier de projets d’un dossier de Visual Studio nommé pour votre version de Visual Studio.

Pour compiler un programme qui a plusieurs fichiers de code source, les entrer sur la ligne de commande, comme suit :

`cl /EHsc file1.cpp file2.cpp file3.cpp`

L’option de ligne de commande **/EHsc** indique au compilateur d’activer la gestion des exceptions C++. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md).

Lorsque vous fournissez plusieurs fichiers sources à ceci, le compilateur utilise le premier fichier d’entrée pour créer le nom du programme. Dans ce cas, il génère un programme appelé file1.exe. Pour modifier le nom à program1.exe, ajoutez une [/out](../build/reference/out-output-file-name.md) option de l’éditeur de liens :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Pour intercepter les erreurs de programmation plus automatiquement, nous vous recommandons de vous compilez à l’aide du [/W3](../build/reference/compiler-option-warning-level.md) ou [/W4](../build/reference/compiler-option-warning-level.md) option niveau d’avertissement :

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Le compilateur, cl.exe, propose de nombreuses options plus, vous pouvez appliquer pour générer, optimiser, déboguer et analyser votre code. Pour obtenir la liste rapide, entrez **cl / ?** à l’invite de commandes développeur. Vous pouvez aussi compiler et lier séparément et appliquer des options de l’éditeur de liens dans les scénarios plus complexes. Pour plus d’informations sur le compilateur et les options de l’éditeur de liens et d’utilisation, consultez [référence à la génération C/C++](../build/reference/c-cpp-building-reference.md).

Vous pouvez utiliser MSBuild et les fichiers projet et makefiles ou NMAKE pour configurer et générer des projets plus complexes sur la ligne de commande. Pour plus d’informations sur l’utilisation de ces outils, consultez [Référence NMAKE](../build/nmake-reference.md) et [MSBuild](../build/msbuild-visual-cpp.md).

Les langages C et C++ sont similaires, mais pas le même. Le compilateur Visual C++ utilise une règle simple pour déterminer le langage à utiliser lors de la compilation de votre code. Par défaut, le compilateur Visual C++ traite tous les fichiers se terminant par .c comme code source C et tous les fichiers se terminant par .cpp comme code source C++. Pour forcer le compilateur à traiter tous les fichiers en C++, quelle que soit l’extension de nom de fichier, utilisez le [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) option du compilateur.

Le compilateur Visual C++ inclut une bibliothèque de Runtime C (CRT) qui est compatible avec la norme ISO C99, mais n’est pas strictement compatible. Dans la plupart des cas, un code portable compilera et s’exécuter comme prévu. Visual C++ ne prend pas en charge certaines modifications CRT ISO C11. Certaines fonctions de bibliothèque et les noms de fonctions POSIX sont déconseillées par le compilateur Visual C++. Les fonctions sont prises en charge, mais les noms par défaut ont été modifiés. Pour plus d’informations, consultez [les fonctionnalités de sécurité dans la bibliothèque CRT](../c-runtime-library/security-features-in-the-crt.md) et [l’avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)  
[Génération de programmes C/C++](../build/building-c-cpp-programs.md)  
[Options du compilateur](../build/reference/compiler-options.md)  
