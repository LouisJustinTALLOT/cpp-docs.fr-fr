---
description: En savoir plus sur:/Gy (activer la liaison de Function-Level)
title: /Gy (Activer la liaison au niveau des fonctions)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 3c4136b25001f7f6d6729b9c6089995d1bcd71bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200128"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Activer la liaison au niveau des fonctions)

Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Notes

L’éditeur de liens requiert que les fonctions soient empaquetées séparément en tant que COMDAT pour exclure ou ordonner des fonctions individuelles dans un fichier DLL ou. exe.

Vous pouvez utiliser l’option de l’éditeur de liens [/OPT (optimisations)](opt-optimizations.md) pour exclure les fonctions empaquetées non référencées du fichier. exe.

Vous pouvez utiliser l’option de l’éditeur de liens [/Order (mettre les fonctions dans l’ordre)](order-put-functions-in-order.md) pour inclure des fonctions packagées dans un ordre spécifié dans le fichier. exe.

Les fonctions inline sont toujours empaquetées si elles sont instanciées en tant qu’appels (ce qui se produit, par exemple, si l’incorporation est désactivée ou si vous prenez une adresse de fonction). En outre, les fonctions membres C++ définies dans la déclaration de classe sont automatiquement empaquetées. d’autres fonctions ne le sont pas, et la sélection de cette option est requise pour les compiler comme fonctions packagées.

> [!NOTE]
> L’option [/Zi](z7-zi-zi-debug-information-format.md) , utilisée pour modifier & continuer, définit automatiquement l’option **/Gy** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **génération de code** .

1. Modifiez la propriété **activer la liaison de Function-Level** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
