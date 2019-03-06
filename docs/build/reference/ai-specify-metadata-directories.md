---
title: /AI (Spécifier les répertoires des métadonnées)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: a2d87039e2195c96e4209c7b5098473a6f52c486
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424442"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Spécifier les répertoires des métadonnées)

Spécifie un répertoire dans lequel le compilateur doit faire une recherche en vue de résoudre les références de fichiers passées à la directive `#using`.

## <a name="syntax"></a>Syntaxe

> **/AI**_directory_

## <a name="arguments"></a>Arguments

*directory*<br/>
Le répertoire ou le chemin d’accès dans lequel le compilateur va effectuer la recherche.

## <a name="remarks"></a>Notes

Un seul répertoire peut être passé à un **/AI** invocation. Spécifiez une **/AI** option pour chaque chemin d’accès que vous voulez que le compilateur à rechercher. Par exemple, pour ajouter C:\Project\Meta et C:\Common\Meta au chemin de recherche du compilateur pour `#using` , ajoutez `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` à la ligne de commande du compilateur ou ajoutez chaque répertoire à la **supplémentaires #using de répertoires** propriété dans Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **général** page de propriétés.

1. Modifier le **supplémentaires #using répertoires** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Directive #using](../../preprocessor/hash-using-directive-cpp.md)
