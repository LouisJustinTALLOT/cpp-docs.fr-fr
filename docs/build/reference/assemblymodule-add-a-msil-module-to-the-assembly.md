---
description: En savoir plus sur:/ASSEMBLYMODULE (ajouter un module MSIL à l’assembly)
title: /ASSEMBLYMODULE (Ajouter un module MSIL à l'assembly)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: d56895b6bec05efda1104e319e93a040f818e06e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182942"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (Ajouter un module MSIL à l'assembly)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Module à inclure dans cet assembly.

## <a name="remarks"></a>Notes

L’option/ASSEMBLYMODULE vous permet d’ajouter une référence de module à un assembly. Les informations de type dans le module ne sont pas disponibles pour le programme d’assembly qui a ajouté la référence de module. Toutefois, les informations de type dans le module sont disponibles pour tout programme qui fait référence à l’assembly.

Utilisez [#using](../../preprocessor/hash-using-directive-cpp.md) pour ajouter une référence de module à un assembly et rendre les informations de type du module disponibles pour le programme d’assembly.

Par exemple, considérez le scénario suivant :

1. Créez un module avec [/LN](ln-create-msil-module.md).

1. Utilisez/ASSEMBLYMODULE dans un autre projet pour inclure le module dans la compilation actuelle, qui créera un assembly. Ce projet ne fait pas référence au module avec `#using` .

1. Tout projet qui fait référence à cet assembly peut désormais également utiliser des types du module.

Les autres options de l’éditeur de liens qui affectent la génération d’assembly sont les suivantes :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

L’éditeur de liens MSVC accepte les fichiers. netmodule comme entrée et le fichier de sortie produit par l’éditeur de liens sera un assembly ou un fichier. netmodule sans dépendance au moment de l’exécution sur l’un des modules. netmodule entrés dans l’éditeur de liens.  Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **entrée** .

1. Modifiez la propriété **Ajouter un module à l’assembly** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
