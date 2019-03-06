---
title: /ASSEMBLYRESOURCE (Incorporer une ressource managée)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: c18a014ca645cceb3196fb7efefd227e96f8e1fa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416214"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Incorporer une ressource managée)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Paramètres

*filename*<br/>
La ressource managée que vous souhaitez incorporer dans cet assembly.

*name*<br/>
Facultatif. Le nom logique de la ressource ; le nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.

Si vous le souhaitez, vous pouvez spécifier si le fichier doit être privé dans le manifeste d’assembly. Par défaut, *nom* est public dans l’assembly.

## <a name="remarks"></a>Notes

Utilisez l’option /ASSEMBLYRESOURCE pour incorporer une ressource dans un assembly.

Les ressources sont publiques dans l’assembly lors de la création avec l’éditeur de liens. L’éditeur de liens ne vous permet pas de renommer la ressource dans l’assembly.

Si *filename* est un fichier de ressources (.resources) de .NET Framework créé, par exemple, par le [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de la **System.Resources** espace de noms (consultez [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager) pour plus d’informations). Pour toutes les autres ressources, utilisez le **GetManifestResource** \* méthodes dans **System.Reflection.Assembly** classe pour accéder à la ressource au moment de l’exécution.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **incorporer de fichier de ressources managé** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
