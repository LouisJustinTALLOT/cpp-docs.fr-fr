---
title: Options du compilateur MSVC
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 831aade72cd728ec42aee5ef1f320deb7bdf173d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294263"
---
# <a name="compiler-options"></a>Options du compilateur

CL.exe est un outil qui contrôle le Microsoft Visual C++ (MSVC) C et de compilateurs C++ et de l’éditeur de liens. CL.exe peut être exécuté uniquement sur les systèmes d’exploitation qui prennent en charge de Microsoft Visual Studio pour Windows.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers. Pour plus d’informations, consultez [utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](../building-on-the-command-line.md).

Les compilateurs génèrent des fichiers objet (.obj) de fichier Format COFF (Common Object). L’éditeur de liens produit des fichiers exécutables (.exe) ou des bibliothèques de liens dynamiques (DLL).

Notez que toutes les options du compilateur respectent la casse. Vous pouvez utiliser soit une barre oblique (`/`) ou un tiret (`-`) pour spécifier une option du compilateur.

Pour compiler sans liaison, utilisez la [/c](c-compile-without-linking.md) option.

## <a name="find-a-compiler-option"></a>Recherchez une option du compilateur

Pour rechercher une option spécifique, consultez une des listes suivantes :

- [Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md)

- [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Spécifiez les options du compilateur

La rubrique pour chaque option du compilateur explique comment elle peut être définie dans l’environnement de développement. Pour plus d’informations sur la spécification des options en dehors de l’environnement de développement, consultez :

- [Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

- [Fichiers de commandes CL](cl-command-files.md)

- [Variables d’environnement CL](cl-environment-variables.md)

## <a name="related-build-tools"></a>Outils de génération connexes

[Options de l’éditeur de liens MSVC](linker-options.md) affectent également la façon dont votre programme est généré.

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)<br/>
[CL appelle l’éditeur de liens](cl-invokes-the-linker.md)
