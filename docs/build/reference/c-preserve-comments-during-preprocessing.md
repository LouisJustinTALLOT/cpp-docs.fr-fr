---
title: /C (Conserver les commentaires pendant le prétraitement)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: f80ebf45dd396a3f92d9b755c56522d4731bb2d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440275"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conserver les commentaires pendant le prétraitement)

Conserve les commentaires pendant le prétraitement.

## <a name="syntax"></a>Syntaxe

```
/C
```

## <a name="remarks"></a>Notes

Cette option de compilateur requiert l’option **/e**, **/p**ou **/EP** .

L’exemple de code suivant affiche le commentaire de code source.

```cpp
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Cet exemple produira la sortie suivante.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés du **préprocesseur** .

1. Modifiez la propriété **conserver les commentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/E (Prétraiter dans stdout)](e-preprocess-to-stdout.md)<br/>
[/P (Prétraiter jusqu’à un fichier)](p-preprocess-to-a-file.md)<br/>
[/EP (Prétraiter dans stdout sans directive #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
