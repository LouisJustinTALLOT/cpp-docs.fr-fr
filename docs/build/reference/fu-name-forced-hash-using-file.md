---
title: '-FU (nom du #using fichier) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e804aa48752d1f100e4c843fae9c0d5c70ae8b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423153"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nom du fichier #using imposé)

Une option du compilateur que vous pouvez utiliser comme alternative au passage d’un nom de fichier à [#using, Directive](../../preprocessor/hash-using-directive-cpp.md) dans le code source.

## <a name="syntax"></a>Syntaxe

> **/FU** *fichier*

## <a name="arguments"></a>Arguments

*fichier*<br/>
Spécifie le fichier de métadonnées à référencer dans cette compilation.

## <a name="remarks"></a>Notes

Le commutateur /FU prend simplement un nom de fichier. Pour spécifier plusieurs fichiers, utilisez /FU avec chacun d’eux.

Si vous utilisez C++ / c++ / CLI et référencez les métadonnées pour utiliser le [assemblys Friend](../../dotnet/friend-assemblies-cpp.md) fonctionnalité, vous ne pouvez pas utiliser **/FU**. Vous devez référencer les métadonnées dans le code à l’aide de `#using`— avec la `[as friend]` attribut. Assemblys friend ne sont pas pris en charge dans les extensions du composant C++ de Visual C++ / c++ / CX.

Pour plus d’informations sur la création d’un assembly ou un module pour le common language runtime (CLR), consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Pour plus d’informations sur la création en C / c++ / CX, consultez [génération d’applications et bibliothèques](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **avancé** page de propriétés.

1. Modifier le **Force #using** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)