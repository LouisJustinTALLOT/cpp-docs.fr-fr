---
title: -ASSEMBLYMODULE (ajouter un Module MSIL à l’Assembly) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c1b5104a264a3fbeeada080b6c34a6b1c5e23ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703935"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (Ajouter un module MSIL à l'assembly)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Le module que vous souhaitez inclure dans cet assembly.

## <a name="remarks"></a>Notes

L’option /ASSEMBLYMODULE vous permet de vous permet d’ajouter une référence de module à un assembly. Informations de type dans le module ne sera pas disponibles pour le programme d’assembly qui a ajouté la référence de module. Toutefois, les informations de type dans le module sera disponibles pour n’importe quel programme qui fait référence à l’assembly.

Utilisez [#using](../../preprocessor/hash-using-directive-cpp.md) pour ajouter une référence de module à un assembly et pour rendre les informations de type du module disponibles pour le programme d’assembly.

Par exemple, examinez le scénario suivant :

1. Créer un module avec [/LN](../../build/reference/ln-create-msil-module.md).

1. Utilisez /ASSEMBLYMODULE dans un autre projet pour inclure le module dans la compilation en cours, ce qui crée un assembly. Ce projet ne référence pas le module avec `#using`.

1. N’importe quel projet qui fait référence à cet assembly peut désormais également utiliser les types à partir du module.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

L’éditeur de liens Visual C++ accepte les fichiers .netmodule en tant qu’entrée et le fichier de sortie produit par l’éditeur de liens sera un assembly ou un fichier .netmodule sans aucune dépendance d’exécution sur un des fichiers .netmodule qui ont été entrés à l’éditeur de liens.  Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **ajouter un Module à l’Assembly** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)