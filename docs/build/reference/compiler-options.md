---
title: Options du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea07361a292ee5e7cde99cedad2d5ac4c8a53aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374271"
---
# <a name="compiler-options"></a>Options du compilateur

CL.exe est un outil qui contrôle le Microsoft Visual C++ (MSVC) C et les compilateurs C++ et l’éditeur de liens. CL.exe peut être exécuté uniquement sur les systèmes d’exploitation qui prennent en charge de Microsoft Visual Studio pour Windows.

> [!NOTE]  
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers. Pour plus d’informations, consultez [code de génération C/C++ sur la ligne de commande](../building-on-the-command-line.md).

Les compilateurs génèrent des fichiers objets (.obj) de fichier Format COFF (Common Object). L’éditeur de liens génère des fichiers exécutables (.exe) ou des bibliothèques de liens dynamiques (DLL).

Notez que toutes les options du compilateur respectent la casse. Vous pouvez utiliser soit une barre oblique (`/`) ou un tiret (`-`) pour spécifier une option du compilateur.

Pour compiler sans liaison, utilisez la [/c](../../build/reference/c-compile-without-linking.md) option.

## <a name="find-a-compiler-option"></a>Rechercher une option du compilateur

Pour rechercher une option du compilateur particulier, consultez une des listes suivantes :

- [Options du compilateur classées par ordre alphabétique](../../build/reference/compiler-options-listed-alphabetically.md)

- [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Spécifiez les options du compilateur

Pour chaque option du compilateur explique comment elle peut être définie dans l’environnement de développement. Pour plus d’informations sur la spécification des options à l’extérieur de l’environnement de développement, consultez :

- [Syntaxe de la ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md)

- [Fichiers de commandes CL](../../build/reference/cl-command-files.md)

- [Variables d’environnement CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Outils de génération connexes

[Options de l’éditeur de liens](../../build/reference/linker-options.md) affectent également la manière dont votre programme est généré.

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
[Compilation rapide](../../build/reference/fast-compilation.md)  
[CL appelle l’éditeur de liens](../../build/reference/cl-invokes-the-linker.md)  
