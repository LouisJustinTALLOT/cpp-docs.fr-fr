---
title: /GX (Activer la gestion des exceptions)
ms.date: 11/19/2019
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
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245087"
---
# <a name="gx-enable-exception-handling"></a>/GX (Activer la gestion des exceptions)

Option déconseillée. Active la gestion synchrone des exceptions en partant du principe que les fonctions déclarées à l’aide de `extern "C"` ne lèvent jamais d’exception.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Notes

**/GX** est déconseillé. Utilisez à la place l’option [/EHsc](eh-exception-handling-model.md) équivalente. Pour obtenir la liste des options du compilateur déconseillées, consultez la section **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

Par défaut, **/EHsc**, l’équivalent de **/GX**, est activé quand vous compilez à l’aide de l’environnement de développement Visual Studio. Lorsque vous utilisez les outils en ligne de commande, aucune gestion des exceptions n’est spécifiée. Il s’agit de l’équivalent de **/GX-** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet de navigation, choisissez **Propriétés de configuration**, **CC++/** , ligne de **commande**.

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modèle de gestion des exceptions)](eh-exception-handling-model.md)
