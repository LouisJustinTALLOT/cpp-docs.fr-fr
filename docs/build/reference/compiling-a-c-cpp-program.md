---
title: Référence du compilateur MSVC C/C++ - Visual Studio
description: Options de jeu d’outils du compilateur MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: 2269ba69cea2702ff190c791eb6753acb3619f7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294146"
---
# <a name="compiling-a-cc-project"></a>Compilation d’un projet C/C++

Les options de compilateur C et C++ peuvent être définies dans l’IDE Visual Studio ou sur la ligne de commande. 

## <a name="in-visual-studio"></a>Dans Visual Studio

Vous pouvez définir les options du compilateur pour chaque projet dans son Visual Studio **Pages de propriétés** boîte de dialogue. Dans le volet gauche, sélectionnez **propriétés de Configuration**, **C/C++** , puis choisissez la catégorie d’option du compilateur. La rubrique relative à chaque option de compilateur explique comment définir cette dernière et où la trouver dans l'environnement de développement. Consultez [Options du compilateur MSVC](compiler-options.md) pour obtenir la liste complète.

## <a name="from-the-command-line"></a>À partir de la ligne de commande

Vous pouvez définir les options de compilateur (CL.exe) :

- [Sur la ligne de commande](compiler-command-line-syntax.md)

- [Dans les fichiers de commandes](cl-command-files.md)

- [Dans la variable d’environnement CL](cl-environment-variables.md)

Les options spécifiées dans la variable d'environnement CL sont utilisées chaque fois qu'elle est appelée. Si un fichier de commandes est nommé dans la variable d'environnement CL ou sur la ligne de commande, les options qu'il spécifie sont utilisées. Contrairement à la ligne de commande ou à la variable d'environnement CL, un fichier de commandes vous permet d'utiliser plusieurs lignes d'options et de noms de fichiers.

Les options de compilateur sont traitées de « gauche à droite », et quand un conflit est détecté, la dernière option (la plus à droite) est celle qui prévaut. La variable d'environnement CL est traitée avant la ligne de commande, de sorte qu'en cas de conflit entre CL et la ligne de commande, c'est cette dernière qui est prioritaire.

## <a name="additional-compiler-topics"></a>Rubriques supplémentaires relatives au compilateur

- [Options du compilateur MSVC](compiler-options.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

- [CL appelle l’éditeur de liens](cl-invokes-the-linker.md)

Pour plus d’informations sur le choix de l’architecture d’hôte et cible du compilateur, consultez [C++ de configurer des projets pour 64 bits, x64 cibles](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)
