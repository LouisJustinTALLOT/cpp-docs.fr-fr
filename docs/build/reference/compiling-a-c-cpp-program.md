---
title: Guide de référenceC++ du compilateur C/MSVC-Visual Studio
description: Options de l’ensemble d’outils du compilateur MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077380"
---
# <a name="compiling-a-cc-project"></a>Compilation d’un projetC++ C/

Les options C++ C et du compilateur peuvent être définies dans l’IDE de Visual Studio ou sur la ligne de commande.

## <a name="in-visual-studio"></a>Dans Visual Studio

Vous pouvez définir des options du compilateur pour chaque projet dans la boîte de dialogue **pages de propriétés** de Visual Studio. Dans le volet gauche, sélectionnez **Propriétés de configuration**, **CC++ /** , puis choisissez la catégorie option du compilateur. La rubrique relative à chaque option de compilateur explique comment définir cette dernière et où la trouver dans l'environnement de développement. Pour obtenir une liste complète, consultez [Options du compilateur MSVC](compiler-options.md) .

## <a name="from-the-command-line"></a>Depuis la ligne de commande

Vous pouvez définir les options de compilateur (CL.exe) :

- [Sur la ligne de commande](compiler-command-line-syntax.md)

- [Dans les fichiers de commandes](cl-command-files.md)

- [Dans la variable d’environnement CL](cl-environment-variables.md)

Les options spécifiées dans la variable d'environnement CL sont utilisées chaque fois qu'elle est appelée. Si un fichier de commandes est nommé dans la variable d'environnement CL ou sur la ligne de commande, les options qu'il spécifie sont utilisées. Contrairement à la ligne de commande ou à la variable d'environnement CL, un fichier de commandes vous permet d'utiliser plusieurs lignes d'options et de noms de fichiers.

Les options de compilateur sont traitées de « gauche à droite », et quand un conflit est détecté, la dernière option (la plus à droite) est celle qui prévaut. La variable d'environnement CL est traitée avant la ligne de commande, de sorte qu'en cas de conflit entre CL et la ligne de commande, c'est cette dernière qui est prioritaire.

## <a name="additional-compiler-topics"></a>Rubriques supplémentaires relatives au compilateur

- [Options du compilateur MSVC](compiler-options.md)

- [Fichiers d'en-tête précompilés](../creating-precompiled-header-files.md)

- [CL appelle l’éditeur de liens](cl-invokes-the-linker.md)

Pour plus d’informations sur le choix de l’architecture hôte et cible du compilateur, consultez [configurer C++ des projets pour les cibles x64 64 bits](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)
