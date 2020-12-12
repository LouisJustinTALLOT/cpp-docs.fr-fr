---
description: 'En savoir plus sur:/FU (nommer le fichier #using forcé)'
title: '/FU (Nom du fichier #using imposé)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: 458369e7ff1322d2d2fa2fb37e8915c5a39c8446
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200375"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nom du fichier #using imposé)

Option du compilateur que vous pouvez utiliser comme alternative au passage d’un nom de fichier à [#using directive](../../preprocessor/hash-using-directive-cpp.md) dans le code source.

## <a name="syntax"></a>Syntaxe

> **/FU** *fichier*

## <a name="arguments"></a>Arguments

*file*<br/>
Spécifie le fichier de métadonnées à référencer dans cette compilation.

## <a name="remarks"></a>Notes

Le commutateur/FU n’accepte qu’un seul nom de fichier. Pour spécifier plusieurs fichiers, utilisez/FU avec chacun d’eux.

Si vous utilisez C++/CLI et que vous référencez des métadonnées pour utiliser la fonctionnalité d' [assemblys friend](../../dotnet/friend-assemblies-cpp.md) , vous ne pouvez pas utiliser **/Fu**. Vous devez référencer les métadonnées dans le code à l’aide de `#using` , avec l' `[as friend]` attribut. Les assemblys friend ne sont pas pris en charge dans Visual C++ extensions de composant C++/CX.

Pour plus d’informations sur la création d’un assembly ou d’un module pour le common language runtime (CLR), consultez [/clr (compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md). Pour plus d’informations sur la génération en C++/CX, consultez [génération d’applications et de bibliothèques](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **Force #using** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
