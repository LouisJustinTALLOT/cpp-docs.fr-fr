---
description: En savoir plus sur:/LN (créer un module MSIL)
title: /LN (Créer le module MSIL)
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: 63b6f47fe6bef24341d3c19a6ad96ac3808e486e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190915"
---
# <a name="ln-create-msil-module"></a>/LN (Créer le module MSIL)

Indique qu'un manifeste d'assembly ne doit pas être inséré dans le fichier de sortie.

## <a name="syntax"></a>Syntaxe

```
/LN
```

## <a name="remarks"></a>Notes

Par défaut, **/LN** n’est pas activé (un manifeste d’assembly est inséré dans le fichier de sortie).

Quand **/LN** est utilisé, l’une des options [/clr (compilation du Common Language Runtime)](clr-common-language-runtime-compilation.md) doit également être utilisée.

Un programme managé qui n’a pas de métadonnées d’assembly dans le manifeste est appelé un module. Si vous compilez avec [/c (compiler sans liaison)](c-compile-without-linking.md) et **/LN**, spécifiez [/noAssembly (créer un module MSIL)](noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer le fichier de sortie.

Vous pouvez créer des modules si vous souhaitez adopter une approche basée sur les composants pour la création d’assemblys.  Autrement dit, vous pouvez créer des types et les compiler dans des modules.  Vous pouvez ensuite générer un assembly à partir d’un ou de plusieurs modules.  Pour plus d’informations sur la création d’assemblys à partir de modules, consultez [fichiers. netmodule en tant qu’entrée](netmodule-files-as-linker-input.md) de l’éditeur de liens ou [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

L’extension de fichier par défaut d’un module est. netmodule.

Dans les versions antérieures à Visual Studio 2005, un module a été créé avec **/clr : noAssembly**.

L’éditeur de liens MSVC accepte les fichiers. netmodule comme entrée et le fichier de sortie produit par l’éditeur de liens sera un assembly ou un fichier. netmodule sans dépendance au moment de l’exécution sur l’un des modules. netmodule entrés dans l’éditeur de liens.  Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](netmodule-files-as-linker-input.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

- Spécifiez [/noAssembly (créer un module MSIL)](noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer le fichier de sortie.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
