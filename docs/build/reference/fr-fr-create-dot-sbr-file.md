---
title: -FR, -Fr (créer. Fichier de sbr) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
dev_langs:
- C++
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5691a87f7350c7816e8ddb58d5591e16cc18189
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709598"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Créer un fichier .sbr)

Crée des fichiers .sbr.

## <a name="syntax"></a>Syntaxe

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Notes

Pendant le processus de build, Microsoft Browse Information File Maintenance Utility (BSCMAKE) utilise ces fichiers pour créer un fichier .BSC, qui affiche des informations de consultation.

**/FR** crée un fichier .sbr contenant des informations symboliques complètes.

**/Fr** crée un fichier .sbr qui ne contient pas d’informations sur les variables locales.

Si vous ne spécifiez pas `filename`, le fichier .sbr a le même nom de base que le fichier source.

**/Fr** est déconseillé. Utilisez **/FR** à la place. Pour plus d’informations, consultez la section « Options du compilateur déconseillées et supprimées » dans [Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md).

> [!NOTE]
>  Ne modifiez pas l’extension .sbr. Avec BSCMAKE, les fichiers intermédiaires doivent avoir cette extension.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Dans le volet de navigation, accédez à la page de propriétés **C/C++**, **Informations de consultation** .

1. Modifiez la propriété **Fichier d’informations de consultation** ou **Activer les informations de consultation** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Voir aussi

[Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)