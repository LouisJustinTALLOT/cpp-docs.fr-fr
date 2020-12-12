---
description: En savoir plus sur:/OD (désactiver (débogage))
title: /Od (Désactiver (Débogage))
ms.date: 11/04/2016
f1_keywords:
- /od
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
ms.openlocfilehash: 9d425244a1790a9bb74e1c92db88f32bb0372ab2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214303"
---
# <a name="od-disable-debug"></a>/Od (Désactiver (Débogage))

Désactive toutes les optimisations dans le programme et accélère la compilation.

## <a name="syntax"></a>Syntaxe

```
/Od
```

## <a name="remarks"></a>Notes

Il s’agit de l’option par défaut. Étant donné que **/OD** supprime le déplacement du code, il simplifie le processus de débogage. Pour plus d’informations sur les options du compilateur pour le débogage, consultez [/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **optimisation** .

1. Modifiez la propriété **Optimization** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le code), options](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md)
