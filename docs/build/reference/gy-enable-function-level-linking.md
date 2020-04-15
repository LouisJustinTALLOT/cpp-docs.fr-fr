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
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328277"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Activer la liaison au niveau des fonctions)

Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs).

## <a name="syntax"></a>Syntaxe

```
/Gy[-]
```

## <a name="remarks"></a>Notes

Le lien exige que les fonctions soient emballées séparément en tant que COMDATs pour exclure ou commander des fonctions individuelles dans un fichier DLL ou .exe.

Vous pouvez utiliser l’option linker [/OPT (Optimizations)](opt-optimizations.md) pour exclure les fonctions emballées non réfrésées du fichier .exe.

Vous pouvez utiliser l’option de liaison [/ORDER (Put Functions in Order)](order-put-functions-in-order.md) pour inclure des fonctions emballées dans un ordre spécifié dans le fichier .exe.

Les fonctions inlines sont toujours emballées si elles sont instantanées sous forme d’appels (ce qui se produit, par exemple, si l’inlining est éteint ou si vous prenez une adresse de fonction). En outre, les fonctions des membres de la CMD définies dans la déclaration de classe sont automatiquement emballées; d’autres fonctions ne le sont pas, et la sélection de cette option est nécessaire pour les compiler en fonctions emballées.

> [!NOTE]
> [L’option /ZI,](z7-zi-zi-debug-information-format.md) utilisée pour Edit and Continue, définit automatiquement l’option **/Gy.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriété **Code Generation.**

1. Modifier la propriété **De liaison fonction fonction-niveau d’activation.**

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
