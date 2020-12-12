---
description: En savoir plus sur les éléments suivants:/Qimprecise_fwaits (supprimer fwaits à l’intérieur des blocs try)
title: /Qimprecise_fwaits (Remove fwaits Inside Try Blocks)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 5f3d96656d062a7e5b0c4ad78ba7cd536069e013
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225620"
---
# <a name="qimprecise_fwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Remove fwaits Inside Try Blocks)

Supprime les `fwait` commandes internes aux **`try`** blocs quand vous utilisez l’option du compilateur [/FP : except](fp-specify-floating-point-behavior.md) .

## <a name="syntax"></a>Syntaxe

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Notes

Cette option n’a aucun effet si **/FP : except** n’est pas également spécifié. Si vous spécifiez l’option **/FP : except** , le compilateur insère une `fwait` commande autour de chaque ligne de code dans un **`try`** bloc. De cette façon, le compilateur peut identifier la ligne de code spécifique qui produit une exception. **/Qimprecise_fwaits** supprime les `fwait` instructions internes, en laissant uniquement les attentes autour du **`try`** bloc. Cela améliore les performances, mais le compilateur ne peut qu’indiquer le **`try`** bloc qui provoque une exception, pas la ligne.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
