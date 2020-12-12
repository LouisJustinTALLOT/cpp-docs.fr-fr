---
description: 'En savoir plus sur : définir le chemin d’accès et les variables d’environnement pour les builds de Command-Line'
title: Définir le chemin d’accès et les variables d’environnement pour les builds Command-Line
ms.custom: conceptual
ms.date: 07/24/2019
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
ms.openlocfilehash: 3accc1cf56b86822298e1f1298bcae7d41c28332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275384"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Définir le chemin d’accès et les variables d’environnement pour les builds Command-Line

Les outils de génération en ligne de commande Microsoft C++ (MSVC) requièrent plusieurs variables d’environnement personnalisées pour votre installation et votre configuration de Build. Lorsqu’une charge de travail C++ est installée par le programme d’installation de Visual Studio, elle crée des fichiers de commandes personnalisés, ou fichiers de commandes, qui définissent les variables d’environnement requises. Le programme d’installation utilise ensuite ces fichiers de commandes pour créer des raccourcis pour le menu Démarrer de Windows afin d’ouvrir une fenêtre d’invite de commandes développeur. Ces raccourcis configurent les variables d’environnement pour une configuration de build spécifique. Lorsque vous souhaitez utiliser les outils en ligne de commande, vous pouvez exécuter l’un de ces raccourcis ou ouvrir une fenêtre d’invite de commandes simple, puis exécuter l’un des fichiers de commandes personnalisés pour définir vous-même l’environnement de configuration de Build. Pour plus d’informations, consultez [utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md). Pour utiliser les fichiers de commandes avec une invite de commandes simple, consultez la section [emplacements des fichiers de commandes développeur](building-on-the-command-line.md#developer_command_file_locations).

Les outils en ligne de commande MSVC utilisent les variables d’environnement PATH, TMP, INCLUDe, LIB et LIBPATH, et utilisent également d’autres variables d’environnement spécifiques à vos outils, plateformes et kits de développement logiciel installés. Même une installation Visual Studio simple peut définir vingt variables d’environnement ou plus. Étant donné que les valeurs de ces variables d’environnement sont spécifiques à votre installation et à votre choix de configuration de build, et peuvent être modifiées par des mises à jour ou des mises à niveau de produit, nous vous recommandons vivement d’utiliser un raccourci d’invite de commandes développeur ou l’un des fichiers de commandes personnalisés pour les définir, au lieu de les définir dans l’environnement Windows.

Pour connaître les variables d’environnement qui sont définies par un raccourci d’invite de commandes développeur, vous pouvez utiliser la commande SET. Ouvrez une fenêtre d’invite de commandes ordinaire et capturez la sortie de la commande SET pour une ligne de base. Ouvrez une fenêtre d’invite de commandes développeur et capturez la sortie de la commande SET pour la comparaison. Un outil diff, tel que celui intégré à l’IDE de Visual Studio, peut être utile pour comparer les variables d’environnement et voir ce qui est défini par l’invite de commandes développeur. Pour plus d’informations sur les variables d’environnement spécifiques utilisées par le compilateur et l’éditeur de liens, consultez [variables d’environnement CL](reference/cl-environment-variables.md).

> [!NOTE]
> Plusieurs outils en ligne de commande ou options d’outil peuvent nécessiter des autorisations d’administrateur. Si vous avez des problèmes d’autorisation lorsque vous les utilisez, nous vous recommandons d’ouvrir la fenêtre d’invite de commandes développeur à l’aide de l’option **exécuter en tant qu’administrateur** . Sur Windows 10, cliquez avec le bouton droit pour ouvrir le menu contextuel de la fenêtre d’invite de commandes, puis choisissez **plus**, **exécuter en tant qu’administrateur**.

## <a name="see-also"></a>Voir aussi

[Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](reference/linking.md)<br/>
[Options de l’éditeur de liens MSVC](reference/linker-options.md)<br/>
[Référence du compilateur MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
