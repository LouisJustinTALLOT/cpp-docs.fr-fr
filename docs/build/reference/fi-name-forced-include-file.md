---
title: /FI (Nom du fichier Include imposé)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: 6460f75e2cad81bc1dcc540e3c687de5d0dc0d32
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439801"
---
# <a name="fi-name-forced-include-file"></a>/FI (Nom du fichier Include imposé)

Fait en sorte que le préprocesseur traite le fichier d’en-tête spécifié.

## <a name="syntax"></a>Syntaxe

```
/FI[ ]pathname
```

## <a name="remarks"></a>Notes

Cette option a le même effet que la spécification du fichier avec des guillemets doubles dans une directive `#include` sur la première ligne de chaque fichier source spécifié sur la ligne de commande, dans la variable d’environnement CL ou dans un fichier de commandes. Si vous utilisez plusieurs options **/fi** , les fichiers sont inclus dans l’ordre dans lequel ils sont traités par CL.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété **fichier include forcé** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
