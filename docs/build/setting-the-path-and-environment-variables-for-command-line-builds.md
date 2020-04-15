---
title: Définir les variables de chemin et d’environnement pour les builds de la ligne de commandement
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
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335586"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Définir les variables de chemin et d’environnement pour les builds de la ligne de commandement

Les outils de conception de la ligne de commande Microsoft CMD (MSVC) nécessitent plusieurs variables d’environnement qui sont personnalisées pour votre configuration d’installation et de construction. Lorsqu’une charge de travail de CMD est installée par l’installateur Visual Studio, elle crée des fichiers de commande personnalisés, ou des fichiers de lots, qui définissent les variables d’environnement requises. L’installateur utilise ensuite ces fichiers de commande pour créer des raccourcis pour le menu Windows Start pour ouvrir une fenêtre d’invitation de commande développeur. Ces raccourcis configurent les variables de l’environnement pour une configuration de construction spécifique. Lorsque vous souhaitez utiliser les outils de ligne de commande, vous pouvez exécuter un de ces raccourcis, ou vous pouvez ouvrir une fenêtre rapide de commande simple, puis exécuter l’un des fichiers de commande personnalisés pour définir l’environnement de configuration de construction vous-même. Pour plus d’informations, voir [Utilisez l’toolset MSVC de la ligne de commande](building-on-the-command-line.md). Pour utiliser les fichiers de commande avec une invite de commande simple, consultez la section intitulée [Emplacements de fichiers de commande des développeurs](building-on-the-command-line.md#developer_command_file_locations).

Les outils de ligne de commande MSVC utilisent les variables de l’environnement PATH, TMP, INCLUDE, LIB et LIBPATH, et utilisent également d’autres variables de l’environnement spécifiques à vos outils, plates-formes et SDK installés. Même une simple installation Visual Studio peut définir une vingtaine de variables d’environnement ou plus. Étant donné que les valeurs de ces variables de l’environnement sont spécifiques à votre installation et à votre choix de configuration de construction, et peuvent être modifiées par des mises à jour ou des mises à niveau de produits, nous vous recommandons fortement d’utiliser un raccourci rapide de commande du développeur ou l’un des fichiers de commande personnalisés pour les définir, au lieu de les définir vous-même dans l’environnement Windows.

Pour voir quelles variables d’environnement sont définies par un raccourci rapide de commande de développeur, vous pouvez utiliser la commande SET. Ouvrez une fenêtre d’invite de commande simple et capturez la sortie de la commande SET pour une ligne de base. Ouvrez une fenêtre d’invite de commande de développeur et capturez la sortie de la commande SET pour comparaison. Un outil diff tel que celui intégré dans l’IDE Visual Studio peut être utile pour comparer les variables de l’environnement et voir ce qui est réglé par l’invite de commande développeur. Pour plus d’informations sur les variables spécifiques de l’environnement utilisées par le compilateur et le lien, voir [CL Environment Variables](reference/cl-environment-variables.md).

> [!NOTE]
> Plusieurs outils ou options d’outils de ligne de commande peuvent nécessiter la permission de l’Administrateur. Si vous avez des problèmes d’autorisation lorsque vous les utilisez, nous vous recommandons d’ouvrir la fenêtre d’invitation de commande du développeur en utilisant **l’option Run as Administrator.** Sur Windows 10, cliquez à droite pour ouvrir le menu raccourci pour la fenêtre d’invitation de commande, puis choisissez **Plus**, **Exécutez comme administrateur**.

## <a name="see-also"></a>Voir aussi

[Utiliser le jeu d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](reference/linking.md)<br/>
[Options de l’éditeur de liens MSVC](reference/linker-options.md)<br/>
[Informations de référence sur le compilateur MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
