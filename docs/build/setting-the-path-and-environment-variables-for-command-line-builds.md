---
title: Définir le chemin d’accès et les Variables d’environnement pour les Builds de ligne de commande
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- include
- Lib
- Path
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: dee8f4ee08f9922c4bfc79c5103618681058e56e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415368"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Définir le chemin d’accès et les Variables d’environnement pour les Builds de ligne de commande

Les outils de génération de ligne de commande de Visual C++ nécessitent plusieurs variables d’environnement personnalisées pour votre configuration de l’installation et de la build. Lorsqu’une charge de travail C++ est installé par le programme d’installation de Visual Studio, il crée des fichiers de commandes personnalisé, ou des fichiers de commandes, définissez les variables d’environnement requises. Le programme d’installation utilise ensuite ces fichiers de commandes pour créer des raccourcis du menu Démarrer de Windows ouvrir une fenêtre d’invite de commandes développeur. Ces raccourcis configurer les variables d’environnement pour un spécifique de configuration de build. Lorsque vous souhaitez utiliser les outils de ligne de commande, vous pouvez exécuter un de ces raccourcis, ou vous pouvez ouvrir une fenêtre d’invite de commandes standard et puis exécutez un des fichiers de commande personnalisée pour définir l’environnement de configuration de build vous-même. Pour plus d’informations, consultez [générer le Code C/C++ sur la ligne de commande](building-on-the-command-line.md).

Les outils de ligne de commande Visual C++ utilisent les variables d’environnement PATH, TMP, INCLUDE, LIB et LIBPATH et également utilisent les autres variables d’environnement spécifiques à vos outils installés, les plateformes et les kits de développement logiciel. Même une simple installation de Visual Studio peut définir des variables d’environnement de vingt ou plus. Étant donné que les valeurs de ces variables d’environnement sont spécifiques à votre installation et de configuration de build de votre choix et peuvent être modifiées en mises à jour de produit ou de mise à niveau, nous recommandons fortement d’utiliser un raccourci d’invite de commandes développeur ou l’un de le commande de fichiers personnalisés pour les définir, au lieu de les définir dans l’environnement Windows vous-même.

Pour afficher les variables d’environnement sont définies par un raccourci d’invite de commandes développeur, vous pouvez utiliser la commande SET. Ouvrez une fenêtre d’invite de commandes standard et capturer la sortie de la commande SET pour une ligne de base. Ouvrez une fenêtre d’invite de commandes développeur et capturer la sortie de la commande SET pour la comparaison. Un outil de comparaison tels que celui de l’IDE Visual Studio peut être utile pour comparer les variables d’environnement et de voir ce qui est défini par l’invite de commandes développeur. Pour plus d’informations sur les variables d’environnement spécifiques utilisées par le compilateur et l’éditeur de liens, consultez [Variables d’environnement CL](../build/reference/cl-environment-variables.md) et [Variables d’environnement de LINK](../build/reference/link-environment-variables.md).

> [!NOTE]
>  Plusieurs outils de ligne de commande ou les options de l’outil peuvent nécessiter une autorisation d’administrateur. Si vous avez des problèmes d’autorisation lorsque vous les utilisez, nous vous recommandons d’ouvrir la fenêtre d’invite de commandes de développeur à l’aide de la **exécuter en tant qu’administrateur** option. Sur Windows 10, avec le bouton droit pour ouvrir le menu contextuel de la fenêtre d’invite de commandes, puis choisissez **plus**, **exécuter en tant qu’administrateur**.

## <a name="see-also"></a>Voir aussi

[Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md)<br/>
[Liaison](../build/reference/linking.md)<br/>
[Options de l’éditeur de liens](../build/reference/linker-options.md)<br/>
[Compilation d’un programme C/C++](../build/reference/compiling-a-c-cpp-program.md)<br/>
[Options du compilateur](../build/reference/compiler-options.md)
