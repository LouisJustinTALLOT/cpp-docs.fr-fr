---
title: Options du compilateur MSVC
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: ab41a5de027f28b361937e58fb179fd72db54e4e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221742"
---
# <a name="compiler-options"></a>Options du compilateur

CL.exe est un outil qui contrôle le Microsoft C++ (MSVC) C et C++ compilateurs et l’éditeur de liens. CL.exe peut être exécuté uniquement sur les systèmes d’exploitation qui prennent en charge de Microsoft Visual Studio pour Windows.

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
