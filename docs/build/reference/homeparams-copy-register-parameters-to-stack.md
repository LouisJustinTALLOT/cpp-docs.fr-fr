---
title: -homeparams (copier les paramètres de Registre de pile) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6c51c5e6062f4d7b793e3adb6e9f22e03a65c11
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699834"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/Homeparams (Copier les paramètres des registres vers la pile)

Force l'écriture des paramètres passés dans les registres à leurs emplacements sur la pile lors de l'entrée de la fonction.

## <a name="syntax"></a>Syntaxe

```
/homeparams
```

## <a name="remarks"></a>Notes

Cette option du compilateur est uniquement pour les x64 compilateurs (compilation natives et croisée).

Lorsque les paramètres sont passés dans un x64 compilation, conventions d’appel requièrent une pile pour les paramètres, même pour les paramètres passés dans les registres. Pour plus d’informations, consultez [passage de paramètres](../../build/parameter-passing.md). Toutefois, par défaut dans une version Release, les paramètres de Registre ne seront pas être écrites dans la pile, dans l’espace qui est déjà fourni pour les paramètres. Cela rend difficile à déboguer une version optimisée (version) de votre programme.

Pour une version Release, utilisez **/homeparams** pour vous assurer que vous pouvez déboguer votre application. **/Homeparams** implique un inconvénient de performances, car elle ne nécessite pas un cycle pour charger les paramètres de Registre sur la pile.

Dans une version debug, la pile est toujours remplie avec les paramètres passés dans les registres.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)