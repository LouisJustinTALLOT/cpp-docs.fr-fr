---
title: /GX (Activer la gestion des exceptions)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 43be8f6d0f080f0d85568ce5b089751fc68f0e8e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815461"
---
# <a name="gx-enable-exception-handling"></a>/GX (Activer la gestion des exceptions)

Obsolète. Permet aux exceptions synchrone à l’aide de l’hypothèse que les fonctions déclarées à l’aide de `extern "C"` jamais lever une exception.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Notes

**/GX** est déconseillée. Utiliser les équivalents [/EHsc](eh-exception-handling-model.md) plutôt l’option. Pour obtenir la liste des options du compilateur déconseillées, consultez le **Options déconseillées et supprimées du compilateur** section [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

Par défaut, **/EHsc**, l’équivalent de **/GX**, est en vigueur quand vous compilez à l’aide de l’environnement de développement Visual Studio. Lorsque vous utilisez les outils de ligne de commande, aucune gestion des exceptions ne sont spécifié. C’est l’équivalent de **/GX-**.

Pour plus d’informations, consultez [gestion des exceptions C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet de navigation, choisissez **propriétés de Configuration**, **C/C++**, **ligne de commande**.

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modèle de gestion des exceptions)](eh-exception-handling-model.md)
