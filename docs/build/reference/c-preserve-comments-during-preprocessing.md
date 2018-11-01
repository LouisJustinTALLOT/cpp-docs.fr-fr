---
title: /C (Conserver les commentaires pendant le prétraitement)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: b37e279af3995bd1d61c97dc88b49cdd95495c75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442599"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conserver les commentaires pendant le prétraitement)

Conserve les commentaires pendant le prétraitement.

## <a name="syntax"></a>Syntaxe

```
/C
```

## <a name="remarks"></a>Notes

Cette option du compilateur nécessite le **/E**, **/P**, ou **/EP** option.

L’exemple de code suivant affiche le commentaire de code source.

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Cet exemple produit la sortie suivante.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **préprocesseur** page de propriétés.

1. Modifier le **Commentaires conservés** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/E (Prétraiter dans stdout)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P (Prétraiter jusqu’à un fichier)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP (Prétraiter dans stdout sans directive #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)