---
title: /Qimprecise_fwaits (Remove fwaits Inside Try Blocks)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 40683382686ea64a80563f3f29b7d3523f4144a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319588"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Remove fwaits Inside Try Blocks)

Supprime le `fwait` commandes internes `try` bloque quand vous utilisez le [/fp : sauf](fp-specify-floating-point-behavior.md) option du compilateur.

## <a name="syntax"></a>Syntaxe

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Notes

Cette option n’a aucun effet si **/fp : à l’exception** n’est pas également spécifié. Si vous spécifiez le **/fp : sauf** option, le compilateur insère un `fwait` commande autour de chaque ligne de code dans un `try` bloc. De cette façon, le compilateur peut identifier la ligne de code qui génère une exception spécifique. **/ Qimprecise_fwaits** supprime interne `fwait` obtenir des instructions, en laissant uniquement les attentes autour du `try` bloc. Cela améliore les performances, mais le compilateur pourrez indiquer laquelle `try` bloc lève une exception, et non pas la ligne.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
