---
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
ms.openlocfilehash: 9643b8b4b4b26b3f7a8a59ed0085601b1a53094d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817970"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Activer la liaison au niveau des fonctions)

Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Notes

L’éditeur de liens requiert que les fonctions soient empaquetées séparément en tant que COMDAT à exclure ou commandez des fonctions individuelles dans un fichier DLL ou .exe.

Vous pouvez utiliser l’option de l’éditeur de liens [/OPT (optimisations)](opt-optimizations.md) à exclure des fonctions empaquetées non référencées à partir du fichier .exe.

Vous pouvez utiliser l’option de l’éditeur de liens [/ORDER (mettre les fonctions dans l’ordre)](order-put-functions-in-order.md) pour inclure des fonctions empaquetées dans un ordre spécifié dans le fichier .exe.

Fonctions inline sont toujours empaquetées si elles sont instanciées en tant qu’appels (ce qui se produit, par exemple, si la fonctionnalité inline est désactivée ou si vous prenez une adresse de fonction). En outre, les fonctions membres C++ définies dans la déclaration de classe sont empaquetées automatiquement ; autres fonctions ne sont pas, et cette option est requise pour les compiler en tant que fonctions empaquetées.

> [!NOTE]
>  Le [/Zi](z7-zi-zi-debug-information-format.md) option, utilisée pour modifier & Continuer, définit automatiquement le **/Gy** option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **génération de Code** page de propriétés.

1. Modifier le **activer la liaison au niveau des fonctions** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
