---
title: -GX (activer la gestion des exceptions) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095db3db73f2be4012efe39f3b8cd8e645ad46c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718323"
---
# <a name="gx-enable-exception-handling"></a>/GX (Activer la gestion des exceptions)

Obsolète. Permet aux exceptions synchrone à l’aide de l’hypothèse que les fonctions déclarées à l’aide de `extern "C"` jamais lever une exception.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Notes

**/GX** est déconseillée. Utiliser les équivalents [/EHsc](../../build/reference/eh-exception-handling-model.md) plutôt l’option. Pour obtenir la liste des options du compilateur déconseillées, consultez le **Options déconseillées et supprimées du compilateur** section [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).

Par défaut, **/EHsc**, l’équivalent de **/GX**, est en vigueur quand vous compilez à l’aide de l’environnement de développement Visual Studio. Lorsque vous utilisez les outils de ligne de commande, aucune gestion des exceptions ne sont spécifié. C’est l’équivalent de **/GX-**.

Pour plus d’informations, consultez [gestion des exceptions C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Dans le volet de navigation, choisissez **propriétés de Configuration**, **C/C++**, **ligne de commande**.

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md)