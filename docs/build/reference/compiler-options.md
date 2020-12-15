---
description: 'En savoir plus sur : options du compilateur'
title: Options du compilateur MSVC
ms.date: 12/14/2020
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.openlocfilehash: f89695b00be4ed67a00f947c6b76943bfa5eaf59
ms.sourcegitcommit: 48b897797b3132ae934b1d191e3870c3c2466335
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97514576"
---
# <a name="compiler-options"></a>Options du compilateur

cl.exe est un outil qui contrôle les compilateurs et l’éditeur de liens Microsoft C++ (MSVC) C et C++. cl.exe ne peut être exécutée que sur des systèmes d’exploitation qui prennent en charge Microsoft Visual Studio pour Windows.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers. Pour plus d’informations, consultez [utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](../building-on-the-command-line.md).

Les compilateurs produisent des fichiers objets COFF (Common Object File Format) (. obj). L’éditeur de liens produit des fichiers exécutables (. exe) ou des bibliothèques de liens dynamiques (dll).

Toutes les options du compilateur respectent la casse. Vous pouvez utiliser une barre oblique ( `/` ) ou un tiret ( `-` ) pour spécifier une option de compilateur.

Pour compiler sans liaison, utilisez l’option [/c](c-compile-without-linking.md) .

## <a name="find-a-compiler-option"></a>Rechercher une option du compilateur

Pour rechercher une option de compilateur particulière, consultez l’une des listes suivantes :

- [Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md)

- [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Spécifier les options du compilateur

La rubrique relative à chaque option du compilateur explique comment elle peut être définie dans l’environnement de développement. Pour plus d’informations sur la spécification d’options en dehors de l’environnement de développement, consultez :

- [Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

- [Fichiers de commandes CL](cl-command-files.md)

- [Variables d’environnement CL](cl-environment-variables.md)

## <a name="related-build-tools"></a>Outils de génération associés

Les options de l' [éditeur de liens MSVC](linker-options.md) affectent également le mode de génération de votre programme.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)<br/>
[CL appelle l’éditeur de liens](cl-invokes-the-linker.md)
